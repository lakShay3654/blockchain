## que6 :- Create a contract that splits incoming Ether between 3 fixed addresses.

```
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract SplitEther {
    address payable public addr1;
    address payable public addr2;
    address payable public addr3;

    constructor(address payable _a1, address payable _a2, address payable _a3) {
        addr1 = _a1;
        addr2 = _a2;
        addr3 = _a3;
    }

    receive() external payable {
        uint share = msg.value / 3;
        addr1.transfer(share);
        addr2.transfer(share);
        addr3.transfer(msg.value - 2 * share); // handle remainder
    }
}
```

![Screenshot 2025-05-19 140939](https://github.com/user-attachments/assets/2d917e13-e4b2-43aa-80ca-bacc91b3cc09)

![image](https://github.com/user-attachments/assets/0a47efce-fe91-407a-9802-e4322051241d)


