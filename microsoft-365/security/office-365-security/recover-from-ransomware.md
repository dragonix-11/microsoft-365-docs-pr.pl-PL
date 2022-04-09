---
title: Odzyskiwanie po ataku wymuszającym okup
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: article
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
- m365solution-ransomware
description: Microsoft 365 administratorzy mogą dowiedzieć się, jak odzyskać sprawności po ataku wymuszającym okup.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 8e5e942bb39097fffa955d5bb9c3b8a72212d0cc
ms.sourcegitcommit: 1ef176c79a0e6dbb51834fe30807409d4e94847c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/19/2021
ms.locfileid: "64730851"
---
# <a name="recover-from-a-ransomware-attack-in-microsoft-365"></a>Odzyskiwanie po ataku ransomware w Microsoft 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Usługi Microsoft Defender dla usługi Office 365 (plan 1 i plan 2)](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Nawet jeśli podejmiesz wszelkie środki ostrożności, aby chronić swoją organizację, nadal możesz paść ofiarą ataku [ransomware](/windows/security/threat-protection/intelligence/ransomware-malware) . Ransomware to wielki biznes, a w dzisiejszym krajobrazie zagrożeń Microsoft 365 jest coraz większym [celem wyrafinowanych ataków](https://i.blackhat.com/USA21/Wednesday-Handouts/us-21-Cloudy-With-A-Chance-Of-APT-Novel-Microsoft-365-Attacks-In-The-Wild.pdf).

Kroki opisane w tym artykule dają największą szansę na odzyskanie danych i zatrzymanie wewnętrznego rozprzestrzeniania się infekcji. Przed rozpoczęciem należy wziąć pod uwagę następujące elementy:

- Nie ma gwarancji, że zapłacenie okupu zwróci dostęp do plików. W rzeczywistości płacenie okupu może sprawić, że będziesz celem dla większej liczby ransomware.

  Jeśli już zapłacono, ale odzyskano je bez korzystania z rozwiązania osoby atakującej, skontaktuj się z bankiem, aby sprawdzić, czy może zablokować transakcję.

  Zalecamy również zgłoszenie ataku wymuszającego okup do organów ścigania, witryn internetowych raportowania oszustw i firmy Microsoft zgodnie z opisem w dalszej części tego artykułu.

- Ważne jest, aby szybko reagować na atak i jego konsekwencje. Tym dłużej czekasz, tym mniejsze jest prawdopodobieństwo odzyskania danych, których dotyczy problem.

## <a name="step-1-verify-your-backups"></a>Krok 1. Weryfikowanie kopii zapasowych

Jeśli masz kopie zapasowe w trybie offline, prawdopodobnie możesz przywrócić zaszyfrowane dane **po** usunięciu ładunku wymuszającego okup (złośliwe oprogramowanie) ze środowiska i **po** sprawdzeniu, czy nie ma nieautoryzowanego dostępu w środowiskach Microsoft 365.

Jeśli nie masz kopii zapasowych lub jeśli oprogramowanie wymuszające okup również miało wpływ na kopie zapasowe, możesz pominąć ten krok.

## <a name="step-2-disable-exchange-activesync-and-onedrive-sync"></a>Krok 2. Wyłączanie Exchange ActiveSync i synchronizacja usługi OneDrive

Kluczowym punktem jest zatrzymanie rozprzestrzeniania się szyfrowania danych przez oprogramowanie wymuszające okup.

Jeśli podejrzewasz, że wiadomość e-mail jest celem szyfrowania oprogramowania wymuszającego okup, tymczasowo wyłącz dostęp użytkowników do skrzynek pocztowych. Exchange ActiveSync synchronizuje dane między urządzeniami i skrzynkami pocztowymi Exchange Online.

