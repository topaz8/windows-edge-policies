# windows-edge-policies

Collection of Microsoft Edge policies implemented as Windows Registry files.

This repository hosts the Edge policies set by [Harden-Windows-Security](https://github.com/HotCakeX/Harden-Windows-Security) project by [HotCakeX](https://github.com/HotCakeX), my conversion of [Microsoft-Edge-Policies](https://github.com/TommyTran732/Microsoft-Edge-Policies) by [Tommy](https://github.com/TommyTran732), and my own personal policies which are meant to follow the application of Tommy's policies.

I recommend that you do not use the Harden-Windows-Security policies hosted in this repository by itself. It is merely a reference to what is actually set after choosing to enable the `Edge Browser Configurations` in [Harden-Windows-Security](https://github.com/HotCakeX/Harden-Windows-Security). I strongly recommend using the module as a whole.

[Here](https://learn.microsoft.com/en-us/DeployEdge/microsoft-edge-policies) is the resource which explains the keys and the different options you may choose for each key.

## Before you begin
Make sure that you back up your registry. To do that open Powershell as Administrator and run:
```powershell
reg export HKLM ${env:USERPROFILE}\Desktop\before_edge_policies_$(Get-Date -Format "yyyyMMdd-HHmmss").reg
```

## Applying policies
Just double-click the registry files in this repository. It's that simple.

> [!NOTE]
> The intended order of application is `mep.reg` then `topaz.reg` should you choose to use my policies as well as Tommy's.
> You should not use `hws.reg` by itself but if you want to, you should apply it first.

## Things that aren't working
Some keys do not seem to work, specifically `VideoCaptureAllowed`, `AudioCaptureAllowed`, `BackgroundModeEnabled`, `EdgeDiscoverEnabled`, `SmartScreenPuaEnabled`, and `DefaultSearchProvider*`. They will be updated if I find a fix or you may create a pull request if you know how to fix them.
`ExtensionSettings` in `mep.reg` is a `Dictionary` type key for which I don't currently know how to write manually and so it is commented out. [Microsoft-Edge-Policies](https://github.com/TommyTran732/Microsoft-Edge-Policies) uses this key to configure some settings for the uBlock Origin Lite extension. Please create a pull request if you know how to write this.

## Credits
A big thanks to [HotCakeX](https://github.com/HotCakeX) for [Harden-Windows-Security](https://github.com/HotCakeX/Harden-Windows-Security) and [Tommy](https://github.com/TommyTran732) for [Microsoft-Edge-Policies](https://github.com/TommyTran732/Microsoft-Edge-Policies).