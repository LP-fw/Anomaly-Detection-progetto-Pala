## Analisi Comparativa di tecniche di Anomaly Detection per serie temporali di sensori in serre agrifood

Progetto d'esame per il corso di Ottimizzazione, Intelligenza Artificiale e Machine Learning (Università di Bologna).

---

Rilevamento non supervisionato di anomalie in serie temporali di sensori ambientali (temperatura e umidità) provenienti da una serra sperimentale belga dedicata alla coltura di pomodori. Sette metodi di outlier detection vengono confrontati sistematicamente su tre mesi di dati orari, usando come sanity check un guasto hardware e il consenso tra metodi come indicatore di affidabilità in assenza di etichette complete.

### Dataset


- **Origine**: [Zenodo DOI 10.5281/zenodo.5793685](https://doi.org/10.5281/zenodo.5793685)
- **Sottoinsieme analizzato**: 5 sensori su 27 (gli unici con copertura del periodo del guasto), maggio-agosto 2020, ricampionati a frequenza oraria (~2.400 ore)
- **Evento certificato**: guasto hardware del sensore AF27 il 14 luglio 2020 (crollo simultaneo di temperatura e umidità)

### Sruttura e flusso di lavoro

1. Introduzione del problema
2. Descrizione del dataset
3. Lettura e preparazione dei dati
4. Visualizzazione ed EDA
5. Outlier detection: prime analisi (baseline + ground truth + analisi di sensibilità)
6. Implementazione dei modelli avanzati
7. Valutazione e confronto dei risultati
8. Conclusioni finali, limiti e sviluppi futuri


### 
||METODI CONFRONTATI |
|---|--------|
| 1 | Z-score classico |
| 2 | Modified z-score (MAD) |
| 3 | STL + MAD sui residui |
| 4 | Isolation Forest |
| 5 | Prophet + MAD sui residui |
| 6 | ARIMA + MAD sui residui STL |
| 7 | Finestre mobili + Isolation Forest |

Stessa soglia statistica (modified z-score 3.5) applicata a rappresentazioni diverse dei dati. 
Valutazione  comparativa: sanity check sul guasto documentato, tassi di allarme, e consenso tra metodi (majority voting).

### Risultati principali

- **5 metodi su 7** riconoscono entrambe le ore del guasto.
- **Il consenso isola l'anomalia senza usare le etichette**: le uniche 3 ore dell'intero periodo con ≥5 metodi concordi sono le 3 ore del 14 luglio.
- **Il consenso segnala un'ora non certificabile** (le 13:00, dato grezzo mancante), isolata da 6 metodi su 7.
- Nodo centrale: **la rappresentazione dei dati conta più della scelta dell'algoritmo**


---
L.Pala, Luglio 2026
