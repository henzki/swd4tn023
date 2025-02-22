# Kurssin kehitysympäristön asentaminen

**Kysy kohtaamistasi ongelmista rohkeasti Teamsissa keskustelukanavalla jo ennen ensimmäistä oppituntia.**

Ennen ensimmäistä oppituntia sinun tulee valmistella itsellesi toimiva unix-pohjainen ympäristö, jossa voit kehittää ja suorittaa jatkossa kurssilla kehittämiämme koodeja. 

Mikäli sinulla on jo valmiiksi hyvä Unix-pohjainen ympäristö, kuten macOS, tai olet kiinnostunut esimerkiksi [WSL2:n](https://docs.microsoft.com/en-us/windows/wsl/install), [Dockerin](https://www.docker.com/), [Raspberry Pin](https://www.raspberrypi.org/), [DigitalOceanin](https://www.digitalocean.com/github-students/), [AWS:n](https://aws.amazon.com/ec2/) tai [Azuren](https://azure.microsoft.com/en-us/services/virtual-machines/) käytöstä, voit hyvin käyttää myös niitä, mutta  emme voi luvata niihin käyttötukea.


## Windows + VirtualBox + Linux

Graafiseen käyttöliittymään tottuneille käyttäjille yksi miellyttävä tie Linuxiin tutustumiseksi on [Ubuntu](https://ubuntu.com/desktop)- tai [Xubuntu](https://xubuntu.org/)-käyttöjärjestelmä graafisella käyttöliittymällä. Ubuntu voidaan asentaa "virtuaalikoneena" Oraclen ilmaisen [VirtualBox](https://www.virtualbox.org/)-virtualisointiympäristön avulla.

Linux voidaan asentaa myös tietokoneen pääkäyttöjärjestelmäksi, "dual boot"-vaihtoehdolla nykyisen käyttöjärjestelmän rinnalle, tai erilliselle muistitikulle, mutta näitä vaihtoehtoja ei kurssin puolesta suositella niihin liittyvien riskien vuoksi.

Virtuaalikoneeseen tekemäsi asennukset eivät vaikuta tietokoneesi normaaliin käyttöön, ja voit tarvittaessa poistaa kaiken kurssilla asentamasi kerralla poistamalla virtuaalikoneen.

> *Using Linux in a virtual machine gives you the option to try Linux within Windows. This step-by-step guide shows you how to install Linux inside Windows using VirtualBox.*
>
> https://itsfoss.com/install-linux-in-virtualbox/

Hyviä ohjeita asennuksiin löytyy sekä YouTubesta että Googlesta. Toimiviksi havaittuja ohjeita ovat mm. video ["How to Install Ubuntu 20.04 LTS on VirtualBox in Windows 10"](https://www.youtube.com/watch?v=x5MhydijWmc) ja artikkeli ["Install Linux Inside Windows Using VirtualBox"](https://itsfoss.com/install-linux-in-virtualbox/). Ubuntun oma virtuaalikoneen asennusohje löytyy [Ubuntu.com:ista](https://ubuntu.com/tutorials/how-to-run-ubuntu-desktop-on-a-virtual-machine-using-virtualbox).

Haaga-Helian Linux-palvelimet kurssilla käytetään Debial-käyttöjärjestelmää VirtualBox-alustalla, mikä sopii hyvin myös tälle kurssille. Edellä mainittu Ubuntu itse asiassa perustuu juuri Debianiin. Asennusohjeet Debianin asentamiseksi löydät Tero Karvisen kotisivulta https://terokarvinen.com/2021/install-debian-on-virtualbox/.

Windows-käyttäjänä joudut mahdollisesti [kytkemään päälle Windowsin Hyper-V -ominaisuuden](https://docs.microsoft.com/en-us/virtualization/hyper-v-on-windows/quick-start/enable-hyper-v#enable-the-hyper-v-role-through-settings) tai [kytkemään virtualisoinnin päälle tietokoneesi BIOS-asetuksista](https://www.google.com/search?q=enable+virtualization+bios).

Mikäli virtuaalikoneen asennuksessa on ongelmia, pyritään pääsääntöisesti ratkaisemaan ne kurssin yhteisessä Teams-chatissa!


## VS Code Remote Development

Kurssilla hyödynnettävä VS Code -editori tukee "etäkehitystä" (remote development), jonka avulla on mahdollista luoda kevyehköjä Linux-pohjaisia kehitysympäristöjä. Myös tämä vaihtoehto voi olla toimiva ratkaisu erillisen Linux-asennuksen sijasta tai lisäksi. Lisätietoja löydät mm. [Visual Studio Code:n ohjeista](https://code.visualstudio.com/docs/remote/containers).


# Ohjelmien asentaminen

Kun olet saanut käyttöjärjestelmän käyttökuntoon, tarvitset vielä siihen joitakin erillisiä asennuksia, erityisesti Gitin, Node.js:n ja Pythonin. Lisäksi suosittelemme koodieditoriksi VS Codea, mutta saat käyttää myös muita editoreja.

Seuraavat kohdat käsittelevät tarvittavien ohjelmien asentamista erityisesti Ubuntu-ympäristössä.


## Pakettien asentaminen

Ubuntussa useat paketit ja ohjelmat asennetaan komentorivityökaluilla. Komentorivin saat auki Ubuntun valikosta nimellä "Terminal", tai näppäinyhdistelmällä `CTRL + ALT + T`.

Mikäli komentorivin käyttö tuottaa ongelmia, hyvä tutoriaali komentorivin käytöstä löytyy osoitteessa https://ubuntu.com/tutorials/command-line-for-beginners. Voit myös aina kysyä neuvoa kurssin opettajilta ja muilta opiskelijoilta kurssin Teams-kanavilla!


## APT (Advanced Package Tool)

Ubuntun asennustyökalu on nimeltään Advanced Package Tool eli APT:

> *APT eli Advanced Package Tool on Debian-projektin kehittämä työkalu Linux-käyttöjärjestelmän pakettienhallinnan helpottamiseen. Se huolehtii mm. asennettavien pakettien riippuvuussuhteista ja niiden päivittämisestä. Se hakee asennettavat paketit netistä. APT-nimitystä käytetään sekä paketinhallintakirjastosta (jota voi käyttää monen käyttöliittymän kautta) että sitä käyttävästä komentorivityökalusta.*
>
> Linux.fi-wiki, https://www.linux.fi/wiki/APT

APT:in avulla sovellusten asennus tapahtuu kirjoittamalla komento muodossa:

    apt install ohjelma

Koska ohjelmien asennus vaatii pääkäyttäjäoikeudet, ei normaalilla käyttäjätunnuksella voida suoraan tehdä asennuksia. Yksittäisiä komentoja saa suoritettua pääkäyttäjäoikeuksilla [`sudo`-komennon avulla](https://wiki.ubuntu-fi.org/Sudo). Käytännössä tulet siis tekemään asennukset seuraavasti:

    sudo apt install ohjelma


**Huom!** APT asentaa koneellesi suoritettavia ohjelmia, joiden kanssa tulee aina huomioida myös tietoturva. Pääsääntöisesti Ubuntun pakettivarastot ovat turvallisia, mutta uusien pakettivarastojen lisääminen saattaa aiheuttaa riskejä. Tällä kurssilla teemme asennuksia vain Ubuntun omista pakettivarastoista. Voit lukea aiheesta lisää artikkelista [Can I get a virus by using "sudo apt-get install"?](https://askubuntu.com/a/818022)


## Git-asennus

Kurssilla käytetään oppimateriaalin ja esimerkkikoodien jakelussa Git-versionhallintaa. Asenna itsellesi valmiiksi Git-työkalut:

```shell
sudo apt install git
```

Asennuksen jälkeen Gitille täytyy vielä kertoa sähköpostiosoite ja nimi, joita käytetään tehdessäsi committeja. Nämä tiedot tulevat esim. GitHubin kautta kaikkien saataville, voit itse valita käytätkö oikeaa nimeäsi ja oikeaa sähköpostiosoitettasi. [GitHub tarjoaa myös mahdollisuuden käyttää anonyymiä sähköpostiosoitetta.](https://docs.github.com/en/github/setting-up-and-managing-your-github-user-account/setting-your-commit-email-address)

```shell
$ git config --global user.email "you@example.com"
$ git config --global user.name "Your Name"
```

Lopuksi voit kloonata tämän repositorion itsellesi (vapaaehtoista):

```shell
git clone https://github.com/haagahelia/swd4tn023.git
```

**Huom!** Tehdessäsi kirjautumista vaativia operaatioita GitHubiin komentoriviltä, et voi tietoturvasyistä käyttää tunnistautumisessa käyttäjätunnusta ja salasanaa, vaan joudut luomaan itsellesi "personal access tokenin". Lue tarkempia ohjeita GitHubin ohjesivuilta: https://docs.github.com/articles/creating-a-personal-access-token-for-the-command-line. Access token ei ole välttämätön vielä tässä vaiheessa, mutta asia on hyvä huomioida tulevaisuudessa.

Jos et halua syöttää käyttäjätunnustasi ja kirjautumistunnustasi (personal access token) joka kerta tehdessäsi kirjautumista vaativia Git-operaatioita, voit asettaa Gitin pitämään kirjautumistietosi muistissa:

```shell
$ git config --global credential.helper cache
```

Yllä oleva komento pitää tiedot tilapäisessä muistissa, josta ne poistuvat automaattisesti myöhemmin. Vaihtoehtoisesti voit [kirjautua GitHubiin SSH-avaimilla](https://docs.github.com/en/authentication/connecting-to-github-with-ssh) tai asettaa Gitin [tallentamaan access tokenin tiedostoon](https://unix.stackexchange.com/questions/379272/storing-username-and-password-in-git), mitä emme suosittele.


## Node.js ja npm

Tulemme tällä kurssilla ohjelmoimaan JavaScriptillä, johon tarvitsemme Node.js-suoritusympäristön. Node-paketeille on lisäksi oma paketinhallintasovellus nimeltä **npm** (Node Package Manager). Nämä voidaan asentaa apt-komennoilla seuraavasti:

```shell
sudo apt install nodejs
sudo apt install npm
```

Halutessasi voit lisäksi konfiguroida npm:n siten, että et tarvitse pääkäyttäjäoikeuksia pakettien asentamiseen: https://github.com/sindresorhus/guides/blob/main/npm-global-without-sudo.md

**Huom!** NPM-paketit sisältävät suoritettavaa ohjelmakoodia, joten niiden kanssa tulee huomioida tietoturva, aivan kuten muidenkin suoritettavien ohjelmien kanssa. Tunnettujen ja laajasti käytettyjen pakettien käyttäminen voi olla turvallisempaa kuin heikommin tunnettujen tai vähäisessä käytössä olevien.


## PIP

APT-komennon lisäksi Linuxille on lukuisia muita pakettienhallintaohjelmia, joista useat ovat erikoistuneet jonkin tietyn ohjelmointikielen kirjastojen asentamiseen.

Python 3 tulee Ubuntussa valmiiksi asennettuna, mutta Python-kirjastojen asentamisessa tarvittavan `pip`-työkalun joudumme asentamaan itse:

> *pip is the package installer for Python. You can use pip to install packages from the Python Package Index and other indexes.*
> 
> https://pypi.org/project/pip/

`pip` voidaan asentaa edellä esitellyn `apt`:in ja `sudo`:n avulla seuraavasti:

```shell
sudo apt install python3-pip
```

## Visual Studio Code

Viimeisenä asennuksena suosittelemme asentamaan Visual Studio Code -kehitysympäristön. Se löytyy ilmaiseksi helpoiten Ubuntun ohjelmistokaupasta. Ohjelmistokaupan voit avata painamalla Windows-painiketta ja kirjoittamalla hakukenttään "Ubuntu Software". Etsi hakukentän avulla "Visual Studio Code" ja valitse "install".

Visual Studio Code voidaan asentaa Linuxiin myös [lukuisilla muilla tavoilla](https://code.visualstudio.com/docs/setup/linux).


### VS Coden laajennokset ja asetukset

Tulemme käyttämään VS Codessa ainakin seuraavia laajennoksia, jotka voit asentaa etukäteen tai tarpeen mukaan:

1. `Python`-tuki VS Codelle

    https://marketplace.visualstudio.com/items?itemName=ms-python.python

1. `Pylint` koodin tarkistus

     `pip3 install pylint`

1. `Rope` refaktorointi

     `pip3 install rope`

1. `autopep8` koodin muotoilu

    `pip3 install autopep8`

Huomaa, että pip-asennukset ovat käyttäjäkohtaisia, eli niitä ei tehdä `sudo`-komennon avulla.

Lisäksi suosittelemme muuttamaan VS Code:n asetuksista koodin automaattisen muotoilun päälle tallennettaessa ja liitettäessä koodia seuraavasti:

> Avaa "User settings". Etsi hakukentän avulla valinnat `Format on save` sekä `Format on paste` ja aseta rastit molempiin ruutuihin.

**Huom!** Python-paketit sisältävät suoritettavaa ohjelmakoodia, joten niiden kanssa tulee huomioida tietoturva, aivan kuten muidenkin suoritettavien ohjelmien kanssa. Paketteja ei kannata ladata tuntemattomista lähteistä. Tunnettujen ja laajasti käytettyjen pakettien käyttäminen voi myös olla turvallisempaa kuin heikommin tunnettujen tai vähäisessä käytössä olevien. Lisätietoa pip-pakettienhallinnan turvallisuudesta löydät esimerkiksi artikkelista ["Look before you pip"](https://www.ayrx.me/look-before-you-pip).


## Extra: Guest additions sekä leikepöydän käyttö

Perusasennuksen lisäksi suosittelemme sinua asentamaan VirtualBoxin "guest additions" -lisäosat virtualisoidulle Linux-koneelle. Lisäosien avulla esimerkiksi VirtualBox-ikkunan koon muuttaminen muuttaa automaattisesti virtualisoidun työpöydän resoluutiota ikkunan koon mukaiseksi. 

Asennus tapahtuu helpoiten syöttämällä virtuaalikoneeseen virtuaalinen asennus CD virtuaalikoneen ollessa käynnissä:

![Install guest additions](guest-additions.png)

Lisää ohjeita löydät [Googlella](https://www.google.com/search?q=virtualbox+install+guest+additions).

Virtuaalikoneen ja "host"-koneen välillä on myös mahdollista synkronoida leikepöytä. Tällöin pystyt kopioimaan ja liittämään tekstiä kätevästi eri järjestelmien välillä. Käynnissä olevan virtuaalikoneen "Devices"-valikosta löytyy kohta "Shared clipboard", jonka avulla voit valita leikepöydän toimintalogiikan haluamaksesi.


## Loppusanat

Jos sait yllä olevat kohdat suoritettua, olet erinomaisesti valmistautunut kurssin tehtäviä varten. Mikäli törmäsit ongelmaan, kysythän neuvoa [Teamsissa](http://teams.microsoft.com/). Myös oppitunneilla on mahdollista kysyä neuvoa.
