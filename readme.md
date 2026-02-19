# Analiza i Rekonstrukcja Symulacji Kalorymetru LUXE

Projekt ten koncentruje się na analizie danych z symulacji Monte Carlo  dla elektromagnetycznego kalorymetru  typu wolfram-krzem, będącego częścią eksperymentu **LUXE (Laser Und XFEL Experiment)**.

Celem pracy jest opracowanie algorytmu rekonstrukcji parametrów cząstek (pozytonów) wpadających do detektora, a następnie zbadanie precyzji tego algorytmu w funkcji energii wiązki.

Głównym zadaniem było przekształcenie surowych odczytów energii z pikseli detektora w konkretne wielkości fizyczne:
1. **Rekonstrukcja przestrzenna $(x, y)$:** wyznaczenie punktu uderzenia cząstki w detektor.
2. **Rekonstrukcja kątowa $(\theta)$:** odtworzenie trajektorii lotu cząstki i kąta padania poprzez analizę śladu kaskady w głąb detektora.

##  Zawartość repozytorium

Analiza została podzielona na dwa główne notatniki

### 1. `Introduction.ipynb` (wstęp teoretyczny)
Ten notatnik stanowi wprowadzenie merytoryczne do projektu. Zawiera:
* Opis fizyki kaskad elektromagnetycznych.
* Szczegółową specyfikację geometrii detektora (układ warstw wolfram-krzem, wymiary sensorów, przeliczanie pikseli na mm).
* Definicję problemu badawczego

### 2. `Analysis.ipynb` (kod i wyniki)
Główny plik z kodem w języku Python. Zawiera implementację algorytmów i wizualizację wyników:
* **Etap I (Kalibracja):** optymalizacja parametru odcięcia szumu $E_{cut}$ dla danych referencyjnych (`output_0`).
* **Etap II (Analiza kątowa):** rekonstrukcja trajektorii dla danych z rozmyciem kątowym (`output_10`, `output_20`) przy użyciu algorytmu klasteryzacji oraz ważonego dopasowania liniowego.
* **Wnioski:** Badanie zależności między energią wiązki, głębokością penetracji kaskady a niepewnością pomiarową.

## Kluczowe wyniki

W toku analizy udowodniono, że precyzja rekonstrukcji jest silnie skorelowana z energią cząstki oraz głębokością penetracji kaskady w detektorze. Dzięki optymalizacji algorytmu uzyskano bardzo wysoką rozdzielczość:
* Dla wysokich energii (**20 GeV**) kaskada dociera niemal do samego końca kalorymetru (średnio >23 aktywne warstwy). Długie ramię pomiarowe pozwala na stabilne dopasowanie trajektorii, co skutkuje wysoką precyzją kątową na poziomie **$\sigma_\theta < 1.8^\circ$**.
* Dla niskich energii (**2.5 GeV**) mniejsza gęstość cząstek wtórnych i krótszy zasięg (~18.5 warstwy) ograniczają stabilność dopasowywanego toru, zwiększając niepewność do poziomu **$\sigma_\theta \approx 5.3^\circ - 5.6^\circ$**.




