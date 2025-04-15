# ERC20 Token Project with Hardhat

This project demonstrates how to create, deploy, and interact with an ERC20 token using [Hardhat](https://hardhat.org/). It uses the OpenZeppelin ERC20 implementation and provides a complete workflow for smart contract development on a local Ethereum environment.

---

## 🛠 Tech Stack

- Solidity (v0.8.x)
- Hardhat
- Ethers.js
- OpenZeppelin Contracts
- Node.js

---

## 📦 Installation

```bash
git clone https://github.com/usama-programmx/ERC20-Token-Hardhat-Deploy-Ignore.git
cd ERC20-Token-Hardhat-Deploy-Ignore
npm install

📄 Smart Contract
The ERC20 contract is defined in contracts/MyToken.sol.

solidity
Copy
Edit
// SPDX-License-Identifier: Unlicense
pragma solidity ^0.8.0;

import "@openzeppelin/contracts/token/ERC20/ERC20.sol";

contract MyToken is ERC20 {
    uint constant _initial_supply = 1000000 * (10 ** 18);

    constructor() ERC20("MyToken", "MT") {
        _mint(msg.sender, _initial_supply);
    }
}
🚀 Deployment
Start a local Hardhat node:

bash
Copy
Edit
npx hardhat node
In a new terminal, deploy the contract:

bash
Copy
Edit
npx hardhat run scripts/deploy.js --network localhost
✅ You'll see the contract address printed on the terminal.

🧪 Interaction
After deployment, you can create a new script like scripts/interact.js to interact with your contract:

js
Copy
Edit
const hre = require("hardhat");

async function main() {
    const [deployer] = await hre.ethers.getSigners();
    const contractAddress = "DEPLOYED_CONTRACT_ADDRESS";

    const MyToken = await hre.ethers.getContractAt("MyToken", contractAddress);

    const balance = await MyToken.balanceOf(deployer.address);
    console.log(`Balance of deployer: ${hre.ethers.utils.formatEther(balance)} MT`);
}

main().catch((error) => {
    console.error(error);
    process.exitCode = 1;
});
Run it with:

bash
Copy
Edit
npx hardhat run scripts/interact.js --network localhost
📁 Project Structure
bash
Copy
Edit
├── contracts/
│   └── MyToken.sol        # ERC20 Token contract
├── scripts/
│   ├── deploy.js          # Deployment script
│   └── interact.js        # (Optional) Interaction script
├── hardhat.config.js      # Hardhat config
└── .gitignore
📝 License
This project is licensed under the MIT License.

