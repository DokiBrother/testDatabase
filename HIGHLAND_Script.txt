CREATE DATABASE HighLand;
USE HighLand;

/*---GUEST TABLE---*/
CREATE TABLE Guest (
GuestID INT(10) UNSIGNED PRIMARY KEY
);
INSERT INTO Guest(GuestID) Value(1),(2),(3),(4),(5),(6),(7),(8),(9),(10),(11),(12),
								(13),(14),(15),(16),(17),(18),(19),(20),(21),(22),(23),(24);
/*===================================================*/

/*---TABLE_CODE TABLE---*/
CREATE TABLE TableCode (
TableID INT(2) UNSIGNED AUTO_INCREMENT PRIMARY KEY,
NumberOfChair INT(1) NOT NULL
);
INSERT INTO TableCode(NumberOfChair) VALUE (1), (1), (1), (1), (1),
										(2), (2), (2), (2), (2),
                                        (4), (4), (4), (4), (4),
                                        (2), (2), (2), (2), (2);
/*===================================================*/

/*---PRODUCT TABLE---*/
CREATE TABLE Product (
ProductID INT(10) UNSIGNED AUTO_INCREMENT PRIMARY KEY,
ProductName VARCHAR(30) NOT NULL,
Size VARCHAR(5),
QuantityPerUnit INT NOT NULL,
UnitPrice INT NOT NULL
);
INSERT INTO Product(ProductName, Size, QuantityPerUnit, UnitPrice)
	VALUE	('Phin sữa đá', '12oz', 243, 35000),		('Phin sữa đá', '16oz', 331, 39000),
			('Bạc xỉu đá', '10oz', 12, 29000), 			('Phindi kem sữa', '12oz', 76, 45000),
			('Phindi hạnh nhân', '12oz', 28, 45000),	('Phindi choco', '16oz', 143, 49000),
			('Bánh Pasty', '', 32, 29000),				('Bánh chuối', '', 11, 29000),
			('Mousse cacao', '', 48, 29000),			('Trà sen vàng', '12oz', 196, 39000),
			('Trà xanh đậu đỏ', '16oz', 148, 49000),	('Trà sen vàng', '16oz', 175, 49000),
			('Trà Thanh Đào', '12oz', 29, 39000),		('Phô mai trà xanh', '', 37, 29000),
			('Phô mai caramel', '', 44, 29000),			('Freeze chocolate', '12oz', 199, 49000),
			('Chanh dây đá viên', '16oz', 0, 55000),	('Tắc quất đá viên', '12oz', 11, 39000),
			('Chocolate', '', 136, 55000),				('Thạch vải', '', 368, 9000);
															
/*===================================================*/

/*---STAFF TABLE---*/
CREATE TABLE Staff (
StaffID INT(10) UNSIGNED AUTO_INCREMENT PRIMARY KEY,
StaffName VARCHAR(50) NOT NULL,
StaffPhone VARCHAR(13)
);
INSERT INTO Staff(StaffName, StaffPhone) VALUE ('Trịnh Tường Vi', '0869289098'),	
														('Hoàng Trung Kiên', '0372115628'),
														('Cao Đức Đạt', '0963425789'),		
                                                        ('Tống Thu Hà', '0320672178'),	
                                                        ('Nguyễn Trường Giang', '0392774891'),
                                                        ('Đỗ Xuân Quyền', '0912325841'),		
                                                        ('Phạm Nhật Kim Anh', '0331547347'),	
                                                        ('Vũ Thùy Linh', '0398298345'),		
                                                        ('Vũ Quỳnh Trang', '0979809244'),		
                                                        ('Trần Thị Kiều Linh', '0357213743');
/*===================================================*/

