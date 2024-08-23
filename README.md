**DESCRIPTION:** Avalanche HyperSDK  
**Project:** Create a Custom Subnet  
**Challenge:** Your startup has identified the need to develop a custom virtual machine for minting and transferring tokens. The HyperSDK provides a powerful framework for building a tailored blockchain to meet these requirements. With the HyperSDK, you can define the rules and functionality of your chain, including token creation, transfer mechanisms, and order book management for asset trading.

### **PRE-INSTALLATION REQUIREMENTS**

- **WSL:** The project is developed on Ubuntu using WSL.
- **GO:** Install Go by running:
  ```bash
  sudo snap install go --classic
  ```
  Verify installation with:
  ```bash
  go version
  ```
- **GCC:** Install GCC in WSL with:
  ```bash
  sudo apt update
  sudo apt install build-essential
  ```
  Verify installation with:
  ```bash
  gcc --version
  ```

### **STEPS TO PERFORM**

1. **Clone the Repository:**
   ```bash
   git clone https://github.com/NirbehKaur/tokenvm/
   ```
2. **Open the Repository in VS Code:**
   ```bash
   code .
   ```
   Install recommended extensions in VS Code.

3. **Normalize Dependencies:**
   In the terminal, run:
   ```bash
   go mod tidy
   ```

4. **Set Go Path:**
   Ensure Go is on your path:
   ```bash
   export PATH=$PATH:$(go env GOPATH)/bin
   ```
   If this path doesn’t work, try:
   ```bash
   export PATH=$PATH:/usr/local/go/bin
   ```

5. **Launch TokenVM Subnet:**
   Run:
   ```bash
   MODE="run-single" ./scripts/run.sh
   ```
   This may take a few minutes.

6. **Build the Project:**
   Execute:
   ```bash
   ./scripts/build.sh
   ```
   The compiled CLI will be located in `./build/token-cli`.

7. **Load Demo Private Key:**
   Import the demo private key:
   ```bash
   ./build/token-cli key import demo.pk
   ```
   Import the network state:
   ```bash
   ./build/token-cli chain import-anr
   ```

### **INTERACTING WITH YOUR HYPERCHAIN**

1. **Create an Asset:**
   ```bash
   ./build/token-cli action create-asset
   ```
   Follow prompts and note the `txID` for your new asset.

2. **Mint the Asset:**
   ```bash
   ./build/token-cli action mint-asset
   ```
   Provide the required details and verify the `txID`.

3. **View Your Balance:**
   ```bash
   ./build/token-cli key balance
   ```
   Check the balance and `assetID`.

4. **Transfer Asset:**
   ```bash
   ./build/token-cli action transfer
   ```
   Specify details for the transfer and confirm.

5. **Create an Order:**
   ```bash
   ./build/token-cli action create-order
   ```
   Follow the instructions to set up your trading order and record the `txID`.

6. **Fill an Order:**
   ```bash
   ./build/token-cli action fill-order
   ```
   Choose the order to fill and confirm the transaction.

7. **Close an Order:**
   ```bash
   ./build/token-cli action close-order
   ```
   Cancel the order and ensure funds are returned.

8. **Watch Activity in Real-Time:**
   ```bash
   ./build/token-cli chain watch
   ```

### **Acknowledgement**

This project builds upon the TokenVM framework. Special thanks to the Metacrafters team for their contributions to the blockchain community.
