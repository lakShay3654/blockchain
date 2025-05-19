## que5 :- Implement a simple auction system where users can place bids, and the highest bidder wins.

```
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract SimpleAuction {
    address public highestBidder;
    uint public highestBid;

    function bid() public payable {
        require(msg.value > highestBid, "Bid too low");

        if (highestBid != 0) {
            payable(highestBidder).transfer(highestBid);
        }

        highestBidder = msg.sender;
        highestBid = msg.value;
    }
}
```

![image](https://github.com/user-attachments/assets/bb48a800-72fe-4cdd-a474-f1de238e6f04)

![image](https://github.com/user-attachments/assets/18eb0b0f-91a3-466d-86c8-eeffb33f5382)