/*---INVOICE TABLE---*/
CREATE TABLE Invoice (
InvoiceID INT(10) UNSIGNED AUTO_INCREMENT PRIMARY KEY,
GuestID INT(10) UNSIGNED, FOREIGN KEY (GuestID) REFERENCES Guest(GuestID),
StaffID INT(10) UNSIGNED, FOREIGN KEY (StaffID) REFERENCES Staff(StaffID),
TableID INT(2) UNSIGNED, FOREIGN KEY (TableID) REFERENCES TableCode(TableID),
NumberOfGuest INT(2) UNSIGNED NOT NULL,
OrderDate DATE NOT NULL,
PaymentMethod VARCHAR(10) NOT NULL,
PaidAmount INT NOT NULL,
TheChange INT
);
INSERT INTO Invoice(GuestID, StaffID, TableID, NumberOfGuest, OrderDate, PaymentMethod, PaidAmount, TheChange)
	VALUE	(1, 3, 2, 1, '2021-04-27', 'cash', 30000, 1000),
			(2, 2, 2, 1, '2021-04-30', 'cash', 50000, 1000),
            (3, 6, 4, 1, '2021-04-30', 'cash', 100000, 25000),
            (4, 9, 5, 2, '2021-04-30', 'cash', 120000, 8000),
            (5, 7, 6, 2, '2021-04-30', 'cash', 100000, 10000),
            (6, 4, 7, 2, '2021-04-30', 'cash', 150000, 13000),
            (7, 1, 4, 2, '2021-05-01', 'cash', 100000, 13000),
            (8, 2, 8, 2, '2021-05-01', 'cash', 100000, 16000),
            (9, 1, 11, 4, '2021-05-01', 'creditcard', 189000, 0),
            (10, 7, 6, 2, '2021-05-01', 'cash', 75000, 0),
            (11, 2, 12, 3, '2021-05-01', 'cash', 150000, 20000),
            (12, 9, 14, 1, '2021-05-01', 'cash', 235000, 0),
            (13, 10, 14, 1, '2021-05-01', 'cash', 200000, 32000),
            (14, 6, 14, 1, '2021-05-02', 'cash', 120000, 7000),
            (15, 8, 17, 2, '2021-05-02', 'cash', 85000, 0),
            (16, 9, 16, 2, '2021-05-03', 'cash',110000, 9000),
            (17, 5, 13, 3, '2021-05-03', 'creditcard', 290000, 0),
            (18, 3, 19, 1, '2021-05-03', 'cash', 55000, 0),
            (19, 2, 2, 1, '2021-05-04', 'cash', 155000, 2000),
            (20, 10, 15, 3, '2021-05-04', 'creditcard', 309000, 0),
            (21, 5, 15, 1, '2021-05-05', 'creditcard', 170000, 0),
            (22, 8, 20, 2, '2021-05-05',  'creditcard', 250000, 0),
            (23, 1, 10, 2, '2021-05-06', 'cash', 200000, 49000), 
            (24, 2, 18, 1, '2021-05-06', 'creditcard', 245000, 0);
/*===================================================*/

/*---ORDER-DETAIL TABLE---*/
CREATE TABLE OrderDetail (
InvoiceID INT(10) UNSIGNED, FOREIGN KEY (InvoiceID) REFERENCES Invoice(InvoiceID),
ProductID INT(10) UNSIGNED, FOREIGN KEY (ProductID) REFERENCES Product(ProductID),
UnitPrice INT NOT NULL,
Quantity INT NOT NULL,
Discount INT NOT NULL,
Total INT AS ((UnitPrice*Quantity) - Discount)
);
INSERT INTO OrderDetail(InvoiceID, ProductID, UnitPrice, Quantity, Discount)
	VALUE	(1, 3, 29000, 1, 0 ),		
			(2, 11, 49000, 1, 0),		
            (3, 13, 39000, 2, 3000),		
            (4, 13, 29000, 2, 1000),	(4, 17, 55000, 1, 0),
            (5, 1, 35000, 1, 0),		(5, 19, 55000, 1, 0),
            (6, 8, 29000, 2, 3000),		(6, 20, 9000, 20, 8000),
            (7, 10, 39000, 1, 0),		(7, 12, 49000, 1, 1000),
            (8, 18, 39000, 1, 0),		(8, 4, 45000, 1, 0),
            (9, 16, 49000, 1, 0),		(9, 6, 49000, 2, 3000),
            (9, 5, 45000, 1, 0),
            (10, 13, 39000, 2, 3000),
            (11, 2, 39000, 2, 3000),	(11, 4, 29000, 2, 3000),
            (12, 6, 49000, 5, 10000),
            (13, 9, 29000, 6, 6000),
            (14, 10, 39000, 3, 4000),
            (15, 14, 29000, 3, 2000),
            (16, 13, 29000, 2, 1000),	(16, 20, 9000, 5, 2000),
            (17, 16, 49000, 6, 4000),
            (18, 17, 55000, 1, 0),
            (19, 2, 39000, 4, 3000),
            (20, 8, 29000, 5, 4000),	(20, 2, 39000, 3, 2000),
            (20, 20, 9000, 6, 1000),
            (21, 4, 45000, 4, 10000),
            (22, 15, 29000, 9, 11000),
            (23, 6, 49000, 2, 3000), 	(23, 7, 29000, 2, 2000),
            (24, 11, 49000, 5, 10000);
/*===================================================*/

