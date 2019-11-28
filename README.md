# DahuaSDKWrapper
Dahua Camera SDK Wrapper

# Changes
- Support to platform target 'Any CPU'  
  - Added library path for x86 and x64 respectively.
    ```C#
    const string LIBRARYNETSDK_x86 = "CamLibs\\x86\\dhnetsdk.dll";
    const string LIBRARYCONFIGSDK_x86 = "CamLibs\\x86\\dhconfigsdk.dll";
    const string LIBRARYNETSDK_x64 = "CamLibs\\x64\\dhnetsdk.dll";
    const string LIBRARYCONFIGSDK_x64 = "CamLibs\\x64\\dhconfigsdk.dll";
    ```  
    <b>You can download runtime dlls from dahua homepage.</b>  
    Then put those to proper path. In this case it will be './CamLibs'.  
  - Added static entry points for x64.
    ```C#
    [DllImport(LIBRARYNETSDK_x64)]
    public static extern int CLIENT_GetLastError_x64();
    ...
    others
    ...
    ```

  - Added platform checking by int size before function call.
    ```C#
    bool result = (IntPtr.Size == 4)
                ? OriginalSDK.CLIENT_ControlDevice(lLoginID, type, param, waittime)
                : OriginalSDK.CLIENT_ControlDevice_x64(lLoginID, type, param, waittime);
    ```
