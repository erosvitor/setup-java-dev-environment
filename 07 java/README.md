
# About
Preparing the Java environment.

# Steps

## Install Java
- Install JDK

## Install certificates

### Download
```
sudo curl -k -sL <endereço-certificado/certificado.cer> -o /tmp/certificado.pem
```

### Install in Java
```
sudo $JAVA_HOME/bin/keytool -import -file /tmp/certificado.pem -alias certificado -keystore $JAVA_HOME/lib/security/cacerts -trustcacerts -noprompt
```

### Install in Linux
```
sudo cp /tmp/certificado.pem /usr/local/share/ca-certificates/certificado.pem

sudo update-ca-certificates --fresh
```

## Create shortcut for jconsole
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

## Install IDE
- Install **IntelliJ** in /opt folder

## Create shortcut for IDE
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

## Install IntelliJ plugings
- SonarQube for IDE
- CodeMetrics
- Cucumber +
- Cucumber for Java
- Gherkin
- GitHub Copilot
