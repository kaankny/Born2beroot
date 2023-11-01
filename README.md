# Born2beroot Ders

## 1.PROJEYE GENEL BAKIŞ

### Sanal makina nasıl çalışır?

- Sanal makina, fiziksel bir bilgisayarın üzerinde çalışan bir yazılım örneğidir.
- Donanımdan ayrılmış katmandan bir bilgisayarın sanal örneğini çalıştırır

### İşletim sistemi tercihleri?

- Oyunlar, ofis işleri ve günlük kullanım için windows; ücretsiz, açık kaynak kodlu ve yazılım özgürlüklü kullanım için linux; tasarım, mühendislik, ios development için MacOS

### Rocky ve Debian arasındaki temel farklar?

- Rocky, red hat tabanlı paket yönetimi sistemlerini kullanır. Debian iste advanced package tool tabanlı paket yöneticisini kullanır
- Rocky RHEL kaynak kodunu temele alırken, Debian kendi özgün kaynak kodunu kullanır.

### Sanal makinaların amacı?

- Bir fiziksel sunucu üzerinde birden çok sanal makina oluşturmamızı sağlar
- Yazılım geliştiricileri ve test ekipleri farklı işletim sistemleri ve konfigürasyonları üzerinde çalışmak için kullanılır.
- Veri yedekleme ve depolanması için kullanılabilir.

### Aptitude ve APT arasındaki fark nedir?

- Aptitude hem komut satırı hemde grafik arayüzlü iken APT bir tek komut satırı aracılığıyla kullanılır.
- Aptitude karmaşık paket bağımlılıklarını daha iyi yönetme yeteneğine sahip
- Paket izleme ve paket işlemi sadece Aptitudede var

### APPArmor nedir?

- Linux tabanlı sistemlerde uygulama güvenliğini artırmak için kullanılan bir güvenlik modülüdür ve uygulamaların kaynaklara erişimini sınırlamak için profil tabanlı bir yaklaşım kullanır
- Hangi uygulama hangi dosyalara hangi izinlerle erişebilir tarzı profiller oluşturur

## 2.BASİT KURULUM

### Seçilen şifreye dikkat edin?

- `chage -l kkanyilm42`  komutunu kullanarak şifre politikasını kontrol edebiliriz.

### UFW hizmetinin başlatıldığını kontrol edin?

- `systemctl status ufw` komutu ile ufw hizmetinin çalıştığını kontrol edin.

### SSH hizmetinin başlatıldığını kontrol edin?

- `systemctl status ssh` komutu ile ssh hizmetinin çalıştığını kontrol edin.

### İşletim sistemi Debian veya Rocky mi kontrol edin?

- `uname -a` komutu ile işletim sistemi bilgilerini yazdırın.

## 3.KULLANICI

### Değerlendirilmekte olan öğrencinin oturum açma bilgilerine sahip bir kullanıcının sanal makinede bulunmasını ister?

- `cat /etc/passwd | grep home` yazınca kkanyilm42 çıkıyor.
- `id kkanyilm` kullanıcı bilgilerini gösterir

## Bu kullanıcının eklendiğini ve "sudo" ve "user42" gruplarına ait olduğunu kontrol edin.?

- `cat /etc/group | grep sudo`
- `cat /etc/group | grep kkanyilm42`
- `id kkanyilm42`
- `groups` komutlarınından birini kullanın

## Aşşağıdaki adımları takip ederek şifre politikası ile ilgili kuralların yerleştirildiğine emin olun.

- ilk olarak yeni br kullanıcı oluşturun
    - `adduser <username>` (yüksek seviyeli)
    - `useradd <username>` (düşük seviyeli)
- Konu kurallarına uyarak istediğiniz şifreyi atayın
    - `passwd <username>`
    - `sudo chage -l username` kurallara uyup uymadığını kontrol et
- Kuralların nasıl değiştirildiğini açıklayın.
    - `sudo vim /etc/login.defs` (burada max days 30, min days 2, warm 7 olarak ayarlandı)
    - `sudo vim /etc/security/pwdquality.conf` (katı kurallar şifre belirlemek için yüklediğimiz sudo apt install libpam-pwdquality komutuyla yüklediğimiz paketten sonra oluşan, katı şifreleme politikalarin belirleyen dosya) enforcing kısmı 0 ise şifre kurallara uymuyorsa uyarı verir ama şifreyi kabul eder.
