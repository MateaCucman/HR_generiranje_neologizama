# HR_generiranje_neologizama
Projekt za OPJ: Generiranje neologizama pomoću ByT5 modela.
Generiranje neologizama iz opisa na hrvatskom jeziku
Ovaj projekt istražuje primjenu metoda dubokog učenja za generiranje novih riječi (neologizama) na temelju njihovih definicija ili opisa. Problem je postavljen kao zadatak nadzirane sumarizacije (engl. supervised summarization) gdje je ulazni podatak opis pojma, a izlazni podatak jedna, novostvorena riječ koja sažima taj koncept.

# Struktura projekta
Projekt je podijeljen u tri ključne faze, od kojih je svaka dokumentirana u zasebnoj Jupyter bilježnici:

Korpus.ipynb (Prikupljanje i obrada podataka)

Sadrži kod za automatizirano struganje podataka (web scraping) s Hrvatskog jezičnog portala (HJP) pomoću biblioteke BeautifulSoup.

Uključuje čišćenje teksta, normalizaciju i integraciju specifične baze neologizama.

Rezultira podjelom skupa podataka na train, dev i test skupove (ukupno preko 30,000 uzoraka).

ByT5-small.ipynb (Glavni model)

Implementacija i dotreniravanje (fine-tuning) ByT5-small modela (arhitektura na razini znakova/bajtova).

Model je odabran zbog svoje robusnosti u radu s morfološki bogatim jezicima poput hrvatskog.

Sadrži proces treniranja, praćenje funkcije gubitka i generiranje riječi pomoću tehnika uzorkovanja (top_k, top_p).

Baseline.ipynb (Referentni model i evaluacija)

Implementacija LSTM Sequence-to-Sequence modela koji služi kao osnova (baseline) za usporedbu.

Sadrži detaljnu evaluaciju oba modela koristeći metrike:

3-gram F1 score (strukturna sličnost).

Semantic Similarity (semantička sličnost pomoću Sentence-BERT modela).

Cross-Entropy Loss.

# 📊 Rezultati
Glavni model (ByT5) pokazao je značajnu nadmoć nad klasičnim LSTM modelom, posebno u zadržavanju semantičkog smisla i pravilne hrvatske morfologije.
| Model | Cross Entropy | 3-gram F1 | Semantic Similarity |
| :--- | :---: | :---: | :---: |
| **Baseline (LSTM)** | 2.8086 | 0.0255 | 0.6460 |
| **ByT5-small** | **1.0090** | **0.2748** | **0.7503** |

# 🛠️ Instalacija i korištenje
Da biste pokrenuli projekt lokalno, osigurajte da imate instaliran Python 3.8+ i potrebne biblioteke:

Pokrenite Korpus.ipynb za generiranje CSV datoteka s podacima.

Pokrenite ByT5-small.ipynb za treniranje glavnog modela.

# 👉 Projekt.pdf
Za usporedbu rezultata pokrenite Baseline.ipynb.
