# VPN + TOR Otomatik Başlatıcı

## Genel Bakış

Bu Python scripti, **OpenVPN** ve **TOR** servislerini otomatik olarak başlatmak, bağlantı durumunu izlemek ve kopma durumunda süreçleri güvenli biçimde sonlandırmak için tasarlanmıştır.

Amaç; VPN bağlantısı **başarılı olmadan TOR’u başlatmamak**, bağlantı koptuğunda ise tüm servisleri temiz şekilde kapatmaktır.

Script, görsel bir ASCII banner ile başlar ve her servisi **ayrı terminal penceresinde** çalıştırır.

---

## Temel Özellikler

• OpenVPN bağlantısını otomatik başlatır  
• VPN (tun0) arayüzünü aktif olarak kontrol eder  
• VPN başarılıysa TOR servisini başlatır  
• VPN koparsa TOR otomatik kapatılır  
• CTRL+C ile tüm süreçler güvenli şekilde durdurulur  
• Root / sudo kontrolü otomatik yapılır  
• Kullanıcıdan ek giriş gerekmez  

---

## Gereksinimler

Aşağıdaki bileşenlerin sistemde kurulu olması gerekir:

• Python 3.x  
• OpenVPN  
• TOR  
• GNOME Terminal  
• Linux tabanlı işletim sistemi  

---

## Dosya Yapısı

Scriptin düzgün çalışması için aşağıdaki dosyalar **home dizininde** bulunmalıdır:

• `~/proton.ovpn` → VPN konfigürasyon dosyası  
• `~/proton_pass.txt` → VPN kullanıcı adı / parola dosyası  

---

## Kurulum

Script dosyasını çalıştırılabilir hale getirin:

```bash
chmod +x vpn_tor_launcher.py
```

# Kullanım

Script **root** yetkisiyle çalıştırılmalıdır:

```bash
sudo python3 owl.py
```

## Çalıştırıldığında

• Sol terminalde OpenVPN başlatılır  
• VPN bağlantısı doğrulanır (`tun0`)  
• Sağ terminalde TOR başlatılır  
• VPN bağlantısı koparsa TOR otomatik olarak kapatılır  

---

## Çalışma Akışı

• Ekran temizlenir ve ASCII banner gösterilir  
• Gerekli dosyaların varlığı kontrol edilir  
• OpenVPN ayrı bir terminal penceresinde başlatılır  
• `tun0` ağ arayüzü sürekli izlenir  
• VPN bağlantısı başarılıysa TOR servisi başlatılır  
• VPN bağlantısı koparsa tüm servisler güvenli şekilde durdurulur  

---

## Hata Durumları

• VPN yapılandırma dosyaları bulunamazsa script çalışmayı durdurur  
• VPN bağlantısı başarısız olursa TOR başlatılmaz  
• `tun0` arayüzü kaybolursa TOR otomatik olarak kapatılır  

---

## Güvenlik Notları

• TOR, VPN bağlantısı olmadan **asla** başlatılmaz  
• Bağlantı durumu aktif olarak izlenir  
• Süreçler arka planda sahipsiz şekilde bırakılmaz  

---

## Yasal Uyarı

Bu araç yalnızca **eğitim**, **laboratuvar**, **CTF** ve **açık izin verilmiş** ortamlarda kullanılmak üzere geliştirilmiştir.  

Yetkisiz ağlarda veya sistemlerde kullanımı **yasadışıdır** ve hukuki sorumluluk doğurur.  

Geliştirici, aracın kötüye kullanımından doğabilecek herhangi bir hukuki veya teknik zarardan **sorumlu değildir**.
