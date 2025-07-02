# Sunucuyu-VPN-Olarak-Kullanmak



Neden VPN'e ihtiyacım var?


Türkiye siyasi gerilimlerin ve tansiyonun yüksek olduğu bir ülke ve bu durum çoğu kez X (eski adıyla Twitter) ve Discord gibi biz kriptocuların yoğun olarak kullandığı uygulamalara ulaşımın kısıtlanmasına hatta çoğu örnekte tamamen engellenmesine neden oluyor. İşte bu durum bizi kazancımızdan edebiliyor. VPN kurmak derdimize en güzel çarelerden biri olarak karşımıza çıkıyor.



Neden kendi VPN'imi kurmalıyım?


Halihazırda nod işleriyle uğraşıyor ve elinizin altında sunucu bulunduruyorsanız en güzeli kendi VPN'inizi yapmak. Çünkü en son Discord erişim engeli geldiğinde Türk topluluğundan bazı arkadaşlarımızın cüzdanları hacklendi. Bu noktada kendi VPN'imizi yapmak bizi güvende tutacaktır.




VPN için açık kaynak kod kullandığından ve yazılım uyumluluğundan dolayı OpenVPN tercih ediyorum. Yapılandırma için Ubuntu 22.04 LTS ile çalışan küçük bir sunucuya ihtiyacımız olacak. Ben Hetzner'in 3 Euro'luk en ucuz sunucusunu kiraladım.



Bu noktada maliyetleri düşürmek adına size VPN ile beraber sunucuya Chromium kurarak DePin projelerini de aynı sunucuda kullanmayı tavsiye edebilirim. Böylece hem güvenli bir VPN'e sahip olmuş hem de DePin uygulamalarını yükleyerek ilerideki airdroplar için puan toplamış olacağız. Kısacası bir taşla iki kuş avlayacağız.



Şimdi VPN kurulumuna geçebiliriz:


## Sistemi Güncelleyelim
```
 sudo apt update && sudo apt upgrade -y
```

## OpenVPN Erişim Sunucusu Deposunu Ekleyelim ve Gerekli Dosyaları Sunucumuza İndirelim
```
echo "deb [signed-by=/etc/apt/keyrings/openvpn-as.gpg.key] http://as-repository.openvpn.net/as/debian $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/openvpn-as.list
```
```
wget --quiet -O - https://as-repository.openvpn.net/as-repo-public.gpg | sudo tee /etc/apt/keyrings/openvpn-as.gpg.key
```

## Gerekli Sertifikaları Yükleyelim
```
sudo apt install apt-transport-https ca-certificates
```

## Ubuntu Sistemimizin Paket Listesini Yenileyelim
```
sudo apt update
```

## OpenVPN Access Server Kurulumunu Yapalım
```
sudo apt install -y openvpn-as
```

Bu kod sonunda bize bir kullanıcı şifresi bir de kullanıcı adı "openvpn" olan bir çıktı verecek. Benimki şu şekildeydi örneğin:


Access Server 2.14.1 has been successfully installed in /usr/local/openvpn_as
Configuration log file has been written to /usr/local/openvpn_as/init.log



Access Server Web UIs are available here:
Admin  UI: https://xx.xx.xx.xx:943/admin
Client UI: https://xx.xx.xx.xx:943/
To login please use the "openvpn" account with "xxxxxxxxx" password.
(password can be changed on Admin UI)


## Web Tarayıcısı Üzerinden OpenVPN Arayüzüne Bağlanalım
```
https://sunucunuzun_ip_veya_alan_adı:943/admin
```
Burada sunucunuzun ip adresini ilgili yere yazarak linki düzenleyin ve herhangi bir tarayıcıya yapıştırın.


![Ekran görüntüsü 2024-10-16 224413](https://github.com/user-attachments/assets/4de4ed4b-c135-402f-8d3c-85322e8e4d46)

Resimde gösterdiklerimi uygulayın

Son olarak alttaki resimde görülen dashboard'a ulaşacaksınız, soldaki menüyü kullanarak VPN'inizi istediğiniz gibi yapılandırabilirsiniz. Örneğin başka kullanıcı ekleyip çıkarmak gibi. Ben ayarları değiştirmeden olduğu gibi kullandım. Hepsi bu kadar:))


![Ekran görüntüsü 2024-10-16 224833](https://github.com/user-attachments/assets/b29bc533-25c8-4cae-96c2-a6aad0c7797d)


