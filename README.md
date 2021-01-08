# Unreal Nano Lite for Desktop

## Prereqs UE
1. Download and install [Unreal Engine](https://www.unrealengine.com/en-US/download) (Publishing license)
2. Currently tested and developed on Unreal Engine 4.26. Not backward compatible but hopefully forward with little effort.

## Build Instructions
1. Clone this repo
2. Right click on UnrealNanoLite.uproject and "switch unreal engine version". Select the UE source you just installed (should be listed)
3. If Mac: Right click on UnrealNanoLite.uproject and "Generate Xcode Project" (Check the troubleshoot section further down)
4. Open UnrealNanoLite.sln in Visual Studio or UnrealNanoLite.xcodeproj xcode (Windows Vs. Mac)
5. Make sure "Development editor" and "Win64" is selected in the dropdowns (Product/Scheme/Edit scheme in xcode)
6. Right click on the Games/UnrealNanoLite in the solution explorer and Build (Windows) or Product/Build (Mac) (this will build the Nano plugin)
7. "Debug/Start without debugging" to open the editor (Windows) or Product -> Run in xcode (Mac) or close VS and run the UnrealNanoLite.uproject (should launch in correct editor). Step 6 is not needed if only packaging on Windows. But on a Mac you need to package from Unreal Engine

## Package Instructions - Windows without using the Engine which saves time
1. Copy UNREALNANOLIGHT_89E22627467FD0611C2E46B115F0F6FD.ulp2 to UnrealEngine-release\Engine\Programs\UnrealFrontend\Profiles
2. Launch UnrealEngine-release\Engine\Binaries\Win64\UnrealFrontend.exe
3. Make sure the correct platforms are selected for example windowsNoEditor or LinuxNoEditor
4. Add the project path at the top
5. Run the profile

## Package from the editor
1. File/Package project/Windows

## Troubleshooting on Mac
Could be permission bugs when using UE4.26. First when generating xcode project files and then when building inside xcode. One solution for when generating xcode files fails is to press arrow up key in the terminal to get latest command and put "sudo" in front of the command. Another way is to run this (given these are the files it complains about). Not sure of chmod is needed.
Replace "user" with your username (maybe also the group "staff").

```
sudo chown user:staff "/Users/Shared/Epic Games/UE_4.26/Engine/Source/Programs/DotNETCommon/DotNETUtilities/obj/Development/DotNETUtilities.dll"
sudo chown user:staff "/Users/Shared/Epic Games/UE_4.26/Engine/Source/Programs/DotNETCommon/DotNETUtilities/obj/Development/DotNETUtilities.pdb"
sudo chown user:staff "/Users/Shared/Epic Games/UE_4.26/Engine/Source/Programs/DotNETCommon/DotNETUtilities/obj/Development/DotNETUtilities.csproj.FilesWrittenAbsolute.txt"
sudo chmod 777 "/Users/Shared/Epic Games/UE_4.26/Engine/Source/Programs/DotNETCommon/DotNETUtilities/obj/Development/DotNETUtilities.dll"
sudo chmod 777 "/Users/Shared/Epic Games/UE_4.26/Engine/Source/Programs/DotNETCommon/DotNETUtilities/obj/Development/DotNETUtilities.pdb"
sudo chmod 777 "/Users/Shared/Epic Games/UE_4.26/Engine/Source/Programs/DotNETCommon/DotNETUtilities/obj/Development/DotNETUtilities.csproj.FilesWrittenAbsolute.txt"
```

It's also likely you will get a similar permission error when building the game in xcode (different file). This should work:

```
sudo chown user:staff "/Users/Shared/Epic Games/UE_4.26/Engine/Source/Programs/UnrealBuildTool/obj/Development/UnrealBuildTool.csproj.FilesWrittenAbsolute.txt"
sudo chmod 777 "/Users/Shared/Epic Games/UE_4.26/Engine/Source/Programs/UnrealBuildTool/obj/Development/UnrealBuildTool.csproj.FilesWrittenAbsolute.txt"
```