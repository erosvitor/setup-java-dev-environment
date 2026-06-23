
# About
Preparing the database environment.

# Steps

## Install DBeaver
- Install DBeaver in /opt folder

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

## Docker Compose for MySQL
1 - Create file named **docker-compose-mysql8.yaml**
```
services:
  mysql:
    image: mysql:8.0
    container_name: mysql8
    restart: unless-stopped
    environment:
      MYSQL_ROOT_PASSWORD: root-root
      MYSQL_DATABASE: hellomysql
      MYSQL_USER: hellouser
      MYSQL_PASSWORD: hellopass
    ports:
      - 3306:3306
    networks:
      - mysql
    volumes:
      - mysql_data:/var/lib/mysql
      - ./scripts/create.sql:/docker-entrypoint-initdb.d/1.create.sql

volumes:
  mysql_data:

networks:
  mysql:
    driver: bridge
    name: mysql8
```

2 - Create folder named **scripts**

3 - Create file named **create.sql** into folder **scripts**
```
CREATE TABLE PERSONS (
  IDT_PERSON INTEGER AUTO_INCREMENT NOT NULL,
  DES_PERSON VARCHAR(80) NOT NULL,
  PRIMARY KEY (IDT_PERSON)
);
```

4 - Create MySQL container
```
docker compose -f docker-compose-mysql8.yaml up -d
```

5 - Get IP address
```
docker inspect mysql8 | grep IPAddress
```

6 - Create DBeaver connection

Main Tab
```
Server Host: <ip-container>
Database: hellomysql
Username: hellouser
Password: hellopass
```

Driver properties Tab
```
allowPublicKeyRetrieval = true
```

7 - Destroy MySQL container
```
docker compose -f docker-compose-mysql8.yaml down
```

## Docker Compose for Postgres
1 - Create file named **docker-compose-postgres17.yaml**
```
services:
  postgres:
    image: postgres:17
    container_name: postgres17
    restart: unless-stopped
    environment:
      POSTGRES_DB: hellopostgres
      POSTGRES_USER: hellouser
      POSTGRES_PASSWORD: hellopass
    ports:
      - 5432:5432
    networks:
      - postgres
    volumes:
      - postgres_data:/var/lib/postgresql/data
      - ./scripts/create.sql:/docker-entrypoint-initdb.d/1.create.sql

networks:
  postgres:
    driver: bridge
    name: postgres17

volumes:
  postgres_data:
```

2 - Create folder named **scripts**

3 - Create file named **create.sql** into folder **scripts**
```
CREATE TABLE PERSONS (
  IDT_PERSON SERIAL NOT NULL,
  DES_PERSON VARCHAR(80) NOT NULL,
  PRIMARY KEY (IDT_PERSON)
);
```

4 - Create Postgres container
```
docker compose -f docker-compose-postgres17.yaml up -d
```

5 - Get IP address
```
docker inspect postgres17 | grep IPAddress
```

6 - Create DBeaver connection

Main Tab
```
Server Host: <ip-container>
Database: hellopostgress
Username: hellouser
Password: hellopass
```

7 - Destroy Postgres container
```
docker compose -f docker-compose-postgres17.yaml down
```

