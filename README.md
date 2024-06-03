# Dynamic Pawn Spawner in Unreal Engine 

## Video Demo
https://drive.google.com/file/d/1QjocDycM4S7aNfhd1j7r419ckN2pckSm/view?usp=drive_link

## Overview
This project implements a system in Unreal Engine using C++ that allows players to dynamically spawn and switch between different types of pawns based on input, utilizing a DataTable for managing pawn configurations. The project consists of four main parts: setting up a default pawn, configuring a DataTable and enum, implementing a custom player controller, and managing pawn attributes using a custom DataAsset.

## Table of Contents
1. [Setup](#setup)
2. [Part 1: Setting Up the Default Pawn](#part-1-setting-up-the-default-pawn)
3. [Part 2: Configuring the DataTable and Enum](#part-2-configuring-the-datatable-and-enum)
4. [Part 3: Implementing the Custom Player Controller](#part-3-implementing-the-custom-player-controller)
5. [Part 4: Pawn Attributes](#part-4-pawn-attributes)
6. [Demo](#demo)


## Setup
1. Clone the repository to your local machine.
2. Open the Unreal Engine project.
3. Build the project to compile the C++ code.


## Part-1 Setting up the Default Pawn

### Default Pawn Creation
- Created a class `AFirstPersonPaw`n derived from `APawn`.
- Excluded a visible player mesh but included a camera component for a first-person view.
- Implemented essential first-person movement controls using the Enhanced Input System, including forward/backward movement, strafing, and looking up/down.


## Part 2: Configuring the DataTable and Enum

### Enum Setup
- Created an Enum `EPawnType` with entries for different pawn types, such as Third Person and Top Down.
### DataTable Creation
- Created a DataTable `PawnDataTable` with columns for `EPawnType` and `PawnClass` (Class Reference).
- Populated the DataTable with at least two pawn types, each linked to a suitable subclass.


## Part 3: Implementing the Custom Player Controller

### Player Controller Class
- Created a custom player controller class `ADynamicPawnController`.
- Implemented logic to spawn and switch between pawns based on a key input (e.g., "P").
- Ensured only one active pawn is in play at any time by destroying any previously spawned pawn when a new one is spawned.


## Part 4: Pawn Attributes

### Base Pawn Class Creation
- Developed a base character class `ABaseCharacter` from which all specific pawn classes are derived.
- Ensured the base class is capable of movement and basic interaction.
### Custom DataAsset Setup
- Created a custom DataAsset class `UPawnAttributeAsset` with UPROPERTY attributes for various pawn characteristics like Speed, Health, and JumpHeight.
- Added a reference to this DataAsset in `ABaseCharacter`.
### DataAsset Creation for Each Pawn Type
- Created instances of `UPawnAttributeAsset` for each pawn type in the Unreal Editor.
- Populated each DataAsset with values for Speed, Health, JumpHeight, etc.
- In the derived pawn classes, added a reference to the corresponding `UPawnAttributeAsset` instance.
### Displaying Pawn Attributes via BP Implementable Event
- Created a Blueprint Implementable Event `DisplayAttributes` in the `PlayerController` class.
- Triggered this event when a pawn is possessed, passing the DataAsset as a parameter.
- Implemented the event in Blueprint to print the pawn's attributes using the Print Screen node.


## Demo
- https://drive.google.com/file/d/1QjocDycM4S7aNfhd1j7r419ckN2pckSm/view?usp=drive_link
