!!! danger "Please make sure you downloaded your data from an appropriate source.<br>This guide is unable to troubleshoot any problems related to bad or poorly managed data."

---

### My game crashes on launch/stuck on "Starting System Process"

!!! tip ""

    Could be due to **many** things, the most common of which are:
    
    - `amdaemon` crashing in the background. Make sure that the `config_*.json` files
    have valid syntax, your ICF files are correct, and the OpenSSL fix is applied on Intel Core 10th Gen CPUs and newer.
    
??? info "Capturing logs from `amdaemon` for troubleshooting"

    To assist with troubleshooting, a script can be used to capture logs from `amdaemon`. Create a file named
    `amdaemontest.bat` in `App\bin`, then paste the code block below into the file.

    ```batch
    @echo off
    cls
    echo Attempting to run AM Daemon ...
    echo Window should close after 30 seconds
    echo Log will be generated at amdaemontest.txt
    call :sub >amdaemontest.txt
    exit /b

    :sub
    set OPENSSL_ia32cap=:~0x20000000
    pushd %~dp0
    start /b "AM Daemon" /min inject -d -k mu3hook.dll amdaemon.exe -f -c config_common.json config_server.json 
    ping 127.0.0.1 -n 31 > nul && taskkill /F /im amdaemon.exe
    ```

    Double-click it to run. The script should run for 30 seconds, and you will get a file
    named `amdaemontest.txt` in `App\bin`, which you can send to help people troubleshoot your issue.

---

### My game is stuck on a black screen at launch!
!!! tip ""

    This could also be due to **many** things, the most common of which are:
    
    - You have one or more incorrect/broken DLL(s) in `App\package\mu3_Data\Managed`
    
        This is likely to be `Assembly-CSharp.dll`, `Assembly-CSharp-firstpass.dll`, and/or `AMDaemon.NET.dll`.
        You can try replacing the DLLs or re-downloading data from elsewhere.
    - An ill-formed keychip is defined in `segatools.ini`

---

### My game is running too slow/fast or the notes are out of sync!

!!! tip ""

    The game could be running under or over its required refresh rate.
    
    - Make sure V-Sync isn't disabled in your graphics settings (called "Vertical sync"
    in NVIDIA Control Panel and "Wait for Vertical Refresh" in AMD Control Panel.)
    - Limit `mu3.exe` to run at 60 FPS using a tool like [RivaTuner](https://www.guru3d.com/download/rtss-rivatuner-statistics-server-download) or a patch.

    It could also be that your computer's performance isn't good enough to keep
    a steady framerate.

---

### My lever controls aren't working!
!!! tip ""

    You may need to calibrate your lever.

    From the `TEST MENU` select **レバー設定** (`LEVER SETTINGS`) and then move the lever left to
    right ensuring that the game detects the full range of motion.

    Then save by selecting **終了** (`EXIT`) and then **保存する** (`SAVE`).

---

### My game is stuttering

!!! tip ""

    For NVIDIA users, create an override for `mu3.exe` in NVIDIA Control Panel
    and change "Power management mode" to "**Prefer maximum performance**".
