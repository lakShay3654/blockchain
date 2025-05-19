## que4 :- Write a contract where people can donate Ether and the top 3 donors are tracked.

```
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract TopDonors {
    struct Donor {
        address donorAddress;
        uint amount;
    }
    
    Donor[3] public topDonors;
    
    function donate() public payable {
        require(msg.value > 0, "Donation amount must be greater than 0");
        
        // Check if donor already exists in top 3
        for(uint i = 0; i < 3; i++) {
            if(topDonors[i].donorAddress == msg.sender) {
                topDonors[i].amount += msg.value;
                sortDonors();
                return;
            }
        }
        
        // If new donor has more than the smallest in top 3
        if(msg.value > topDonors[2].amount) {
            topDonors[2] = Donor(msg.sender, msg.value);
            sortDonors();
        }
    }
    
    function sortDonors() private {
        for(uint i = 1; i < 3; i++) {
            for(uint j = 0; j < i; j++) {
                if(topDonors[i].amount > topDonors[j].amount) {
                    Donor memory temp = topDonors[i];
                    topDonors[i] = topDonors[j];
                    topDonors[j] = temp;
                }
            }
        }
    }
}
```
![Screenshot 2025-05-19 135344](https://github.com/user-attachments/assets/43e0aff4-62e8-4806-b425-eb91509566ff)

![Screenshot 2025-05-19 135415](https://github.com/user-attachments/assets/8d0200ff-973c-44aa-85b2-03ab39740091)


