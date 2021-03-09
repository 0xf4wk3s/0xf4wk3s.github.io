---
published: true
---
![](https://i.imgur.com/J1ik7ZU.png) 


Merhabalar bu yazımda sizinle TryHackMe üzerindeki [Shodan.io](https://tryhackme.com/room/shodan) adlı odanın çözümünü paylaşacağım.

odanın Shodan'ı anlamak ve tanımak için güzel bir kaynak olduğunu düşünüyorum. 


Öyleyse 2 adet akılda kalıcı tanımımızla başlayalım,

**Tanım 1 :** Shodan.io, nesnelerin interneti için oluşturulan bir arama motorudur.

**Tanım 2 :** Shodan.io, internete bağlı cihazların arama motorudur.


## Servisleri Bulma

Bir şirket üzerinde pentest yaptığımızı düşünelim, napabiliriz? 

sunucularının hangi hizmetleri çalıştırdığını öğrenmek isteyebiliriz.

Bu konuda shodan.io bize yardımcı olabilir.

İlk olarak sirketin IP adresini bulalım, elbette _tryhackme.com_ 'un IP adresi :)

Nasıl bulabiliriz? Tabi kii  >> **ping** atarak.

![tryhackme_ip.PNG](https://raw.githubusercontent.com/0xf4wk3s/0xf4wk3s.github.io/master/_posts/tryhackme_ip.PNG)

 > IP burada : 104.26.11.129
 
 Hadi gidip biraz _shodan_ 'layalım!
 
 ![shodan_arama.PNG](https://raw.githubusercontent.com/0xf4wk3s/0xf4wk3s.github.io/master/_posts/shodan_arama.PNG)
 
 ![shodan_screenshot0.PNG](https://raw.githubusercontent.com/0xf4wk3s/0xf4wk3s.github.io/master/_posts/shodan_screenshot0.PNG)
 
TryHackMe'nin Amerika Birleşik Devletleri'nde Cloudflare üzerinde çalıştığını ve birçok bağlantı noktasına sahip olduğunu görüyoruz.

Cloudflare, TryHackMe ile gerçek sunucu arasında proxy görevi görür. Büyük bir şirket için test yapıyor olsaydık bu bilgi bize pek bir yarar sağlamazdı. IP adreslerini almanın bir yolunu bulmalıyız.

Bunu Otonom Sistem Numarası (Autonomous System Numbers : ASN) ile yapabiliriz.

Otonom Sistem Numarası(ASN) nedir? tanımlamaya çalışalım, 

Birden fazla IP adresine sahip Google gibi devasa bir şirket olduğunuzu düşünün. Otonom Sistem Numarası(ASN) burada devreye girer. Bu numara sizi tanımlar.

ASN numarasını Shodan.io üzerinden asn filtresi ile bulabiliriz.

> Kullanılacak filtre ==> asn:[asn_numarası]

TryHackMe büyük bir şirket olmadığından kendine özel ASN adresine sahip değildir.

Yukarıdaki resimde gördüğünüz _Cloudflare_ ASN adresi : AS13335

Shodan kullanarak bize örnek olarak verilen  : AS14061 (ASN) adresini bulabiliriz.

Şu Shodan filtresini kullanalım :  

> asn:AS14061  

![digitalocean_asn.PNG](https://raw.githubusercontent.com/0xf4wk3s/0xf4wk3s.github.io/master/_posts/digitalocean_asn.PNG)

Bulduk! Bu ASN DigitalOcean'a ait.

Konuyu anladığımızı düşünüyorum, fakat son kez bana aşağıdaki ASN numarasının sahibi kim bulun bakalım.

> AS15169

Evet! Google :) Tebrikler.

### Getting Started - Başlarken Bölümündeki Sorulara geçebiliriz.

## Google'ın ASN Numarası nedir? : What is Google's ASN number?

Adım 1 : google.com'a ping atalım.

Adım 2 : IP adresini bulduk, 216.58.206.206 işte burada.

Adım 3 : bunu shodan üzerinden aratalım, 

Adım 4 : Bulduk! ASN Numarası : AS15169

Cevap : AS15169

## Ne zaman tahsis edildi? Sadece yılı verin. : When was it allocated? Give the year only.

https://ipinfo.io/AS15169

ipinfo.io adresi üzerinden Google'ın ASN numarasını girdiğimizde tanımlandığı yılı bulabildik.

Cevap : 2000

![ipinfo.io_google.PNG](https://raw.githubusercontent.com/0xf4wk3s/0xf4wk3s.github.io/master/_posts/ipinfo.io_google.PNG)

## Fiziksel olarak dünyada bu ASN numarasındaki makinelerin çoğu nerede? : Where are most of the machines on this ASN number, physically in the world?

![asn_sc0.PNG](https://raw.githubusercontent.com/0xf4wk3s/0xf4wk3s.github.io/master/_posts/asn_sc0.PNG)

Cevap : United States

## Bu ASN'de Google'ın tüm cihazlarında en iyi hizmeti nedir? : What is Google's top service across all their devices on this ASN?

Cevap : SSH

## Google hangi SSH ürününü kullanıyor? : What SSH product does Google use?

![openssh_0.PNG](https://raw.githubusercontent.com/0xf4wk3s/0xf4wk3s.github.io/master/_posts/openssh_0.PNG)

Cevap : OpenSSH

## Bu aramaya göre Google'ın en çok kullandığı Google ürünü nedir? Önündeki "Google" kelimesini dikkate almayın. : What is Google's most used Google product, according to this search? Ignore the word "Google" in front of it.

![cloud_0.PNG](https://raw.githubusercontent.com/0xf4wk3s/0xf4wk3s.github.io/master/_posts/cloud_0.PNG)

Cevap : Google Cloud

### Filters : Filtreler bölümündeki sorulara geçelim,




