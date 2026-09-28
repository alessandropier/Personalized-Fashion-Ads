# Personalized Fashion Ads

**`Personalized Fashion Ads`** è un sistema interattivo per il settore moda che utilizza modelli generativi — VLM (Vision Language Model) e LDM (Latent Diffusion Model) — per creare immagini pubblicitarie personalizzate, partendo da capi baseline e dal profilo dell’utente.

Le immagini generate vengono poi **_valutate attraverso questionari_** e **_analizzate tramite metodi statistici avanzati_** (_correlazioni, regressioni, modelli di preferenza_) per comprendere il legame tra personalizzazione visiva e preferenze estetiche.

🔹 Il progetto si compone di **due web app**:

- **Interfaccia Utente**: gli utenti inseriscono il proprio profilo, visualizzano immagini **baseline** e **generate ad hoc**, e compilano un questionario per ogni confronto.
- **Dashboard Superuser**: consente di analizzare l'impatto dela personalizzazione tramite **query SQL**, **grafici interattivi**, **correlazioni**, **modelli di regressione** e **modelli di scelta** come Bradley-Terry.

🎯 L’obiettivo del progetto è **valutare l’impatto della personalizzazione** nel contesto della moda, esplorando quanto i contenuti generati su misura influenzino le **preferenze estetiche** e, potenzialmente, le **decisioni d’acquisto**.  
L’analisi si concentra sul legame tra **caratteristiche individuali** e **reazioni visive**, con l’intento di offrire insight utili per strategie creative e pubblicitarie più mirate.

In prospettiva, questo progetto pone le basi per sviluppare un sistema di personalizzazione ex-novo, dinamico e adattivo, capace di generare contenuti visivi in linea con i gusti e le esigenze dell’utente in tempo reale.

## 🎞️ Video di Funzionamento

### 👨‍👦​​ Registrazione Utente
L’utente inserisce i propri dati tramite un **form** all’interno della web app; tali informazioni vengono poi memorizzate nel **database sottostante**.
<div align="center">
  <img src="./readme gifs/registrazione.gif" width="900"/>
</div>

### 🖼️​📃 ​Generazione e Questionario
L’utente genera **quattro immagini**, una per ogni immagine di baseline. Per ogni tab di generazione, all’utente vengono presentate due immagini: l’immagine di partenza (_baseline_) e quella _generata_, disposte affiancate in **ordine casuale**. Non viene indicata l’origine di ciascuna immagine, in modo da garantire un **confronto anonimo** e **ridurre eventuali bias** nella valutazione. Dopo **ogni generazione** l'utente compila un apposito **questionario di valutazione**. Tutte le immagini generate vengono salvate nell'apposita cartella dedicata alle immagini generate, mentre le relative informazioni vengono archiviate nel **database sottostante**.
<div align="center">
  <img src="./readme gifs/gen&quest.gif" width="900"/>
</div>

### 📈​​📊​ Schermata SuperUser
Web app dedicata al **superuser**, progettata per l’**analisi dei dati** raccolti dalle generazioni e dai questionari utente. Le prime quattro schermate sono destinate a **interrogazioni** sul database, mentre le ultime quattro offrono strumenti per l’**analisi statistica**. Tutti i dati vengono presentati attraverso **tabelle** e **grafici interattivi**.
<div align="center">
  <img src="./readme gifs/superU.gif" width="900"/>
</div>

## 👜 Perché la Moda?
Il mio interesse nasce da un grande **amore** per la moda. Sono sempre stato affascinato dall'alta moda e dall'universo che ruota attorno ai capi, alle passerelle e all'**identità dei brand**. Maison come *Rick Owens*, *Valentino*, *Jacquemus*, *Prada*, *Margiela* e *Miu Miu* non si limitano a creare abiti: comunicano una cultura visiva, un'atmosfera e una **storia**.

Nell'e-commerce tradizionale, mantenere una presentazione dei prodotti **pulita** e oggettiva ha perfettamente senso perché l'obiettivo è **mostrare il capo** nella sua forma più pura. Tuttavia, esiste una grande opportunità per spingersi oltre. È proprio per questo che ho realizzato questo progetto:

