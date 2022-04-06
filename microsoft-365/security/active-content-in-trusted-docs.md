---
title: Zarządzanie zawartością aktywną w Office dla administratorów IT
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
description: Administratorzy mogą dowiedzieć się, jak tworzyć zasady blokowania zawartości aktywnej w Office dokumentach
ms.openlocfilehash: 33d53ab14fec1b6cd16b8de95befe8bc8a898e16
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2022
ms.locfileid: "64468926"
---
# <a name="manage-active-content-in-office-documents"></a>Zarządzanie zawartością aktywną w Office dokumentów

> [!NOTE]
> Funkcje opisane w tym artykule są dostępne w wersji Preview, są niedostępne dla wszystkich i mogą ulec zmianie.

Office dokumenty mogą być automatycznie odświeżane, aktualizowane lub wykonywane w przypadku, gdy zawierają _zawartość aktywną_. Przykładami zawartości aktywnej są makra, kontrolki ActiveX i Office dodatki. Zawartość aktywna może zapewniać użytkownikom zaawansowane i przydatne funkcje, ale atakujący mogą też używać zawartości aktywnej do dostarczania złośliwego oprogramowania.

Administratorzy mogą tworzyć zasady organizacji (zasady grupy lub zasady chmury), które ograniczają użycie zawartości aktywnej do określonych zestawów użytkowników lub całkowicie wyłączą zawartość aktywną. Użytkownicy mogą konfigurować własne ustawienia zabezpieczeń i prywatności w Centrum Office zaufania w swoich Office w  \>  \> Centrum **zaufania opcje plików**.

Wcześniej, gdy użytkownicy zidentyfikowali dokumenty jako zaufane dokumenty, ich wybór pozwalał na uruchamianie zawartości aktywnej, nawet jeśli administrator skonfigurował zasady blokowania zawartości aktywnej w Office dokumentów. Teraz zasady ustawione przez administratorów mają pierwszeństwo przed identyfikacją zaufanych dokumentów przez użytkowników. Ta zmiana w zachowaniu może powodować problemy dla użytkowników.

Zaktualizowana logika Centrum zaufania jest opisana na poniższym diagramie:

:::image type="content" source="../media/office-trust-center-flow.png" alt-text="Schemat blokowy z opisem logiki Centrum zaufania w portalu Microsoft 365 Defender zaufania" lightbox="../media/office-trust-center-flow.png":::

1. Użytkownik otwiera dokument programu Office zawierający zawartość aktywną.

2. Jeśli dokument pochodzi z zaufanej lokalizacji, zostanie otwarty z włączoną zawartością aktywną. Jeśli dokument nie pochodzi z zaufanej lokalizacji, ocena będzie kontynuowana.

3. Oto zaktualizowane zachowanie zostanie wprowadzone:
   - Wcześniej następne oceniane ustawienie było, gdyby użytkownik zidentyfikował ten dokument jako zaufany dokument. W przypadku gdyby tak było, dokument zostanie otwarty z włączoną zawartością aktywną.
   - Teraz, niezależnie od tego, czy użytkownik zidentyfikował dokument jako zaufany dokument, nie jest tu rozważany (obecnie w kroku 8).

     Podstawową zmianę zachowania opisano w następujący sposób: zasady chmury (krok 4), zasady grupy (krok 6) i ustawienia lokalne (krok 7) są sprawdzane przed  oznaczeniem zaufanego dokumentu przez użytkownika. Jeśli którykolwiek z tych kroków blokuje dostęp do zawartości aktywnej i żaden z kroków nie zezwala na zastępowanie przez użytkownika, oznacza to, że identyfikacja przez użytkownika dokumentu jako zaufanego dokumentu nie ma znaczenia.

4. Zasady chmury są sprawdzane, aby sprawdzić, czy tego typu zawartość aktywna jest dozwolona, czy blokowana. Jeśli zawartość aktywna nie zostanie zablokowana, ocena będzie kontynuowana do kroku 6.

   Jeśli zawartość aktywna jest blokowana przez zasady, środowisko jest opisane w kroku 5.

