---
published: true
---
![](https://i.imgur.com/J1ik7ZU.png) 


Merhabalar bu yazımda TryHackMe üzerindeki [Shodan.io](https://tryhackme.com/room/shodan) adlı odanın çözümünü paylaşacağım.

Bu odanın Shodan'ı anlamak ve tanımak için güzel bir kaynak olduğunu düşünüyorum. 


Öyleyse başlayalım.

Shodan.io Nesnelerin İnterneti için oluşturulan bir arama motorudur.

İnternete bağlı cihazların arama motoru olarak da tanımlayabiliriz.

## Servisleri Bulma

Bir şirket üzerinde pentest yaptığımızı düşünelim, napabiliriz? 

>>> sunucularının hangi hizmetleri çalıştırdığını öğrenmek isteyebiliriz.

Bu konuda shodan.io bize yardımcı olabilir.

İlk olarak sirketin IP adresini bulalım, elbette _tryhackme.com_ 'un IP adresi :)

Nasıl bulabiliriz? Tabi kii  >> **ping** atarak.

![tryhackme_ip.PNG]({{site.baseurl}}/_posts/tryhackme_ip.PNG)

 > IP burada : 104.26.11.129
 
 Hadi gidip biraz _shodan_ 'layalım!
