Bu repo'nun amacı elimdeki Rasberry Pi 3'ün serüvenini belgelemek.

Ubuntu Server kurulumundan sonra kullanıcı adı ubuntu ve şifresi ubuntu olarak çalışmaya başladım.

Bence ilk sorun klavye nin türkçe olmamasıydı. Bunu çözmek için hem 
```
sudo dpkg-reconfigure keyboard-configuration
```
hem de 
```
sudo dpkg-reconfiguration -plow console-setup
```
çalıştırıp gerekli seçimleri yaptım.

Maalesef wifi tanıtamadım. Kablo bağlantısıyla yolumuza devam ediyorum. İlk planda bu sorunu çözmek olacaktır.

##SAMBA Kurulumu


https://ubuntu.com/tutorials/install-and-configure-samba#1-overview

```
sudo apt update
sudo apt install samba
mkdir /home/ubuntu/sambashare/
sudo vi /etc/samba/smb.conf
```

```
[sambashare]
	comment = Samba on Rasberry Pi 3
	path = /home/ubuntu/sambashare
	read only = no
	browsable = yes
```
sudo service samba restart
sudo ufw allow samba

##DLNA Server Kurulumu

Digital Living Network Alliance, Bir grup kişisel bilgisayar ve tüketici elektroniği şirketlerinin 2003 yılında kurduğu bir birliktir. 

Rasberry Pi 3 için çok da sistemi yormayan bir DLNA server olarak miniDLNA'i tercih ettim. İlkel bir arayüzü olmasına karşın iş görüyor. 
```
sudo apt install minidlna
```
Bağladığınız usb bellek veya  
