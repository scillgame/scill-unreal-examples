# SCILL Blueprint Example

This blueprint-only example project showcases the usage and display of the core SCILL functionality using a sample Application. The sample application can also be interacted with using the [SCILL Playground](https://playground.scillgame.com/). 

![BattlePass as displayed in the Sample App](Documentation/BattlePass.png)

## Prerequisites

To run this example project, the SCILL Unreal SDK has to be installed either to your engine's or into your project's Plugin directory. Please take a look at this guide on installing the SCILL plugin: [https://developers.4players.io/scill/sdks/unreal/#installing-the-plugin](https://developers.4players.io/scill/sdks/unreal/#installing-the-plugin).

## Initialization

The base SCILL setup is implemented as seen in the documentation on [https://developers.4players.io/scill/sdks/unreal/#quick-start](https://developers.4players.io/scill/sdks/unreal/#quick-start):

- The Scill Client Component is placed on the ```BP_ScillPlayerController```. The Request for generating the Access Token and the logic for sending events is placed in the PlayerController. Additionally, the User Data will be initialized with a name based on the User Id and a random Avatar Icon from a list of icons.
- The Scill Client Backend Component is placed on the ```BP_ScillExampleGameMode```.
- The ```BP_ScillGameInstance``` contains references to the User Id and the Access Token.

## UI
All UI widgets can be found in ```_ScillExample/UI``` directory.
The root widget ```WBP_Menu``` contains the three main widgets for displaying the Application's
SCILL Data:
- The ```WBP_ChallengeList``` displays Personal Challenges, ordered by the available categories. The blueprint requests
the challenge data from the SCILL servers and forwards the response data to the Widgets ```WBP_ChallengeCategory``` for displaying categories and ```WBP_Challenge_Personal``` for displaying single challenges. The Widget Blueprints can be found in the ```Elements/Challenges``` directory.
- The ```WBP_BattlePassList``` displays all available and unlockable Battle Passes. When pressing the "View" Button, the ```WBP_BattlePass_DetailView``` renders all information contained in the selected battle pass, using Child Widgets contained in the ```Elements/BPs``` directory.
- The ```WBP_Leaderboard``` displays a single leaderboard, using the leaderboard id entered in the data asset ```DA_LeaderboardSettings```, located under ```UI/Data/Leaderboards```.
The example shows how to switch between pages, color leaderboard entries based on rank and loading avatar icons using SCILL User Data. 

## Environment

The player can find interactable elements in the environment for accomplishing all battle pass levels and personal challenges. Actor Blueprints for interactable elements are located in the ```_ScillExample/Environment``` directory. 
Interactions with those actors will trigger the player controller to send events to the SCILL backend, updating progress on challenges, battle passes and leaderboards in realtime.

## Further information

A great way to dive even deeper into the SCILL Unreal SDK is the SCILL developers documentation at [https://developers.4players.io/scill/sdks/unreal/](https://developers.4players.io/scill/sdks/unreal/) or the video tutorials series by Stephen Sommerfeld [![Image Thumbnail for the SCILL Unreal SDK Tutorial Video Playlist](https://img.youtube.com/vi/6oLQEylIhMg/0.jpg)](https://www.youtube.com/watch?v=6oLQEylIhMg&list=PL6Hjbq3t2BfYm7Z51Pi5HkK2Z1n042dWK)