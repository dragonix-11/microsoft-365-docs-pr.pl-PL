---
title: Jak działa funkcja ochrony w usłudze Microsoft 365 Business Premium mapowanie na ustawienia usługi Intune
f1.keywords:
- NOCSH
ms.author: sharik
author: skjerland
manager: scotv
ms.date: 8/13/2018
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Adm_O365
- M365-subscription-management
- M365-identity-device-management
- Adm_TOC
ms.custom:
- Adm_O365
- Core_O365Admin_Migration
- MiniMaven
- MSB365
- OKR_SMB_M365
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
ms.assetid: aad21b1a-c775-469a-b89c-c5d1d59d27db
description: Dowiedz się, jak są dostępne funkcje Microsoft 365 Business Premium mapowanie na ustawienia usługi Intune. Subskrypcja udostępnia licencję na modyfikowanie ustawień usługi Intune.
ms.openlocfilehash: 144a49f6c6463e7562c6509c981ab56b4702453c
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62984086"
---
# <a name="how-do-protection-features-in-microsoft-365-business-premium-map-to-intune-settings"></a>Jak działa funkcja ochrony w usłudze Microsoft 365 Business Premium mapowanie na ustawienia usługi Intune

## <a name="android-and-ios-application-protection-settings"></a>Ustawienia ochrony aplikacji dla systemów Android lub iOS

W poniższej tabeli przedstawiono mapowanie ustawień zasad aplikacji systemów Android i iOS na ustawienia usługi Intune.
  
Aby znaleźć ustawienie usługi Intune, zaloguj się przy użyciu poświadczeń Microsoft 365 Business Premium administratora, przejdź do pozycji Centra **administracyjne, a** następnie **Intune**.
  
 > [!IMPORTANT]
 > 
 > Subskrypcja Microsoft 365 Business Premium udostępnia licencję na modyfikowanie wszystkich ustawień usługi Intune. Aby [rozpocząć, zobacz Wprowadzenie do usługi Intune.](/intune/introduction-intune)
  
Wybierz nazwę zasad, na przykład &mdash; Zasady aplikacji dla systemu Android &mdash; , a następnie wybierz **pozycję Ustawienia zasad**.
  
W obszarze **Chroń pliki służbowe w przypadku zgubienia lub kradzieży urządzenia**
  
|**Ustawienie zasad aplikacji dla systemu Android lub iOS**|**Ustawienia usługi Intune**|
|:-----|:-----|
|Usuń pliki służbowe z nieaktywnego urządzenia po  <br/> |Interwał przebywania w trybie offline (w dniach) przed wyczyszczeniem danych aplikacji  <br/> |
|Wymuszaj na użytkownikach zapisywanie plików służbowych w usłudze OneDrive dla Firm  <br/> Uwaga: dozwolona jest tylko usługa OneDrive dla Firm  <br/> |Wybierz, w których usługach magazynu można zapisywać dane firmowe  <br/> |
|||
   
W obszarze **Zarządzaj dostępem użytkowników do plików pakietu Office na urządzeniach przenośnych**
  
