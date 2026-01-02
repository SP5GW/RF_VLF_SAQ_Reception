<p align="center">
<img src="./img/IMG_2358.jpg" width="800" height="600"/>
</p> 

# Wprowadzenie
Pomysł przeprowadzenia odbioru sygnału emitowanego przez szwedzką stację SAQ nadającą spod Geteborga pojawił się przed ponad rokiem. Gdy pierwsza próba odbioru z wykorzystaniem anteny aktywnej miniwhip zakończyła się niepowodzeniem, postanowiłem spróbować ponwnie, ale tym razem wykorzystując przedwzmacniacz opisany na stronach Towarzystwka Przyjaciół Grimeton SAQ [1] w połączeniu z anteną magnetyczną.
Wyniki tego eksperymentu oraz wyzwania przed jakimi stanąłem w trakcie jego realizacji opisałem w poniższym artykule.
Źródłem inspiracji do ponownego zmierzenia się z problematyką odbioru sygnałów VLF (Very Low Frequencies) oraz cennych uwag w trakcie przygotowań był kolega Jacek Lipkowski, SQ5BPF. Dziękuję Jacku!

# Antena

## Konstrukcja Anteny

<p align="center">
<img src="./img/antenna/IMG_2331.jpg" width="400" height="300"/>
<img src="./img/antenna/IMG_2336.jpg" width="400" height="300"/>
</p>
*Zdjęcia 1 i 2: Konstrukcja mechaniczna anteny pętlowej. Indukcyjność anteny to 24.7mH a nie tak jak na rysunku 24.7nH!*

Podczas pierwszej próby odbioru sygnału SAQ posłużyłem się anteną aktywną typu miniwhip podłączoną do odbiornika RSP1A z oprogramowaniem SDRUno [3] konstrukcja tej anteny została opisana w [2], w moim przypadku poziom zakłóceń całkowicie uniemożliwił odbiór sygnałów SAQ czy DCF-77 mimo, że na pasmach amatorskich 80m i 40m antena sprawowała się znakomicie. Dodawanie tłumików prądów błądzących czy poprawa jakości uziemienia stacji odbiorczej nie przyniosły znaczącej poprawy. 

Śledząc tematykę odbioru sygnałów VLF można zauważyć, że najbardziej popularnymi typami anten dla tych długości fal są anteny pętlowe i miniwhip. Antena pętlowa reaguje na składową magnetyczną fali radiowej co czyni ją bardziej odporną na zakłócenia przemysłowe, ponadto magnetyczna antena pętlowa cechuje się dużą kierunkowością co pomaga w zminimalizowaniu zakłóceń przez właściwą orientację anteny względem źródła nieporzadanej emisji. Antena miniwhip, którą wykorzystałem podczas nieudanej próby reaguje z kolei na składową elektryczną i dlatego wykazuje dużą wrażliwość na zakłócenia przemysłowe (których źrodłem mogą być np. stacje transformatorowe lub zasilacze impulsowe).  

Antenę pętlową zbudowałem na ramie drewnianej w kształcie kwadratu o boku 80cm. Uzwojenie anteny to 80 zwojów drutu o średnicy 0.2mm nawiniętego na plastikowe prowadnice [4] przymocowane do drewnianej ramy (indukcyjność: 2.45mH, rezystancja: 68 omów). Antena nie posiada kondensatora strojeniowego, ponieważ obwód rezonansowy zestrojony na częstotliwość SAQ jest częścią układu przedwzmacniacza. Wymiary anteny są znacząco mniejsze od długości fal z zakresu VLF i dlatego nie są krytyczne. Wybór długości boku został podyktowany głównie walorami praktycznymi takimi jak swoboda przemieszczania anteny pomiędzy różnymi lokalizacjami.

