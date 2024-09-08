# 007-Solidity-Enum
They are explicitly convertible to and from all integer types but implicit conversion is not allowed.
Enums are value type comprising a pre-defined list of constant values
Constant values with an enum can be explicity converted to integer
Enums require at least one number
Enums cannot have more than 256 members
You do not need to end the enum declaration with a semicolon. The compiler uses the semicolon ; and curly brackets {} to determine the scope of the code
Using type(name of enum).min get the smallest value
Using type(name of enum).max get the largest value
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
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




