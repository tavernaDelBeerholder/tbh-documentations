# [Lista dei moduli sempre aggiornati](https://github.com/tavernaDelBeerholder/tbh-documentations/blob/master/FVTT-MODULESv4.md)


# Linee guida per una gestione furba degli assets su FoundryVTT

# Documenti e risorse utili per iniziare (ancora in scrittura, i documenti potrebbero variare)

### I moduli testati e consigliati per FoundryVTT (per adesso secondo 4535992 poi dovremo decidere insieme)

[LINK LISTA MODULI by 4535992](https://github.com/tavernaDelBeerholder/tbh-documentations/blob/master/FVTT-MODULESv4.md)

# Linee guida degli assets

Non sto a entrare nei dettagli tecnici, ma queste sono le linee guida consigliate per evitare problemi con il codice degli sviluppatori.

### I nomi dei file e delle cartelle

1) Evitare nei nomi dei file degli assets spazi bianchi (molto importante), eventualmente sostituire con il carattere `_`
2) Evitare nei nomi dei file degli assets i seguenti caratteri speciali **( { } [ ] ( ) / \ ' " \` ~ , ; : . < > )**
3) I nomi delle cartelle SEMPRE tutti in minuscolo eventualmente il nome della cartella `Immagini Fiche` diventa `immagini_fiche`

#### Regole Opzionali consigliate, ma non sono essenziali:

4) Mettere nel nome delle immagini (in particolare per le scene) i riferimenti alle dimensioni, per esempio un'immagine di una caverna di dimensione 48x64 dovrebbe avere il nome `caverna_48x64.png`
5) Mettere nel nome delle immagini (in particolare per le scene) i riferimenti al fatto che sono di una mappa illuminata o non `caverna_lit_48x64.png`, `caverna_no_lit_48x64.png`
6) Mettere nel nome delle immagini (in particolare per le scene) i riferimenti al fatto che sono varianti di una mappa `caverna_summer_lit_48x64.png`, `caverna_winter_no_lit_48x64.png`

# Il formato e la dimensione degli assets

1) qualunque sia l'assets audio, video, immagine visto che non tutti abbiamo la fibra e il supercomputer con la CPU 8GB **NESSUN FILE DOVRA' ESSERE SUPERIORE AI 20 MB**, eventualmente nella sezione `TOOL` è possibile trovare dei programmi che comprimono o tagliano tali elementi, per esemio è inutile caricare in file mp4 da 169MB in 4k che è in pratica un loop dei medesimi 30 secondi, si taglia il video ai primi 30 secondi di dimensione di circa 6MB in 4k e il loop viene impostato su FoundryVTT.
2) Tutti i file immagine superiori ai 20MB possono essere ridotte anche dell' 80% semplicemente convertendo l'immagine nel formato `webp`.

#### Regole Opzionali consigliate, ma non sono essenziali:

3) Il formato preferenziale dei file audio è `.ogg` maggiore qualità e meno spazio usato rispetto al classico mp3.

# Come installare e utilizzare git (base)

1) Andare sul sito [Git](https://git-scm.com/download/)
2) Scaricare l'eseguibile ed installare

### Interfaccia grafica per git

Un tool utile per chi non è "codice dipendente" è il software [Tortoisegit](https://tortoisegit.org/download/) che aggiungi nelle voci di contesto di windows (click con il destro), le opzioni per i comandi base di git:

- git clone (download = scarica il progetto git)
- git commit (preparazione all'upload = indicizza i file da te modificati in locale)
- git push (upload = carica la tua roba)
- git pull (aggiornamento = prende le modifiche fatte da altri)

### Come caricare file di dimensioni superiori ai 100 mb su git

![img1](https://miro.medium.com/max/1140/1*CxjIFTuTb_tguRX3P08i6Q.jpeg)

Quindi l'altro giorno mi sono imbattuto in questo errore durante il caricamento di un file MP4 in cui Github afferma che non accetterà file superiori a 100 MB.

Questo mi ha fatto capire che abbiamo dato Github per scontato e che dovremmo usarlo più saggiamente... lol, scherzo ... Ecco come caricare i file superiori ai 100mb su github repository:

1) scarica e installa Git-lfs ( Git Large File Storage ) da [qui](https://git-lfs.github.com/).
2) imposta Git lfs per il tuo account utente git lfs install.
3) se hai già provato a eseguire il commit di file di grandi dimensioni e hai ricevuto l'errore, devi prima annullare il commit, utilizzare git reset — soft HEAD~1 altrimenti ignora questo passaggio.
4) Seleziona i tipi di file che vuoi che Git-lfs gestisca usando il comando `git lfs track "*.mp4"` sul progetto git, questo crea un file `.gitattributes` sulla root del progetto.
5) aggiungere il file `.gitattributes` insieme ad altri file di cui è necessario eseguire il commit e inviare le modifiche.

```
git add .gitattributes
git commit -m "Messaggio qualsiasi"
git push origin master
```

i seguenti comandi possono esseri fatti anche da interfaccia grafica con il programma `tortoisegit` sopra citato

