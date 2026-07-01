# PrimeNode - Raspberry PI Hotspot System
### Powered by SvxLink | Developed by SQ7UTP

Witamy w oficjalnym repozytorium systemu **PrimeNode**. 
Jest to zaawansowane, lekkie i nowoczesne oprogramowanie dla hotspotów radiowych, oparte na systemie **Raspberry Pi OS** oraz silniku **SvxLink**. Projekt został stworzony od podstaw z myślą o intuicyjnej obsłudze (Dashboard WWW), stabilności (System plików Read-Only/Logi w RAM) oraz elastyczności konfiguracji (Roaming Sieciowy i wsparcie dla różnego hardware'u).
PrimeNode to projekt rozwojowy, tworzony z myślą o prostocie i stabilności – bez zbędnych „wodotrysków”, za to z naciskiem na funkcjonalność. Starałem się pozbyć potencjalnych błędów. Jestem w pełni otwarty na Wasze uwagi, propozycje nowych funkcji oraz konstruktywną krytykę. Projekt ma charakter otwarty, więc jeśli masz pomysł na modyfikację lub usprawnienie kodu – śmiało modyfikuj lub daj znać! Budujmy to rozwiązanie wspólnie.

---

## 📥 GŁÓWNY OBRAZ SYSTEMU / MAIN SYSTEM IMAGE

Gotowy do wgrania obraz systemu (`.img`) znajduje się w sekcji **Releases** po prawej stronie tego repozytorium. Nie musisz kompilować kodu ręcznie – pobierz, wgraj i używaj.

👉 **[PRZEJDŹ DO POBIERANIA / GO TO RELEASES](../../releases)**

### 🛠️ Kompatybilność Sprzętowa / Hardware
* **Komputer:** Raspberry Pi Zero W, Zero 2W, 3, 3B, 3B+, 4
* **Radio:** Płytka **RF Guru** (I2S WM8960), Moduł **SHARI / SA818** **LUB** zewnętrzny radiotelefon podłączony przez kartę dźwiękową USB (CM108) i piny GPIO.
* **Pamięć:** Karta microSD min. 8GB (Zalecane Class 10/A1)

---

## 🚀 Szybki Start / Quick Start

### 🔐 Dane Logowania / Credentials

| Usługa / Service | Login / User | Hasło / Password | Port / Address |
| :--- | :--- | :--- | :--- |
| **Terminal (SSH)** | `root` | `primenode` | 22 |
| **Dashboard WWW** | *(brak / none)* | *(brak / none)* | `http://primenode.local`<br>lub adres IP (LAN IP) |
| **Web Terminal** | `root` | `primenode` | (via Dashboard) |
| **Tryb Ratunkowy AP** | SSID: `PrimeNode_AP` | `primenode123` | `http://192.168.4.1` |

*(Uwaga: Zalecamy zmianę domyślnego hasła `root` po pierwszym zalogowaniu komendą `passwd`)*

---

## ✨ Główne Funkcje / Key Features

System PrimeNode oferuje zestaw zaawansowanych funkcji ułatwiających codzienną pracę z hotspotem (Zaktualizowano do **V1.6**!):

1.  **🌍 System Raportowania APRS:**
    * Twój hotspot może automatycznie wysyłać swoją pozycję oraz parametry radiowe (moc, zysk anteny, wysokość) do ogólnoświatowej sieci APRS-IS.
    * Wbudowany inteligentny konwerter współrzędnych i wybór dedykowanych ikon (np. Węzeł EchoLink, Dom, Samochód).

2.  **🔗 Inteligentna Wyszukiwarka EchoLink:**
    * Wbudowana w zakładkę DTMF szybka wyszukiwarka Live (baza serwerów synchronizuje się w tle).
    * Wpisz minimum 3 znaki, aby w ułamku sekundy przeszukać tysiące aktywnych węzłów na świecie, natychmiast nawiązać połączenie lub zapisać stację w swojej prywatnej książce adresowej.

3.  **💾 Moduł Kopii Zapasowych:**
    * Zabezpiecz swoją pracę! Pobierz pełną konfigurację, dodane sieci, parametry audio i własne przyciski DTMF do jednego pliku ZIP. 
    * Przywróć cały system do działania jednym kliknięciem po zmianie karty pamięci.

4.  **🎛️ Smart Config:**
    * Koniec z ręcznym wpisywaniem numerów grup TG w konfiguracji! Kliknij pole *Startowe TG* lub *Monitorowane TG*, by otworzyć dotykowy panel wyboru, który zaciąga Twoje ulubione grupy prosto z zakładek DTMF.

5.  **📱 Interaktywny DTMF, Książka Adresowa i Zakładki:**
    * Nowoczesny edytor z obsługą **przeciągania kafelków (Drag & Drop)**.
    * Twórz własne, nielimitowane zakładki (np. "Echolink Polska", "Ulubione TG") grupujące przyciski dla Reflektora i EchoLinka w spójną książkę adresową.

6.  **⚡ Szybkie Przełączanie (Quick-Dial) i Wizualizacja TX:**
    * Gdy ktoś nadaje, jego kafelek na liście i znacznik na mapie dynamicznie pulsują na czerwono.
    * Kliknij pulsujący kafelek w zakładce Nodes, aby jednym przyciskiem natychmiast przełączyć swoje radio na grupę (TG), na której toczy się rozmowa.

7.  **📻 Multi-Hardware (Wybór Radia):**
    * Wbudowana i zautomatyzowana obsługa zaawansowanych płytek **RF Guru** ze sprzętowym kodekiem audio I2S (WM8960) z poziomu przeglądarki.
    * Wbudowana obsługa popularnych płytek nakładkowych **SHARI (SA818)**.
    * Tryb pracy dla zewnętrznych radii przez kartę dźwiękową USB (**CM108**). System pozwala na samodzielne przypisanie pinów GPIO dla sygnałów PTT oraz COS z poziomu panelu WWW.

8.  **🆘 Tryb Ratunkowy Wi-Fi (Access Point):**
    * Jesteś w podróży lub zmieniłeś router? Jeśli urządzenie po uruchomieniu nie połączy się ze znaną siecią Wi-Fi, po 2 minutach wygeneruje własną sieć ratunkową (`PrimeNode_AP`). Połącz się z nią, wejdź na `http://192.168.4.1` i wygodnie dodaj nowe Wi-Fi z poziomu Dashboardu.

9.  **🌐 Network Roaming (Baza Sieci):**
    * Wbudowany menedżer sieci. Definiuj wiele serwerów (Reflektorów) z różnymi hasłami i przypisanymi zapowiedziami audio.
    * Szybkie przełączanie sieci kodami DTMF z radia: `555` + `ID` + `#`. System sam zrestartuje usługę i wejdzie na Twoją domyślną grupę.

10. **🔄 System Aktualizacji (OTA Update):**
    * Wbudowany mechanizm aktualizacji. Pobieraj poprawki i nowości (w tym modyfikacje skryptów i crontab) jednym kliknięciem w zakładce *Zasilanie*, bez konieczności ponownego wgrywania obrazu na kartę.

11. **💻 Web Terminal (SSH) i Audio Mixer:**
    * Pełny dostęp do konsoli systemowej bezpośrednio z przeglądarki.
    * Wbudowany mikser ALSA w Dashboardzie. Precyzyjna regulacja poziomów (Mic Boost, ADC Gain, DAC Vol) suwakami – koniec z przesterowanym audio!

---

## 📺 PrimeNode Monitor (OLED)

System PrimeNode posiada wbudowaną integrację z autorskim oprogramowaniem monitorującym. Obsługuje ono wyświetlacze **OLED 1.3 cala oraz 2.42 cala**, prezentując kluczowe parametry pracy węzła w czytelnej formie.

![PrimeNode Monitor Animation](images/monitor_demo.gif)

👉 **Oprogramowanie oraz instrukcja podłączenia wyświetlacza znajdują się w osobnym repozytorium: [PrimeNode-Monitor](https://github.com/ArduUTP/PrimeNode_Monitor_OLED_1.3_2.42_BY_SQ7UTP)**

---

## 📸 Galeria / Screenshots (V1.5)

| **Smart Config (Wybór TG)** | **EchoLink Wyszukiwarka Live** |
| :---: | :---: |
| ![Smart Config](images/new_config.jpg) | ![EchoLink Search](images/echolink_search.jpg) |

| **Ustawienia APRS** | **Backup & Restore** |
| :---: | :---: |
| ![APRS Config](images/aprs_config.jpg) | ![Backup](images/backup.jpg) |

| **Dashboard (Live Monitor)** | **Nodes List** |
| :---: | :---: |
| ![Dashboard](images/dashboard.jpeg) | ![Nodes](images/nodes.jpeg) |

| **Nodes Map (Leaflet)** | **DTMF Editor (Drag & Drop)** |
| :---: | :---: |
| ![Nodes Map](images/node_mapa.jpeg) | ![DTMF](images/dtmf.jpeg) |

| **Radio Config (Multi-Hardware)** | **Audio Mixer** |
| :---: | :---: |
| ![Radio](images/radio.jpeg) | ![Audio](images/audio.jpeg) |

| **SvxLink Config & Roaming** | **WiFi Manager** |
| :---: | :---: |
| ![Config](images/config.jpeg) | ![WiFi](images/wifi.jpeg) |

| **Power Control** | **Live Logs** |
| :---: | :---: |
| ![Zasilanie](images/zasilanie.jpeg) | ![Log](images/log.jpeg) |

| **Web Terminal (SSH)** | **Help Center** |
| :---: | :---: |
| ![SSH](images/ssh.jpeg) | ![Help](images/help.jpeg) |

---

## 🇵🇱 Instrukcja Instalacji

### 1. Pobranie i Wgrywanie
1. Pobierz najnowszy plik `.img.xz` lub `.zip` z zakładki [Releases](../../releases).
2. Rozpakuj archiwum.
3. Użyj programu **Balena Etcher** lub **Rufus**, aby nagrać obraz na kartę microSD.

### 2. Podłączenie i Uruchomienie
1. Włóż kartę do Twojego **Raspberry Pi**.
2. Podłącz dedykowaną nakładkę (**RF Guru** / **SHARI**) lub kabel USB z chipem CM108.
3. **Zalecane:** Podłącz kabel sieciowy (Ethernet) do routera dla pewności podczas pierwszego uruchomienia. *(Jeśli nie posiadasz kabla sieciowego, odczekaj aż urządzenie wygeneruje ratunkową sieć Wi-Fi "PrimeNode_AP")*.
4. Podłącz zasilanie.
5. Poczekaj około 2-3 minuty na pierwsze uruchomienie i inicjalizację usług.

### 3. Konfiguracja
1. Wpisz w przeglądarce adres: `http://primenode.local`
   *(Jeśli adres nie działa, sprawdź na routerze jaki adres IP pobrało urządzenie "primenode").*
2. Przejdź do zakładki **Wi-Fi** i połącz malinę ze swoją domową siecią bezprzewodową.
3. Przejdź do zakładki **Konfiguracja (Config)**.
4. Wpisz swoje dane:
    * **Znak (Callsign)**
    * **Hasło** do sieci reflektorów
    * **Adres Reflektora (Host)**
    * **Port**
    * **Adres API** (do listy nodów)
    * Kliknij *Zapisz*.
5. W zakładce **Radio** wybierz swój typ urządzenia (RF Guru, SHARI lub USB/CM108), ustaw piny GPIO (jeśli dotyczy), wpisz częstotliwość pracy swojego hotspota i kliknij *Zapisz*.
6. Gotowe! Możesz rozmawiać.

---

## 🇬🇧 Installation Guide

### 1. Download & Flash
1. Get the latest `.img.xz` or `.zip` file from the [Releases](../../releases) section.
2. Unzip the archive.
3. Use **Balena Etcher** or **Rufus** to write the image to a microSD card.

### 2. Connect & Boot
1. Insert the SD card into your **Raspberry Pi**.
2. Attach your dedicated board (**RF Guru** / **SHARI**) or USB CM108 sound card.
3. **Recommended:** Connect an Ethernet cable to your router to ensure connectivity during the first boot. *(If you don't have an ethernet cable, wait for the device to broadcast the rescue "PrimeNode_AP" Wi-Fi network).*
4. Power up the device.
5. Wait approx. 2-3 minutes for the first boot initialization.

### 3. Configuration
1. Open your browser and go to: `http://primenode.local`
   *(If not resolving, check your router's DHCP list for the device IP).*
2. Go to the **Wi-Fi** tab and connect the Raspberry Pi to your local wireless network.
3. Go to the **Config** tab.
4. Enter your details:
    * **Callsign**
    * **Reflector Password**
    * **Reflector Host Address**
    * **Port**
    * **Node API URL**
    * Click *Save*.
5. Go to the **Radio** tab, select your hardware type (RF Guru, SHARI or USB/CM108), configure GPIO pins (if applicable), enter your frequency, and click *Save*.
6. Done! You are on air.

---

## 📜 Licencja i Autorzy / License & Credits

> **⚠️ NOTA LICENCYJNA ORAZ ZNAKI TOWAROWE / LICENSE & TRADEMARK NOTICE** <br>
> Oprogramowanie z otwartym kodem źródłowym. Udostępniane i rozwijane pod autorską marką **PrimeNode** na warunkach licencji **GPLv3**. Używasz go na własną odpowiedzialność (Software is provided "AS IS"). 
>
> *Przy modyfikacji i redystrybucji kodu wymagane jest bezwzględne zachowanie informacji o oryginalnym autorze, zachowanie logotypów PrimeNode oraz oryginalnej nazwy systemu w nagłówkach i stopkach interfejsu zgodnie z warunkami licencji otwartego oprogramowania.*

* **Twórca Systemu & Dashboardu (Author):** Marcin "Skrętka" **SQ7UTP**
* **Kontakt / Contact:** sq7utp@gmail.com
* **Core Software (Silnik radiowy):** Tobias Blomberg (SM0SVX) - *SvxLink Creator*

🙌 **Specjalne podziękowania:** Dla Oktawiana (**SP2EOE**) za inicjatywę oraz nieocenione wsparcie sprzętowe, które umożliwiło wdrożenie i zoptymalizowanie układów RF Guru. 

*Projekt stworzony z pasji do krótkofalarstwa. 73!*
