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

Tehtävän lähteenä käytin tuntimuistiinpanojani ja Karvisen [artikkelia](https://terokarvinen.com/2022/django-instant-crm-tutorial/).  
  
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

Komento haki ja asensi koneelle virtaulenvin, jonka avulla voidaan luoda eristettyjä Python-ympäristöjä.  
  
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
  
Asensin pwgen-salasanageneraattorin ja loin sen avulla superuserilleni tietoturvallisen salasanan.
  
**superuserin luominen**  
*sudo apt-get install pwgen*  
*pwgen -s 30 1*  
*./manage.py createsuperuser*  
   
![Kuva 13.](pics/harjoitus_5/13.png)  
*Käyttäjän luominen onnistui*  
   
  Tämän jälkeen käynnistin testiserverin:  
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
  
Ensin tiedostoon tuotiin models django.db:stä ja sitten luotiin luokka Receipt, joka peri models.Modelin ominaisuudet. Tarkoituksenani on pitkässä juoksussa luoda maksujen jakamiseen ja talouden seuraamiseen & analysointiin sopiva työkalu. Muutin myös Micron oletusasetuksen tabulaattorien automaattisesta muuttamisesta välilyönneiksi. Pythonissa ohjelmalohkojen hierarkiaa ilmaistaa vain sisennyksillä ja siten on äärimmäisen tärkeää, että sisennykset ovat oikein.  

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
  
Käyttökelpoisuuden parantamiseksi lisäsin models.py-tiedostoon päivämäärän:  
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
Ajoin makemigrationin ja pääsin päättämään mitä lomakkeeseen syötetään oletusarvona.  

![Kuva 36.](pics/harjoitus_5/36.png)  
*Lopputuloksena objekteillani oli nyt kolme ominaisuutta (shopName, date & amount)*  
  
Lopuksi muokkasin models.py:tä siten, että objektilistaus näyttäisi mukavammalta admin-konsolissa:  
*micro settle/models.py*  
  
![Kuva 37.](pics/harjoitus_5/37.png)  
*Muokattu models.py*  
  
![Kuva 38.](pics/harjoitus_5/38.png)  
*Päivitetty admin-näkymä*  
  
Yritin saada riville tulostumaan myös hinnan, mutta sitten objektin muokkausta yrittäessä sain virheilmoituksen tuplesta (shopName, amount ja date lienevät tuple-muotoon tallennettuja) ja objektia kutsuttaessa saatiin aikaiseksi virheilmoitus.  
  
![Kuva 39.](pics/harjoitus_5/39.png)  
*Tähän asti sain returnilla palautettua objektista haluamani tiedot*  
  
![Kuva 40.](pics/harjoitus_5/40.png)  
*Pyysin objektia palvelimelta ja tuloksena oli virheilmoitus*  
  
Lopetin työt n. 22.15 taukojen jälkeen.  
    
Aloitin työt n. 10.00.  
    
Päätin testata toimiiko ominaisuuksien iterointi, jos kaikki attribuutit ovat samaa datatyyppiä ja loin Testing-luokan muokkaamalla models.py-tiedostoa.  
  
![Kuva 41.](pics/harjoitus_5/41.png)  
*Uusi models.py:n sisältö*  
  
Rekisteröin muutokset tietokantaan ja suoritin ne komennoilla:  
*./manage.py makemigrations*  
*./manage.py migrate*  
  
Tämän lisäksi piti vielä muokata admin.py-tiedostoa komennolla:  
*micro settle/admin.py*  
  
![Kuva 42.](pics/harjoitus_5/42.png)  
*admin.py:n uusi sisältö*  
  
![Kuva 43.](pics/harjoitus_5/43.png)  
*admin-konsolin näkymässä pyytämäni tiedot tulostuivat*  
  
![Kuva 44.](pics/harjoitus_5/44.png)  
*Koin saman virheilmoituksen myös samantyyppisiä ominaisuuksia sisältävällä objektilla*  
  
Kokeilin vielä __str__:n vaihtamista __init__:iin.  
  
![Kuva 45.](pics/harjoitus_5/45.png)  
*models.py:n uusi sisältö*  
  
![Kuva 46.](pics/harjoitus_5/46.png)  
*En ollut yhtään lähempänä ongelmani ratkaisua*  
  
Ymmärräkseni Pythonista ei riittänyt ongelman ratkaisuun, joten poistin Testing-luokan ja viittaukset siihen admin.py:stä ja tein tietokantamigraation uudestaan palatakseni alkutilanteeseen.  
  
Päivitän artikkelia, kun saan ongelman ratkaistua.  
  
## b) Prod. Make a production style Django install. Use Apache and mod_wsgi, disable DEBUG.  
  
Aloitin tuotantotyyppisen asennuksen tekemisen käyttämällä työohjeenani [Karvisen artikkelia](https://terokarvinen.com/2022/deploy-django/) ja tuntimuistiinpanojani.  
  
Päätin testata taitojani suoraan julkiseen nettiin tapahtuvalla asennuksella, joten aloitin työt ottamalla ssh-yhteyden palvelimeeni komennolla:  
*ssh kayttajatunnus@domain*  
  
Asensin Microon bash-completion -lisäosan ja määritin sen vakioeditoriksi:  
*sudo apt-get install -y micro bash-completion*  
*export EDITOR=micro*  
  
![Kuva 47.](pics/harjoitus_5/47.png)  
*Edellisen tehtävän jäljiltä minulla oli käyttäjänä tehty kotisivu*  
  
Poistin nykyisen public_html-kansion, joka sijaitsi kotihakemistossani:  
*rm  -r public_html*  
  
Tämän jälkeen tein kotihakemistoon uuden kansion:  
*mkdir -p publicwsgi/splitlyze/static/*  
  
mkdir-komennon p-parametri luo alikansiot samalla kerralla.  
  
Tämän jälkeen tein index.html tiedoston sisältöineen:  
*echo "Static test page" |tee publicwsgi/splitlyze/static/index.html*  
  
Seuraavaksi määrittelin VirtualHostin sijainnit http- ja https-liikenteelle:  
*sudoedit /etc/apache2/sites-available/splitlyze.conf*  
  
![Kuva 48.](pics/harjoitus_5/48.png)  
*splitlyze.conf-tiedoston sisältö*  
  
Kytkin konfiguraatiotestiä varten edellisen konfiguraation pois päältä ja uuden päälle:  
*sudo a2ensite splitlyze.conf*  
*sudo a2dissite 000-defaul.conf*  
  
Konfiguraatio testattiin komennolla:  
*/sbin/apache2ctl configtest*  

![Kuva 49.](pics/harjoitus_5/49.png)  
*Tuloksena oli virheilmoitus ssl-sertifikaatista ja muista asioista*  
  
Päätin ensin avata ssl-konfiguraatiotiedoston:  
*sudoedit /etc/apache2/sites-enabled/000-default-le-ssl.conf*  
  
Tämä tuotti tulokseksi virheilmoituksen:  
	sudoedit: /etc/apache2/sites-enabled/000-default-le-ssl.conf: editing symbolic links is not permitted  
  
Seuraavaksi otin kokeilun alle documentrootin korjaamisen splitlyzy.conf-tiedostoon:  
*sudoedit /etc/apache2/sites-available/splitlyze.conf* 
  
[Kuva 50.](pics/harjoitus_5/50.png)  
*splitlyze.conf-tiedoston uusi sisältö*  
  
Uusi yritys:  
*/sbin/apache2ctl configtest*   
  
Virheilmoitukset pysyivät samoina, enkä tiennyt miksi, joten päätin kokeilla mitä käy, jos käynnistän serverin uudestaan, sillä voin aina palata edelliseen tehtävään ja tehdä kaikki toimenpiteet uudestaan päästäkseni takaisin alkupisteeseen.  
  
Annoin komennon:  
*sudo systemctl restart apache2**  
  
[Kuva 51.](pics/harjoitus_5/51.png)  
*Demoni käynnistyi uudestaan mukisematta*  
  
[Kuva 52.](pics/harjoitus_5/52.png)  
*Domainin juurihakemistossa tuli ilmoitus puutteellisista oikeuksista*    

[Kuva 53.](pics/harjoitus_5/53.png)  
*käyttäjän kansiossa todettiin samaa*  
  
Sudoedit ei toiminut yllä ssl-konfiguraatiotiedoston muokkaamiseen, mutta microlla sne muokkaus onnistui:  
*sudo micro /etc/apache2/sites-enabled/000-default-le-ssl.conf*  
  
[Kuva 54.](pics/harjoitus_5/54.png)  
*Uusittu DocumentRoot-parametri*  
  
[Kuva 55.](pics/harjoitus_5/55.png)  
*Tällä kertaa konfiguraatiotesti lopetti herjaamisen DocumentRootista*  
  
Jäljelle jäänyt virheilmoitus liittynee ssl-sertifikaattiin ja sen korjaaminen ei ole oleellista tätä tehtävää varten. Päätin kuitenkin kokeilla CertBotin ajamista manuaalisesti sertifikaatin uudistamiseksi:  
*sudo certbot renew --dry-run*  
  
[Kuva 56.](pics/harjoitus_5/56.png)  
*Kaikki on ok*  
  
Uskon, että viimeinen virheilmoitus korjaantuu itsestään, kun sertifikaatti seuraavan kerran uudistaa itsensä automaattisesti.  
  
[Kuva 57.](pics/harjoitus_5/57.png)  
*Julkisessa netissä ssl-suojaamaton staattinen testisivu toimi oikein*  
  
**Virtuaaliympäristön asentaminen**  
  
Seuraavaksi oli aika asentaa virtuaaliympäristö:  
*sudo apt-get install -y virtualenv*  
  
Siirryin haluamaani kansioon:  
*cd publicwsgi/*  
  
Loin virtuaaliympäristön env-kansioon:  
*virtualenv -p python3 --system-site-packages env*  
  
	--system-site-packages sallii Python-pakettien käyttämisen virtuaaliympäristön ulkopuolelta.  
	-p python3 varmistaa, että käytössä on Pythonin oikea versio.  
Käynnistin virtuaaliympäristön ja tarkistin, että olen ympäristön sisällä:  
*source env/bin/activate*  
*which pip*  
  
[Kuva 58.](pics/harjoitus_5/58.png)  
*Olin oikeassa paikassa*  
  
Syötin requirements.txt-tiedostoon djangon:  
*micro requirements.txt*  

[Kuva 59.](pics/harjoitus_5/59.png)  
*requirements.txt:n sisältö*  
  
Asennus käynnistettiin ja todennettiin komennoilla:  
*pip install -r requirements.txt*  
*django-admin --version*  
  
[Kuva 60.](pics/harjoitus_5/60.png)  
*Django oli nyt todennetusti asennettu*  
  
**Projektin perustaminen**  

Perustin projektin Djangolla komennolla:  
*django-admin startproject splitlyze*  
  
[Kuva 61.](pics/harjoitus_5/61.png)  
*hakemistopolku oli jo olemassa, kun orjallisesti loin sen tehtävän alussa static-sivustoa varten*  
  
Poistin hakemiston sisältöineen komennolla:  
*rm -r splitlyze*  
  
Seuraavaksi editoin konfiguraatiotiedostoa:  
*sudoedit /etc/apache2/sites-available/splitlyze.conf*  
  
[Kuva 62.](pics/harjoitus_5/62.png)  
*Muokkasin [Karvisen pohjaan](https://terokarvinen.com/2022/deploy-django/) muuttujiin omat tietoni*  
  
Sitten asennettiin wsgi-modi Apacheen:  
*sudo apt-get install -y libapache2-mod-wsgi-py3*  
  
Tein tuhoamani static-hakemiston ja index.html-tiedoston uudestaan:  
*mkdir -p /home/kallet/publicwsgi/splitlyze/static*  
*echo "Static test page 2" |tee /home/kallet/publicwsgi/splitlyze/static/index.html*  
  
Ajoin testin konfiguraatiooni:  
*/sbin/apache2ctl configtest*  
  
[Kuva 63.](pics/harjoitus_5/63.png)  
*Konfiguraatio toimi niin kuin ylläkin, sama ssl-virheilmoitus oli edelleen olemassa*  
  
Käynnistin demonin uudestaan:  
*sudo systemctl restart apache2*  
  
Huomasin, että olin sössinyt jossain, sillä debugatessa muutin splitlyze.conf-hosteja takaisin aiemmin toimineisiin ja sain Apachen vakiosivun näkyviin.  

[Kuva 64.](pics/harjoitus_5/64.png)  
*Ei mennyt niin kuin piti*  
  
Päättelin, että jostain tuo sivu loihditann esiin ja se löytyikin /var/www/html -hakemistosta. Sitten päätin konfiguroida apachea uudestaan käyttämään oikeaa tiedostoa:  
*sudo a2dissite splitlyze.conf*  
*sudo a2dissite 000-default.conf*  
*sudo a2dissite 000-default-le-ssl.conf*  
*sudo a2ensite splitlyze.conf*  
  
*sudo systemctl restart apache2*  
  
[Kuva 65.](pics/harjoitus_5/65.png)  
*Edelleen apache2:n vakiosivu kummitteli*  
  
Päätin selvittää mitä konffitiedostoja Apache2 käytti ja totesin että helpoimmalla pääsen, kun asennan koko Apachen, virtualenvin ja sertifikaatit uudestaan.  

**Uusi alku**  
  
Aloitin poistamalla publicwsgi-kansion alihakemistoineen kotihakemistostani ja apachen [tehtävän 3](https://github.com/kalletolonen/linux_palvelimet/blob/main/tehtava3.md) ohjeiden mukaan:  
*rm -r publicwsgi*  
*sudo service apache2 stop*  
*sudo apt-get purge apache2 apache2-utils apache2.2-bin apache2-common*  
*sudo apt-get autoremove*  
*whereis apache2*  
  
Poistin kaikki apacheen viittaavat hakemistot ja tiedostot, jotka whereis löysi.  
  
[Kuva 66.](pics/harjoitus_5/66.png)  
*Demoni oli poistettu*  
  
Poistin myös virtualenvin komennolla:  
*sudo apt-get purge virtualenv*  
*whereis virtualenv*  
*sudo rm -r whereisin tarjoamat sijainnit*  
  
Hain päivitykset pakettilistaan:  
*sudo apt-get update*  
  
Asensin apache2-demonin:  
*sudo apt-get install -y apache2*  
  
Komento ilmoitti, että apache on edelleen asennettu, joten ajoin komennot:  
*sudo apt-get remove -y virtualenv*  
*sudo apt-get remove -y apache2*  
*sudo apt-get purge -y apache2*  
*sudo apt autoremove*  
  
[Kuva 67.](pics/harjoitus_5/67).png)  
*Viimein demoni oli oikeasti poistettu*  
  
Uusi asennus:  
*sudo apt-get install apache2*  
*sudo apt-get install virtualenv*  
  
Oletussivun korvaaminen oli seuraava askel:  
*echo "Tämä tuhosi oletussivun" |sudo tee /var/www/html/index.html*  
  
Lopetin työt n. 17.30 ja päätin palata aiheen pariin myöhemmin.  
  
Aloitin työt 18.44.  

Asensin virtualenvin, tein publicwsgi-kansion ja siirryin sinne:  
*sudo apt-get install -y virtualenv*  
*mkdir publicwsgi*  
*cd publicwsgi*  
  
Loin virtuaaliympäristön ja tarkistin sijainnin:  
*virtualenv -p python3 --system-site-packages env*  
*which pip*  
  
[Kuva 68.](pics/harjoitus_5/68.png)  
*Virtuaaliympäristö oli nyt luotu ja käytössä*  
  
Tein vaatimuslistan requirements.txt-tiedostoon:  
*micro requirements.txt*  
-vaatimukseksi syötettiin vain django  
  
Django asennettiin pip:llä:  
*pip install -r requirements.txt*  
  
Aloitin projektin:  
*django-admin startproject splitlyze*  
  
Kävin luomassa kansion staattiselle sisällölle ja sinne tiedoston:  
*mkdir splitlyze/static/*  
*echo "Tämä on staattinen sivu" |tee splitlyze/static/index.html*  
[Kuva 69.](pics/harjoitus_5/69.png)  
*Testisivu luotiin*  

Loin virtualhost-tiedoston ja aktivoin sen:  
*sudo micro /etc/apache2/sites-available/splitlyze.conf*  
  
````
	<VirtualHost *:80>
		Alias /static/ /home/tero/publicwsgi/teroco/static/
		<Directory /home/tero/publicwsgi/teroco/static/>
			Require all granted
		</Directory>
	</VirtualHost>
````  
  
*sudo a2ensite splitlyze.conf*  
*sudo a2dissite 000-default.conf*  
*/sbin/apache2ctl configtest*  
  
[Kuva 70.](pics/harjoitus_5/70.png)  
*Viimeinen komento aiheutti virheilmoituksen*  
  
Googlauksen perusteella ajoin komennon:  
*sudo apt install --reinstall apache2-bin*  
  
Epäilen että olin poistanut apache-demonin jotenkin väärin ja nyt järjestelmä ei ollut osannut asentaa sitä oikein.  
  
[Kuva 71.](pics/harjoitus_5/71.png)  
*Tällä kertaa configtest meni onnistuneesti läpi*  
  
Laitoin käyttäjähakemistot päälle:  
*sudo a2enmod userdir*  
  
[Kuva 73.](pics/harjoitus_5/73.png)  
*Pääsin julkisesta netistä selaamaan käyttäjän kotihakemistoa*  
  
Minut valtasi syvä epäusko ja päätin ajaa koko dropletin maantasalle ja tehdä uudestaan, sillä ongelmani johtuivat mahdollisesti väärin poistetuista tai asennetuista paketeista.  
  
**Sisyphos**  
  
Tuhosin serverin Digital Oceanissa ja tein sen uudestaan kuvaavalla hostnamella.  
  
[Tehtävässä 4](https://github.com/kalletolonen/linux_palvelimet/blob/main/tehtava4.md) on tarkemmin kuvattuna tämä luomis- ja yhdistämisprosessi, joten en kuvaile sitä tämän enempää.  
  
[Kuva 74.](pics/harjoitus_5/74.png)  
*Jatkoin töitä tabula rasa -tilanteesta, jossa minulla oli tyhjä droplet pilvessä ja vain ssh-yhteydet päällä palomuurista*  
  
````
$ sudo apt-get -y install micro bash-completion
$ export EDITOR=micro
````
  
Lopetin työt 19.59.