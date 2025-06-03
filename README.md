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

# Filmik przedstawiający krótką wizualizacje


