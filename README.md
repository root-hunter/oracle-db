[![MIT License][license-shield]][license-url]

## Pre-requisites
<ul>
  <li><a href="https://docs.docker.com/compose/install/">Docker and Docker compose</a></li>
  <li><a href="https://www.docker.com/products/docker-desktop/">Docker Desktop (Optional but recommended)</a></li>
</ul>

## Installation
1. Clone the repo
   ```sh
    git clone https://github.com/root-hunter/oracle-db.git
    ```
2. Move to directory
   ```sh
   cd oracle-db
   ```
3. Start container deamon
   ```sh
   docker compose up -d
   ```

## Connection
We use <a href="https://www.oracle.com/database/sqldeveloper/technologies/download/">Sql Developer</a>.

### 1. Access to database (default pass: password123)

<br />
<img src="screenshots/login.png">
<br />

### 2. Add DBA

<br />
<img src="screenshots/dba.png">
<br />

## Troubleshooting
### 1. In oracle db image for default is set COMMON_USER_PREFIX with "C##" so every user and role must be start with "C##" prefix, if you want remove this limitation can set COMMON_USER_PREFIX to NULL
```sql
SELECT * FROM V$PARAMETER WHERE NAME = 'COMMON_USER_PREFIX';
```
### 2. Create a example user with some privileges
```sql
-- USER SQL
CREATE USER "C##YELLOWCOM" IDENTIFIED BY "password"  
DEFAULT TABLESPACE "USERS"
TEMPORARY TABLESPACE "TEMP";

-- QUOTAS
ALTER USER "C##YELLOWCOM" QUOTA UNLIMITED ON "USERS";

-- ROLES
GRANT "CONNECT" TO "C##YELLOWCOM" ;

-- SYSTEM PRIVILEGES
GRANT DROP ANY TRIGGER TO "C##YELLOWCOM" ;
GRANT ALTER ANY INDEX TO "C##YELLOWCOM" ;
GRANT DROP ANY SEQUENCE TO "C##YELLOWCOM" ;
GRANT CREATE TRIGGER TO "C##YELLOWCOM" ;
GRANT ALTER ANY PROCEDURE TO "C##YELLOWCOM" ;
GRANT CREATE ANY PROCEDURE TO "C##YELLOWCOM" ;
GRANT CREATE ANY INDEX TO "C##YELLOWCOM" ;
GRANT CREATE OPERATOR TO "C##YELLOWCOM" ;
GRANT CREATE ANY SEQUENCE TO "C##YELLOWCOM" ;
GRANT CREATE VIEW TO "C##YELLOWCOM" ;
GRANT ALTER ANY TABLE TO "C##YELLOWCOM" ;
GRANT SELECT ANY TABLE TO "C##YELLOWCOM" ;
GRANT ALTER ANY SEQUENCE TO "C##YELLOWCOM" ;
GRANT CREATE TABLE TO "C##YELLOWCOM" ;
GRANT DROP ANY TABLE TO "C##YELLOWCOM" ;
GRANT DROP ANY OPERATOR TO "C##YELLOWCOM" ;
GRANT CREATE ANY OPERATOR TO "C##YELLOWCOM" ;
GRANT CREATE TYPE TO "C##YELLOWCOM" ;
GRANT CREATE TABLESPACE TO "C##YELLOWCOM" ;
GRANT DROP ANY TYPE TO "C##YELLOWCOM" ;
GRANT CREATE ANY SYNONYM TO "C##YELLOWCOM" ;
GRANT DROP ANY SYNONYM TO "C##YELLOWCOM" ;
GRANT EXECUTE ANY PROCEDURE TO "C##YELLOWCOM" ;
GRANT CREATE SYNONYM TO "C##YELLOWCOM" ;
GRANT CREATE SEQUENCE TO "C##YELLOWCOM" ;
GRANT DROP ANY INDEX TO "C##YELLOWCOM" ;
GRANT EXECUTE ANY OPERATOR TO "C##YELLOWCOM" ;
GRANT UPDATE ANY TABLE TO "C##YELLOWCOM" ;
GRANT DROP ANY VIEW TO "C##YELLOWCOM" ;
GRANT ALTER ANY TRIGGER TO "C##YELLOWCOM" ;
GRANT CREATE ANY VIEW TO "C##YELLOWCOM" ;
GRANT READ ANY TABLE TO "C##YELLOWCOM" ;
GRANT INSERT ANY TABLE TO "C##YELLOWCOM" ;
GRANT ALTER ANY TYPE TO "C##YELLOWCOM" ;
GRANT DROP ANY PROCEDURE TO "C##YELLOWCOM" ;
GRANT CREATE ANY TRIGGER TO "C##YELLOWCOM" ;
GRANT CREATE ANY TABLE TO "C##YELLOWCOM" ;
GRANT CREATE ANY TYPE TO "C##YELLOWCOM" ;
GRANT CREATE PROCEDURE TO "C##YELLOWCOM" ;
GRANT ALTER ANY OPERATOR TO "C##YELLOWCOM" ;
```

[license-shield]: https://img.shields.io/github/license/othneildrew/Best-README-Template.svg?style=for-the-badge
[license-url]: https://github.com/root-hunter/oracle-db/blob/master/LICENSE
