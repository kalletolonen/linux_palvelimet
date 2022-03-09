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
[Harjoitus 4]()
[Harjoitus 5]()
Harjoitus 6 on tämä harjoitus.

## b) Tarkista, että olet viitannut jokaisessa tehtävässä kaikkiin lähteisiin. Esimerkiksi kurssiin, tehtävänantoihin, käyttämiisi toisten kotitehtävärapotteihin, manuaalisivuihin, kotisivuihin...  
  
Tarkistin ja päivitin raporttini - päivitettyihin kohtiin merkitsin selkeästi, että niitä on päivitetty alkuperäisen päivityksen jälkeen. Versiohistoriasta voi tarvittaessa hankkia alkuperäisen palautuksen käyttöönsä.  
    
## c) Uusi komento Linuxiin. Tee uusi komento, joka tulostaa käyttäjälle hyödyllistä tietoa. Kokeile, että komento toimii kaikista hakemistoista ja muillakin käyttäjillä kuin omallasi.  
  
	micro hello

Tein komentoaihiooni sisällön. Taikakommentti (#! /usr/bin/bash) kertoo mikä ohjelma suorittaa shell-scriptin. Muut scriptissä olevat komennot ovat linuxin vakiokomentoja. Tiedostopäätteen antaminen ei ole pakollsita, joten en sellaista antanut.  
  
![Kuva 1.](pics/harjoitus_6/1.png)  
*hello-scriptin sisältö*  
  
	bash hello
	
Kokeilin scriptin toimivuutta ajamalla sen.  
  
![Kuva 2.](pics/harjoitus_6/2.png)  
*Scripti toimi, kun sen ajoi siinä kansiossa, jossa se sijaitsi.  
  
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
*Muokkasin shebangiin oikean hakemiston (/-merkki puuttui alusta)  
  
![Kuva 18.](pics/harjoitus_6/18.png)  
*Komento toimi eri hakemistoista*  
  
![Kuva 19.](pics/harjoitus_6/19.png)  
*Komento toimi myös toisella käyttäjällä*  
  
Lopetin työt 14.55.  
  
## e) Ratkaise valitsemasi vanha arvioitava laboratorioharjoitus tältä kurssilta. (Löytyy DuckDuckGolla, Googlella, linkeistä tältä sivulta tai hakemalla yläreunan hakutoiminnolla). Sovella tarvittaessa tehtäviä tähän toteutukseen sopivaksi, esimerkiksi PHP:n tilalta voi tehdä vastaavan Pythonilla; Flaskin tilalta käyttää Djangoa. Tai jättää pois jonkin epärelevantin kohdan.  
  
## f) Tee uusi tyhjä virtuaalikone (tai oikea kone) viimeisen kerran arvioitavaa labraa varten. Koneella ei saa olla luottamuksellisia tietoja. Kannattaa tehdä koneelle tarpeeksi iso virtuaalinen levy ja laittaa riittävästi RAM:ia. Guest additions saa olla asennettuna. Koneella ei saa olla muita asetuksia ennakkoon, eikä ylimääräisiä asennettuja ohjelmia.


  

  


