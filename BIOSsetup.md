## BIOS setup的password 設定完之後每次開機都會被清除掉
* Sol1：在Components/ServerPlatformPkg/Features/PlatformPassword.c中的PlatformPasswordEntryPoint可以發現IsClearPasswordJumper=ProcessPwdClearHwJmpReg ();然後回查他的定義。
  可以追到UbaGpioV2PlatConfigTable.h底下有建一個PLATFORM_GPIOV2_CONFIG_TABLE然後直接查詢有呼叫此表的c檔，會發現有不同版本的GpioPlatformConfig像是Avenue與Beechnut可以先找同事確認再改。
* Sol2：也可以在Components/ServerPlatformPkg/Features/Features.sdl把"PlatformPassword"關掉(sdl告訴系統要不要使用此零件)
  ```
  INFComponent
    Name  = "PlatformPassword"
    File  = "PlatformPassword\PlatformPasswordDxe.inf"
    Package  = "ServerPlatformPkg"
    Arch = "X64"
    ModuleTypes  = "DXE_DRIVER"
    Disable=Yes
  End
  ```
  
  