- “değerlendirme” adında grup oluşturması ve kullanıcıya ataması
    - `addgroup <değerlendirme>` (grubu kur)
    - `cat /etc/group | grep değerlendirme` (kurulan grubu gör)
    - `usermod -aG <groupName> <username>`  (grubu kullanıcıya ata)
- kullanıcının “değerlendirme” grubuna ait olup olmadığını kontrol edin.
    - `id <username>`
    - `cat /etc/group | grep değerlendirme`
    - `groups <username>`
- son olarak şifre politikasının avantajlarından ve dezavantajlarından bahsedin
    - avantajları:
        - minlen = 10, 15, 20 olması parola ne kadar uzunsa kırmakda o kadar zor olur
        - büyük küçük harf kullanmak şifre kombinasyonlarını artırır.
        - numara koymakda aynı şekilde kombinasyonu artırır.
        - alfabe harici karakter kullanmakta aynı şekil
    - dezavantajlar:
        - şifrelerin zor konulması sık sık unutulmasına, hesapların kitlenmesine, yeni şifre oluşturmak için tekrar aynı kurallar etrafında şifre seçme gibi zaman vakit kayıpları yaşanır. (fakat aynı zamanda hep şifreyi değiştirmek avantaj sayılabilir )

## 4.Ana bilgisayar adı ve bölümleri

### Makinenin ana bilgisayar adının doğru olduğunu kontrol edin (kkanyilm42)

- `hostname` komutu ile kontrol ediliyor

### Ana bilgisayar adını değiştirin ve bilgisayarı yeniden başlatın

