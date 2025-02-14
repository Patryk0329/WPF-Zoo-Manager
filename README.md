# 🦁 WPF Zoo Manager 🐘

## Description

WPF Zoo Manager is a WPF application that manages zoos and their associated animals using a Microsoft SQL Server 2019 database. It allows users to view, add, update, and delete zoos and animals, as well as manage the associations between them.

## Prerequisites

- Visual Studio 2022
- .NET Framework 4.7.2
- Microsoft SQL Server 2019

## Setup and Running the Application

### 1. Database Setup

Create the database and tables:

```sql
CREATE DATABASE ZooManagerDB;

USE ZooManagerDB;

CREATE TABLE Zoo (
    Id INT PRIMARY KEY IDENTITY,
    Location NVARCHAR(100)
);

CREATE TABLE Animal (
    Id INT PRIMARY KEY IDENTITY,
    Name NVARCHAR(100)
);

CREATE TABLE ZooAnimal (
    ZooId INT,
    AnimalId INT,
    FOREIGN KEY (ZooId) REFERENCES Zoo(Id),
    FOREIGN KEY (AnimalId) REFERENCES Animal(Id)
);
```

Insert sample data:

``` sql
INSERT INTO Zoo (Location) VALUES ('New York Zoo'), ('San Diego Zoo');
INSERT INTO Animal (Name) VALUES ('Lion'), ('Tiger'), ('Elephant');
INSERT INTO ZooAnimal (ZooId, AnimalId) VALUES (1, 1), (1, 2), (2, 3);
```

### 2. Configure Connection String
Ensure the connection string in App.config is correctly set:
``` xml
<connectionStrings>
    <add name="WPF_Zoo_Manager.Properties.Settings.PanjutorialsDBConnectionString"
         connectionString="Data Source=YOUR_SERVER_NAME;Initial Catalog=ZooManagerDB;Integrated Security=True"
         providerName="System.Data.SqlClient" />
</connectionStrings>
```

### 3. Run the Application
- Open the solution in Visual Studio 2022.
- Build and run the application.

### Features
- 🏢 View list of zoos.
- 🦓 View list of animals associated with a selected zoo.
- ➕ Add, update, and delete zoos and animals.
- 🔄 Manage associations between zoos and animals.