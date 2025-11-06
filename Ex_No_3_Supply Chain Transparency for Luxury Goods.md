# Aim:
To develop a smart contract that tracks the supply chain of luxury goods, ensuring authenticity.
# Algorithm:
The manufacturer records product creation details on-chain.


The product moves through different supply chain checkpoints.


The ownership of the product can be transferred securely.


Buyers can verify the product’s authenticity.


# Program:
## Name : Koppala Naveen
## Register Number : 212223100023
```
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

contract LuxurySupplyChain {
    struct Product {
        string name;
        address currentOwner;
        bool verified;
    }

    mapping(uint256 => Product) public products;

    event ProductRegistered(uint256 productId, string name);
    event OwnershipTransferred(uint256 productId, address newOwner);

    function registerProduct(uint256 productId, string memory name) public {
        require(products[productId].currentOwner == address(0), "Product already registered");
        products[productId] = Product(name, msg.sender, true);
        emit ProductRegistered(productId, name);
    }

    function transferOwnership(uint256 productId, address newOwner) public {
        require(products[productId].currentOwner == msg.sender, "Not the owner");
        products[productId].currentOwner = newOwner;
        emit OwnershipTransferred(productId, newOwner);
    }

    function verifyProduct(uint256 productId) public view returns (string memory, address, bool) {
        Product memory p = products[productId];
        return (p.name, p.currentOwner, p.verified);
    }
}
```
# Expected Output:
A luxury good (e.g., a Rolex watch) is registered on-chain.


Ownership is transferred at every checkpoint.


Buyers can check the authenticity before purchasing.

# Output : 

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/651093f6-680a-4aac-a5bd-cdd297aea0ff" />

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/c1a3260a-4bc6-40ad-aeb0-b746ad25dd16" />

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/7a8aebaf-37ec-49bc-8251-1d5bdb257ce8" />

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/ed1eadb8-4301-41c6-a10f-0a66181bce7e" />


# High-Level Overview:
Helps prevent counterfeit luxury goods.


Teaches real-world supply chain use cases.


# RESULT : 

Thus, the execution of the suplly chain Transpanrency for Luxury Goods has executed successfully.
