---
title: Wdrażanie ochrony przed oprogramowaniem wymuszającym okup dla dzierżawy Microsoft 365
author: dansimp
f1.keywords:
- NOCSH
ms.author: dansimp
manager: dansimp
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- Strat_O365_Enterprise
- ransomware
- m365solution-ransomware
- m365solution-overview
ms.custom: seo-marvel-jun2020
keywords: ransomware, oprogramowanie wymuszające okup obsługiwane przez człowieka, oprogramowanie wymuszające okup obsługiwane przez człowieka, HumOR, atak wymuszenia, atak ransomware, szyfrowanie, kryptowirtuologia, zero zaufania
description: Przeprowadź proces ochrony zasobów Microsoft 365 przed atakami wymuszania okupu.
ms.openlocfilehash: fde24132341512d76467284cb2f9c9b11b7d88cc
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2022
ms.locfileid: "64943244"
---
# <a name="deploy-ransomware-protection-for-your-microsoft-365-tenant"></a>Wdrażanie ochrony przed oprogramowaniem wymuszającym okup dla dzierżawy Microsoft 365

Ransomware to rodzaj ataku wymuszenia, który niszczy lub szyfruje pliki i foldery, uniemożliwiając dostęp do krytycznych danych. Towarowe oprogramowanie wymuszające okup zwykle rozprzestrzenia się jak wirus, który infekuje urządzenia i wymaga tylko korygowania złośliwego oprogramowania. Oprogramowanie wymuszające okup obsługiwane przez człowieka jest wynikiem aktywnego ataku cyberprzestępców, który infiltruje lokalną lub chmurową infrastrukturę IT organizacji, podnosi ich uprawnienia i wdraża oprogramowanie wymuszające okup do krytycznych danych.

Po zakończeniu ataku osoba atakująca żąda pieniędzy od ofiar w zamian za usunięte pliki, odszyfrowywanie kluczy dla zaszyfrowanych plików lub obietnicę nieudostępniania poufnych danych do ciemnej sieci Web lub publicznego Internetu. Obsługiwane przez człowieka oprogramowanie wymuszające okup może być również używane do zamykania krytycznych maszyn lub procesów, takich jak te potrzebne do produkcji przemysłowej, doprowadzenia normalnych operacji biznesowych do zatrzymania do czasu zapłaty okupu i skorygowania szkód lub sama organizacja koryguje szkody.

Atak ransomware obsługiwany przez człowieka może być katastrofalny dla firm każdej wielkości i jest trudny do oczyszczenia, co wymaga całkowitej eksmisji przeciwnika w celu ochrony przed przyszłymi atakami. W przeciwieństwie do towarowego oprogramowania wymuszającego okup, oprogramowanie wymuszające okup obsługiwane przez człowieka może nadal zagrażać działalności firm po początkowym żądaniu okupu.

>[!Note]
>Atak wymuszający okup na dzierżawę Microsoft 365 zakłada, że osoba atakująca ma prawidłowe poświadczenia konta użytkownika dla dzierżawy i ma dostęp do wszystkich plików i zasobów, które są dozwolone dla konta użytkownika. Osoba atakująca bez żadnych prawidłowych poświadczeń konta użytkownika musiałaby odszyfrować dane magazynowane, które zostały zaszyfrowane przez Microsoft 365 domyślne i rozszerzone szyfrowanie. Aby uzyskać więcej informacji, zobacz [Omówienie szyfrowania i zarządzania kluczami](/compliance/assurance/assurance-encryption). 
>

