# Finding Visual Studio Version
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
  # Output the display name and installation version of the latest Visual Studio
  Write-Host "The highest version of Visual Studio installed is:"
  Write-Host "DisplayName: $($latestVS.DisplayName)"
  Write-Host "Version: $($latestVS.InstallationVersion)"
}
else {
  Write-Warning "No Visual Studio instances found on this machine."
}
```

## Get-VSSetupInstance -Prerelease:$false | Select-VSSetupInstance -Latest
![image](https://github.com/user-attachments/assets/d29f9c35-8867-46eb-915d-865b176f20c4)

## Get-VSSetupInstance -Prerelease:$true | Select-VSSetupInstance -Latest
![image](https://github.com/user-attachments/assets/b35617b0-0eeb-4da7-baf7-7035e66650f0)
