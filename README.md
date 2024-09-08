# 007-Solidity-Enum

Enum are one way to create a user defined type in solidity
```solidity
//SPDX-License-Identifier: MIT
pragma solidity 0.8.24;
contract enumExample{
    enum statues {ON,OFF }
    statues public lightOn = statues.ON;
    statues public lightOff = statues.OFF;
    }
```
Error enum with no members not allow
```solidity
//SPDX-License-Identifier: MIT
pragma solidity 0.8.24;
contract enumExample{
    enum statues{} //Error enum with no members not allow
    }
```
```solidity
//SPDX-License-Identifier: MIT
pragma solidity 0.8.24;
contract enumExample{
    enum shipMent{notFound,Approved,Rejected}
    shipMent status;
    shipMent DefaultStatues = shipMent.notFound;

    function setToApproved() public{
        status = shipMent.Approved;
    }

    function setToRejected() public{
        status = shipMent.Rejected;
    }
    function getChoice()public view returns(shipMent){
        return status;
    }
    function getDefaultStatus() public view returns(shipMent){
        return DefaultStatues;
    }
    function getSmallestValue() public pure returns(shipMent){
        return type(shipMent).min;
    }   
    function getLargestValue() public pure returns(shipMent){
        return type(shipMent).max;
    } 

}
```
Solidity document Example
```solidity
// SPDX-License-Identifier: GPL-3.0
pragma solidity ^0.8.8;

contract test {
    enum ActionChoices { GoLeft, GoRight, GoStraight, SitStill }
    ActionChoices choice;
    ActionChoices constant defaultChoice = ActionChoices.GoStraight;

    function setGoStraight() public {
        choice = ActionChoices.GoStraight;
    }


    function getChoice() public view returns (ActionChoices) {
        return choice;
    }

    function getDefaultChoice() public pure returns (uint) {
        return uint(defaultChoice);
    }

    function getLargestValue() public pure returns (ActionChoices) {
        return type(ActionChoices).max;
    }

    function getSmallestValue() public pure returns (ActionChoices) {
        return type(ActionChoices).min;
    }
}
```
Example from geeks for geeks
```solidity
// Solidity program to demonstrate
// how to use 'enumerator'
pragma solidity ^0.5.0;
// Creating a contract
contract Types {
// Creating an enumerator
 enum week_days
 {
 Monday,
 Tuesday,
 Wednesday,
 Thursday,
 Friday,
 Saturday,
 Sunday
 }
// Declaring variables of
 // type enumerator
 week_days week;
 
 week_days choice;
// Setting a default value
 week_days constant default_value
 = week_days.Sunday;
 
 // Defining a function to
 // set value of choice
 function set_value() public {
 choice = week_days.Thursday;
 }
// Defining a function to
 // return value of choice
 function get_choice(
 ) public view returns (week_days) {
 return choice;
 }
 
 // Defining function to
 // return default value
 function getdefaultvalue(
 ) public pure returns(week_days) {
  return default_value;
 }
}
```
Juice size example
```solidity
// SPDX-License-Identifier: GPL-3.0
pragma solidity ^0.8.0;
contract test {
// predefined value enum EnumName
enum FreshJuiceSize{ SMALL, MEDIUM, LARGE }
//Enum variable
FreshJuiceSize choice;
// access default choice
FreshJuiceSize constant defaultChoice = FreshJuiceSize.MEDIUM;
function setLarge() public {
choice = FreshJuiceSize.LARGE;
}
function getChoice() public view returns (FreshJuiceSize) {
return choice;
}
function getDefaultChoice() public pure returns (uint) {
return uint(defaultChoice);
}
}
```
Shipped Status
```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;
contract Enum {
//enum representing shipping status
enum Status {Pending,Shipped, Accepted, Rejected,Canceled}
//enum variable, Default value  pending =0
Status public status;
function getChoice() public view returns (Status) {
return status;
}
// Update status by passing uint into input
function set(Status _status) public {
status = _status;
}
//You can update to a specific enum like this
function cancel() public {
status = Status.Canceled;
}
// delete resets the enum to it's first value, 0
function reset() public {
delete status;
}
}
```
Move between enum elements
```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;
contract Enum {
enum Status {Pending,Shipped, Accepted, Rejected,Canceled}
Status public status;
function nextChoice() public  {
status=Status(uint(status)+1);
}
}
```
Example from stack exchange
```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

// Lets see Enums which are often used for state machine like this
enum State { Created, Locked, Inactive };

// post this a variable can be Declared like this
State public state;

// Initializing the state can be done like this
state = State.Created;

// It is important to note that enums can be explicitly converted to ints like this
uint createdState = uint(State.Locked);
```
Enum & mapping
```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;
contract Enum {
enum Status {Pending,Shipped, Accepted, Rejected,Canceled}
mapping(uint=> Status) enumMappnig;
}
```
Enum & struct
```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;
contract Enum {
enum Status {Pending,Shipped, Accepted, Rejected,Canceled}
struct enumStruct{
Status _status;
}
}
```
Enum Declaration Outside a Contract or Library
When you declare an enum outside a contract or library, it becomes a globally accessible type for any contract or library within that file. Here's an example:
```solidity


//SPDX-License-Identifier:MIT
pragma solidity ^0.8.24;
// Declare the enum at the file level
enum Status { Pending, Shipped, Delivered, Cancelled }

contract Order {
    Status public orderStatus;

    constructor() {
        orderStatus = Status.Pending; // Default status is "Pending"
    }

    function shipOrder() public {
        orderStatus = Status.Shipped; // Change status to "Shipped"
    }

    function cancelOrder() public {
        orderStatus = Status.Cancelled; // Change status to "Cancelled"
    }

    function getStatus() public view returns (Status) {
        return orderStatus;
    }
}

contract Delivery {
    Status public deliveryStatus;

    constructor() {
        deliveryStatus = Status.Delivered; // Default status is "Delivered"
    }

    function updateStatus(Status _status) public {
        deliveryStatus = _status;
    }
}
```






