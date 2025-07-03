
## About
Preparing the database environment.

## Steps

### Install DBeaver
- Install DBeaver in /opt folder

### Create shortcut
- Create file named dbeaver.desktop in ~/Desktop folder.
```
[Desktop Entry]
Name=DBeaver
Type=Application
Exec=/opt/dbeaver/dbeaver
Icon=/opt/dbeaver/dbeaver.png
```

- On the desktop, right-click on the dbeaver.deskop item and select item properties.

- Click on Permissions tab and check 'Allow executing file as program' option.

- Now on the desktop again right-click on the dbeaver.desktop item and select Allow Lauching

### Dockerfile for MySQL

### Dockerfile for Postgres

### Dockerfile for Oracle
```
services:
  oracle-xe:
    image: repo.intranet.pags/psp-docker-qa-local/oracle-xe:21.3.0-slim-faststart
    container_name: oracle-xe
    restart: always
    environment:
      ORACLE_ALLOW_REMOTE: true
      ORACLE_SID: XE
      ORACLE_PDB: XEPDB1
      ORACLE_PASSWORD: admin
    ports:
      - 1521:1521
      - 5500:5500
    expose:
      - 1521
      - 5500
```
      
