---
title: Sterowanie urządzeniem dla systemu macOS
description: Dowiedz się, jak skonfigurować Ochrona punktu końcowego w usłudze Microsoft Defender na komputerze Mac w celu zmniejszenia zagrożeń związanych z nośnikami wymiennymi, takimi jak urządzenia USB.
keywords: microsoft, defender, Ochrona punktu końcowego w usłudze Microsoft Defender, mac, urządzenie, control, usb, wymienne, multimedia
ms.prod: m365-security
ms.mktglfcycl: security
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: fbe693272a2f2893dff5f8614f3f9eff301069fd
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2022
ms.locfileid: "64477308"
---
# <a name="device-control-for-macos"></a>Sterowanie urządzeniem dla systemu macOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz doświadczyć Ochrona punktu końcowego w usłudze Microsoft Defender? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

## <a name="requirements"></a>Wymagania

Sterowanie urządzeniem dla systemu macOS ma następujące wymagania wstępne:

> [!div class="checklist"]
>
> - Ochrona punktu końcowego w usłudze Microsoft Defender uprawnienia (może być próbna)
> - Minimalna wersja systemu operacyjnego: macOS 11 lub nowsza
> - Minimalna wersja produktu: 101.34.20

## <a name="device-control-policy"></a>Zasady sterowania urządzeniami

Aby skonfigurować sterowanie urządzeniami dla systemu macOS, musisz utworzyć zasady opisujące ograniczenia, które mają zostać wprowadzone w organizacji.

