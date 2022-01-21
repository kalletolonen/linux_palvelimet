**Harjoitus1**

## z)

### FSF: Free Software Definition

-Määritelmän mukaisesti käyttäjillä on oikeus käyttää, kopioida, jakaa, tutkia ja muokata ohjelmakoodia/ohjelmistoa
-Mikäli ohjelmakoodi ei täytä näitä kohtia, se ei ole FSF:n määritelmän mukaisesti vapaata koodia
-Vapaa ohjelmakoodi voi olla kaupallista

Lähde: https://www.gnu.org/philosophy/free-sw.html

Vapaata ohjelmakoodia voi ja kannattaa siis hyödyntää oman tekemisensä apuna ja pohjana, jolloin pyörää ei tarvitse keksiä uudestaan ja pääsee rakentamaan hyvien perustusten päälle.

### Karvinen 2021: Install Debian on VirtualBox

-Linuxiin on mahdollista tutustua muilla käyttöjärjestelmillä, kun käytetään virtualisointia

Asennuksen päävaiheet tutoriaalista:
1. Lataa oikea levykuva
2. Lataa ja asenna virtualisointiohjelmisto
3. Asenna käyttöjärjestelmä levykuvaa käyttäen virtualisointialustan päälle
4. Muista käyttää kunnollisia salasanoja!
5. Päätä asennus asennusohjelman ohjeiden mukaisesti
6. Käynnistä järjestelmä uudestaan ja kirjaudu sisään
7. Aja järjestelmäpäivitykset
8. Käytä Linuxia

Lähde: https://terokarvinen.com/2021/install-debian-on-virtualbox/

Virtualisointi on helppo tapa kokeilla erilaisia Linux-distroja - asentaminen vie muutaman minuutin ja mitään pysyvää vahinkoa ei ole mahdollista saada aikaan.

### Karvinen 2016: Raportin kirjoittaminen

-Raporttiin tulee kirjoittaa tarkasti mitä on tehty ja mitä tekemisestä seurasi  
-Raporttia tulee kirjoittaa samalla kun tekee työtä  
-Helpointa on tehdä raportti suoraan sähköiseen muotoon  
-Hyvä raportti on:  
--Toistettava (Toinen opiskelija voi validoida tulokset toistamalla raportin toimet)  
--Täsmällinen (Raportissa tulee olla myös esim. kellonajat, käytetyt komennot, onnistumiset ja epäonnistumiset)  
--Helppolukuinen (Tekstin tulee olla selkeää, jäsenneltyä ja julkaisukanavan demografian huomioivaa)  
--Lähdeviitteellinen (Viittaukset tuovat raportille uskottavuutta ja antavat tunnustusta alkuperäiselle lähteelle)  

-GPL-lisenssin käyttäminen on suositeltavaa  
  
Raporttiin tulee kirjoittaa vain oikeasti tapahtuneita asioita ja muiden työtä ei saa plagioida.
  
Lähde: https://terokarvinen.com/2006/raportin-kirjoittaminen-4/
  
Työnsä dokumentoinnilla pääsee siis helposti virheidensä jäljille. Hyvällä dokumentoinnilla voi tarjota monimutkaisten ongelmien ratkaisuun ulkopuolisille tahoille hyvän aloituspisteen.

## a)

Asensin Debianin VirtualBox-alustalle, koska minulla on käytössäni vain yksi tietokone ja tarvitsen koulutyössäni myös Microsoftin tuotteita, joiden käyttäminen toisella käyttöjärjestelmällä menee väistämättä monimutkaiseksi. Aloitin työt noin kahdelta ja dokumentoin niitä samalla. Valmista tuli puoli neljään mennessä. Päätin tehdä raportoinnin markdown-formaattia hyödyntäen, sillä tavoitteenani on rakentaa portfoliota pikkuhiljaa GitHubiin ja .md on siellä tuettu tiedostomuoto.

**Asennusvaiheet**:

1. Latasin kurssilla käytössä olevan version Debianista osoitteesta: https://cdimage.debian.org/images/unofficial/non-free/images-including-firmware/current-live/amd64/iso-hybrid/debian-live-11.2.0-amd64-xfce+nonfree.iso
2. Latasin VirtualBoxin osoitteesta: https://download.virtualbox.org/virtualbox/6.0.24/VirtualBox-6.0.24-139119-Win.exe
3. Asensin VirtualBoxin
4. Käynnistin VirtualBoxin ja aloitin asennustyöt

