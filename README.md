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

## UC5 - Delete Existing Contact using firstName
```DELETE FROM addressBook WHERE firstName='Harshit';```

## UC6 -Ability to Retrieve Person belonging to a City or State

### Display based on State
```SELECT * FROM addressBook WHERE State='Delhi';```

### Display based on city
```SELECT * FROM addressBook WHERE City='New Delhi';```

## UC7 - Ability to understand the size of address book by City and State
### Count contacts By city
```
SELECT city,COUNT(city) FROM addressBook GROUP BY city;
```
### Count contacts By state
```
SELECT state,COUNT(state) FROM addressBook GROUP BY state;
```

## UC8 - Ability to retrieve entries sorted alphabetically by Person’s name for a given city
```SELECT * FROM addressBook WHERE city='New Delhi' ORDER BY firstName;```
