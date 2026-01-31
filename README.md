# SimpleStorage 
A beginner-friendly Solidity smart contract built as part of the **Cyfrin Updraft** course.  
This project demonstrates basic Solidity concepts and how to deploy and interact with contracts using **Foundry**.

# clone projekt In Visual Studio WSL
```bash
git clone https://github.com/barb323/simple-storage-foundry
cd simple-storage-foundry
forge install
```
# New start Visual Studio


# Start local blockchain
```bash
anvil
```

# Then configure MetaMask with the local network (Localhost / Anvil)
# and import an account using a private key from Anvil.

# Deploy contract to Anvil
```bash
forge create SimpleStorage --interactive
0xac0974bec39a17e36ba4a6b4d238ff944bacb478cbed5efcae784d7bf4f2ff80 // Anvil private key
```

# Deploy contract to Anvil using a script
# Start Anvil before running the DeploySimpleStorage.s.sol script.
```bash
forge script script/DeploySimpleStorage.s.sol --rpc-url http://127.0.0.1:8545
 --broadcast --private-key 0xac0974bec39a17e36ba4a6b4d238ff944bacb478cbed5efcae784d7bf4f2ff80
 ```

# Store the private key encrypted (password: password)
```bash
cast wallet import deployer --interactive

forge script script/DeploySimpleStorage.s.sol --rpc-url http://127.0.0.1:8545
 --broadcast --account deployer
 ```

# Work with a .env file
```bash
source .env
echo $PRIVATE_KEY

forge script script/DeploySimpleStorage.s.sol --rpc-url $RPC_URL --broadcast --private-key $PRIVATE_KEY
```

# For security reasons, never expose private keys directly.
# A safer solution is described in "22 Never Use a .env File".

# Interact with a smart contract using the CLI
```bash
cast --help
cast send --help
```

# Use cast send with the contract address to send data to the contract
```bash
cast send 0x5fbdb2315678afecb367f032d93f642f64180aa3 "store(uint256)" 2026 --rpc-url $RPC_URL --private-key $PRIVATE_KEY


cast send 0x5fbdb2315678afecb367f032d93f642f64180aa3 "addPerson(string,uint256)" "Alice" 42 --rpc-url $RPC_URL --private-key $PRIVATE_KEY
```

# Use cast call to read data from the contract [TO] [SIG] [ARGS]
``` bash
cast call 0x5fbdb2315678afecb367f032d93f642f64180aa3 "retrieve()"
cast call 0x5fbdb2315678afecb367f032d93f642f64180aa3 "nameToFavoriteNumber(string)(uint256)" "Alice" --rpc-url $RPC_URL
cast call 0x5fbdb2315678afecb367f032d93f642f64180aa3 "listOfPeople(uint256)(uint256,string)" 0 --rpc-url $RPC_URL
```

# Deploy to the Sepolia testnet
# Create a new Sepolia testnet app in Alchemy
# Copy the RPC endpoint URL into the .env file
# Use the private key from your MetaMask Sepolia wallet
``` bash
source .env
forge script script/DeploySimpleStorage.s.sol --rpc-url $SEPOLIA_RPC_URL --private-key $SEPOLIA_PRIVATE_KEY --broadcast
```

# Convert HEX to DEC
``` bash
cast --to-base 0xff dec
```