Zasady sterowania urządzeniami są zawarte w profilu konfiguracji używanym do konfigurowania wszystkich pozostałych ustawień produktu. Aby uzyskać więcej informacji, zobacz [Struktura profilu konfiguracji](mac-preferences.md#configuration-profile-structure).

W profilu konfiguracji zasady sterowania urządzeniami są zdefiniowane w następującej sekcji:

<br>

****

|Sekcja|Value|
|---|---|
|**Domain (Domena)**|`com.microsoft.wdav`|
|**Klucz**|deviceControl|
|**Typ danych**|Słownik (preferencja zagnieżdżona)|
|**Komentarze**|Opis zawartości słownika można znaleźć w poniższych sekcjach.|
|

Zasady sterowania urządzeniami mogą służyć do:

- [Dostosowywanie wartości docelowej adresu URL dla powiadomień podniesionych przez kontrolkę urządzenia](#customize-url-target-for-notifications-raised-by-device-control)
- [Zezwalanie lub blokowanie urządzeń wymiennych](#allow-or-block-removable-devices)

### <a name="customize-url-target-for-notifications-raised-by-device-control"></a>Dostosowywanie wartości docelowej adresu URL dla powiadomień podniesionych przez kontrolkę urządzenia

Jeśli wprowadzone zasady sterowania urządzeniem są wymuszane na urządzeniu (na przykład dostęp do nośniki wymiennych jest ograniczony), użytkownikowi jest wyświetlane powiadomienie.

:::image type="content" source="images/mac-device-control-notification.png" alt-text="Powiadomienie o kontrolce urządzenia" lightbox="images/mac-device-control-notification.png":::

Gdy użytkownicy końcowi klikną to powiadomienie, w domyślnej przeglądarce zostanie otwarta strona sieci Web. Możesz skonfigurować adres URL, który jest otwierany po kliknięciu powiadomienia przez użytkowników końcowych.

<br>

****

|Sekcja|Value|
|---|---|
|**Domain (Domena)**|`com.microsoft.wdav`|
|**Klucz**|navigationTarget|
|**Typ danych**|Ciąg|
|**Komentarze**|Jeśli nie zdefiniowano, w produkcie jest używany domyślny adres URL, który zawiera ogólną stronę z wyjaśnieniem akcji wykonanej przez produkt.|
|

### <a name="allow-or-block-removable-devices"></a>Zezwalanie lub blokowanie urządzeń wymiennych

Sekcja nośniki wymiennych zasad sterowania urządzenia służy do ograniczania dostępu do nośników wymiennych.

> [!NOTE]
> Następujące typy nośników wymiennych są obecnie obsługiwane i mogą być zawarte w zasadach: urządzenia magazynujących USB.

<br>

****

|Sekcja|Value|
|---|---|
|**Domain (Domena)**|`com.microsoft.wdav`|
|**Klucz**|removableMediaPolicy|
|**Typ danych**|Słownik (preferencja zagnieżdżona)|
|**Komentarze**|Opis zawartości słownika można znaleźć w poniższych sekcjach.|
|

Ta sekcja zasad jest hierarchiczna, pozwalająca na maksymalną elastyczność i obejmujący szereg przypadków użycia. Na najwyższym poziomie są dostawcy identyfikowani za pomocą identyfikatora dostawcy. Każdy dostawca ma produkty oznaczone identyfikatorem produktu. Ponadto dla każdego produktu istnieją numery seryjne oznaczające określone urządzenia.

```text
|-- policy top level
    |-- vendor 1
        |-- product 1
            |-- serial number 1
            ...
            |-- serial number N
        ...
        |-- product N
    ...
    |-- vendor N
```

Aby uzyskać informacje o tym, jak znaleźć identyfikatory urządzeń, zobacz [Wyszukiwanie identyfikatorów urządzeń](#look-up-device-identifiers).

Zasady są obliczane od najbardziej konkretnego wpisu do najbardziej ogólnego. Oznacza to, że po podłączeniu urządzenia produkt próbuje znaleźć najbardziej szczegółowe dopasowanie w zasadach dla każdego urządzenia przenośnego i zastosować uprawnienia na tym poziomie. Jeśli brakuje dopasowania, zostanie zastosowane następne najlepsze dopasowanie, do poziomu uprawnień określonego na najwyższym poziomie, które jest ustawieniem domyślnym, gdy urządzenie nie pasuje do żadnego innego wpisu w zasadach.

#### <a name="policy-enforcement-level"></a>Poziom wymuszania zasad

W sekcji nośnik wymienny dostępna jest opcja ustawienia poziomu wymuszania, który może przyjmować jedną z następujących wartości:

- `audit` - Na tym poziomie wymuszeń, jeśli dostęp do urządzenia jest ograniczony, użytkownikowi zostanie wyświetlone powiadomienie, ale nadal będzie można z niego korzystać. Taki poziom wymusów może być przydatny do oceny skuteczności zasad.
- `block` — Na tym poziomie wymuszania operacje, które użytkownik może wykonywać na urządzeniu, są ograniczone do danych zdefiniowanych w zasadach. Ponadto użytkownik jest zwracany do użytkownika z powiadomieniem.

> [!NOTE]
> Domyślnie poziom wymusze jest ustawiony na `audit`.

<br>

****

|Sekcja|Value|
|---|---|
|**Domain (Domena)**|`com.microsoft.wdav`|
|**Klucz**|enforcementLevel|
|**Typ danych**|Ciąg|
|**Dopuszczalne wartości**|inspekcja (domyślna) <p> blok|
|

#### <a name="default-permission-level"></a>Domyślny poziom uprawnień

Na najwyższym poziomie sekcji nośniki wymiennych możesz skonfigurować domyślny poziom uprawnień dla urządzeń, które nie są zgodne z niczego innego w zasadach.

To ustawienie można skonfigurować jako:

- `none` — Na urządzeniu nie można wykonywać żadnych operacji
- Kombinacja następujących wartości:
  - `read` — Operacje czytania są dozwolone na urządzeniu
  - `write` — Operacje zapisu są dozwolone na urządzeniu
  - `execute` - Wykonywanie operacji na urządzeniu jest dozwolone

> [!NOTE]
> Jeśli `none` poziom uprawnień jest obecny, wszelkie inne uprawnienia (`read``write`lub `execute`) zostaną zignorowane.
>
> Uprawnienia `execute` dotyczą tylko wykonywania danych binralnych Mach-O. Nie obejmuje wykonywania skryptów ani innych typów elementów ładu.

<br>

****

|Sekcja|Value|
|---|---|
|**Domain (Domena)**|`com.microsoft.wdav`|
|**Klucz**|uprawnienie|
|**Typ danych**|Tablica ciągów|
|**Dopuszczalne wartości**|brak <p> czytanie <p> pisanie <p> wykonywanie|
|

#### <a name="restrict-removable-media-by-vendor-product-and-serial-number"></a>Ograniczanie nośnika wymiennych według dostawcy, produktu i numeru seryjnego

Zgodnie z opisem w [opisie wymiennych](#allow-or-block-removable-devices) urządzeń wymiennych nośniki wymienne, takie jak urządzenia USB, można zidentyfikować za pomocą identyfikatora dostawcy, identyfikatora produktu i numeru seryjnego.

Na najwyższym poziomie zasad dotyczących nośników wymiennych można opcjonalnie zdefiniować bardziej szczegółowe ograniczenia na poziomie dostawcy.

Słownik `vendors` zawiera co najmniej jeden wpis, z każdym wpisem oznaczonym identyfikatorem dostawcy.

<br>

****

|Sekcja|Value|
|---|---|
|**Domain (Domena)**|`com.microsoft.wdav`|
|**Klucz**|dostawcy|
|**Typ danych**|Słownik (preferencja zagnieżdżona)|
|

Dla każdego dostawcy możesz określić żądany poziom uprawnień dla urządzeń od tego dostawcy.

<br>

****

|Sekcja|Value|
|---|---|
|**Domain (Domena)**|`com.microsoft.wdav`|
|**Klucz**|uprawnienie|
|**Typ danych**|Tablica ciągów|
|**Dopuszczalne wartości**|Taki sam jak [domyślny poziom uprawnień](#default-permission-level)|
|

Ponadto możesz opcjonalnie określić zestaw produktów należących do tego dostawcy, dla którego są zdefiniowane bardziej szczegółowe uprawnienia. Słownik `products` zawiera co najmniej jeden wpis, z każdym wpisem oznaczonym identyfikatorem produktu.

<br>

****

|Sekcja|Value|
|---|---|
|**Domain (Domena)**|`com.microsoft.wdav`|
|**Klucz**|produkty|
|**Typ danych**|Słownik (preferencja zagnieżdżona)|
|

Dla każdego produktu możesz określić żądany poziom uprawnień dla tego produktu.

<br>

****

|Sekcja|Value|
|---|---|
|**Domain (Domena)**|`com.microsoft.wdav`|
|**Klucz**|uprawnienie|
|**Typ danych**|Tablica ciągów|
|**Dopuszczalne wartości**|Taki sam jak [domyślny poziom uprawnień](#default-permission-level)|
|

Ponadto możesz określić opcjonalny zestaw liczb kolejnych, dla których są zdefiniowane bardziej szczegółowe uprawnienia.

Słownik `serialNumbers` zawiera co najmniej jeden wpis, a każdy wpis jest identyfikowany za pomocą numeru seryjnego.

<br>

****

|Sekcja|Value|
|---|---|
|**Domain (Domena)**|`com.microsoft.wdav`|
|**Klucz**|liczba_kolejną|
|**Typ danych**|Słownik (preferencja zagnieżdżona)|
|

Dla każdego numeru seryjnego możesz określić odpowiedni poziom uprawnień.

<br>

****

|Sekcja|Value|
|---|---|
|**Domain (Domena)**|`com.microsoft.wdav`|
|**Klucz**|uprawnienie|
|**Typ danych**|Tablica ciągów|
|**Dopuszczalne wartości**|Taki sam jak [domyślny poziom uprawnień](#default-permission-level)|
|

#### <a name="example-device-control-policy"></a>Przykładowe zasady sterowania urządzeniami

W poniższym przykładzie pokazano, jak można połączyć wszystkie powyższe pojęcia z zasadami sterowania urządzeniami. W poniższym przykładzie zwróć uwagę na hierarchiczny charakter zasad multimediów wymiennych.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
    <key>deviceControl</key>
    <dict>
        <key>navigationTarget</key>
        <string>[custom URL for notifications]</string>
        <key>removableMediaPolicy</key>
        <dict>
            <key>enforcementLevel</key>
            <string>[enforcement level]</string> <!-- audit / block -->
            <key>permission</key>
            <array>
                <string>[permission]</string> <!-- none / read / write / execute -->
                <!-- other permissions -->
            </array>
            <key>vendors</key>
            <dict>
                <key>[vendor id]</key>
                <dict>
                    <key>permission</key>
                    <array>
                        <string>[permission]</string> <!-- none / read / write / execute -->
                        <!-- other permissions -->
                    </array>
                    <key>products</key>
                    <dict>
                        <key>[product id]</key>
                        <dict>
                            <key>permission</key>
                            <array>
                                <string>[permission]</string> <!-- none / read / write / execute -->
                                <!-- other permissions -->
                            </array>
                            <key>serialNumbers</key>
                            <dict>
                                <key>[serial-number]</key>
                                <array>
                                    <string>[permission]</string> <!-- none / read / write / execute -->
                                    <!-- other permissions -->
                                </array>
                                <!-- other serial numbers -->
                            </dict>
                        </dict>
                        <!-- other products -->
                    </dict>
                </dict>
                <!-- other vendors -->
            </dict>
        </dict>
    </dict>
</dict>
</plist>
```

W poniższych dokumentach podano więcej przykładów zasad sterowania urządzeniami:

- [Przykłady zasad sterowania urządzeniami dla Intune](mac-device-control-intune.md)
- [Przykłady zasad sterowania urządzeniami dla jamf](mac-device-control-jamf.md)

#### <a name="look-up-device-identifiers"></a>Sprawdź identyfikatory urządzeń

Aby znaleźć identyfikator dostawcy, identyfikator produktu i numer seryjny urządzenia USB:

1. Zaloguj się na urządzeniu Mac.
1. Podłącz urządzenie USB, dla którego chcesz sprawdzić identyfikatory.
1. W menu najwyższego poziomu w systemie macOS wybierz pozycję **Informacje o tym komputerze Mac**.

   :::image type="content" source="images/mac-device-control-lookup-1.png" alt-text="Strona Informacje o tym komputerze Mac" lightbox="images/mac-device-control-lookup-1.png":::

1. Wybierz **pozycję Raport systemowy**.

   :::image type="content" source="images/mac-device-control-lookup-2.png" alt-text="Raport systemowy" lightbox="images/mac-device-control-lookup-2.png":::

1. W lewej kolumnie wybierz pozycję **USB**.

   :::image type="content" source="images/mac-device-control-lookup-3.png" alt-text="Widok wszystkich urządzeń USB" lightbox="images/mac-device-control-lookup-3.png":::
    

1. W **obszarze Drzewo urządzeń USB** przejdź do podłączonego urządzenia USB.

   :::image type="content" source="images/mac-device-control-lookup-4.png" alt-text="Szczegóły urządzenia USB" lightbox="images/mac-device-control-lookup-4.png":::

1. Zostanie wyświetlony identyfikator dostawcy, identyfikator produktu i numer seryjny. Dodając identyfikator dostawcy i identyfikator produktu do zasad nośniki wymiennych, wystarczy dodać część `0x`po . Na przykład na poniższej ilustracji identyfikator dostawcy to `1000` , a identyfikator produktu to `090c`.

#### <a name="discover-usb-devices-in-your-organization"></a>Odkryj urządzenia USB w swojej organizacji

Możesz wyświetlać zdarzenia dotyczące montażu, unmount i głośności pochodzące z urządzeń USB w Ochrona punktu końcowego w usłudze Microsoft Defender wyszukiwania zaawansowanego. Te zdarzenia mogą być pomocne przy identyfikowaniu podejrzanych działań w zakresie użycia lub przeprowadzaniu wewnętrznych badań.

```bash
DeviceEvents
    | where ActionType == "UsbDriveMounted" or ActionType == "UsbDriveUnmounted" or ActionType == "UsbDriveDriveLetterChanged"
    | where DeviceId == "<device ID>"
```

## <a name="device-control-policy-deployment"></a>Wdrażanie zasad sterowania urządzeniami

Zasady sterowania urządzeniem muszą być uwzględnione obok innych ustawień produktu, tak jak to opisano w tece Ustawianie preferencji Ochrona punktu końcowego w usłudze Microsoft Defender [w systemie macOS](mac-preferences.md).

Ten profil można wdrożyć, korzystając z instrukcji podanych w [tece Wdrożenie profilu konfiguracji](mac-preferences.md#configuration-profile-deployment).

## <a name="troubleshooting-tips"></a>Porady dotyczące rozwiązywania problemów

Po wypychaniu profilu konfiguracji przez program Intune lub JAMF możesz sprawdzić, czy produkt został pomyślnie odebrany przez produkt, uruchamiając następujące polecenie z aplikacji Terminal:

```bash
mdatp device-control removable-media policy list
```

To polecenie zostanie wydrukowane do standardowego wydruku zasad sterowania urządzeniem, których używa ten produkt. Na wypadek `Policy is empty`wydrukowania tego pliku upewnij się, że (a) profil konfiguracji rzeczywiście został wypchnął na Twoje urządzenie z konsoli zarządzania i (b) że są to prawidłowe zasady sterowania urządzeniami zgodnie z opisem w tym dokumencie.

Na urządzeniu, na którym zasady zostały pomyślnie dostarczone i gdzie jest co najmniej jedno urządzenie podłączone, możesz uruchomić następujące polecenie, aby wyświetlić listę wszystkich urządzeń i zastosowanych do nich efektywnych uprawnień.

```bash
mdatp device-control removable-media devices list
```

Przykładowe dane wyjściowe:

```Output
.Device(s)
|-o Name: Untitled 1, Permission ["read", "execute"]
| |-o Vendor: General "fff0"
| |-o Product: USB Flash Disk "1000"
| |-o Serial number: "04ZSSMHI2O7WBVOA"
| |-o Mount point: "/Volumes/TESTUSB"
```

W powyższym przykładzie `read` `execute` jest podłączone tylko jedno wymienne urządzenie multimedialne, które jest podłączone oraz ma i uprawnienia, zgodnie z zasadami sterowania urządzeniem dostarczonymi na to urządzenie.

## <a name="related-topics"></a>Tematy pokrewne

- [Przykłady zasad sterowania urządzeniami dla Intune](mac-device-control-intune.md)
- [Przykłady zasad sterowania urządzeniami dla jamf](mac-device-control-jamf.md)
