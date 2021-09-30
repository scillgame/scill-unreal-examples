# Action RPG and Scill Unreal SDK

This example shows an implementation of the Scill Unreal SDK. It is based on the [ActionRPG](https://www.unrealengine.com/marketplace/en-US/product/action-rpg) example by Epic Games in the Unreal Marketplace. This example project is the result of the tutorial series giving a quick start to the usage of the Unreal SDK.

This document will quickly guide you through how to get the example running with your Scill Application and show the elements that were added to make it work with the Scill SDK.

![title.png](/ActionRPG/Documentation/title.png)

## Requirements

- [Scill Account](https://www.4players.io/4players-scill-engagement-toolkit/)
- Unreal Engine Version 4.26.2 or higher

## Starting the Example

To start you need to create a Scill Application in the [Admin Panel](https://admin.scill.4players.io). Create an App with Challenges, Battle Passes and Leaderboards according to the [Event Types](#used-event-types) that are used in the example.

Once done you can open the Project in the Unreal Editor. Here you need to open the BP_ScillGameMode and add the API Key of your Scill App to the API Key property of the Scill Client Backend Component.

![ScillClientBackendComponent.png](/ActionRPG/Documentation/ScillClientBackendComponent.png)

In the same manner change the UserId and ApplicationId properties on the Scill Client Component on the BP_ScillPlayerController class to a user id and the application id of your Scill App. 

![ScillClientComponent.png](/ActionRPG/Documentation/ScillClientComponent.png)

Afterwards you can start the game.

You can open the different menus for the Scill features using hotkeys:
- **C**: Personal Challenges - Lists all personal challenges for the current user. You can unlock, activate and claim according to the challenge's current type.
- **L**: Leaderboards - Lists the first leaderboard found in the Scill App. You can change your Name and Avatar here as well.
- **B**: Battle Passes - Lists the first found battle pass in the Scill App. You can unlock battle passes and claim battle pass levels here as well.

## Structure Overview

The main work of the project is done in the BP_ScillGameMode and BP_ScillPlayerController. All Scill-specific classes can be found in the **Blueprints/SCILL_Sample** folder.

In the **BP_ScillGameMode** we mostly only listen to game play events and keep track of them using instance variables or send them to the Scill Backend directly. You can see this is in the various "Receive Event" Functions. 

The **BP_ScillPlayerController** handles the creation of an access token on behalf of the player in the Begin Play Event and all functions and Events that are called here. Partly they serve as communication in a potential Server-Client game setup. Additionally the Player Controller starts to listen to Challenge Updates here. Lastly this Blueprint processes the Inputs of the player regarding the three types of Scill-related menues and opens or closes them accordingly.

This is already the game specific structure - take a look at the different Blueprint classes in the **Blueprints/SCILL_Sample** folder to learn more.

## Used Event Types

The Action RPG example sends the following events and metadata. Use the same event names and metadata in the configuration of your Scill App. If you want to have a detailed look at how exactly the sample sends events to Scill, open the BP_ScillGameMode and inspect the respective "Receive Event" functions.

- **kill-enemy**: used for each killed enemy. Sent at the end of a play session together with the **Amount** of enemies killed and the current session id.
- **use-item**: used whenever you use a potion or a skill with the respective **Item Names**: 
    - **health**: Health Potion
    - **mana**: Mana Potion
    - **combined**: Combined Potion  
    - **roll**: Roll Action (Triggered in-game with e.g. right-click)
    - **Combust**: Combust Skill
    - **Fire Ball**: Fire Ball Skill
    - **Fire Wave**: Fire Wave Skill
    - **Meteor Shower**: Meteor Shower Skill
- **achieve-score**: used to send the current wave progress. Each reached wave increases the **Score** by one.
- **destroy-item**: used to indicate how much souls were spent in the shop via the **Amount** property. **Item Id** is **souls**.
- **receive-damage**: **Amount** indicates how often the player has died until now.

All these are just used to give a rough idea of how to implement the Unreal SDK in a real game - but you can of course add as many other event names as you like.