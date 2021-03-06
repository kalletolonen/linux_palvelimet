# **Harjoitus 2**

Harjoitustyön tehtävänantona käytettiin Karvisen kotisivuilta löytyvää [h2-kohtaa](https://terokarvinen.com/2021/linux-palvelimet-ict4tn021-3018/#h2)

**Harjoituksen laitekokoonpano**  
*Järjestelmänä Win 11 + VirtualBox 6.0*  
  
*Koneen perustiedot:*  
*Suoritin: AMD Ryzen 9 5900HS 8-ytiminen 3,1 - 4,5 GHz, 16 Mt välimuisti*  
*Muisti: 16 Gt LPDDR4X*  
*Näytönohjain: NVIDIA GeForce RTX 3050 Ti 4 Gt GDDR6*  
*Kiintolevy: 512 Gt M.2 2230 NVMe PCIe 3.0 SSD*  

# CLI

## Z) Lue ja tiivistä
*Lähdeartikkeli [Karvinen 2020: Command Line Basics Revisited](https://terokarvinen.com/2020/command-line-basics-revisited/])*  

Komentokehotteen opetteleminen on hyödyllistä, sillä se on ollut olemassa jo kauan ennen nykyaikaisia GUI-järjestelmiä. Samat komennot ovat olleet käytössä vuosikymmeniä, ja tulevat olemaan käytössä vuosikymmeniä, sillä ne ovat tehokas tapa saada asioita tehtyä. GUI tarkoittaa graafista käyttäjäympäristöä.  

## **Oleellisia komentoja**  
  
| Komento   |      Käyttötarkoitus      |  Huom. |
|----------:|:-------------|:------|
| pwd |  nykyinen työhakemisto |  |
| ls |    listaa hakemiston sisällön   |    |
| cd HAKEMISTONNIMI | hakemiston vaihtaminen |     |
|less TIEDOSTONNIMI|tiedoston sisällön tulostaminen näytölle||
|nano|miltei jokaisesta jakelusta löytyvä tekstieditori|nano UUSITIEDOSTO.TXT luo UUSITIEDOSTO.TXT:n|
|mkdir HAKEMISTONNIMI|uuden hakemiston luominen||
|mv PARAMETRI1 PARAMETRI2|hakemiston/tiedoston siirtäminen tai nimeäminen uudelleen  |komennolla voi myös helposti ylikirjoittaa tiedoston, mikäli molemmat parametrit ovat olemassaolevia tiedostoja!|
|cp -r LÄHDE KOHDE|kopioidaan tiedosto kohteeseen|mikäli lähde on kansio, kopioidaan myös kansion sisältö|
|rmdir HAKEMISTO|poista tyhjä hakemisto||
|rm TIEDOSTO|poistaa tiedoston||
|rm -r KANSIO|poistaa kansion sisältöineen||
    
Komentoja syöttäessä on hyvä muistaa, että Linux ei juuri jakele varoituksia käskyjä toteuttaessaan.  
  
	SSH kalle@serveri.com = ottaa yhteyden serveri.com-serveriin käyttäjätunnuksella kalle  
	exit = palaa omalle tietokoneelle  
	scp -r KANSIO kalle@serveri.com:KOHDEKANSIO/ = kopioi kansio omalta koneelta kohdekoneelle  
	man KOMENTO = näyttää KOMENNON manuaali  
	KOMENTO -h tai --help = KOMENNON lyhyempi help-tiedosto  

Tabulaattorilla täydennetään komentoja ja hakemistopolkuja. Tabulaattorin tuplapainalluksella järjestelmä näyttää vaihtoehdot, joista valita.  

## **Tärkeitä hakemistoja**  

Linuxissa kaikki asiat ovat hakemistoissa.

|Hakemisto|Käyttötarkoitus|Huom.|
|---------:|:---------------|:----|
|/|Tämä on juurihakemisto, kaikki sijaitsee juurihakemiston alla||
|/home|Käyttäjien kotihakemistot||
|/home/kalle|Käyttäjän kalle hakemisto|Vain tämä käyttäjä voi tallentaa ko. hakemistoon|
|/etc|Järjestelmäasetukset|Asetukset ovat selkokielisissä tekstitiedostoissa|
|/media|irrotettava levytila|Esim. muistitikku|
|/var/log|lokitiedostot||
  
## **Admin-komennot**  

Linuxissa on periaate, jossa operoidaan aina pienimmillä mahdollisilla käyttäjäoikeuksilla. Korkeampia käyttäjäoikeuksia tarvitaan järjestelmään vaikuttavien komentojen yhteydessä, esimerkiksi silloin, kun asennetaan uusia ohjelmia.  
  
Paketinhallinnan avulla uusien ohjelmien asentaminen on jouhevaa.  
  
	*sudo apt-get update*  
	Päivittää saatavissa olevien pakettien listan.  
  
	*apt-cache search hakusana*  
	Etsii saatavilla paketteja hakusanalla.  
  
	*sudo apt-get -y install paketinnimi*  
	Asentaa paketin ja vastaa kyllä kaikkiin kysymyksiin asennusvaiheessa.  
  
	*dpkg --listfiles paketinnimi*  
	Etsii tiedostoja hakusanalla  
  
	*sudo apt-get purge ohjelma*  
	Poistaa asennuksen ja siihen liittyvät asetukset  
  
	*sudo apt-get -y install blender nethack-console pico*  
	apt-get -komentoon voi myös ketjuttaa monien ohjelmien asennukset.

## **YCombinator Hacker News**  

Lähdeartikkeli: https://hub.github.com/

* Artikkelissa neuvotaan miten Githubia voi käyttää suoraan komentokehotteesta hub-ohjelmalla
* Käytän Git:iä hyvin alkeellisesti, eikä minulle intuitiivisesti aukea työkalun tuottama arvo
* [Kommenteista](https://news.ycombinator.com/item?id=20372770) tulkitsen, että kyseessä on niche-tuote, joka helpottaa tiettyjä operaatioita
 
## A) FHS

Aloitin tehtävän tekemisen 10.00 ja lopetin sen taukojen jälkeen 15.25.

Kaikkien tehtävässä olevien hakemistojen sisällön listaamiseen käytin ls-komentoa.

**/**  
/ on juurihakemisto, sillä sijaitsee kaikki mitä järjestelmä pitää sisällään.
  
![1. Kuva: root](/pics/harjoitus_2/1.png)  
*Kuvassa kaikki kansiot, jokainen niistä on tärkeä.*  

**/home/ ja /home/kallet**  
/home/ on kirjautuneen käyttäjän kotihakemisto, tänne käyttäjän alakansioon tallentuvat kaikki ko. käyttäjän tiedostot. 
  
![2. Kuva: kissa.txt](/pics/harjoitus_2/2.png)  
*Kuvassa kallet-käyttäjän kissa.txt-tiedoston sisältö cat-komennolla iteroituna.*  
  
**/etc/**  
/etc-hakemistossa löytyivät kaikki järjestelmän asetukset. 

![3. Kuva: /etc-hakemisto](/pics/harjoitus_2/3.png)  
*listasin sisällön ls:n avulla ja less-parametrillä, koska alirakenne ei mahtunut yhdelle näytölle.*  

Valitsin tarkasteltavaksi hostnamen. Se näytti käytössä olleen hostnamen.  
  
![4. Kuva: hostname-tiedosto](/pics/harjoitus_2/4.png)  
*Kokeilin tiedoston kutsumista pelkästään hostnamella ja cat-käskyn kautta - lopputulos oli sama.*  

**/media**  
Media-kansiossa ei ollut mitään sisältöä, koska koneeseeni ei ollut yhdistetty ulkoisia tallennusmedioita.  

![5. Kuva: /media-kansio](/pics/harjoitus_2/5.png)  
*tarkistin pwd-komennolla olevani oikeassa kansiossa.*  
  
**/var/log**  
/var/log-kansiosta löytyivät kaikki lokitiedostot. Päätin tarkastella syslog-tiedostoa. Nimensä perusteella oletin sen olevan järjestelmäloki.  
  
![6. Kuva: syslog](/pics/harjoitus_2/6.png)  
*Tiedoston tarkasteleminen ei onnistunut ilman sudo:a*  

![7. Kuva: syslog](/pics/harjoitus_2/7.png)  
*sudon avulla listaus avautui*  

Tiedoston rivit eivät tarkoittaneet minulle juuri mitään, sillä ymmärrykseni ei riittänyt. Lokista löytyi ainakin muistiosoitteita, laitteita ja ladattuja tiedostoja.  

## My CLI  
  
Asennettavat ohjelmat: wget, micro & Git.

Halusin kokeilla nettipankin käyttämistä komentoriviltä, tämän raportin kirjoittamista TUI-käyttöliittymällä ja raportin tallentamista repositorioon Gitillä, jotta raportista tulisi sopivan metamainen. Gitin oikean paketin selvitin [githubista](https://github.com/git-guides/install-git), koska komentokehotteesta sitä ei helposti saanut kaivettua.

Olin käyttänyt Git:iä aikaisemmin Windowsin komentokehotteesta, joten täysin vierasta se ei minulle ollut.

![8. Kuva: asennusta](/pics/harjoitus_2/8.png)    
Asensin kaikki ohjelmat kerralla käyttämällä komentoa:  
*sudo apt-get install -y wget micro git-all*  

Yritin ottaa yhteyden Osuuspankin nettipankkiin. Tässä vaiheessa minulle selvisi, että wget ei toimi tähän tarkoitukseen, joten googlasin ja asensin Lynxin komennolla:  
*sudo apt-get install -y lynx*  

ctrl + g-kombolla pääsin syöttämään osoitteen, johon syötin pankkini nettisivujen osoitteen. Lynx kyseli evästeasetuksia ja vastasin niihin myöntävästi.  
![9. Kuva: op.fi](/pics/harjoitus_2/9.png)    
*Sisäänkirjautuminen ei kuitenkaan onnistunut, epäilen että kyseessä oli Lynxin JavaScriptin puute, sillä OP:n sivuston napit käyttävät JS:ä. Nettipankin käyttäminen ei siis onnistunut komentokehotteesta.*  
  
Seuraavaksi oli vuorossa tämän raportin kirjoittaminen microlla, joten googlasin ohjeita miten repositorion [saa ladattua koneelle](https://github.com/git-guides/git-pull). Lisähaun perusteella tähän tarvittiin myös [git clone-komentoa](https://github.com/git-guides/git-init)  
![10. Kuva: Git-kansio](/pics/harjoitus_2/10.png)  
*loin kotihakemistooni uuden kansion raporttia varten mkdir-komennolla*  

Tein vielä viimeisen push-komennon Windowsin komentokehotteessa, jotta saisin pull-komennolla vedettyä Githubista viimeisimmän version repositoriosta.  
![11. Git-clone](/pics/harjoitus_2/11.png)  
*kloonatun repositorion sisältö virtuaalikoneessa*  

Kloonasin etärepositorion virtuaalikoneeseeni komennolla:  
*git clone osoite*  
  
Sitten kirjoitin muokkauksia raporttiini microlla avaamalla sen komennolla:  
*git micro tehtava_2.md*  
  
![12. Git-clone](/pics/harjoitus_2/12.png)  
*Tässä vaiheessa olin vielä optimistinen siitä, että onnistuisin lataamaan muutokset näyttökaappauksia lukuunottamatta VirtualBoxin sisältä repoon*  

![13. Git-status](/pics/harjoitus_2/13.png)  
*Tarkistin statuksen*  

![14. Git-status](/pics/harjoitus_2/14.png)  
*Lisäsin muutokset commit-viestiin*  
  
Meni kuitenkin vaikeaksi, kun Github alkoi vaatimaan jotain tunnistetietoja, joten kirjoitin saman asian uudelleen sellaisessa ympäristössä, jota osaan käyttää. Ongelmaan löytynee ratkaisu netistä, sillä uskon monien tekevän kehitystyötä usealla eri koneella, sillä sitä varten koko Git on kehitetty.  
  
Jatkoin tehtävien tekemistä myöhemmin illalla, aloitin työt klo 20.24.

## C) Tukki

Tätä tehtävää tehdessäni tulin samalla selvittäneeksi miten voisin saada VirtualBoxin ja oman koneen välillä leikepöydän toimimaan. Se tapahtui valitsemalla virtuaalikoneen asetuksista jaettu leikepöytä. Tai niin luulin, kun kirjoitin tätä raporttia samalla tehdessäni harjoitusta.  
  
*Settings -> General -> Advanced -> Shared Clipboard*  
  
Totuus kuitenkin paljastui ja [näillä ohjeilla](https://www.howtogeek.com/187535/how-to-copy-and-paste-between-a-virtualbox-host-machine-and-a-guest-machine/) ei leikepöytä alkanut toimimaan.  

Kokeilen vielä toisia [ohjeita](https://www.pc-freak.net/blog/copy-paste-virtualbox-enable-linux-host-guest-virtual-machine/), ja sain aikaiseksi virheilmoituksen VirtualBoxissa.  

	Unable to insert the virtual optical disk C:\Program Files\Oracle\VirtualBox\VBoxGuestAdditions.iso into the machine virtual_debian.
  
	Could not mount the media/drive 'C:\Program Files\Oracle\VirtualBox/VBoxGuestAdditions.iso' (VERR_PDM_MEDIA_LOCKED).

	Result Code: E_FAIL (0x80004005)  
	Component: ConsoleWrap  
	Interface: IConsole {872da645-4a9b-1727-bee2-5585105b9eed}  
	Callee: IMachine {5047460a-265d-4538-b23e-ddba5fb84976}  

Jatkoin matkaa ja analysoin varsinaisen tehtävän lokimerkinnät suoraan kuvasta.  
  
![18. Git-status](/pics/harjoitus_2/18.png)  
*Lokiin tallentui epäonnistunut salasanan syöttäminen*  

Ensimmäisenä kuvassa näkyivät päivämäärä ja kellonaika, sitten hostname (eli se tietokone, jota ilmoitus koskee), seuraavaksi käytetty komento (sudo) ja lopulta käyttäjätunnus. Virheilmoituksena annettiin 3 väärää salasanayritystä. TTY=pts/0:n merkitys ei auennut intuitiivisesti, joten selvitin sen [googlaamalla](https://www.golinuxcloud.com/difference-between-pty-vs-tty-vs-pts-linux/) (se liittyi siihen, että käsky on syötetty terminaalista).  PWD tulostaa virheilmoituksen hetken työhakemiston, USER kertoo käyttäjän ja COMMAND syötetyn komennon. Lokitiedosto siis kertoo siitä, mitä on yritetty tehdä, milloin ja kenen toimesta.  
  
Lopetin työt 21.20 ja laitoin tehtävän vielä latautumaan Githubiin.  

Aloitin harjoituksen täyttämisen seuraavana päivänä 12.30.  
  
![19. Git-status](/pics/harjoitus_2/19.png)  
*Lokiin tallentui sudo apt-get update-käskyn ajaminen*  
  
Onnistnut lokimerkintä oli sisältönsä puolesta ylläolevan kaltainen, paitsi että siinä ei ollut merkintää epäonnistumisesta. Tämäkin merkintä kertoi siitä, että kuka on tehnyt mitä, millä ja milloin, sekä mahdollisesti seurasi. Huomion arvoista oli myös se, että korostetun rivin alapuoliset rivit liittyivät komentoon, sillä siinä avattiin sessio (jossa suorittiin käsky?) sudo-valtuuksilla ja sen jälkeen sessio suljettiin.  
  
## D) The Friendly M.  
  
Grep on [etsintätyökalu](https://www.cyberciti.biz/faq/howto-use-grep-command-in-linux-unix/#Use_grep_to_search_a_file). 

Grepin avulla voi:  
1. Etsiä tekstiä tiedostojen sisältä 
![20. Git-status](/pics/harjoitus_2/20.png)  
*grep -r "kissa" /home/ | less*-komento palautti listauksen, jossa oli ruutu kerrallaan kaikki /home/-hakemiston ja sen alikansioiden kissa-sanan sisältävät rivit tiedostoista.    
  
2. Suodattaa laitelistauksista haluamaansa tietoa  
![21. Git-status](/pics/harjoitus_2/21.png)  
*Pelkän prosessorimallin sisältävä listaus laadittiin komentoyhdistelmällä.*  
  
3. Etsiä ja suodattaa laitelistauksesta kiintolevyt  
![22. Git-status](/pics/harjoitus_2/22.png)  
*dmesg | egrep "(s|h)d[a-z]"*-komento etsi dmesg-hausta grepin avulla.  
  
Regex tarkoittaa standardimallin ilmaisuja, joilla on mahdollista suodattaa merkkijonoja. Tässä esimerkissä listattiin laitteet, jotka alkoivat a:lla tai h:lla, joiden keskimmäinen kirjain on d ja jotka päättyvät mihin tahansa aakkoseen a:n ja z:n välillä.  
  
[regex-tarkenne](https://en.wikipedia.org/wiki/Regular_expression)  
  
## E) Pwnkit  
  
Ajoin järjestelmäpäivitykset seuraavilla komennoilla:  
*sudo apt-get update*  
*sudo apt-get system-upgrade*  
![16. Järjestelmäpäivitys](/pics/harjoitus_2/16.png)  
*Järjestelmäni oli jo ajantasainen, joten lisäpäivityksiä ei asennettu.*  

## Bonus: Recursive  

Etsin kaikki kissa-sanan sisältävät rivit etsitään *grep -r -i "kissa" /home/*-komennolla. Komennon -i-parametri tarkoittaa kirjainkoon jättämistä huomioimatta.  
  
Lopetin harjoituksen tekimisen 13.49.  
  
*Tekijä: Kalle Tolonen*


