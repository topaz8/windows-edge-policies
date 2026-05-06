# windows-edge-policies

Collection of Microsoft Edge policies implemented as Windows Registry files.

This repository hosts my conversion of [Microsoft-Edge-Policies](https://github.com/TommyTran732/Microsoft-Edge-Policies) into registry format, and my own personal policy.

You can learn what the registry keys mean, their options, and how to define them [here](https://learn.microsoft.com/en-us/DeployEdge/microsoft-edge-policies).

## Before you begin
Make sure that you back up your registry. To do that open Powershell as Administrator and run:
```powershell
reg export "HKLM\SOFTWARE\Policies\Microsoft\Edge" ${env:USERPROFILE}\Desktop\before_edge_policy_edits_$(Get-Date -Format "yyyyMMdd-HHmmss").reg
```

Or open regedit as Administrator, navigate to `Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Edge`, then click `File -> Export`.

## Applying policies
Just double-click the registry files in this repository. It's that simple.

> [!NOTE]
> My personal policy is intended to be applied after Tommy's policies. If you wish to use my policy, please look at it first before applying it to see if it fits your needs.
> Remember that you can always overwrite keys should you wish to write your own policy, so basically you can use Tommy's policy as a base.

## Things that aren't working
Some keys do not seem to work, specifically `VideoCaptureAllowed`, `AudioCaptureAllowed`, `BackgroundModeEnabled`, `SmartScreenPuaEnabled`, and `DefaultSearchProvider*`. They will be updated if I find a fix or you may create a pull request if you know how to fix them.

Some permission settings appear to not have associated keys for them, so if you like to block everything you will have to visit the permission page and unfortunately will have to manually toggle them.

## Credits
A big thanks to [Tommy](https://github.com/TommyTran732) for [Microsoft-Edge-Policies](https://github.com/TommyTran732/Microsoft-Edge-Policies)!