|**Ustawienie zasad aplikacji dla systemu Android lub iOS**|**Ustawienia usługi Intune**|
|:-----|:-----|
|Usuń pliki służbowe z nieaktywnego urządzenia po  <br/> |Interwał przebywania w trybie offline (w dniach) przed wyczyszczeniem danych aplikacji  <br/> |
|Wymuszaj na użytkownikach zapisywanie plików służbowych w usłudze OneDrive dla Firm  <br/> Uwaga: dozwolona jest tylko usługa OneDrive dla Firm  <br/> |Wybierz, w których usługach magazynu można zapisywać dane firmowe  <br/> |
|Szyfruj pliki służbowe  <br/> |Szyfruj dane aplikacji  <br/> |
|W obszarze **Zarządzaj dostępem użytkowników do plików pakietu Office na urządzeniach przenośnych** <br/> ||
|Wymagaj numeru PIN lub odcisku palca w celu uzyskania dostępu do aplikacji pakietu Office  <br/> | Wymagaj numeru PIN w celu uzyskania dostępu  <br/>  Spowoduje to również ustawienie:  <br/> **Zezwalaj na prosty numer PIN** na **Tak** <br/> **Długość numeru PIN** na 4  <br/> **Zezwalaj na używanie odcisku palca zamiast numeru PIN** na **Tak** <br/> **Wyłącz numer PIN aplikacji, gdy zarządzany jest numer PIN urządzenia** na **Tak** <br/> |
|Resetuj numer PIN, gdy logowanie często kończy się niepowodzeniem (jest ona wyłączona, jeśli numer PIN nie jest wymagany)  <br/> |Liczba prób przed zresetowaniem numeru PIN  <br/> |
|Wymagaj ponownego logowania użytkowników po Office bezczynności aplikacji (ta tryb jest wyłączona, jeśli numer PIN nie jest wymagany)  <br/> | Ponownie sprawdź wymagania dostępu po (w minutach)  <br/>  Spowoduje to również ustawienie:  <br/> **Limit czasu**  zostają ustawione minuty  <br/>  Jest to ta sama liczba minut, która jest ustawiana w usłudze Microsoft 365 Business.  <br/> **Okres karencji w trybie offline**  zostaje domyślnie ustawiona wartość 720 minut  <br/> |
|Odmów dostępu do plików służbowych na urządzeniach z usuniętymi natywnymi ograniczeniami producenta  <br/> |Blokuj uruchamianie aplikacji zarządzanych na urządzeniach ze zdjętymi zabezpieczeniami systemu lub odblokowanym dostępem do konta administratora  <br/> |
|Zezwalaj użytkownikom na kopiowanie zawartości z aplikacji pakietu Office do aplikacji osobistych  <br/> | Ograniczanie wycinania, kopiowania i wklejania w innych aplikacjach  <br/>  Jeśli dla Microsoft 365 Business Premium jest ustawiona wartość **Wł**., dla tych trzech opcji jest również ustawiona wartość **Wszystkie** aplikacje w usłudze Intune:  <br/> **Zezwalaj aplikacji na przesyłanie danych do innych aplikacji** <br/> **Zezwalaj aplikacji na odbieranie danych z innych aplikacji** <br/> **Ogranicz wycinanie, kopiowanie i wklejanie w innych aplikacjach** <br/>  Jeśli dla opcji Microsoft 365 Business została ustawiona wartość **Włączone**, to dla wszystkich tych opcji w usłudze Intune zostają ustawione wskazane wartości:  <br/> **Zezwalaj aplikacji na przesyłanie danych do innych aplikacji**  zostaje ustawiona wartość **Aplikacje zarządzane przez zasady** <br/> **Zezwalaj aplikacji na odbieranie danych z innych aplikacji**  zostaje ustawiona wartość **Wszystkie aplikacje** <br/> **Ogranicz wycinanie, kopiowanie i wklejanie w innych aplikacjach**  zostaje ustawiona wartość **Aplikacje zarządzane przez zasady z funkcją wklejania** <br/> |
|||
   
## <a name="windows-10-app-protection-settings"></a>Ustawienia ochrony aplikacji dla systemu Windows 10

W poniższej tabeli przedstawiono mapowanie ustawień zasad aplikacji systemu Windows 10 na ustawienia usługi Intune.
  
