## Contract

The `Vault` contract serves as a practical example to illustrate how data is organized and stored in Ethereum smart contracts' storage slots. It includes various data types and structures to showcase the efficient use of storage.

## Storage Organization

The `Vault` contract's storage is organized as follows:

- **Slot 0:** `count`, a `uint` with an initial value of 123.
- **Slot 1:** `u16`, `isTrue`, and `owner`, representing a `uint16`, a `bool`, and an `address`, respectively.
- **Slot 2:** `password`, a `bytes32` variable (private).
- **Slot 3, 4, 5:** An array of `bytes32` named `data`, with three elements.
- **Slot 6:** An array of `User` structs. The `User` struct contains a `uint` (id) and a `bytes32` (password).
- **Slot 7:** Reserved for future use (empty).
- **Mapping:** The `idToUser` mapping stores `User` structs.

## Constants

- The contract defines a constant `someConst` which is set to 123. Constants do not use storage slots.

## Functions

The `Vault` contract includes the following functions:

- **Constructor:** The constructor sets the initial `password` value.
- **addUser:** Adds a new user to the `users` array and updates the `idToUser` mapping.

## Utility Functions

Two utility functions are provided to demonstrate how to calculate storage locations:

- **getArrayLocation:** Calculates the storage location of an array element.
- **getMapLocation:** Calculates the storage location of a mapping entry.