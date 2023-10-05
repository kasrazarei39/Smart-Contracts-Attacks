# Reentrancy Attack and Solutions

This section of the repository focuses on understanding and mitigating the Reentrancy Attack, a common vulnerability in Ethereum smart contracts. We provide an overview of the attack, a vulnerable contract example, and two solutions to secure your contracts against this threat.



## Reentrancy Attack

The Reentrancy Attack is a type of vulnerability that allows an attacker to repeatedly call a vulnerable contract's function, potentially draining the contract's balance. The attack is possible when a contract interacts with external contracts, such as sending Ether or calling external functions, without properly controlling the order of execution. Attackers can take advantage of this by recursively calling the vulnerable contract, reentering it before the previous execution completes.



## Vulnerable Contract

In the vulnerable contract scenario, a contract called `Bank` is susceptible to a Reentrancy Attack. This contract allows users to deposit and withdraw funds from their accounts. The vulnerability arises in the `withdraw` function, where the contract transfers Ether to the caller without setting the user's balance to zero first.



## Solutions

To protect your contracts from Reentrancy Attacks, we recommend two solutions:

### Solution 1

This solution involves modifying the `withdraw` function to set the user's balance to zero before transferring funds. This prevents any reentrant calls from reentering the `withdraw` function and draining the contract's balance.

### Solution 2

The second solution involves using the OpenZeppelin `ReentrancyGuard` library, which adds an extra layer of security to your contract. By applying this library, you can prevent reentrant calls to the vulnerable function, making your contract resistant to Reentrancy Attacks.