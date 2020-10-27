# SQL-AddressBook 
## UC1 - Create addressBook database 
```create database addressBook;```

### Go to the database created
```use addressBook;```

## UC2 - Create Table addressBook
```create table addressBook
    ( firstName    varchar(30) NOT NULL,
      lastName     varchar(30) NOT NULL,
      Address      varchar(100) NOT NULL,
      City         varchar(30) NOT NULL,
      State        varchar(30) NOT NULL,
      Zip          int(6)      NOT NULL,
      Phone No. int(15)      NOT NULL,
      Email        varchar(50) NOT NULL,
      PRIMARY KEY  (firstName)
    );```
