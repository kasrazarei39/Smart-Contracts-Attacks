# Self-Destruct Attack

This README provides an overview of a vulnerability and a solution within the context of the "EtherGame" smart contract. The vulnerability involves a self-destruct attack that can be executed by malicious actors to disrupt the game. The provided solution addresses this vulnerability.

## Vulnerability Description

The "EtherGame" contract is designed as a game where players deposit 1 Ether, and the goal is to be the 7th player to deposit and become the winner. Players can deposit only 1 Ether at a time, and the winner can claim all the Ether in the contract.

However, there is a critical vulnerability in the original "EtherGame" contract:

1. A player (e.g., Alice) deploys the "EtherGame" contract.
2. Players (e.g., Alice and Bob) decide to play and deposit 1 Ether each.
3. A malicious actor deploys the "Attack" contract, targeting the "EtherGame" contract.
4. The attacker calls the "Attack.attack" function, sending a significant amount of Ether (e.g., 5 Ether) to the "EtherGame" contract.

**What Happens:** The attacker's "Attack" contract executes the self-destruct operation on the "EtherGame" contract, destroying it and transferring the Ether balance of the "EtherGame" contract to the attacker. As a result, the game is disrupted, and no one can become the winner.

## Solution

To address the self-destruct attack vulnerability and ensure the integrity of the game, a modified version of the "EtherGame" contract is provided.

1. The `targetAmount` in the "EtherGame" contract is adjusted to a lower value (e.g., 3 Ether) to demonstrate a functional game for testing purposes.
2. In the `deposit` function, the player's deposited Ether is added to the contract's `balance`. Players can still deposit, and the game continues as long as the `balance` does not exceed the `targetAmount`.
3. The `claimReward` function allows the winner to claim the entire balance when they are identified.

By adjusting the `targetAmount` and ensuring that the game continues even if the `balance` does not reach the target, players can continue participating in the game without the risk of a self-destruct attack disrupting it.