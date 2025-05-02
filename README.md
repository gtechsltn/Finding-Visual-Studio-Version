# Finding Visual Studio Version
+ C:\Program Files\Microsoft Visual Studio\2022\Enterprise\Common7\IDE\devenv.exe
+ C:\Program Files\Microsoft Visual Studio\2022\Enterprise\MSBuild\Current\Bin\MSBuild.exe

## VSSetupCheck.ps1
```
# Check if the VSSetup module is available, if not, install it
if (-not (Get-Module -Name VSSetup -ListAvailable)) {
    Install-Module -Name VSSetup -Scope CurrentUser -Force
}

# Import the VSSetup module
Import-Module VSSetup

# Get the latest installed Visual Studio instance
$latestVS = Get-VSSetupInstance -Prerelease:$false | Select-VSSetupInstance -Latest

# Check if any Visual Studio instance was found
if ($latestVS) {
    # Output the display name, installation version, and installation path of the latest Visual Studio
    Write-Host "The highest version of Visual Studio installed is:"
    Write-Host "DisplayName: $($latestVS.DisplayName)"
    Write-Host "Version: $($latestVS.InstallationVersion)"
    Write-Host "Physical Path: $($latestVS.InstallationPath)"
} else {
    Write-Warning "No Visual Studio instances found on this machine."
}
```

## Output
```
C:\Program Files\Microsoft Visual Studio\2022\Enterprise\Common7\IDE\devenv.exe
C:\Program Files\Microsoft Visual Studio\2022\Enterprise\MSBuild\Current\Bin\MSBuild.exe
```

## Get-VSSetupInstance -Prerelease:$false | Select-VSSetupInstance -Latest
![image](https://github.com/user-attachments/assets/d29f9c35-8867-46eb-915d-865b176f20c4)

```
The highest version of Visual Studio installed is:
DisplayName: Visual Studio Professional 2019
Version: 16.11.34407.143
Physical Path: C:\Program Files (x86)\Microsoft Visual Studio\2019\Professional
```

## Get-VSSetupInstance -Prerelease:$true | Select-VSSetupInstance -Latest
![image](https://github.com/user-attachments/assets/b35617b0-0eeb-4da7-baf7-7035e66650f0)

```
The highest version of Visual Studio installed is:
DisplayName: Visual Studio Enterprise 2022
Version: 17.13.35507.96
Physical Path: C:\Program Files\Microsoft Visual Studio\2022\Enterprise
```
