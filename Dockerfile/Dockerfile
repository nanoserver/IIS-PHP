# Dockerfile for Nano Server + IIS Role + PHP.

FROM nanoserver/iis

MAINTAINER nanoserver.es@gmail.com

ADD https://windows.php.net/downloads/releases/php-7.1.19-nts-Win32-VC14-x64.zip php.zip
ADD https://jbit.es/files/vcruntime140.dll C:\\Windows\\System32\\vcruntime140.dll
ADD https://jbit.es/files/iisfcgi.dll C:\\Windows\\System32\\inetsrv\\iisfcgi.dll
ADD https://jbit.es/files/info.dll C:\\inetpub\\wwwroot\\info.php

ENV PHP C:\\php

RUN powershell -command Expand-Archive -Path c:\php.zip -DestinationPath C:\php

RUN setx PATH /M %PATH%;C:\php 

ADD https://jbit.es/files/php.ini C:\\php\\php.ini

RUN powershell -command \

    rm C:\Windows\System32\inetsrv\config\Applicationhost.config ; \
    Invoke-WebRequest -uri https://jbit.es/files/ApplicationHost.dll -outfile C:\\Windows\\System32\\inetsrv\\config\\Applicationhost.config ; \
    Remove-Item c:\php.zip -Force
