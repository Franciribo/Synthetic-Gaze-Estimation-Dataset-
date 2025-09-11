# Synthetic-Gaze-Estimation-Dataset
Synthetic Gaze Estimation Dataset

Questo progetto utilizza Blender per generare un dataset sintetico per la stima dello sguardo (“gaze estimation”). La generazione di immagini 3D rende possibile creare molteplici variazioni con annotazioni automatiche perfette
github.com
, superando i limiti dei dataset reali. Qui lo script Python controlla la scena in Blender per produrre diverse direzioni di sguardo e posizioni di camera, registrando tutte le combinazioni in file CSV organizzati secondo i punti chiave (landmark) facciali.

### Caratteristiche del dataset

-**Gaze directions**: 432 diverse direzioni dello sguardo per soggetto.

-**Posizioni camera**: 55 posizioni prefissate della camera (su vertici di una semisfera intorno al soggetto).

-**Combinazioni totali**: 432 * 55 = 23.760 combinazioni di sguardo-camera per soggetto.

-**Movimentazione**: lo script sposta la camera lungo vertici di una semisfera e utilizza il rig degli occhi per orientare gli occhi del modello nelle direzioni desiderate.

-**Salvataggio dati**: ogni combinazione generata viene registrata in un file CSV. Ogni riga del CSV corrisponde a una configurazione unica (posizione camera + direzione sguardo), con intestazioni iniziali che identificano i landmark.

-**Landmark MediaPipe**: gli indici dei punti chiave del volto (occhi, ciglia, contorni, ecc.) vengono convertiti dagli indici interni di Blender agli indici standard di MediaPipe Face Mesh (che definisce 468 punti 3D del volto)
github.com
.

### Strumenti

-**Blender**: ambiente di modellazione 3D e rendering, con scripting Python integrato. È lo strumento principale usato per posizionare camera e occhi e generare le immagini.

-**Python**: linguaggio di scripting usato all’interno di Blender (via bpy) per automatizzare la generazione di tutte le pose e salvare i dati.

-**MB-Lab**: add-on di Blender (basato su Manuel Bastioni Lab) che permette di creare facilmente personaggi umani 3D con pochi click
blender-addons.org. Viene usato per generare i modelli di testa sui quali ruotare lo sguardo.

### Installazione ed esecuzione

Per eseguire lo script seguire questi passi:

1-Aprire il file .blend incluso nel progetto con Blender.

2-Nella sezione Scripting di Blender, caricare il codice Python fornito.

3-Aprire la Console di sistema di Blender (es. dal menu Window > Toggle System Console) per monitorare l’andamento dello script.

4-Avviare lo script (premere Run Script). Il processo è complesso e richiede diverse ore per completare tutte le combinazioni.

5-Al termine dell’esecuzione, i file CSV saranno salvati nella stessa cartella del file .blend.

### Output

Lo script genera come output un file CSV. Quindi in totale vengono prodotti 6 file CSV (uno per ciascuno dei 6 modelli). Ogni file contiene 23.760 righe (una per ogni combinazione di sguardo e camera), più una riga di intestazione all’inizio. Le colonne del CSV includono gli identificatori dei landmark e le loro coordinate secondo la corrispondenza a MediaPipe. I file CSV risultanti possono essere usati per addestrare e valutare algoritmi di stima dello sguardo.
