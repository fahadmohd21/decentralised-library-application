# decentralised-library-application
// SPDX-License-Identifier: MIT<br>
 pragma solidity ^ 0.8.0;<br>
contract libraryapplication{<br>
    address public contractOwner;<br>
    constructor() {<br>
        contractOwner=msg.sender;
    }
    modifier onlyOwner(){<br>
        require(msg.sender==contractOwner);
        _;
    }
    struct book{<br>
        uint price;
        uint id;
        string name;
        string author;
    }
    mapping(uint=>book) public books;<br>
    function addBook(
        uint _price,
        uint _id,
        string memory _name,
        string memory _author
     ) <br>public onlyOwner {<br>
        books[_id].name=_name;
        books[_id].price=_price;
        books[_id].author=_author;
     }<br>
     function queryByBookById(uint _id)<br>
     public view returns (
        string memory name,
        string memory author,
        uint price
        )
        <br>{
            return (<br>
                books[_id].name,
                books[_id].author,
                books[_id].price
            );<br>
        }<br>
     }

