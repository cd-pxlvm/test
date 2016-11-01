# Git

## Achtergrond

Git is bedacht door de Linus Torvalds, de geestelijke vader van Linux. 
Daarom ook is git van huis uit een Linux tool. Omdat echter deze tool zo
populair was, ontstonden ook ports naar de andere besturingssystemen.

We willen in dit hoofdstuk de focus leggen op een Windows installatie,
zonder af te hangen van oorspronkelijke Linux tools zoals bash. Daarom
opteren we voor een installatie via _Github Desktop_.
Dit pakket is gratis, en integreert een volledige git-installatie,
zonder teveel extra configuratie. Bovendien kan gebruik gemaakt worden
van de Powershell- of DOS-prompt, hetgeen voor windowsprogrammeurs gekend
terrein is.

> Merk op: deze software draait onder Windows en Mac.

## Accounts aanmaken

### Mail

Zorg dat je een bestaand e-mail adres hebt. Via dit adres zal je soms
bepaalde mails moeten bevestigen.

### Github

Github is een project dat open source software verzamelt. Er wordt aangemoedigd
om _sociaal_ de coderen, m.a.w. mee te werken aan open source software en zelf nieuwe
projecten aan te maken die door anderen kunnen gebruikt worden.

Ga naar [github.com](http://github.com) en maak een account. In deze tutorial werken
we met de fictieve gebruiker _Xavier La Place_.

![Github account](images/github1.png)

Vervolgens kom je in het welkomstscherm van github terecht.

![Github welkom](images/github2.png)

In principe ben je nu klaar om projecten (_repositories_) op te zetten en code op github
te plaatsen. Bedenk echter dat deze code per definitie _open source_ is en dat iedereen
deze code kan en mag gebruiken. Omdat dit soms niet altijd wenselijk is, maken we ook
een account op Bitbucket.

### Bitbucket

Bitbucket is een organisatie die private repositories toelaat. Dit laat je toe om code geheim
te houden voor de buitenwereld. Bovendien is het gratis als je project uit maximaal 5 teamleden bestaat.

Ga naar [bitbucket.org](http://bitbucket.org) en maak een account. We gebruiken dezelfde gebruiker:

![Bitbucket account](images/bitbucket1.png)

Je komt terecht in het welkomstscherm van bitbucket:

![Bitbucket welkom](images/bitbucket2.png)

Nu zijn we klaar om de software te installeren.

> __TIP: noteer en/of bewaar deze paswoorden goed!__

## Installatie

Ga naar [http://desktop.github.com](desktop.github.com) en download daar de laatste versie.
Eens ge&iuml;nstalleerd, zal dit programma zichzelf up-to-date houden.

Start de installatie door het bestand `GitHubSetup.exe` te starten.

![Start de installatie](images/gh4w-1.png)

Klik op `Install`, vervolgens worden de eigenlijke installatiebestanden gedownload en ge&iuml;nstalleerd.

![Downloaden en installeren](images/gh4w-2.png)

Na de installatie ga je automatisch naar het configuratiescherm.
Hier vul je je accountgegevens in van de Github website.

![Accountgegevens github](images/gh4w-3.png)

Klik vervolgens op `Log in`.

Nu kan je git configureren. Vul naam en e-mail in:

![Git configuratie](images/gh4w-4.png)

Klik op `Continue`.

Let op: in veel git tutorials wordt het configureren via de command line gedaan:

~~~
$ git config --global user.name "Xavier La Place"
$ git config --global user.email Xavier.Laplace@outlook.be
~~~

Als je dit dus ergens in een tutorial leest, hoef je deze stap dus niet meer te doen.

In een laatste stap, genaamd _Repositories_, zal het systeem je locale repositories
opsporen en toevoegen. Dit mag je eventueel overslaan.

![Github Desktop is klaar voor gebruik](images/gh4w-5.png)

Uiteindelijk is het programma klaar om nieuwe repositories aan te maken.

## Controle van de installatie

Github Desktop heeft twee snelkoppelingen op het bureaublad gezet: _Github_ en _Git Shell_. De eerste is de
grafische omgeving, de tweede de command line. Als je de _Git Shell_ start, krijg je een omgeving waarin je
de git commando's kan uitvoeren. Vaak is dit veel handiger dan de grafische schil.

![De git shell](images/gitshell.png)

Deze command line omgeving is de standaard Windows PowerShell, uitgebreid met een aantal instellingen om
gemakkelijker met git te werken.

Als je je zou afvragen waar de installatiebestanden zijn van deze tool, moet je eens een kijkje nemen in
de map `C:\Users\JouwNaam\AppData\Local\GitHub`.

![Github installatiebestanden](images/gitfiles.png)

Wat opvalt zijn de mappen met _PortableGit_ en _PoshGit_. De eerst map bevat alles met betrekking tot
de git tool zelf. De tweede map zijn de PowerShell uitbreidingen om gemakkelijk met git in de console te werken.

Veel installatiegidsen onder Windows installeren deze beide tools apart. Door te kiezen voor Github Desktop, worden
deze installaties gebundeld, krijg je een grafische schil en wordt ook alles automatisch up-to-date gehouden!

Je lokale instellingen vind je ten slotte terug in het bestand `C:\Users\JouwNaam\.gitconfig`

## Een nieuwe repository

We gaan vanaf nul een repository aanmaken, om lokaal mee te werken. Start de _Git Shell_ op je desktop. Ga naar
een map waar je je projecten bewaart, bijvoorbeeld `C:\Projects` en tik volgend commando:

~~~
C:\Projects\git init demoproject
Initialized empty Git repository in C:/Projects/demoproject/.git
~~~

Er is een map aangemaakt met daarin een folder `.git`. Dit is een speciale folder waar git zijn administratie bewaart.
Navigeer nu naar de projectfolder:

~~~
cd demoproject
C:\Projects\demoproject [master]\
~~~

Je merkt dat de shell aangeeft dat je je bevindt in de _master_ branch. Branches zijn afsplitsingen van een
project om bijvoorbeeld nieuwe features te ontwikkelen. Later worden die dan samengevoegd (_merge_) met de hoofdbranch.
De hoofdbranch is _master_ en bevat altijd de meest recente, stabiele code.

Maak nu eens een bestand aan in deze map genaamd `Program.cs`:

~~~ {.cs}
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace ConsoleApplication1
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Hello PXL");
        }
    }
}
~~~

