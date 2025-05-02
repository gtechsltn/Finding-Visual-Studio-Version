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
