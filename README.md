
UTD CAMPUS LENS

AR-based indoor navigation app using Unity. It uses Unity's Universal Render Pipeline (URP), AR Foundation, and NavMesh. The setup involves Android support, implementing depth API features, and creating navigation paths.



## Deployment


Step-by-Step Guide
1. Unity Project Setup
Start a New Project: Use the URP template.

Install Required Packages:

Go to 
```
  File > Build Settings and switch the platform to Android.
```
```
  Open Edit > Project Settings > Player Settings and set:
Remove default icons.
```

Remove default icons.
Adjust description and input handling.
Install the XR Plugin Management and enable ARCore for Android.
Install 
```
AI Navigation
```
 via the Package Manager (optional to update).


Adjust Rendering Settings:

Replace the default graphics asset with 
```
Mobile URP Asset.
```
Adjust Quality Settings to Mobile.
Setup AR Settings:

Add the AR Occlusion Manager component to the main camera.
Set Depth Mode to 
```
Best
```
 and enable Environmental Occlusion.

 2. Scene Preparation
Basic Setup:

Delete "Main Camera"
 and "Global Volume".
Right-click in the hierarchy and create an XR Origin under XR.
Add AR Session and Image Tracking:

Add an AR Session object.
Add an AR Tracked Image Manager to the XR Origin.
Create a XR Reference Image Library in a 
```
new Assets > Image Tracking folder.
```
Add your reference image (e.g., Unity logo) with specified dimensions (e.g., 0.1m).
Prefabs and Materials:

Create folders for Scripts, Materials, and Prefabs.
Design a basic navigation environment:
Floor (Plane with material).
Walls and a target (Cube objects for obstacles and goals).
Assign materials:
Use Transparent Material for walls.
Create a Line Material for navigation paths.
Bake Navigation Mesh:

Add a NavMeshSurface to the floor.
Configure a small agent radius for tight navigation.

3. Code Implementation
Create Scripts:

Create and attach scripts:
```
NavigationTarget.cs: For marking navigation targets.
IndoorNav.cs: For managing AR tracking and navigation logic.
```
IndoorNav.cs Breakdown:
Components:
Reference AR Tracked Image Manager.
Manage navigation targets and NavMesh surfaces.
On Trackable Changes:
Instantiate prefabs on detecting a tracked image.
Update positions and rotations dynamically.
Path Updates:
Calculate paths using NavMeshPath.
Use a LineRenderer to visually render paths.
Integration:

Attach IndoorNav.cs to a central IndoorNavigation object.
Assign required references:
Player (Main Camera), Tracked Image Manager, Line Renderer, and Prefab.

4. Testing
Simulate AR:

Install XR Simulation to test in the Unity Editor.
Press Play and verify:
Image tracking spawns the prefab.
Navigation paths update as you move the camera.
Deploy to Android:

Go to 
```
File > Build Settings > Android.
```
Attach your device and click Build and Run.
Test AR functionality on the smartphone.

## Acknowledgements

 - [Unity NavMesh](https://docs.unity3d.com/Packages/com.unity.ai.navigation@2.0/manual/CreateNavMesh.html)
 - [AR Foundation Occlusion](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@6.0/manual/features/occlusion.html)
 - [AR Core supported devices](https://developers.google.com/ar/devices)
  - [Github Repository](https://github.com/FireDragonGameStudio/ARIndoorNavigation-Unity6)
   - [NAVIGATION TUTORIAL](https://www.youtube.com/watch?v=G3khfWQUa78&t=903s)
    
