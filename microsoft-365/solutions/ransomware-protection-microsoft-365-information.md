---
title: Krok nr 5. Ochrona informacji
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
ms.custom: seo-marvel-jun2020
keywords: ransomware, oprogramowanie wymuszające okup obsługiwane przez człowieka, oprogramowanie wymuszające okup obsługiwane przez człowieka, HumOR, atak wymuszenia, atak ransomware, szyfrowanie, kryptowirtuologia, zero zaufania
description: Użyj kontrolowanego dostępu do folderów, Information Protection Microsoft Purview, DLP i Microsoft Defender for Cloud Apps, aby chronić Microsoft 365 poufne dane.
ms.openlocfilehash: e32c214688adb60fa39fc3c392512f46ec94aecf
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2022
ms.locfileid: "64945136"
---
# <a name="step-5-protect-information"></a>Krok nr 5. Ochrona informacji

Ponieważ osoby atakujące za pomocą oprogramowania wymuszającego okup będą również przeglądać dane lokalne znajdujące się na plikach, bazach danych i innych typach serwerów, jednym z najlepszych sposobów ochrony tych danych jest migrowanie ich do dzierżawy Microsoft 365. W tym miejscu można go chronić za pomocą wbudowanych funkcji ograniczania ryzyka i odzyskiwania, takich jak [przechowywanie wersji, kosz i przywracanie plików](ransomware-protection-microsoft-365.md#ransomware-mitigation-and-recovery-capabilities-provided-with-microsoft-365).

Aby zapewnić dodatkową ochronę poufnych informacji w dzierżawie Microsoft 365:

- Znajdź poufne informacje.
- Zaimplementuj ścisłe uprawnienia i eliminując szeroki dostęp (na przykład uniemożliwiaj zbyt wielu użytkownikom zapisywanie, edytowanie i usuwanie możliwości).
- Chroń poufne informacje.

>[!Note]
>Aby uzyskać szczegółowe wskazówki dotyczące wdrażania ochrony informacji w dzierżawie Microsoft 365, zobacz [Wdrażanie ochrony informacji dla przepisów dotyczących prywatności danych](information-protection-deploy.md). Chociaż są one przeznaczone dla przepisów dotyczących prywatności danych, większość wskazówek ma również zastosowanie do ochrony przed oprogramowaniem wymuszającym okup.
>

## <a name="locate-your-sensitive-information"></a>Znajdowanie poufnych informacji

Pierwszym zadaniem jest [zidentyfikowanie typów i lokalizacji](/microsoft-365/compliance/information-protection#know-your-data) poufnych informacji w dzierżawie, które mogą obejmować następujące typy:

- Wrażliwe
- Własność własnościowa lub własność intelektualna
- Regulowane, takie przepisy regionalne, które określają ochronę danych osobowych (PII)
- Plany odzyskiwania IT

Dla każdego typu informacji poufnych określ następujące kwestie:

- Korzystanie z informacji w organizacji
- Względna miara jego wartości pieniężnej, jeśli była przetrzymywana dla okupu (na przykład wysoka, średnia, niska)
- Jego bieżąca lokalizacja, taka jak folder OneDrive lub SharePoint lub miejsce współpracy, takie jak zespół Microsoft Teams
- Bieżące uprawnienia, które składają się z:

   - Konta użytkowników, którzy mają dostęp

   - Akcje, które są dozwolone dla każdego konta, które ma dostęp 

## <a name="implement-strict-permissions-for-locations-with-sensitive-information"></a>Implementowanie ścisłych uprawnień dla lokalizacji z informacjami poufnymi

Implementowanie ścisłych uprawnień w dzierżawie Microsoft 365 używa zasady najniższych uprawnień dla lokalizacji i miejsc komunikacji, które w Microsoft 365 są zwykle OneDrive folderów, SharePoint lokacji i folderów oraz zespołów. 

Chociaż łatwiej jest tworzyć lokalizacje magazynu plików lub zespoły z szerokim dostępem (na przykład domyślnie dla wszystkich w organizacji), w przypadku informacji poufnych dozwolone konta użytkowników i dozwolone akcje muszą być ograniczone do minimalnego zestawu wymaganego do spełnienia wymagań dotyczących współpracy i działalności biznesowej.

Gdy osoba atakująca oprogramowania wymuszającego okup przeniknie do dzierżawy, próbuje eskalować swoje uprawnienia, narażając poświadczenia kont użytkowników na szersze zakresy uprawnień w dzierżawie, takie jak konta roli administratora lub konta użytkowników, które mają dostęp do poufnych informacji. 

Na podstawie tego typowego zachowania osoby atakującej istnieją dwa poziomy trudności dla osoby atakującej:

- **Niskie:** Osoba atakująca może używać konta o niskich uprawnieniach i odnajdywać poufne informacje ze względu na szeroki dostęp w całej dzierżawie.
- **Wyższe:** Osoba atakująca nie może używać konta o niskich uprawnieniach i odnajdywać poufnych informacji ze względu na ścisłe uprawnienia. Muszą eskalować swoje uprawnienia, określając, a następnie narażając poświadczenia konta, które ma dostęp do lokalizacji z informacjami poufnymi, ale wtedy może być możliwe tylko wykonywanie ograniczonego zestawu akcji.

W przypadku informacji poufnych należy określić poziom trudności tak wysoki, jak to tylko możliwe.

Aby zapewnić ścisłe uprawnienia w dzierżawie, wykonaj następujące kroki:

1. W celu [zlokalizowania poufnych informacji przejrzyj](#locate-your-sensitive-information) uprawnienia do lokalizacji informacji poufnych. 
2. Zaimplementuj ścisłe uprawnienia do informacji poufnych, spełniając wymagania dotyczące współpracy i działalności biznesowej oraz poinformuj użytkowników, których dotyczy problem.
3. Zarządzanie zmianami dla użytkowników umożliwia tworzenie i utrzymywanie przyszłych lokalizacji informacji poufnych przy użyciu ścisłych uprawnień.
4. Przeprowadź inspekcję i monitorowanie lokalizacji pod kątem informacji poufnych, aby upewnić się, że nie są udzielane szerokie uprawnienia.

Aby uzyskać szczegółowe wskazówki[, zobacz Konfigurowanie bezpiecznego udostępniania plików i współpracy z Microsoft Teams](setup-secure-collaboration-with-teams.md). Przykładem miejsca komunikacji i współpracy z rygorystycznymi uprawnieniami do informacji poufnych jest [zespół z izolacją zabezpieczeń](/microsoft-365/solutions/secure-teams-security-isolation).

## <a name="protect-your-sensitive-information"></a>Ochrona poufnych informacji

Aby chronić poufne informacje w przypadku, gdy osoba atakująca wymuszające okup uzyska do nich dostęp:

- Użyj [kontrolowanego dostępu do folderu](/windows/security/threat-protection/microsoft-defender-atp/controlled-folders) , aby utrudnić nieautoryzowanym aplikacjom modyfikowanie danych w kontrolowanych folderach.

- Użyj Information Protection i etykiet poufności [usługi Microsoft Purview](/microsoft-365/compliance/information-protection) i zastosuj je do informacji poufnych. Etykiety poufności można skonfigurować pod kątem dodatkowego szyfrowania i uprawnień przy użyciu zdefiniowanych kont użytkowników i dozwolonych akcji. Plik z etykietą tego typu poufności, który jest eksfiltrowany z dzierżawy, będzie można użyć tylko do konta użytkownika zdefiniowanego w etykiecie.

- Za pomocą usługi Microsoft Purview [Data Loss Prevention (DLP)](/microsoft-365/compliance/dlp-learn-about-dlp) można wykrywać, ostrzegać i blokować ryzykowne, niezamierzone lub niewłaściwe udostępnianie danych zawierających dane osobowe lub poufne na podstawie etykiet poufności, zarówno wewnętrznie, jak i zewnętrznie.

- Użyj [Microsoft Defender for Cloud Apps](/cloud-app-security/what-is-cloud-app-security), aby zablokować pobieranie poufnych informacji, takich jak pliki. Możesz również użyć [zasad wykrywania anomalii usługi Defender dla Chmury Apps](/cloud-app-security/anomaly-detection-policy#ransomware-activity), aby wykryć dużą liczbę działań związanych z przekazywaniem plików lub usuwaniem plików.

## <a name="impact-on-users-and-change-management"></a>Wpływ na użytkowników i zarządzanie zmianami

Zmiany administracyjne dotyczące szerokich uprawnień mogą prowadzić do odmowy dostępu użytkownikom lub nie można wykonać niektórych akcji.

Ponadto w celu ochrony poufnych informacji w dzierżawie Microsoft 365 wytrenuj użytkowników, aby:

- Utwórz miejsca komunikacji i współpracy z uprawnieniami ścisłymi (minimalny zestaw kont użytkowników na potrzeby dostępu i minimalne dozwolone akcje dla każdego konta). 
- Zastosuj odpowiednie etykiety poufności do informacji poufnych.
- Użyj kontrolowanego dostępu do folderu.

## <a name="resulting-configuration"></a>Konfiguracja wyniku

Oto ochrona przed oprogramowaniem wymuszającym okup dla dzierżawy w krokach 1–5.

![Ochrona przed oprogramowaniem wymuszającym okup dla dzierżawy Microsoft 365 po kroku 5](../media/ransomware-protection-microsoft-365/ransomware-protection-microsoft-365-architecture-step5.png)

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
