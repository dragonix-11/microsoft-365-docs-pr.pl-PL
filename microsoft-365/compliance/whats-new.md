---
title: Co nowego w zakresie zgodności Microsoft 365
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
audience: Admin
ms.topic: reference
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- SPO160
- MOE150
- MET150
ms.assetid: e3c6df61-8513-499d-ad8e-8a91770bff63
ms.collection:
- M365-security-compliance
description: Niezależnie od tego, czy chcesz dodać nowe rozwiązania do centrum zgodności, zaktualizować istniejące funkcje na podstawie opinii, czy też zaktualizować nową i zaktualizowaną dokumentację, Microsoft 365 pomoże Ci być na bieżąco z stale zmieniającymi się poziomami zgodności. Dowiedz się, nad czym pracujemy w tym miesiącu.
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: 15a97fc419bc6e4264f3c3cd0bbe389b79e5c2f0
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63326975"
---
# <a name="whats-new-in-microsoft-365-compliance"></a>Co nowego w zakresie zgodności Microsoft 365

Niezależnie od tego, czy chcesz dodać nowe rozwiązania do [Centrum zgodności platformy Microsoft 365,](microsoft-365-compliance-center.md) zaktualizować istniejące funkcje na podstawie opinii, czy też zaktualizować nową i zaktualizowaną dokumentację, Microsoft 365 pomoże Ci być na bieżąco z stale zmieniającymi się poziomami zgodności. Zapoznaj się z poniższymi instrukcjami, aby zobaczyć, co nowego w p Microsoft 365 zgodności.

> [!NOTE]
> Niektóre funkcje zgodności są dostępne dla klientów z różną szybkością. Jeśli jeszcze nie widzisz funkcji, spróbuj dodać siebie do wersji [docelowej](/office365/admin/manage/release-options-in-office-365).

