# **Harjoitus 5**

Aloitin työt 12.10.


Harjoitustyön tehtävänantona käytettiin Karvisen kotisivuilta löytyvää [h4-kohtaa](https://terokarvinen.com/2021/linux-palvelimet-ict4tn021-3018/#h5)

**Harjoituksen laitekokoonpano**  
*Järjestelmänä Win 11 + VirtualBox 6.0 + Debian 11*  
  
*Koneen perustiedot:*  
*Suoritin: AMD Ryzen 9 5900HS 8-ytiminen 3,1 - 4,5 GHz, 16 Mt välimuisti*  
*Muisti: 16 Gt LPDDR4X*  
*Näytönohjain: NVIDIA GeForce RTX 3050 Ti 4 Gt GDDR6*  
*Kiintolevy: 512 Gt M.2 2230 NVMe PCIe 3.0 SSD*  

## a) CRUD. Make a simple web program, that allows multiple users modify the same data. Have user accounts and logins. You can use Django development server and admin interface here. Single table is enough. We already did a Customer (CRM) database, so it might be interesting to do something as simple, but slightly different.

Tehtävän lähteenä käytin tuntimuistiinpanojani ja Karvisen (artikkelia)[https://terokarvinen.com/2022/django-instant-crm-tutorial/].  
  
Ensin poistin virtualenvin, jotta pääsin asentamaan ohjelmat alusta pitäen:  
*sudo apt-get purge virtualenv*  
  
![Kuva 1.](pics/harjoitus_5/1.png)  
*Virtualenv poistettiin onnistuneesti, pl. gitwebiä koskeva virheilmoitus*  
  
Järjestelmä kehotti poistamaan myös muita paketteja, joita ei enää tarvita, joten ajoin sen ehdottaman komennon:  
*sudo apt autoremove*  
  
![Kuva 2.](pics/harjoitus_5/2.png)  
*gitweb-paketista jäi edelleen virheilmoitus*  
  
Päätin kokeilla gitwebin poistamista:  
*sudo apt-get purge gitweb*  
  
![Kuva 3.](pics/harjoitus_5/3.png)  
*Käsky kommentoi jotain Apacheen liittyvää, joten tarkistin, että palvelin oli edelleen päällä*  
  
![Kuva 4.](pics/harjoitus_5/4.png)  
*Palvelin pystyi edelleen ajamaan pythonia*  
  
![Kuva 5.](pics/harjoitus_5/5.png)  
*Poistin tuntiharjoituskessa luomani tiedoston ja hakemistot sisältöineen*  
  
Aloitin asennustyöt komennolla:  
*sudo apt-get install -y virtualenv*  

Komento hakee ja asentaa koneelle virtaulenvin, jonka avulla voidaan luoda eristettyjä Python-ympäristöjä.  
  
![Kuva 6.](pics/harjoitus_5/6.png)  
*Asennus sujui ilman virheilmoituksia*  
  
Seuraavaksi oli aika saa virtuaaliympäristö päälle komennoilla:  
*virtualenv --system-site-packages -p python env/*  
*source env/bin/activate*  
  
  
Ensimmäinen komento loi kansion env, jossa on saatavilla tuoreimmat paketit kansiosta lib/sitepackages/. Jälkimmäinen komento käynnisti virtuaaliympäristön.  
  
![Kuva 7.](pics/harjoitus_5/7.png)  
*Lopputulos*  
  
Tarkistin, että olin virtuaaliympäristön sisällä, jotta en vahingossa tee asennuksia jonnekin aivan toisaalle:  
*which pip*  
  
![Kuva 8.](pics/harjoitus_5/8.png)  
*Olin oikeassa paikassa*  
  
Editoin Microlla tiedostoon vaatimukseksi Djangon:
*micro requirements.txt*  

![Kuva 9.](pics/harjoitus_5/9.png)  
*Django lisättiin vaatimuslistaan ainoaksi merkinnäksi*  

Seuraaavaksi laittiin pip asentamaan django requirements.txt-tiedostosta ja tarkistettiin Djangon versionumero:  
*pip install -r requirements.txt*  
*django-admin --version*  
  
![Kuva 10.](pics/harjoitus_5/10.png)  
*Versio oli sama kuin ohjeessa*    
  
Loin projektin komennolla:  
*django admin startproject splitlyze*  
  
Sen jälkeen siirryin projektikansioon ja laitoin kehitysserverin päälle:  
*cd splitlyze*  
*./manage.py runserver*  
  
![Kuva 11.](pics/harjoitus_5/11.png)  
*Great success!*  
  
Seuraavaksi oli aika laittaa Djangon admin-konsoli toimimaan:  
*./manage.py makemigrations*  
*./manage.py migrate*  
  
![Kuva 12.](pics/harjoitus_5/12.png)  
*Komennot päivittivät projektin tietokannat*  

**superuserin luominen**  
*sudo apt-get install pwgen*  
*pwgen -s 30 1*  
*./manage.py createsuperuser*  
   
![Kuva 13.](pics/harjoitus_5/13.png)  
*Käyttäjän luominen onnistui*  
   
Asensin pwgen-salasanageneraattorin ja loin sen avulla superuserilleni tietoturvallisen salasanan.  Tämän jälkeen käynnistin testiserverin:  
*./manage.py runserve*  

![Kuva 14.](pics/harjoitus_5/14.png)  
*Pääsin kirjautumaan sisälle konsoliin*  

Päätin myös avata toisen terminaalin ja antaa serverin pyöriä toisessa, jotta sitä ei tarvitsi jatkuvasti käynnistellä. Siirryin kotihakemistoon ja kirjoitin komennon:  
  
*source env/bin/activate*
  
Tein saman which pip-varmistuksen kuin ylempänä, jotta pystyin olemaan varma siitä, että olin virtuaaliympäristön sisällä.  
  
Lopetin työt 13.33.  

Aloitin työt 14.32.  

Loin weppikäyttöliittymästä toisen käyttäjän ja annoin tälle kaikki oikeudet.  

![Kuva 15.](pics/harjoitus_5/15.png)  
*testikayttaja-käyttäjälle annettiin Staff- ja Superuser status*  
  
![Kuva 16.](pics/harjoitus_5/16.png)  
*En päässyt kirjautumaan, epäilin syyksi vääriä tunnistetietoja*  
  
Tein testikayttaja-userin uudestaan ja kirjauduin onnistuneesti.  
  
![Kuva 17.](pics/harjoitus_5/17.png)  
*Sisäänkirjautuminen onnistui toisella kerralla*  
  
![Kuva 18.](pics/harjoitus_5/18.png)  
*testikayttaja-tunnuksella oli nyt staff- ja superuser-oikeudet*  
  
Palasin komentokehotteeseen ja lisäsin projetiini ensimmäisen app:n, sekä merkinnän siitä asetustiedostoon:  
*./manage.py startapp settle*  
*micro splitlyze/settings.py*  
  
![Kuva 19.](pics/harjoitus_5/19.png)  
*Näkymä Micron editoidusta kohdasta, johon lisäsin oman appini*  
  
Tämän jälkeen oli aika lisätä malleja:  
*micro /settle/models.py*  
    
![Kuva 20.](pics/harjoitus_5/20.png)  
*Kirjoittamani python-koodi*  
  
Ensin tiedostoon tuodaan models django.db:stä ja sitten luodaan luokka Receipt, joka perii models.Modelin ominaisuudet. Tarkoituksenani on pitkässä juoksussa luoda maksujen jakamiseen ja talouden seuraamiseen ja analysointiin sopiva työkalu. Muutin myös Micron oletusasetuksen tabulaattorien automaattisesta muuttamisesta välilyönneiksi. Pythonissa ohjelmalohkojen hierarkiaa ilmaistaa vain sisennyksillä ja siten on äärimmäisen tärkeää, että sisennykset ovat oikein.  

**Tabulaattorin toiminnan muuttaminen tapahtui seuraavasti:**  
*ctrl + e*  
*set tabtospaces false*  
  
Tallensin kirjoittamani koodin ja tein tietokantamigraatiot komentokehotteesta:  
*./manage.py makemigrations*  
  
![Kuva 21.](pics/harjoitus_5/21.png)  
*Virheilmoituksen perusteella päättelin, että olin tehtyt kirjoitusvirheen parametrissä "max_lenght"*  
  
![Kuva 22.](pics/harjoitus_5/22.png)  
*Korjattu kirjoitusasu*  
  
![Kuva 23.](pics/harjoitus_5/23.png)  
*Seuraava virheilmoitus vihjasi, että DecimalFields kaipasi myös uutta parametriä max_digits*  
  
![Kuva 24.](pics/harjoitus_5/24.png)  
*Arvelin, että parametrit voitaisiin erotella toisistaan pilkulla*  
  
![Kuva 25.](pics/harjoitus_5/25.png)  
*Tällä kertaa ./manage.py makemigrations teki tehtävänsä mukisematta*  
  
Makemigrationsin onnistuttua annoin komennon:  
*./manage.py migrate*  

Makemigration luo migraatiot ja migrate suorittaa tietokantamigraatiot.  
  
Jäljellä oli vielä rekisteröinnin tekeminen admin.py-tiedostoon:  
*micro settle/admin.py*  
  
![Kuva 26.](pics/harjoitus_5/26.png)  
*Admin.py:n uusi sisältö*  
  
Tässä kerrottiin, että admin.siteen rekisteröidään Receipt-malli, joka perii models-luokan ominaisuudet.  
  
![Kuva 27.](pics/harjoitus_5/27.png)  
*testikayttaja pystyi lisäämään objekteja*  
  
Selkeämpää objektien nimeämistä varten lisäsin models.py-tiedostoon päivämäärän:  
*micro settle/models.py*  
  
![Kuva 28.](pics/harjoitus_5/28.png)  
*Muokattu models.py*  
  
![Kuva 29.](pics/harjoitus_5/29.png)  
*Kehitysserveri kertoi virheeestä sisennyksessä*  
   
![Kuva 31.](pics/harjoitus_5/31.png)  
*Debuggaaminen etenee, päättelin fiksuista virheilmoituksista, että minun täytyy löytää oikea tapa ilmaista mitä parametristä haluan*  
  
![Kuva 32.](pics/harjoitus_5/32.png)  
*Kokeilin formsin tuomista epäonnistuneesti*  
  
![Kuva 33.](pics/harjoitus_5/33.png)  
*Yritin myös periyttää luokkaan kahdesta eri luokasta*  
  
![Kuva 34.](pics/harjoitus_5/34.png)  
*Lopulta päädyin vain käyttämään modelsin DateFieldiä*  
  
![Kuva 35.](pics/harjoitus_5/35.png)  
Ajoin makemigrationin ja mpääsin päättämään mitä lomakkeeseen syötetään oletusarvona.  

![Kuva 36.](pics/harjoitus_5/36.png)  
*Lopputuloksena objekteillani oli nyt kolme ominaisuutta (shopName, date & amount)*  
  
Lopuksi muokkasin models.py:tä siten, että objektilistaus näyttäisi mukavammalta admin-konsolissa:  
*micro settle/models.py*  
  
![Kuva 37.](pics/harjoitus_5/37.png)  
*Muokattu models.py*  
  
Yritin saada riville tulostumaan myös päivämäärän ja hinnan, mutta sitten objektin muokkausta yrittäessä sain virheilmoituksen tuplesta (shopName, amount ja date ovat tuple-muotoon tallennettuja) ja siten kutsuun tuli joku vika.  
  
![Kuva 37.](pics/harjoitus_5/37.png)  
*Päivitetty admin-näkymä*  
  


  




## b) Prod. Make a production style Django install. Use Apache and mod_wsgi, disable DEBUG.