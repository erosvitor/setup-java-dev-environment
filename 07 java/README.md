
## About
Preparing the Java environment.

## Steps

### Install Java
- Install JDK

### Create shortcut for jconsole
- Create file named jconsole.desktop in ~/Desktop folder.
```
[Desktop Entry]
Name=JConsole
Type=Application
Exec=/usr/lib/jvm/jdk-<VERSION>/bin/jconsole
```

- On the desktop, right-click on the jconsole.deskop item and select item properties.

- Click on Permissions tab and check 'Allow executing file as program' option

- Now on the desktop again right-click on the jconsole.desktop item and select Allow Lauching

### Install IDE
- Install IntelliJ in /opt folder

### Create shortcut
- Create file named intellij.desktop in ~/Desktop folder.
```
[Desktop Entry]
Name=IntelliJ
Type=Application
Exec=/opt/intellij/bin/idea.sh
Icon=/opt/intellij/bin/idea.png
```

- On the desktop, right-click on the intellij.deskop item and select item properties.

- Click on Permissions tab and check 'Allow executing file as program' option

- Now on the desktop again right-click on the intellij.desktop item and select Allow Lauching

