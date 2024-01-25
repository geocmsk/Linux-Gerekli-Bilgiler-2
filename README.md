# Linux-Gerekli-Bilgiler-2


Linux, güçlü ve esnek bir işletim sistemi olarak, sınırsız keşif imkanları sunar. İster yeni bir Linux meraklısı olun, ister orta seviye bir kullanıcı; bu platform her seviyedeki insan için her zaman yeni bir şeyler öğrenme fırsatı barındırır. Bu yazımda, özellikle orta seviye Linux kullanıcılarına yönelik günlük işleri kolaylaştıran ve terminaldeki verimliliği artıran bazı hayati komutlar üzerine odaklanacağız. awk ve sed gibi metin işleme araçlarından, scp ve rsync gibi dosya transfer komutlarına kadar, bu yazıda Linux'un derinliklerine bir dalış yapacağız ve bu komutların günlük kullanımdaki pratik uygulamalarını keşfedeceğiz. Hazırsanız başlıyoruz :)


Orta Seviye Bazı Linux Komutları


apt, apt-get Komutları:
Ubuntu ve diğer Debian tabanlı Linux dağıtımlarında, paket yönetimi apt ve apt-get komutları ile yapılır. Bu komutlar, yazılım yüklemek, güncellemek ve sistemdeki paketleri yönetmek için kullanılır. İşte bu komutların detayları ve gerçek kullanım örnekleri:

apt ve apt-get Komutları:
Bu iki komut, Debian tabanlı sistemlerde paket yönetimi için kullanılır. apt daha yeni bir 		sürümdür ve kullanıcı dostu çıktılar sunar, apt-get ise daha eski, ancak hala yaygın olarak 		kullanılan bir araçtır.
				Temel Farklar:

apt: Kullanıcı dostu arayüzü ile interaktif kullanım için tasarlanmıştır.
apt-get: Daha çok otomatik scriptlerde ve sistem içi işlemlerde tercih edilir.
Komutlara geçmeden önce paket listesinden bahsetmek istiyorum:
Paket listesi, bir Linux dağıtımının paket yönetim sisteminde mevcut olan tüm yazılım paketlerinin bir envanteridir. Bu liste, paketlerin isimlerini, sürümlerini ve bulundukları depoları (repositories) içerir. Paket yönetim sistemi, bu listeyi kullanarak hangi yazılımın yüklenebileceğini, güncellenebileceğini veya kaldırılabileceğini belirler.


Paket Listesinin Kullanımı ve Önemi:
Ne İçin Kullanılır: Paket listesi, sisteminize hangi yazılımların yüklenebileceğini ve bu yazılımların hangi sürümlerinin mevcut olduğunu belirler. Bu liste, çeşitli yazılım depolarından alınır ve yerel olarak saklanır.
Nasıl Kullanılır: Kullanıcılar genellikle doğrudan paket listesiyle etkileşime girmezler. Bunun yerine, apt veya apt-get gibi paket yönetim araçları aracılığıyla bu listeyi kullanırlar.


Paket Listesinin Güncellenmesi (update):
Ne Zaman Gereklidir: Paket listesi, yeni yazılım paketleri eklenmiş, güncellenmiş veya kaldırılmış olabilir. Bu değişiklikleri yansıtmak için paket listesinin güncellenmesi gerekir.
Nasıl Yapılır: sudo apt update veya sudo apt-get update komutu, tüm yazılım depolarından en güncel paket bilgilerini çeker ve yerel paket listesini bu bilgilerle günceller.
Örnek: Bir PPA (Personal Package Archive) eklediğinizde veya bir yazılım deposunu değiştirdiğinizde, paket listesini update komutu ile güncellemeniz gerekir.


Sistem Güncellemesi (upgrade):
Ne Zaman Gereklidir: Sisteminizdeki yazılım paketleri, güvenlik güncellemeleri, hata düzeltmeleri veya yeni özellikler içerecek şekilde güncellenebilir.
Nasıl Yapılır: sudo apt upgrade veya sudo apt-get upgrade komutu, update ile güncellenen paket listesine dayanarak, yüklü paketleri en son sürümlerine yükseltir.
Örnek: Güvenlik açıklarını kapatmak veya yazılım özelliklerini güncel tutmak için düzenli olarak upgrade işlemi yapılmalıdır.
Kısacası, paket listesi, bir Linux sisteminde halihazırda mevcut yazılımların bir katalogudur ve sistem yöneticileri veya kullanıcılar tarafından periyodik olarak güncellenmesi gerekir. Bu, apt update ile yapılır ve ardından apt upgrade komutu ile yüklü yazılımlar güncellenir. Bu işlemler, sistemin güvenli ve güncel kalmasını sağlar.


 apt-get install:
Belirli bir paketi veya paketleri yüklemek için kullanılır.

sudo apt-get install nginx


apt-get remove ve apt-get purge:
remove, belirli bir paketi sistemden kaldırır ancak yapılandırma dosyalarını bırakır. purge, paketi ve tüm yapılandırma dosyalarını kaldırır.

sudo apt-get remove nginx
sudo apt-get purge nginx
 
apt-get autoremove ve apt-get autoclean:
autoremove, artık gerekli olmayan bağımlılık paketlerini kaldırır. autoclean, indirilmiş paket arşivlerinden kullanılmayanları temizler.

sudo apt-get autoremove
sudo apt-get autoclean




