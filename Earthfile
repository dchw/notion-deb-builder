
deps:
    FROM node:15
    COPY build.sh .
    RUN apt update && \
        apt -y install p7zip-full imagemagick fakeroot wget python3 make && \
        npm -g install asar electron-packager electron-installer-debian

build-win:
    FROM +deps
    RUN wget 'https://desktop-release.notion-static.com/Notion%20Setup%202.0.8.exe' -O notion.exe && \
        ./build.sh win
    SAVE ARTIFACT out/notion-desktop_2.0.8-win_amd64.deb AS LOCAL notion-desktop_2.0.8-win_amd64.deb

build-mac:
    FROM +deps
    RUN wget 'https://desktop-release.notion-static.com/Notion-2.0.7.dmg' -O notion.dmg && \
        ./build.sh mac
    SAVE ARTIFACT out/notion-desktop_2.0.7-mac_amd64.deb AS LOCAL notion-desktop_2.0.7-mac_amd64.deb