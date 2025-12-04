# 📘 README – Etapa 3: Analiza și Pregătirea Setului de Date pentru Rețele Neuronale

**Disciplina:** Rețele Neuronale  
**Instituție:** POLITEHNICA București – FIIR  
**Student:** Savu Vladut George  
**Data:** 20.11.2025  

---

## Introducere

Acest document descrie activitățile realizate în **Etapa 3**, în care se analizează și se preprocesează setul de date necesar proiectului „Rețele Neuronale". Scopul etapei este pregătirea corectă a datelor pentru instruirea modelului RN, respectând bunele practici privind calitatea, consistența și reproductibilitatea datelor.

---

##  1. Structura Repository-ului Github (versiunea Etapei 3)

```
project-name/
├── README.md
├── docs/
│   └── datasets/          # descriere seturi de date, surse, diagrame
├── data/
│   ├── raw/               # date brute
│   ├── processed/         # date curățate și transformate
│   ├── train/             # set de instruire
│   ├── validation/        # set de validare
│   └── test/              # set de testare
├── src/
│   ├── preprocessing/     # funcții pentru preprocesare
│   ├── data_acquisition/  # generare / achiziție date (dacă există)
│   └── neural_network/    # implementarea RN (în etapa următoare)
├── config/                # fișiere de configurare
└── requirements.txt       # dependențe Python (dacă aplicabil)
```

---

##  2. Descrierea Setului de Date

### 2.1 Sursa datelor

* Origine: Set de date public de imagini, destinat antrenării unui model de Clasificare a vehiculelor.
* Modul de achiziție: Fișier extern
* Perioada / condițiile colectării: Nu este specificat, dar setul de date trebuie să fie divers (varietate de unghiuri, iluminare zi/noapte, condiții meteo) pentru a asigura robustetea modelului CNN.

### 2.2 Caracteristicile dataset-ului

* **Număr total de observații:** 9211
* **Număr de caracteristici (features):** 640x640
* **Tipuri de date: Imagini si Numerice**
* **Format fișiere:** JPG, TXT

### 2.3 Descrierea fiecărei caracteristici

|-------------------|---------|-------------|--------------------------|--------------------|
| **Caracteristică**| **Tip** | **Unitate** |       **Descriere**      | **Domeniu valori** |
|-------------------|---------|-------------|--------------------------|--------------------|
|	            |         | 	    |                          |		    |
|  Imagine Vehicul  |  Input  |   Pixeli    |Sursa principală de date, |      640x640       |
|	            |         | 	    |cu rezoluție uniformă.    |		    |
|-------------------|---------|-------------|--------------------------|--------------------|
|	            |         | 	    |                          |		    |
|   Etichetă YOLO   |  Label  |  Normalizat |Index clasă, x_center,    |       [0-4]        |
|                   |         |             |y_center, lățime, înălțime|                    |
|-------------------|---------|-------------|--------------------------|--------------------|


**Fișier recomandat: `data/README.md`**

---

##  3. Analiza Exploratorie a Datelor (EDA) – Sintetic

### 3.1 Statistici descriptive aplicate

* **Rezoluția imaginii:** Uniformă (640 x 640 pixels)
* **Distribuția pe Clase:** Analiza frecvenței Indexurilor de Clasă (0, 1, 2, 3, 4) în întregul set.
* Histograme

### 3.2 Analiza calității datelor

* **Detectarea etichetelor inconsistente sau eronate**
* **Identificarea imaginilor neclare sau obstruate**

### 3.3 Probleme identificate

*

---

##  4. Preprocesarea Datelor

### 4.1 Curățarea datelor

* **Eliminare duplicatelor**
* **Tratarea imaginilor corupte/outlier:** Eliminarea imaginilor neclare sau cu etichete YOLO eronate.

### 4.2 Transformarea caracteristicilor

* **Extracția Etichetei **
* **Redimensionare: ** Imaginile de 640 x 640 vor fi redimensionate la o dimensiune standardizată pentru CNN.
* **Normalizare (Min–Max): ** Scalarea valorilor pixelilor de la 0-255 la 0-1.

### 4.3 Structurarea seturilor de date

**Împărțire**
* 70% – train
* 15% – validation
* 15% – test

**Principii respectate:**
* **Stratificare pentru clasificare: ** Împărțirea se face pe baza Clasei Dominante obținute, menținând proporțiile.
* **Fără scurgere de informație: ** Parametrii de normalizare se calculează DOAR pe setul de train.

### 4.4 Salvarea rezultatelor preprocesării

* Date preprocesate în `data/processed/`
* Seturi train/val/test în foldere dedicate, organizate după Clasa Dominantă (ex: `data/train/Autoturism/`)

---

##  5. Fișiere Generate în Această Etapă

* `data/raw/` – date brute
* `data/processed/` – imaginile și etichetele finale
* `data/train/`, `data/validation/`, `data/test/` – seturi finale
* `src/preprocessing/` – codul Python care implementează logica de simplificare YOLO -> Clasificare
* `data/README.md` – descrierea dataset-ului
* `requirements.txt` - dependente Python

---

##  6. Stare Etapă (de completat de student)

- [ ] Structură repository configurată
- [ ] Dataset analizat (EDA realizată)
- [ ] Date preprocesate
- [ ] Seturi train/val/test generate
- [ ] Documentație actualizată în README + `data/README.md`

---


# 📘 README – P3: Proiect SAF - Diagram State Machines

**Disciplina:** Sisteme Avansate de Fabricare  
**Instituție:** POLITEHNICA București – FIIR  
**Student:** Savu Vladut George  
**Data:** 04.12.2025  
---