alias Komutu:
Açıklama: alias komutu, daha uzun komutları kısaltmak ve kolayca hatırlanabilir hale getirmek için kullanılır. Kullanıcılar, sık kullandıkları komutlara kısa adlar (aliaslar) tanımlayabilirler.
Örnek Kullanım:

alias ll='ls -l': Bu alias, ls -l komutunu ll olarak kısaltır. Artık ll yazdığınızda, uzun listeleme formatında dosyaları görüntüleyebilirsiniz.
alias rm='rm -i': Bu, her rm komutunda interaktif modu etkinleştirir, yani dosya silinmeden önce kullanıcıdan onay ister.

![image](https://github.com/geocmsk/Linux-Gerekli-Bilgiler-2/assets/90604931/561a9999-c671-4222-bdc0-c26bb1abf2f2)


 find Komutu:
Açıklama: find komutu, dosya veya dizinleri isim, boyut, değiştirilme tarihi gibi özelliklerine göre aramak için kullanılır. Çok güçlü ve esnek bir arama aracıdır.
Örnek Kullanım:

find /home -name 'dosya.txt': Bu komut, /home dizini altında 'dosya.txt' adında dosyaları arar.
find / -type d -name 'Proje*': Bu komut, kök dizininden başlayarak 'Proje' ile başlayan tüm dizinleri arar.
find /home -size +1M: Bu komut, /home altında boyutu 1MB'den büyük olan dosyaları listeler.


 diff Komutu:
Açıklama: diff komutu, iki dosya veya iki dizin arasındaki farkları gösterir. Değişiklikleri karşılaştırmak ve sonuçları analiz etmek için sıkça kullanılır.
Örnek Kullanım:

diff dosya1.txt dosya2.txt: Bu komut, dosya1.txt ve dosya2.txt arasındaki farkları satır satır karşılaştırır ve gösterir.
diff -u dosya1.txt dosya2.txt: Bu, iki dosya arasındaki farkları 'unified' formatında gösterir, bu format daha okunabilir ve anlaşılırdır.



![image](https://github.com/geocmsk/Linux-Gerekli-Bilgiler-2/assets/90604931/697180db-f746-4fca-8c14-1540e0da1432)




 tail ve head Komutları:
Açıklama: tail dosyanın son bölümünü, head ise baş bölümünü gösterir.
Örnek Kullanım:


![image](https://github.com/geocmsk/Linux-Gerekli-Bilgiler-2/assets/90604931/38488eed-7540-458d-a8d4-46411adb55dd)




tail -n 10 dosya.txt: dosya.txt'nin son 10 satırını gösterir.
head -n 10 dosya.txt: dosya.txt'nin ilk 10 satırını gösterir.


 ln Komutu:
Açıklama: Dosyalara sembolik linkler (kısayollar) oluşturur.
Örnek Kullanım:

ln -s orijinal_dosya link: 'orijinal_dosya'ya 'link' adında bir sembolik link oluşturur.


 scp Komutu:
Açıklama: Güvenli bir şekilde dosya kopyalamak için kullanılır, genellikle SSH üzerinden uzak sistemlerle dosya transferi için tercih edilir.
Örnek Kullanım:

scp dosya.txt kullanici@sunucu:/hedef/dizin: Yerel sistemden uzak sunucuya dosya.txt kopyalar.
kullanici@sunucu --> örn. root@127.0.0.1


 rsync Komutu:
Açıklama: Dosya ve dizinleri senkronize etmek için kullanılır. Ağ üzerinden verimli dosya transferi sağlar.
Örnek Kullanım:

rsync -avz /kaynak/dizin/ kullanici@sunucu:/hedef/dizin/: Kaynak dizini uzak sunucudaki hedef dizinle senkronize eder.


 gzip ve gunzip Komutları:
Açıklama: gzip dosyaları sıkıştırmak, gunzip ise sıkıştırılmış dosyaları açmak için kullanılır.
Örnek Kullanım:

gzip dosya.txt: dosya.txt'yi sıkıştırır.



Derleme için @lilium hocama teşekkür ederim..




![image](https://github.com/geocmsk/Linux-Gerekli-Bilgiler-2/assets/90604931/9591bd1e-87f1-4269-97ed-590fb77eef74)


gunzip dosya.txt.gz: Sıkıştırılmış dosya.txt.gz dosyasını açar.

![image](https://github.com/geocmsk/Linux-Gerekli-Bilgiler-2/assets/90604931/9396e4c1-a29d-43a4-b363-f7589ce0bdbe)

 ping Komutu:
Açıklama: Ağ üzerindeki diğer makinelerle bağlantı testi yapar.
Örnek Kullanım:

ping ornek.com: 'ornek.com' adresine ağ bağlantısını test eder.

![image](https://github.com/geocmsk/Linux-Gerekli-Bilgiler-2/assets/90604931/91a4bfd8-6fc1-4b75-8f91-9408246433db)


 traceroute Komutu:
Açıklama: Paketlerin hedeflerine ulaşana kadar izledikleri yolu gösterir.
Örnek Kullanım:

traceroute ornek.com: 'ornek.com' adresine giden paketlerin yolunu gösterir.

![image](https://github.com/geocmsk/Linux-Gerekli-Bilgiler-2/assets/90604931/04549bf5-0f9e-4f02-bb59-83f975ca324f)
