--create Employee Table
CREATE TABLE EMPLOYEES(
    employee_id NUMBER(6),
    last_name VARCHAR2(25) NOT NULL,
    first_name VARCHAR2(25) NOT NULL,
    phone_number NUMBER(14),
    email VARCHAR2 (25),
    salary NUMBER(6),
    cust_adress VARCHAR2(30),
    job_id NUMBER(6),
    CONSTRAINT email UNIQUE(employee_id),
    CONSTRAINT job_id 
    FOREIGN KEY (job_id) REFERENCES jobs(job_id)
);
-- create JOBs table
CREATE TABLE JOBS(
    job_id NUMBER(10),
    job_title VARCHAR2(35),
    min_salary NUMBER(6),
    max_salary NUMBER (6)
);
-- create JOB HISTORY table
CREATE TABLE JOB_HISTORY(
    CONSTRAINT employee_id 
    FOREIGN KEY (employee_id) REFERENCES employees(employee_id),
    start_date DATE,
    end_date DATE,
    CONSTRAINT job_id 
    FOREIGN KEY (job_id) REFERENCES jobs(job_id)
);
--CREATE Customers talbe
CREATE TABLE CUSTOMERS(
    customer_id NUMBER(6),
    cust_last_name VARCHAR2(25) NOT NULL,
    cust_first_name VARCHAR2(25) NOT NULL,
    cust_phone_number NUMBER(14),
    email VARCHAR2 (25),
    cust_password NUMBER(6),
    cust_adress VARCHAR2(30),
    cust_piont NUMBER(6),
    CONSTRAINT material_id 
    FOREIGN KEY (material_id) REFERENCES car_brand(material_id)
);
--Manifacturers table
CREATE TABLE MANIFACTURERS(
    manifacturer_id NUMBER(6) PRIMARY KEY,
    manifacturer_name VARCHAR2(25) NOT NULL,
    place_of_product VARCHAR2(25) NOT NULL,
    type_of_material VARCHAR2(30)
);
-- Products table
CREATE TABLE PRODUCTS(
    product_id NUMBER(6) PRIMARY KEY,
    product_name VARCHAR2(25) NOT NULL,
    color VARCHAR2(25),
    price NUMBER(6),
    number_product NUMBER (6),
    point_product NUMBER(6),
    manifacturer_id NUMBER(6),
    material_id NUMBER(6),
    CONSTRAINT mani_id 
    FOREIGN KEY (manifacturer_id) REFERENCES manifacturers(manifacturer_id)
);
ALTER TABLE products ADD picture VARCHAR(25);
--Car brand table
CREATE TABLE CAR_BRAND(
    car_id NUMBER(6),
    brand_name VARCHAR2(25) NOT NULL,
    model_name VARCHAR2(25) NOT NULL,
    material_id NUMBER(14)
);
-- add column
ALTER TABLE car_brand ADD year_in_issue NUMBER(6);
-- create table for delivery
CREATE TABLE DELIVERY(
    delivery_id NUMBER(6),
    product_id NUMBER(6),
    customer_id NUMBER(6),
    employee_id NUMBER(6),
    CONSTRAINT product_id 
    FOREIGN KEY (product_id) REFERENCES products(product_id),
    CONSTRAINT customer_id 
    FOREIGN KEY (customer_id) REFERENCES customers(customer_id),
     CONSTRAINT employee_id 
    FOREIGN KEY (employee_id) REFERENCES employees(employee_id)
);

-- add info for car_brand
INSERT INTO car_brand(car_id,brand_name,model_name,material_id,year_in_issue)
VALUES  (1,'Toyota','Camry',01);
INSERT INTO car_brand(year_in_issue) VALUES (2001);
INSERT INTO car_brand(car_id,brand_name,model_name,material_id,year_in_issue)
VALUES  (2,'Toyota','Camry',02,2002);
INSERT INTO car_brand(car_id,brand_name,model_name,material_id,year_in_issue)
VALUES  (3,'BMW','M3',03,2005);

-- add info for customers
INSERT INTO customers(customer_id,cust_last_name,cust_first_name,cust_phone_number,email,
    cust_password,cust_adress,cust_point,user_name)
    VALUES (1,'John','Cena',87781027832,'johncena@gmail.com',123456,'Nur-Sultan Abay 24',0);
INSERT INTO customers(customer_id,cust_last_name,cust_first_name,cust_phone_number,email,
    cust_password,cust_adress,cust_point,user_name)
    VALUES (2,'Jack','Chins',87078521479,'jacknchins@gmail.com',85971,'Nur-Sultan Mukhtarova 5',1);
INSERT INTO customers(customer_id,cust_last_name,cust_first_name,cust_phone_number,email,
    cust_password,cust_adress,cust_point,user_name)
    VALUES (3,'Ivan','Petka',87781027832,'ivanpetka@gmail.com',1286,'Almaty Al-Farabi 50',2);
--empoyee
INSERT INTO employees(employee_id,first_name,last_name,email,phone_number,hire_date,job_id,salary)
    VALUES (1,'Dog','Bull','bulldog@gmail.com',87777418523,DATE '2017-12-25','AD_PRES',1500);

-- add info for jobs table
INSERT INTO customers(job_id,job_title,min_salary,max_salary)
    VALUES (1,deliveryman,1000,2500);
INSERT INTO customers(job_id,job_title,min_salary,max_salary)
    VALUES (2,deliveryman,1550,3500);
INSERT INTO customers(job_id,job_title,min_salary,max_salary)
    VALUES (1,seller,5000,7500);
INSERT INTO customers(job_id,job_title,min_salary,max_salary)
    VALUES (1,seller,5000,7500);

-- add info for manifacturers
INSERT INTO manifacturers(manifacturer_id,manifacturer_name,place_of_product,type_of_material)
    values(1,'Toyota Company','Kazakhstan Nur-Sultan','metal');
INSERT INTO manifacturers(manifacturer_id,manifacturer_name,place_of_product,type_of_material)
    values(2,'BMW Company','Germany M?nchen','metal');

-- add info for products table
INSERT INTO products (product_id,product_name,color,price,number_product,point_product,material_id)
    VALUES (1,'povorotniki','white',100,10,2,2);
INSERT INTO products (product_id,product_name,color,price,number_product,point_product,manifacturer_id,material_id)
    VALUES (2,'kapot','black',215,5,5,2,2);

--add info for delivery
INSERT INTO delivery(delivery_id,product_id,customer_id,employee_id)
    VALUES (1,1,1,1);
    
-- SELECT all table
select * from car_brand;
select * from customers;
select * from employees;
select * from job_history;
select * from jobs;
select * from products;
select * from delivery;
select * from manifacturers