# ER_google-Case-study

create database ER_google;
use ER_google;

create table Customer(
CustomerID int primary key,
Name Varchar(50),
Email varchar(100),
City varchar(50)
);

Create table Products(
ProductID int primary key,
ProductName varchar(50),
Category varchar(50),
Price int
);

Create table Orders(
OrderID int primary key,
CustomerID int,
Order_name varchar (50),
Amount int,
foreign key (customerID) references Customer(CustomerID)
);

Create table Orders_Item(
OrderItemID int primary key,
OrderID int,
ProductID int,
Quantity int,
Item_name varchar(50),
foreign key (OrderID) references Orders(OrderID),
foreign key (ProductID) references Products(ProductID)
);

Create table Employee(
EmployeeID int primary key,
Name varchar (100),
Salary int,
OrderItemID int ,
foreign key (OrderItemID) references Orders_Item(OrderItemID)
);

Create table Inventory(
InventoryID int primary key,
ProductID int,
foreign key (ProductID) references Products(ProductID)
);

Create table Payments(
CustomerID int,
ProductID int,
OrderID int,
OrderItemID int,
EmployeeID int,
InventoryID int,
foreign key (CustomerID) references Customer(CustomerID),
foreign key (ProductID) references Products(ProductID),
foreign key (OrderID) references Orders(OrderID),
foreign key (OrderItemID) references Orders_Item(OrderItemID),
foreign key (EmployeeID) references Employee(EmployeeID),
foreign key (InventoryID) references Inventory(InventoryID)
);
