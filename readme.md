# Hướng dẫn config mạng cho bbb
# Issue

Ban đầu khi gõ ifconfig nó sẽ hiện như sau , kiểm tra không có /dev/usb0 và /dev/usb1
```
debian@arm:~$ ifconfig
eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.0.104  netmask 255.255.255.0  broadcast 192.168.0.255
        inet6 fe80::6a3:16ff:feac:24d7  prefixlen 64  scopeid 0x20<link>
        ether 04:a3:16:ac:24:d7  txqueuelen 1000  (Ethernet)
        RX packets 3295  bytes 218003 (212.8 KiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 656  bytes 50834 (49.6 KiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 12  bytes 1658 (1.6 KiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 12  bytes 1658 (1.6 KiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
```

### Cách làm 

Yêu cầu cần cắm ethernet cho board bbb trước để nó có mạng sau đó chúng ta sẽ tải source từ mạng về cho board

Thực hiện trên board như sau 

```
sudo apt update
sudo apt install bb-usb-gadgets
```

Link : https://github.com/rcn-ee/repos/tree/master/bb-usb-gadgets/suite/bullseye/debian

Kích hoạt usb khởi động cùng systemd 
```
sudo systemctl enable --now bb-usb-gadgets.service

```

Kiểm tra thử status của nó
```
sudo systemctl status bb-usb-gadget
```

Reboot lại 
```
sudo reboot
```

Bây giờ board sẽ có thể chạy một cách bình thường rồi.

Khi chạy nó sẽ tạo một phân vùng bbb và bạn cần config mạng trên máy nữa.

Đối với mỗi máy sẽ khác nhau 

Máy win : https://www.digikey.com/en/maker/blogs/how-to-connect-a-beaglebone-black-to-the-internet-using-usb
