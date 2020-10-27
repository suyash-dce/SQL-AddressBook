# SQL-AddressBook 
## UC1 - Create addressBook database 
```create database addressBook;```

### Go to the database created
```use addressBook;```

## UC2 - Create Table addressBook
``` 
    create table addressBook
    ( firstName    varchar(30) NOT NULL,
      lastName     varchar(30) NOT NULL,
      Address      varchar(100) NOT NULL,
      City         varchar(30) NOT NULL,
      State        varchar(30) NOT NULL,
      Zip          int(6)      NOT NULL,
      Phone_No. int(15)      NOT NULL,
      Email        varchar(50) NOT NULL,
      PRIMARY KEY  (firstName)
    );
```
    
## UC3 - Insert Values in addressBook
```
    INSERT INTO addressBook(firstName,lastName,Address,City,State,Zip,Phone_No.,Email) VALUES
    -> ('Suyash','Jain','Najafgarh','New Delhi','Delhi',110043,9810224035,'suyash.jain@gmail.com'),
    -> ('Harshit','Jain','Njf','New Delhi','Delhi',110043,8285683470,'harshit.jain@gmail.com');        
```

## UC4 - Edit Existing Contact using Name
```UPDATE addressBook SET Phone_No.=9810223540 WHERE firstName='Suyash';```
    
