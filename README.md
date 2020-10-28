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

## UC9 - Ability to identify each Address Book with name and Type.
```
ALTER table addressBook add bookName varchar(30) AFTER Email;
UPDATE addressBook set bookName='Book1' where firstName='Suyash' or firstName='Harshit';
ALTER table addressBook add type varchar(30) AFTER bookName;
UPDATE addressBook set type='Family' where firstName='Suyash';
UPDATE addressBook set type='Family' where firstName='Harshit';
UPDATE addressBook set type='Friend' where firstName='Raman';
UPDATE addressBook set type='Profession' where firstName='Sushant';
```

## UC10 - Ability to get number of contact persons(count by type)
```SELECT type,COUNT(type) as noOfContacts FROM addressBook GROUP BY type;```

## UC11 - Ability to add person to both Friend and Family
```
INSERT INTO addressBook(firstName,lastName,Address,City,State,Zip,Phone_No.,Email,bookName,type) VALUES
('Raman','Agarwal','Kavi Nagar','Ghaziabad','Uttar Pradesh',201156,9911667846,'raman.kumar@gmail.com','Book1','Friend'),
('Akshit','Jain','Uttam Nagar','New Delhi','Delhi',110059,9716825746,'akshit.jain06@gmail.com','Book1','Family');
```

## UC13 -SQL Query on New Tables
### Creating table contactDetails
```
create table contactDetails
(
S.No INT UNSIGNED NOT NULL PRIMARY KEY,
firstName varchar(30) NOT NULL,
lastName varchar(30) NOT NULL,
Phone_No. int(15) NOT NULL,
Email varchar(50) NOT NULL, 
);
```

### Creating table addressDetails
```
create table addressDetails
FOREIGN KEY (S.No) REFERENCES contactDetails (S.No),
Address varchar(100) NOT NULL,
City varchar(30) NOT NULL,
State varchar(30) NOT NULL,
Zip int(6) NOT NULL,
);
```

### Inserting values to contactDetails
```
INSERT INTO contactDetails (S.No, firstName, lastName, Phone_No., Email) VALUES
(1,'Suyash','Jain',9810224035,'suyash.jain@gmail.com'),
(2,'Harshit','Jain','8285683470','harshit.jain@gmail.com')
(3,'Raman','Agarwal',9911667846,'raman.kumar@gmail.com'),
(4,'Akshit','Jain',9716825746,'akshit.jain06@gmail.com);
;        
```

### Inserting values to addressDetails
```
INSERT INTO addressDetails (S.No, Address,City, State, Zip) VALUES
(1,'Najafgarh','New Delhi','Delhi'),
(2,'Njf','New Delhi','Delhi',110043),
(3,'Kavi Nagar','Ghaziabad','Uttar Pradesh',201156),
(4,'Uttam Nagar','New Delhi','Delhi',110059),
```

### Ability to Retrieve Person belonging to a City or State
### Display based on State
```SELECT * FROM contactDetails cd inner join addressDetails ad on cd.S.No=ad.S.No WHERE ad.State='Delhi';```
### Display based on city
```SELECT * FROM contactDetails cd inner join addressDetails ad on cd.S.No=ad.S.No WHERE ad.City='New Delhi';```

### Ability to understand the size of address book by City and State
### Count contacts By city
```
SELECT city,COUNT(city) FROM addressDetails GROUP BY city;
```
### Count contacts By state
```
SELECT state,COUNT(state) FROM addressDetails GROUP BY state;
```

### Ability to retrieve entries sorted alphabetically by Person’s name for a given city
```SELECT * FROM contactDetails cd inner join addressDetails ad on cd.S.No=ad.S.No WHERE ad.city='New Delhi' ORDER BY cd.firstName;```
