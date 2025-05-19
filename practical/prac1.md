## que.1 Create a voting system with multiple candidates. Each address can vote only once.

```
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract VotingSystem {
    struct Candidate {
        string name;
        uint voteCount;
    }
    
    Candidate[] public candidates;
    mapping(address => bool) public hasVoted;
    address public owner;
    
    constructor(string[] memory _candidateNames) {
        owner = msg.sender;
        for(uint i = 0; i < _candidateNames.length; i++) {
            candidates.push(Candidate({
                name: _candidateNames[i],
                voteCount: 0
            }));
        }
    }
    
    function vote(uint _candidateIndex) public {
        require(!hasVoted[msg.sender], "You have already voted");
        require(_candidateIndex < candidates.length, "Invalid candidate");
        
        candidates[_candidateIndex].voteCount++;
        hasVoted[msg.sender] = true;
    }
    
    function getWinner() public view returns (string memory) {
        uint winningVoteCount = 0;
        uint winningIndex = 0;
        
        for(uint i = 0; i < candidates.length; i++) {
            if(candidates[i].voteCount > winningVoteCount) {
                winningVoteCount = candidates[i].voteCount;
                winningIndex = i;
            }
        }
        
        return candidates[winningIndex].name;
    }
}
```

![1](https://github.com/user-attachments/assets/1d03d4c0-573f-4e95-8e36-049e8ad6268f)

![2](https://github.com/user-attachments/assets/30d087cd-6712-4b3b-bd87-634f348103f5)


