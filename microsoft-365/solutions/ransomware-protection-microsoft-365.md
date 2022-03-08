---
title: Wdrażanie ochrony przed oprogramowaniem wymuszającym okup dla Microsoft 365 dzierżawy
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
keywords: oprogramowanie wymuszające okup, oprogramowanie wymuszające okup obsługiwane przez człowieka, oprogramowanie wymuszające okup przez człowieka, humor, ataki wymuszające okup, ataki oprogramowania wymuszającego okup, szyfrowanie, kryptografia, zerowe zaufanie
description: Kroki ochrony zasobów internetowych przed Microsoft 365 oprogramowania wymuszającego okup.
ms.openlocfilehash: c356a0e3fac83c77a7e1eb1eda6e169405f43863
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63324413"
---
# <a name="deploy-ransomware-protection-for-your-microsoft-365-tenant"></a>Wdrażanie ochrony przed oprogramowaniem wymuszającym okup dla Microsoft 365 dzierżawy

Oprogramowanie wymuszające okup to rodzaj ataku, który zniszczy lub szyfruje pliki i foldery, uniemożliwiając dostęp do kluczowych danych. Oprogramowanie wymuszające okup zwykle rozpowszechnia się jak wirus, który infekuje urządzenia i wymaga tylko działań naprawczych w przypadku złośliwego oprogramowania. Oprogramowanie wymuszające okup obsługiwane przez człowieka jest wynikiem aktywnego ataku cyberprzestępców, który infiltruje lokalną lub chmurową infrastrukturę it organizacji, podniesie swoje uprawnienia i wdraża oprogramowanie wymuszające okup w krytycznych danych.

Po zakończeniu ataków atakujący żąda pieniędzy w zamian za usunięte pliki, klucze odszyfrowywania zaszyfrowanych plików lub obietnicę nieudostępnia poufnych danych do ciemnej sieci lub publicznego Internetu. Oprogramowania wymuszającego okup obsługiwanego przez człowieka można również używać do zamykania krytycznych maszyn lub procesów, takich jak urządzenia potrzebne do produkcji w przemyśle, w celu wstrzymania normalnych operacji biznesowych do czasu zapłaty na okup i naprawy szkód lub gdy organizacja rekultywuje szkody.

Ataki oprogramowania wymuszającego okup przez ludzi mogą być katastrofą dla firm o wszystkich rozmiarach i są trudne do oczyszczenia, co wymaga pełnego wykupu adversary w celu ochrony przed przyszłymi atakami. Inaczej niż w przypadku oprogramowania wymuszającego okup, oprogramowanie wymuszające okup wykonywane przez człowieka może nadal zasypować firmy po początkowym zmowie okup.

>[!Note]
>Atak oprogramowania wymuszającego okup na dzierżawę usługi Microsoft 365 zakłada, że atakujący ma prawidłowe poświadczenia konta użytkownika dla dzierżawy i ma dostęp do wszystkich plików i zasobów dozwolonych dla konta użytkownika. Atakujący bez prawidłowych poświadczeń konta użytkownika musiałby odszyfrować dane, które zostały zaszyfrowane przez Microsoft 365 i rozszerzone szyfrowanie. Aby uzyskać więcej informacji, zobacz [Omówienie szyfrowania i zarządzania kluczami](/compliance/assurance/assurance-encryption). 
>