Aby wyłączyć Exchange ActiveSync dla skrzynki pocztowej, zobacz [Jak wyłączyć Exchange ActiveSync dla użytkowników w Exchange Online](https://support.microsoft.com/help/2795303).

Aby wyłączyć inne typy dostępu do skrzynki pocztowej, zobacz:

- [Włącz lub wyłącz mapę MAPI dla skrzynki pocztowej](/Exchange/recipients-in-exchange-online/manage-user-mailboxes/enable-or-disable-mapi).

- [Włączanie lub wyłączanie dostępu POP3 lub IMAP4 dla użytkownika](/Exchange/clients-and-mobile-in-exchange-online/pop3-and-imap4/enable-or-disable-pop3-or-imap4-access)

Wstrzymanie synchronizacja usługi OneDrive pomoże chronić dane w chmurze przed aktualizacją przez potencjalnie zainfekowane urządzenia. Aby uzyskać więcej informacji, zobacz [Jak wstrzymywać i wznawiać synchronizację w OneDrive](https://support.microsoft.com/office/2152bfa4-a2a5-4d3a-ace8-92912fb4421e).

## <a name="step-3-remove-the-malware-from-the-affected-devices"></a>Krok 3. Usuwanie złośliwego oprogramowania z urządzeń, których dotyczy problem

Uruchom pełne, bieżące skanowanie antywirusowe na wszystkich podejrzanych komputerach i urządzeniach, aby wykryć i usunąć ładunek skojarzony z oprogramowaniem wymuszającym okup.

Nie zapomnij przeskanować urządzeń synchronizujących dane lub obiektów docelowych zamapowanych dysków sieciowych.

Można użyć [Windows Defender](https://www.microsoft.com/windows/comprehensive-security) lub (dla starszych klientów) [Microsoft Security Essentials](https://www.microsoft.com/download/details.aspx?id=5201).

Alternatywą, która pomoże Ci również usunąć oprogramowanie wymuszające okup lub złośliwe oprogramowanie, jest [narzędzie do usuwania złośliwego oprogramowania (MSRT).](https://www.microsoft.com/download/details.aspx?id=9905)

Jeśli te opcje nie działają, możesz spróbować [Windows Defender w trybie offline](https://support.microsoft.com/help/17466) lub [rozwiązać problemy z wykrywaniem i usuwaniem złośliwego oprogramowania](https://support.microsoft.com/help/4466982).

## <a name="step-4-recover-files-on-a-cleaned-computer-or-device"></a>Krok 4. Odzyskiwanie plików na oczyszczonym komputerze lub urządzeniu

Po wykonaniu poprzedniego kroku w celu usunięcia ładunku oprogramowania wymuszającego okup ze środowiska (co uniemożliwi oprogramowanie wymuszające okup szyfrowanie lub usunięcie plików), możesz użyć [historii plików](https://support.microsoft.com/help/17128) w Windows 11, Windows 10, Windows 8.1 i za pomocą ochrony systemu w Windows 7, aby spróbować odzyskać lokalne pliki i foldery.

**Uwagi**:

- Niektóre programy wymuszające okup będą również szyfrować lub usuwać wersje kopii zapasowych, więc nie można przywrócić plików za pomocą historii plików ani ochrony systemu. W takim przypadku należy użyć kopii zapasowych na dyskach zewnętrznych lub urządzeniach, na które oprogramowanie wymuszające okup lub OneDrive nie miało wpływu, zgodnie z opisem w następnej sekcji.

- Jeśli folder jest synchronizowany z OneDrive i nie używasz najnowszej wersji Windows, mogą istnieć pewne ograniczenia dotyczące historii plików.

## <a name="step-5-recover-your-files-in-your-onedrive-for-business"></a>Krok 5. Odzyskiwanie plików w OneDrive dla Firm

Przywracanie plików w OneDrive dla Firm umożliwia przywrócenie całego OneDrive do poprzedniego punktu w czasie w ciągu ostatnich 30 dni. Aby uzyskać więcej informacji, zobacz artykuł [Przywracanie w usłudze OneDrive](https://support.microsoft.com/office/fa231298-759d-41cf-bcd0-25ac53eb8a15).

## <a name="step-6-recover-deleted-email"></a>Krok 6. Odzyskiwanie usuniętej wiadomości e-mail

W rzadkich przypadkach, gdy oprogramowanie wymuszające okup usunęło całą wiadomość e-mail, prawdopodobnie można odzyskać usunięte elementy. Więcej informacji można znaleźć w następujących artykułach:

- [Odzyskiwanie usuniętych wiadomości w skrzynce pocztowej użytkownika](/exchange/recipients-in-exchange-online/manage-user-mailboxes/recover-deleted-messages)

- [Odzyskiwanie usuniętych elementów w Outlook dla Windows](https://support.microsoft.com/office/49e81f3c-c8f4-4426-a0b9-c0fd751d48ce)

## <a name="step-7-re-enable-exchange-activesync-and-onedrive-sync"></a>Krok 7. Ponowne włączanie Exchange ActiveSync i synchronizacja usługi OneDrive

Po oczyszczeniu komputerów i urządzeń oraz odzyskaniu danych można ponownie włączyć Exchange ActiveSync i synchronizacja usługi OneDrive, które zostały wcześniej wyłączone w [kroku 2](#step-2-disable-exchange-activesync-and-onedrive-sync).

## <a name="step-8-optional-block-onedrive-sync-for-specific-file-extensions"></a>Krok 8 (opcjonalnie): blokuj synchronizacja usługi OneDrive dla określonych rozszerzeń plików

Po odzyskaniu danych można uniemożliwić OneDrive dla Firm klientom synchronizowanie typów plików, których dotyczy ten oprogramowanie wymuszające okup. Aby uzyskać więcej informacji, zobacz [Set-SPOTenantSyncClientRestriction](/powershell/module/sharepoint-online/set-spotenantsyncclientrestriction)

## <a name="report-the-attack"></a>Zgłoś atak

### <a name="contact-law-enforcement"></a>Skontaktuj się z organami ścigania

Należy skontaktować się z lokalnymi lub federalnymi organami ścigania. Jeśli na przykład jesteś w Stany Zjednoczone możesz skontaktować się z [lokalnym biurem terenowym FBI](https://www.fbi.gov/contact-us/field), [IC3](http://www.ic3.gov/complaint/default.aspx) lub [Secret Service](http://www.secretservice.gov/).

### <a name="submit-a-report-to-your-countrys-scam-reporting-website"></a>Przesyłanie raportu do witryny internetowej zgłaszania oszustw w twoim kraju

Witryny z raportami o oszustwach zawierają informacje o tym, jak zapobiegać oszustwom i unikać ich. Zapewniają one również mechanizmy zgłaszania, jeśli padłeś ofiarą oszustwa.

- Australia: [SCAMwatch](http://www.scamwatch.gov.au/)

- Kanada: [Kanadyjskie Centrum Zwalczania Nadużyć Finansowych](http://www.antifraudcentre-centreantifraude.ca/)

- Francja: [Agence nationale de la sécurité des systèmes d'information](http://www.ssi.gouv.fr/)

- Niemcy: [Bundesamt für Sicherheit in der Informationstechnik](https://www.bsi.bund.de/DE/Home/home_node.html)

- Irlandia: [Garda Síochána](http://www.garda.ie/)

- Nowa Zelandia: [Oszustwa w sprawach konsumenckich](http://www.consumeraffairs.govt.nz/scams)

- Szwajcaria [Nationales Zentrum für Cybersicherheit NCSC](https://www.ncsc.admin.ch/ncsc/de/home.html)

- Wielka Brytania: [Action Fraud](http://www.actionfraud.police.uk/)

- Stany Zjednoczone: [On Guard Online](http://www.onguardonline.gov/)

Jeśli Twojego kraju nie ma na liście, zapytaj lokalne lub federalne organy ścigania.

### <a name="submit-email-messages-to-microsoft"></a>Przesyłanie wiadomości e-mail do firmy Microsoft

Komunikaty wyłudzania informacji zawierające oprogramowanie wymuszające okup można zgłaszać przy użyciu jednej z kilku metod. Aby uzyskać więcej informacji, zobacz [Zgłaszanie komunikatów i plików do firmy Microsoft](report-junk-email-messages-to-microsoft.md).

## <a name="additional-ransomware-resources"></a>Dodatkowe zasoby oprogramowania wymuszającego okup

Kluczowe informacje od firmy Microsoft:

- [Rosnące zagrożenie oprogramowaniem wymuszającym okup](https://blogs.microsoft.com/on-the-issues/2021/07/20/the-growing-threat-of-ransomware/), wpis w blogu Microsoft On the Issues 20 lipca 2021 r.
- [Oprogramowanie wymuszające okup obsługiwane przez człowieka](/security/compass/human-operated-ransomware)
- [Szybka ochrona przed oprogramowaniem wymuszającym okup i wymuszeniami](/security/compass/protect-against-ransomware)
- [2021 Microsoft Digital Defense Report](https://www.microsoft.com/security/business/microsoft-digital-defense-report) (zobacz strony 10–19)
- [Oprogramowanie wymuszające okup: wszechobecny i ciągły](https://security.microsoft.com/threatanalytics3/05658b6c-dc62-496d-ad3c-c6a795a33c27/overview) raport analizy zagrożeń w portalu Microsoft 365 Defender

Microsoft 365:

- [Wdrażanie ochrony przed oprogramowaniem wymuszającym okup dla dzierżawy Microsoft 365](/microsoft-365/solutions/ransomware-protection-microsoft-365)
- [Maksymalizowanie odporności oprogramowania wymuszającego okup za pomocą platformy Azure i Microsoft 365](https://azure.microsoft.com/resources/maximize-ransomware-resiliency-with-azure-and-microsoft-365/)
- [Ochrona przed złośliwym oprogramowaniem i oprogramowaniem wymuszającym okup](/compliance/assurance/assurance-malware-and-ransomware-protection)
- [Ochrona komputera Windows przed oprogramowaniem wymuszającym okup](https://support.microsoft.com//windows/protect-your-pc-from-ransomware-08ed68a7-939f-726c-7e84-a72ba92c01c3)
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
