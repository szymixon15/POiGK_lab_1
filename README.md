# Właściwości materiałów kul
- Zróżnicowane kolory albedo: W celu zwiększenia wizualnej różnorodności, przypisano kulom jaskrawe kolory (czerwony, zielony, niebieski) w zależności od ich indeksu w scenie.
- Zwiększona szansa na odbicia lustrzane: Wartość parametru specularChance rośnie liniowo od 0.1 do 0.5 w zależności od pozycji kuli. Dzięki temu obiekty stają się bardziej refleksyjne i błyszczące w miarę postępu sceny.
- Zmienny współczynnik załamania światła (IOR): Wprowadzono dynamiczny zakres IOR od 1.05 do 1.75, co pozwala uzyskać bardziej zróżnicowane i realistyczne efekty refrakcji.
- Dynamiczny kolor refrakcji: Parametr refractionColor zmienia się w zależności od postępu (progress), symulując różne właściwości absorpcji światła przez materiał.
- Oświetlenie emisyjne: Dla kul w scenie 0 dodano subtelną emisję światła (emissive). Jej intensywność zmienia się w czasie (sin(time + sphereIndex)) i jest zależna od pozycji kuli (progress), co sprawia, że kule delikatnie świecą, co jest szczególnie widoczne w ciemniejszych obszarach.

# Właściwości materiałów kul 
- Podłoga w szachownicę: Jednolitą powierzchnię podłogi zastąpiono wzorem szachownicy, generowanym proceduralnie z użyciem operacji mod na współrzędnych (x, z) punktu trafienia promienia. Dodatkowo, aby nadać podłodze subtelny połysk, ustawiono dla niej stałą, niską szansę na odbicie lustrzane (specularChance = 0.05f).
- Efekt rozmycia w ruchu: Zaimplementowano delikatne przesunięcie pozycji kul w osi X (motionOffset), zależne od czasu oraz indeksu kuli. Symuluje to subtelny ruch, dodając scenie dynamiki.
- Dynamiczna zmiana koloru: W scenie 0 wprowadzono zaawansowany efekt zmiany kolorów albedo oraz refrakcji. Parametry te są modyfikowane w czasie rzeczywistym w oparciu o czas (FrameIndex) i indeks kuli (sphereIndex), z wykorzystaniem funkcji sin i cos do płynnych przejść między składowymi RGB.
- Dynamiczna zmiana rozmiaru kul: W scenie 0 dodano efekt pulsowania rozmiaru kul poprzez modyfikację ich promienia (radius). Promień oscyluje wokół bazowej wartości 2.8 w zakresie ±0.8, zgodnie ze wzorem: radius = 2.8f + 0.8f * sin(time + float(sphereIndex) * 0.7f) Dzięki zróżnicowaniu fazy dla każdej kuli, efekt jest niesynchroniczny, co tworzy wrażenie „oddychania” obiektów.

# Efekt końcowy
Kule rytmicznie pulsują, płynnie zmieniając swój rozmiar i kolorystykę, a także subtelnie poruszają się i emitują własne światło. Podłoga z wzorem szachownicy, dzięki swojej delikatnej refleksyjności, dodatkowo podkreśla zaawansowane efekty świetlne. Odbijające się w kulach otoczenie wzmacnia efekt lustrzanych odbić, dodając całej kompozycji wizualnej głębi.

# Filmik przedstawiający krótką wizualizacje

https://github.com/user-attachments/assets/70638f7e-7b1d-494e-810a-84cddd805d49