Aby uzyskać więcej informacji na temat ochrony przed oprogramowaniem wymuszającym okup w produktach firmy Microsoft, zobacz [te dodatkowe zasoby oprogramowania wymuszającego okup](#additional-ransomware-resources).

## <a name="security-in-the-cloud-is-a-partnership"></a>Bezpieczeństwo w chmurze to partnerstwo

Bezpieczeństwo usług w chmurze firmy Microsoft to partnerstwo między Tobą a firmą Microsoft:

- Usługi w chmurze firmy Microsoft są oparte na fundamencie zaufania i bezpieczeństwa. Firma Microsoft zapewnia mechanizmy kontroli zabezpieczeń i możliwości ułatwiające ochronę danych i aplikacji.
- Jesteś właścicielem danych i tożsamości oraz ponosisz odpowiedzialność za ich ochronę, bezpieczeństwo zasobów lokalnych i bezpieczeństwo składników chmury, które kontrolujesz.

Łącząc te możliwości i obowiązki, możemy zapewnić najlepszą ochronę przed atakiem wymuszającym okup.

## <a name="ransomware-mitigation-and-recovery-capabilities-provided-with-microsoft-365"></a>Funkcje ograniczania ryzyka i odzyskiwania oprogramowania wymuszającego okup dostarczane z Microsoft 365

Osoba atakująca z oprogramowaniem wymuszającym okup, która przeniknęła do dzierżawy Microsoft 365, może zatrzymać organizację dla okupu przez:

- Usuwanie plików lub wiadomości e-mail
- Szyfrowanie plików w miejscu
- Kopiowanie plików poza dzierżawę (eksfiltracja danych)

Jednak Microsoft 365 Usługi online mają wiele wbudowanych funkcji i mechanizmów kontroli, aby chronić dane klientów przed atakami wymuszania okupu. Poniższe sekcje zawierają podsumowanie. Aby uzyskać więcej informacji na temat ochrony danych klientów przez firmę Microsoft, [złośliwego oprogramowania i ochrony przed oprogramowaniem wymuszającym okup w Microsoft 365](/compliance/assurance/assurance-malware-and-ransomware-protection).

>[!Note]
>Atak wymuszający okup na dzierżawę Microsoft 365 zakłada, że osoba atakująca ma prawidłowe poświadczenia konta użytkownika dla dzierżawy i ma dostęp do wszystkich plików i zasobów, które są dozwolone dla konta użytkownika. Osoba atakująca bez żadnych prawidłowych poświadczeń konta użytkownika musiałaby odszyfrować dane magazynowane, które zostały zaszyfrowane przez Microsoft 365 domyślne i rozszerzone szyfrowanie. Aby uzyskać więcej informacji, zobacz [Omówienie szyfrowania i zarządzania kluczami](/compliance/assurance/assurance-encryption). 
>

### <a name="deleting-files-or-email"></a>Usuwanie plików lub wiadomości e-mail

Pliki w SharePoint i OneDrive dla Firm są chronione przez:

- Wersji 

   Microsoft 365 domyślnie zachowuje co najmniej 500 wersji pliku i można je skonfigurować tak, aby zachować więcej. 

   Aby zminimalizować obciążenie personelu ds. zabezpieczeń i pomocy technicznej, wytrenuj użytkowników, jak [przywrócić poprzednie wersje plików](https://support.microsoft.com/office/restore-a-previous-version-of-an-item-or-file-in-sharepoint-f66dbda0-81f4-4d1e-b08c-793265c58934).

- Kosza

   Jeśli oprogramowanie wymuszające okup tworzy nową zaszyfrowaną kopię pliku i usuwa stary plik, klienci mają 93 dni na przywrócenie go z kosza. Po 93 dniach istnieje 14-dniowe okno, w którym firma Microsoft nadal może odzyskać dane. 
  
   Aby zminimalizować obciążenie pracowników działu zabezpieczeń i pomocy technicznej, przeszkol użytkowników, jak [przywracać pliki z kosza](https://support.microsoft.com/office/restore-deleted-items-from-the-site-collection-recycle-bin-5fa924ee-16d7-487b-9a0a-021b9062d14b).

- [Przywracanie plików](https://support.microsoft.com/office/restore-your-onedrive-fa231298-759d-41cf-bcd0-25ac53eb8a15)

   Kompletne rozwiązanie do samoobsługowego odzyskiwania dla SharePoint i OneDrive, które umożliwia administratorom i użytkownikom końcowym przywracanie plików z dowolnego punktu w czasie w ciągu ostatnich 30 dni.

   Aby zminimalizować obciążenie pracowników działu bezpieczeństwa i pomocy technicznej IT, wytrenuj użytkowników przy [przywracaniu plików](https://support.microsoft.com/office/restore-your-onedrive-fa231298-759d-41cf-bcd0-25ac53eb8a15).


W przypadku plików OneDrive i SharePoint firma Microsoft może cofnąć się do poprzedniego punktu w czasie przez maksymalnie 14 dni, jeśli zostanie osiągnięty masowy atak.

Poczta e-mail jest chroniona przez:

- [Odzyskiwanie pojedynczego elementu](/exchange/recipients-in-exchange-online/manage-user-mailboxes/enable-or-disable-single-item-recovery) i przechowywanie skrzynek pocztowych, w których można odzyskać elementy w skrzynce pocztowej po niezamierzonym lub złośliwym przedwczesnym usunięciu. Możesz domyślnie wycofać wiadomości e-mail usunięte w ciągu 14 dni i można je skonfigurować do 30 dni.

- [Zasady przechowywania](/exchange/security-and-compliance/messaging-records-management/retention-tags-and-policies) umożliwiają przechowywanie niezmiennych kopii wiadomości e-mail dla skonfigurowanego okresu przechowywania.

### <a name="encrypting-files-in-place"></a>Szyfrowanie plików w miejscu

Jak opisano wcześniej, pliki w SharePoint i OneDrive dla Firm są chronione przed złośliwym szyfrowaniem za pomocą:

- Wersji
- Kosza
- Biblioteka archiwum zachowywania

Aby uzyskać więcej informacji, zobacz [Rozwiązywanie problemów z uszkodzeniem danych w Microsoft 365](/compliance/assurance/assurance-dealing-with-data-corruption).

### <a name="copying-files-outside-your-tenant"></a>Kopiowanie plików poza dzierżawę 

Możesz uniemożliwić atakującemu oprogramowania wymuszającego okup kopiowanie plików poza dzierżawę za pomocą następujących funkcji:

- Zasady [ochrony przed utratą danych (DLP) w usłudze Microsoft Purview](/microsoft-365/compliance/dlp-learn-about-dlp)

    Wykrywanie, ostrzeganie i blokowanie ryzykownych, niezamierzonych lub niewłaściwych udostępniania danych zawierających:

    - Dane osobowe, takie jak dane osobowe w celu zachowania zgodności z regionalnymi przepisami dotyczącymi ochrony prywatności.

    - Poufne informacje o organizacji oparte na etykietach poufności.

- [Microsoft Defender for Cloud Apps](/cloud-app-security/what-is-cloud-app-security)

    Blokuj pobieranie poufnych informacji, takich jak pliki. 

    Zasady sesji można również używać do [kontroli aplikacji dostępu warunkowego Defender dla Chmury Apps](/cloud-app-security/tutorial-dlp#how-to-discover-and-protect-sensitive-information-in-your-organization), aby monitorować przepływ informacji między użytkownikiem a aplikacją w czasie rzeczywistym.

## <a name="whats-in-this-solution"></a>Co jest w tym rozwiązaniu

To rozwiązanie przeprowadzi Cię przez proces wdrażania funkcji ochrony Microsoft 365 i ograniczania ryzyka, konfiguracji i bieżących operacji, aby zminimalizować możliwość używania krytycznych danych w dzierżawie Microsoft 365 przez osobę atakującą wymuszającego okup i przechowywania organizacji w celu okupu.

![Kroki ochrony przed oprogramowaniem wymuszającym okup za pomocą Microsoft 365](../media/ransomware-protection-microsoft-365/ransomware-protection-microsoft-365-step-grid.png)

Kroki opisane w tym rozwiązaniu są następujące:

1. [Konfigurowanie planu bazowego zabezpieczeń](ransomware-protection-microsoft-365-security-baselines.md)
2. [Wdrażanie wykrywania ataków i reagowania](ransomware-protection-microsoft-365-attack-detection-response.md)
3. [Ochrona tożsamości](ransomware-protection-microsoft-365-identities.md)
4. [Ochrona urządzeń](ransomware-protection-microsoft-365-devices.md)
5. [Ochrona informacji](ransomware-protection-microsoft-365-information.md)

Poniżej przedstawiono pięć kroków rozwiązania wdrożonego dla dzierżawy Microsoft 365.

![Ochrona przed oprogramowaniem wymuszającym okup dla dzierżawy Microsoft 365](../media/ransomware-protection-microsoft-365/ransomware-protection-microsoft-365-architecture.png)

To rozwiązanie używa zasad [Zero Trust](/security/zero-trust/): 

- **Weryfikuj jawnie:** Zawsze uwierzytelniaj się i autoryzuj na podstawie wszystkich dostępnych punktów danych.
- **Użyj dostępu z najniższymi uprawnieniami:** Ogranicz dostęp użytkowników za pomocą funkcji just in time i just-enough-access (JIT/JEA), zasad adaptacyjnych opartych na ryzyku i ochrony danych.
- **Załóżmy, że naruszenie:** Minimalizuj promień wybuchu i dostęp do segmentu. Zweryfikuj kompleksowe szyfrowanie i użyj analizy, aby uzyskać widoczność, zwiększyć wykrywanie zagrożeń i ulepszyć ochronę.

W przeciwieństwie do konwencjonalnego dostępu do intranetu, który ufa wszystkim za zaporą organizacji, Zero Trust traktuje każde logowanie i dostęp tak, jakby pochodziło z niekontrolowanej sieci, czy to za zaporą organizacji, czy z Internetu. Zero Trust wymaga ochrony sieci, infrastruktury, tożsamości, punktów końcowych, aplikacji i danych.

## <a name="microsoft-365-capabilities-and-features"></a>Microsoft 365 możliwości i funkcje

Aby chronić dzierżawę Microsoft 365 przed atakiem wymuszającym okup, skorzystaj z tych Microsoft 365 możliwości i funkcji, aby wykonać te kroki w rozwiązaniu.

### <a name="1-security-baseline"></a>1. Punkt odniesienia zabezpieczeń

| Możliwość lub funkcja | Opis | Pomaga... | Licencjonowanie |
|:-------|:-----|:-------|:-------|
| Wskaźnik bezpieczeństwa Microsoft |  Mierzy stan zabezpieczeń dzierżawy Microsoft 365. | Ocena konfiguracji zabezpieczeń i sugerowanie ulepszeń. | Microsoft 365 E3 lub Microsoft 365 E5 |
| Reguły zmniejszania obszaru podatnego na ataki | Zmniejsza podatność organizacji na ataki cybernetyczne przy użyciu różnych ustawień konfiguracji. | Blokuj podejrzane działania i zawartość podatną na zagrożenia. | Microsoft 365 E3 lub Microsoft 365 E5 |
| ustawienia Exchange poczty e-mail |  Umożliwia korzystanie z usług, które zmniejszają podatność organizacji na ataki oparte na wiadomościach e-mail. | Zapobiegaj początkowemu dostępowi do dzierżawy poprzez wyłudzanie informacji i inne ataki oparte na wiadomościach e-mail.  | Microsoft 365 E3 lub Microsoft 365 E5 |
| Microsoft Windows, Microsoft Edge i Aplikacje Microsoft 365 dla ustawień Enterprise | Zapewnia standardowe w branży konfiguracje zabezpieczeń, które są szeroko znane i dobrze przetestowane. | Zapobiegaj atakom za pośrednictwem Windows, przeglądarki Edge i Aplikacje Microsoft 365 dla Enterprise. | Microsoft 365 E3 lub Microsoft 365 E5 |
|

### <a name="2-detection-and-response"></a>2. Wykrywanie i reagowanie

| Możliwość lub funkcja | Opis | Pomaga wykrywać i reagować na... | Licencjonowanie |
|:-------|:-----|:-------|:-------|
| Microsoft 365 Defender | Łączy sygnały i organizuje możliwości w jednym rozwiązaniu. <br><br> Umożliwia specjalistom ds. zabezpieczeń łączenie sygnałów zagrożeń i określanie pełnego zakresu i wpływu zagrożenia. <br><br> Automatyzuje akcje, aby zapobiec atakowi lub zatrzymać go oraz samodzielnie naprawiać skrzynki pocztowe, punkty końcowe i tożsamości użytkowników. | Zdarzenia, które są połączonymi alertami i danymi, które składają się na atak. | Microsoft 365 E5 lub Microsoft 365 E3 z dodatkiem Zabezpieczenia platformy Microsoft 365 E5 |
| Microsoft Defender for Identity |  Identyfikuje, wykrywa i bada zaawansowane zagrożenia, tożsamości, których zabezpieczenia zostały naruszone, oraz złośliwe działania wewnętrzne skierowane do organizacji za pośrednictwem interfejsu zabezpieczeń opartego na chmurze używa sygnałów usług lokalna usługa Active Directory Domain Services (AD DS). | Naruszenie zabezpieczeń poświadczeń dla kont usług AD DS. | Microsoft 365 E5 lub Microsoft 365 E3 z dodatkiem Zabezpieczenia platformy Microsoft 365 E5 |
| Ochrona usługi Office 365 w usłudze Microsoft Defender | Chroni organizację przed złośliwymi zagrożeniami, jakie stwarzają wiadomości e-mail, linki (adresy URL) i narzędzia do współpracy. <br><br> Chroni przed złośliwym oprogramowaniem, wyłudzaniem informacji, fałszowaniem i innymi typami ataków. | Ataki wyłudzające informacje. | Microsoft 365 E5 lub Microsoft 365 E3 z dodatkiem Zabezpieczenia platformy Microsoft 365 E5 |
| Ochrona punktu końcowego w usłudze Microsoft Defender | Umożliwia wykrywanie i reagowanie na zaawansowane zagrożenia w różnych punktach końcowych (urządzeniach). | Instalacja złośliwego oprogramowania i naruszenie zabezpieczeń urządzenia. | Microsoft 365 E5 lub Microsoft 365 E3 z dodatkiem Zabezpieczenia platformy Microsoft 365 E5 |
| Azure Active Directory (Azure AD) Identity Protection | Automatyzuje wykrywanie i korygowanie zagrożeń opartych na tożsamościach oraz badanie tych zagrożeń. | Naruszenie zabezpieczeń poświadczeń dla kont usługi Azure AD i eskalacja uprawnień. | Microsoft 365 E5 lub Microsoft 365 E3 z dodatkiem Zabezpieczenia platformy Microsoft 365 E5 |
| Defender for Cloud Apps | Broker zabezpieczeń dostępu do chmury do odnajdywania, badania i zapewniania ładu we wszystkich usługach firmy Microsoft i innych firm w chmurze. | Przenoszenie boczne i eksfiltracja danych. | Microsoft 365 E5 lub Microsoft 365 E3 z dodatkiem Zabezpieczenia platformy Microsoft 365 E5 |
|

### <a name="3-identities"></a>3. Tożsamości

| Możliwość lub funkcja | Opis | Zapobiega... | Licencjonowanie |
|:-------|:-----|:-------|:-------|
|Ochrona haseł w usłudze Azure AD | Blokuj hasła z wspólnej listy i wpisów niestandardowych. | Określanie hasła do konta użytkownika w chmurze lub lokalnie. |Microsoft 365 E3 lub Microsoft 365 E5|
|Uwierzytelnianie wieloskładnikowe wymuszane przy użyciu dostępu warunkowego | Wymagaj uwierzytelniania wieloskładnikowego na podstawie właściwości logowań użytkowników przy użyciu zasad dostępu warunkowego. | Naruszenie poświadczeń i dostęp. | Microsoft 365 E3 lub Microsoft 365 E5|
|Uwierzytelnianie wieloskładnikowe wymuszane przy użyciu dostępu warunkowego opartego na ryzyku | Wymagaj uwierzytelniania wieloskładnikowego na podstawie ryzyka logowania użytkowników przy użyciu usługi Azure AD Identity Protection. |Naruszenie poświadczeń i dostęp. | Microsoft 365 E5 lub Microsoft 365 E3 z dodatkiem Zabezpieczenia platformy Microsoft 365 E5|
|

### <a name="4-devices"></a>4. Urządzenia

Zarządzanie urządzeniami i aplikacjami:

| Możliwość lub funkcja | Opis | Zapobiega... | Licencjonowanie |
|:-------|:-----|:-------|:-------|
| Microsoft Intune | Zarządzanie urządzeniami i aplikacjami, które na nich działają.  | Naruszenie zabezpieczeń urządzenia lub aplikacji i dostęp. | Microsoft 365 E3 lub E5 |
|  |  |  |  |

W przypadku urządzeń Windows 11 lub 10:

| Możliwość lub funkcja | Opis | Pomaga... | Licencjonowanie |
|:-------|:-----|:-------|:-------|
| Zapora usługi Microsoft Defender | Udostępnia zaporę opartą na hoście.  | Zapobiegaj atakom z przychodzącego, niechcianego ruchu sieciowego. | Microsoft 365 E3 lub Microsoft 365 E5 |
| Program antywirusowy Microsoft Defender | Zapewnia ochronę przed złośliwym oprogramowaniem urządzeń (punktów końcowych) przy użyciu uczenia maszynowego, analizy danych big data, szczegółowych badań nad odpornością na zagrożenia i infrastruktury chmury firmy Microsoft. | Zapobiegaj instalowaniu i uruchamianiu złośliwego oprogramowania. | Microsoft 365 E3 lub Microsoft 365 E5 |
| Microsoft Defender SmartScreen | Chroni przed wyłudzaniem informacji lub złośliwym oprogramowaniem witryn internetowych i aplikacji oraz pobieraniem potencjalnie złośliwych plików. | Blokuj lub ostrzegaj podczas sprawdzania witryn, plików, aplikacji i plików. | Microsoft 365 E3 lub Microsoft 365 E5 |
| Ochrona punktu końcowego w usłudze Microsoft Defender | Pomaga zapobiegać zaawansowanym zagrożeniom na urządzeniach (punktach końcowych) i wykrywać je oraz badać je oraz reagować na nie. | Ochrona przed naruszeniem sieci. | Microsoft 365 E5 lub Microsoft 365 E3 z dodatkiem Zabezpieczenia platformy Microsoft 365 E5 |
|  |  |  |  |

### <a name="5-information"></a>5. Informacje

| Możliwość lub funkcja | Opis | Pomaga... | Licencjonowanie |
|:-------|:-----|:-------|:-------|
| Kontrolowany dostęp do folderu | Chroni dane, sprawdzając aplikacje pod kątem listy znanych, zaufanych aplikacji. | Zapobiegaj modyfikowaniu lub szyfrowaniu plików przez oprogramowanie wymuszające okup. | Microsoft 365 E3 lub Microsoft 365 E5 |
| Microsoft Purview Information Protection | Umożliwia stosowanie etykiet poufności do informacji, które można okupować | Zapobiegaj używaniu eksfiltrowanych informacji. | Microsoft 365 E3 lub Microsoft 365 E5 |
| Ochrona przed utratą danych (DLP) | Chroni poufne dane i zmniejsza ryzyko, uniemożliwiając użytkownikom ich niewłaściwe udostępnianie. | Zapobiegaj eksfiltracji danych. | Microsoft 365 E3 lub Microsoft 365 E5 |
| Defender for Cloud Apps | Broker zabezpieczeń dostępu do chmury na potrzeby odnajdywania, badania i zapewniania ładu. | Wykrywanie ruchu bocznego i zapobieganie eksfiltracji danych. | Microsoft 365 E5 lub Microsoft 365 E3 z dodatkiem Zabezpieczenia platformy Microsoft 365 E5 |
|

## <a name="impact-on-users-and-change-management"></a>Wpływ na użytkowników i zarządzanie zmianami

Wdrażanie dodatkowych funkcji zabezpieczeń oraz implementowanie wymagań i zasad zabezpieczeń dla dzierżawy Microsoft 365 może mieć wpływ na użytkowników. 

Na przykład można narzucić nowe zasady zabezpieczeń, które wymagają od użytkowników tworzenia nowych zespołów do określonych zastosowań z listą kont użytkowników jako członków, zamiast łatwiej tworzyć zespół dla wszystkich użytkowników w organizacji. Może to pomóc zapobiec eksplorowaniu przez osobę atakującą oprogramowania wymuszającego okup zespołów, które nie są dostępne dla konta użytkownika, których bezpieczeństwo zostało naruszone przez osobę atakującą, i określaniu zasobów tego zespołu w kolejnym ataku.

To podstawowe rozwiązanie określi, kiedy nowe konfiguracje lub zalecane zasady zabezpieczeń mogą mieć wpływ na użytkowników, dzięki czemu można wykonywać wymagane zarządzanie zmianami.

## <a name="next-steps"></a>Następne kroki

Wykonaj następujące kroki, aby wdrożyć kompleksową ochronę dzierżawy Microsoft 365:

1. [Konfigurowanie planu bazowego zabezpieczeń](ransomware-protection-microsoft-365-security-baselines.md)
2. [Wdrażanie wykrywania ataków i reagowania](ransomware-protection-microsoft-365-attack-detection-response.md)
3. [Ochrona tożsamości](ransomware-protection-microsoft-365-identities.md)
4. [Ochrona urządzeń](ransomware-protection-microsoft-365-devices.md)
5. [Ochrona informacji](ransomware-protection-microsoft-365-information.md)

[![Krok 1 dotyczący ochrony przed oprogramowaniem wymuszającym okup za pomocą Microsoft 365](../media/ransomware-protection-microsoft-365/ransomware-protection-microsoft-365-step1.png)](ransomware-protection-microsoft-365-security-baselines.md)

## <a name="additional-ransomware-resources"></a>Dodatkowe zasoby oprogramowania wymuszającego okup

Kluczowe informacje od firmy Microsoft:

- [Rosnące zagrożenie oprogramowaniem wymuszającym okup](https://blogs.microsoft.com/on-the-issues/2021/07/20/the-growing-threat-of-ransomware/), wpis w blogu Microsoft On the Issues 20 lipca 2021 r.
- [Oprogramowanie wymuszające okup obsługiwane przez człowieka](/security/compass/human-operated-ransomware)
- [Szybka ochrona przed oprogramowaniem wymuszającym okup i wymuszeniami](/security/compass/protect-against-ransomware)
- [2021 Microsoft Digital Defense Report](https://www.microsoft.com/security/business/microsoft-digital-defense-report) (zobacz strony 10–19)
- [Oprogramowanie wymuszające okup: wszechobecny i ciągły](https://security.microsoft.com/threatanalytics3/05658b6c-dc62-496d-ad3c-c6a795a33c27/overview) raport analizy zagrożeń w portalu Microsoft 365 Defender
- Podejście firmy Microsoft do wykrywania i reagowania na oprogramowanie wymuszające okup (DART) [oraz najlepsze rozwiązania](/security/compass/incident-response-playbook-dart-ransomware-approach) i [analiza przypadku](/security/compass/dart-ransomware-case-study)

Microsoft 365:

- [Maksymalizowanie odporności oprogramowania wymuszającego okup za pomocą platformy Azure i Microsoft 365](https://azure.microsoft.com/resources/maximize-ransomware-resiliency-with-azure-and-microsoft-365/)
- [Odzyskiwanie po ataku wymuszającym okup](/microsoft-365/security/office-365-security/recover-from-ransomware)
- [Ochrona przed złośliwym oprogramowaniem i oprogramowaniem wymuszającym okup](/compliance/assurance/assurance-malware-and-ransomware-protection)
- [Ochrona komputera Windows 10 przed oprogramowaniem wymuszającym okup](https://support.microsoft.com//windows/protect-your-pc-from-ransomware-08ed68a7-939f-726c-7e84-a72ba92c01c3)
- [Obsługa oprogramowania wymuszającego okup w usłudze SharePoint Online](/sharepoint/troubleshoot/security/handling-ransomware-in-sharepoint-online)
- [Raporty analizy zagrożeń dotyczące oprogramowania wymuszającego okup](https://security.microsoft.com/threatanalytics3?page_size=30&filters=tags%3DRansomware&ordering=-lastUpdatedOn&fields=displayName,alertsCount,impactedEntities,reportType,createdOn,lastUpdatedOn,tags,flag) w portalu Microsoft 365 Defender

Microsoft 365 Defender:

- [Znajdowanie oprogramowania wymuszającego okup za pomocą zaawansowanego wyszukiwania zagrożeń](/microsoft-365/security/defender/advanced-hunting-find-ransomware)

Microsoft Azure:

- [Azure Defenses for Ransomware Attack](https://azure.microsoft.com/resources/azure-defenses-for-ransomware-attack/)
- [Maksymalizowanie odporności oprogramowania wymuszającego okup za pomocą platformy Azure i Microsoft 365](https://azure.microsoft.com/resources/maximize-ransomware-resiliency-with-azure-and-microsoft-365/)
- [Plan tworzenia kopii zapasowych i przywracania w celu ochrony przed oprogramowaniem wymuszającym okup](/security/compass/backup-plan-to-protect-against-ransomware)
- [Ochrona przed oprogramowaniem wymuszającym okup za pomocą usługi Microsoft Azure Backup](https://www.youtube.com/watch?v=VhLOr2_1MCg) (26-minutowe wideo)
- [Odzyskiwanie po systemowym naruszeniach tożsamości](/azure/security/fundamentals/recover-from-identity-compromise)
- [Zaawansowane wieloetapowe wykrywanie ataków w usłudze Microsoft Sentinel](/azure/sentinel/fusion#ransomware)
- [Wykrywanie fuzji dla oprogramowania wymuszającego okup w usłudze Microsoft Sentinel](https://techcommunity.microsoft.com/t5/azure-sentinel/what-s-new-fusion-detection-for-ransomware/ba-p/2621373)

Microsoft Defender for Cloud Apps:

-  [Tworzenie zasad wykrywania anomalii w usłudze Defender dla Chmury Apps](/cloud-app-security/anomaly-detection-policy)

Wpisy w blogu zespołu ds. zabezpieczeń firmy Microsoft:

- [3 kroki zapobiegania i odzyskiwania po oprogramowaniu wymuszającym okup (wrzesień 2021 r.)](https://www.microsoft.com/security/blog/2021/09/07/3-steps-to-prevent-and-recover-from-ransomware/)
- [Przewodnik po zwalczaniu oprogramowania wymuszającego okup obsługiwane przez człowieka: część 1 (wrzesień 2021 r.)](https://www.microsoft.com/security/blog/2021/09/20/a-guide-to-combatting-human-operated-ransomware-part-1/)

  Kluczowe kroki dotyczące sposobu, w jaki zespół ds. wykrywania i reagowania firmy Microsoft (DART) prowadzi badania zdarzeń wymuszania okupu.

- [Przewodnik po zwalczaniu oprogramowania wymuszającego okup przez człowieka: część 2 (wrzesień 2021 r.)](https://www.microsoft.com/security/blog/2021/09/27/a-guide-to-combatting-human-operated-ransomware-part-2/)

  Rekomendacje i najlepsze rozwiązania.

- [Odporność dzięki zrozumieniu zagrożeń związanych z cyberbezpieczeństwem: część 4 — poruszanie się po bieżących zagrożeniach (maj 2021 r.)](https://www.microsoft.com/security/blog/2021/05/26/becoming-resilient-by-understanding-cybersecurity-risks-part-4-navigating-current-threats/)

  Zobacz sekcję **Oprogramowanie wymuszające okup** .

- [Ataki ransomware obsługiwane przez człowieka: możliwe do uniknięcia katastrofy (marzec 2020 r.)](https://www.microsoft.com/security/blog/2020/03/05/human-operated-ransomware-attacks-a-preventable-disaster/)

  Obejmuje analizy łańcucha ataków dotyczące rzeczywistych ataków.

- [Odpowiedź wymuszania okupu — aby zapłacić, czy nie płacić? (grudzień 2019 r.)](https://www.microsoft.com/security/blog/2019/12/16/ransomware-response-to-pay-or-not-to-pay/)
- [Norsk Hydro reaguje na atak ransomware z przejrzystością (grudzień 2019)](https://www.microsoft.com/security/blog/2019/12/17/norsk-hydro-ransomware-attack-transparency/)