Warto też wspomnieć, że wybór pomiędzy anteną pętlową a aktywną anteną miniwhip w dużej mierze zależy od warunków panujących w danej lokalizacji. W przypadku obszarów miejskich o potencjalnie dużym poziomie zakłóceń przemysłowych bardziej optymalnym wyborem wydaje się być antena pętlowa. W warunkach wiejskich antena miniwhip ze względu na wysoką czułość oraz niski poziom zakłóceń występujących w takim środowisku może być znakomitym wyborem.

W praktyce odbiór sygnału SAQ w obszarze miejskim przy wykorzystaniu anteny miniwhip jest jak najbardziej możliwy, oczywiście przy założeniu niskiego poziomu zakłóceń wstępujących w danej lokalizacji (przypadek Jacka SP5PBE, który z powodzeniem wykorzystuje antenę miniwhip).

## Orientacja Anteny względem radiostacji SAQ

Orientacja anteny nie wymaga specjalistycznego sprzętu i może zostać wykonana zgróbnie przy użyciu aplikacji kompasa dostępnej w telefonach komórkowych (pamiętajmy o odznaczeniu opcji "true north" jeśli taka opcja występuje w naszej aplikacji). W moim przypadku użyłem GPS Compass dostępnej dla systemu iOS. Koordynaty lokalizacji anteny odnalazłem na stronie [4], 

<p align="center">
<img src="./img/antenna_positioning/coordinates.png" width="400" height="300"/>
</p>
* Zdjęcia 3: Strona internetowa, która wylicza koordynaty lokalizacji o podanym adresie. *

zaś azymut na który musiałem skierować antenę odczytałem z mapy, którą można wygenerować pod adresem [5].

<p align="center">
<img src="./img/antenna_positioning/AzimuthMap.png" width="400" height="300"/>
</p>
* Zdjęcia 4: Strona internetowa, która umożliwia storzenie mapy azymutów. *
  
W sytuacji gdy w naszej lokalizacji wystęuje silne źródło zakłóceń kierunkowych warto rozważyć takie ustawienie, które skutkuje najwyższym współczynikiem sygnału do szumu co nie zawsze będzie tożsame z najwyższym poziomem odbieranego sygnału porządanego.

# Przedwzmacniacz

## Budowa przedwzmacniacza

Konstrukcja przedwzmacniacza została opisana na stronach Stowarzyszenia Przyjaciół Aleksandra Grimetona [1][6]. W ramach tego projektu wprowadziłem następujące modyfikacje:

<p align="center">
<img src="./img/preamp/preamp_schematics.jpeg" width="800" height="600"/>
</p>
* Zdjęcia 4 Schemat ideowy przedwzmacniacza wraz z układem monitorowania zasilania. *

1) Kondensatory odsprzęgające 1uF zostały zastąpione parami kondensatorów 100n oraz 10u
2) Uzwojenie wtórne transformatora wejściowego T1 zwiększono z 90 do 100 zwojów drutu o średnicy 0.2mm
3) Dodano wyjście sma-c w celu łatwiejszego przyłącznia odbiornika SDR takiego jak np. RSP1A [3], w przypadku współpracy przedwzmacniacza z odbiornikiem SDR nie jest wymagany dodatkowy tłumik sygnału, Funkcję tę realizuje filtr górnoprzepustowy utworzony przez elementy C10 (100 nF) oraz rezystor R9 (1 kΩ), pracujący z równoległym obciążeniem w postaci impedancji wejściowej odbiornika SDR (50 Ω). Po dołączeniu odbiornika SDR, charakteryzującego się znacznie niższą impedancją wejściową niż wejście liniowe karty dźwiękowej komputera PC, częstotliwość graniczna filtru ulega przesunięciu w kierunku niższych częstotliwości, co skutkuje efektywnym obniżeniem poziomu sygnału doprowadzanego do obciążenia o około 10 dB.
4) Baterie 4V zastąpiono bardziej dostępnymi bateriami 9V.
5) Dodano proste układy monitorujące stan baterii oparte o tranzystor BC546 oraz diody zabezpieczające przed niewłaściwą polaryzacją. W przypadku obniżenia napięcia zasilania poniżej 8,11V kolor diod LED D3/D4 zmienia się z zielonego na czerwony.