Aby uzyskać więcej informacji na temat ochrony przed oprogramowaniem wymuszającym okup w produktach firmy Microsoft, zobacz te [dodatkowe zasoby oprogramowania wymuszającego okup](#additional-ransomware-resources).

## <a name="security-in-the-cloud-is-a-partnership"></a>Bezpieczeństwo w chmurze to partnerstwo

Bezpieczeństwo usług firmy Microsoft w chmurze jest oparte na współpracy między Tobem a firmą Microsoft:

- Podstawą usług firmy Microsoft w chmurze jest zaufanie i bezpieczeństwo. Firma Microsoft udostępnia funkcje i mechanizmy kontroli zabezpieczeń, które pomagają chronić dane i aplikacje.
- Jesteś właścicielem danych i tożsamości oraz ponosisz odpowiedzialność za ich ochronę, bezpieczeństwo zasobów lokalnych i bezpieczeństwo składników chmury, które kontrolujesz.

Łącząc te funkcje i obowiązki, możemy zapewnić najlepszą ochronę przed atakami oprogramowania wymuszającego okup.

## <a name="ransomware-mitigation-and-recovery-capabilities-provided-with-microsoft-365"></a>Funkcje zaradcze przed oprogramowaniem wymuszającym okup i odzyskiwania dostępne Microsoft 365

Atakujący oprogramowania wymuszającego okup, który zfiltrował Microsoft 365 dzierżawę usługi, może wstrzymywać twoją organizację w celu okupu:

- Usuwanie plików lub wiadomości e-mail
- Szyfrowanie plików w miejscu
- Kopiowanie plików poza dzierżawę (ex ex szybkowanie danych)

Jednak usługi Microsoft 365 online mają wiele wbudowanych funkcji i kontrolek w celu ochrony danych klientów przed atakami oprogramowania wymuszającego okup. Poniższe sekcje zawierają podsumowanie. Aby uzyskać więcej szczegółowych informacji na temat ochrony danych klientów, złośliwego oprogramowania i ochrony przed [oprogramowaniem wymuszającym okup](/compliance/assurance/assurance-malware-and-ransomware-protection) w sieci Microsoft 365.

>[!Note]
>Atak oprogramowania wymuszającego okup na dzierżawę usługi Microsoft 365 zakłada, że atakujący ma prawidłowe poświadczenia konta użytkownika dla dzierżawy i ma dostęp do wszystkich plików i zasobów dozwolonych dla konta użytkownika. Atakujący bez prawidłowych poświadczeń konta użytkownika musiałby odszyfrować dane, które zostały zaszyfrowane przez Microsoft 365 i rozszerzone szyfrowanie. Aby uzyskać więcej informacji, zobacz [Omówienie szyfrowania i zarządzania kluczami](/compliance/assurance/assurance-encryption). 
>

### <a name="deleting-files-or-email"></a>Usuwanie plików lub wiadomości e-mail

Pliki w SharePoint i OneDrive dla Firm są chronione przez:

- Versioning (Wersja) 

   Microsoft 365 przechowuje domyślnie co najmniej 500 wersji pliku i można skonfigurować ich większą ilość. 

   Aby zminimalizować obciążenie związane z zabezpieczeniami i pracownikami działu pomocy technicznej, przeszkoli użytkowników w zakresie [przywracania poprzednich wersji plików](https://support.microsoft.com/office/restore-a-previous-version-of-an-item-or-file-in-sharepoint-f66dbda0-81f4-4d1e-b08c-793265c58934).

- Kosz

   Jeśli oprogramowanie wymuszające okup utworzy nową zaszyfrowaną kopię pliku i usunie stary plik, klienci mają 93 dni na przywrócenie pliku z Kosza. Po 93 dniach jest 14-dniowe okno, w którym firma Microsoft nadal może odzyskać dane. 
  
   Aby zminimalizować obciążenie związane z zabezpieczeniami i pracownikami działu pomocy technicznej, przeszkoli użytkowników w zakresie sposobu przywracania plików [z Kosza](https://support.microsoft.com/office/restore-deleted-items-from-the-site-collection-recycle-bin-5fa924ee-16d7-487b-9a0a-021b9062d14b).

- [Przywracanie plików](https://support.microsoft.com/office/restore-your-onedrive-fa231298-759d-41cf-bcd0-25ac53eb8a15)

   Kompleksowe rozwiązanie do samodzielnego odzyskiwania plików dla systemów SharePoint i OneDrive, które umożliwia administratorom i użytkownikom końcowy przywracanie plików od dowolnego miejsca w czasie w ciągu ostatnich 30 dni.

   Aby zminimalizować obciążenie związane z zabezpieczeniami i pracownikami działu pomocy technicznej IT, przeszkoli użytkowników w zakresie [przywracania plików](https://support.microsoft.com/office/restore-your-onedrive-fa231298-759d-41cf-bcd0-25ac53eb8a15).


W OneDrive plikach SharePoint i innych firma Microsoft może wycofać się do poprzedniego punktu w czasie do 14 dni w przypadku ataku masowego ataku.

Poczta e-mail jest chroniona przez:

- [Odzyskiwanie pojedynczych elementów](/exchange/recipients-in-exchange-online/manage-user-mailboxes/enable-or-disable-single-item-recovery) i przechowywanie w skrzynkach pocztowych, w których można odzyskać elementy ze skrzynki pocztowej po przypadkowej lub złośliwej usunięciu. Domyślnie możesz wycofać usunięte wiadomości e-mail w ciągu 14 dni i skonfigurować je w ciągu 30 dni.

- [Zasady przechowywania](/exchange/security-and-compliance/messaging-records-management/retention-tags-and-policies) umożliwiają przechowywanie nieumiejętnych kopii wiadomości e-mail przez skonfigurowany okres przechowywania.

### <a name="encrypting-files-in-place"></a>Szyfrowanie plików w miejscu

Jak opisano wcześniej, pliki SharePoint i OneDrive dla Firm są chronione przed złośliwym szyfrowaniem za pomocą:

- Versioning (Wersja)
- Kosz
- Biblioteka Z zachowaniem

Aby uzyskać dodatkowe informacje, zobacz [Radzenie sobie z uszkodzeniami danych w Microsoft 365](/compliance/assurance/assurance-dealing-with-data-corruption).

### <a name="copying-files-outside-your-tenant"></a>Kopiowanie plików poza dzierżawę 

Możesz zapobiec kopiowaniu przez atakującego oprogramowania wymuszającego okup plików spoza Twojej dzierżawy za pomocą:

- [Zasady ochrony przed utratą danych (DLP)](/microsoft-365/compliance/dlp-learn-about-dlp)

    Wykrywanie, ostrzeganie i blokowanie ryzykownego, przypadkowego lub nieodpowiedniego udostępniania danych zawierających:

    - Informacje osobiste, takie jak dane osobowe, w celu zachowania zgodności z regionalnymi przepisami dotyczącymi prywatności.

    - Poufne informacje o organizacji oparte na etykietach poufności.

- [Usługa Microsoft Defender dla aplikacji w chmurze](/cloud-app-security/what-is-cloud-app-security)

    Blokowanie pobierania poufnych informacji, takich jak pliki. 

    Przy użyciu zasad sesji dla aplikacji warunkowych programu [Defender dla](/cloud-app-security/tutorial-dlp#how-to-discover-and-protect-sensitive-information-in-your-organization) aplikacji w chmurze można również monitorować przepływ informacji między użytkownikiem a aplikacją w czasie rzeczywistym.

## <a name="whats-in-this-solution"></a>Co jest w tym rozwiązaniu

To rozwiązanie prowadzi Cię przez proces wdrażania funkcji ochrony i środków zaradczych, konfiguracji oraz trwających operacji, które minimalizują możliwość używania przez atakującego oprogramowania wymuszającego okup najważniejszych danych w dzierżawie usługi Microsoft 365 Microsoft 365 i przechowywania oprogramowania w organizacji w celu okupu.

![Kroki ochrony przed oprogramowaniem wymuszającym okup za pomocą Microsoft 365](../media/ransomware-protection-microsoft-365/ransomware-protection-microsoft-365-step-grid.png)

W tym rozwiązaniu należy wykonać następujące czynności:

1. [Konfigurowanie planu bazowego zabezpieczeń](ransomware-protection-microsoft-365-security-baselines.md)
2. [Wdrażanie wykrywania ataków i reagowania](ransomware-protection-microsoft-365-attack-detection-response.md)
3. [Ochrona tożsamości](ransomware-protection-microsoft-365-identities.md)
4. [Ochrona urządzeń](ransomware-protection-microsoft-365-devices.md)
5. [Ochrona informacji](ransomware-protection-microsoft-365-information.md)

Poniżej znajdują się pięć kroków wdrożenia rozwiązania dla Twojej Microsoft 365 dzierżawy.

![Ochrona przed oprogramowaniem wymuszającym okup dla Microsoft 365 dzierżawy](../media/ransomware-protection-microsoft-365/ransomware-protection-microsoft-365-architecture.png)

W tym rozwiązaniu są używane zasady [zerowego zaufania](/security/zero-trust/): 

- **Jawne sprawdzanie:** Zawsze uwierzytelnianie i autoryzacja na podstawie wszystkich dostępnych punktów danych.
- **Użyj dostępu z najmniejszymi uprawnieniami:** Ogranicz dostęp użytkowników dzięki technologii Just-In-Time i Just-Enough-Access (JIT/JEA), adaptacyjnym zasadom opartym na ryzyko i ochronie danych.
- **Załóżmy naruszenie:** Minimalizowanie promieni rozdęć i dostępu segmentów. Weryfikuj zaawansowane szyfrowanie i korzystaj z analizy, aby uzyskać widoczność, usprawnić wykrywanie zagrożeń i usprawnić obronę.

W przeciwieństwie do konwencjonalnego dostępu do intranetu, który ufa wszystkomu, co znajduje się w zaporze organizacji, zaufanie zerowe traktuje każde logowanie i dostęp tak, jakby pochodziło z niepod kontrolowanych sieci, niezależnie od tego, czy znajduje się za zaporą organizacji, czy za Internetem. Zerowe zaufanie wymaga ochrony sieci, infrastruktury, tożsamości, punktów końcowych, aplikacji i danych.

## <a name="microsoft-365-capabilities-and-features"></a>Microsoft 365 i funkcje

Aby chronić dzierżawę Microsoft 365 przed atakiem oprogramowania wymuszającego okup, użyj tych Microsoft 365 funkcji i funkcji oprogramowania wymuszającego okup, aby wykonać te kroki w rozwiązaniu.

### <a name="1-security-baseline"></a>1. Plan bazowy zabezpieczeń

| Funkcja lub funkcja | Opis | Pomaga... | Licencjonowanie |
|:-------|:-----|:-------|:-------|
| Microsoft Secure Score |  Mierzy poziom zabezpieczeń dzierżawy Microsoft 365 dzierżawy. | Oceń konfigurację zabezpieczeń i sugeruje ulepszenia. | Microsoft 365 E3 lub Microsoft 365 E5 |
| Reguły zmniejszania obszaru podatnego na ataki | Ogranicza luki w zabezpieczeniach organizacji przed cyberatakami przy użyciu różnych ustawień konfiguracji. | Blokowanie podejrzanych aktywności i narażenie zawartości. | Microsoft 365 E3 lub Microsoft 365 E5 |
| Exchange ustawień poczty e-mail |  Włącza usługi, które ograniczają ryzyko twojej organizacji w przypadku ataku opartego na wiadomościach e-mail. | Zapobieganie początkowemu dostępowi do dzierżawy przez próby wyłudzenia informacji i innych ataków opartych na wiadomościach e-mail.  | Microsoft 365 E3 lub Microsoft 365 E5 |
| Aplikacje Microsoft Windows, Microsoft Edge i Aplikacje Microsoft 365 do Enterprise ustawień | Zawiera standardowe konfiguracje zabezpieczeń, które są ogólnie znane i dobrze przetestowane. | Zapobieganie atakom z Windows, Edge i innych Aplikacje Microsoft 365 dla Enterprise. | Microsoft 365 E3 lub Microsoft 365 E5 |
|

### <a name="2-detection-and-response"></a>2. Wykrywanie i odpowiedź

| Funkcja lub funkcja | Opis | Pomaga wykrywać i odpowiadać na... | Licencjonowanie |
|:-------|:-----|:-------|:-------|
| Microsoft 365 Defender | Łączy możliwości sygnału i bajtów w jedno rozwiązanie. <br><br> Umożliwia specjalistom zabezpieczeń łączenie sygnałów zagrożeń oraz określanie pełnego zakresu i wpływu zagrożenia. <br><br> Automatyzuje akcje w celu zapobiegania atakom i samodzielnej obsługi skrzynek pocztowych, punktów końcowych i tożsamości użytkowników, których dotyczy problem. | Zdarzenia, czyli połączone alerty i dane, które są wykorzystywane do ataków. | Microsoft 365 E5 lub Microsoft 365 E3 pomocą Zabezpieczenia platformy Microsoft 365 E5 dodatku |
| Microsoft Defender for Identity |  Identyfikuje, wykrywa i bada zaawansowane zagrożenia, naruszone tożsamości i złośliwe działania niejawnego programu testów skierowane do organizacji za pośrednictwem opartego na chmurze interfejsu zabezpieczeń używa sygnałów Usługi domenowe w usłudze Active Directory (AD DS). | Złamanie poświadczeń dla AD DS konta. | Microsoft 365 E5 lub Microsoft 365 E3 pomocą Zabezpieczenia platformy Microsoft 365 E5 dodatku |
| Usługa Microsoft Defender dla Office 365 | Chroni organizację przed złośliwymi zagrożeniami ze strony wiadomości e-mail, linków (adresów URL) i narzędzi do współpracy. <br><br> Chroni przed złośliwym oprogramowaniem, wyłudzaniem informacji, fałszerniem i innymi typami ataków. | Ataki służące do wyłudzania informacji. | Microsoft 365 E5 lub Microsoft 365 E3 pomocą Zabezpieczenia platformy Microsoft 365 E5 dodatku |
| Ochrona punktu końcowego w usłudze Microsoft Defender | Umożliwia wykrywanie i reagowanie na zaawansowane zagrożenia dla punktów końcowych (urządzeń). | Bezpieczeństwo instalacji i urządzeń z złośliwym oprogramowaniem. | Microsoft 365 E5 lub Microsoft 365 E3 pomocą Zabezpieczenia platformy Microsoft 365 E5 dodatku |
| Azure Active Directory tożsamości w usłudze Azure AD | Automatyzuje wykrywanie i rozwiązywanie problemów związanych z zagrożeniami opartymi na tożsamościach oraz ich badanie. | Złamanie poświadczeń dla kont usługi Azure AD i eskalacji uprawnień. | Microsoft 365 E5 lub Microsoft 365 E3 pomocą Zabezpieczenia platformy Microsoft 365 E5 dodatku |
| Defender for Cloud Apps | Broker zabezpieczeń dostępu w chmurze do odnajdowania, badania i zarządzania we wszystkich usługach firmy Microsoft i innych firm w chmurze. | Ruch lateralny i ex ex  rozsyłanie danych. | Microsoft 365 E5 lub Microsoft 365 E3 pomocą Zabezpieczenia platformy Microsoft 365 E5 dodatku |
|

### <a name="3-identities"></a>3. Tożsamości

| Funkcja lub funkcja | Opis | Pomaga zapobiec... | Licencjonowanie |
|:-------|:-----|:-------|:-------|
|Ochrona hasłem w usłudze Azure AD | Blokowanie haseł na liście wspólnych i wpisach niestandardowych. | Określanie hasła do chmury lub lokalnego konta użytkownika. |Microsoft 365 E3 lub Microsoft 365 E5|
|Uwierzytelniania wieloskładnikowego z dostępem warunkowym | Wymaganie uwierzytelniania WIELOSKŁADNIKOWEGO na podstawie właściwości logowania użytkownika przy użyciu zasad dostępu warunkowego. | Bezpieczeństwo poświadczeń i dostęp. | Microsoft 365 E3 lub Microsoft 365 E5|
|Uwierzytelniania wieloskładnikowego z dostępem warunkowym opartym na czynniku ryzyka | Wymagaj uwierzytelniania wieloskładnikowego na podstawie ryzyka związanego z logowaniem użytkowników za pomocą usługi Azure AD Identity Protection. |Bezpieczeństwo poświadczeń i dostęp. | Microsoft 365 E5 lub Microsoft 365 E3 pomocą Zabezpieczenia platformy Microsoft 365 E5 dodatku|
|

### <a name="4-devices"></a>4. Urządzenia

Do zarządzania urządzeniami i aplikacją:

| Funkcja lub funkcja | Opis | Pomaga zapobiec... | Licencjonowanie |
|:-------|:-----|:-------|:-------|
| Microsoft Intune | Zarządzaj urządzeniami i aplikacjami, które na nich działają.  | Bezpieczeństwo i dostęp do urządzenia lub aplikacji. | Microsoft 365 E3 lub E5 |
|  |  |  |  |

Dla Windows 11 lub 10 urządzeń:

| Funkcja lub funkcja | Opis | Pomaga... | Licencjonowanie |
|:-------|:-----|:-------|:-------|
| Zapora Microsoft Defender | Zapewnia zaporę opartą na hoście.  | Zapobieganie atakom przed przychodzącym, niechcianym ruchem sieciowym. | Microsoft 365 E3 lub Microsoft 365 E5 |
| Program antywirusowy Microsoft Defender | Zapewnia ochronę przed złośliwym oprogramowaniem urządzeń (punktów końcowych) przy użyciu uczenia maszynowego, analizy dużych danych, szczegółowego badania odporność na zagrożenia i infrastruktury chmury firmy Microsoft. | Zapobiegaj instalacji i uruchomieniu złośliwego oprogramowania. | Microsoft 365 E3 lub Microsoft 365 E5 |
| Microsoft Defender SmartScreen | Chroni przed wyłudzaniem informacji, witrynami internetowymi i aplikacjami złośliwego oprogramowania oraz przed pobieraniem potencjalnie złośliwych plików. | Blokuj lub ostrzegaj podczas sprawdzania witryn, pobierania, aplikacji i plików. | Microsoft 365 E3 lub Microsoft 365 E5 |
| Ochrona punktu końcowego w usłudze Microsoft Defender | Pomaga zapobiegać zaawansowanym zagrożeniam na różnych urządzeniach (punktach końcowych), wykrywać i badać zaawansowane zagrożenia oraz odpowiadać na nie. | Ochrona przed naruszeniami sieci. | Microsoft 365 E5 lub Microsoft 365 E3 pomocą Zabezpieczenia platformy Microsoft 365 E5 dodatku |
|  |  |  |  |

### <a name="5-information"></a>5. Informacje

| Funkcja lub funkcja | Opis | Pomaga... | Licencjonowanie |
|:-------|:-----|:-------|:-------|
| Kontrolowany dostęp do folderu | Chroni dane, sprawdzając aplikacje przed listą znanych, zaufanych aplikacji. | Zapobiegaj modyfikowaniu i szyfrowanym plikom za pomocą oprogramowania wymuszającego okup. | Microsoft 365 E3 lub Microsoft 365 E5 |
| Microsoft Information Protection | Umożliwia zastosowanie etykiet wrażliwości do informacji, które można uruchomić. | Zapobieganie używaniu zfiltrowanych informacji. | Microsoft 365 E3 lub Microsoft 365 E5 |
| Ochrona przed utratą danych (DLP) | Chroni poufne dane i zmniejsza ryzyko, uniemożliwiając użytkownikom nieodpowiednie udostępnianie tych danych. | Zapobieganie wykrojom danych. | Microsoft 365 E3 lub Microsoft 365 E5 |
| Defender for Cloud Apps | Broker zabezpieczeń dostępu w chmurze do odnajdowania, badania i zarządzania. | Wykrywaj ruchy boczne i zapobiegaj wykrzykceniu danych. | Microsoft 365 E5 lub Microsoft 365 E3 pomocą Zabezpieczenia platformy Microsoft 365 E5 dodatku |
|

## <a name="impact-on-users-and-change-management"></a>Wpływ na użytkowników i zarządzanie zmianami

Wdrażanie dodatkowych funkcji zabezpieczeń oraz wdrażanie wymagań i zasad zabezpieczeń na potrzeby dzierżawy usługi Microsoft 365 może mieć wpływ na użytkowników. 

Na przykład można nałożyć nowe zasady zabezpieczeń, które wymagają od użytkowników tworzenia nowych zespołów do określonych zastosowań z listą kont użytkowników jako członków, zamiast łatwiej utworzyć zespół dla wszystkich użytkowników w organizacji. Może to zapobiec poznaniu przez atakującego oprogramowania wymuszającego okup zespołów, które nie są dostępne dla naruszonego konta użytkownika tego atakującego, i kierowania ich do zasobów tego zespołu podczas kolejnych ataków.

To rozwiązanie foundation zidentyfikuje, kiedy nowe konfiguracje lub zalecane zasady zabezpieczeń mogą mieć wpływ na użytkowników, dzięki czemu będzie można wykonywać wymagane zarządzanie zmianami.

## <a name="next-steps"></a>Następne kroki

Skorzystaj z tej procedury, aby wdrożyć pełną ochronę dla Microsoft 365 dzierżawy:

1. [Konfigurowanie planu bazowego zabezpieczeń](ransomware-protection-microsoft-365-security-baselines.md)
2. [Wdrażanie wykrywania ataków i reagowania](ransomware-protection-microsoft-365-attack-detection-response.md)
3. [Ochrona tożsamości](ransomware-protection-microsoft-365-identities.md)
4. [Ochrona urządzeń](ransomware-protection-microsoft-365-devices.md)
5. [Ochrona informacji](ransomware-protection-microsoft-365-information.md)

[![Krok 1 dla ochrony przed oprogramowaniem wymuszającym okup przy użyciu oprogramowania Microsoft 365](../media/ransomware-protection-microsoft-365/ransomware-protection-microsoft-365-step1.png)](ransomware-protection-microsoft-365-security-baselines.md)

## <a name="additional-ransomware-resources"></a>Dodatkowe zasoby oprogramowania wymuszającego okup

Najważniejsze informacje od firmy Microsoft:

- [Coraz większe zagrożenie związane z oprogramowaniem wymuszającym okup](https://blogs.microsoft.com/on-the-issues/2021/07/20/the-growing-threat-of-ransomware/) (Microsoft) w wpisie w blogu Problemy z 20 lipca 2021 r.
- [Oprogramowanie wymuszające okup obsługiwane przez człowieka](/security/compass/human-operated-ransomware)
- [Błyskawiczna ochrona przed oprogramowaniem wymuszającym okup i wymuszającym okup](/security/compass/protect-against-ransomware)
- [2021: Microsoft Digital Defense Report](https://www.microsoft.com/security/business/microsoft-digital-defense-report) (zobacz strony 10-19)
- [Oprogramowanie wymuszające okup: natłok](https://security.microsoft.com/threatanalytics3/05658b6c-dc62-496d-ad3c-c6a795a33c27/overview) i bieżący raport analizy zagrożeń w portalu Microsoft 365 Defender okup
- Rozwiązanie firmy Microsoft dotyczące oprogramowania wymuszającego okup (DETECTION and Response Team) firmy Microsoft oraz najlepsze [rozwiązania i](/security/compass/incident-response-playbook-dart-ransomware-approach) [analiza przypadku](/security/compass/dart-ransomware-case-study)

Microsoft 365:

- [Zmaksymalizuj odporność oprogramowania wymuszającego okup na platformie Azure Microsoft 365](https://azure.microsoft.com/resources/maximize-ransomware-resiliency-with-azure-and-microsoft-365/)
- [Odzyskiwanie po atakach oprogramowania wymuszającego okup](/microsoft-365/security/office-365-security/recover-from-ransomware)
- [Ochrona przed złośliwym oprogramowaniem i oprogramowaniem wymuszającym okup](/compliance/assurance/assurance-malware-and-ransomware-protection)
- [Ochrona komputera Windows 10 przed oprogramowaniem wymuszającym okup](https://support.microsoft.com//windows/protect-your-pc-from-ransomware-08ed68a7-939f-726c-7e84-a72ba92c01c3)
- [Obsługa oprogramowania wymuszającego okup w SharePoint Online](/sharepoint/troubleshoot/security/handling-ransomware-in-sharepoint-online)
- [Raporty analizy zagrożeń dotyczące oprogramowania wymuszającego](https://security.microsoft.com/threatanalytics3?page_size=30&filters=tags%3DRansomware&ordering=-lastUpdatedOn&fields=displayName,alertsCount,impactedEntities,reportType,createdOn,lastUpdatedOn,tags,flag) okup w Microsoft 365 Defender sieci

Microsoft 365 Defender:

- [Znajdź oprogramowanie wymuszające okup dzięki zaawansowanej chłonie](/microsoft-365/security/defender/advanced-hunting-find-ransomware)

Microsoft Azure:

- [Obrony platformy Azure w przypadku ataków na oprogramowanie wymuszające okup](https://azure.microsoft.com/resources/azure-defenses-for-ransomware-attack/)
- [Zmaksymalizuj odporność oprogramowania wymuszającego okup na platformie Azure Microsoft 365](https://azure.microsoft.com/resources/maximize-ransomware-resiliency-with-azure-and-microsoft-365/)
- [Plan tworzenia kopii zapasowej i przywracania w celu ochrony przed oprogramowaniem wymuszającym okup](/security/compass/backup-plan-to-protect-against-ransomware)
- [Pomóż chronić przed oprogramowaniem wymuszającym okup Microsoft Azure zapasowej](https://www.youtube.com/watch?v=VhLOr2_1MCg) (26-minutowy klip wideo)
- [Odzyskiwanie po najechania na tożsamość tożsamości przez tożsamość](/azure/security/fundamentals/recover-from-identity-compromise)
- [Zaawansowane wykrywanie wieloetapowego ataku w programie Microsoft Sentinel](/azure/sentinel/fusion#ransomware)
- [Wykrywanie oprogramowania wymuszającego okup w programie Microsoft Sentinel](https://techcommunity.microsoft.com/t5/azure-sentinel/what-s-new-fusion-detection-for-ransomware/ba-p/2621373)

Program Microsoft Defender dla aplikacji w chmurze:

-  [Tworzenie zasad wykrywania anomaly w usłudze Defender dla aplikacji w chmurze](/cloud-app-security/anomaly-detection-policy)

Wpisy w blogu zespołu zabezpieczeń firmy Microsoft:

- [3 kroki, aby zapobiec oprogramowaniem wymuszającym okup i odzyskać je (wrzesień 2021 r.)](https://www.microsoft.com/security/blog/2021/09/07/3-steps-to-prevent-and-recover-from-ransomware/)
- [Przewodnik dotyczący zwalczania oprogramowania wymuszającego okup obsługiwany przez człowieka: część 1 (wrzesień 2021 r.)](https://www.microsoft.com/security/blog/2021/09/20/a-guide-to-combatting-human-operated-ransomware-part-1/)

  Kluczowe instrukcje dotyczące sposobu, w jaki zespół wykrywanie i odpowiedzi firmy Microsoft przeprowadza badania zdarzeń oprogramowania wymuszającego okup.

- [Przewodnik dotyczący zwalczania oprogramowania wymuszającego okup obsługiwany przez człowieka: część 2 (wrzesień 2021 r.)](https://www.microsoft.com/security/blog/2021/09/27/a-guide-to-combatting-human-operated-ransomware-part-2/)

  Rekomendacje i najlepsze rozwiązania.

- [Odporność dzięki zrozumieniu zagrożeń związanych z sezonowością: część 4. — poruszanie się po bieżących zagrożeniach (maj 2021 r.)](https://www.microsoft.com/security/blog/2021/05/26/becoming-resilient-by-understanding-cybersecurity-risks-part-4-navigating-current-threats/)

  Zobacz sekcję **Oprogramowanie wymuszające okup** .

- [Ataki oprogramowania wymuszającego okup przez ludzi: zapobiegalna awaria oprogramowania wymuszającego okup (marzec 2020 r.)](https://www.microsoft.com/security/blog/2020/03/05/human-operated-ransomware-attacks-a-preventable-disaster/)

  Zawiera analizy łańcucha ataków rzeczywistego.

- [Odpowiedź oprogramowania wymuszającego okup — na płatność lub nie? (Grudzień 2019 r.)](https://www.microsoft.com/security/blog/2019/12/16/ransomware-response-to-pay-or-not-to-pay/)
- [Norsk Nie odpowiada na ataki oprogramowania wymuszającego okup z przezroczystością (grudzień 2019 r.)](https://www.microsoft.com/security/blog/2019/12/17/norsk-hydro-ransomware-attack-transparency/)
