---
title: Zarządzanie aktywną zawartością w dokumentach Office dla administratorów IT
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: Admin
ms.topic: tutorial
ms.localizationpriority: medium
ms.prod: m365-security
ms.collection:
- M365-security-compliance
search.appverid:
- MET150
ROBOTS: NOINDEX,NOFOLOW
description: Administratorzy mogą dowiedzieć się, jak tworzyć zasady blokowania aktywnej zawartości w dokumentach Office
ms.openlocfilehash: 7a24c56bdd388f2dc9a8f408b52b2de1c6805a0a
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65100946"
---
# <a name="manage-active-content-in-office-documents"></a>Zarządzanie aktywną zawartością w dokumentach pakietu Office

> [!NOTE]
> Funkcje opisane w tym artykule są w wersji zapoznawczej, nie są dostępne dla wszystkich i mogą ulec zmianie.

Office dokumenty mogą być automatycznie odświeżane, aktualizowane lub wykonywane, gdy zawierają _aktywną zawartość_. Przykładami aktywnej zawartości są makra, kontrolki ActiveX i dodatki Office. Aktywna zawartość może zapewniać użytkownikom zaawansowane i przydatne funkcje, ale osoby atakujące mogą również używać aktywnej zawartości do dostarczania złośliwego oprogramowania.

Administratorzy mogą tworzyć zasady organizacji (zasady grupy lub zasady w chmurze), które ograniczają korzystanie z aktywnej zawartości do określonych zestawów użytkowników lub całkowicie wyłączają aktywną zawartość. Użytkownicy mogą konfigurować własne ustawienia zabezpieczeń i prywatności w centrum zaufania Office w swoich aplikacjach Office w **Centrum zaufania** **opcji** \> **plików**\>.

Wcześniej, gdy użytkownicy identyfikowali dokumenty jako zaufane dokumenty, ich wybór umożliwiał uruchamianie aktywnej zawartości, nawet jeśli administrator skonfigurował zasady do blokowania aktywnej zawartości w Office dokumentach. Teraz zasady ustawione przez administratorów mają pierwszeństwo przed identyfikacją zaufanych dokumentów przez użytkownika. Ta zmiana zachowania może powodować problemy dla użytkowników.

Zaktualizowana logika Centrum zaufania została opisana na poniższym diagramie:

:::image type="content" source="../media/office-trust-center-flow.png" alt-text="Wykres blokowy opisujący logikę centrum zaufania w portalu Microsoft 365 Defender" lightbox="../media/office-trust-center-flow.png":::

1. Użytkownik otwiera dokument Office zawierający aktywną zawartość.

2. Jeśli dokument pochodzi z zaufanej lokalizacji, dokument jest otwierany z włączoną aktywną zawartością. Jeśli dokument nie pochodzi z zaufanej lokalizacji, ocena będzie kontynuowana.

3. W tym miejscu zaktualizowane zachowanie jest skuteczne:
   - Wcześniej następnym ocenionym ustawieniem byłoby, gdyby użytkownik zidentyfikował ten dokument jako zaufany dokument. Jeśli tak się stało, dokument zostanie otwarty z włączoną aktywną zawartością.
   - Teraz nie jest brane pod uwagę, czy użytkownik zidentyfikował dokument jako zaufany dokument (teraz w kroku 8).

     Podstawowa zmiana zachowania jest opisana w następujący sposób: zasady w chmurze (krok 4), zasady grupy (krok 6) i ustawienia lokalne (krok 7) są sprawdzane _przed rozważeniem_ oznaczenia zaufanego dokumentu przez użytkownika. Jeśli którykolwiek z tych kroków blokuje dostęp do aktywnej zawartości **i** żaden z kroków nie zezwala na zastępowanie przez użytkownika, identyfikacja dokumentu jako dokumentu zaufanego jest nieistotna.

4. Zasady chmury są sprawdzane, aby sprawdzić, czy ten typ aktywnej zawartości jest dozwolony lub zablokowany. Jeśli aktywna zawartość nie zostanie zablokowana, ocena będzie kontynuowana w kroku 6.

   Jeśli aktywna zawartość zostanie zablokowana przez zasady, środowisko zostanie opisane w kroku 5.