<p align="center">
<img src="./img/preamp/IMG_2328.jpg" width="800" height="600"/>
</p>
<p align="center">
<img src="./img/preamp/IMG_2355.jpg" width="400" height="300"/>
<img src="./img/preamp/IMG_2357.jpg" width="400" height="300"/>
</p>
* Zdjęcia 5,6,7 Konstrukcja mechaniczna układu przedwzmacniacza. *

Jak można zauważyć w oparciu o powyższe ilustracje, wzmacniacz nie wprowadza tłumienia, poza pasmem przenoszwenia obwodu rezonansowego, co można z powodzeniem wykorzystać do odbioru stacji innych niż SAQ nadających na częstatliwościach nawet z zakresu fal długich. Prezentowany układ pozwalił np. na stabilny odbiór sygnałów synchronizacji czasu NPL (60khz) oraz DCF-77 (77.5kHz). W tej samej lokalizacji odbiór tych sygnałów był bardzo niestabilny, a często nawet niemożliwy przy użyciu anteny typu "random wire" (w tym konkretnym przypadku długość elementu odbiorczego wynosiła ok. 13m) czy miniwhip.

## Strojenie przedwzmacniacza

Do zestrojenia wzmacniacza na częstotliwość SAQ 17,2 kHz nie jest wymagane użycie specjalistycznej aparatury pomiarowej. Oczywiście możliwe jest wykorzystanie generatora funkcyjnego oraz oscyloskopu, jednak wystarczającą dokładność zapewnia obserwacja poziomu wzmocnienia szumów tła pochodzących z wejścia przedwzmacniacza pozostawionego bez podłączonej anteny. Jeżeli maksimum poziomu szumów występuje w pobliżu częstotliwości SAQ, można uznać, że układ został prawidłowo zestrojony. Należy przy tym uwzględnić, że obwód rezonansowy charakteryzuje się stosunkowo wąskim pasmem przenoszenia — w przedstawionej implementacji wynoszącym około 200 Hz — co wymaga dość precyzyjnego dostrojenia układu.

W przypadku strojenia przy użyciu generatora funkcjonalnego należy pamiętać o właściwym odseparowaniu generatora od układu przedwzmacniacza, aby w trakcie strojenia częstotliwość rezonansu nie uległa zmianie w wyniku przełączania źródła sygnału pomiędzy generatorem a anteną. Dobrym rozwiązaniem jest użycie krótkiej anteny podłączonej do wyjścia generatora (dwa niepołączone ze sobą kable o długości ok. 10-15cm) znajdującego się w pobliżu przedwzmacniacza lub przyłączenie generatora do układu przedwzmacniacza przez rezystor o dużej oporności np. 100komów. 

<p align="center">
<img src="/img/preamp/NoInputSignal_Decimation32_SDR_Uno.png" width="600" height="400"/>
</p>
* Zdjęcia 8 Widmo sygnału na wyjściu przedwzmacniacza z odłączoną anteną. *

### Preamplifier performance

<p align="center">
<img src="./img/preamp/preamp_bandwidth.png" width="600" height="400"/>
</p>
* Zdjęcia 8 Pasmo przenoszenia przedwzmacniacza wyznaczone na podstawie rzeczywistych danych pomiarowych. *

<p align="center">
<img src="./img/preamp/Gain_measurement.png" width="600" height="600"/>
</p>

* Zdjęcia 8 Oszacowanie wzmocnienia układu w obszarze rezonansu obwodów wejściowych. *


## Potencjalne problemy do uniknięcia