/*---SUPPLIER TABLE---*/
CREATE TABLE Supplier (
SupplierID INT(10) UNSIGNED AUTO_INCREMENT PRIMARY KEY,
CompanyName VARCHAR(30) NOT NULL,
SupplierPhone VARCHAR(13) NOT NULL,
SupplierAddress VARCHAR(30)
);
INSERT INTO Supplier(CompanyName, SupplierPhone, SupplierAddress)
	VALUE	('Nguyễn Sơn', '0969454545', 'Bắc Từ Liêm - Hà Nội'),
			('Mega Market', '02253528128', 'Bắc Từ Liêm - Hà Nội'),
			('Kim Cương', '0963131419', 'Hai Bà Trưng - Hà Nội'),
            ('DalatMilk', '0901778775', 'Cầu Giấy - Hà Nội'),
            ('Thành Đạt', '0904192388', 'Hoàng Mai - Hà Nội'),
            ('An Phú', '0982636618', 'Ba Vì - Hà Nội'),
            ('Abby', '1900779907', 'Hà Đông - Hà Nội'),
            ('ĐVP Market', '0907309988', 'Bắc Từ Liêm - Hà Nội'),
            ('Nhất An', '0931847626', 'Ba Vì - Hà Nội'),
            ('United Vision', '0902888461', 'Ba Đình - Hà Nội');
/*===================================================*/

/*---INVOICE TABLE---*/
CREATE TABLE VendorInvoice (
VendorInvoiceID INT(10) UNSIGNED AUTO_INCREMENT PRIMARY KEY,
StaffID INT(10) UNSIGNED, FOREIGN KEY (StaffID) REFERENCES Staff(StaffID),
ImportDate DATE NOT NULL
);
INSERT INTO VendorInvoice(StaffID, ImportDate) VALUE	(2, '2021-01-19'),
														(1, '2021-01-31'),
														(3, '2021-02-16'),
														(6, '2021-02-28'),
														(7, '2021-03-01'),
														(8, '2021-03-15'),
														(10, '2021-04-01'),
														(2, '2021-04-19'),
														(6, '2021-05-02'),
														(4, '2021-05-24');
/*===================================================*/

/*---WAREHOUSE-ENTRY TABLE---*/
CREATE TABLE WarehouseEntry (
VendorInvoiceID INT(10) UNSIGNED, FOREIGN KEY (VendorInvoiceID) REFERENCES VendorInvoice(VendorInvoiceID),
ProductID INT(10) UNSIGNED, FOREIGN KEY (ProductID) REFERENCES Product(ProductID),
UnitRequired INT NOT NULL,
SupplierID INT(10) UNSIGNED, FOREIGN KEY (SupplierID) REFERENCES Supplier(SupplierID),
Note VARCHAR(100)
);
INSERT INTO WarehouseEntry(VendorInvoiceID, ProductID, UnitRequired, SupplierID, Note)
	VALUE	(1, 5, 200, 6, ''),	(1, 2, 200, 7, ''),	(1, 4, 200, 2, ''),
			(2, 1, 200, 1, ''),	(2, 6, 200, 4, ''),	(2, 9, 200, 10, ''),
			(3, 14, 200, 2, ''),(3, 11, 200, 3, ''),(3, 20, 500, 6, ''),
			(4, 17, 150, 9, ''),(4, 15, 350, 10, ''),
            (5, 13, 200, 4, ''),(5, 15, 10, 4, 'Change for new ones'),
            (6, 7, 150, 3, ''),	(6, 18, 150, 7, ''),
            (7, 14, 300, 2, ''),(7, 11, 350, 2, ''),
            (8, 6, 300, 8, 'Prepare for Liberation Day'),	(8, 4, 500, 9, 'Prepare for Liberation Day'),
            (9, 1, 500, 10, ''),
            (10, 2, 500, 6, '');
            
