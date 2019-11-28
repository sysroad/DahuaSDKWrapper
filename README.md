# DahuaSDKWrapper
Dahua Camera SDK Wrapper

# Changes
- Support to platform target 'Any CPU'  
  - Set library path for x86 and x64 respectively.
    ```C#
    const string LIBRARYNETSDK_x86 = "CamLibs\\x86\\dhnetsdk.dll";
    const string LIBRARYCONFIGSDK_x86 = "CamLibs\\x86\\dhconfigsdk.dll";
    const string LIBRARYNETSDK_x64 = "CamLibs\\x64\\dhnetsdk.dll";
    const string LIBRARYCONFIGSDK_x64 = "CamLibs\\x64\\dhconfigsdk.dll";
    ```

  - Check platform by int size before function call.
    ```C#
    bool result = (IntPtr.Size == 4)
                ? OriginalSDK.CLIENT_ControlDevice(lLoginID, type, param, waittime)
                : OriginalSDK.CLIENT_ControlDevice_x64(lLoginID, type, param, waittime);
    ```
