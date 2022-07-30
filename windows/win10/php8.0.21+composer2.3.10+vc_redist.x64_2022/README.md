# 1-command-install

## php-8.0.21(with vc_redist) and composer 2.3.10

Press "Windows" button, search Powershell, Right click Windows PowerShell, <b>Run as administrator</b>, Yes.  
Copy the command, go to PowerShell, right click the PowerShell (means paste), Press Enter to run the command.  

```
cd $env:TEMP;Invoke-WebRequest https://github.com/techdesignism/1-command-install/raw/main/windows/win10/php8.1.8%2Bcomposer2.3.10%2Bvc_redist.x64_2022/php-8.1.8-Win32-vs16-x64.zip -O php.zip;Expand-Archive php.zip -DestinationPath C:/php;Copy-Item 'C:/php/php.ini-development' -Destination 'C:/php/php.ini';(Get-Content C:/php/php.ini) -Replace ';extension=openssl', 'extension=openssl' -Replace ';extension=curl', 'extension=curl' -Replace ';extension=gd', 'extension=gd' -Replace ';extension=mbstring', 'extension=mbstring' -Replace ';extension=pdo_mysql', 'extension=pdo_mysql' -Replace ';extension=pdo_sqlite', 'extension=pdo_sqlite' -Replace ';extension=sqlite3', 'extension=sqlite3' -Replace ';extension=fileinfo', 'extension=fileinfo'  | Set-Content C:/php/php.ini;$env:Path += ';C:/php';[Environment]::SetEnvironmentVariable("Path", $env:Path + ";C:\php", "Machine");Invoke-WebRequest https://github.com/techdesignism/1-command-install/raw/main/windows/win10/php8.1.8%2Bcomposer2.3.10%2Bvc_redist.x64_2022/VC_redist.x64.exe -O vc.exe;Start-Process -FilePath "vc.exe" -ArgumentList "/Q" -Wait;$env:Path += ';C:/php';cd C:/php;cmd /c "php -r ""copy('https://github.com/techdesignism/1-command-install/raw/main/windows/win10/php8.1.8%2Bcomposer2.3.10%2Bvc_redist.x64_2022/installer', 'composer-setup.php');""";cmd /c "php -r ""if (hash_file('sha384', 'composer-setup.php') === '55ce33d7678c5a611085589f1f3ddf8b3c52d662cd01d4ba75c0ee0459970c2200a51f492d557530c71c15d8dba01eae') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;""";cmd /c "php composer-setup.php";cmd /c "php -r ""unlink('composer-setup.php');""";Set-Content composer.bat '@php "%~dp0composer.phar" %*';$mdm=[environment]::getfolderpath("mydocuments");cd $mdm;start cmd -ArgumentList '/k','php --version && composer -V';exit;
```

Source files:  

php-8.0.21-Win32-vs16-x64.zip  
https://windows.php.net/downloads/releases/php-8.0.21-Win32-vs16-x64.zip

installer  
https://getcomposer.org/installer

VC_redist.x64.exe  
https://aka.ms/vs/17/release/vc_redist.x64.exe
