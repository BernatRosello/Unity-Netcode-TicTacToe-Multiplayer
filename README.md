# Unity Netcode TicTacToe Multiplayer
 
This branch's prupose is to test the UX of migrating a traditional NGO project, particularly one using the Relay Transport.

The necessary code has already been modified for you, you can checkout the changes in the GameManager.cs file (It will initially give out an error, don't worry this error is expected because the assembly reference to the transport is missing).

# Steps:

1. Add the package to the Unity project, it is currently hosted on the [OpenUPM registry](https://openupm.com/packages/com.bernatrosello.nearby-connections-transport/), this is the recommended method of installation. Though, you could also download it directly from [GitHub repository](https://github.com/BernatRosello/Unity-NearbyConnections-Transport/tree/upm). Following the installation steps described on either of those should get you up and running.

2. Change the build target to Android, if you don't have a preexisting Android-target Build Profile you can use the one provided in the Samples folder of the Nearby Connections Transport Package.
    - It is recommended you follow the latest Unity guidelines (pertaining to release 6000.2) for Android builds, meaning enabling the IL2CPP Scripting Backend, split APKs or AABs for distribution. Though these settings aren't necessary for the Package to function, it is recommended to improve performance and to make development easier.
    - This project already include Android Logcat for instance, which is HIGHLY recommended to debug your app be it Netcode functionality or otherwise.

3. Allow the depency package of External Dependecy Manager (EDM4U) to resolve the external dependencies required by the transport.
    - Enable Auto-Resolve
    - Enable Android Gradle Templates

4. Change the NetworkManager Transport over to the Nearby Connections Transport. This can be done by simply removing the reference to the current transport and selecting it from the drop-down menu for transport selection that shows up when None is referenced.
    - You should remove the Relay Transport component from the NetworkManager object.
    * You could also remove the Relay Transport Package, as well as all of Unity's Service Packages making the game completely offline.

5. Enable the checkboxes for Auto Advertise & Auto Approve Connection Request, as well as Auto Browse & Auto Send Connection Request. These settings will enable the sample to connect without needing to approve the connection manually , players just need to Start as Host and Client respectively to start a game.

6. To finish configuring it you will want to add the PermissionRequestDialog.prefab reference to the network manager, this is necessary for the user to be prompted of when the necessary permissions for execution of the transport haven't been granted "permanently" so they can change the permission settings for the app. You should also specify what Rect Transform the prefab should be instantiated under to be displayed correctly.
    - You can find a placeholder version of this prefab inside the package's Samples/PermissionDialogBox, though ideally you could modify it or create your own.

7. Finally, building & running the app should provide a functioning Tic Tac Toe sample with seamless local multiplayer.
