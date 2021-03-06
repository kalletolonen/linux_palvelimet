# **Harjoitus 6**

Aloitin työt 13.00.


Harjoitustyön tehtävänantona käytettiin Karvisen kotisivuilta löytyvää [h6-kohtaa](https://terokarvinen.com/2021/linux-palvelimet-ict4tn021-3018/#h6)

**Harjoituksen laitekokoonpano**  
*Järjestelmänä Win 11 + VirtualBox 6.0 + Debian 11*  
  
*Koneen perustiedot:*  
*Suoritin: AMD Ryzen 9 5900HS 8-ytiminen 3,1 - 4,5 GHz, 16 Mt välimuisti*  
*Muisti: 16 Gt LPDDR4X*  
*Näytönohjain: NVIDIA GeForce RTX 3050 Ti 4 Gt GDDR6*  
*Kiintolevy: 512 Gt M.2 2230 NVMe PCIe 3.0 SSD*  

## a) Kaikki tehtävät arvioitavaksi. Palauta linkit kaikkiin kotitehtäväraportteihisi. Arviointi tehdään ensisijaisesti tästä linkistä  
[Harjoitus 1](https://github.com/kalletolonen/linux_palvelimet/blob/main/tehtava1.md)  
[Harjoitus 2](https://github.com/kalletolonen/linux_palvelimet/blob/main/tehtava2.md)  
[Harjoitus 3](https://github.com/kalletolonen/linux_palvelimet/blob/main/tehtava3.md)  
[Harjoitus 4](https://github.com/kalletolonen/linux_palvelimet/blob/main/tehtava4.md)  
[Harjoitus 5](https://github.com/kalletolonen/linux_palvelimet/blob/main/tehtava5.md)  
Harjoitus 6 on tämä harjoitus.  

## b) Tarkista, että olet viitannut jokaisessa tehtävässä kaikkiin lähteisiin. Esimerkiksi kurssiin, tehtävänantoihin, käyttämiisi toisten kotitehtävärapotteihin, manuaalisivuihin, kotisivuihin...  
  
Tarkistin ja päivitin raporttini - päivitettyihin kohtiin merkitsin selkeästi, että niitä on päivitetty alkuperäisen palautuksen jälkeen. Versiohistoriasta voi tarvittaessa hankkia alkuperäisen palautuksen käyttöönsä.  
    
## c) Uusi komento Linuxiin. Tee uusi komento, joka tulostaa käyttäjälle hyödyllistä tietoa. Kokeile, että komento toimii kaikista hakemistoista ja muillakin käyttäjillä kuin omallasi.  
  
	micro hello

Tein komentoaihiooni sisällön. Taikakommentti (#! /usr/bin/bash) kertoo mikä ohjelma suorittaa shell-scriptin. Muut scriptissä olevat komennot ovat linuxin vakiokomentoja. Tiedostopäätteen antaminen ei ole pakollsita, joten en sellaista antanut.  
  
![Kuva 1.](pics/harjoitus_6/1.png)  
*hello-scriptin sisältö*  
  
	bash hello
	
Kokeilin scriptin toimivuutta ajamalla sen.  
  
![Kuva 2.](pics/harjoitus_6/2.png)  
*Scripti toimi, kun sen ajoi siinä kansiossa, jossa se sijaitsi*  
  
Muokkasin tiedoston käyttäjäoikeudet sellaisiksi, että scriptin saa kuka tahansa ajaa ja tarkistin että tekemäni muutokset tulivat voimaan.  
  
	sudo chmod ugo+x hello
	ls -ld hello

![Kuva 3.](pics/harjoitus_6/3.png)  
*Muutokset olivat voimassa*  
  
Seuraavaksi siirsin hello-tiedoston oikeaan kansioon, jotta sen pystyisi suorittamaan mistä tahansa. Siirto tuli tehdä sudo-oikeuksilla, sillä bin-kansion tiedostot ovat ajettavia ohjelmia ja sinne ei ole tavallisella käyttäjällä siirto-oikeuksia.  
  
	sudo cp hello /usr/local/bin/

![Kuva 4.](pics/harjoitus_6/4.png)  
*Tarkistin scriptin toimivuuden eri kansiosta ajamalla sen sieltä käsin*  
  
Tein uuden käyttäjän, jotta pääsisin testaamaan scriptiä toisella käyttäjällä.  
  
	sudo adduser testika
	
Syötin tarvittavat tiedot ja kirjauduin kallet-käyttäjällä ulos ja testika-käyttäjällä sisään.  
  
![Kuva 5.](pics/harjoitus_6/5.png)  
*Komento toimi myös toisella käyttäjällä*  
  
## d) Parametreja. Tee skripti, joka ottaa komentoriviparametreja. Esim. 'greetuser Tero' joka tulostaa "moi" ja parametrinä olevan nimen, esim "moi Tero".  
  
Päätin tehdä komentoriviltä toimivan python-scriptin, joka laskee käyttäjän painoindeksin.  
  
Ensin räpelsin kasaan koodin, joka toimii sellaisenaan, jotta pääsin käsittelemään parametrien tuomista komentorivistä erillisenä ongelmana, kun on sellaisenaan toimiva ohjelma.  
![Kuva 6.](pics/harjoitus_6/6.png)  
*Toimiva bmi-laskuri*  
  
![Kuva 7.](pics/harjoitus_6/7.png)  
*Tuote toimi ilman komentorivisyötteitä*  
  
Etsin [lähteen](https://www.geeksforgeeks.org/command-line-arguments-in-python/) komentorivisyötteen lukemiseksi ja muokkasin ohjelmaa sen perusteella. Tein myös kopion toimivasta koodistani komennolla:  
  
	cp bmi.py bmi2.py
	
![Kuva 8.](pics/harjoitus_6/8.png)  
*Uusi ohjelman sisältö*  
  
Aloitin toimivuuden testaamisen syöttämällä kaksi parametriä ja katsomalla siitä tapahtui.  
  
![Kuva 9.](pics/harjoitus_6/9.png)  
*Tulosteesta päättelin, että syötteen argumentti [0] ei ollut oikea paikka aloittaa*  
  
![Kuva 10.](pics/harjoitus_6/10.png)  
*Seuraava yritys*  
  
![Kuva 11.](pics/harjoitus_6/11.png)  
*Totesin, että ohjelma otti parametrit vastaan komentoriviltä*  
  
Muokkasin tiedostoon loput ohjelmastani ja testasin sitä.  
  
![Kuva 12.](pics/harjoitus_6/12.png)  
*Ohjelman sisältö*  
  
Tuloksena oli tietotyypistä annettu virheilmoitus.  
  
![Kuva 13.](pics/harjoitus_6/13.png)  
*Virheilmoituksen perusteella Python oletti saavansa potenssilaskuun numerotyyppistä tietoa, mutta saikin int/str-tyyppistä*  
  
Tein siis tyyppimuunnoksen samalla, kun tallensin komentoriltä tulleet parametrit muuttujiin.  
  
![Kuva 14.](pics/harjoitus_6/14.png)  
*Muutetut kohdat ohjelmassani*  
  
![Kuva 15.](pics/harjoitus_6/15.png)  
*Ohjelma toimi testattaessa*  
  
Tein vielä huvikseni ohjelmasta sellaisen version, jota pystyi ajamaan mistä tahansa järjestelmässä ja kenen tahansa toimesta.   
  
1. Muokkasin tiedoston nimeä: *mv bmi.py bmi*  
2. Muokkasin ajo-oikeuksia: *sudo chmod ugo+x bmi*  
3. Siirsin tiedoston bin-kansioon: *sudo cp bmi /usr/local/bin/
  

![Kuva 16.](pics/harjoitus_6/16.png)  
*Kokeilu tuotti virheilmoituksen pythonin sijainnista*  
  
Selvitin ongelmaa ja lopulta ratkaisin sen, sillä minulla oli virhe bmi-tiedoston shebangissä, eli taikakommentissa.  
  
![Kuva 17.](pics/harjoitus_6/17.png)  
*Muokkasin shebangiin oikean hakemiston (/-merkki puuttui alusta ja pythonista oikea versio*  
  
![Kuva 18.](pics/harjoitus_6/18.png)  
*Komento toimi eri hakemistoista*  
  
![Kuva 19.](pics/harjoitus_6/19.png)  
*Komento toimi myös toisella käyttäjällä*  
  
Lopetin työt 14.55.  
  
## e) Ratkaise valitsemasi vanha arvioitava laboratorioharjoitus tältä kurssilta. (Löytyy DuckDuckGolla, Googlella, linkeistä tältä sivulta tai hakemalla yläreunan hakutoiminnolla). Sovella tarvittaessa tehtäviä tähän toteutukseen sopivaksi, esimerkiksi PHP:n tilalta voi tehdä vastaavan Pythonilla; Flaskin tilalta käyttää Djangoa. Tai jättää pois jonkin epärelevantin kohdan.  
  
Aloitin työt 16.41.  
  
Valitsin toteutettavaksi labraharjoitukseksi Karvisen sivuilta tehtävän: [https://terokarvinen.com/2017/arvioitava-laboratorioharjoitus-linux-palvelimet-ict4tn021-4-tiistai-alkusyksy-2017-5-op/](https://terokarvinen.com/2017/arvioitava-laboratorioharjoitus-linux-palvelimet-ict4tn021-4-tiistai-alkusyksy-2017-5-op/)  
  
Aloitin työt tekemällä uuden, tyhjän virtualikoneen, kun olin ensin selaillut tehtävänantoa pintapuolisesti.  
  
![Kuva 20.](pics/harjoitus_6/20.png)  
*Virtuaalikone ruksutteli live-usb:tä käyntiin*  
  
Labratehtävän tehtävänannossa sanottiin: "Kehittäjämme haluavat käyttää LAMP (Linux Apache MySQL PHP) -pinoa. Asenna tarvittavat ohjelmistot ja tee tietokantaa käyttävä esimerkkiohjelma."  
  
Päätin soveltaa pinoa sen verran, että vaihdoin SQLiten ja Pythonin/Djangon kahden viimeisen tilalle.  
  
Live-tila ei valitettavasti lähtenyt toimimaan virtuaalikoneessani (eikä tuottanut mitään mustaa ruutua kummempaa virhetietoa), joten päätin kokeilla asennusohjelman käynnistämistä suoraan.  
  
### Käyttäjät  
  
Ensimmäiseksi päätin asentaan salasanamanagerin, jotta saisin hyvät salasanat käyttäjille muistiin harjoitusta varten. Pass-sovelluksen asennusta yrittäessäni huomisin, että repositorioita ei tullut esiasennettuina Debianin CLI-asennuksessa, joten päätin vetää asennuksen sileäksi ja aloittaa alusta, koska se olisi varmasti nopeampi tie kuin niiden asettaminen googlaamisen lisäksi kerralla oikein.  
  
![Kuva 21.](pics/harjoitus_6/21.png)  
*Toisella virtuaalikoneella, joka oli asennettu livenä, oli repositoriot kohdillaan ja asennus onnistui*  
  
Toisella asennuskerralla päätin antaa liven ladata itseään käyntiin ainakin vartin. Kärsimättömyyteni paljastui syyksi siihen, että live-asennus ei ollut toiminut, se olisi tarvinnut vain enemmän aikaa ladatakseen itsensä.  
  
Latasin pass-salasanamanagerin, gpg-avaingeneraattorin [työohjeella](https://keyring.debian.org/creating-key.html) ja pwgenin salasanojen generoimiseksi:  

*sudo apt-get update*  
*sudo apt-get install -y pass*  
*sudo apt-get install -y pwgen*  
*sudo apt-get install -y gnupg2*  
*gpg --list-keys --with-subkey-fingerprint* <-Näyttää gpg-avaimet  
*gpg --gen-key --default-new-key-algo=rsa4096/cert,sign+rsa4096/encr* <-Generoi gpg-avaimen  
  
Näiden komentojen jälkeen gpg kysyi passphrasea generointia varten ja annoin sellaisen.  
  
![Kuva 22.](pics/harjoitus_6/22.png)  
*Komento saatiin suoritettua*  
  
Sitten en enää ymmärtänyt mitä olisi seuraavaksi pitänyt tehdä, sillä ohjeen serverille lähetettävä avain esiintyy ohjeessa vain kerran - lähetyskäskyn yhteydessä. Niin siis että mikä avain lähetetään mihin ja miksi?  
  
Päätin käyttää harjoituksen salasanojen tallentamiseen Firefoxin salasanamanageria, sillä se oli ainakin helppokäyttöinen. Tähän harjoitustehtävään se oli varmasti myös tarpeeksi tietoturvallinen vaihtoehto - salasanat eivät olleet missään muussa käytössä kuin virtuaalikoneen sisällä olevilla kuvitteellisilla käyttäjillä.  
  
**Käyttäjät**  
Tehtävänannossa käyttäjinä olivat: Nakke Nertola, Håkan Värs, Einari Mikkonen, Einari Öljysaari ja Eija Vähäkäähkä.  

Tein heille tunnuksien tekemistä varten scriptin, joka nappaa 3 ensimmäistä kirjainta etu- ja sukunimistä ja tekee niistä käyttäjätunnuksen - tiesin jo tähän ryhtyessäni, että tähän menee 10 kertaisesti se aika mitä menisi asioiden tekemiseen käsin, mutta kokeilemalla oppisi takuulla enemmän.  
  
Asensin Micron:  
*sudo apt-get install -y micro*  

Tein skriptikansion:  
*mkdir scripts*  
  
päivitin järjestelmän, koska olin unohtanut tehdä sen alussa:  
*sudo apt-get upgrade*  
  
Lähdin rakentamaan käyttäjänimigeneraattoriani lähteiden [1](https://stackoverflow.com/questions/3194516/replace-special-characters-with-ascii-equivalent) ja [2](https://stackoverflow.com/questions/35964691/generating-username-using-python) perusteella.  
  
````
koodi jonka pohjalle rakensin nimen pilkkomisen osiin:  
  
full_name = input("Please enter your name: ")
first_letter = full_name[0]
space_index = full_name.find(" ")
three_letters_surname = full_name[space_index + 1:space_index + 4]
number = random.randrange (1,999)
username = (first_letter, three_letters_surname, number)
print = (username)
  
Koodi ääkkösten korvaamiseksi:  
#!/usr/bin/env python
# -*- coding: utf-8 -*-

import unicodedata
text = u'Cześć'
print unicodedata.normalize('NFD', text).encode('ascii', 'ignore')

````
  
![Kuva 23.](pics/harjoitus_6/23.png)  
*Muokattu koodi*  
  
![Kuva 24.](pics/harjoitus_6/24.png)  
*Ääkkösten muokkaaminen unix-ystävällisemmiksi onnistui*  
  
![Kuva 26.](pics/harjoitus_6/26.png)  
*Ensimmäinen while-looppi käy nimet läpi ja lisää ne listaan ilman ääkkösiä ja muita kummallisuuksia*  
  
![Kuva 27.](pics/harjoitus_6/27.png)  
*Toinen while-looppi pätkii nimet ja tekee niistä "3 kirjainta + 3 kirjainta + 1 numero"-tyylisiä käyttäjätunnusaihioita
  
![Kuva 28.](pics/harjoitus_6/28.png)  
*Ohjelman tuloste komentokehotteessa*  
  
Parannettavia asioita jäi paljon:  
-Nimet ovat kovakoodattuja listassa (ohjelma voisi hakea nämä vaikka csv-tiedostosta)  
-Käyttäjätunnukset tulisi generoinnin jälkeen kirjata tiedostoon, jotta ne olisivat helposti käytettävissä
-Käyttäjätunnusten ja salasanojen automaattinen luonti kokonaisuutena  
  
Lopetin työt 21.45 ajauduttuani sivuraiteille.  
  
Aloitin työt 14.14.  
  
Generoin viidelle käyttäjälle satunnaiset, 12 merkkiä pitkät salasanat:  
*pwgen -s 12 5*  
  
Loin käyttäjät adduser-komennolla ja käytin generoimiani käyttäjätunnuksia.  
  
````
sudo adduser tunnus
````  
  
Tallensin käyttäjätunnukset virtuaalikoneessa paikallisesti Firefoxin salasanamanageriin. Lopuksi tarkistin, että loin kaikille viidelle käyttäjälle tunnukset:  
*cut -d: -f1,3 /etc/passwd | egrep ':[0-9]{4}$' | cut -d: -f1*  
  
Lähde komennolle: [https://askubuntu.com/questions/257421/list-all-human-users](https://askubuntu.com/questions/257421/list-all-human-users)  
  
Tein komennosta itselleni scriptin listhumans, ja lisäsin sen paikalliseeen bin-kansioon. Uusien komentojen luomista on käsitelty tarkasti jo aiemmissa tehtäväkohdissa, enkä siten raportoinut sitä tähän tarkasti. Suunnitelmissani on kerätä hyödyllisistä scripteistä git-repositorio käyttööni.  
  
![Kuva 29.](pics/harjoitus_6/29.png)  
*Kommennon tuloste*  
  
![Kuva 30.](pics/harjoitus_6/30.png)  
*listhumans tulosti saman luettelon*  
  
**Apachen asennus ja käyttäjien sivut**  
  
Hain apachen koneelle ja tarkistin sen toimivuuden:  
*sudo apt-get install -y apache2*  
*sudo systemctl apache2.service*  
*sudo service apache2 status*  
  
Korvasin Apachen vakiosivun:  
*sudo micro var/www/html/index.html*    
Palvelu rullasi, joten tarkistin curlilla localhostin:  
*curl localhost*  
  
![Kuva 31.](pics/harjoitus_6/31.png)  
*Korvaava index.html saatiin tehtyä*  
  
Päädyin harjoitusmielessä tekemään scriptin käyttäjien kotisivujen luomiseksi.  
  
![Kuva 32.](pics/harjoitus_6/32.png)  
*Scripti luo syötteen mukaan kaikille käyttäjille kotisivut*  
  
Päätin myös, että teen aikaisempaan käyttäjätunnusgeneraattoriini tunnusten tallentamisen tiedostoon, jotta voin hyödyntää sitä jatkossa syötteenä kotisivugeneraattorissani.  
  
![Kuva 33.](pics/harjoitus_6/33.png)  
*Lisäsin loppuun koodia, jonka seurauksena käyttäjätunnukset tulostuvat tekstitiedostoon*  
  
![Kuva 34.](pics/harjoitus_6/34.png)  
*Käyttäjätunnukset listattuina*  
  
Parannettavaa jäi scripteihin, kuten aina:  
-Scripti joka tarkistaa, onko kyseinen käyttäjätunnus jo olemassa  
-Numeroiden lisääminen käyttäjätunnusten perään vain siinä tapauksessa, että kirjainyhdistelmä on jo käytössä  
-Käyttäjätunnuksien tekeminen järjestelmään generoiduilla salasanoilla  
-Käyttäjätunnuksien lähettäminen käyttäjille automaattisesti  
  
![Kuva 35.](pics/harjoitus_6/35.png)  
*Tässä parametrit syötettiin manuaalisesti tekemäni listhumans-komennon avulla, koska olin jo käsipelillä luonut käyttäjät*  
  
Seuraavaksi laitoin käyttäjien kotisivut päälle:  
*sudo a2enmod userdir*  
*sudo systemctl restart apache2*  
  
En saanut käyttäjien kotisivuja toimimaan ja vika löytyi scriptistäni, joka loi hakemistot ja sivut - olin epähuomiossa jättänyt sinne hakemistojen poiston niiden luomisen jälkeen päälle.  
  
![Kuva 36.](pics/harjoitus_6/36.png)  
*Korjattu scripti*  
  
![Kuva 37.](pics/harjoitus_6/37.png)  
*Käyttäjien sivut generoitiin tällä kertaa onnistuneesti*  
  
**Suuri palomuuri**  
  
Asensin palomuurin ja laitoin http- ja ssh-portit auki:  
*sudo apt-get install -y ufw*  
*sudo ufw allow 22/tcp*  
*sudo ufw allow 80/tcp*  
  
Tarkistin palomuurin tilanteen:  
*sudo ufw status*  
  
![Kuva 38.](pics/harjoitus_6/38.png)  
*Palomuuri oli kunnossa*  
  
**WhoWhere**  

Tein bashilla ajettavan scriptin, jonka tallensin ylempänä olevien tehtävien logiikalla ja käyttöoikeuksien muuttamisella oikeaan kansioon.  
  
![Kuva 39.](pics/harjoitus_6/39.png)  
*Scriptini sisältö*  
  
![Kuva 40.](pics/harjoitus_6/40.png)  
*Komento toimi myös luomallani testikäyttäjällä*  
  
**SneakyGarden.Example.com**  
  
Aloitin työt 11.13.  
  
Sovelletut työohjeet:  
[https://docs.djangoproject.com/en/4.0/intro/tutorial01/](https://docs.djangoproject.com/en/4.0/intro/tutorial01/)  
[https://github.com/kalletolonen/linux_palvelimet/blob/main/tehtava5.md](https://github.com/kalletolonen/linux_palvelimet/blob/main/tehtava5.md)  
  
Asensin virtualenvin ja loin Pythonille ympäristön:  
*sudo apt-get install -y virtualenv*  
*virtualenv --system-site-packages -p python env/*  

Tarkistin, että olen env:n sisällä:  
*which pip*  
  
![Kuva 41.](pics/harjoitus_6/41.png)  
*Kaikki oli kunnossa*  
  
Lisäsin djangon vaatimuksiin, asensin sen ja tarkistin version:  
*echo "django" |tee requirements.txt*  
*pip install -r requirements.txt*  
*django-admin --version*  

![Kuva 42.](pics/harjoitus_6/42.png)  
*Asennus oli onnistunut*  
  
Aloitin django-projektin:  
*django-admin startproject sneakygarden*  
  
Asensin hakemistopolkujen tarkasteluohjelman ja katsoin rakennetta:  
*sudo apt-get install -y tree*  
*tree sneakygarden*  
  
![Kuva 43.](pics/harjoitus_6/43.png)  
*Hakemistorakenne täsmäsi djangoprojektin lähteeseen*  
  
Siirryin projektikansiooni ja käynnistin kehitysserverin:  
*cd sneakygarden*
*./manage.py runserver*  
  
![Kuva 44.](pics/harjoitus_6/44.png)  
*Serveri käynnistyi*  
  
Serveri antoi tavanomaiset virheilmoitukset migraatioiden tekemättömyydestä, enkä ohjeen mukaisesti kiinnittänyt niihin huomiota vielä tässä vaiheessa.  
  
![Kuva 45.](pics/harjoitus_6/45.png)  
*Virheilmoitukset migraatioista*  
  
Avasin toisen konsoli-ikkunan, siirryin sneakygarden-hakemistoon ja alustin applikaation:  
*./manage.py startapp ninjamoves*  
  
![Kuva 46.](pics/harjoitus_6/46.png)  
*Myös applikaation hakemistorakenne oli samanlainen kuin ohjeessa*  
  
**Ensimmäisen view:n rakentaminen**  
  
Editoin views.py-tiedostoa:  
*micro ninjamoves/views.py*  
  
![Kuva 47.](pics/harjoitus_6/47.png)  
*Tiedoston sisältö*  
  
Seuraavaksi view tuli mapata URL:iin:  
*micro ninjamoves/urls-py*  

![Kuva 48.](pics/harjoitus_6/48.png)  
*urls.py:n sisältö*  
  
Siirryin muokkaamaan PROJEKTIN urls.py:tä:  
*micro sneakygarden/sneakygarden/urls.py*  
  
![Kuva 49.](pics/harjoitus_6/49.png)  
*Muokattu sisältö korostettuna*  
  
![Kuva 50.](pics/harjoitus_6/50.png)  
*Olin unohtanut pilkun määritysten välistä*  
  
![Kuva 51.](pics/harjoitus_6/51.png)  
*Import puuttui myös*  
  
Korjasin projektitiedostoni urls.py:n sisältöä.  
  
![Kuva 52.](pics/harjoitus_6/52.png)  
*Uusi sisältö*  
  
![Kuva 53.](pics/harjoitus_6/53.png)  
*Onnistunut testi - haluamani sivu oli näkyvissä*  
  
Lopetin työt 12.05.  
  
Aloitin työt 12.31.  
  
**Tietokanta-asetukset**  
  
Muokkasin settings.py:tä projektikansioni alakansiossa:  
*micro sneakygarden/setting.py*  
  
![Kuva 54.](pics/harjoitus_6/54.png)  
*Muokkasin hosts-kohtaa tässä vaiheessa*  
  
Tein tietokantamigraatiot:  
*./manage.py migrate*  
  
![Kuva 55.](pics/harjoitus_6/55.png)  
*Migraatiot onnistuivat*  
  
Lisäsin vielä 127.0.0.1-osoitteen ALLOWED_HOSTS-parametriin.  
  
![Kuva 56.](pics/harjoitus_6/56.png)  
*Admin-konsoli aukesi oikein*  
  
**Models**  
  
Rakensin ninjamoves-applikaatioon models.py:n:  
*micro ninjamoves/models.py*  
  
![Kuva 57.](pics/harjoitus_6/57.png)  
*models.py:n sisältö*  
  
Lisäsin settings.py-tiedostoon viittauksen INSTALLED_APPS-parametriin.  
  
![Kuva 58.](pics/harjoitus_6/58.png)  
*Lisätty parametri*  
  
Ajoin migraatiot:  
*./manage.py makemigrations ninjamoves*  
*./manage.py migrate*  
  
![Kuva 59.](pics/harjoitus_6/59.png)  
*Migraatiot onnistuivat*  
  
**Superuserin luominen**  

Ylläpitäjäksi tuli tehtävänannossa Eija Vähäkäähkä, joten tein hänelle superuserin samalla käyttäjätunnuksella kuin mitä hänellä on järjestelmässäkin, jotta sen muistaminen olisi helpompaa:  
*./manage.py createsuperuser*  
  
![Kuva 60.](pics/harjoitus_6/60.png)  
*Superuserin luominen onnistui*  
  
![Kuva 61.](pics/harjoitus_6/61.png)  
*Sisäänkirjautuminen admin-konsoliin onnistui*  
  
Konsolissa ei kuitenkaan ollut näkyvissä malliani, joten palasin muokkaamaan admin.py:tä:  
*micro ninjamoves/admin.py*  
  
![Kuva 62.](pics/harjoitus_6/62.png)  
*admin.py:n uusi sisältö*  
  
![Kuva 63.](pics/harjoitus_6/63.png)  
*Eijan admin-näkymä*  
  
Loin Eijalle tehtävänannossa olevat liikkeet tietokantaan admin-näkymästä.  
  
Lisäsin myös models.py-tiedostoon nätimmän returnin, jotta Eijan on helpompi tarkastella liikkeitä käyttöliittymästään.  
  
![Kuva 64.](pics/harjoitus_6/64.png)  
*models.py:n return*  
  
![Kuva 65.](pics/harjoitus_6/65.png)  
*Eijan admin-näkymä*  
  
Lopetin työt 13.21.  
  
Aloitin työt 14.15.  
  
**Näkymät webbisivulle**  
  
Seuraavaksi lisäsin näkymiä ninjamoves/views.py-tiedostoon:  
*micro ninjamoves/views.py*  
  
![Kuva 66.](pics/harjoitus_6/66.png)  
*Tiedoston uusi sisältö*  
  
Sitten muokkasin ninjamoves/urls.py-tiedostoa:  
*micro ninjamoves/urls.py*  
  
![Kuva 67.](pics/harjoitus_6/67.png)  
*urls.py:n uusi sisältö*  
  
![Kuva 68.](pics/harjoitus_6/68.png)  
*Testi todisti toimivuuden*  
  
Muokkasin ninjamoves/views.py:tä.  
  
![Kuva 69.](pics/harjoitus_6/69.png)  
*Uusi sisältö*  
  
![Kuva 70.](pics/harjoitus_6/70.png)  
*Testisivusto toimi*  
  
Jäljellä oli siis sivun saattaminen osoitteeseen hosts-tiedoston avulla:
SneakyGarden.Example.com  
  
Lopetin työt 14.50 ja latasin tehtävän githubiin.  
  
Aloitin työt 15.15.  
  
**Tuotantoasennus, VirtualHosts ja domainin emulointi**  
  
Lähteet:   [https://terokarvinen.com/2018/name-based-virtual-hosts-on-apache-multiple-websites-to-single-ip-address/](https://terokarvinen.com/2018/name-based-virtual-hosts-on-apache-multiple-websites-to-single-ip-address/)  
[https://github.com/kalletolonen/linux_palvelimet/blob/main/tehtava5.md](https://github.com/kalletolonen/linux_palvelimet/blob/main/tehtava5.md)  
  
Kopioin projektini kotihakemistostani ja tein publicwsgi-kansion:  
*sudo cp -r sneakygarden publicwsgi*  
  
Tein uuden conffitiedoston Apachelle:  
*sudo micro /etc/apache2/sites-available/sneakygarden.conf*  
  
![Kuva 71.](pics/harjoitus_6/71.png)  
*Tiedoston sisältö*  
  
Enabloin tekemäni conf-tiedoston, poistin vanhan käytöstä ja testasin sisällön oikeellisuuden:  
*sudo a2ensite sneakygarden.conf*  
*sudo a2dissite 000-default.conf*  
*sudo /sbin/apache2ctl configtest*  
  
![Kuva 72.](pics/harjoitus_6/72.png)  
*Conf-tiedosto oli validi*  
  
Käynnistin Apachen uudestaan:  
*sudo systemctl restart apache2*  
  
Tein staattiselle sisällölle hakemiston ja tiedoston:  
*sudo mkdir -p publicwsgi/sneakygarden/static/*  
*echo "Static ninja" |tee publicwsgi/sneakygarden/static/index.html*  
  

Tein conffitiedostossa mainitun static-kansion ja sinne index.html-tiedoston.  
  
![Kuva 73.](pics/harjoitus_6/73.png)  
*curl-testi tuotti tekemäni staattisen sivun määrittämästäni osoitteesta*  
  
Djangon konffiohjeet seuraavaan kohtaan nappasin Karvisen sivuilta:  
[https://terokarvinen.com/2022/deploy-django/](https://terokarvinen.com/2022/deploy-django/)  
  
**sneakygarden.conf-tiedoston uusi sisältö**  
````
Define TDIR /home/kallet/publicwsgi/sneakygarden
Define TWSGI /home/kallet/publicwsgi/sneakygarden/sneakygarden/wsgi.py
Define TUSER kallet
Define TVENV /home/kallet/publicwsgi/env/lib/python3.9/site-packages
# See https://terokarvinen.com/2022/deploy-django/

<VirtualHost *:80>
        Alias /static/ ${TDIR}/static/
        <Directory ${TDIR}/static/>
                Require all granted
        </Directory>

        WSGIDaemonProcess ${TUSER} user=${TUSER} group=${TUSER} threads=5 python-path="${TDIR}:${TVENV}"
        WSGIScriptAlias / ${TWSGI}
        <Directory ${TDIR}>
             WSGIProcessGroup ${TUSER}
             WSGIApplicationGroup %{GLOBAL}
             WSGIScriptReloading On
             <Files wsgi.py>
                Require all granted
             </Files>
        </Directory>

</VirtualHost>

Undefine TDIR
Undefine TWSGI
Undefine TUSER
Undefine TVENV
````

Latasin mod-wsgi:n:  
*sudo apt-get install -y libapache2-mod-wsgi-py3*  
  
Käynnistin serverin uudestaan tarkistettuani syntaksin:  
*sbin/apache2ctl configtest*  
*sudo systemctl restart apache2*  
  
Sain virheilmoituksen Djangosta ja arvailin, että hakemiston siirtämisellä voisi olla ollut jokin vaikutus siihen, että mod_swgi ei löydä djangoa(?)  
  
![Kuva 74.](pics/harjoitus_6/74.png)  
*Virheilmoitus Djangosta*  
  
Päätin kokeilla virtualenvin määrittelemistä uudelleen public_wsgi-kansiossa:  
*virtualenv -p python3 --system-site-packages env*  
  
Jouduin ajamaan käskyn uudestaan sudolla, sillä ilman sitä tuli virheilmoitus siitä, että kohteeseen ei voi kirjoittaa.  
  
Totesin että tilanne ei tästä muuttunut, enkä enää osannut kokeilla muuta. Päätin palata aiheeseen myöhemmin täysjärkisenä ja kokeilla projektin tekemistä uudelleen publicwsgi-kansioon alusta lähtien, enkä kopioiden jo olemassa olevaa kansiota - jos se vaikka sekoitti (jätti siirtämättä) jotain asetuksia.  
  
Lopetin työt testattuani alkuperäisen projektini edelleen toimivaksi 16.53.  
  
Aloitin työt 14.15.  
  
Yö toi ratkaisun ongelmaan, minulla oli jäänyt vanha conf-tiedosto käyttöön.  
  
Käytössä olevan conf-tiedoston voi tarkistaa hakemalla hakemiston sisällön:  
*sudo ls /etc/apache2/sites-enabled/*  
  
Vaihdoin sneakygarden.conf-tiedoston käyttöön ja käynnistin demonin uudelleen:  
*sudo a2dissite 000-default.conf*  
*sudo a2ensite sneakygarden.conf*  
  
Tarkistin, että demoni oli oikea:  
*curl -sI localhost|grep Server*  
  
![Kuva 75.](pics/harjoitus_6/75.png)  
*curl tuotti toivotun tuloksen*  
  
![Kuva 76.](pics/harjoitus_6/76.png)  
*Myös selain näytti siltä mitä pitikin*  
  
Seuraavaksi otin DEBUG-tilan pois käytöstä editoimalla settings.py:tä:  
*micro hakemisto/settings.py*  
  
![Kuva 77.](pics/harjoitus_6/77.png)  
*Editoitu kohta tiedostossa*  
  
![Kuva 78.](pics/harjoitus_6/78.png)  
*Eija pystyi lisäämään admin-konsolista uuden ninjaliikkeen*  
  
**Admin-konsolin ulkoasun parantaminen**  
  
*micro hakemisto/settings.py*  
  
![Kuva 79.](pics/harjoitus_6/79.png)  
*Lisäsin rivit 14 ja 17*  
  
Sitten ajoin collectstaticin:  
*./manage.py collectstatic*  
  
![Kuva 80.](pics/harjoitus_6/80.png)  
*Admin-konsoli sai uuden ilmeen*  
  
**Uusi käyttäjä**  
  
Jussi Laitavalosta tuli järjestelmän uusi ylläpitäjä. Generoin Jussille uuden käyttäjätunnuksen lisäämällä hänet generointiscriptiini ja generoin vahvan salasanan pwgenillä:  
*python3 namegen.py*  
*cat output.txt*  
*pwgen 12 1*  
  
![Kuva 81.](pics/harjoitus_6/81.png)  
*Uusi käyttäjä luotiin onnistuneesti*  
  
Lopuksi lisäsin Jussin sudo-ryhmään:  
*sudo adduser juslai5 sudo*  
  
![Kuva 82.](pics/harjoitus_6/82.png)  
*Lisäys onnistui*  
  
Sitten oli jäljellä sivuston saattaminen osoitteeseen:  
SneakyGarden.Example.com  
  
Muokkasin conf-tiedostoa:  
sudo micro /etc/apache2/sites-available/sneakygarden.conf*  
  
Lisäämäni uusi VirtualHost.  
  
````
</VirtualHost>

<VirtualHost *:80>
 ServerName sneakygarden.example.com
 ServerAlias www.sneakygarden.example.com
 DocumentRoot /home/kallet/publicwsgi/sneakygarden/ninjamoves
 <Directory /home/kallet/publicwsgi/sneakygarden/ninjamoves>
   Require all granted
 </Directory>
</VirtualHost>

````  
    
Muokkasin hosts-tiedostoa:  
*sudo micro /etc/hosts*  
  
````
# Host addresses
127.0.0.1  localhost
127.0.1.1  labraharjoitus2
127.0.0.1  sneakygarden.example.com
::1        localhost ip6-localhost ip6-loopback
ff02::1    ip6-allnodes
ff02::2    ip6-allrouters
````  
  
Käynnistin demonin uudestaan ja tarkistin virheilmoitukset kokeiltuani noutaa sivuja domainista:  
sudo cat :10  /var/log/apache2/other_vhosts_access.log  
  
````
sneakygarden.example.com:80 127.0.0.1 - - [12/Mar/2022:16:49:54 +0200] "GET /ninjamoves/ HTTP/1.1" 403 506 "-" "Mozilla/5.0 (X11; Linux x86_64; rv:91.0) Gecko/20100101 Firefox/91.0"

sneakygarden.example.com:80 127.0.0.1 - - [12/Mar/2022:16:49:56 +0200] "GET / HTTP/1.1" 403 505 "-" "Mozilla/5.0 (X11; Linux x86_64; rv:91.0) Gecko/20100101 Firefox/91.0"

````
  
Localhost/ninjamoves toimi edelleen moitteestomasti.  
  
Poistin koko VirtualHost-lisäykseni ja sain pseudodomainin toimimaan miltei oikein.  
  
![Kuva 83.](pics/harjoitus_6/83.png)  
*Toimi miltei niin kuin pitikin - ei suoraan domainista, mutta alikansion kautta*  
  
Tehtävän viimeinen ratkaisu jäi mysteeriksi.  
  
Lopetin työt 17.15.  
  
Loput tehtävän toimet liittyivät labraharjoituksen palauttamiseen ja palautteen antamiseen. Ne olivat sellaisenaan epäoleellisia, joten jätin ne tekemättä.  
  
## f) Tee uusi tyhjä virtuaalikone (tai oikea kone) viimeisen kerran arvioitavaa labraa varten. Koneella ei saa olla luottamuksellisia tietoja. Kannattaa tehdä koneelle tarpeeksi iso virtuaalinen levy ja laittaa riittävästi RAM:ia. Guest additions saa olla asennettuna. Koneella ei saa olla muita asetuksia ennakkoon, eikä ylimääräisiä asennettuja ohjelmia.

Asensin uuden virtuaalikoneen - löysin myös toimivat asennusohjeet Guest additionsin asentamiseksi:  
[https://kifarunix.com/install-virtualbox-guest-additions-on-debian-11/](https://kifarunix.com/install-virtualbox-guest-additions-on-debian-11/)  
  
