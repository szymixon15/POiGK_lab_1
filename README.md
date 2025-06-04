# Wprowadzone zmiany w grze
- Zróżnicowane kolory albedo: Dodałeś jaskrawe kolory (czerwony, zielony, niebieski) w zależności od indeksu kuli, co zwiększa wizualną różnorodność sceny.
- Zwiększona szansa na odbicie lustrzane (specularChance): Wartość rośnie od 0.1 do 0.5 w zależności od pozycji kuli, co sprawia, że kule są bardziej błyszczące w miarę postępu.
- Zmienny IOR: Wprowadziłeś zakres IOR od 1.05 do 1.75, co daje bardziej zróżnicowane efekty załamania światła.
- Dynamiczny kolor refrakcji: refractionColor zmienia się w zależności od progress, co symuluje różne właściwości absorpcji światła.
- Dynamiczne oświetlenie emisyjne: Dodałem delikatną emisję światła (emissive) dla kul w scenie 0, która zmienia się w czasie (sin(time + sphereIndex)) i zależy od pozycji kuli (progress). To sprawia, że kule delikatnie świecą, co jest szczególnie - widoczne w ciemniejszych obszarach sceny.
- Szachownica na podłodze: Zastąpiłem jednolitą podłogę wzorem szachownicy, używając mod na współrzędnych x i z punktu trafienia promienia. Dodatkowo dodałem niewielką szansę na odbicie lustrzane (specularChance = 0.05f), aby podłoga miała subtelny połysk.
- Efekt rozmycia ruchu: Wprowadziłem delikatne przesunięcie pozycji kul w osi X (motionOffset), zależne od czasu i indeksu kuli, co symuluje subtelny ruch i dodaje dynamiki do sceny.
- Dynamiczna zmiana koloru: W scenie 0 dodałem efekt zmiany koloru dla albedo i refractionColor kul, który jest zależny od czasu (FrameIndex * 0.02f) oraz indeksu kuli (sphereIndex * 0.5f dla przesunięcia fazowego). Użyłem funkcji sin i cos z różnymi przesunięciami fazowymi dla każdej składowej RGB, aby stworzyć płynne przejścia kolorystyczne:
  - albedo: Kolory oscylują w zakresie [0, 1] dla każdej składowej RGB, tworząc efekt pulsowania między różnymi odcieniami.
  - refractionColor: Kolory absorpcji zmieniają się w synchronizacji z albedo, ale są dodatkowo modulowane przez progress, aby zachować oryginalną ideę zróżnicowania absorpcji wzdłuż linii kul.
- Dynamiczna zmiana rozmiaru kul: Dodałem efekt pulsowania rozmiaru kul w scenie 0, zmieniając promień (radius) każdej kuli w funkcji TestSphereTrace. Promień oscyluje między 2.0 a 3.6 (bazowy promień 2.8 ± 0.8) w zależności od czasu (FrameIndex * 0.02f) i indeksu kuli (sphereIndex * 0.7f). Użyłem funkcji sin z przesunięciem fazowym dla każdej kuli, aby efekt był zróżnicowany.
  - Wzór: radius = 2.8f + 0.8f * sin(time + float(sphereIndex) * 0.7f)
  - Efekt wizualny: Kule będą się powiększać i zmniejszać, tworząc wrażenie "oddychania", co jest bardzo zauważalne, zwłaszcza w połączeniu z ruchem (motionOffset), zmianą kolorów i emisją światła.
  
# Efekt końcowy
Kule teraz pulsują rozmiarem, zmieniają kolory, delikatnie się poruszają i emitują światło, co sprawia, że scena jest bardzo dynamiczna i przyciąga wzrok. Szachownica na podłodze dodatkowo podkreśla efekty świetlne dzięki delikatnej 
refleksyjności. Tło sceny może odbijać się od kul, wzmacniając efekt lustrzanych odbić i dodając głębi wizualnej.

# Filmik przedstawiający krótką wizualizacje

https://github.com/user-attachments/assets/70638f7e-7b1d-494e-810a-84cddd805d49