Aby znaleźć ustawienie usługi Intune, zaloguj się przy użyciu poświadczeń Microsoft 365 Business Premium administratora, a następnie przejdź do [portalu Azure Portal](https://portal.azure.com). Wybierz **pozycję Więcej usług** i wpisz Intune w **filtrze**. Wybierz **pozycję Zasady aplikacji Intune App Protection**\>.
  
 > [!IMPORTANT]
 >
 >Subskrypcja Microsoft 365 Business Premium udostępnia licencję na modyfikowanie tylko ustawień usługi Intune mapowych na ustawienia dostępne w usłudze Microsoft 365 Business Premium. 
  
Aby poznać dostępne ustawienia, wybierz nazwę zasady, a następnie wybierz pozycję **Ogólne,** Przydziały **, Dozwolone** **aplikacje, Wykluczone** **aplikacje, Wymagane** ustawienia lub Ustawienia **zaawansowane** w lewym okienku nawigacji. 
  
|**Ustawienie zasad aplikacji dla systemu Windows 10**|**Ustawienia usługi Intune**|
|:-----|:-----|
|Szyfruj pliki służbowe  <br/> |**Ustawienia zaawansowane** \> **Ochrona danych**: **Odwołaj klucze szyfrowania po wyrejestrowaniu** i **Odwołaj dostęp do chronionych danych po zarejestrowaniu urządzenia w usłudze MDM**  dla obu zasad zostaje ustawiona wartość **Włączone**.  <br/> |
|Uniemożliwia użytkownikom kopiowanie danych firmy do plików osobistych.  <br/> |**Wymagane ustawienia** \> **Tryb funkcji Windows Information Protection**. **Na** w Microsoft 365 Business Premium mapy do: **Ukryj przesłonięcia****, Wyłączone** w Microsoft 365 Business Premium mapuje do: **Wyłączone**.  <br/> |
|Kontrola dostępu do dokumentów pakietu Office  <br/> | Jeśli w programie Microsoft 365 Business Premium  jest ustawiona wartość Wł.,  <br/> dla zasady **Ustawienia zaawansowane** \> **Dostęp**, **Użyj usługi Windows Hello dla firm jako metody logowania się do systemu Windows** zostaje ustawiona wartość **Włączone** z następującymi ustawieniami dodatkowymi:  <br/> **Ustaw minimalną wymaganą liczbę znaków kodu PIN**  zostaje ustawiona wartość **4**.  <br/> **Skonfiguruj użycie wielkich liter w kodzie PIN usługi Windows Hello dla firm**  zostaje ustawiona wartość **Nie zezwalaj na użycie wielkich liter w kodzie PIN**.  <br/> **Skonfiguruj użycie małych liter w kodzie PIN usługi Windows Hello dla firm**  zostaje ustawiona wartość **Nie zezwalaj na użycie małych liter w kodzie PIN**.  <br/> **Skonfiguruj użycie znaków specjalnych w kodzie PIN usługi Windows Hello dla firm**  zostaje ustawiona wartość **Nie zezwalaj na użycie znaków specjalnych w kodzie PIN**.  <br/> **Określ czas (** w dniach), przez jaki może być używany numer PIN, zanim system wymaga zmiany przez użytkownika ma ustawioną wartość **0**.  <br/> **Określ liczbę ostatnich numerów PIN skojarzonych z kontem użytkownika, które nie mogą zostać ponownie użyte**  zostaje ustawiona wartość **0**.  <br/> **Liczba dozwolonych niepowodzeń uwierzytelniania, po przekroczeniu której urządzenie zostanie wyczyszczone**  zostaje ustawiona wartość taka sama jak w usłudze Microsoft 365 Business (domyślnie: 5).  <br/> **Maksymalny czas (w minutach) bezczynności urządzenia, po którym urządzenie zostanie zablokowane przy użyciu kodu PIN lub hasła**  zostaje ustawiona wartość taka sama jak w usłudze Microsoft 365 Business.  <br/> |
|Włącz odzyskiwanie chronionych danych  <br/> |**Ustawienia zaawansowane** \> **Ochrona danych**: **Pokaż ikonę ochrony danych przedsiębiorstwa** i **Użyj usługi Azure RMS na potrzeby funkcji WIP**  dla obu zasad zostaje ustawiona wartość **Włączone**.  <br/> |
|Chroń dodatkowe lokalizacje firmowe w chmurze  <br/> |**Ustawienia zaawansowane** \> **Domeny chronione** i **Zasoby w chmurze**  są tu wskazywane domeny i witryny programu SharePoint.  <br/> |
|Pliki używane przez te aplikacje są chronione  <br/> |Listę chronionych aplikacji można znaleźć w obszarze **Dozwolone aplikacje**.  <br/> |
|||
   
## <a name="windows-10-device-protection-settings"></a>Ustawienia ochrony urządzeń dla systemu Windows 10

W poniższej tabeli przedstawiono mapowanie ustawień konfiguracji urządzeń systemu Windows 10 na ustawienia usługi Intune.
  
Aby znaleźć ustawienie usługi Intune, zaloguj się przy użyciu poświadczeń administratora usługi Microsoft 365 Business Premium, przejdź do portalu [Azure Portal](https://portal.azure.com), wybierz pozycję Więcej **usług i wpisz** Intune w filtrze **, wybierz** pozycję Profile konfiguracji urządzenia **Intune** \> **.**\> Then select **Device policy for Windows 10** \> **Properties** \> **Settings**.
  
|**Ustawienie zasad urządzeń dla systemu Windows 10**|**Ustawienia usługi Intune**|
|:-----|:-----|
|Chroń komputery przed wirusami i innymi zagrożeniami za pomocą ochrony antywirusowej programu Windows Defender  <br/> |Zezwalaj na monitorowanie w czasie rzeczywistym = włączone  <br/> Zezwalaj na ochronę w chmurze = włączone  <br/> Pytaj użytkowników o przesyłane próbki = Wyślij bezpieczne próbki automatycznie (domyślnie bez automatycznego wysyłania identyfikowalnych danych osobowych)  <br/> |
|Chroń komputery przed zagrożeniami internetowymi w programie Microsoft Edge  <br/> |**SmartScreen** w obszarze **Ustawienia przeglądarki Edge**  zostaje ustawiona wartość **Wymagane**.  <br/> |
|Wyłącz ekran urządzenia po takim czasie (minuty)  <br/> |Maksymalna liczba minut braku aktywności przed zablokowaniem ekranu (minuty)  <br/> |
|Zezwalaj użytkownikom na pobieranie aplikacji z witryny Microsoft Store  <br/> |Niestandardowe zasady URI  <br/> |
|Zezwalaj użytkownikom na korzystanie z Cortany  <br/> |**Ogólne** \> **Cortana** jest ustawiona na blokowanie **w** usłudze Intune, gdy jest ona **ustawiona na wartość Wyłączone** w Microsoft 365 Business Premium.  <br/> |
|Zezwalaj użytkownikom na otrzymywanie porad i reklam dotyczących systemu Windows od firmy Microsoft  <br/> |**Windows polecane**, wszystkie zablokowane, jeśli ta funkcja jest ustawiona **na wyłączone w** Microsoft 365 Business Premium.  <br/> |
|Automatycznie aktualizuj urządzenia z systemem Windows 10  <br/> | To ustawienie **znajduje się w** Microsoft Intune \> **aktualizacji usługi —** Windows 10 Pierścienie aktualizacji, wybierz pozycję Zasady aktualizacji **dla Windows 10** urządzeń, a **następnie pozycję** \> **Właściwości Ustawienia**.  <br/>  Gdy ustawienie Microsoft 365 Business Premium jest ustawione na **Wartość Wł**., są ustawione wszystkie następujące ustawienia:  <br/> **Gałąź** usługi ma ustawioną **wartość CB** (CBB, gdy ta gałąź jest Microsoft 365 Business Premium).  <br/> **Aktualizacje produktów firmy Microsoft**  zostaje ustawiona wartość **Zezwalaj**.  <br/> **Sterowniki systemu Windows**  zostaje ustawiona wartość **Zezwalaj**.  <br/> **Zachowanie automatycznych aktualizacji**  zostaje ustawiona wartość **Automatycznie zainstaluj podczas konserwacji** oraz:  <br/> **Początek godzin aktywnego użytkowania**  zostaje ustawiona wartość **6:00**.  <br/> **Koniec godzin aktywnego użytkowania**  zostaje ustawiona wartość **22:00**.  <br/> **Okres odroczenia aktualizacji dotyczących jakości (dni)**  zostaje ustawiona wartość **0**.  <br/> **Okres odroczenia aktualizacji funkcji (dni)**  zostaje ustawiona wartość **0**.  <br/> **Tryb pobierania optymalizacji dostarczania**  zostaje ustawiona wartość **HTTP w połączeniu z komunikacją równorzędną za tym samym translatorem adresów sieciowych**.  <br/> |
|||
