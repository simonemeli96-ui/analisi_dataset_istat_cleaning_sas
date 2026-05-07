# Digital Divide in Italia: Analisi dell'uso della tecnologia post-Covid (2019–2023)

> **Progetto accademico di gruppo**  
> Autori: Daniele Cepparrone, Simone Meli, Federico Orizzonte  
> Master in Analisi Dati per la Business Intelligence — Università di Torino, A.A. 2024/2025

## Descrizione del progetto
Analisi statistica dei cambiamenti nei comportamenti digitali della popolazione italiana 
prima e dopo la pandemia di Covid-19, condotta su dati reali ISTAT dell'indagine 
"Aspetti della vita quotidiana" (AVQ) degli anni 2019 e 2023.

Il progetto esplora se e come la pandemia abbia accelerato la digitalizzazione della 
popolazione italiana, e quali variabili socio-demografiche influenzano maggiormente 
il livello di utilizzo della tecnologia.

---

## Obiettivo di ricerca
Verificare l'ipotesi che la pandemia Covid-19 abbia rappresentato un momento 
trasformativo nei comportamenti digitali degli italiani, e identificare i principali 
fattori socio-demografici associati al digital divide nel 2023.

---

## Dataset
- **Fonte:** ISTAT – Indagine multiscopo "Aspetti della vita quotidiana"
- **Anni:** 2019 e 2023
- **Dimensione:** ~41.750 record per anno, ~24.000 famiglie campionate
- **Variabili analizzate:** 24 variabili (8 anagrafiche + 8 tecnologiche + altre)

---

## Tecnologie utilizzate
- **Linguaggio:** SAS (SAS Studio)
- **Procedure principali:** PROC FREQ, PROC MEANS, PROC SGPLOT, PROC TABULATE, 
  PROC LOGISTIC, PROC GLM, PROC CORR, PROC FORMAT, DATA Step, Macro SAS

---
## Principali procedure SAS utilizzate

| Procedura | Scopo |
|---|---|
| `DATA Step` | Preparazione dati, merge dataset 2019-2023, costruzione indice |
| `PROC FORMAT` | Decodifica e standardizzazione delle variabili |
| `PROC FREQ` | Distribuzioni di frequenza e test Chi-quadro |
| `PROC MEANS` | Statistiche descrittive e analisi valori mancanti |
| `PROC SGPLOT` | Visualizzazioni grafiche |
| `PROC GLM` | ANOVA con interazioni (R² = 0.481) |
| `PROC LOGISTIC` | Regressione logistica ordinale |
| `PROC CORR` | Correlazioni di Spearman |
| `PROC TABULATE` | Tabelle di riepilogo |

---

## Metodologia

### 1. Preparazione dei dati
- Selezione di 24 variabili rilevanti da 741 variabili disponibili
- Decodifica e standardizzazione dei metadati con PROC FORMAT
- Analisi dei valori mancanti con PROC MEANS (NMISS)
- Riclassificazione delle fasce d'età da 15 a 7 categorie
- Merge dei dataset 2019 e 2023 su variabili comuni tramite DATA Step

### 2. Costruzione dell'indice tecnologico
Indice composito (0–17) basato su 17 variabili binarie, suddiviso in tre sottogruppi:
- **Gruppo 1 – Uso internet e attività online:** frequenza internet (FREQIN12), 
  social network (INCOMU6), espressione opinioni online (INCOMU7)
- **Gruppo 2 – Servizi avanzati:** banking online (INTATT11), vendite online 
  (INTATT13), corsi di formazione online (INTATT18A)
- **Gruppo 3 – Possesso strumenti:** smartphone con internet (TELCIN), 
  computer in casa (PC)

Gestione delle differenze di codifica tra i due anni per variabili identiche 
ma con valori diversi (es. INCOMU6, INCOMU7).

### 3. Analisi statistica
- **Test Chi-quadro** per l'associazione tra livello tecnologico e variabili 
  demografiche (età, istruzione, condizione occupazionale, regione, sesso)
- **ANOVA (PROC GLM)** con interazioni di secondo ordine per valutare gli effetti 
  delle variabili socio-demografiche (R² = 0.481, p < 0.001)
- **Regressione logistica ordinale (PROC LOGISTIC)** per modellare i predittori 
  del livello tecnologico
- **Correlazioni di Spearman (PROC CORR)** tra variabili ordinali
- **Alpha di Cronbach = 0.757** — buona coerenza interna dell'indice

---

## Principali risultati

- **L'indice tecnologico 2023 supera quello del 2019** in tutti i valori positivi: 
  la pandemia ha accelerato l'adozione della tecnologia
- Nel 2019 nessun individuo raggiungeva il punteggio massimo nell'uso dei 
  servizi online avanzati; nel 2023 questo dato cambia significativamente
- **Condizione occupazionale:** gli occupati hanno un livello tecnologico "alto" 
  nel 52,8% dei casi vs. 20,2% degli inattivi (p < 0.001)
- **Istruzione:** il 76% degli individui con alto livello tecnologico ha almeno 
  il diploma; il 38,2% dei low-tech non ha titolo di studio
- **Digital divide generazionale:** forte correlazione età-tecnologia; 
  gli over 65 mostrano prevalentemente basso livello tecnologico
- **Divario geografico:** Nord-Centro vs. Sud — Lazio al 50,8% di alto livello 
  tecnologico, Calabria al 60,4% di basso livello
- Il modello ANOVA spiega il **48,1% della varianza** dell'indice tecnologico

---

## Struttura del repository

| File | Descrizione |
|---|---|
| `analisi_digital_divide.sas` | Codice SAS completo: data preparation, indice tecnologico, analisi statistica |
| `Report SAS.docx` | Report descrittivo dell'analisi |

---

## Note sui dati

I microdati ISTAT utilizzati sono pubblici e disponibili sul 
[portale ISTAT](https://www.istat.it/it/archivio/91926).  
Il dataset grezzo non è incluso nel repository per ragioni di dimensione.  
Il codice SAS è eseguibile scaricando i microdati AVQ 2019 e 2023 
direttamente dal portale ISTAT.
