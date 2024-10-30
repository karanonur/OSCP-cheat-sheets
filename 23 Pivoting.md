### #Pivoting 

### Pivoting is a post exploitation technique that involves utilizing a compromised host that is connected to multiple networks to<span style="background:#d4b106"> gain access to systems within other networks.</span>

## Meterpreter provides us with the ability to <span style="background:#ff4d4f">add a network route to the internal network’s subnet</span>, perform <span style="background:#d4b106">port forwarding</span> and consequently scan and exploit other systems on the network.

## Port Forwarding
##### + Port forwarding is the process of <span style="background:#d3f8b6">redirecting traffic from a specific port on a target system to a specific port on our system.</span>
##### + In the context of pivoting, <span style="background:#ff4d4f">we can forward a remote port on a previously inaccessible host to a local port on our Kali Linux system</span> so that we can remotely interact/exploit the service running on the port.
### Trafiği yeniden yönlendirip senin istediğin porta yönlendirme yapmalısın.

![[Pasted image 20240422212408.png]]
## Durum şu ben victim-1 'A eirişm sağladım. Burada local enumeration yaptım ve ipconfig yaptığımda şunu gördüm. Bu victim var 2 ağa bağlı. Diğer ağı taramak için oradaki hostları belirlemek için route özelliğini lullandış ve oraya host taraması yaptık ve oradaki hedefleri bulduk.

### Bu bulduğumuz ikinci networkde ki host'ların portlarıyla alakalı bilgi almak için veya buraya exploit etmek için port forwarding yapmalıyım.

## Örnek uzak hedefteki port 80'e herhangi bir işlem yapmak için nmap scan yapmak için bu portu bizim port 1234' forward yapıyoruz ve ben port 1234'e yaptığım nmapscan bana uzak hedefin enumeration'unnu yapıyor.




##### Pivoting kafa karıştırıcı olabilir. Çünkü 2 tane akış var 1 tanesi senin direk erişim sağladığın.  Diğeri ise senin erişim sağladığın hedef üzerinden eriştiğin uzak hedef denilebilir.
### Bu senin erişim sağladığın sistem üzerinden ulaştığın sistem bir DMZ demilitarized zone da olabilir veya farklı bir network de olabilir.
  

---

## LAb
### rejetto ile erişim sağladık
## getsystem ile NT/Authority olduk.

# Pivoting için en önemli enum IPCONFIG


![[Pasted image 20240422220922.png]]
![[Pasted image 20240422220910.png]]
![[Pasted image 20240422220953.png]]
![[Pasted image 20240422221003.png]]
### Öğretmen yaparken #route işlemini hedefin subnetine göre verdi ve  
### meterpreter> run autoroute -s 10.0.29.0/20
## subnetten dolayı 20 oldu.
![[Pasted image 20240422221333.png]]
### meterpreter> run autoroute -s 10.0.2.0/24
![[Pasted image 20240422221549.png]]
##### Bizim subnet 255.255.255.0 o yüzden 
![[Pasted image 20240422221859.png]]
### #CIDR Classless Inter-Domain Routing

---

### meterpreter> run autoroute -s 10.0.2.0/24
![[Pasted image 20240422222507.png]]
## Burası bizim active route table'ımız. Yani bu şu demek biz şu an <span style="background:#ff4d4f">MSFCONSOLE </span>ile uzaktaki nat network ağındaki diğer hedeflere erişebiliriz. <span style="background:#ff4d4f">YALNIZ MSFCONSOLE ile unutma.</span>

### Bu yüzdne biz eğer bir tarama yapacaksak MSFCONSOLE içindeki TCP scan module kullanarak yapacağız. nmap üzerinden nmap sorgusu yaptığımız 
![[Pasted image 20240422222841.png]]
# bu komut çalışmaz.
![[Pasted image 20240422222938.png]]

---
## msf6> use auxilary(scanner/portscan/tcp)

![[Pasted image 20240422225630.png]]
![[Pasted image 20240422225721.png]]

### Ben win7 DE smb eternalblue zaafiyeti olduğunu bildiğimden buna bind_tcp  payload ile bağlanabildim.
![[Pasted image 20240422225859.png]]
![[Pasted image 20240422225802.png]]

---

## Ancak hedefi bilmeseyim nasıl bulacaktım port'larda ne çalışıyor Diyelim ki tamamen Black-Box bir test yapıyoruz......

### O zaman biz msfconsole içinden enumeration yapamayız tek tek portları taramak farklı farklı modullerle ve banner grabing yapmak inanılmaz zor olur bizim #nmap'e ihtiyacımız var.
# O zaman çare Port Forwarding'te

---

## Port Forwarding 
![[Pasted image 20240422230339.png]]
### bizim senaryomuzda bizim port 445'e ihtiyacımız var
##### meterpreter> portfwd add -l 4321 -p 445 -r 10.0.2.15
![[Pasted image 20240422230741.png]]

### nmap localhost -p 4321 -A

![[Pasted image 20240422232136.png]]

![[Pasted image 20240609005305.png]]

![[Pasted image 20240609005430.png]]




![[Pasted image 20240609005627.png]]






