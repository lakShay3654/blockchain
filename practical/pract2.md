## que.2 Write a contract that manages a list of student records (name, roll number). Allow adding and retrieving student data.

```
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract StudentRecords {
    struct Student {
        string name;
        uint rollNumber;
    }
    
    Student[] public students;
    mapping(uint => bool) public rollNumberExists;
    
    function addStudent(string memory _name, uint _rollNumber) public {
        require(!rollNumberExists[_rollNumber], "Roll number already exists");
        students.push(Student(_name, _rollNumber));
        rollNumberExists[_rollNumber] = true;
    }
    
    function getStudent(uint _index) public view returns (string memory, uint) {
        require(_index < students.length, "Invalid index");
        return (students[_index].name, students[_index].rollNumber);
    }
    
    function getStudentCount() public view returns (uint) {
        return students.length;
    }
}
```
![Screenshot 2025-05-19 134520](https://github.com/user-attachments/assets/ace41b36-6ffd-4ff8-8d9b-3da5ebbe7da9)

![image](https://github.com/user-attachments/assets/9a057d67-d522-4dcf-9f38-c618033704eb)




