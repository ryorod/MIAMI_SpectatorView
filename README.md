# The Mixed Reality Interface for MIAMI (Spectator View QR ver.)

The main repository of **MIAMI** is [here](https://github.com/ryorod/MIAMI).

---

Tested on system requirements below.

- Windows 11 Dev (OS build 22499.1010)
  - Visual Studio 2019 (16.9.31229.75)
  - Windows SDK 10.0.19041.0
  - Unity 2019.4.26f1
  - MRTK 2.6.1
  - [Spectator View master branch](https://github.com/microsoft/MixedReality-SpectatorView/tree/master) (updated from v1.1.0 but not an official release)
- Hololens 2 (OS build 10.0.19041.1161)
- macOS Big Sur (11.6.1)
  - Xcode 12.5.1
- iPadOS 14.8.1

---

### What I did to create a Spectator View (QR ver.) app with my own project

1. Clone [MixedReality-SpectatorView](https://github.com/microsoft/MixedReality-SpectatorView). `git clone https://github.com/microsoft/MixedReality-SpectatorView.git`
2. Move to the cloned folder and run `git submodule update --init --recursive`.
3. Run `tools/Scripts/SetupRepository.bat` for the QR code plugin.
4. Add MRTK in `/samples/SpectatorView.Example.Unity/Packages/manifest.json`.  
 ![image](https://user-images.githubusercontent.com/47845995/153886853-14a70d66-7e41-4519-a010-88ef57c69238.jpg)
5. Open the sample project `/samples/SpectatorView.Example.Unity` with Unity 2019.4.
6. Open the Package Manager and update the following packages to 4.x.x.  
 `AR Foundation`  
 `ARCore XR Plugin`  
 `ARKit XR Plugin`
7. In  
 ![image](https://user-images.githubusercontent.com/47845995/153879561-15d1cb59-23f7-4490-b90a-0807e5113ddb.jpg)
 replace the functions as below to resolve errors (which might be done automatically).  
 ![image](https://user-images.githubusercontent.com/47845995/153879761-0a4f8c3f-2800-4832-ae01-1fa9be78c1f5.jpg)
8. Enable AR functions for Hololens and iOS in Project Settings as below.  
 ![image](https://user-images.githubusercontent.com/47845995/153881161-cf24a870-6c7b-45a7-987b-ecd5296cc101.jpg)  
 ![image](https://user-images.githubusercontent.com/47845995/153881362-295d7fb7-cae4-4779-8eff-2e913ddcff01.jpg)
9. Open `Scenes/SpectatorView.HoloLens` and add MRTK assets.  
 ![image](https://user-images.githubusercontent.com/47845995/153882319-1e4c0f1a-0abc-4e6a-a396-376a370d566a.jpg)
10. Under `Broadcasted Content`, delete the default objects and add your own ones.
11. Press `Update All Asset Caches` in `Spectator View` tab.
12. Press the `HoloLens` button on the Platform Switcher attached to Spectator View in the Unity inspector.
13. Build the scene as below.  
 ![image](https://user-images.githubusercontent.com/47845995/153885189-d5262647-1087-445b-a520-f0cdd5c3f13f.jpg)
14. Open the `.sln` file with Visual Studio 2019 and deploy the app to Hololens.
15. Open `Packages/com.microsoft.mixedreality.spectatorview/SpectatorView/Scenes/SpectatorView.ARFoundation.Spectator`.
16. Press the `iOS` button on the Platform Switcher attached to Spectator View in the Unity inspector.
17. Build the scene as below.  
 ![image](https://user-images.githubusercontent.com/47845995/153888072-907238df-0629-4570-915d-5f82bdf31c83.jpg)
18. Copy the created folder to a Mac PC. From now on, all operations have to be done on Mac.
19. Install CocoaPods if not yet.
20. Run `pod install --repo-update` inside the folder.
21. Run `chmod 755 ./MapFileParser.sh`.
22. Open `Unity-iPhone.xcworkspace`.
23. Set `Signing` in `Unity-iPhone`.
24. Add the `Azure Spatial Anchor` framework downloaded by CocoaPods from `General/Framework and Libraries` in `UnityFramework`.  
 ![image](https://user-images.githubusercontent.com/47845995/153893751-79df4002-6615-41a8-9a72-2afa933b503c.jpg)  
 Select `Pods/AzureSpatialAnchors/bin/frameworks/AzureSpatialAnchors.framework`.  
 ![image](https://user-images.githubusercontent.com/47845995/153893954-4ca11e65-6c4e-4da5-9533-465c42e054a2.jpg)
25. Build and run it on iPad.

---

references:  
https://akihiro-document.azurewebsites.net/post/hololens2_spectatorview2019.4/  
https://microsoft.github.io/MixedReality-SpectatorView/doc/SpectatorView.Setup.html  
https://qiita.com/Futo_Horio/items/c8fe6b99f5bdc0dd72ac