/*===================================================*/

									/*==========================================================*/		 
									/*		Question 1.	Manage the history of guests payment.	*/
									/*==========================================================*/
                                    
                            CREATE VIEW PaidHistory AS        
							SELECT Guest.GuestID, InvoiceID, OrderDate, PaymentMethod, PaidAmount, TheChange
							FROM Invoice
							INNER JOIN Guest ON Guest.GuestID = Invoice.GuestID
                            ORDER BY OrderDate ASC;
													SELECT * FROM PaidHistory;

					/*======================================================================================*/		 
					/*		Question 2.	At a specific date, what is the amount of each product was sold?	*/
					/*======================================================================================*/
                        
										CREATE VIEW SaleAtDate AS
										SELECT Pro.ProductID, Pro.ProductName, Pro.Size,
										SUM(Ordd.Quantity) as Quantity, Invoice.OrderDate AS SOLD_DATE
										FROM ((OrderDetail Ordd
										INNER JOIN Product Pro ON Pro.ProductID = Ordd.ProductID)
										INNER JOIN Invoice ON Ordd.InvoiceID = Invoice.InvoiceID)
										GROUP BY SOLD_DATE, ProductID
										ORDER BY SOLD_DATE ASC;
                                        
													SELECT * FROM SaleAtDate;
										
							/*==============================================================*/		 
							/*		Question 3.	What is the top 5 Best-Seller products?		*/
							/*==============================================================*/   
									
                            CREATE VIEW BestSeller AS
							SELECT Pro.ProductID, Pro.ProductName, Pro.Size, Pro.UnitPrice,
								   Ordd.Discount, SUM(Ordd.Quantity) AS Sold_out, Ordd.Total AS Profit
							FROM Product Pro
							INNER JOIN OrderDetail Ordd ON Pro.ProductID = Ordd.ProductID
							GROUP BY ProductID
							ORDER BY Total DESC
							LIMIT 5;
												SELECT * FROM BestSeller;
							
						/*======================================================================================*/		 
						/* 		Question 4.	The difference of days between today and the latest supply day		*/
						/*======================================================================================*/  
							
                            CREATE VIEW DayDiff AS
							SELECT GR.VendorInvoiceID, EI.StaffID, Supplier.SupplierID, Supplier.CompanyName, GR.Note,
								   EI.ImportDate AS Lastest_Supply_Day, CURDATE() AS Today,
                                   DATEDIFF(CURDATE(), EI.ImportDate) AS Day_Interval
							FROM ((WarehouseEntry GR
							INNER JOIN VendorInvoice EI ON EI.VendorInvoiceID = GR.VendorInvoiceID)
							INNER JOIN Supplier ON Supplier.SupplierID = GR.SupplierID)
							ORDER BY VendorInvoiceID DESC
                            LIMIT 1;
														SELECT * FROM DayDiff;
							/*======================================================================*/		 
							/* 		Question 5. Total number of products and their revenue on		*/
							/*			Reunification Day and International Workers' Day			*/
							/*======================================================================*/  
                                    
                         CREATE VIEW SaleOn5D1 AS
                         SELECT Pro.ProductID, Pro.ProductName, Invoice.OrderDate AS Sold_date,
								SUM(Ordd.Quantity) AS Sold_out, SUM(Ordd.Discount) AS Total_discount, Ordd.Total AS Revenue
						 FROM ((OrderDetail Ordd
                         INNER JOIN Product Pro ON Pro.ProductID = Ordd.ProductID)
                         INNER JOIN Invoice ON Invoice.InvoiceID = Ordd.InvoiceID)
                         WHERE OrderDate = '2021-05-01' OR OrderDate = '2021-04-30'
                         GROUP BY ProductID
						 ORDER BY Sold_date ASC;
														SELECT * FROM SaleOn5D1;
							 
								/*==============================================================*/		 
								/* 		Question 6. Manage total revenue with payment method	*/
								/*==============================================================*/  
									
							CREATE VIEW RevPayMethod AS
							SELECT Invoice.PaymentMethod, COUNT(DISTINCT(Invoice.InvoiceID)) AS Number_Of_Invoice,
								   SUM(Ordd.Quantity) AS Sold_out, SUM(Ordd.Total) AS Revenue
							FROM OrderDetail Ordd
							INNER JOIN Invoice ON Invoice.InvoiceID = Ordd.InvoiceID
							GROUP BY PaymentMethod
							ORDER BY Revenue DESC;
												SELECT * FROM RevPayMethod;
                                                    
								/*===============================================================*/		 
								/* Question 7. Supply of Product 'Chanh dây đá viên' has arrived */
								/*    And now we should update the database with this new one    */
								/*	  		  Show the new-added Product on the screen			 */
								/*					    (Transaction in used)					 */
								/*===============================================================*/   
                                
							ALTER TABLE Product ADD CHECK (QuantityPerUnit <= 1500);
                            /*Transaction will rollback when QuantityPerUnit > 1500 because of the maximum storage's capaity*/
                            
							START TRANSACTION;
                            SET AUTOCOMMIT = ON;
                            UPDATE Product
							SET QuantityPerUnit = QuantityPerUnit + 300
							WHERE ProductID = 17;							
							INSERT INTO VendorInvoice(StaffID, ImportDate) VALUE (1, CURDATE() );
														/*Only Date is inserted, time is not included*/
							INSERT INTO WarehouseEntry(VendorInvoiceID, ProductID, UnitRequired, SupplierID, Note)
									SELECT MAX(VendorInvoiceID) + 1, 17, 300, 10, 'New Supply' FROM WarehouseEntry;
										/* Insert new InvoiceID = Max(InvoiceID) + 1 */					
							COMMIT;
                            
							/*Display on the screen*/
							SELECT GR.VendorInvoiceID, GR.ProductID, Pro.ProductName, Pro.QuantityPerUnit, Supplier.CompanyName, GR.Note
							FROM ((WarehouseEntry GR
							INNER JOIN Product Pro ON Pro.ProductID = GR.ProductID)
							INNER JOIN Supplier ON Supplier.SupplierID = GR.SupplierID)
							ORDER BY VendorInvoiceID DESC
							LIMIT 1;
							
                            					
								/*==================================================================*/		 
								/* 			  Question 8. The data of a product has changed			*/
								/*		And the manager want to manage the history of the change	*/
                                /*							(Trigger in used)						*/
								/*==================================================================*/  
								
									CREATE TABLE HistoryProduct (
									ProductHistoryID INT(10) UNSIGNED AUTO_INCREMENT PRIMARY KEY,
									ProductID INT(10) UNSIGNED NOT NULL,
									ProductName VARCHAR(30),
									Size VARCHAR(5),
									QuantityPerUnit INT,
									UnitPrice INT,
									ChangeDate DATE NOT NULL
									); 
                                    
									/*USE TRIGGER*/
									CREATE TRIGGER Before_change_product
									BEFORE UPDATE ON Product
									FOR EACH ROW
										INSERT INTO HistoryProduct
											SET		ProductID = OLD.ProductID,
													ProductName = OLD.ProductName,
													Size = OLD.Size,
													QuantityPerUnit = OLD.QuantityPerUnit,
													UnitPrice = OLD.UnitPrice,
													ChangeDate = CURDATE();
                                    /*DROP TRIGGER Before_change_product;*/
                                    
                                    /*Demo with Thạch vải*/
									UPDATE Product
                                    SET ProductName = 'Thạch vải nhập khẩu',
										QuantityPerUnit = 500,
										UnitPrice = 10000
                                    WHERE ProductName = 'Thạch vải';
								
					/*==============================================================================================*/		 
					/*		Question 9. The manager wants to print out all the vendor invoice of 20/4 to 05/25		*/
					/*										(Procedure in used)										*/
					/*==============================================================================================*/  
							
                             /*DEFINER should be change to user's local host before being used*/
                             
							USE `highland`;
							DROP procedure IF EXISTS `ManageDiscount`;
							DELIMITER $$
							USE `highland`$$
							CREATE DEFINER=`root`@`localhost` PROCEDURE `PrintVendorInvoice`()
							BEGIN
								SELECT GR.VendorInvoiceID, GR.ProductID, Pro.ProductName, Pro.Size, Pro.QuantityPerUnit, Pro.UnitPrice,
                                (Pro.QuantityPerUnit * UnitPrice) AS TotalVendor, VI.ImportDate,
                                Supplier.CompanyName, GR.Note
								FROM (((WarehouseEntry GR
								INNER JOIN Product Pro ON Pro.ProductID = GR.ProductID)
								INNER JOIN Supplier ON Supplier.SupplierID = GR.SupplierID)
                                INNER JOIN VendorInvoice VI ON VI.VendorInvoiceID = GR.VendorInvoiceID)
                                WHERE VI.ImportDate BETWEEN '2021-04-20' AND '2021-05-25'
								ORDER BY VendorInvoiceID ASC;
					
							END$$
							DELIMITER ;
                            
                            CALL PrintVendorInvoice();
                            
				/*================================================================================================================*/  
				/*						   Question 10. Today 05/05/2021, we arrive at work and discover that					  */
				/*        our new data entry clerk in training has entered all new Invoice incorrectly on the last 3 days.		  */
				/*					We wish to teach our new trainee to find and correct all erroneous records.					  */
				/*        What’s the easiest way to get all the records from the Invoice table entered on the last 3 days?		  */
				/*================================================================================================================*/  
                
                /*See erroneous records*/
                SELECT * FROM Invoice 
				WHERE OrderDate BETWEEN '2021-05-03' AND '2021-05-05';
                /*Update*/
                UPDATE Invoice
                SET		TableID = TableID - 1
               	WHERE TableID > 1 AND OrderDate BETWEEN '2021-05-03' AND '2021-05-05';
                            
/*===================================================*/
/* SOME USEFUL COMMAND
ALTER TABLE () MODIFY COLUMN () INT(10) UNSIGNED AUTO_INCREMENT;
ALTER TABLE () RENAME COLUMN () TO ();
SELECT * FROM ();
DELETE FROM ();
DROP TABLE ();
*/
/*===================================================*/