- `sudo hostnamectl set-hostname <new-name>`
- `sudo vim /etc/hosts`  (vim içinde 127.0.1.1 yanına newhostname’ini yaz
- `reboot`
- `hostname`

### Sanal makina için bölümleri gösterin.

- `lsblk` (sanal makina bölümleri ile ilgili ayrıntılı bilgi verir)
    
    > SDA ilk diski temsil eder. Sonraki blok cihaz bölümleri sda’ın yanında ondalık sayı olarak gösterilir. `sr0` çıkarılabilir cihazı temsil eder. Cd -rom. Listelenen cihazlar için çıarılabilir olup olmayanların gösterildiği bölüm `RO` dur. (RO = removable).                                      RO = 0 ise çıkarılamaz block device                                                                                                 RO= 1 ise çıkarılabilir block device. sda birincil cihazdır. sda(1-4) arası öncelikli cihazları temsil ederken sda4 sonrası logical birimler olduklarını gösterir. `mountpoint` bu, cihazın monte edildiği bağlama noktasını görüntüler
    > 
    

### LVM’nin nasıl çalıştığını açıklayın?

- LVM(logical volume manager) ile birden fazla diski tek bir disk bölümü olarak kullanabilir ve disk yönetimi işlemlerininden büyük kolaylık sağlar. Disk alanının yetersiz kaldığı durumlarda LVM ile oluşturulan disk veri kümesine kolaylıkla yeni disk ve ya disk bölümleri ilave edebilir, ihtiyaca göre disk alanı şekillendirilebilir. Yani istenildiğinde mevcut disk alanı üzerinde istenilen boyutlandırmanın yeniden yapabilmesini sağlar.
- Büyük disk alanı ihtiyacı olan sistemlerde LVM ile disk veri kümeleri oluşturularak ya da sisteme yeni bir disk daha eklenerek toplam disk boyutu arttırılabilir

# 5. SUDO

## “Sudo” programının sanal makineye düzgün şekilde yüklenip yüklenmediğini kontrol edin.

## Öğrenci artık yeni kullanıcınızı “sudo” grubuna atadığını göstermelidir.

- `usermod -aG sudo kkanyilm42`
- `cat /etc/group | grep sudo`
- `groups kkanyilm42`

## Sudo’nun değerini ve işleyişini açıklamalıdır

- Sudo sıradan kullanıcıların sisteme yönetici olarak bağlanmaları gerekmeden yönetici yetkisi gerektiren işlemleri yapabilmesini sağlayan bir programdır
- Sudo yetkisiyle yapılan işlemlerde kimin hangi işlemi yaptığının takibi daha kolaydır. sudo log dosyasında gözüküyor kimin hangi işlemi yaptığı

## PDF’in getirdiği kuralların uygulanmasını size göstermelidir.

- `sudo visudo`
- `sudo vim /etc/sudoers`

## “/var/log/sudo/” klasörünün var olduğunu ve en az bir dosyaya sahip olduğunu doğrulayın. Sudo ile kullanılan komutların geçmişini görmelisiniz.

- `cd /var/log/sudo`
- `ls -l`

## Sudo üzerinde bir komut çalıştırmayı deneyin.

- mesela bir kullanıcının şifresini değiştir sudo yardımı ile

## “/var/log/sudo/” klasöründeki dosya(lar)ın güncellenip güncellenmediğine bakın.

- `sudo cat /var/log/sudo/sudo.log`

# 6.UFW

## “UFW” programının sanal makineye düzgün şekilde yüklenip yüklenmediğini kontrol edin.

- systemctl status ufw

## UFW’nin ne olduğunu ve onu kullanmanın değerini açıkla?

- Ubuntu üzerinde kurulan firewall uygulamasıdır. ipv4 ve ipv6 firewall güvenlik yönetimi yapmamıza imkan verir.
- Hem konsol hem de GUI üzerinden port ve güvenlik duvarı işlemlerini gerçekleştirmemize olanak veren bir güvenlik duvarı aracı olarak ifade edilebilir.
- Genel olarak SSH işlemleri içerisinde port açma/değiştirme/kapatma aşamalarında faydalangığımız UFW…
- linux tabanlı işletim sistemlerinde güvenlik duvarı varsayılan olarak iptables’dır. Ancak iptables linux’e çok aşina olmayan kullanıcılar için biraz komplike olabilir. Linux acemisi iseniz firewall ayarlarını yapmal için ufw komut setini kurup kullanabilirsiniz.
- Firewall, zararlı yazılımlara karşı bir duvar örür ve bunların ağ yolu ile bilgisayara sızmasını önüne geçer.
- Güvenlik duvaru, iç ve dış trafiği denetlememizi sağlayan bir cihazdır. Bu duvar sayesinde bilgisayarımızdaki yazılımlar bizim iznimiz dışında bilgi veremez.

## UFW’deki aktif kuralları listeleyin.

- `sudo ufw status numbered`

## 8080 numaralı bağlantı noktasını açmak için yeni bir kural ekleyin.

- `sudo ufw allow 8080`

## 8080 kuralını sil.

- `sudo ufw delete <silinecek satır>`

# 7.SSH

## SSH başarılı şekilde yüklendi mi?

- `systemctl status ssh`
- `vim /etc/ssh/sshd_config` (SSH hizmetinin sadece 4242 portunda çalıştığını gösteren → #port 4242 ve güvenlik seveviyle SSH’a root olarak bağlanmayı yasaklayan PermitRootLogin no olmalı)

## SSH nedir ve kullanmanın değerini nedir?

- Linux sunuculara erişim sağlamak için SSH protokolü kullanıyoruz. Yani uzaktaki bir sunucuya bağlanmak, ona komutlar ve dosyalar göndermek üzere kullanılan şifrelenmiş bir uzaktan sağlayıcı protodolüdür.
- Sadece belirlediğimiz adreslerdem SSH erişimi sağlamak istiyorsak güvenlik duvarı (UFW) burada çok işe yarar.

## SSH hizmetinin yalnızca 4242 numaralı bağlantı noktasını kullandığını doğrulayın.

- `ssh root42@localhost -p 4242` (root olarak dene ve kabul edilmediğini göster)
- `ssh <username>@localhost -p 22` (22 portundan dene ve kabul edilmediğni göster)
- `ssh <username>@localhost -p 4242` (giriş sağla son olarak )

# 8.Script Monitoring

## YAZMAYA ÜŞENDİM YAZARIM BİRAZDAN
