## que3 :- Develop a contract that only allows the deployer (owner) to call a specific function (use modifiers).

```
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract OwnerRestricted {
    address public owner;
    string private secretMessage;
    
    constructor() {
        owner = msg.sender;
    }
    
    modifier onlyOwner() {
        require(msg.sender == owner, "Only owner can call this");
        _;
    }
    
    function setSecretMessage(string memory _message) public onlyOwner {
        secretMessage = _message;
    }
    
    function getSecretMessage() public view onlyOwner returns (string memory) {
        return secretMessage;
    }
}
```

![Screenshot 2025-05-19 135013](https://github.com/user-attachments/assets/5d3437eb-5d7b-4dd8-9614-587d29866bf9)

![Screenshot 2025-05-19 135042](https://github.com/user-attachments/assets/b819da61-0951-4ad7-ac52-cb4e8f54f7e0)


