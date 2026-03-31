* ERROR CODE
```
FIT Tool path is Intel\BirchStreamRpPkg\Tool\FTool\Flash_Image_Tool\FitmCmd
Current Working Directory is D:\Sky722V4_Password\Intel\BirchStreamRpPkg\Tool\FTool\Flash_Image_Tool\FitmCmd
Python was not found; run without arguments to install from the Microsoft Store, or disable this shortcut from Settings > Apps > Advanced app settings > App execution aliases.
Traceback (most recent call last):
  File "D:\Sky722V4_Password\Intel\ServerPlatformPkg\BuildImage.py", line 957, in <module>
    main()
  File "D:\Sky722V4_Password\Intel\ServerPlatformPkg\BuildImage.py", line 931, in main
    build_image.run_fitm()
  File "D:\Sky722V4_Password\Intel\ServerPlatformPkg\BuildImage.py", line 890, in run_fitm
    self.CopyBinariesToRomDir()
  File "D:\Sky722V4_Password\Intel\ServerPlatformPkg\BuildImage.py", line 290, in CopyBinariesToRomDir
    shutil.copy("outimage.map", dest_mapfile_path)
  File "C:\Programs\Python\Python311\Lib\shutil.py", line 419, in copy
    copyfile(src, dst, follow_symlinks=follow_symlinks)
  File "C:\Programs\Python\Python311\Lib\shutil.py", line 256, in copyfile
    with open(src, 'rb') as fsrc:
         ^^^^^^^^^^^^^^^
FileNotFoundError: [Errno 2] No such file or directory: 'outimage.map'
make[4]: *** [CreateBios] Error 1
BirchStreamCrb.mak:546: recipe for target 'CreateBios' failed
AmiPkg/Configuration/Main.mak:196: recipe for target 'Build\BeechnutCity\RELEASE_VS2019\FV\AMIROM.fd.patch' failed
make[3]: *** [Build\BeechnutCity\RELEASE_VS2019\FV\AMIROM.fd.patch] Error 2
makefile:83: recipe for target 'AptioV' failed
make[2]: *** [AptioV] Error 2
Intel/BirchStreamFspPkg/RebuildFspBios/RebuildFspBios.mak:58: recipe for target 'FinishRebuildFsp' failed
make[1]: *** [FinishRebuildFsp] Error 2
makefile:83: recipe for target 'AptioV' failed
make: *** [AptioV] Error 2
```
1. 大概問題介紹：Windows 為了方便使用者，預設在系統路徑中放了一個名為 python.exe 的「空殼（捷徑）」，對於 BIOS 編譯環境來說，這個「空殼」會導致你的編譯腳本（如 BuildImage.py）因為抓不到真正的執行檔而中斷，進而產生你之前遇到的 outimage.map 找不到的問題。
2. 
到以下圖片把與python.exe相關的全部切換為關閉。
<img width="854" height="561" alt="image" src="https://github.com/user-attachments/assets/adc85595-2647-4d6d-9735-34301ab1dc8c" />