> [!TIP]
> Chcesz się zainteresować tym, co dzieje się w innych centrach aadministracyjnym? Zapoznaj się z tymi artykułami:
>
> - [Co nowego w centrum administracyjne platformy Microsoft 365](/office365/admin/whats-new-in-preview)
> - [Co nowego w centrum administracyjnym SharePoint administracyjnego](/sharepoint/what-s-new-in-admin-center)
> - [Co nowego w programie Microsoft 365 Defender](../security/defender/whats-new.md)
>
> Odwiedź przewodnik po programie [Microsoft 365](https://www.microsoft.com/microsoft-365/roadmap), aby dowiedzieć się więcej o Microsoft 365, które zostały uruchomione, są obecnie wdrażania, są w opracowywania, zostały wycofane lub opublikowane wcześniej.

## <a name="february-2022"></a>Luty 2022 r.

### <a name="ediscovery"></a>zbierania elektronicznych materiałów dowodowych

- [Zarządzanie szablonami komunikacji](advanced-ediscovery-communications-library.md) po stronie Advanced eDiscovery — menedżerowie zbierania elektronicznych materiałów dowodowych mogą teraz tworzyć szablony komunikacji po stronie organizacji, które mogą być używane w Advanced eDiscovery przypadku organizacji.
- [Zarządzanie kierownikami](advanced-ediscovery-issuing-officers.md) ds. wydania w programie Advanced eDiscovery — Menedżerowie zbierania elektronicznych materiałów dowodowych mogą dodawać listę kierowników ds. wydania, których można przypisać do komunikacji w każdym Advanced eDiscovery przypadku w organizacji.

### <a name="information-governance-and-records-management"></a>Zarządzanie informacjami i zarządzanie rekordami

- [Adaptacyjne zakresy](retention.md#adaptive-or-static-policy-scopes-for-retention) zasad przechowywania i zasad etykiet przechowywania są teraz ogólnie dostępne . Instrukcje dotyczące [SharePoint konfigurowania](retention-settings.md#to-configure-an-adaptive-scope) adaptacyjnego zakresu zawierają teraz więcej informacji na temat zakresów witryn: Informacje o wpisie w blogu dotyczące używania niestandardowych właściwości witryny i używania właściwości SiteTemplate do dołączania lub wykluczania określonych typów witryn za pomocą zaawansowanego konstruktora zapytań.
- [Odnośnik zasad w](retention.md#policy-lookup) rozwiązaniu do zarządzania informacjami jest teraz ogólnie dostępny (GA).
- Program PowerShell to alternatywa dla ustawienia zarządzania rekordami, które umożliwia użytkownikom usuwanie elementów oznaczonych w programach SharePoint i OneDrive za pomocą poleceń AllowFilesWithKeepLabelToBeDeletedSPO i AllowFilesWithKeepLabelToBeDeletedODB z systemów [Get-PnPTenant](/powershell/module/sharepoint-pnp/get-pnptenant) i [Set-PnPTenant]( /powershell/module/sharepoint-pnp/set-pnptenant).

### <a name="sensitivity-labels"></a>Etykiety wrażliwości

- Nowe wskazówki Dlaczego warto wybrać wbudowane etykiety miP za pomocą dodatku [AIP](sensitivity-labels-aip.md) dla aplikacji Office, jeśli używasz ujednoliconego klienta etykiet usługi Azure Information Protection (AIP) dla komputerów Windows przenośnych. Ta strona zawiera informacje o nowej prywatnej wersji Preview dla nowych Office aplikacji.
- Nowe ustawienia [zasad automatycznego oznaczania etykiet](apply-sensitivity-label-automatically.md#how-to-configure-auto-labeling-policies-for-sharepoint-onedrive-and-exchange):
  - Dodatkowe ustawienia poczty e-mail do obsługi zawsze stosowania dopasowanej etykiety wrażliwości oraz zastosowania szyfrowania do wiadomości e-mail odbieranych spoza organizacji.
  - Wykluczenia dla określonych wystąpień (użytkowników, grup, witryn) są obsługiwane przy użyciu nowej opcji Wykluczone, gdy dla ustawienia  Wszystkie zostanie określona domyślna opcja **Uwzględniany**.
- Now in preview: Mobile devices (iOS and Android) support [współtworowanie](sensitivity-labels-coauthoring.md) when you have minimum versions and opt in to this preview.
- Obsługa ustawiania domyślnego typu linku udostępniania jest rozszerzana na pojedyncze dokumenty w SharePoint i OneDrive. Aby uzyskać więcej informacji, zobacz nowy artykuł Używanie etykiet wrażliwości do konfigurowania domyślnego typu [linku]( sensitivity-labels-default-sharing-link.md) udostępniania dla witryn i dokumentów w witrynach i SharePoint i OneDrive.
- Teams obsługuje teraz etykiety kontenerów (etykiety wrażliwości z zakresu grup & witryn).

## <a name="january-2022"></a>Styczeń 2022

### <a name="microsoft-information-governance"></a>Microsoft Information Governance

- Strona [i](manage-information-governance.md) sekcja dokumentacji dotyczącej zarządzania informacjami firmy Microsoft w programie Microsoft 365 została znacząco zmieniona i zmieniona w sposób ułatwiający znajdowanie informacji związanych z rozwiązaniami skonfigurowanymi w p programie Centrum zgodności platformy Microsoft 365: łączniki danych, zarządzanie informacjami i zarządzanie rekordami. W ramach tej poprawki w dokumentacji wyraźniejsze rozróżnienie scenariuszy przechowywania informacji w zakresie zarządzania informacjami a zarządzaniem rekordami.
- [Dowiedz się więcej na temat zarządzania informacjami](information-governance.md) — nowe, w celu obsługi struktury ponownej.
- [Wprowadzenie do zarządzania informacjami](get-started-with-information-governance.md) — nowe, które zastępują "Wprowadzenie do przechowywania", ten artykuł zawiera wprowadzenie do wszystkich funkcji zarządzania informacjami, które obejmują przechowywanie.
- [Tworzenie etykiet przechowywania dla wyjątków od zasad przechowywania](create-retention-labels-information-governance.md) — nowego, zidentyfikowanego scenariusza używania etykiet przechowywania do zarządzania informacjami, a nie zarządzania rekordami.
- [Informacje o archiwalnych skrzynkach pocztowych](archive-mailboxes.md) — nowy sposób obsługi struktury zawiera informacje koncepcyjne, które wcześniej były zawarte w tece Włączanie archiwalnych skrzynek pocztowych.

### <a name="microsoft-priva"></a>Microsoft Priva

- [Zarządzanie prywatnością to teraz Microsoft Priva](/privacy/priva/priva-overview) — zaktualizowano w celu zmiany marki produktu i jego rozwiązań, priva zarządzania ryzykiem prywatności i żądań praw podmiotu Priva.

### <a name="sensitivity-labels"></a>Etykiety wrażliwości

- Obsługa nowych grup ról [i ról miP](get-started-with-sensitivity-labels.md#permissions-required-to-create-and-manage-sensitivity-labels) jest teraz w wersji Preview.
- Nowe [funkcje monitorowania](apply-sensitivity-label-automatically.md#monitoring-your-auto-labeling-policy) dotyczące zasad automatycznego oznaczania etykiet.
- Teraz jest wprowadzana etykieta domyślna dla istniejących dokumentów w bieżącym kanale (wersja zapoznawcza) oraz justowanie Office w sieci Web.
- Zapowiedziane na lipiec Semi-Annual Enterprise w wersji 2202+: współtworowanie i inspekcja dla Outlook.

## <a name="december-2021"></a>Grudzień 2021

### <a name="compliance-and-service-assurance"></a>Zgodność i zapewnianie ochrony usługi

- Powiadomienie o naruszeniu usług [Azure, Dynamics 365 i Windows](/compliance/regulatory/gdpr-breach-notification) w ramach RODO — zaktualizowano w celu wyjaśnienia, że klienci nie muszą korzystać z usługi płatności, takiej jak Defender dla chmury, aby otrzymywać powiadomienia o zabezpieczeniach i prywatności

### <a name="ediscovery"></a>zbierania elektronicznych materiałów dowodowych

- [Advanced eDiscovery przepływu pracy dla zawartości w programie Microsoft Teams](teams-workflow-in-advanced-ediscovery.md#reference-guide) — zaktualizowano go o nowy krótki przewodnik do pobrania dotyczący zarządzania zawartością Teams w programie Advanced eDiscovery

### <a name="information-governance"></a>Zarządzanie informacjami

- [Włączanie archiwalnych skrzynek pocztowych w centrum](enable-archive-mailboxes.md#run-diagnostics-on-archive-mailboxes) zgodności — dodano sekcję na temat nowego narzędzia diagnostycznego dla archiwalnych skrzynek pocztowych
- [Importowanie plików PST organizacji do programu](use-network-upload-to-import-pst-files.md#step-2-upload-your-pst-files-to-microsoft-365) za pomocą przekazywania sieciowego Microsoft 365 — import pliku PST obsługuje teraz azcopy w wersji 10
- [Przywracanie nieaktywnej](restore-an-inactive-mailbox.md) skrzynki pocztowej — zmieniono procedurę przywracania nieaktywnej skrzynki pocztowej przez dodanie LegacyExchangeDN nieaktywnej skrzynki pocztowej do docelowej skrzynki pocztowej

### <a name="information-protection"></a>Ochrona informacji

- [Wdrażanie rozwiązania miP](information-protection-solution.md) — nowe wskazówki krok po kroku dla klientów szukających planu wdrażania usługi Microsoft Information Protection (MIP)

### <a name="retention-and-records-management"></a>Przechowywanie i zarządzanie rekordami

- Nowe wskazówki [dotyczące okresu, po jakim](create-retention-policies.md#how-long-it-takes-for-retention-policies-to-take-effect) mają obowiązywać zasady przechowywania
- Nowe ustawienia dzierżawy. Ustawienie zarządzania rekordami, które uniemożliwia edytowanie właściwości elementów oznaczonych jako SharePoint oznaczonych jako rekord i zablokowanych, oraz inne ustawienie uniemożliwiające użytkownikom odblokowywanie elementów oznaczonych jako rekord

### <a name="sensitivity-labels"></a>Etykiety wrażliwości

- Obowiązkowe etykiety i etykieta domyślna Power BI są teraz ogólnie dostępne (GA)

## <a name="november-2021"></a>Listopad 2021

### <a name="compliance-manager"></a>Menedżer zgodności

Nowe aktualizacje zawartości można wyświetlić w [witrynie Co nowego w Menedżerze zgodności firmy Microsoft](compliance-manager-whats-new.md).

### <a name="device-onboarding"></a>Dołączanie urządzenia

Dodano następujące artykuły dotyczące dołączania urządzeń:

- [Dołączanie urządzeń z systemem macOS do Microsoft 365 przegląd (wersja zapoznawcza)](device-onboarding-macos-overview.md)
- [Wdychaj i wydojaj urządzenia z systemem macOS Microsoft 365 rozwiązania zgodności przy użyciu usługi Intune (wersja preview)](device-onboarding-offboarding-macos-intune.md)
- [Dołączanie i wydojażanie urządzeń macOS w rozwiązaniach zgodności przy użyciu usługi Intune dla klientów programu Microsoft Defender for Endpoint (wersja preview)](device-onboarding-offboarding-macos-intune-mde.md)
- [Urządzenia z systemem macOS w nowych Microsoft 365 zgodności przy użyciu usługi JAMF Pro (wersja zapoznawcza)](device-onboarding-offboarding-macos-jamfpro.md)
- [Dołączanie i wydoszczenie urządzeń macOS w rozwiązaniach zgodności przy użyciu usługi JAMF Pro dla klientów programu Microsoft Defender for Endpoint (wersja preview)](device-onboarding-offboarding-macos-jamfpro-mde.md)

### <a name="ediscovery"></a>zbierania elektronicznych materiałów dowodowych

- [Nowy format sprawy w formacie Advanced eDiscovery](advanced-ediscovery-new-case-format.md) został wydany w ogólnoowej dostępności i zmieniono jego nazwę na "duży format sprawy".

### <a name="retention-and-records-management"></a>Przechowywanie i zarządzanie rekordami
- Nowość: Nowe ustawienia zarządzania rekordami, które sterują tym, czy elementy SharePoint i OneDrive mogą być usuwane przez użytkowników. Wcześniej etykiety przechowywania skonfigurowane w taki sposób, aby zachowywały zawartość i które nie oznaczały elementów jako rekordów, uniemożliwiały użytkownikom usuwanie zawartości oznaczonej etykietą w programie SharePoint, gdy ta akcja została dozwolona w programie OneDrive. Aby uzyskać więcej informacji, zobacz [Jak działa przechowywanie w SharePoint i OneDrive](retention-policies-sharepoint.md#how-retention-works-for-sharepoint-and-onedrive).

### <a name="sensitive-information-types"></a>Typy informacji poufnych

Dodano następujące nowe artykuły:

- [Informacje o dokładnie tych typach informacji poufnych na podstawie danych](sit-learn-about-exact-data-match-based-sits.md)
- [Wprowadzenie do dokładnych typów informacji poufnych opartych na danych](sit-get-started-exact-data-match-based-sits-overview.md)
- [Eksportowanie danych źródłowych w celu dokładnego dopasowania danych na podstawie typu informacji poufnych](sit-get-started-exact-data-match-export-data.md)
- [Tworzenie schematu w celu dokładnego dopasowania danych do typów informacji poufnych](sit-get-started-exact-data-match-create-schema.md)
- [Skróty i przekazywanie tabeli źródła informacji poufnych w celu dokładnego dopasowania danych do typów informacji poufnych](sit-get-started-exact-data-match-hash-upload.md)
- [Tworzenie dokładnego dopasowania danych do typów informacji poufnych/pakietu reguł](sit-get-started-exact-data-match-create-rule-package.md)
- [Testowanie dokładnego dopasowania danych do typu informacji poufnych](sit-get-started-exact-data-match-test.md)
- [Zarządzanie dokładnym schematem dopasowania danych](sit-use-exact-data-manage-schema.md)
- [Odświeżanie pliku tabeli źródłowej informacji poufnych](sit-use-exact-data-refresh-data.md)

### <a name="sensitivity-labels"></a>Etykiety wrażliwości
- Nazwa zakresu etykiet usługi [Azure Purview to](/azure/purview/create-sensitivity-label) teraz "Schematowane zasoby danych".

## <a name="october-2021"></a>Październik 2021

### <a name="app-governance"></a>Zarządzanie aplikacją

- [Dla usługi Defender](/cloud-app-security/app-governance-manage-app-governance) dla aplikacji w chmurze opublikowano dodatek do zarządzania aplikacjami w ogólną dostępność. Dokumentacja zarządzania aplikacjami została przeniesiona w celu dołączenia do dokumentacji programu Defender dla aplikacji w chmurze.

### <a name="compliance--service-assurance"></a>Zapewnianie zgodności & usługi

- [Zapewnianie ochrony](/compliance) usługi — kwartalne przeglądanie aktualizacji zawartości certyfikatów i instrukcje dotyczące stosowania) Zarządzanie zasobami centrum danych
  - Architektura i infrastruktura centrum danych
  - Zapewnianie ciągłości działania i odzyskiwanie po awarii centrum danych
  - Ochrona środowiska w centrum danych
  - Zabezpieczenia dostępu fizycznego w centrum danych
  - Microsoft 365 zgodności SDL
  - Microsoft 365 kontroli dostępu dla inżyniera usługi
  - Przewodnik po ocenie ryzyka dla usługi MS Cloud

### <a name="data-loss-prevention"></a>Ochrona przed utratą danych

- [Dowiedz się więcej o funkcji Zapobieganie utracie](endpoint-dlp-learn-about.md) danych w przypadku obsługi i zaawansowanej klasyfikacji systemu macOS. zaktualizowano w celu utworzenia niestandardowych zasad DLP w celu inspekcji aktywności we wszystkich obsługiwanych typach plików.
- [Wprowadzenie do ochrony Microsoft 365 danych punktu](endpoint-dlp-getting-started.md) końcowego zostało zaktualizowane w celu obsługi i zaawansowanej klasyfikacji systemu macOS.
- [Zaktualizowano korzystanie z ochrony przed utratą danych](endpoint-dlp-using.md) w punkcie końcowym na poziomie pomocy technicznej i zaawansowanej klasyfikacji systemu macOS.
- [Porady dotyczące zasad ochrony przed utratą danych zostały](dlp-policy-tips-reference.md) zaktualizowane w celu obsługi i zaawansowanej klasyfikacji systemu macOS.
- [Na urządzeniach z systemem macOS Microsoft 365 (wersja zapoznawcza) zaktualizowano](device-onboarding-macos-overview.md) na poziomie pomocy technicznej i zaawansowanej klasyfikacji systemu macOS.
- Dodano następujące nowe strony dla urządzeń dołączających:
  - [Wdychaj i wydojaj urządzenia z systemem macOS Microsoft 365 rozwiązania zgodności przy użyciu usługi Intune (wersja preview)](device-onboarding-offboarding-macos-intune.md)
  - [Dołączanie i wydojażanie urządzeń macOS w rozwiązaniach zgodności przy użyciu usługi Intune dla klientów programu Microsoft Defender for Endpoint (wersja preview)](device-onboarding-offboarding-macos-intune-mde.md)
  - [Urządzenia z systemem macOS w nowych Microsoft 365 zgodności przy użyciu usługi JAMF Pro (wersja zapoznawcza)](device-onboarding-offboarding-macos-jamfpro.md)
  - [Dołączanie i wydoszczenie urządzeń macOS w rozwiązaniach zgodności przy użyciu usługi JAMF Pro dla klientów programu Microsoft Defender for Endpoint (wersja preview)](device-onboarding-offboarding-macos-jamfpro-mde.md)

### <a name="ediscovery"></a>zbierania elektronicznych materiałów dowodowych

- Zbieraj załączniki w chmurze w programie [Advanced eDiscovery](advanced-ediscovery-cloud-attachments.md) poza zbieraniem najnowszej wersji załącznika w chmurze, możesz zbierać wersję udostępnioną w wiadomości e-mail lub konwersacji na czacie programu Teams. Zbieranie informacji o wersji udostępnionej jest możliwe dzięki nowej funkcji automatycznego stosowania etykiet przechowywania do załączników w chmurze.
- Skonfiguruj wersje historyczne w [programie Advanced eDiscovery](advanced-ediscovery-historical-versions.md) nową funkcję indeksowania wszystkich wersji dokumentów przechowywanych w witrynie programu SharePoint w celu wyszukiwania. Oznacza SharePoint, że wersje dokumentów zawierające zawartość dopasowaną do zapytania kolekcji są zwracane w wynikach wyszukiwania.

### <a name="encryption"></a>Szyfrowanie

- [Szyfrowanie połączeń Microsoft Teams przychodzących](/microsoftteams/teams-end-to-end-encryption) (publiczna wersja zapoznawcza) Nowa zawartość do podglądu publicznego, użyj szyfrowania jeden do jednego.

### <a name="information-governance"></a>Zarządzanie informacjami

- [Konfigurowanie łącznika w](import-epic-data.md) celu importowania danych inspekcji EHR Nowy łącznik umożliwia importowanie danych z systemu elektronicznej opieki zdrowotnej Do obsługi nowego ogólnego scenariusza błędnego użycia danych pacjentów na rzecz zarządzania ryzykiem w niejawnym programie testów.
- [Konfigurowanie łącznika](import-healthcare-data.md) do importowania danych inspekcji EHR opieki zdrowotnej Nowy łącznik umożliwia importowanie danych z systemu elektronicznej dokumentacji opieki zdrowotnej w celu obsługi nowego ogólnego scenariusza błędnego użycia danych pacjenta w zarządzaniu ryzykiem w ramach niejawnego programu testów.

### <a name="retention-and-records-management"></a>Przechowywanie i zarządzanie rekordami
- [Zakresy adaptacyjnych zasad są](retention.md#adaptive-or-static-policy-scopes-for-retention) dostępne w wersji Preview w przypadku zasad przechowywania i zasad etykiet przechowywania.
- Teraz możesz [automatycznie zastosować etykietę przechowywania na podstawie etykiety wrażliwości](apply-retention-labels-automatically.md#identify-files-and-emails-that-have-a-sensitivity-label).
- W planie importu jest nowy [proces importowania](file-plan-manager.md#import-retention-labels-into-your-file-plan).
- [Typowe ustawienia zasad przechowywania i zasad etykiet](retention-settings.md) przechowywania: Nowy artykuł ze szczegółowymi informacjami na temat konfigurowania adaptacyjnych zakresów i innych ustawień w zasadach przechowywania i zasadach etykiet przechowywania.

### <a name="sensitive-information-types"></a>Typy informacji poufnych

- [Dowiedz się więcej o nazwanych jednostkach (podgląd)](named-entities-learn.md) nowej zawartości dla nazwanych jednostek.
- [Używaj nazwanych obiektów w zasadach ochrony przed utratą danych (podgląd)](named-entities-use.md) nowej zawartości dotyczącej używania nazwanych jednostek.

### <a name="sensitivity-labels"></a>Etykiety wrażliwości

- [Etykiety domyślne i zasady domyślne](mip-easy-trials.md) są obecnie dostępne dla uprawnionych klientów.

## <a name="september-2021"></a>Wrzesień 2021

### <a name="app-governance"></a>Zarządzanie aplikacją

- [Usprawnione zarządzanie wprowadzeniem informacji o aplikacjach](app-governance-get-started.md) uległo zmianie i dodano nowe linki do publicznego procesu rejestracji w wersji Preview
- [Dodano nową definicję](app-governance-anomaly-detection-alerts.md#app-made-high-volume-of-importance-mail-read-and-created-inbox-rule) alertów wykrywania (zaktualizowano; dodano nową definicję alertów kolekcji)

### <a name="auditing"></a>Inspekcja

- [Włączanie lub wyłączanie inspekcji w](turn-audit-log-search-on-or-off.md) nowej sekcji dotyczącej sposobu inspekcji zmian stanu inspekcji w organizacji; oznacza to, że rekordy inspekcji są rejestrowane, gdy inspekcja jest włączona lub wyłączona. przeszukiwać dziennik inspekcji Exchange w poszukiwaniu tych rekordów inspekcji

### <a name="communication-compliance"></a>Zgodność komunikacji

- [Zgodność komunikacji z rozwiązaniami SIEM](communication-compliance-siem.md) w zakresie integracji zgodności komunikacji z rozwiązaniami SIEM)

### <a name="compliance-offerings"></a>Oferty dotyczące zgodności

- [Zabezpieczenia wielopoziomowe w chmurze (MTCS)](/compliance/regulatory/offering-mtcs-singapore) Standardowe aktualizacje dla Singapuru dla usługi Dynamics 365
- [Branża kart płatniczych (PCI)](/compliance/regulatory/offering-pci-dss) Aktualizacje standardu zabezpieczeń danych (DSS, Data Security Standard) dotyczące SharePoint online
- [Wskazówki dotyczące nowego oprogramowania klienckiego w sekcji 508](/compliance/regulatory/offering-section-508-vpats) dla Stanów Zjednoczonych
- [Wskazówki dotyczące ułatwień dostępu dla zawartości sieci Web](/compliance/regulatory/offering-wcag-2-1) , wskazówki dotyczące nowego oprogramowania klienckiego

### <a name="compliance--service-assurance"></a>Zapewnianie zgodności & usługi

- [Kwartalne](/compliance/) przeglądanie aktualizacji zawartości na temat zapewniania ochrony usługi dla certyfikatów i potwierdzeń stosowania
  - Sprocentrowanie urządzenia z wpływami na dane
  - Ataki DDOS

### <a name="data-connectors"></a>Łączniki danych

- [Archiwizowanie danych innych firm w łącznikach danych Microsoft 365](archiving-third-party-data.md#data-connectors-in-the-us-government-cloud) firmy CellTrust i firmy 17a-4 LLC. Jest teraz dostępne w GCC organizacjach w chmurze amerykańskiej instytucji rządowych
- [Skonfigurowanie łącznika do archiwizowania danych z serwisu YouTube](archive-youtube-data.md) udostępnia nowe wskazówki dotyczące tej funkcji w publicznej wersji zapoznawczej.

### <a name="ediscovery"></a>zbierania elektronicznych materiałów dowodowych

- Za pomocą edytora [KQL](ediscovery-kql-editor.md) można tworzyć publiczne podglądy zapytań wyszukiwania w nowy sposób na tworzenie zapytań wyszukiwania w przeszukiwaniu zawartości, zbierania elektronicznych materiałów dowodowych i Advanced eDiscovery; edytor KQL udostępnia autouzupełnianie obsługiwanych właściwości i warunków, które można wyszukiwać, oraz wyświetla listy obsługiwanych wartości standardowych właściwości i warunków. Edytor KQL udostępnia również funkcje wykrywania błędów i sugestii dotyczących poprawek potencjalnych błędów w zapytaniach wyszukiwania

### <a name="information-barriers"></a>Bariery informacyjne

- [Wprowadzenie do barier informacyjnych Nowa](information-barriers-policies.md#step-6-information-barriers-modes) funkcja wersji Preview dla trybów informacyjnych
- [Bariery informacyjne dzięki Microsoft Teams](/microsoftteams/information-barriers-in-teams) funkcji podglądu dla trybów informacyjnych
- [Bariery informacyjne dzięki OneDrive](/onedrive/information-barriers) funkcji podglądu dla trybów informacyjnych
- [Bariery informacyjne dzięki nowej SharePoint wersji Zapoznawczej w](/sharepoint/information-barriers) trybie online dla trybów informacyjnych

### <a name="insider-risk-management"></a>Zarządzanie ryzykiem w niejawnym programie testów

- [Wprowadzenie do nowej funkcji wersji Preview do zarządzania ryzykiem](insider-risk-management-configure.md#recommended-actions-preview) w ramach niejawnego programu testów, która umożliwia rozpoczęcie zalecanych akcji
- [Badanie działań ryzyka w niejawnym programie](insider-risk-management-activities.md#get-help-managing-your-insider-risk-alert-queue) testów nowa sekcja "Uzyskaj pomoc w zarządzaniu kolejką alertów o ryzyku niejawnego programu testów"
- [Wprowadzenie do ustawień zarządzania ryzykiem w niejawnym programie testów Nowa](insider-risk-management-settings.md#admin-notifications) funkcja w wersji Preview ustawień powiadomień administratora

### <a name="retention-and-records-management"></a>Przechowywanie i zarządzanie rekordami
- [Wieloetapowy przegląd rozsyłania](disposition.md) jest teraz ogólnie dostępny (GA, Multi-stage disposition review) z [nowymi zdarzeniami inspekcji](search-the-audit-log-in-security-and-compliance.md#disposition-review-activities). Wieloetapowy przegląd rozsyłania umożliwia określenie do pięciu kolejnych etapów recenzji ich przechowywania, a recenzentzy mogą dodawać innych użytkowników do etapu recenzji ich rozsyłania. Możesz także dostosować powiadomienia e-mail i przypomnienia.
- Kanały prywatne dla [Teams przechowywania](create-retention-policies.md#retention-policy-for-teams-locations) są teraz ogólnie dostępne (GA).

### <a name="sensitivity-labels"></a>Etykiety wrażliwości
- [](sensitivity-labels-coauthoring.md) Funkcja współtworzenia i autozazyskiwu są teraz ogólnie dostępne dla systemu Windows (minimalna wersja 2107 z bieżącego kanału lub miesięcznego kanału Enterprise) i systemu macOS (minimalna wersja 16.51).
- Wdowy dla Office, które korzystają z wbudowanych etykiet: Domyślne ustawienie etykiet obsługuje teraz istniejące dokumenty, a także nowe dokumenty. Taka zmiana w zachowaniu zapewnia parowanie z ujednoliconym klientem etykiet usługi Azure Information Protection. Aby uzyskać więcej informacji na temat rzutowania na aplikację i wersji minimalnych, [](sensitivity-labels-office-apps.md#sensitivity-label-capabilities-in-word-excel-and-powerpoint) zobacz tabelę możliwości dla programu Word, Excel i PowerPoint.
- Etykiety kontenerów obsługują [teraz domyślne ustawienia linku udostępniania przy użyciu ustawień zaawansowanych programu PowerShell](sensitivity-labels-teams-groups-sites.md#configure-settings-for-the-default-sharing-link-type-for-a-site-by-using-powershell-advanced-settings).
- Tabele [funkcji, które](sensitivity-labels-office-apps.md#support-for-sensitivity-label-capabilities-in-apps) zawierają minimalne obsługiwane wersje wbudowanych etykiet, mają teraz wersje dla bieżącego kanału, miesięcznego kanału Enterprise i Semi-Annual Enterprise kanału.
