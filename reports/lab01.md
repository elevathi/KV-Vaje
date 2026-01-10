# Lab 01 - Uvod v Kali Linux

## Sistemske informacije

### whoami
```
kali
```

### hostnamectl
```
Static hostname: kali
      Icon name: computer-vm
        Chassis: vm
  Virtualization: vmware
Operating System: Kali GNU/Linux Rolling
          Kernel: Linux 6.17.10+kali-amd64
    Architecture: x86-64
 Hardware Vendor: VMware, Inc.
  Hardware Model: VMware Virtual Platform
```

### uname -a
```
Linux kali 6.17.10+kali-amd64 #1 SMP PREEMPT_DYNAMIC Kali 6.17.10-1kali1 (2025-12-08) x86_64 GNU/Linux
```

### df -h
```
Filesystem      Size  Used Avail Use% Mounted on
udev            865M     0  865M   0% /dev
tmpfs           194M  1.2M  193M   1% /run
/dev/sda1        79G   19G   56G  26% /
tmpfs           969M  4.0K  969M   1% /dev/shm
tmpfs           969M  8.0K  969M   1% /tmp
tmpfs           194M  116K  194M   1% /run/user/1000
```

### ip a
```
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536
    inet 127.0.0.1/8 scope host lo
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500
    inet 192.168.227.129/24 brd 192.168.227.255 scope global dynamic noprefixroute eth0
```

### which nmap / john
```
/usr/bin/nmap
/usr/sbin/john
```

## Namestitev in uporaba orodij

### htop
Uspesno zagnan - prikazuje sistemske procese in porabo virov.

### traceroute microsoft.com
```
traceroute to microsoft.com (13.107.213.44), 30 hops max
1  192.168.227.2  0.418 ms
2-30  * * * (paketi blokirani - tipicno za NAT/firewall)
```

### strings /bin/ls | head
```
!/lib64/ld-linux-x86-64.so.2
_ITM_deregisterTMCloneTable
__gmon_start__
_ITM_registerTMCloneTable
fgetfilecon_raw
...
```

### nload
Uspesno namescen in zagnan - graficni prikaz omreznega prometa.

### speedtest-cli --secure
```
Testing from Telekom Slovenije (188.197.202.55)...
Hosted by COSYS DATA GmbH (Vienna) [235.73 km]: 20.064 ms
Download: 277.17 Mbit/s
Upload: 50.15 Mbit/s
```

### tcpdump -c 10
```
listening on eth0, link-type EN10MB (Ethernet)
09:19:26.393860 IP 192.168.227.1.54736 > 239.255.255.250.1900: UDP, length 170
09:19:26.425803 IP 192.168.227.1.54741 > 239.255.255.250.1900: UDP, length 170
... (zajeti DNS in UDP paketi)
10 packets captured
```

## Varnostna orodja

### nmap -O 192.168.1.101
```
Nmap scan report for 192.168.1.101
Host is up (0.0014s latency).
PORT   STATE SERVICE
21/tcp open  ftp
Warning: OSScan results may be unreliable (manjka zaprta vrata)
```

### searchsploit wordpress ftp
```
WordPress Plugin MiwoFTP 1.0.5 - Arbitrary File Download (1)     | php/webapps/36774.txt
WordPress Plugin MiwoFTP 1.0.5 - Arbitrary File Download (2)     | php/webapps/36801.txt
WordPress Plugin MiwoFTP 1.0.5 - CSRF / Arbitrary File Creation  | php/webapps/36763.txt
WordPress Plugin MiwoFTP 1.0.5 - CSRF / Arbitrary File Deletion  | php/webapps/36761.txt
WordPress Plugin MiwoFTP 1.0.5 - Multiple CSRF/XSS               | php/webapps/36762.txt
```

### dnsenum microsoft.com
Rezultati:
- **Host's addresses:** 13.107.213.44, 13.107.246.44
- **Name Servers:** ns1-39.azure-dns.com, ns2-39.azure-dns.net, ns3-39.azure-dns.org, ns4-39.azure-dns.info
- **Mail Servers:** microsoft-com.mail.protection.outlook.com
- **Zone Transfer:** REFUSED (pravilno konfigurirano)
- **Brute force subdomains:** accounts, admin, ads, apps, asia, autodiscover, beta, dev, forums, ftp, linux, mail, mobile, news, office, owa, portal, privacy, search, secure, shop, smtp, www, ...

### lbd microsoft.com
```
Checking for DNS-Loadbalancing: FOUND
microsoft.com has address 13.107.213.44
microsoft.com has address 13.107.246.44

microsoft.com does Load-balancing. Found via Methods: DNS
```

### nth -t ef487f75307f96954d3bb132e5f4b035
```
Most Likely:
- MD5, HC: 0 JtR: raw-md5 (Used for Linux Shadow files)
- MD4, HC: 900 JtR: raw-md4
- NTLM, HC: 1000 JtR: nt (Often used in Windows Active Directory)
- Domain Cached Credentials, HC: 1100 JtR: mscach
```

## Refleksija

**Zakaj uporabljamo Kali Linux?**
Kali Linux uporabljamo za preverjanje kako uspesen je nas hardening (utrjevanje sistemov). Omogoca nam izvajanje penetracijskih testov in odkrivanje ranljivosti pred napadalci.

**Prednost Kali Linux v primerjavi z ostalimi distribucijami?**
Prednost je da ima veliko varnostnih orodij (600+) ze namescenih in konfiguriranih za takojsnjo uporabo.

**Katere funkcionalnosti so vas najbolj pritegnile?**
Je orodje za delo - prakticno za varnostne preglede.