![1.kuva](/pics/harjoitus_1/1.png)  
*VirtualBoxin aloitusnäkymä*

Painoin New-nappia ja aloitin virtuaalikoneen luomisen.  
![2.kuva](/pics/harjoitus_1/2.png)  
*VirtualBoxin Create Virtual Machine -näkymä*  

Määritin virtuaaliseksi levytilaksi (joka siis allokoidaan oikealta levyasemalta dynaamisesti todellisen käytön mukaan) n. 50 gigaa.  
![3.kuva](/pics/harjoitus_1/3.png)  
*VirtualBoxin levynluonti*  

![4.kuva](/pics/harjoitus_1/4.png)  
*Toistaiseksi tyhjän koneen tietoja*  

![5.kuva](/pics/harjoitus_1/5.png)  
*Käynnistin virtuaalikoneen Start-nappulasta ja valitsin levykuvaksi kohdassa 1 lataamani levykuvan.*  

![6.kuva](/pics/harjoitus_1/6.png)  
*Valitsin asennusvalikosta ylimmän vaihtoehdon, joka starttaa Linuxin suoraan työpöytänäkymään, mutta ei varsinaisesti vielä asenna mitään.*  

![7.kuva](/pics/harjoitus_1/7.png)  
*Kone pyöritteli hetken aikaa itseään valmiiksi ja sitten käynnistin asennusohjelman työpöydältä tuplaklikkaamalla "Install Debian"-pikakuvaketta. Harmikseni VirtualBox ei salli kuvakaappausten ottamista Windowsin äärimmäisen kätevällä Win + Shift + s -yhdistelmällä, jolloin kuvan voi rajata samantien. Valikoista löytyi kuitenkin keino tehdä kuvankaappaus ja projekti pääsi eteenpäin. Asennuskieleksi valikoin englannin.*  

![8.kuva](/pics/harjoitus_1/8.png)  
*Lokalisaatioasetukseksi valitsin suomen aikavyöhykkeen.*  

![9.kuva](/pics/harjoitus_1/9.png)  
*Näppäimistöasetukseksi valitsin suomalaisen asettelun.*  

![10.kuva](/pics/harjoitus_1/10.png)  
*Valitsin levyn alustamisen ja syötin salasanan sen kryptaamista varten.*  

![11.kuva](/pics/harjoitus_1/11.png)  
*Syötin tarvittavat tiedot käyttäjätunnusta varten ja valitsin koneen nimeksi sellaisen, mistä identiteettiäni ei voida päätellä yhdistäessäni vieraisiin verkkoihin.*  

![12.kuva](/pics/harjoitus_1/12.png)  
*Hyväksyin syöttämäni asennusasetukset ja painoin Install-nappia.*  

![13.kuva](/pics/harjoitus_1/13.png)  
*Asennus valmistui n. viidessä minuutissa - tästä voi kiittää nopeahkoa ssd-levyä*  

![14.kuva](/pics/harjoitus_1/14.png)  
*Asennuksen päätteeksi käynnistin virtuaalisen koneen uudestaan*  

![15.kuva](/pics/harjoitus_1/15.png)  
*Kryptattu levy pyysi salasanaa uudelleenkäynnistämisen yhteydessä*  

![16.kuva](/pics/harjoitus_1/16.png)  
*Pari näyttöä ehti tämän jälkeen vilahtaa ohi liian nopeasti, jotta niistä olisi saanut kuvakaappauksia. Odotin muutaman minuuttin ajan ja näytöllä oli edelleen vain pelkkää mustaa.*  
  
