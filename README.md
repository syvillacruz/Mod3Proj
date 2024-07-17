# SToken 

The SToken contract is an ERC20 token implementation that allows the contract owner to mint tokens and any user to burn and transfer tokens.

## State Variables

owner: The address of the contract owner, set to the address that deploys the contract.

## Constructor

```
constructor(string memory name, string memory symbol) ERC20(name, symbol) {
    owner = msg.sender;
    _mint(msg.sender, 100 * 10**uint(decimals()));
}
```

## Functions
```
function _onlyOwner() internal view {
    require(owner == msg.sender, "Caller is not the owner");
}
```

```
function mint(address to, uint256 amount) public {
    _onlyOwner();
    _mint(to, amount);
}
```

```
function burn(uint256 amount) public {
    _burn(msg.sender, amount);
}
```

```
function transferToken(address recipient, uint256 amount) public {
        emit Transfer(msg.sender, recipient, amount);
        _transfer(msg.sender, recipient, amount);

    }
}
```
### Executing program

Deployment:
When the contract is deployed, the deployer becomes the owner and receives an initial supply of 100 tokens.

Minting Tokens: 
The owner can mint additional tokens to any address using the mint function.

Burning Tokens: 
Any user can reduce the total supply by burning their own tokens using the burn function.

Transferring Tokens: 
Token holders can transfer their tokens to other addresses using the transfer function.

## Deployment Using Remix

1. Open Remix: Go to Remix IDE.
2. Create a New File: Create a new file named SToken.sol and paste the smart contract code into it.
3. Compile the Contract: Click on the "Solidity Compiler" tab, set the compiler version to a compatible version (e.g., 0.8.0), and click "Compile SToken.sol".
4. Deploy the Contract: Click on the "Deploy & Run Transactions" tab, select the appropriate environment, set the token name and symbol, and click "Deploy".

## Authors

syvillacruz 

