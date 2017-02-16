# Dockerfile for Nano Server + IIS Role + PHP.

FROM nanoserver/iis

MAINTAINER nanoserver.es@gmail.com

ADD http://windows.php.net/downloads/releases/php-7.0.16-nts-Win32-VC14-x64.zip php.zip
ADD https://nanoserver.es/nanofiles/vcruntime140.dll C:\\Windows\\System32\\vcruntime140.dll
ADD https://nanoserver.es/nanofiles/iisfcgi.dll C:\\Windows\\System32\\inetsrv\\iisfcgi.dll
ADD https://nanoserver.es/nanofiles/info.dll C:\\inetpub\\wwwroot\\info.php

ENV PHP C:\\php

RUN powershell -command Expand-Archive -Path c:\php.zip -DestinationPath C:\php

RUN setx PATH /M %PATH%;C:\php 

ADD https://nanoserver.es/nanofiles/php.ini C:\\php\\php.ini

RUN powershell -command \

    rm C:\Windows\System32\inetsrv\config\Applicationhost.config ; \
    Invoke-WebRequest -uri https://nanoserver.es/nanofiles/Applicationhost.txt -outfile C:\\Windows\\System32\\inetsrv\\config\\Applicationhost.config ; \
    Remove-Item c:\php.zip -Force
 