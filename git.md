## 📜Git versiohallinta

Luodaan ensin uusi *Projekti* niminen kansio/hakemisto esim. *Tiedostot* hakemistoon.  
`md %userprofile%\documents`  

Harmaalla pohjalla näkyvät komennot annetaan joko komentokehotteessa tai *Visual Studio Code*:n pääte (terminal) ikkunassa.  
Jos käytetään komentokehotetta, tulee työhakemistona olla *C:\users\omatunnus\Documents\Tiedostot\Projekti*.  

**Alustetaan työkansio Git:ä**

`git init ` | Alustetaan työhakemisto git käyttöä varten   
`git config --global user.email "etunimi.sukunimi@example.com" `| Määrittää sähköpostiosoitteen    
`git config --global user.name "Etunimi Sukunimi"` | Määrittää käyttäjänimen    
`git config --list` | Näyttää asetukset  
`git config user.name` | Näyttää käyttäjän edellä määritetyn käyttäjänimen    
`git config --global init.defaultBranch main` | Muuttaa päähaaran nimeksi main masterin sijaan    
`git config --list --global` | Näyttää globaalit asetukset  
`git config --edit --global` | Avaa git asetukset oletuseditoriin. Oletuseditori valitaan alun perin gittiä asennettaessa)  

**Tiedosto .gitignore**  
Luodaan *projekti* hakemistoon uusi tiedosto nimeltä *.gitignore*   
Luodaan *projekti* hakemistoon uusi hakemisto nimeltä *alustava*  
Luodaan uusi *suunnitelma.txt* niminen tiedosto hakemistoon *alustava*   
Asetetaan *.gitignore* tiedoston sisällöksi seuraavaa *alustava/* ja tallennetaan muutokset       

`git add .` | Lisätään tiedosto *.gitignore* indeksiin  
`git status` | Tarkistetaan gitin tilanne  
`git commit -m "Tiedosto .gitignore luotu"` | Luodaan ensimmäinen committi    

**Luodaan tiedosto a.txt ja sinne sisältöä**

Luodaan projekti hakemistoon uusi *a.txt*  niminen tiedosto.  Asetetaan sisällöksi *a* ja tallennetaan muutokset.  
`git add a.txt` | Lisätään a.txt indeksiin  
`git status` | Tarkistetaan gitin tilanne  
`git commit -m "Tiedosto a.txt luotu"` | Luodaan uusi committi    
`git log` | Tarkistetaan commitit  

**Luodaan tiedosto b.txt ja siihen sisältöä ja "tajutaan" että se olisi pitänyt lisätä jo edelliseen commititin**

Luodaan *projekti* hakemistoon uusi *b.txt*  niminen tiedosto.  Asetetaan sisällöksi *b* ja tallennetaan muutokset.  
`git add b.txt` | Lisätään *b.txt* indeksiin  
`git status` | Tarkistetaan gitin tilanne    
`git commit --amend -m "Lisätty tiedosto A.txt ja B.txt"` | Lisätään indeksissä olevat tiedot eli uusi tiedosto *b.txt* edelliseen kommitiin ja muutetaan commitin kommenttia    
`git log --oneline` |  Tarkistetaan git commitit tiiviimmässä muodossa 

**Luodaan tiedosto c.txt ja sinne sisältöä**

Luodaan projekti hakemistoon uusi *c.txt*  niminen tiedosto.  Asetetaan sisällöksi *c* ja tallennetaan muutokset.  
`git add .` | Lisätään tiedosto *c.txt* indeksiin..   
ja tajutaan että tiedostoa ei olisi vielä pitänyt lisätä indeksiin  
`git diff HEAD` |  Tarkistetaan mitä eroa on työkansiolla ja viimeksi commitoidulla tiedolla     
`git restore --staged c.txt` | Poistetaan tiedosto *c.txt* indeksistä eli perutaan edellinen *add .* komento tiedoston *c.txt* osalta.  
`git status` | Tarkistetaan gitin tilanne. 

**Lisätään tiedosto d.txt ja siihen sisältöä**

Luodaan projekti hakemistoon uusi *d.txt*  niminen tiedosto.  Asetetaan sisällöksi *d* ja tallennetaan muutokset.  
`git add .` | Lisätään kaikki työkansion muutokset indeksiin.  Piste tarkoittaa kaikkia edellisen kommitin jälkeen tulleita muutoksia.     
`git commit -m "lisätty tiedostot c.txt ja d.txt"` | Luodaan uusi commit.    
`git log` | Tarkistetaan commitit  

**Lisätään lisää tietoa d.txt tiedostoon ja tallennetaan muutokset (ei commitoida). Muutokset halutaan kuitenkin perua**

Lisätään tiedostoon *d.txt* uutta tietoa ja tallennetaan muutos.  
Huomataan että tiedostoon tehty muutos halutaan perua.  
`git  checkout -- d.txt` | Palautetaan *d.txt* aiempaan versioon eli edellisessä commitissa olevaan tilanteeseen.      

**Luodaan uusi muutoshaara eli branch**

`git branch` = Tarkastetaan nykyiset muutoshaarat/branchit.    
`git branch bugfixi` | Luodaan uusi muutoshaara/branch TAI `git checkout -b bugfixi` | Luo ja siirtyy muutoshaaraan bugfixi yhdellä komennolla.  
`git branch -m bugfixi bugfix` | muutetaan muutoshaaran nimi bugfixi -> bugfix  
`git checkout bugfix` TAI `git switch bugfix` | Siirrytään uuteen muutoshaaraan jos edellä ei käytetty komentoa *git checkout -b bugfix*    

**Luodaan uusi tiedosto e.txt ja siihen sisältöä**

Luodaan uusi *e.txt* niminen tiedosto.  Asetetaan sisällöksi *e* ja tallennetaan muutokset.  
`git add e.txt` | Lisätään tiedosto *e.txt*  indeksiin.    
`git commit -m "Lisätty tiedosto e.txt"` | Luodaan uusi committi.    
`git log`   Tarkistetaan commitit.      
`git checkout main` |  Siirrytään takaisin *master* muutoshaaraan  
`git branch` | Tarkistetaan aktivinen muutoshaara    
`git merge bugfix` | Yhdistetaan *master* ja *bugfix* haaroissa olevat tiedot ja commitit.    

**Tarkastetaan että e.txt on ilmestynyt työkansioon ja poistetaan muutoshaara bugfix** 

Tarkistetaan että tiedosto *e.txt* on ilmestynyt työhakemistoon.  

`git log` |  Tarkistetaan että edellä *bugfix* muutoshaarassa luotu committi on lisätty *master* muutoshaaran kommitteihin.   
`git branch -d bugfix` | Poistetaan edellä luotu *bugfix* niminen muutoshaara.    

**Työhakemiston tarkastelu halutussa commitissa**   

`git log --oneline` |  Listataan commitit ja otetaan jonkin commitin id leikepöydälle    
`git checkout *commit id*` | Siirrytåään haluttuun committiin sen id-numeron perusteella    
Työhakemiston sisälktö päivittyy vastaamaan työhakemiston tilannetta committin tallennuksen hetkellä.    
`git chekcout master` | siirrytään takaisin viimeisimmän commitin mukaiseen tilanteeseen.    

**Tägien luominen, tarkastelu ja poistaminen**:

`git tag v.1.0` | Lisää ns. *lightweight* tägin *v.1.0* joka tarttuu nykyiseen (mutta ei seuraaviin) committin.    

Luodaan uusi *y.txt* niminen tiedosto. Asetetaan sisällöksi *y* ja tallennetaan muutokset.     
`git add y.txt` | Lisätään tiedosto *y.txt* indeksiin.    
`git commit -m "Lisätty tiedosto y.txt` | Luodaan uusi committi.    
`git log --oneline` | Tarkistetaan git commitit tiiviissä muodossa.    
`git tag` | Tarkistetaan tägit.    
`git log` v.1.0 --oneline` | Näyttää commitit jotka edeltävät mainittua tagiä    

`git tag -a v.1.1 -m "Versio 1.1"` | Luodaan ns. *annotated täg*.     
`git show v.1.1` | Näyttää tägin *v.1.1*  
`git log --oneline` | Tarkistetaan git commitit tiiviissä muodossa   
`git tag v1.2` = luo tägin v.1.1 rinnalle    
`git log --oneline` | Tarkistetaan git commitit tiiviissä muodossa  
`git tag -d v1.2`| Poistetaan edellä luotu rinnakkainen v1.2 tägi    

**Tägit eivät kopioidu esim. Githubiin automaattisesti**   
Jos tägit halutaan kopioida esim. GitHub ympäristöön tulee ne siirtää sinne erikseen.  
`git push v.1.1` | Puskee vain kyseisen tägin.   
`git push --tags` | Puskee kaikki tägit GtiHub:n    
`git push --delete v1.1` | Poistaa ko. tägin remotesta (esim. GitHub).    

#### Tiedostojen palauttamisesta: 

**Tallennettujen *commitoimattomien* tietojen peruminen**: 

Lisätään työkansioon tiedosto x.txt ja asetetaan sisällöksi *x* ja tallennetaan muutokset.  
`git add x.txt` Lisätään y.txt indeksiin.  
`git commit -m "Lisätty tiedosto x.txt"` | Luodaan uusi committi.    

Lisätään tiedostoon *x.txt* uutta sisältöä ja tallennetaan tiedosto
**HUOM**:  Ei committia eikä `add` tässä vaiheessa.  

Huomataan että uusi sisältö oli virhe ja halutaan palata tiedoston *x.txt* osalta aikaisempaan commitoituun sisältöön  
`git status` | Tarkistetaan gitin tilanne.     
`git checkout -- x.txt` | Palautetaan tiedosto *x.txt* edellisessä commitissa olevaan tilaan.      

**Tallennettujen ja commitoitujen tietojen peruminen**

Lisätään tiedostoon x.txt taas uutta sisältöä ja tallennetaan muutokset.  
`git commit -m "Sisältöä muokattu"` | Luodaan uusi commit joka sisätää edellä tehdyt muutokset.   

Huomataan että commitoitu sisältö oli virhe ja se halutaan perua. Tarkastetaan mitä muutoksia edellisessä commitissa oli.  

`git log --oneline` | Tulostetetaan commitit tiiviissä muodossa. Kopioidaan edellä tehdyn commitin id numero leikepöydälle.      
`git show *commitin id numero*` | Tarkistetaan mitä muutoksia committi sisältää.    
`git revert *peruttavan commitin id numero* --no-edit` | Perutaan viimeisimmässä commitissa olevat muutokset ja luodaan uusi committi perumisesta.   

**Työhakemistosta poistettun tiedoston palauttaminen**

Poistetaan tiedosto x.txt työhakemistosta.    
`git checkout HEAD x.txt` TAI `git checkout -- x.txt` | Palauttaa edellä poistetun tiedoston x.txt työhakemistoon.    
 
Jos poistaminen olisi ehditty jo commitoida  
`git reset --hard HEAD~1` tai git revert --no-edit *Poiston commitID* | Kumoaa viimeisimmän kommitin muutokset ja poistaa viimeisimmän commitin.  


**Commitin poistaminen**
Halutaan poistaa viimeisin commit.  
Luodaan uusi tiedosto *y.txt* ja asetetaan sisällöksi *y*.  
`git add y.txt` | Lisätään tiedosto *y.txt* indeksiin.  
`git commit -m "Lisätty tiedosto y.txt"` | Luodaan uusi commit joka sisätää tiedoston y.txt ja sen sisällön.   
`git log --oneline` | Tarkastetaan commitit tiiviissä muodossa.  
Todetaan että tiedosto commitoitiin liian aikaisin > halutaan perua viimeisin commitin mutta säästää muutokset työhakemistossa.   
`git reset --soft HEAD~1`      

Jos poistaa ainoastaan commit mutta säästää muutokset työkansiossa
`git reset --soft *commit hash*` TAI `git reset --soft HEAD~1`

*** HUOM Älä käytä *git reset* komentoa jos olet jakanut projektin muille esim. GitHub:a.***

#### Työhakemiston synkronoiminen GitHubiin

Rekisteröidytään GitHub ympäristöön ja käyttäjätunnusta ei vielä ole olemassa.  
`git branch -m main` | Vaihdetaan paikallisen *master* haaran nimeksi *main*.      

Luodaan uusi *projekti* niminen repositorio GitHubiin ja otetaan repositorion URL osoite leikepöydälle.  
`git remote add origin https://github.com/*oma github tunnus*/projekti.git` | Kytketään paikallinen työkansio Github repositorioon *origin* nimiseksi remoteksi.   

`git remote -v` | Tarkastetaan että edellä luotu GitHub repositoria on kytketty remoteksi nimellä *origin*.    

Remote voidaan tarvittaessa nimetä uudelleen komennolla `git remote rename origin *uusi remoten nimi*`     

`git push -u origin main` | Pusketaan paikallinen projekti hakemiston sisältö Githubiin. (*git push origin --all* puskee kaikki paikalliset haarat GitHubiin)  
Annetaan tarvittaessa GitHub käyttäjänimi ja salasana esille tulevaan ikkunaan.  
`git push origin --tags` | Pusketaan tägit GtiHubiin.    

Siirrytään GitHub ympäristöön ja lisätään sinne uusi *f.txt* niminen tiedosto.  GitHubissa ollaan yksi commit edellä  
`git fetch` | Haetaan GitHub tilanne paikalliseen ympäristöön.  
`git status` | Tarkistetaan gitin tilanne. Paikallinen ympäristö on yhden commitin (ja tiedoston) verran perässä GitHubissa olevan repositorian tilannetta.  
`git pull` | Kopioidaan GitHub:a olevat muutokset (tiedosto *f.txt* ja commit) paikalliseen työhakemistoon.    

Tarvittessa remote voidaan kytkeä irti komennolla remote `git remote rm origin`   

#### Upstream

Jos halutaan ladata sisältöä vieraasta *remotesta* oman työhakemistoon.  

Forkataan vieras julkinen repositorio omaan GitHubiin.   

Kloonataan oma forkki paikalliseksi työkansioksi.  

`git clone https://linkki_omaan_forkkiin.git`  

Lisätään paikallisen työkansioon upstream alkuperäiseen vieras repoon  
`git remote add upstream https://linkki_vieraaseen_repoon.git`  

`git remote -v`  

Alkuperäisessä etä_repossa on muutoksia ja ne pullataan paikalliseen työhakemistoon  

`git merge upstream/main`  

Tehdään muutoksia paikalliseen hakemistoon  

Lisätään ja commitoidaan  muutokset  
Työnnetään muutokset omaan forkkiin  
`git push` tai `git push origin`  