- Come **strumento** per **creare** campagne pubblicitarie o esplorare nuovi concept di abbigliamento (sulla scia del [progetto A.I.R. di Nike](https://about.nike.com/en-GB/magazine/creating-the-unreal-how-nike-made-its-wildest-air-footwear-yet), che utilizza l'IA per superare i confini della creatività).
- Come **funzionalità** che i brand possono **integrare** direttamente nei propri **e-commerce**, consentendo agli utenti di visualizzare un capo abbinato e **personalizzato** in base al proprio profilo, **su richiesta**.

## ⚖️ Etica

Questo strumento deve fungere sempre da **supporto**, **mai** da **sostituto** della **creatività** e dell'**artigianalità** umane. L'obiettivo del progetto non è eliminare la componente umana dalla moda, bensì **fornire** a designer e creativi **strumenti** potenti per valorizzare il proprio lavoro e presentarlo al meglio.

Maggiori informazioni su questo argomento sono disponibili nella mia tesi.

## 📦 Funzionalità del Progetto

### Interfaccia Utente
- **Registrazione guidata** con form dettagliato su interessi, stile, preferenze e dati demografici
- **Visualizzazione immagini baseline** in base al genere dell'utente
- **Generazione automatica** di immagini personalizzate (`Gemini` + `Stable Diffusion`)
- **Compilazione di questionari** obbligatori per ogni immagine generata
- **Raccolta feedback** su preferenze estetiche e percezione del contenuto

### Sistema di Generazione
- **Prompt dinamico** costruito con componenti fisse e variabili (profilo utente + immagine)
- **Modello VLM** (`Gemini Flash 2.0 Exp`) per descrizione e arricchimento del prompt
- **Modello LDM** (`Stable Diffusion 3.5 Large`) per sintesi visiva dell’immagine

### Interfaccia Superuser
- **Dashboard interattiva** con visualizzazioni `Plotly`, `Matplotlib` e `Seaborn`
- **Query SQL** realizzabili direttamente dal browser
- **Analisi performance immagini baseline** (preferenze vs. varianti generate)
- **Calcolo metriche statistiche**:
  - Matrice di correlazione (`Pearson`)
  - Regressione lineare (`OLS`)
  - Modelli di confronto (`Bradley-Terry`, standard e pesato)

### Gestione Dati
- **Importazione automatica** da file CSV per:
  - Registrazioni utenti
  - Immagini baseline/generate
  - Risposte ai questionari
- **Database SQLite** coerente e relazionato, creato dinamicamente con i CSV
- **Struttura modulare** e facilmente estendibile


## Struttura del progetto
```
📁 Immagini Baseline/
├── uomo/
├── donna/
📁 Immagini Generate/
📁 readme gifs/

📄 immagini_baseline.csv
📄 immagini_generate.csv
📄 questionario.csv
📄 registrazioni.csv
📄 domande.csv
💾 fashion_database.db

📄 main.py
📄 models.py
📄 sql superinterface.py
📄 OneTimeScript crea_immagini_baselinecsv.py
📄 OneTimeScript_crea_domandecsv.py
📄 Tesi Piergiovanni.pdf
📄 requirements.txt

📄 README.md
```

#### Descrizione dei file e delle cartelle

#### 🗂️ Cartelle

- `Immagini Baseline/`  
  Contiene le immagini di partenza (baseline) suddivise per genere:
  - `uomo/`: immagini baseline maschili
  - `donna/`: immagini baseline femminili

- `Immagini Generate/`  
  Contiene le immagini generate dinamicamente dal sistema (`Stable Diffusion 3.5 Large`) a partire dal profilo utente

- `readme gifs/`  
Contiene le gif che mostrano il funzionamento del sistema

#### 📁 File CSV

- `immagini_baseline.csv`  
  Elenco delle immagini baseline con ID, genere e percorso file. Viene generato automaticamente dallo script `onetime_crea_immagini_baselinecsv.py`.

- `immagini_generate.csv`  
  Contiene informazioni sulle immagini generate, incluso il prompt, data/ora, immagine baseline di riferimento e percorso file salvato.

- `questionario.csv`  
  Raccolta delle risposte utente alle domande comparative tra immagini baseline e generate (inclusa la domanda finale Likert).

- `registrazioni.csv`  
  Contiene i profili degli utenti che hanno partecipato alla valutazione (età, genere, interessi, preferenze moda, ecc.).

- `domande.csv`  
  Elenco delle domande presentate nel questionario, suddivise per set. Creato dallo script `onetime_crea_domandecsv.py`.

#### ⚙️ File Python

- `main.py`  
  Avvia la **web app utente**: consente la registrazione, la generazione delle immagini, la compilazione del questionario e funzioni ausiliarie per gestire dati e logica.

- `models.py`  
  Contiene le **funzioni di generazione contenuti** per il sistema:
    - `generate_fashion_prompt()`: costruisce un prompt testuale personalizzato a partire da un'immagine di riferimento e da un profilo utente, utilizzando **Gemini Flash** (VLM).
    - `generate_adv_image()`: genera un'immagine pubblicitaria basata sul prompt ricevuto, tramite **Stable Diffusion 3.5 Large** (LDM).

- `sql superinterface.py`  
  Avvia la **dashboard analitica (superuser)**: permette di visualizzare i dati raccolti tramite:
  - grafici interattivi Plotly/Matplotlib
  - analisi statistiche (correlazioni, regressioni)
  - modelli di scelta (Bradley-Terry)

- `onetime_crea_immagini_baselinecsv.py`  
  Script una tantum per generare automaticamente il file `immagini_baseline.csv` leggendo le immagini nelle cartelle `Immagini Baseline/`.

- `onetime_crea_domandecsv.py`  
  Script una tantum per definire e salvare nel CSV i testi delle domande che compongono il questionario.

#### 📦 Altri file

- `requirements.txt`  
  Elenco completo delle librerie Python richieste per eseguire il progetto (es. `gradio`, `plotly`, `pandas`, `statsmodels`...).

- `fashion_database.db`  
  Database SQLite generato automaticamente dal sistema. Contiene tutte le informazioni strutturate (utenti, immagini, domande e risposte).

- `Tesi Piergiovanni.pdf`  
  Tesi di laurea sul sistema realizzato: include introduzione, stato dell'arte, documentazione completa del progetto, con descrizione, implementazione e analisi dei risultati.


## 🛠️ Requisiti

- Python 3.9+
- Ambiente virtuale (`venv`) consigliato

### 1. Installa le dipendenze

```
pip install -r requirements.txt
```
### 2. Configurazioni Iniziali
Se **non è presente** il file `immagini_baseline.csv`, oppure il **numero** di immagini nella cartella `Immagini Baseline/` **è cambiato**:
```
python OneTimeScript_crea_immagini_baselinecsv.py
```
Se devi **aggiornare le domande** del questionario (o ricreare il file `domande.csv`), esegui:
```
python OneTimeScript_crea_domandecsv.py
```
Ricorda di aggiornare l’**ID del set domand**e nel file `main.py` o `sql superinterface.py` se stai utilizzando un nuovo set e di **aggiungere/modificare** le domande nello script!

Se non hai **nessuna modifica da fare** puoi passare al passaggio successivo.

### 3. Impostazione delle API KEYS
Aggiungere le tue **API Key** nel file `models.py`:  
> - Chiave per **Gemini** tramite [OpenRouter](https://openrouter.ai/)  
> - Chiave per **Stable Diffusion** tramite [Stability AI](https://platform.stability.ai/)  

Senza queste chiavi, la generazione delle immagini non funzionerà.

### 4. Esecuzione delle Web App
- Per avviare la **Web App Utente**:
```
python "main.py"
```
- Per avviare la **Dashboard Superuser**:
```
python "sql superinterface.py"
```

⚠️ I due script condividono la stessa porta (_7860_), quindi possono essere eseguiti solo **uno alla volta**.
Avvia `main.py` per la _web app utente_ o `sql superinterface.py` per la _dashboard superuser_.

Entrambe saranno disponibili all’indirizzo http://localhost:7860.
Se si vuole rendere le pagine raggiungibili **via web**, è necessario impostare `share = True` alla riga di avvio della pagina:
```
app.launch(server_port = 7860, share = True) 
```
Di seguito, Gradio fornisce un **link temporaneo** con validità di _3 giorni_ nel terminale per raggiungere la pagina web da qualsiasi dispositivo con una connessione di rete.


## 👨‍🎓 Autore

**Alessandro Piergiovanni** </br>
Corso di Laurea in Informatica </br>
Università degli Studi di Bari “Aldo Moro” </br>
Tesi triennale in "_Metodi per il Ritrovamento dell’Informazione_" </br>
Anno Accademico 2023/2024 

📝 Portfolio: [alessandro.github.io](https://alessandropier.github.io)  
🔗 GitHub: [github.com/alessandropier](https://github.com/alessandropier)  
📫 Contatti: [alessandropiergiovanni.info@gmail.com](mailto:alessandropiergiovanni001@gmail.com)  
