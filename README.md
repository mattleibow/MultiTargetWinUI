Multi-targeted WinUI

This fails to build in the IDE with an error:

```
C:\Program Files (x86)\Microsoft Visual Studio\2019\Preview\MSBuild\Microsoft\DesktopBridge\Microsoft.DesktopBridge.targets(718,5):
  error : Specified EntryPointExe 'MultiTargetWinUI.exe' was not found in the project outputs.
```

Some target is not running correctly. However, running this on the solution in the terminal:

```
msbuild /r /p:Platform=x64
```

Is all it takes to get things running. You can switch back to the IDE and deploy/debug. However, the IDE no longer builds the app on changes and only the terminal can be used for builds.

The terminal still does not do the correct thing because the WinUI targets are copying files into the `obj\x64\Debug` and `bin\x64\Debug` directories - even though this is an Any CPU build. Some of the files are in the `obj\x64\Debug` and some are in the `obj\Debug` directories.
