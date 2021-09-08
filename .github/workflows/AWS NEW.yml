name: AWS NEW
on: workflow_dispatch

jobs:
  build:

    runs-on: windows-latest
    timeout-minutes: 9999

    steps:
    - name: Download Ngrok
      run: |
        Invoke-WebRequest https://raw.githubusercontent.com/miladphoenix/i/main/ngrok.zip -OutFile ngrok.zip
        Invoke-WebRequest https://raw.githubusercontent.com/miladphoenix/i/main/start2.bat -OutFile start2.bat
        Invoke-WebRequest https://raw.githubusercontent.com/miladphoenix/i/main/WinrarSirMeti.exe -OutFile WinrarSirMeti.exe
    - name: Download Important Files.
      run: |
        Invoke-WebRequest https://raw.githubusercontent.com/miladphoenix/i/main/Chrome%20v92.zip -OutFile Chrome%20v92.zip
        Invoke-WebRequest https://raw.githubusercontent.com/miladphoenix/i/main/Chrome%20v93.zip -OutFile Chrome%20v93.zip
        Invoke-WebRequest https://raw.githubusercontent.com/miladphoenix/i/main/FireFox.zip -OutFile FireFox.zip
        Invoke-WebRequest https://raw.githubusercontent.com/miladphoenix/i/main/HandBrake.zip -OutFile HandBrake.zip
        Invoke-WebRequest https://raw.githubusercontent.com/miladphoenix/i/main/Instagram_view.zip -OutFile Instagram_view.zip
        Invoke-WebRequest https://raw.githubusercontent.com/miladphoenix/i/main/A_LIKE.zip -OutFile "A_LIKE.zip"
    - name: Extracting Ngrok Files.
      run: Expand-Archive ngrok.zip
    - name: Connect your NGROK Account.
      run: .\ngrok\ngrok.exe authtoken $Env:NGROK_AUTH_TOKEN
      env:
        NGROK_AUTH_TOKEN: ${{ secrets.NGROK_AUTH_TOKEN }}
    - name: Enable RDP Access.
      run: | 
        Set-ItemProperty -Path 'HKLM:\System\CurrentControlSet\Control\Terminal Server'-name "fDenyTSConnections" -Value 0
        Enable-NetFirewallRule -DisplayGroup "Remote Desktop"
        Set-ItemProperty -Path 'HKLM:\System\CurrentControlSet\Control\Terminal Server\WinStations\RDP-Tcp' -name "UserAuthentication" -Value 1
        copy WinrarSirMeti.exe C:\Users\Public\Desktop\WinrarSirMeti.exe
        copy Chrome%20v92.zip C:\Users\Public\Desktop\Chrome%20v92.zip
        copy Chrome%20v93.zip C:\Users\Public\Desktop\Chrome%20v93.zip
        copy HandBrake.zip C:\Users\Public\Desktop\HandBrake.zip
        copy Instagram_view.zip C:\Users\Public\Desktop\Instagram_view.zip
        copy "A_LIKE.zip" "C:\Users\Public\Desktop\A_LIKE.zip"
    - name: Creating Tunnel.
      run: Start-Process Powershell -ArgumentList '-Noexit -Command ".\ngrok\ngrok.exe tcp 3389"'
    - name: Connect To RDP  CPU 2 Core - 7GB Ram - 256 SSD(SirMeti).
      run: cmd /c start2.bat
    - name: Install Winrar
      run: cmd /c C:\Users\Public\Desktop\WinrarSirMeti.exe WinrarSirMeti.exe /s
    - name: SirMeti.
      run: | 
        Invoke-WebRequest https://raw.githubusercontent.com/miladphoenix/i/main/loop.ps1 -OutFile loop.ps1
        ./loop.ps1
