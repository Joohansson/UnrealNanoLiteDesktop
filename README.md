# Unreal Nano Desktop

## Prereqs UE
1. Download and install the latest [Unreal Engine](https://www.unrealengine.com/en-US/download) (Publishing license)

## Build Instructions
1. Clone this repo
2. Right click on UnrealNanoLight.uproject and "switch unreal engine version". Select the UE source you just installed (should be listed)
3. Open UnrealNanoLight.sln in Visual Studio or UnrealNanoLight.xcodeproj xcode (Windows Vs. Mac)
4. Make sure "Development editor" and "Win64" is selected in the dropdowns (Project/Scheme/Edit scheme in xcode)
5. Right click on the Games/UnrealNanoLight in the solution explorer and Build (this will build the Nano plugin)
6. "Debug/Start without debugging" to open the editor (Product -> Run in xcode) or close VS and run the UnrealNanoLight.uproject (should launch in correct editor). Step 6 is not needed if only packaging on Windows. But on a Mac you need to package from Unreal Engine

## Package Instructions - Windows without using the Engine which saves time
1. Copy UNREALNANOLIGHT_89E22627467FD0611C2E46B115F0F6FD.ulp2 to UnrealEngine-release\Engine\Programs\UnrealFrontend\Profiles
2. Launch UnrealEngine-release\Engine\Binaries\Win64\UnrealFrontend.exe
3. Make sure the correct platforms are selected for example windowsNoEditor or LinuxNoEditor
4. Add the project path at the top
5. Run the profile

## Package from the editor
1. File/Package project/Windows