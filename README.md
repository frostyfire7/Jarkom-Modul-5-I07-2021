# Jarkom-Modul-5-I07-2021

Ascarya Arkaandhiyaa Allaam (05111942000027)\
Farah Dhiah Qorirah (05111942000018)\
Julius Adetya Eka Bhaswara (05111942000026)

## (A) Tugas pertama kalian yaitu membuat topologi jaringan sesuai dengan rancangan yang diberikan Luffy dibawah ini

![image](https://user-images.githubusercontent.com/77782259/145575814-f089ae9d-b104-4f81-b3c6-706245711bb1.png)

Keterangan :\
    Doriki adalah DNS Server\
		Jipangu adalah DHCP Server\
		Maingate dan Jorge adalah Web Server\
		Jumlah Host pada Blueno adalah 100 host\
		Jumlah Host pada Cipher adalah 700 host\
		Jumlah Host pada Elena adalah 300 host\
		Jumlah Host pada Fukurou adalah 200 host
    
## (B) Karena kalian telah belajar subnetting dan routing, Luffy ingin meminta kalian untuk membuat topologi tersebut menggunakan teknik CIDR atau VLSM. setelah melakukan subnetting

### Subnet

![image](https://user-images.githubusercontent.com/77782259/145575912-62376fd7-1953-469b-a1f9-b9a5f63febf2.png)

### Tabel Subnet
**Subnet**|**Node**|**IP**|**Subnet Mask**|**Length**|
:-------:| :-------:|:-------:|:-------:|:-------:|
| A | Water7  	|  10.41.7.1	|  255.255.255.128	|	/25  	|
| A | Blueno	|  10.41.7.2  	|  255.255.255.128	|	    	|
| B | Water7	|  10.41.7.129  |  255.255.255.248	|	/29    	|
| B | Doriki	|  10.41.7.130  |  255.255.255.248	|	    	|
| B | Jipangu	|  10.41.7.131  |  255.255.255.248	|	    	|
| C | Water7	|  10.41.0.1  	|  255.255.252.0	|	/22    	|
| C | Ciper	|  10.41.0.2  	|  255.255.252.0	|	   	|
| D | Foosha	|  10.41.7.145	|  255.255.255.252	|	/30    	|
| D | Water7	|  10.41.7.146	|  255.255.255.252	|	    	|
| E | Foosha	|  10.41.7.149	|  255.255.255.252	|	/30    	|
| E | Guanhao	|  10.41.7.150	|  255.255.255.252	|	    	|
| F | Guanhao	|  10.41.6.1  	|  255.255.255.0	|	/24    	|
| F | Elena	|  10.41.6.2  	|  255.255.255.0	|	    	|
| G | Guanhao	|  10.41.7.137	|  255.255.255.248	|	/29  	|
| G | Jorge	|  10.41.7.138	|  255.255.255.248	|	    	|
| G | Maingate	|  10.41.7.139	|  255.255.255.248	|	    	|
| H | Guanhao	|  10.41.4.2  	|  255.255.254.0	|	/23   	|
| H | Fukurou	|  10.41.4.2  	|  255.255.254.0	|	    	|


### Subnet Tree

![image](https://user-images.githubusercontent.com/77782259/145576019-e57c86fd-c4e6-4421-9913-8c29e258a3c5.png)

