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

![tryhackme_ip.PNG](https://i.hizliresim.com/h1pG8K.png)

 > IP burada : 104.26.11.129
 
 Hadi gidip biraz _shodan_ 'layalım!
 
 ![shodan_ip.PNG](https://i.hizliresim.com/OxrKn8.png)
 
 ![shodan_screenshot0.PNG]({{site.baseurl}}/_posts/shodan_screenshot0.PNG)