1) Brak kondensatorów odsprzęgających może skutkować wzbudzaniem się układu wzmacniaczy operacyjnych co w skrajnym przywadku może doprowadzić nawet do ich uszkodzenia w skótek przegrzania się. Efekt może występować poza zakresem częstotliwości VLF i nie być bezpośrednio widocznym na osyloskopie czy wodospadzie odbiornika SDR ustawionego na monitorowanie częstotliwości VLF (tak straciłem jeden z układów na kilka dni przed planowaną emisją...)

2) Strojenie za pomocą generatora funkcyjnego bezpośrednio przyłączonego do układu wejściowego przedwzmacniacza  prowadzi do zmiany charakterystyki obwodu i w efekcie przesunięcia częstotliwości rezonansu w porównaniu do sytuacji, w której obciążeniem uzwojenia pierwotnego jest antena. Jest to podyktowane faktem, że impedancja uzwojenia pierwotnego z szeregowo przyłączoną niską impedancją generatora sygnałowego (o charakterze mocno rezystancyjnym) istotnie wpływa na reaktancję obwodu rezansowego, podwyższając jego częstotliwość rezonansową. 
 
Początkowo nie byłem świadomy występowania tego zjawiska. W konsekwencji, w celu uzyskania maksimum wzmocnienia przy częstotliwości 17,2 kHz przy podłączonym generatorze, do kondensatora C2 (8,2 nF) dołączyłem równolegle dodatkowy kondensator o pojemności 22 nF. Jak jednak pokazuje przedstawiona poniżej symulacja oraz potwierdzają wyniki pomiarów, po odłączeniu generatora i zastąpieniu go anteną, rzeczywista częstotliwość rezonansowa obwodu ulegała istotnemu obniżeniu.

<p align="center">
<img src="./meas/_30dBmInputSignal_Decimation32_34_2nF_SDR_Uno.png" width="400" height="300"/>
<img src="./img/measurement_issue/measurement_issue.png" width="600" height="400"/>
</p>
* Zdjęcia 9 Oszacowanie wzmocnienia układu w obszarze rezonansu obwodów wejściowych. *
* Zdjęcia 10 Oszacowanie wzmocnienia układu w obszarze rezonansu obwodów wejściowych. *
  
Usunięcie dodatkowego kondensatora 22nF, pozwoliło na uzyskanie poprawnego zestrojenia układu na częstotliwość 17.2kHz z przyłączoną anteną.

<p align="center">
<img src="./meas/_30dBmInputSignal_Decimation32_2n2_SDR_Uno.png" width="400" height="300"/>
</p>

Podczas testów sygnał SAQ był symulowany przez nośną z generatora sygnałowego do którego wyjścia przyłączony został przewód pełniący rolę prostej anteny. Poziom sygnału wyjściowego generatora w tym scenariouszu testowym był ustawiony na maksymalną wartość.

# Oprogramowanie

Układ przedwzmacniacza może współpracować zarówno z kartą dźwiękową PC jak też odbiornikiem SDR zdolnym do odbioru sygnałów w zakresie VLF (np. moduł RSP1A firmy SDRPlay). 
W przypadku odbioru z wykorzystaniem karty dźwiękowej bardzo dobrze sprawdziło się oprogramowanie SAQrx dostępne na stronie Towarzystwka Przyjaciół Grimeton SAQ [1]:

<p align="center">
<img src="./img/software_options/saqrx 2026-01-01 235010.png" width="400" height="300"/>
</p>

oraz oprgramwanie Spectrum Lab autorstwa Wolfganga Bueschera, DL4YHF rekomendowane przez Jacka SQ5BPF:

<p align="center">
<img src="./img/software_options/spectrum_lab 2026-01-01 234459.png" width="600" height="400"/>
</p>

Zaletą pakietu spectrumlab jest dostępność funkcji wodospadu.

W przypadku odbioru z wykorzystaniem układu SDR wybór oprogramowania jest bardzo zależny od wykorzystywanej platformy sprzętowej. W przypadku RSP1A, najepszym wyborem wydaje się oprogramowanie rozwijane przez dostawcę sprzętu czyli program SDRUno.