5. Otwarcie dokumentu zostanie zablokowane z powiadomieniem na pasku zaufania. To, co się dzieje w następnej sytuacji, jest kontrolowane przez użytkownika zastępującego ustawienia w zasadach: a. **Użytkownik może zastąpić niedozwolone**: Użytkownik nie może otworzyć dokumentu i proces oceny zostanie zatrzymany.
   b. **Użytkownik może zastąpić:** Użytkownik może kliknąć link na pasku zaufania, aby otworzyć dokument z włączoną zawartością aktywną.

6. Zasady grupy są sprawdzane, aby sprawdzić, czy tego typu zawartość aktywna jest dozwolona, czy blokowana. Jeśli zawartość aktywna nie zostanie zablokowana, ocena będzie kontynuowana do kroku 7.

   Jeśli zawartość aktywna jest blokowana przez zasady, środowisko jest opisane w kroku 5.

7. Ustawienia lokalne są sprawdzane, aby sprawdzić, czy zawartość aktywna tego typu jest dozwolona, czy blokowana. Jeśli zawartość aktywna zostanie zablokowana, otwarcie dokumentu zostanie zablokowane z powiadomieniem na pasku zaufania. Jeśli zawartość aktywna nie zostanie zablokowana, ocena będzie kontynuowana.

8. Jeśli użytkownik zidentyfikował wcześniej dokument jako zaufany dokument, zostanie on otwarty z włączoną zawartością aktywną. W innych wąsach otwarcie dokumentu jest blokowane.

## <a name="what-is-a-trusted-document"></a>Co to jest zaufany dokument?

Zaufane dokumenty są Office dokumentami, które są otwierane bez żadnych monitów zabezpieczeń dotyczących makr ActiveX kontrolek sieci ActiveX i innych typów zawartości aktywnej w dokumencie. Widok chroniony ani application Guard nie są używane do otwierania dokumentu. Po otwarciu zaufanego dokumentu przez użytkownika i włączeniu całej zawartości aktywnej. Nawet jeśli dokument zawiera nową zawartość aktywną lub aktualizacje istniejącej zawartości aktywnej, użytkownicy nie będą otrzymywać monitów zabezpieczeń przy następnym otwarciu dokumentu.

Z tego powodu użytkownicy powinni wyraźnie ufać dokumentom tylko wtedy, gdy są zaufanymi źródłami dokumentów.

Jeśli administrator blokuje zawartość aktywną przy użyciu zasad lub jeśli użytkownik ustawi ustawienie Centrum zaufania blokujące zawartość aktywną, zawartość aktywna pozostanie zablokowana.

Aby uzyskać więcej informacji, zapoznaj się z następującymi artykułami:

