# VolareDiPiu
## Abstract
A simple airline route operability discovery modeller. 
The prototype is in Italian as it is mainly directed to an Italian audience.
## Operabilità Rotte
### Introduzione
Il documento Operabilità Rotte.xlsx è un prototipo sviluppato in Excel per modellare l'operabilità di una specifica rotta da parte di una compagnia aerea.

In questa versione vi sono 2 fogli di calcolo e 3 grafici.

Il primo foglio di calcolo permette la configurazione dei parametri di ingresso. La configurazione proposta inizialmente è per una rotta giornaliera Ryanair da Reggio Calabria a Milano Linate, ma agendo sui parametri a disposizione si possono modellare svariati scenari.
L'ultimo foglio di calcolo ospita il modellatore. 

Per usare il prototipo per analizzare l'operabilità di una rotta basta semplicemente cambiare i parametri di ingresso nel primo foglio di calcolo. Il modellatore nell'ultimo foglio di calcolo è il motore del prototipo, chi vuole può provare a raffinarlo.

Il primo grafico mostra l'operabilità in termini dei fattori di riempimento richiesti per far decidere alla compagnia aerea di operare la rotta. Ad esempio, per la configurazione proposta inizialmente il grafico mostra che **la rotta di esempio da Reggio Calabria a Milano Linate**, dati i parametri di ingresso ipotizzati, **non è operabile ad alcun livello di fattori di riempimento**. Cambiare i parametri di ingresso potrebbe cambiare questo risultato, ad esempio **portando a zero il parametro per le imposte di imbarco aeroportuali renderà la rotta operabile**.

Il secondo grafico mostra i costi effettivi ed i profitti effettivi. Sull'asse delle x troviamo il numero incrementale dei passeggeri che comprano un biglietto, mentre sull'asse delle y vediamo le conseguenze finanziali per costi e ricavi.

Il terzo grafico mostra i costi effettivi ed i guadagni effettivi. Sull'asse delle x troviamo il numero incrementale dei passeggeri che comprano un biglietto, mentre sull'asse delle y vediamo le conseguenze finanziali per costi e guadagni.

### Suggerimenti

Il prototipo può modellare fino a cinque frequenze giornaliere su una stessa rotta. Nella realtà molte rotte, soprattutto tra piccoli aeroporti, sono sottili, nel senso che non possono reggere più di una frequenza giornaliera, spesso meno che giornaliera.

In generale, quando si modella più di una frequenza giornaliera, ha senso scegliere una serie decrescente di margini netti.

Aumentare i margini netti delle rotte rende ovviamente tutte le rotte operabili, in termini di un qualsiasi fattore di riempimento. Nelle realtà **i route manager dei vettori usano parametri realistici**, nel senso che aumentando il margine netto necessariamente diminuiscono i fattori di riempimento effettivi, per cui le rotte, pur essendo teoricamente operabili in termini di un teoretico fattore di riempimento, non sono veramente operabili, perchè quel fattore di riempiento non è in pratica materializzabile.

Per dare un esempio che chiarisca la questione, la rotta d'esempio da Reggio Calabria a Milano Linate diventerebbe teoreticamente operabile con un margine netto dell'85% già con un fattore di riempimento del 75%. Il problema è che quasi certamente per gran parte dei giorni dell'anno quella specifica rotta non raggiungerebbe un fattore di riempimento del 75% al prezzo del biglietto medio di €66.49 calcolato dal prototipo per quel margine netto. 

I route manager hanno generalmente a disposizione delle buone stime dei fattori di riempimento e dei margini osservati in passato per gran parte delle possibili rotte, e per quelle per cui non hanno stime a disposizione hanno dei modelli per calcolarle in maniera statistica. Se non si hanno buone stime a disposizione, il suggerimento è di essere realistici, ed anche un po pessimistici.

Una futura versione del prototipo potrebbe introdurre parametri di ingresso per configurare anche i fattori di riempimento effettivi.

### Parametri di Ingresso

| Variabili     | Valore           | Descrizione  | Suggerimenti | Note |
| ------------- |-------------:| -----| --- | --- | 
| Passeggeri| 189 | Numero massimo di passeggeri dell'aereo oggetto della simulazione |189 per I B737-800 di Ryanair|Se piú di 189, bisogna manualmente aggiornare il range dei dati per i grafici.|
| CASK carburante| 1.57 | Costo chilometrico del carburante per posto disponibile, in centesimi di Euro | 1,57 per Ryanair, 2,30 per Lufthansa, .. | Dipende anche dalle politiche di hedging. |
| CASK escluso carburante | 2.12 | Costo chilometrico escluso carburante per posto disponibile, in centesimi di Euro |da 2.12 per Ryanair a salire (e.g. 8,20 per Lufthansa)||
|CASK|3.69|Costo chilometrico per posto disponibile, in centesimi di Euro|da 3.69 per Ryanair a salire (e.g. 10,50 per Lufthansa)|Il CASK aumenta per le rotte brevi, e diminuisce per le rotte lunghe. Nella realtá, varia anche per ogni coppia di aeroporti, e.g. per via delle variazioni dei costi aeroportuali (tasse, diritti, ..).|
|Margine Netto I|25%|Margine sul primo aereo nella rotta oggetto della simulazione|minimo 20% negli aeroporti piccoli, di piú nei medi e nei grandi|Ryanair ha un obiettivo di un margine netto del 20%. Se la rotta non garantisce quell'obiettivo, é improbabile che la operino. Altre compagnie potrebbero avere obiettivi di margine netto differenti, in quel caso sostituire al 20% quel diverso obiettivo di margine netto.|
|Margine Netto II|0%|Margine sul secondo aereo nella rotta oggetto della simulazione|minimo 20% negli aeroporti medio piccoli (e.g. Brindisi o Olbia in summer)|Se la rotta regge 2 frequenze, altrimenti 0%|
|Margine Netto III|0%|Margine sul terzo aereo nella rotta oggetto della simulazione|minimo 20% negli aeroporti medi (e.g. Palermo, Pisa)|Se la rotta regge 3 frequenze, altrimenti 0%|
|Margine Netto IV|0%|Margine sul quarto aereo nella rotta oggetto della simulazione|minimo 20% negli aeroporti grandi. (e.g. Linate, Venezia)|Se la rotta regge 4 frequenze, altrimenti 0%|
|Margine Netto V|0%|Margine sul quinto aereo nella rotta oggetto della simulazione|minimo 20% negli aeroporti grandi|Se la rotta regge 5 frequenze, altrimenti 0%|
|Distanza (KM)|974|Distanza tra l'aeroporto di partenza e quello di arrivo della rotta oggetto della simulazione|974 km per un Reggio Calabria - Linate|
|Imposta|€ 7.15|Imposta addizionale di imbarco (uno dei maggiori ostacoli allo sviluppo dei collegamenti aerei in Italia)|€7,15 sui nazionali, €6,50 sugli internazionali|Nei primi 8 mesi del 2019 €9,90 sui nazionali, €9,00 sugli internazionali|
|Margine Netto Obiettivo|20%|Margine netto obiettivo del vettore|20% Ryanair|Piú si allontana dal margine netto, meno é probabile che una rotta venga operata|