<p align="center">
<img src="./img/software_options/sdr_uno 2026-01-01 234807.png" width="600" height="400"/>
</p>


# Jakość odbioru a typ anteny

Niniejsze porównanie zostało wykonane w obszarze miejskim o stosunkowo silnym poziomie zakłóceń przemysłowych (zasilacze impulsowe, stacja transformatorowa oddalona od anten nie dalej niż o 80m, stacja bazowa telefonii komórkowej oddalona nie dalej niż o 100m). Uzyskane wyniki mogłyby być zupełnie inne dla obszaru wiejskiego.

Ponieważ wielu z nas mieszka w miejscach o zbliżonym poziomie zakłóceń, zdecydowałem się na wykonanie i prezentację pomiarów dla anteny pętlowej oraz miniwhip znajdujących się w niewielkiej odległości od siebie.

Sposób zawieszenia porównywanych anten został pokazany na zdjęciu poniżej:

<p align="center">
<img src="./img/antenna_comparison/AntennaLocation.jpg" width="400" height="300"/>
</p>

## Wyniki dla anteny pętlowej

Od lewej widmo odbieranego sygnału w paśmie VLF, oraz widmo sygnału stacji DCF-77 przy pomocy anteny pętlowej z przyłączonym przedwzmacniaczem:

<p align="center">
<img src="./img/antenna_comparison/loop 2026-01-01 104826.png" width="400" height="300"/>
<img src="./img/antenna_comparison/loop2026-01-01 104710.png" width="400" height="300"/>
</p>

## Wyniki dla anteny miniwhip

Od lewej widmo odbieranego sygnału w paśmie VLF, oraz widmo sygnału stacji DCF-77 przy pomocy anteny miniwhip:

<p align="center">
<img src="./img/antenna_comparison/miniwhip 2026-01-01 104910.png" width="400" height="300"/>
<img src="./img/antenna_comparison/miniwhip 2026-01-01 104612.png" width="400" height="300"/>
</p>

W moim przypadku, odbiór sygnałów w paśmie VLF oraz sygnału synchronizacji czasu DCF-77 był możliwy wyłącznie z wykorzystaniem przedwzmacniacza wraz z anteną pętlową. 

# Podsumowanie

Po roku przygotowań udało się odebrać sygnał stacji SAQ Grimeton. Oprócz samej satysfakcji z odbioru, projekt ten umożliwił mi zdobycie cennego doświadczenia oraz wymianę wiedzy z innymi pasjonatami fal bardzo długich.

Ze względu na regularne emisje stacji SAQ oraz możliwość całorocznych nasłuchów w paśmie 10–250 kHz, opisane rozwiązanie może stanowić dobrą bazę do dalszych eksperymentów.

73 Andrzej SP5GW

<p align="center">
<img src="./img/SAQTransmission.png" width="200" height="600"/>
</p>

# Źródła

[1] Towarzystwo Przyjaciół Grimeton SAQ, https://alexander.n.se/

[2] Antena miniwhip, https://github.com/SP5GW/MiniWhip_Antenna

[3] SDR Play, https://www.sdrplay.com/

[4] Oprogramowanie Spectrum lab autorstwa Wolfganga Bueschera, DL4YHF https://www.qsl.net/dl4yhf/spectra1.html

[5] Ustawienia programu Spectrum Lab dla SAQ  https://www.qsl.net/dl4yhf/speclab/vlf_rcvr.htm

[6] Opis przedwzmacniacza VLF, https://alexander.n.se/en/the-radio-station-saq-grimeton/lyssna-pa-saq/

[7] Opis działania anteny pętlowej autorstwa Williama E. Paynea, N4YWK, http://www.vlf.it/octoloop/rlt-n4ywk.htm

[8] Portal dla entuzjastów VLF, http://www.vlf.it/