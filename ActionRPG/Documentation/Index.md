# Action RPG and Scill Unreal SDK

This example shows an implementation of the Scill Unreal SDK. It is based on the [ActionRPG](https://www.unrealengine.com/marketplace/en-US/product/action-rpg) example by Epic Games in the Unreal Marketplace.

This document will quickly guide you through how to get the example running with your Scill Application and show the elements that were added to make it work with the Scill SDK.

## Requirements

- [Scill Account](https://www.4players.io/4players-scill-engagement-toolkit/)
- Unreal Engine Version 4.26.2 or higher

## Starting the Example

To start you need to create a Scill Application in the [Admin Panel](https://admin.scill.4players.io). Create an App with Challenges, Battle Passes and Leaderboards according to the [Event Types](#used-event-types) that are used in the example.

Once done you can open the Project in the Unreal Editor. Here you need to open the BP_ScillGameMode and add the API Key of your Scill App to the API Key property of the Scill Client Backend Component.

(ScillClientBackendComponent.png)[/ActionRPG/Documentation/ScillClientBackendComponent.png]

In the same manner change the UserId and ApplicationId properties on the Scill Client Component on the BP_ScillPlayerController class to a user id and the application id of your Scill App. 

(ScillClientComponent.png.png)[/ActionRPG/Documentation/ScillClientComponent.png.png]

Afterwards you can start the game.

You can open the different menus for the Scill features using hotkeys:
- **C**: Personal Challenges - Lists all personal challenges for the current user. You can unlock, activate and claim according to the challenge's current type.
- **L**: Leaderboards - Lists the first leaderboard found in the Scill App. You can change your Name and Avatar here as well.
- **B**: Battle Passes - Lists the first found battle pass in the Scill App. You can unlock battle passes and claim battle pass levels here as well.

## Structure Overview

The main work of the project is done in the BP_ScillGameMode and BP_ScillPlayerController. 

## Used Event Types

