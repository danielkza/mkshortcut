# Description

This project allows creating Windows Shortcuts (.lnk files) with special attributes that are otherwise not easily modifiable.


## Extending Windows Shortcut Properties editor

Add the following Windows Registry entries as String type:

```
[HKEY_CLASSES_ROOT\lnkfile]
"InfoTip"="prop:System.Comment;System.Link.TargetParsingPath;System.AppUserModel.ID;System.ItemFolderPathDisplay"
"ExtendedTileInfo"="prop:System.Comment;System.Link.TargetParsingPath;System.AppUserModel.ID;System.ItemFolderPathDisplay"
"PreviewDetails"="prop:System.Comment;System.Link.TargetParsingPath;System.AppUserModel.ID;System.ItemFolderPathDisplay"
"PreviewTitle"="prop:System.Comment;System.Link.TargetParsingPath;System.AppUserModel.ID;System.ItemFolderPathDisplay"
"QuickTip"="prop:System.Comment;System.Link.TargetParsingPath;System.AppUserModel.ID;System.ItemFolderPathDisplay"
"TileInfo"="prop:System.Comment;System.Link.TargetParsingPath;System.AppUserModel.ID;System.ItemFolderPathDisplay"
"FullDetails"="prop:System.PropGroup.Description;System.ItemTypeText;System.Comment;System.Link.TargetParsingPath;System.AppUserModel.ID;System.ItemFolderPathDisplay;prop:System.PropGroup.FileSystem;System.ItemNameDisplay;System.Size;System.DateCreated;System.DateModified;System.FileAttributes;*System.OfflineAvailability;*System.OfflineStatus;*System.SharedWith;*System.FileOwner;*System.ComputerName"
```

To revert the changes, simply delete the entries listed above.

**Note: The Windows Registry is a very dangerous, scary, and risky place to fiddle around. Use at your own risk!**


## PortableApps.com

Typical usage of `mkshortcut` for PortableApps.com packages with dedicated launchers.

```
mkshortcut.exe -output "Shortcut Name.lnk" -target "C:\Path\to\ExecutablePortable.exe" -appid "AppID-read-below"
```

Sometimes the AppID is the path to the executable itself (e.g. 7-zip, Firefox Stable). Sometimes it is a different value (e.g. Firefox Developer 59.0).

If the steps above to enhance Windows Shortcuts Properties were taken, then you can obtain the correct AppID as follows:

1. Pin the already running executable and close the application.
2. Shift-right click the pinned icon and click Properties.
3. Go to the Details tab and find the value under AppUserModelID.
4. Use that value as the AppID parameter to `mkshortcut.exe`.


# License

Copyright 2010 Daniel Miranda. All rights reserved.

Redistribution and use in source and binary forms, with or without
modification, are permitted provided that the following conditions are met:

   1. Redistributions of source code must retain the above copyright notice,
   this list of conditions and the following disclaimer.
   2. Redistributions in binary form must reproduce the above copyright notice,
   this list of conditions and the following disclaimer in the documentation
   and/or other materials provided with the distribution.

THIS SOFTWARE IS PROVIDED BY THE AUTHOR ``AS IS'' AND ANY EXPRESS OR IMPLIED
WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES OF
MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO
EVENT SHALL THE AUTHOR OR CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT,
INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT
LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, DATA, OR
PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF
LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE
OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS SOFTWARE, EVEN IF
ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.