Käynnistin virtuaalikoneen uudestaan, jotta selviäisi onko vika koneessa vai näppäimistön ja selkänojan välissä. Luen [Karvisen artikkelin](https://terokarvinen.com/2021/install-debian-on-virtualbox/) uudemman kerran ja buuttaan koneen.
  
![17.kuva](/pics/harjoitus_1/17.png)  
*Nyt ehdin lukea myös vaihtoehdot ja valitsen ylimmän*  

![18.kuva](/pics/harjoitus_1/18.png)  
*Tällä kertaa järjestelmä latautui.*  

![19.kuva](/pics/harjoitus_1/19.png)  
*Sisäänkirjautumisen kanssa ei ollut ongelmia*  

![20.kuva](/pics/harjoitus_1/20.png)  
*Avaan alapalkista komentokehotteen ja laitan koneen lataamaan päivityksiä*  
  
Latasinn päivitykset komennoilla:  
*sudo apt-get update*  
*sudo apt-get -y dist-upgrade*  
  
Sudo viittaa pääkäyttäjän oikeuksiin - sellaiset on oltava, jos mielii tehdä muutoksia järjestelmään. Syötin salasanan terminaaliin ja päivitykset saatiin hoidettua yhdestä paikasta.  
  
## b)Listaa testaamasi koneen rauta  

Käytin listaukseen tehtävänannon komentoa:  
sudo lshw -short -sanitize  
  
Komento tuottaa tulokseksi virheilmoituksen:  
bash: command not found  
  
Päättelen, että lshw-käsky ei kuulu jakelun vakiotuotteisiin. Kirjoitan seuraavaksi käskyksi:  
sudo apt-get install lshw  
  
Tämän jälkeen komento tuottaa tuloksen.  
  
![21.kuva](/pics/harjoitus_1/21.png)  
*Listaus virtuaalikoneeni raudasta*  
  
**Selitys listauksen riveille**  
Listauksessa oli järjestelmän laitteita, joista ensimmäisenä löytyi bios (Basic Input Output System), jonka avulla tietokoneen rauta voi käynnistyä ja keskustella seuraavan ohjelmiston abstraktiotason kanssa. Muistia listauksesa oli 4 gigaa, joka tarkoittaa siis virtuaalikoneeseen allokoitua määrää järjestelmän todellisesta kapasiteetista. Tietokoneen prosessori näkyy sellaisenaan. Muuta huomionarvoista oli se, että Virtualbox oli emuloinut Linuxille käyttöön cd-aseman ja langaton verkkoyhteys ulkomaailmaan on toteutettu VirtualBoxin sisällä ikään kuin se olisi kiinteä verkkoyhteys.  
  
## c) Asenna kolme itsellesi uutta ohjelmaa.  
  
Asensin kaikki ohjelmat komentokehotteesta käyttämällä komentoa:  
  
sudo apt-get install ohjelmannimi  
  
**Chromium**  
  
![22.kuva](/pics/harjoitus_1/22.png)  
*Käytän Firefoxia ja päätin kokeilla vaihtoehtoista selainta*  
  
**Libreoffice**  
![23.kuva](/pics/harjoitus_1/23.png)  
*Olen käyttänyt enimmäkseen Google Sheetsiä, sillä se on ilmainen ja pilvinatiivi sovellus**  
  
**Vim + (Python)**  
![24.kuva](/pics/harjoitus_1/24.png)  
*Halusin kokeilla ohjelmointia alkeellisilla työkaluilla, joten asensin tekstieditorin*  
  
Käskyjä sai googlata, jotta sain koodinpätkän tallennettua tiedostoon.  
  
:w tiedostonnimi luo tiedoston  
:q poistuu vim:stä  
  
![25.kuva](/pics/harjoitus_1/25.png)  
*"Hello World" toimii*  
  
## d) Mitä lisenssiä kukin näistä ohjelmista käyttää?   
  
**Chromium**  
  
Lisenssi: [3-clause license ("BSD License 2.0", "Revised BSD License", "New BSD License", or "Modified BSD License")](https://en.wikipedia.org/wiki/BSD_licenses#3-clause_license_(%22BSD_License_2.0%22,_%22Revised_BSD_License%22,_%22New_BSD_License%22,_or_%22Modified_BSD_License%22))  
Oikeudet: BSD-lisenssi antaa levitysoikeudet mihin tahansa käyttötarkoitukseen, kunhan alkuperäiset copyright-merkinnät ja huomiolausekkeet(disclaimer) säilytetään. Sitä voi siis käyttää myös suljetun lähdekoodin ohjelmistossa.  
Velvollisuudet: Alkuperäisten tekijöiden nimiä ei saa käyttää koodista kehitetyn ohjelmiston mainostamisessa ilman heidän lupaansa.  
  
Lähde: https://en.wikipedia.org/wiki/Chromium_(web_browser)  
  
Googlen osuus koodista on BSD-lisenssin alla ja muut osat ovat lisensoituja MIT, LGPL, Ms-PL ja MPL/GPL/LGPL-lisensseillä. Ylläolevat kommentit koskevat BSD-lisenssiä.   
  
-[MIT-lisenssi](https://en.wikipedia.org/wiki/MIT_License) on vastaava kuin BSD-lisenssi.   
-[LGPL-lisenssin](https://en.wikipedia.org/wiki/GNU_Lesser_General_Public_License) erona on se, että mikäli lähdekoodia muokkaa, tulee muokatun osan lisenssiksi myös LGPL.  
-[Ms-PL](https://en.wikipedia.org/wiki/Shared_Source_Initiative#Microsoft_Public_License_(Ms-PL)) on Microsoftin lisenssi, joka sallii valmiin ohjelmakoodin (compiled) jakamisen eteenpäin, mutta koodin muokkaamista ei. Ms-PL ei mielestäni myöskään salli lähdekoodin jakamista.  
-MPL/GPL/LGPL-monilisenssointi jäi minulle hieman epäselväksi  
  
Kaikki mainittuja lisenssejä voi käyttää kaupallisiin tarkoituksiin.  
  
**LibreOffice**  
  
Lisenssi: [Mozilla Public License](https://www.mozilla.org/en-US/MPL/2.0/)  
Oikeudet: Saa käyttää osana suljettua ohjelmistoa tai avointa ohjelmistoa. Voi käyttää kaupallisiin tarkoituksiin.  
Velvollisuudet: Käytettyjen komponenttien on oltava myös MPL-ehtojen alla  
  
**Vim**  
  
Lisenssi: Charitytware  
Oikeudet/velvollisuudet: Saa jaella miten tahansa, kunhan lisenssiteksti on mukana paketissa. Pakettiin voi myös liittää omia VIM-scriptejään. Muokattua ohjelmistoa saa jaella, jos neljä ehtoa täyttyvät:  
1. Lisenssitekstiä ei saa muokata  
2.   
a) Muokattussa versiossa tulee olla muokkaajan yhteystiedot ja ylläpitäjälle tulee ilmaiseksi toimittaa lähdekoodi pyydettäessä. Ylläpitäjä voi liittää lähdekoodin osaksi viralliseen ohjelmistoversioon.  
b) Muokattua versiota saa muokata edelleen, a-kohdan ehto pätee myös seuraaviin muokkauskertoihin  
c) Omalle koodilleen voi asettaa muun lisenssiehdon, mutta lähdekoodin on oltava paketissa mukana. Lisenssi ei saa rajoittaa muiden oikeutta tehdä muutoksia ohjelmistoon.  
d) Ilman lähdekoodia voi modifioitua ohjelmistoa jakaa, jos:  
-Koodi on edelleen saatavilla Vim-ylläpitäjälle  
-"You keep the changes for at least three years after last distributing the corresponding modified Vim.  When the maintainer or someone who you distributed the modified Vim to asks you (in any way) for the changes within this period, you must make them available to him."  
-Yhteystietojen on oltava voimassa vähintään kolme vuotta jakelun aloittamisestea  
e) Silloin kun GPL-lisenssi koskee muutoksia, saa modifioitua ohjelmistoa jaella GPL2-lisenssillä tai uudemmalla versiolla  
3. Käyttäjälle tulee tarjota vähintään :version-komennolla tieto, että ohjelmistoa on muokattu  
4. Muokkaajan yhteystietoja ei saa muokata tai poistaa  
  
## e)Käyttämäni ohjelmat

**Yleisimmät käyttämäni ohjelmat ovat:**  
-Eclipse  
-Git  
-VSCode  
-Blender  
-Steam  
-Firefox  
-Drive for desktop  
-Office  
-Polar Flow  
-Teams  
-Zoom  
  
Näistä miltei kaikki ovat suoraan saatavilla Linuxille. Steam ja sen tarjoamat pelit ovat suurin erottava tekijä Windows- ja Linux-ympäristössä. Steam sellaisenaan löytyy myös Linuxille, mutta edelleen pitää paikkansa, että Windows on ylivoimaisesti paras pelialusta. Polar Flow on näistä ohjelmistoista ainoa, joka ei ole suoraan saatavilla Linuxille.  