- [Zaufane dokumenty](https://support.microsoft.com/topic/trusted-documents-cf872bd8-47ec-4c02-baa5-1fdba1a11b53)
- [Dodawanie, usuwanie lub zmienianie zaufanej lokalizacji](https://support.microsoft.com/topic/add-remove-or-change-a-trusted-location-7ee1cdc2-483e-4cbb-bcb3-4e7c67147fb4)
- [Typy zawartości aktywnej w plikach](https://support.microsoft.com/topic/active-content-types-in-your-files-b7ff2e8a-4055-47d4-8c7d-541e19f62bea)

## <a name="configure-trusted-document-settings-in-office-policies"></a>Konfigurowanie ustawień zaufanych dokumentów w Office dokumentów

Administratorzy mają wiele sposobów konfigurowania Office w organizacji. Przykład:

- **Office usługi zasad** w chmurze: Skonfiguruj zasady oparte na użytkownikach, które mają zastosowanie do użytkownika na dowolnym urządzeniu, które ma dostęp do plików w aplikacji Office za pomocą konta usługi Azure AD. Zapoznaj się z krokami [tworzenia konfiguracji zasad Office chmurze](/DeployOffice/overview-office-cloud-policy-service) w [usłudze Office w chmurze](https://config.office.com/officeSettings/officePolicies).
- **Office** w programie Intune: Użyj wykazu Intune Ustawienia lub szablonów administracyjnych, aby wdrożyć zasady usługi HKCU na Windows 10 PC: W centrum administracyjnym [MEM](https://endpoint.microsoft.com/#blade/Microsoft_Intune_DeviceSettings/DevicesMenu/configurationProfiles)  \> w obszarze Profile konfiguracji **urządzeń.**
  - ***Szablony administracyjne***: Zobacz instrukcje dotyczące używania Windows 10 do [konfigurowania szablonów administracyjnych](/mem/intune/configuration/administrative-templates-windows).
  - ***Ustawienia (wersja zapoznawcza)***: Zobacz instrukcje dotyczące korzystania [z Ustawienia (wersja zapoznawcza)](/mem/intune/configuration/settings-catalog).
- **Zasady grupy**. Użyj lokalnego usługi Active Directory, aby wdrożyć obiekty zasad grupy (GPOs) u użytkowników i komputerów. Aby utworzyć zasadę zasad grupy dla tego ustawienia, pobierz najnowsze pliki szablonów administracyjnych [(ADMX/ADML) i narzędzie do dostosowywania usługi Office dla wersji Aplikacje Microsoft 365 dla przedsiębiorstw, Office 2019 i Office 2016](https://www.microsoft.com/download/details.aspx?id=49030).

## <a name="known-issues"></a>Znane problemy

- Gdy zasady Powiadomienia makr **VBA** (Access, PowerPoint, Visio, Word) lub Powiadomienia **makr (Excel**) są ustawione na wartość Wyłącz wszystkie oprócz makr podpisanych cyfrowo **, oczekiwany** pasek zaufania nie jest wyświetlany, a informacje o zabezpieczeniach w backstage nie zawierają listy  zablokowanych makr, nawet jeśli to ustawienie działa zgodnie z oczekiwaniami. Zespół Office pracuje nad rozwiązaniem tego problemu.

## <a name="admin-options-for-restricting-active-content"></a>Opcje administratora dotyczące ograniczania zawartości aktywnej

Istnieje duża różnica w poziomie zaufania w zawartości utworzonej wewnętrznie a w zawartości, która jest tworzona przez użytkowników z Internetu. Rozważ zezwolenie na zawartość aktywną w dokumentach wewnętrznych, a globalnie nie zezwalanie na zawartość aktywną w dokumentach z Internetu.

Jeśli użytkownicy nie potrzebują konkretnych typów zawartości aktywnej, najbezpieczniejszym rozwiązaniem jest użycie zasad w celu wyłączenia dostępu użytkowników do tej zawartości aktywnej i w razie potrzeby zezwalania na wyjątki.

Dostępne są następujące zasady:

- **Wyłącz zaufane lokalizacje**: wyjątki dla grup.
- **Wyłącz zaufane dokumenty: wyjątki** dla grup.
- **Wyłącz całą zawartość aktywną**: Wyjątki dla poszczególnych osób.

W poniższych sekcjach opisano ustawienia kontrolujące zawartość aktywną. Te zasady, jeśli mają zastosowanie do użytkowników, będą wymuszane w zaufanych dokumentach, a poprzednie środowisko użytkownika końcowego może nie być takie same. Tabele zawierają również zalecane ustawienie planu bazowego zabezpieczeń i identyfikują inne ustawienia, w których użytkownik może zastąpić monit (umożliwiający użytkownikowi włączenie zawartości aktywnej).

### <a name="hkey_current_user-settings"></a>HKEY_CURRENT_USER ustawienia

<p>

****
|Kategoria|Aplikacja|Nazwa zasad|Plan bazowy zabezpieczeń<br>ustawienie (zalecane)|Ustawienie z monitem użytkownika<br>i zastąpić dostępne?|
|---|---|---|---|---|
|ActiveX|Pakiet Office|ActiveX inicjowania kontroli|**6**|**Tak** dla następujących wartości: <ul><li>**3**</li><li>**4**</li><li>**5**</li><li>**6**</li></ul>|
|ActiveX|Pakiet Office|Zezwalaj na formularze ActiveX One Off|**Ładowanie tylko Outlook sterowania**|Nie|
|ActiveX|Pakiet Office|Sprawdzanie ActiveX obiektów|Nie jest to ustawienie planu bazowego zabezpieczeń.|Nie|
|ActiveX|Pakiet Office|Wyłącz wszystkie ActiveX|Nie jest to ustawienie planu bazowego zabezpieczeń.|**Tak** dla następujących wartości: <ul><li>**Wyłączone**</li><li>**Nieskonfigurowane**</li></ul>|
|ActiveX|Pakiet Office|Ładowanie kontrolek w formularzu 3|**1**|**Tak** dla następujących wartości: <ul><li>**2**</li><li>**3**</li></ul>|
|Dodatki z & rozszerzalności|Excel <p> PowerPoint <p> Project <p> Publisher <p> Visio <p> Word|Wyłączanie powiadomień na pasku zaufania dla niepodpisanych dodatków aplikacji i blokowanie ich|**Włączone**|**Tak** dla wartości **Wyłączone**.|
|Dodatki z & rozszerzalności|Excel <p> PowerPoint <p> Project <p> Publisher <p> Visio <p> Word|Wymaganie, aby dodatki aplikacji zostały podpisane przez zaufane Publisher|**Włączone**|Nie|
|Dodatki z & rozszerzalności|Excel|Nie pokazuj alertu ostrzegawczego Automatyczne automatyczne opublikowanie ponowne|**Wyłączone**|Nie|
|Dodatki z & rozszerzalności|Excel|Powiadomienie dotyczące funkcji WEBSERVICE Ustawienia|**Wyłącz wszystko, korzystając z powiadomienia**|**Tak** dla następujących wartości: <ul><li>**Wyłącz wszystko, korzystając z powiadomienia**</li><li>**Wyłączone**</li><li>**Nieskonfigurowane**</li></ul>|
|Dodatki z & rozszerzalności|Pakiet Office|Wyłączanie Office z ankiet w programie SharePoint Server dla opublikowanych linków|**Wyłączone**|Nie|
|Dodatki z & rozszerzalności|Pakiet Office|Wyłączanie rozszerzania interfejsu użytkownika na dokumenty i szablony|Disallow in Word = True <p> Nie zezwalaj na Project = Fałsz <p> Nie zezwalaj na Excel = Prawda <p> Disallow in Visio= False <p> Nie zezwalaj na PowerPoint = Prawda <p> Nie zezwalaj w programie Access = True <p> Nie zezwalaj na Outlook = Prawda <p> Nie zezwalaj na Publisher = Prawda <p> Disallow in InfoPath = True|Nie|
|Dodatki z & rozszerzalności|Outlook|Konfigurowanie monitu Outlook modelu obiektów podczas uzyskiwania dostępu do książki adresowej|**Automatycznie odmów**|**Tak** dla następujących wartości: <ul><li>**Monituj użytkownika**</li><li>**Monituj użytkownika na podstawie zabezpieczeń komputera**</li><li>**Wyłączone**</li><li>**Nieskonfigurowane**</li></ul>|
|Dodatki z & rozszerzalności|Outlook|Konfigurowanie Outlook monitu o model obiektu Podczas uzyskiwania dostępu do właściwości Formuła obiektu UserProperty|**Automatycznie odmów**|**Tak** dla następujących wartości: <ul><li>**Monituj użytkownika**</li><li>**Monituj użytkownika na podstawie zabezpieczeń komputera**</li><li>**Wyłączone**</li><li>**Nieskonfigurowane**</li></ul>|
|Dodatki z & rozszerzalności|Outlook|Konfigurowanie Outlook modelu obiektów podczas wykonywania polecenia Zapisz jako|**Automatycznie odmów**|**Tak** dla następujących wartości: <ul><li>**Monituj użytkownika**</li><li>**Monituj użytkownika na podstawie zabezpieczeń komputera**</li><li>**Wyłączone**</li><li>**Nieskonfigurowane**</li></ul>|
|Dodatki z & rozszerzalności|Outlook|Konfigurowanie monitu Outlook modelu obiektów podczas odczytywania informacji adresowych|**Automatycznie odmów**|**Tak** dla następujących wartości: <ul><li>**Monituj użytkownika**</li><li>**Monituj użytkownika na podstawie zabezpieczeń komputera**</li><li>**Wyłączone**</li><li>**Nieskonfigurowane**</li></ul>|
|Dodatki z & rozszerzalności|Outlook|Konfigurowanie monitu Outlook obiektowego podczas odpowiadania na wezwania na spotkania i zadania|**Automatycznie odmów**|**Tak** dla następujących wartości: <ul><li>**Monituj użytkownika**</li><li>**Monituj użytkownika na podstawie zabezpieczeń komputera**</li><li>**Wyłączone**</li><li>**Nieskonfigurowane**</li></ul>|
|Dodatki z & rozszerzalności|Outlook|Konfigurowanie monitu Outlook modelu obiektów podczas wysyłania poczty|**Automatycznie odmów**|**Tak** dla następujących wartości: <ul><li>**Monituj użytkownika**</li><li>**Monituj użytkownika na podstawie zabezpieczeń komputera**</li><li>**Wyłączone**</li><li>**Nieskonfigurowane**</li></ul>|
|Dodatki z & rozszerzalności|Outlook|Ustawianie Outlook wykonywania akcji w modelu obiektów|**Automatycznie odmów**|**Tak** dla następujących wartości: <ul><li>**Monituj użytkownika**</li><li>**Monituj użytkownika na podstawie zabezpieczeń komputera**</li><li>**Wyłączone**</li><li>**Nieskonfigurowane**</li></ul>|
|Dodatki z & rozszerzalności|PowerPoint|Uruchamianie programów|**wyłącz (nie uruchamiaj żadnych programów)**|**Tak** dla wartości **Włącz (monituj użytkownik przed uruchomieniem)**|
|Dodatki z & rozszerzalności|Word <p> Excel|Wyłączanie używania manifestów w dokumencie inteligentnym|**Włączone**|Nie|
|DDE|Excel|Nie zezwalaj na uruchamianie serwera Exchange danych dynamicznych (DDE, Dynamic Data Excel|**Włączone**|**Tak** dla wartości **Nieskonfigurowane**.|
|DDE|Excel|Nie zezwalaj na wyszukiwania na Exchange danych dynamicznych (DDE, Dynamic Data Excel|**Włączone**|**Tak** dla następujących wartości: <ul><li>**Wyłączone**</li><li>**Nieskonfigurowane**</li></ul>|
|DDE|Word|Dynamiczne Exchange|**Wyłączone**|Nie|
|Jscript & VBScript|Outlook|Zezwalaj na skrypty w formularzach Outlook formularzach|**Wyłączone**|Nie|
|Jscript & VBScript|Outlook|Nie zezwalaj na Outlook skryptów modelu obiektów dla folderów publicznych|**Włączone**|Nie|
|Jscript & VBScript|Outlook|Nie zezwalaj na Outlook skryptów modelu obiektów dla folderów udostępnionych|**Włączone**|Nie|
|Makra|Excel|Powiadomienia dotyczące makr|**Wyłącz wszystko oprócz makr podpisanych cyfrowo**|**Tak** dla następujących wartości: <ul><li>**Wyłączone**</li><li>**Nieskonfigurowane**</li></ul>|
|Makra|Access <p> PowerPoint <p> Project <p> Publisher <p> Visio <p> Word|Powiadomienie dotyczące makr VBA Ustawienia|**Wyłącz wszystko oprócz makr podpisanych cyfrowo** <p> i <p> **Wymaganie podpisania makr przez zaufanego wydawcę**|**Tak** dla następujących wartości: <ul><li>**Wyłączone**</li><li>**Nieskonfigurowane**</li></ul>|
|Makra|Access <p> Excel <p> PowerPoint <p> Visio <p> Word|Blokowanie uruchamiania makr w Office plików z Internetu|**Włączone**|**Tak** dla następujących wartości: <ul><li>**Wyłączone**</li><li>**Nieskonfigurowane**</li></ul>|
|Makra|Excel|Skanowanie zaszyfrowanych makr w Excel otwartych skoroszytach XML|**Skanowanie zaszyfrowanych makr (domyślnie)**|Nie|
|Makra|Pakiet Office|Zezwalanie VBA na ładowanie odwołań typulib według ścieżki z niezaufanych lokalizacji intranetowych|**Wyłączone**|Nie|
|Makra|Pakiet Office|Zabezpieczenia automatyzacji|**Używanie poziomu zabezpieczeń makr aplikacji**|Nie|
|Makra|Pakiet Office|Wyłącz inne testy zabezpieczeń odwołań do bibliotek VBA, które mogą odwoływać się do niebezpiecznych lokalizacji na komputerze lokalnym|**Wyłączone**|Nie|
|Makra|Pakiet Office|Zakres skanowania w czasie wykonywania makr|**Włącz dla wszystkich dokumentów**|Nie|
|Makra|Pakiet Office|Ufaj tylko makrom VBA, które używają podpisów V3|Nie jest to ustawienie planu bazowego zabezpieczeń.|Nie|
|Makra|Outlook|Outlook tryb zabezpieczeń|**Korzystanie Outlook zabezpieczeń zasady grupy**|Wymagane do włączenia wszystkich Outlook GPO. <p> Wspomniano jako zależność (te zasady nie blokują samej zawartości aktywnej).|
|Makra|Outlook|Ustawienie zabezpieczeń makr|**Ostrzeganie za podpisem, wyłączanie niepodpisanych**|**Tak** dla następujących wartości: <ul><li>**Zawsze ostrzegaj**</li><li>**Ostrzeganie za podpisem, wyłączanie niepodpisanych**</li><li>**Wyłączone**</li><li>**Nieskonfigurowane**</li></ul>|
|Makra|PowerPoint|Skanowanie zaszyfrowanych makr w PowerPoint Open XML|**Skanowanie zaszyfrowanych makr (domyślnie)**|Nie|
|Makra|Publisher|Publisher poziomu zabezpieczeń automatyzacji|**Według interfejsu użytkownika (monit)**|Nie|
|Makra|Word|Skanowanie zaszyfrowanych makr w dokumentach Open XML programu Word|**Skanowanie zaszyfrowanych makr (domyślnie)**|Nie|
|

### <a name="hkey_local_machine-settings"></a>HKEY_LOCAL_MACHINE ustawienia

<p>

****
|Kategoria|Aplikacja|Nazwa zasad|Plan bazowy zabezpieczeń<br>ustawienie (zalecane)|Ustawienie z monitem użytkownika<br>i zastąpić dostępne?|
|---|---|---|---|---|
|ActiveX|Pakiet Office|Ogranicz ActiveX instalacji|excel.exe = Prawda <p> exprwd.exe = Prawda <p> groove.exe = Prawda <p> msaccess.exe = Prawda <p> mse7.exe = Prawda <p> mspub.exe = Prawda <p> onent.exe = Prawda <p> outlook.exe = Prawda <p> powerpnt.exe = Prawda <p> pptview.exe = Prawda <p> spDesign.exe = Prawda <p> visio.exe = Prawda <p> winproj.exe = Prawda <p> winword.exe = Prawda|Nie|
|Dodatki z & rozszerzalności|Pakiet Office|Zarządzanie zasobami dodatków|excel.exe = Prawda <p> exprwd.exe = Prawda <p> groove.exe = Prawda <p> msaccess.exe = Prawda <p> mse7.exe = Prawda <p> mspub.exe = Prawda <p> onent.exe = Prawda <p> outlook.exe = Prawda <p> powerpnt.exe = Prawda <p> pptview.exe = Prawda <p> spDesign.exe = Prawda <p> visio.exe = Prawda <p> winproj.exe = Prawda <p> winword.exe = Prawda|Nie|
|Dodatki z & rozszerzalności|Pakiet Office|Blokowanie aktywacji w programie Flash Office dokumentach|Zobacz pliki ADMX/ADML przewodnika po zabezpieczeniach firmy Microsoft, aby uzyskać listę plików COM killbits w celu zablokowania wszystkich aktywacji programu Flash w Microsoft 365 aplikacji. Pliki ADMX/ADML dla planu bazowego zabezpieczeń przedsiębiorstwa są dostępne w zestawie [narzędzi do zgodności zabezpieczeń](https://www.microsoft.com/download/details.aspx?id=55319).|Nie|
|Jscript & VBScript|Pakiet Office|Ograniczanie wykonywania starszych JScript w Office|**Włączone**: <p> Access: 69632 <p> Excel: 69632 <p> OneNote: 69632 <p> Outlook: 69632 <p> PowerPoint: 69632 <p> Project: 69632 <p> Publisher: 69632 <p> Visio: 69632 <p> Word: 69632|Nie|
|Jscript & VBScript|Pakiet Office|Ograniczenia zabezpieczeń okien w skryptach|excel.exe = Prawda <p> exprwd.exe = Prawda <p> groove.exe = Prawda <p> msaccess.exe = Prawda <p> mse7.exe = Prawda <p> mspub.exe = Prawda <p> onent.exe = Prawda <p> outlook.exe = Prawda <p> powerpnt.exe = Prawda <p> pptview.exe = Prawda <p> spDesign.exe = Prawda <p> visio.exe = Prawda <p> winproj.exe = Prawda <p> winword.exe = Prawda|Nie|
|