## Scopul Etapei P3

Această etapă corespunde punctului **3. Dezvoltare proiect software** - slide 10 **SAF - Specificatii proiect.pdf**.

**Trebuie să livrați un SCHELET COMPLET și FUNCȚIONAL al întregului Sistem Ciber-Fizic.**


##  Livrabile Obligatorii

### 1. Tabelul Nevoie Reală → Soluție CPS → Modul Software (max ½ pagină)

| **Nevoie reală concretă** |   **Cum o rezolvă SIA-ul vostru**  | **Modul software responsabil** |
|---------------------------|------------------------------------|--------------------------------|
|   Reducerea timpului de   |  Identificare automată a tipului   |    **AI Prediction Service**   |
|   așteptare la barieră    |     de vehicul în < 1 secundă      | (`predictor.py` + MobileNetV2) |
|   Aplicarea automată a    | Decizie instantanee de acces și    |   **Decision Logic Module**    | 
|  politicilor de taxare    |calcul taxă pe baza clasei detectate|    (`decision_logic.py`)       |
|  Auditarea traficului și  | Înregistrarea automată (Timestamp, |**Data Logging & Web Dashboard**|
|     statistici pentru     |   Tip, Decizie) și generarea de    |     (`app.py` + CSV Logs)      |
|  managementul campusului  |   statistici lunare în timp real   |                                |


---


### 2. Diagrama State Machine a Întregului Sistem (OBLIGATORIE)

**Cerințe:**
- **Minimum 4-6 stări clare** cu tranziții între ele
- **Formate acceptate:** PNG/SVG, pptx, draw.io 
- **Legendă obligatorie:** 1-2 paragrafe în acest README: "De ce ați ales acest State Machine pentru nevoia voastră?"


**Exemple concrete per domeniu de inginerie:**

#### Clasificare imagini defecte/producție
```
IDLE (Așteptare vehicul) 
   ↓ [Senzor prezență / Upload UI]
ACQUIRE_IMAGE (Captură foto & Decodare Base64)
   ↓
VALIDATE_IMAGE (Verificare format & rezoluție)
   ├─ [Invalid/Corupt] → LOG_ERROR → DISPLAY_ERROR → IDLE
   └─ [Valid] → PREPROCESS (Smart Crop, Resize 224x224, Normalizare RGB)
                  ↓
              RN_INFERENCE (MobileNetV2 Forward Pass)
                  ↓
              CHECK_CONFIDENCE (Prag > 75%)
                  ├─ [Low Confidence] → TRIGGER_MANUAL_CHECK (Alertă Pază) → LOG_WARNING → IDLE
                  └─ [High Confidence] → IDENTIFY_CLASS (Ex: "Autoturism")
                                           ↓
                                     APPLY_POLICY (Verificare Reguli & Calcul Taxă)
                                           ↓
                                     LOG_TRANSACTION (CSV + Update Contor Lunar)
                                           ↓
                                     UPDATE_UI & ACTUATE_BARRIER (Deschide/Închide)
                                           ↓
                                         IDLE
```
**Legendă obligatorie (scrieți în README):**
```markdown
### Justificarea State Machine-ului ales:

Am ales o arhitectură de tip "Event-Driven Classification Loop" pentru că proiectul meu vizează automatizarea accesului într-un campus universitar, unde latența deciziei și acuratețea sunt critice. Sistemul nu monitorizează continuu un semnal, ci reacționează instantaneu la prezența unui vehicul (upload imagine).

Stările principale sunt:
1. [ACQUIRE_IMAGE] & [PREPROCESS]: Modulul Web (app.py) primește imaginea brută și o trimite la predictor.py, unde aplicăm Smart Cropping (bazat pe coordonate YOLO simulate) și redimensionarea la 224x224 RGB
2. [RN_INFERENCE]: Rularea modelului antrenat pentru a obține vectorul de probabilități pentru cele 6 clase
3. [DECISION_LOGIC]: Această stare transformă ieșirea brută a AI-ului într-o decizie de business. Aici interogăm dicționarul de politici (decision_logic.py) pentru a stabili dacă vehiculul are drept de acces și ce taxă se aplică

Tranzițiile critice sunt:
- [RN_INFERENCE] → [CHECK_CONFIDENCE]: Aceasta este cea mai importantă măsură de siguranță. Dacă modelul nu este sigur (confidență < 75%), sistemul NU ia o decizie automată, ci trece într-o stare de MANUAL_CHECK, prevenind accesul neautorizat sau taxarea eronată.
- [APPLY_POLICY] → [ACTUATE_BARRIER]: Tranziția finală care leagă lumea digitală de cea fizică, condiționată de validarea regulilor de acces.

Starea [LOG_WARNING] / [MANUAL_CHECK] este esențială deoarece modelele de vedere artificială pot fi influențate de condiții meteo nefavorabile (ploaie, noapte). În loc să respingem automat un vehicul (ceea ce ar crea cozi), sistemul solicită intervenția umană doar în cazurile incerte, menținând fluiditatea traficului pentru restul de 90%+ cazuri clare.
```


---

## Checklist Final – Bifați Totul Înainte de Predare

### Documentație și Structură
- [x] Tabelul Nevoie → Soluție → Modul complet (minimum 2 rânduri cu exemple concrete completate in README_Etapa4_Arhitectura_SIA.md)
- [x] Diagrama State Machine creată și salvată și postată alături de acest readme pe moodle la P3. State Machine pentru proiectul SAF
- [x] Legendă State Machine scrisă în acest readme (minimum 1-2 paragrafe cu justificare) 