Zodra je deze file hebt aangemaakt verschijnt in de shell:

~~~
C:\Projects\demoproject [master +1 ~0 -0 !]>
~~~

Het systeem detecteert dus dat er een nieuw bestand is. Dit kan je ook achterhalen door het statuscommando:

~~~
C:\Projects\demoproject [master +1 ~0 -0 !]> git status
# On branch master
#
# Initial commit
#
# Untracked files:
#   (use "git add <file>..." to include in what will be committed)
#
#       Program.cs
nothing added to commit but untracked files present (use "git add" to track)
~~~

Vooraleer git deze file voor je bijhoudt, moet je het toevoegen:

~~~
C:\Projects\demoproject [master +1 ~0 -0 !]> git add Program.cs
C:\Projects\demoproject [master +1 ~0 -0]>
~~~

Opnieuw de status opvragen, levert:

~~~
C:\Projects\demoproject [master +1 ~0 -0]> git status
# On branch master
#
# Initial commit
#
# Changes to be committed:
#   (use "git rm --cached <file>..." to unstage)
#
#       new file:   Program.cs
#
~~~

We hebben dit bestand _gestaged_, hetgeen betekent dat het klaar is om _gecommit_ te worden.
Het is klaargezet. Merk ook op dat git in zijn uitvoer ook uitleg geeft wat er gebeurt en
tips om je acties ongedaan te maken.

Uiteindelijk committen geeft:
~~~
C:\Projects\demoproject [master +1 ~0 -0]> git commit -m "eerste commit"
[master (root-commit) 874a279] eerste commit
 1 file changed, 16 insertions(+)
 create mode 100644 Program.cs
~~~

Merk op dat we nog steeds _lokaal_ werken, dus we houden versies van bestanden bij op de eigen machine,
zonder ze uit te wisselen met een externe server.

Best lees je nu eerst over de basiscommando's om volgende bewerkingen te doen: toevoegen, committen,
ongedaan maken en branches.

Meer info over deze basiscommando's, vind je op volgende referenties:

- [Pro Git, (Scott Chaconn)](http://git-scm.com/book/nl/De-basis-van-Git)
- [Git Succintly (Ryan Hodson)](http://www.syncfusion.com/resources/techportal/ebooks/git)

Tenslotte tonen we je nog hoe je het project toevoegt in de grafische schil van git. Open Github en sleep vanuit
een verkenner venster de map `demoproject` naar Github. Dubbelklik nu in Github op het project
en je krijgt een overzicht van je commits.

![Github commits in demoproject](images/github_commits.png)

## Push naar bitbucket

Na een tijdje wil je je lokale repository, met al zijn commits, uploaden naar een remote server.
Een eerste reden is backup: als je computer crasht, ben je veilig dat je harde werk bewaard is.
Een tweede reden is samenwerking: andere programmeurs kunnen deze repository weer ophalen en op
hun computer verderwerken.

### Maak een repository op bitbucket

Log in op (bitbucket)[http://bitbucket.org] en maak een nieuwe Repository aan:

![Een nieuwe repository](images/newrepo.png)

Als naam kiezen we voor __demoproject__, dezelfde naam als de folder in onze projectdir.
Dit is niet verplicht, maar wel duidelijk. We kiezen ook voor een __private__ project,
zodat niet de hele wereld onze code kan bekijken. Je kan later tot 4 teamgenoten uitnodigen
om samen aan deze repository te werken. Klik nu op `Create Repository`.

![Voeg code toe](images/addsomecode.png)

Het volgende scherm gidst je verder: afhankelijk of je vanaf nu begint of je reeds code hebt.
Wij hebben al lokaal een repository draaien, dus kies voor _"I have an existing project to push up"_:

![Push code](images/firstpush.png)

Er verschijnen nu een aantal git commando's die je moet ingeven op je code te uploaden.
We bekijken die even van dichtbij.

Het eerste commando zegt je om naar je lokale repository te gaan. Voor ons wordt dit dus:

~~~
cd C:\Projects\demoproject
~~~

De tweede lijn zegt:

~~~
git remote add origin https://xavierlaplace@bitbucket.org/xavierlaplace/demoproject.git
~~~

Dit zal de locatie van de remote repository verbinden met onze lokale repository. Dit commando zal __niet__ werken,
omwille van de installatie van github voor windows. Maar er is een andere en betere manier. Open het __Github__ programma,
selecteer het demoproject en ga naar settings:

![github settings](images/settings.png)

Nu kan je het adres invullen bij primary remote (`https://enz.`).

![repository adres](images/accountinfo.png)

Klik ook op de link _Add a default .gitignore file_. Dit zorgt ervoor dat gegeneerde bestanden, zoals bin-folders,
exe-bestanden e.d. niet in de repository komen. Je kan deze file aanpassen als je wilt, maar standaard staat deze goed
ingesteld voor zowel java als C\# projecten.

Klik ook op de linkt _Add the recommended .gitattribute file_. Dit zorgt ervoor dat er correct omgegaan
wordt met nieuwelijntekens die kunnen verschillen als je samenwerkt met programmeurs op andere besturingssystemen.

Het resultaat ziet eruit als volgt:

![ignore files](images/ignorefiles.png)

Klik nu op `Update` en vul je accountgegevens voor bitbucket in.

Als je nu terug naar de console gaat, zal je merken dat er twee nieuwe bestanden zijn toegevoegd. Commit deze:

~~~
C:\Projects\demoproject\git add .
C:\Projects\demoproject\git commit -m "administratieve bestanden"
~~~

Nu is het tijd om onze repository te pushen naar de remote site. Eerst nog een laatste controle:

~~~
git remote -v show
origin  https://xavierlaplace@bitbucket.org/xavierlaplace/demoproject.git (fetch)
origin  https://xavierlaplace@bitbucket.org/xavierlaplace/demoproject.git (push)
~~~

Hier zie je dat de site ingesteld staat voor het uploaden (push) als het downloaden (pull).
Doe nu de laatste stap:

~~~
git push -u origin --all # pushes up the repo and its refs for the first time
Counting objects: 7, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (6/6), done.
Writing objects: 100% (7/7), 2.14 KiB | 0 bytes/s, done.
Total 7 (delta 0), reused 0 (delta 0)
To https://xavierlaplace@bitbucket.org/xavierlaplace/demoproject.git
 * [new branch]      master -> master
Branch master set up to track remote branch master from origin.
~~~

Optioneel kan je ook doen:

~~~
git push -u origin --tags # pushes up any tags
~~~

Maar voor ons project is dit overbodig, want er zijn nog geen tags gedefinieerd.

Commit en push operaties kan je ook uitvoeren vanaf het github venster. Als er gewijzigde of
nog niet toegevoegd bestanden zijn, laat github de verschillen zien. Links kan je dan ineens
een commit bericht toevoegen en committen.

![github commit](images/githubcommit.png)

Rechtsboven is een knop om je repo te syncen met de remote server.

![github sync](images/githubsync.png)

## pull van bitbucket

Je hebt een repository aangemaakt op bitbucket. Nu wil je die delen met collega-programmeurs.
Ga hiervoor opnieuw naar je bitbucket project in de browser en klik op __Invite friends__.

![Invite](images/invitation.png)

Vervolgens geef je een email adres of username van je collega. Vergeet ook niet aan te geven
welk recht die collega krijgt: read, write of admin rechten.

![Share](images/share.png)

Nadat je op `Share` hebt geklikt, krijgt je collega een mail met daarin een link. Eens op deze link
geklikt, is je collega toegevoegd aan het team.

Collega "Kris" surft nu naar bitbucket en opent de repository waar hij is aan toegevoegd. Vervolgens
zoekt hij via de `Clone`-knop het git-commando dat hij nodig heeft om de repository
lokaal naar zijn machine te kopiëren.

~~~
git clone https://usernamecollega@bitbucket.org/xavierlaplace/demoproject.git
~~~

Dit commando maakt een subdirectory `demoproject` aan en kopieert daarin het volledige project.