5. Otwieranie dokumentu jest blokowane z powiadomieniem na pasku zaufania. To, co dzieje się dalej, jest kontrolowane przez ustawienia przesłonięcia przez użytkownika w zasadach: a. **Przesłonięcia użytkownika są niedozwolone**: użytkownik nie może otworzyć dokumentu i ocena zostanie zatrzymana.
   b. **Dozwolone zastąpienie przez użytkownika**: użytkownik może kliknąć link na pasku zaufania, aby otworzyć dokument z włączoną aktywną zawartością.

6. Zasady grupy są sprawdzane, aby sprawdzić, czy ten typ aktywnej zawartości jest dozwolony lub zablokowany. Jeśli aktywna zawartość nie zostanie zablokowana, ocena będzie kontynuowana w kroku 7.

   Jeśli aktywna zawartość zostanie zablokowana przez zasady, środowisko zostanie opisane w kroku 5.

7. Ustawienia lokalne są sprawdzane, aby sprawdzić, czy ten typ aktywnej zawartości jest dozwolony lub zablokowany. Jeśli aktywna zawartość jest zablokowana, otwieranie dokumentu jest blokowane z powiadomieniem na pasku zaufania. Jeśli aktywna zawartość nie zostanie zablokowana, ocena będzie kontynuowana.

8. Jeśli użytkownik wcześniej zidentyfikował dokument jako dokument zaufany, dokument zostanie otwarty z włączoną aktywną zawartością. Jeśli nie, otwieranie dokumentu jest zablokowane.

## <a name="what-is-a-trusted-document"></a>Co to jest zaufany dokument?

Zaufane dokumenty są Office dokumentów, które są otwierane bez monitów o zabezpieczenia makr, kontrolek ActiveX i innych typów aktywnej zawartości w dokumencie. Do otwierania dokumentu nie jest używany widok chroniony ani funkcja Application Guard. Gdy użytkownicy otwierają zaufany dokument, a cała aktywna zawartość jest włączona. Nawet jeśli dokument zawiera nową aktywną zawartość lub aktualizacje istniejącej aktywnej zawartości, użytkownicy nie będą otrzymywać monitów o zabezpieczenia przy następnym otwarciu dokumentu.

Z tego powodu użytkownicy powinni wyraźnie ufać dokumentom tylko wtedy, gdy ufają źródle dokumentu.

Jeśli administrator zablokuje aktywną zawartość przy użyciu zasad lub jeśli użytkownicy ustawią ustawienie Centrum zaufania, które blokuje aktywną zawartość, aktywna zawartość pozostanie zablokowana.

Aby uzyskać więcej informacji, zapoznaj się z następującymi artykułami:

- [Zaufane dokumenty](https://support.microsoft.com/topic/trusted-documents-cf872bd8-47ec-4c02-baa5-1fdba1a11b53)
- [Dodawanie, usuwanie lub zmienianie zaufanej lokalizacji](https://support.microsoft.com/topic/add-remove-or-change-a-trusted-location-7ee1cdc2-483e-4cbb-bcb3-4e7c67147fb4)
- [Aktywne typy zawartości w plikach](https://support.microsoft.com/topic/active-content-types-in-your-files-b7ff2e8a-4055-47d4-8c7d-541e19f62bea)

## <a name="configure-trusted-document-settings-in-office-policies"></a>Konfigurowanie ustawień zaufanego dokumentu w zasadach Office

Administratorzy mają wiele sposobów konfigurowania Office w organizacji. Przykład:

- **Office usługi zasad w chmurze**: skonfiguruj zasady oparte na użytkownikach, które mają zastosowanie do użytkownika na dowolnym urządzeniu uzyskującym dostęp do plików w aplikacjach Office przy użyciu konta usługi Azure AD. Zobacz kroki [tworzenia konfiguracji zasad w chmurze Office](/DeployOffice/overview-office-cloud-policy-service) w [usłudze Office Cloud Policy Service](https://config.office.com/officeSettings/officePolicies).
- **Office zasad w Intune**: użyj wykazu Intune Ustawienia lub szablonów administracyjnych, aby wdrożyć zasady HKCU do Windows 10 komputerów: w [centrum administracyjnym MEM](https://endpoint.microsoft.com/#blade/Microsoft_Intune_DeviceSettings/DevicesMenu/configurationProfiles) w obszarze **Profile konfiguracji** **urządzeń**\>.
  - ***Szablony administracyjne***: zobacz instrukcje dotyczące używania szablonów Windows 10 do konfigurowania [szablonów administracyjnych](/mem/intune/configuration/administrative-templates-windows).
  - ***wykaz Ustawienia (wersja zapoznawcza)***: zobacz instrukcje dotyczące korzystania z [wykazu Ustawienia (wersja zapoznawcza)](/mem/intune/configuration/settings-catalog).
- **Zasady grupy**: użyj lokalnej usługi Active Directory, aby wdrożyć obiekty zasad grupy (GPO) dla użytkowników i komputerów. Aby utworzyć obiekt zasad grupy dla tego ustawienia, pobierz najnowsze [pliki szablonów administracyjnych (ADMX/ADML) i Office Customization Tool for Aplikacje Microsoft 365 dla przedsiębiorstw, Office 2019 i Office 2016](https://www.microsoft.com/download/details.aspx?id=49030).

## <a name="known-issues"></a>Znane problemy

- Gdy **powiadomienia makr VBA** zasad (dostęp, PowerPoint, Visio, Word) lub **powiadomienia makr** (Excel) są ustawione na wartość **Wyłącz wszystkie z wyjątkiem makr podpisanych cyfrowo**, oczekiwany pasek zaufania nie jest wyświetlany, a **informacje o zabezpieczeniach** na zapleczu nie zawierają listy szczegółów zablokowanych makr, mimo że ustawienie działa zgodnie z oczekiwaniami. Zespół Office pracuje nad rozwiązaniem tego problemu.

## <a name="admin-options-for-restricting-active-content"></a>Opcje administratora dotyczące ograniczania aktywnej zawartości

Istnieje duża różnica w poziomie zaufania do zawartości utworzonej wewnętrznie i zawartości pobieranej przez użytkowników z Internetu. Rozważ zezwolenie na aktywną zawartość w dokumentach wewnętrznych i globalne nie zezwalanie na aktywną zawartość w dokumentach z Internetu.

Jeśli użytkownicy nie potrzebują określonych typów aktywnej zawartości, najbezpieczniejszą opcją jest użycie zasad, aby wyłączyć dostęp użytkowników do tej aktywnej zawartości i zezwolić na wyjątki zgodnie z potrzebami.

Dostępne są następujące zasady:

- **Wyłącz pozycję Zaufane lokalizacje**: wyjątki dla dostępnych grup.
- **Wyłącz pozycję Zaufane dokumenty**: wyjątki dla dostępnych grup.
- **Wyłącz całą aktywną zawartość**: wyjątki dla użytkowników indywidualnych.

Tabele w poniższych sekcjach opisują ustawienia kontrolujące aktywną zawartość. Te zasady, jeśli zostaną zastosowane do użytkowników, będą wymuszane w zaufanych dokumentach, a poprzednie środowisko użytkownika końcowego może nie być takie samo. Tabele zawierają również zalecane ustawienie punktów odniesienia zabezpieczeń i identyfikują inne ustawienia, w których jest dostępny monit użytkownika o zastąpienie (dzięki czemu użytkownik może włączyć aktywną zawartość).

### <a name="hkey_current_user-settings"></a>ustawienia HKEY_CURRENT_USER

<p>

****
|Kategoria|Aplikacja|Nazwa zasad|Punkt odniesienia zabezpieczeń<br>ustawienie (zalecane)|Ustawienie z monitem użytkownika<br>i przesłonięcia dostępne?|
|---|---|---|---|---|
|ActiveX|Pakiet Office|Inicjowanie kontrolki ActiveX|**6**|**Tak** dla następujących wartości: <ul><li>**3**</li><li>**4**</li><li>**5**</li><li>**6**</li></ul>|
|ActiveX|Pakiet Office|Zezwalaj na aktywne x jednorazowe formularze|**Ładowanie tylko kontrolek Outlook**|Nie|
|ActiveX|Pakiet Office|Sprawdzanie obiektów ActiveX|Nie jest to ustawienie punktu odniesienia zabezpieczeń.|Nie|
|ActiveX|Pakiet Office|Wyłącz wszystkie ActiveX|Nie jest to ustawienie punktu odniesienia zabezpieczeń.|**Tak** dla następujących wartości: <ul><li>**Wyłączona**</li><li>**Nie skonfigurowano**</li></ul>|
|ActiveX|Pakiet Office|Kontrolki ładowania w formularzach 3|**1**|**Tak** dla następujących wartości: <ul><li>**2**</li><li>**3**</li></ul>|
|Rozszerzalność & dodatków|Excel <p> PowerPoint <p> Project <p> Publisher <p> Visio <p> Word|Wyłączanie powiadomienia paska zaufania dla dodatków niepodpisanych aplikacji i blokowanie ich|**Włączone**|**Tak** dla wartości **Wyłączone**.|
|Rozszerzalność & dodatków|Excel <p> PowerPoint <p> Project <p> Publisher <p> Visio <p> Word|Wymagaj, aby dodatki aplikacji były podpisane przez zaufane Publisher|**Włączone**|Nie|
|Rozszerzalność & dodatków|Excel|Nie pokazuj alertu ostrzegawczego automatycznego publikowania|**Wyłączona**|Nie|
|Rozszerzalność & dodatków|Excel|Ustawienia powiadomień funkcji WEBSERVICE|**Wyłącz wszystko za pomocą powiadomienia**|**Tak** dla następujących wartości: <ul><li>**Wyłącz wszystko za pomocą powiadomienia**</li><li>**Wyłączona**</li><li>**Nie skonfigurowano**</li></ul>|
|Rozszerzalność & dodatków|Pakiet Office|Wyłącz klienta Office przed sondowaniem serwera SharePoint dla opublikowanych linków|**Wyłączona**|Nie|
|Rozszerzalność & dodatków|Pakiet Office|Wyłączanie rozszerzania interfejsu użytkownika z dokumentów i szablonów|Nie zezwalaj w programie Word = True <p> Nie zezwalaj w Project = False <p> Nie zezwalaj w Excel = True <p> Nie zezwalaj w Visio = False <p> Nie zezwalaj w PowerPoint = True <p> Nie zezwalaj w programie Access = True <p> Nie zezwalaj w Outlook = True <p> Nie zezwalaj w Publisher = True <p> Nie zezwalaj w programie InfoPath = True|Nie|
|Rozszerzalność & dodatków|Outlook|Konfigurowanie Outlook monitu modelu obiektów podczas uzyskiwania dostępu do książki adresowej|**Automatycznie odmów**|**Tak** dla następujących wartości: <ul><li>**Monituj użytkownika**</li><li>**Monituj użytkownika na podstawie zabezpieczeń komputera**</li><li>**Wyłączona**</li><li>**Nie skonfigurowano**</li></ul>|
|Rozszerzalność & dodatków|Outlook|Konfigurowanie Outlook wiersza polecenia modelu obiektów podczas uzyskiwania dostępu do właściwości Formula obiektu UserProperty|**Automatycznie odmów**|**Tak** dla następujących wartości: <ul><li>**Monituj użytkownika**</li><li>**Monituj użytkownika na podstawie zabezpieczeń komputera**</li><li>**Wyłączona**</li><li>**Nie skonfigurowano**</li></ul>|
|Rozszerzalność & dodatków|Outlook|Konfigurowanie monitu Outlook modelu obiektów podczas wykonywania polecenia Zapisz jako|**Automatycznie odmów**|**Tak** dla następujących wartości: <ul><li>**Monituj użytkownika**</li><li>**Monituj użytkownika na podstawie zabezpieczeń komputera**</li><li>**Wyłączona**</li><li>**Nie skonfigurowano**</li></ul>|
|Rozszerzalność & dodatków|Outlook|Konfigurowanie monitu modelu obiektów Outlook podczas odczytywania informacji o adresie|**Automatycznie odmów**|**Tak** dla następujących wartości: <ul><li>**Monituj użytkownika**</li><li>**Monituj użytkownika na podstawie zabezpieczeń komputera**</li><li>**Wyłączona**</li><li>**Nie skonfigurowano**</li></ul>|
|Rozszerzalność & dodatków|Outlook|Konfigurowanie Outlook monitu modelu obiektu podczas odpowiadania na żądania dotyczące spotkań i zadań|**Automatycznie odmów**|**Tak** dla następujących wartości: <ul><li>**Monituj użytkownika**</li><li>**Monituj użytkownika na podstawie zabezpieczeń komputera**</li><li>**Wyłączona**</li><li>**Nie skonfigurowano**</li></ul>|
|Rozszerzalność & dodatków|Outlook|Konfigurowanie Outlook wiersza polecenia modelu obiektu podczas wysyłania wiadomości e-mail|**Automatycznie odmów**|**Tak** dla następujących wartości: <ul><li>**Monituj użytkownika**</li><li>**Monituj użytkownika na podstawie zabezpieczeń komputera**</li><li>**Wyłączona**</li><li>**Nie skonfigurowano**</li></ul>|
|Rozszerzalność & dodatków|Outlook|Ustawianie wiersza polecenia wykonywania niestandardowych akcji modelu obiektów Outlook|**Automatycznie odmów**|**Tak** dla następujących wartości: <ul><li>**Monituj użytkownika**</li><li>**Monituj użytkownika na podstawie zabezpieczeń komputera**</li><li>**Wyłączona**</li><li>**Nie skonfigurowano**</li></ul>|
|Rozszerzalność & dodatków|PowerPoint|Uruchamianie programów|**wyłącz (nie uruchamiaj żadnych programów)**|**Tak** dla wartości **Włącz (monituj użytkownika przed uruchomieniem)**|
|Rozszerzalność & dodatków|Word <p> Excel|Wyłączanie używania manifestów przez dokument inteligentny|**Włączone**|Nie|
|DDE|Excel|Nie zezwalaj na uruchamianie serwera usługi Dynamic Data Exchange (DDE) w Excel|**Włączone**|**Tak** dla wartości **Nie skonfigurowano**.|
|DDE|Excel|Nie zezwalaj na wyszukiwanie serwera usługi Dynamic Data Exchange (DDE) w Excel|**Włączone**|**Tak** dla następujących wartości: <ul><li>**Wyłączona**</li><li>**Nie skonfigurowano**</li></ul>|
|DDE|Word|Dynamiczne Exchange danych|**Wyłączona**|Nie|
|Jscript & VBScript|Outlook|Zezwalaj na skrypty w jednorazowych formularzach Outlook|**Wyłączona**|Nie|
|Jscript & VBScript|Outlook|Nie zezwalaj na uruchamianie skryptów modelu obiektów Outlook dla folderów publicznych|**Włączone**|Nie|
|Jscript & VBScript|Outlook|Nie zezwalaj na uruchamianie skryptów modelu obiektów Outlook dla folderów udostępnionych|**Włączone**|Nie|
|Makra|Excel|Powiadomienia makr|**Wyłącz wszystkie z wyjątkiem makr podpisanych cyfrowo**|**Tak** dla następujących wartości: <ul><li>**Wyłączona**</li><li>**Nie skonfigurowano**</li></ul>|
|Makra|Access <p> PowerPoint <p> Project <p> Publisher <p> Visio <p> Word|Ustawienia powiadomień makr VBA|**Wyłącz wszystkie z wyjątkiem makr podpisanych cyfrowo** <p> i <p> **Wymaganie podpisania makr przez zaufanego wydawcę**|**Tak** dla następujących wartości: <ul><li>**Wyłączona**</li><li>**Nie skonfigurowano**</li></ul>|
|Makra|Access <p> Excel <p> PowerPoint <p> Visio <p> Word|Blokowanie uruchamiania makr w plikach Office z Internetu|**Włączone**|**Tak** dla następujących wartości: <ul><li>**Wyłączona**</li><li>**Nie skonfigurowano**</li></ul>|
|Makra|Excel|Skanowanie zaszyfrowanych makr w Excel skoroszytów Open XML|**Skanowanie zaszyfrowanych makr (domyślne)**|Nie|
|Makra|Pakiet Office|Zezwalaj usłudze VBA na ładowanie odwołań typelib według ścieżki z niezaufanych lokalizacji intranetowych|**Wyłączona**|Nie|
|Makra|Pakiet Office|Zabezpieczenia automatyzacji|**Korzystanie z poziomu zabezpieczeń makr aplikacji**|Nie|
|Makra|Pakiet Office|Wyłączanie innych kontroli zabezpieczeń odwołań do biblioteki VBA, które mogą odwoływać się do niebezpiecznych lokalizacji na komputerze lokalnym|**Wyłączona**|Nie|
|Makra|Pakiet Office|Zakres skanowania środowiska uruchomieniowego makr|**Włącz dla wszystkich dokumentów**|Nie|
|Makra|Pakiet Office|Ufaj tylko makram VBA, które używają sygnatur w wersji 3|Nie jest to ustawienie punktu odniesienia zabezpieczeń.|Nie|
|Makra|Outlook|tryb zabezpieczeń Outlook|**Korzystanie z Outlook Security zasady grupy**|Wymagane do włączenia wszystkich Outlook ustawień obiektu zasad grupy. <p> Wymienione jako zależność (te zasady nie blokują samej aktywnej zawartości).|
|Makra|Outlook|Ustawienie zabezpieczeń dla makr|**Ostrzegaj przed podpisem, wyłącz niepodpisane**|**Tak** dla następujących wartości: <ul><li>**Zawsze ostrzegaj**</li><li>**Ostrzegaj przed podpisem, wyłącz niepodpisane**</li><li>**Wyłączona**</li><li>**Nie skonfigurowano**</li></ul>|
|Makra|PowerPoint|Skanowanie zaszyfrowanych makr w PowerPoint prezentacji Open XML|**Skanowanie zaszyfrowanych makr (domyślne)**|Nie|
|Makra|Publisher|Poziom zabezpieczeń usługi Publisher Automation|**Według interfejsu użytkownika (monit)**|Nie|
|Makra|Word|Skanowanie zaszyfrowanych makr w dokumentach Open XML programu Word|**Skanowanie zaszyfrowanych makr (domyślne)**|Nie|
|

### <a name="hkey_local_machine-settings"></a>ustawienia HKEY_LOCAL_MACHINE

<p>

****
|Kategoria|Aplikacja|Nazwa zasad|Punkt odniesienia zabezpieczeń<br>ustawienie (zalecane)|Ustawienie z monitem użytkownika<br>i przesłonięcia dostępne?|
|---|---|---|---|---|
|ActiveX|Pakiet Office|Ograniczanie instalacji ActiveX|excel.exe = True <p> exprwd.exe = True <p> groove.exe = True <p> msaccess.exe = True <p> mse7.exe = True <p> mspub.exe = True <p> onent.exe = True <p> outlook.exe = True <p> powerpnt.exe = True <p> pptview.exe = True <p> spDesign.exe = True <p> visio.exe = True <p> winproj.exe = True <p> winword.exe = True|Nie|
|Rozszerzalność & dodatków|Pakiet Office|Zarządzanie dodatkami|excel.exe = True <p> exprwd.exe = True <p> groove.exe = True <p> msaccess.exe = True <p> mse7.exe = True <p> mspub.exe = True <p> onent.exe = True <p> outlook.exe = True <p> powerpnt.exe = True <p> pptview.exe = True <p> spDesign.exe = True <p> visio.exe = True <p> winproj.exe = True <p> winword.exe = True|Nie|
|Rozszerzalność & dodatków|Pakiet Office|Blokuj aktywację flash w dokumentach Office|Aby uzyskać listę killbitów COM, zobacz Pliki ADMX/ADML przewodnika po zabezpieczeniach firmy Microsoft, aby zablokować całą aktywację dla programu Flash w Microsoft 365 aplikacji. Pliki ADMX/ADML dla punktów odniesienia zabezpieczeń przedsiębiorstwa są dostępne w zestawie [narzędzi do zgodności zabezpieczeń](https://www.microsoft.com/download/details.aspx?id=55319).|Nie|
|Jscript & VBScript|Pakiet Office|Ograniczanie starszego wykonywania JScript dla Office|**Włączone**: <p> Dostęp: 69632 <p> Excel: 69632 <p> OneNote: 69632 <p> Outlook: 69632 <p> PowerPoint: 69632 <p> Project: 69632 <p> Publisher: 69632 <p> Visio: 69632 <p> Word: 69632|Nie|
|Jscript & VBScript|Pakiet Office|Ograniczenia zabezpieczeń okna skryptowego|excel.exe = True <p> exprwd.exe = True <p> groove.exe = True <p> msaccess.exe = True <p> mse7.exe = True <p> mspub.exe = True <p> onent.exe = True <p> outlook.exe = True <p> powerpnt.exe = True <p> pptview.exe = True <p> spDesign.exe = True <p> visio.exe = True <p> winproj.exe = True <p> winword.exe = True|Nie|
|
