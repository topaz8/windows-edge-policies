# Policy Editing Tips
Tommy's policies are meant to be applied first. You can then apply my policies if they fit your needs. Should you disagree with a setting or settings, you can always change it or unset it entirely. That can be done a couple of ways. You can either manually edit the policies within the registry editor or you can write your own reg file.

## Registry Editor
Open `regedit.exe` as Administrator and navigate to `Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Edge`. This is where all the edge policies are located. From here you can right click a setting, then click either **`Modify...`** to change a setting or `Delete` to unset it entirely. Deleting a value restores that value's default behavior. It does not "turn off" something.

### Adding new policies in Registry Editor
Right click in the empty space to the right, click `New    >` and choose whether to add a new `Key`, `String`, or `DWORD (32-bit) Value` depending on what data type the setting you want to add requires. Booleans and integers will be added as `DWORD (32-bit) Value`'s. Strings and dictionaries will be added as `String`'s. List of strings and keys will be added as a `Key` and then within them their options added. Let's take `AutomaticFullscreenBlockedForUrls` for example. If this policy didn't already exist, we would (within the Edge key), right click, click `New    >` `Key`. We would then fill in `AutomaticFullscreenBlockedForUrls` where it says `New Key #1` in the left hand side. The right side has updated to be inside this key already. In the blank space we can add our options. `AutomaticFullscreenBlockedForUrls` takes a list of strings, with value names `1`, `2`, `3`, and so on, and they take URL's as their data. You can visualize this as literally a list:
```
1    https://www.example.com
2    [*.]example.edu
3    https://example2.com
```
Inside the `AutomaticFullscreenBlockedForUrls` key, right click, `New    >` `String Value` and name it `1`. Right click `1` and click **`Modify...`**. Type the URL in the box and click `OK`. Do this for each URL you want to add.

## Reg files
One of the best ways to edit these policies and create your own policies is with a reg file. It's way more time efficient, and additions and edits can be applied instantaneously. Open your favorite editor. To start with, you need to add the registry file header.
```
Windows Registry Editor Version 5.00
```

To add or change values within the Edge key, define the section we want to work with:
```
[HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Edge]
```

Underneath this section we can modify, add, or unset values. For example:
```
"ExtensionManifestV2Availability"=dword:00000000 ; semicolon starts a comment
"VideoCaptureAllowed"=dword:00000001 ; next few values we change to be different
"AudioCaptureAllowed"=dword:00000001
"DefaultNotificationsSetting"=dword:00000001
"WhateverVal"="this would be how to define a string"
"DefaultSearchProviderEnabled"=- ; this unsets a value to its default behavior
```

To unset a key, its subkeys, and values (to their default behavior):
```
[-HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Edge\JavaScriptBlockedForUrls]
```

Elaborating on the `AutomaticFullscreenBlockedForUrls` key (as an example):
```
[HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Edge\AutomaticFullscreenBlockedForUrls]
"1"="https://www.example.com"
"2"="*" ; to block all URLs
```

### Dictionaries
Dictionaries e.g. `ManagedSearchEngines` and `ManagedConfigurationPerOrigin` take JSON formatted data. When writing this in a reg file, it needs to be condensed into one line with spaces removed and double quotes in the JSON data escaped:
```
"ManagedSearchEngines"="[{\"allow_search_engine_discovery\":false},{\"is_default\":true,\"keyword\":\"bing.com\",\"name\":\"Bing\",\"search_url\":\"https://www.bing.com/search?q={searchTerms}\",\"suggest_url\":\"https://www.bing.com/search?q={searchTerms}\"}]"
```

## Where to learn more
You can learn what the registry keys mean, their options, and how to define them [here](https://learn.microsoft.com/en-us/DeployEdge/microsoft-edge-policies).