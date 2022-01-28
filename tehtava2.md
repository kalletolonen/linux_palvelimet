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

### z) Lue ja tiivistä
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
|/home/|Käyttäjien kotihakemistot||
|/home/kalle|Käyttäjän kalle hakemisto|Vain tämä käyttäjä voi tallentaa ko. hakemistoon|
|/etc|Järjestelmäasetukset|ASetukset ovat selkokielisissä tekstitiedostoissa|
|/media/|irrotettava levytila|Esim. muistitikku|
|/var/log/|lokitiedostot||
  
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


    ### a) FHS. Esittele kansiot, jotka on listattu "Command Line Basics Revisited" kappaleessa "Important directories". Näytä kuvaava esimerkki kunkin tärkeän kansion sisältämästä tiedostosta tai kansiosta. Jos kyseessä on tiedosto, näytä siitä kuvaava esimerkkirivi. Työskentele komentokehotteessa ja näytä komennot, joilla etsit esimerkit.

    ### b) My CLI. Keksi jokin asia, jota haluaisit tehdä komentokehotteessa. Etsi ja asenna komentokehotteen paketinhallinnasta ohjelmat, joilla asian voi ratkaista. Asenna ainakin kolme itsellesi uutta komentorivillä (command line interface, CLI) tai tekstitilassa (text user interface, TUI) toimivaa ohjelmaa. Näytä, miten kuvitteellista ongelmaa voi ratkoa näillä ohjelmilla. Voit valita jonkin helpon tai yksinkertaistetun esimerkin.

    ### c) Tukki. Aiheuta lokiin kaksi eri tapahtumaa: yksi esimerkki onnistuneesta ja yksi esimerkki epäonnistuneesta tai kielletystä toimenpiteestä. Analysoi rivit yksityiskohtaisesti.

    ### d) The Friendly M. Näytä 2-3 kuvaavaa esimerkkiä grep-komennon käytöstä. Ohjeita löytyy 'man grep' ja tietysti verkosta.

    ### e) Pwnkit. Päivitä kaikki Linux-ohjelmat ja asenna tietoturvapäivitykset.

    ### y) cdlspwd! Opettele tärkeimmät komennot ulkoa ja harjoittele suurella määrällä kokeiluja. Opeteltavat komennot ovat artikkelissa Karvinen 2020: Command Line Basics Revisited (tätä y-alakohtaa ei tarvitse raportoida lainkaan)

    ### Bonus: Recursive. Pystytkö etsimään kaikki rivit, joilla lukee Tero isolla tai pienellä, kun tiedostoja on sisäkkäisissä kansioissa? (Eli tutkimaan jonkin kansion kaikkine alihakemistoineen)

    ### g) Sshecrets. Vaikeampi vapaaehtoinen bonuskohta, ei ole opetettu vielä: Asenna SSH-demoni. Kokeile omalla ssh-palvelimellasi jotain seuraavista: ssh-copy-id, sshfs, scp tai git. (Helpoin lienee scp: ‘scp foo.txt tero@example.com:’)



