# **Harjoitus 2**

Harjoitustyön tehtävänantona käytettiin Karvisen kotisivuilta löytyvää [h2-kohtaa](https://terokarvinen.com/2021/linux-palvelimet-ict4tn021-3018/#h2)

**Harjoituksen laitekokoonpano**  
*Järjestelmänä Win 11 + VirtualBox 6.0*  
  
*Koneen perustiedot:*  
*Suoritin: AMD Ryzen 9 5900HS 8-ytiminen 3,1 - 4,5 GHz, 16 Mt välimuisti*  
*Muisti: 16 Gt LPDDR4X*  
*Näytönohjain: NVIDIA GeForce RTX 3050 Ti 4 Gt GDDR6*  
*Kiintolevy: 512 Gt M.2 2230 NVMe PCIe 3.0 SSD*  

## CLI

### Z) Lue ja tiivistä
*Lähdeartikkeli [Karvinen 2020: Command Line Basics Revisited](https://terokarvinen.com/2020/command-line-basics-revisited/])*  

Komentokehotteen opetteleminen on hyödyllistä, sillä se on ollut olemassa jo kauan ennen nykyaikaisia GUI-järjestelmiä. Samat komennot ovat olleet käytössä vuosikymmeniä, ja tulevat olemaan käytössä vuosikymmeniä, sillä ne ovat tehokas tapa saada asioita tehtyä. GUI tarkoittaa graafista käyttäjäympäristöä.  

**Oleellisia komentoja**  
  
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
man KOMENTO = näytä KOMENNON manuaali  
KOMENTO -h tai --help = KOMENNON lyhyempi help-tiedosto  

Tabulaattorilla täydennetään komentoja ja hakemistopolkuja. Tabulaattorin tuplapainalluksella järjestelmä näyttää vaihtoehdot, joista valita.  

**Tärkeitä hakemistoja**  

Linuxissa kaikki asiat ovat hakemistoissa.

|Hakemisto|Käyttötarkoitus|Huom.|
|---------:|:---------------|:----|
|/|Tämä on juurihakemisto, kaikki sijaitsee juurihakemiston alla||
|/home|Käyttäjien kotihakemistot||
|/home/kalle|Käyttäjän kalle hakemisto|Vain tämä käyttäjä voi tallentaa ko. hakemistoon|
|/etc|Järjestelmäasetukset|Asetukset ovat selkokielisissä tekstitiedostoissa|
|/media|irrotettava levytila|Esim. muistitikku|
|/var/log|lokitiedostot||
  
**Admin-komennot**  

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

**YCombinator Hacker News**  

Lähdeartikkeli: https://hub.github.com/

* Artikkelissa neuvotaan miten Githubia voi käyttää suoraan komentokehotteesta hub-ohjelmalla
* Käytän Git:iä hyvin alkeellisesti, eikä minulle intuitiivisesti aukea työkalun tuottama arvo
* Kommenteista tulkitsen, että kyseessä on niche-tuote, joka helpottaa tiettyjä operaatioita
 
### A) FHS

Aloitin tehtävän tekemisen 10.00 ja lopetin sen taukojen jälkeen 17.00.

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

/etc-hakemistossa löytyvät kaikki järjestelmän asetukset. 

![3. Kuva: /etc-hakemisto](/pics/harjoitus_2/3.png)  
*listasin sisällön ls:n avulla ja less-parametrillä, koska alirakenne ei mahtunut yhdelle näytölle.*  

Valitsin tarkasteltavaksi hostnamen. Se näyttää sisältää käytössä olevan hostnamen.  
  
![4. Kuva: hostname-tiedosto](/pics/harjoitus_2/4.png)  
*Kokeilin tiedoston kutsumista pelkästään hostnamella ja cat-käskyn kautta - lopputulos oli sama.*  

**/media**  

Media-kansiossa ei ollut mitään sisältöä, koska koneeseeni ei ollut yhdistetty ulkoisia tallennusmedioita.  

![5. Kuva: /media-kansio](/pics/harjoitus_2/5.png)  
*tarkistin pwd-komennolla olevani oikeassa kansiossa.*  
  
**/var/log**  
/var/log-kansiosta löytyvät kaikki lokitiedostot. Päätin tarkastella syslog-tiedostoa. Nimensä perusteella oletin sen olevan järjestelmäloki.  
  
![6. Kuva: syslog](/pics/harjoitus_2/6.png)  
*Tiedoston tarkasteleminen ei onnistunut ilman sudo:a*  

![7. Kuva: syslog](/pics/harjoitus_2/7.png)  
*sudon avulla listaus avautui*  

Tiedoston rivit eivät tarkoittaneet minulle juuri mitään, sillä ymmärrykseni ei riittänyt. Lokista löytyi ainakin muistiosoitteita, laitteita ja ladattuja tiedostoja.  

### My CLI  
  
Asennettavat ohjelmat: wget, micro & Git.

Halusin kokeilla nettipankin käyttämistä komentoriviltä, tämän raportin kirjoittamista TUI-käyttöliittymällä ja raportin tallentamista repositorioon Gitillä, jotta raportista tulisi sopivan metamainen. Gitin oikean paketin selvitin [githubista](https://github.com/git-guides/install-git), koska komentokehotteesta sitä ei helposti saanut kaivettua.

Olin käyttänyt Git:iä aikaisemmin Windowsin komentokehotteesta, joten täysin vierasta se ei minulle ollut.

![8. Kuva: asennusta](/pics/harjoitus_2/8.png)    
Asensin kaikki ohjelmat kerralla käyttämällä komentoa:  
*sudo apt-get install -y wget micro git-all*  

Yritin ottaa yhteyden Osuuspankin nettipankkiin. Tässä vaiheessa minulle selvisi, että wget ei toimi tähän tarkoitukseen, joten googlasin ja asensin Lynxin komennolla:  
*sudo apt-get install -y lynx*  

ctrl + g-kombolla pääsin syöttämään osoitteen, johon syötin pankkini nettisivujen osoitteen. Lynx kyseli evästeasetuksia ja vastasin niihin.  


  




   

    ### b) My CLI. Keksi jokin asia, jota haluaisit tehdä komentokehotteessa. Etsi ja asenna komentokehotteen paketinhallinnasta ohjelmat, joilla asian voi ratkaista. Asenna ainakin kolme itsellesi uutta komentorivillä (command line interface, CLI) tai tekstitilassa (text user interface, TUI) toimivaa ohjelmaa. Näytä, miten kuvitteellista ongelmaa voi ratkoa näillä ohjelmilla. Voit valita jonkin helpon tai yksinkertaistetun esimerkin.

    ### c) Tukki. Aiheuta lokiin kaksi eri tapahtumaa: yksi esimerkki onnistuneesta ja yksi esimerkki epäonnistuneesta tai kielletystä toimenpiteestä. Analysoi rivit yksityiskohtaisesti.

    ### d) The Friendly M. Näytä 2-3 kuvaavaa esimerkkiä grep-komennon käytöstä. Ohjeita löytyy 'man grep' ja tietysti verkosta.

    ### e) Pwnkit. Päivitä kaikki Linux-ohjelmat ja asenna tietoturvapäivitykset.

    ### y) cdlspwd! Opettele tärkeimmät komennot ulkoa ja harjoittele suurella määrällä kokeiluja. Opeteltavat komennot ovat artikkelissa Karvinen 2020: Command Line Basics Revisited (tätä y-alakohtaa ei tarvitse raportoida lainkaan)

    ### Bonus: Recursive. Pystytkö etsimään kaikki rivit, joilla lukee Tero isolla tai pienellä, kun tiedostoja on sisäkkäisissä kansioissa? (Eli tutkimaan jonkin kansion kaikkine alihakemistoineen)

    ### g) Sshecrets. Vaikeampi vapaaehtoinen bonuskohta, ei ole opetettu vielä: Asenna SSH-demoni. Kokeile omalla ssh-palvelimellasi jotain seuraavista: ssh-copy-id, sshfs, scp tai git. (Helpoin lienee scp: ‘scp foo.txt tero@example.com:’)



