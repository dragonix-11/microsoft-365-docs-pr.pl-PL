---
title: Co nowego w usłudze Microsoft Purview
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
description: Niezależnie od tego, czy chodzi o dodawanie nowych rozwiązań do centrum zgodności, aktualizowanie istniejących funkcji na podstawie opinii, czy wprowadzanie nowej i zaktualizowanej dokumentacji, Microsoft 365 pomaga być na bieżąco z ciągle zmieniającym się poziomem zgodności. Dowiedz się, co mieliśmy do tego miesiąca.
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: 20a8a96146b7f65ef3f8ccec4f099b91d74822a0
ms.sourcegitcommit: 6c2ab5e8efe74d0dc2df610e2d9d2fdda8aaf074
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/25/2022
ms.locfileid: "65670107"
---
# <a name="whats-new-in-microsoft-purview"></a>Co nowego w usłudze Microsoft Purview

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Niezależnie od tego, czy chodzi o dodawanie nowych rozwiązań do [portal zgodności Microsoft Purview](microsoft-365-compliance-center.md), aktualizowanie istniejących funkcji na podstawie opinii, czy wprowadzanie nowej i zaktualizowanej dokumentacji, Microsoft 365 pomaga być na bieżąco z ciągle zmieniającym się poziomem zgodności. Spójrz poniżej, aby zobaczyć, co nowego w Microsoft Purview dzisiaj.

> [!NOTE]
> Niektóre funkcje zgodności są wdrażane z różnymi prędkościami dla naszych klientów. Jeśli nie widzisz jeszcze funkcji, spróbuj dodać siebie do [docelowej wersji](/office365/admin/manage/release-options-in-office-365).

> [!TIP]
> Interesuje Cię to, co dzieje się w innych centrach administracyjnych? Zapoznaj się z następującymi artykułami:
>
> - [Co nowego w Centrum administracyjne platformy Microsoft 365](/office365/admin/whats-new-in-preview)
> - [Co nowego w centrum administracyjnym SharePoint](/sharepoint/what-s-new-in-admin-center)
> - [Co nowego w usłudze Microsoft 365 Defender](../security/defender/whats-new.md)
>
> I odwiedź [Microsoft 365 plan,](https://www.microsoft.com/microsoft-365/roadmap) aby dowiedzieć się więcej o Microsoft 365 funkcji, które zostały uruchomione, są wdrażane, są w programie, zostały anulowane lub wcześniej wydane.

## <a name="april-2022"></a>Kwiecień 2022 r.

### <a name="communication-compliance"></a>Zgodność w komunikacji

- [Tworzenie zasad zgodności komunikacji i zarządzanie nimi](communication-compliance-policies.md) — zaktualizowano ją o wskazówki dotyczące nowej funkcji zasad komunikatów zgłaszanych przez użytkowników na potrzeby integracji Microsoft Teams.
- [Wprowadzenie ze zgodnością z komunikacją](communication-compliance-configure.md) — zaktualizowano w celu dodania wyjaśnień dotyczących subskrypcji i licencjonowania F5.

### <a name="compliance-manager"></a>Menedżer zgodności

- [Lista szablonów programu Compliance Manager](compliance-manager-templates-list.md) — dodano 6 nowych szablonów i linków nawigacyjnych na stronie, aby łatwiej przejść do kategorii szablonów.
- [Omówienie programu Compliance Manager](compliance-manager.md) — zaktualizowane wideo z omówieniem produktu.

### <a name="compliance-offerings--service-assurance"></a>Oferty zgodności & service assurance

- [Oferty zgodności](/compliance/regulatory/offering-home) — aktualizacje dotyczące pokrycia usług i raportowania inspekcji dla ofert VPATS, SOC, ISO i FedRAMP.

### <a name="data-lifecycle-management-and-records-management"></a>Zarządzanie cyklem życia danych i zarządzanie rekordami

- Zmiana [nazwy produktu](#changes-to-product-names) powoduje zmianę **nazwy zarządzania informacjami** na **Zarządzanie cyklem życia danych** w portalu zgodności.
- Obecnie wdrażane: nowy projekt konfiguracji ustawień etykiety przechowywania.
- Obecnie wdrażana: nowa opcja etykiety w wersji zapoznawczej: "Domyślnie odblokuj ten rekord". Aby uzyskać więcej informacji, zobacz [Konfigurowanie etykiet przechowywania do deklarowania rekordów](declare-records.md#configuring-retention-labels-to-declare-records) i [Używanie przechowywania wersji rekordów do aktualizowania rekordów przechowywanych w SharePoint lub OneDrive](record-versioning.md).

### <a name="data-loss-prevention"></a>Zapobieganie utracie danych

- Zaktualizowano artykuły dotyczące dołączania urządzenia macOS:
  - [Dowiedz się więcej o programie DLP punktu końcowego](endpoint-dlp-learn-about.md)
  - [Konfigurowanie ustawień ochrony przed utratą danych punktu końcowego](dlp-configure-endpoint-settings.md)
  - [Planowanie zapobiegania utracie danych (DLP)](dlp-overview-plan-for-dlp.md)
  - [Dokumentacja zasad ochrony przed utratą danych](dlp-policy-reference.md)
  - [Wprowadzenie do ochrony przed utratą danych punktu końcowego](endpoint-dlp-getting-started.md)
- [Warunki zasad DLP, wyjątki i akcje](dlp-conditions-and-exceptions.md) — dodano wskazówki dotyczące modyfikowania akcji podmiotu.
- [Dokumentacja zasad ochrony przed utratą danych](dlp-policy-reference.md) — predykaty GA SPO/ODB; zaktualizowano o nowe wskazówki dotyczące przetwarzania reguł w punktach końcowych.

### <a name="device-onboarding"></a>Dołączanie urządzenia

- Zaktualizowano artykuły dotyczące dołączania urządzenia macOS:
  - [Dołączanie urządzeń macOS do Microsoft 365 — omówienie](device-onboarding-macos-overview.md)
  - [Dołączanie i odłączanie urządzeń z systemem macOS do rozwiązań zgodności przy użyciu usługi Microsoft Intune dla klientów usługi Ochrony punktu końcowego w usłudze Microsoft Defender](device-onboarding-offboarding-macos-intune-mde.md)
  - [Dołączanie i odłączanie urządzeń macOS do rozwiązań Microsoft Purview przy użyciu Intune](device-onboarding-offboarding-macos-intune.md)
  - [Dołączanie i odłączanie urządzeń z systemem macOS do rozwiązań zgodności przy użyciu narzędzia JAMF Pro dla klientów usługi Ochrony punktu końcowego w usłudze Microsoft Defender](device-onboarding-offboarding-macos-jamfpro-mde.md)
  - [Dołączanie i odłączanie urządzeń macOS do rozwiązań Microsoft Purview przy użyciu Pro JAMF](device-onboarding-offboarding-macos-jamfpro.md)

### <a name="information-barriers"></a>Bariery informacyjne

- [Korzystanie z barier informacyjnych w SharePoint](/sharepoint/information-barriers) — dodano wskazówki dotyczące obsługi nowych kanałów prywatnych w SharePoint.
- [Zarządzanie zasadami barier informacyjnych](information-barriers-edit-segments-policies.md) — dodano wskazówki dotyczące usuwania segmentów i zasad/segmentów razem.

### <a name="microsoft-priva"></a>Microsoft Priva

- [Zasady zarządzania ryzykiem prywatności](/privacy/priva/risk-management) — nowe strony, istotne aktualizacje i restrukturyzacja zawartości zasad; szczegóły poniżej:
  - [Zasady zarządzania ryzykiem prywatności](/privacy/priva/risk-management-policies) — dodano istotne szczegóły dotyczące konfiguracji zasad i zarządzania nimi, które mają zastosowanie do wszystkich zasad; dodano linki do nowych stron dla każdego z trzech typów zasad.
  - [Zasady nadmiernej eksponowania danych](/privacy/priva/risk-management-policy-data-overexposure) — określa potrzeby i zastosowania zasad; Objaśnia ustawienia domyślne tworzenia po wyjętej wersji oraz szczegółowe instrukcje dotyczące dostosowywania ustawień.
  - [Zasady transferu danych](/privacy/priva/risk-management-policy-data-transfer) — wyróżnia nowy warunek dla zasad wykrywania transferów poza organizacją; wyraża potrzebę i zastosowania zasad; Objaśnia ustawienia domyślne tworzenia po wyjętej wersji oraz szczegółowe instrukcje dotyczące dostosowywania ustawień.
  - [Zasady minimalizacji danych](/privacy/priva/risk-management-policy-data-minimization) — określa potrzeby i zastosowania zasad; Objaśnia ustawienia domyślne tworzenia po wyjętej wersji oraz szczegółowe instrukcje dotyczące dostosowywania ustawień.
  - [Badanie i korygowanie alertów](/privacy/priva/risk-management-alerts) — dodano objaśnienie szczegółów i formatowanie zmian w celu zwiększenia czytelności.
  - [Powiadomienia użytkowników](/privacy/priva/risk-management-notifications) — dodano informacje na temat funkcji wyświetlania podglądu i dostosowywania zawartości powiadomień e-mail.
- [Utwórz żądanie praw podmiotu](/privacy/priva/subject-rights-requests-create) — dodano sekcję dotyczącą rozpoczynania pracy z pierwszym żądaniem z ustawieniami domyślnymi w celu eksplorowania funkcji.
- [Przejrzyj dane dotyczące żądania praw podmiotu](/privacy/priva/subject-rights-requests-data-review) — dodano szczegóły wyjaśniające elementy priorytetu do przeglądu i sposoby ich znajdowania oraz potrzebę skonfigurowania dopasowywania danych w celu uzyskania tej analizy.
- [Znajdowanie i wizualizowanie danych osobowych](/privacy/priva/priva-data-profile) — wyjaśniono, że użytkownicy muszą skonfigurować dopasowywanie danych w celu uzyskania szczegółowych informacji o elementach z największą zawartością podmiotu danych w obszarze "Kluczowe szczegółowe informacje".
- [Dopasowywanie danych dla żądań praw podmiotu](/privacy/priva/subject-rights-requests-data-match) — wyjaśniono postęp kroku w tym procesie i dodano drugi krok tworzenia typów informacji poufnych.

### <a name="sensitive-information-types"></a>Typy informacji poufnych

- [Użyj nazwanych jednostek w zasadach DLP](named-entities-use.md) — jednostek o nazwie GA.
- [Dowiedz się więcej o nazwanych jednostkach](named-entities-learn.md) — jednostkach o nazwie GA.
- [Informacje poufne typy definicji jednostek](sensitive-information-type-entity-definitions.md) — jednostki nazwane ogólnej dostępności i aktualizacje wzorca.
- [Dowiedz się więcej o typach informacji poufnych](sensitive-information-type-learn-about.md) — jednostki o nazwie GA.

### <a name="sensitivity-labels"></a>Etykiety wrażliwości

- Nowo obsługiwany scenariusz dla witryn SharePoint, teraz w wersji zapoznawczej: [Konfigurowanie uprawnień do udostępniania witryn przy użyciu ustawień zaawansowanych programu PowerShell](sensitivity-labels-teams-groups-sites.md#configure-site-sharing-permissions-by-using-powershell-advanced-settings)
- [Współtworzenie plików zaszyfrowanych przy użyciu etykiet poufności](sensitivity-labels-coauthoring.md) jest teraz dostępne do testowania za pomocą kanału Semi-Annual Enterprise Channel (wersja zapoznawcza).
- Usunięte OneDrive konta są teraz poprawnie wyświetlane w wynikach symulacji dla zasad automatycznego etykietowania.
- Znany problem podczas [przypisywania uprawnień do kontaktów poczty e-mail w grupach](/office365/troubleshoot/sensitivity-labels/mail-contacts-lose-access-encrypted-content) podczas konfigurowania etykiety poufności na potrzeby szyfrowania.

### <a name="changes-to-product-names"></a>Zmiany nazw produktów

Aby sprostać wyzwaniom współczesnego zdecentralizowanego, bogatego w dane miejsca pracy, wprowadzamy [Microsoft Purview](https://aka.ms/microsoftpurview), kompleksowy zestaw rozwiązań, które ułatwiają zrozumienie, zarządzanie i ochronę całego majątku danych. Ta nowa rodzina marek łączy możliwości dawnej Microsoft Purview Data Map i portfolio zgodności Microsoft 365, na których klienci już polegają, zapewniając ujednolicone zarządzanie danymi i zarządzanie ryzykiem dla Twojej organizacji.

| **Poprzednie imię i nazwisko** | **Nowa nazwa** | **Opis** |
|:----------------|:-------------|:----------------|
| zaawansowany inspekcja Microsoft 365 <br><br> Microsoft 365 Inspekcja podstawowa | inspekcja Microsoft Purview (Premium) <br><br> inspekcja Microsoft Purview (standardowa)| Rozwiązania do inspekcji zapewniają zintegrowane rozwiązanie ułatwiające organizacjom skuteczne reagowanie na zdarzenia związane z bezpieczeństwem, badania kryminalistyczne, dochodzenia wewnętrzne i obowiązki w zakresie zgodności. Aby dowiedzieć się więcej, zobacz [Microsoft Purview Advanced Audit (Premium)](advanced-audit.md) i [Microsoft Purview Advanced Audit (Standard)](set-up-basic-audit.md). |
| zgodność z komunikacją Microsoft 365 | Zgodność w komunikacji w usłudze Microsoft Purview | Zgodność z komunikacją pomaga zminimalizować ryzyko, pomagając szybko wykrywać, przechwytywać i podejmować akcje korygowania dla kanałów komunikacyjnych firmy i naruszeń zasad. Aby dowiedzieć się więcej, zobacz [Zgodność w komunikacji w Microsoft Purview](communication-compliance-solution-overview.md). |
| Microsoft Compliance Manager | Menedżer zgodności Microsoft Purview | Menedżer zgodności może pomóc w całym procesie zapewniania zgodności, od tworzenia spisu zagrożeń związanych z ochroną danych po zarządzanie złożonością wdrażania mechanizmów kontroli, zachowanie aktualności z przepisami i certyfikatami oraz raportowanie do audytorów. Aby dowiedzieć się więcej, zobacz [Microsoft Purview Compliance Manager](compliance-manager.md). |
| klucz klienta Microsoft 365 | klucz klienta Microsoft Purview | Klucz klienta zapewnia dodatkową ochronę przed wyświetlaniem danych przez nieautoryzowane systemy lub personel oraz uzupełnia szyfrowanie dysków BitLocker w centrach danych firmy Microsoft. Aby dowiedzieć się więcej, zobacz [Microsoft Purview Klucz klienta](customer-key-overview.md). |
| Office 365 skrytka klienta | Microsoft Purview skrytka klienta | Skrytka klienta zapewnia, że firma Microsoft nie może uzyskać dostępu do Zawartości w celu wykonywania operacji usług bez twojej jawnej zgody. Skrytka klienta umożliwia przejście do procesu przepływu pracy zatwierdzania używanego przez firmę Microsoft w celu zapewnienia, że tylko autoryzowane żądania zezwalają na dostęp do zawartości. Aby dowiedzieć się więcej, zobacz [Microsoft Purview Skrytka klienta](customer-lockbox-requests.md). |
| Zapobieganie utracie danych | Ochrona przed utratą danych w Microsoft Purview | DLP pomaga chronić poufne dane i zmniejszać ryzyko, uniemożliwiając użytkownikom niewłaściwe udostępnianie tych danych osobom, które nie powinny ich mieć. Aby dowiedzieć się więcej, zobacz [Ochrona przed utratą danych w Microsoft Purview](dlp-learn-about-dlp.md). |
| Szyfrowanie podwójnym kluczem dla Microsoft 365 | szyfrowanie podwójnego klucza Microsoft Purview | Szyfrowanie podwójnym kluczem (DKE) używa dwóch kluczy razem w celu uzyskania dostępu do chronionej zawartości. Firma Microsoft przechowuje jeden klucz w Microsoft Azure, a drugi klucz. Aby dowiedzieć się więcej, zobacz [Microsoft Purview Szyfrowanie podwójnym kluczem](double-key-encryption.md) |
| bariery informacyjne Microsoft 365 | Bariery informacyjne w usłudze Microsoft Purview | Bariery informacyjne to rozwiązanie, które ogranicza komunikację i współpracę między niektórymi osobami w organizacji w celu ochrony informacji wewnętrznych. Aby dowiedzieć się więcej, zobacz [Microsoft Purview Bariery informacyjne](information-barriers-solution-overview.md). |
| Microsoft Information Protection | Microsoft Purview Information Protection | Ochrona informacji pomaga odnajdywać, klasyfikować i chronić poufne informacje wszędzie tam, gdzie się znajdują lub podróżują. Aby dowiedzieć się więcej, zobacz [Microsoft Purview Information Protection](information-protection.md). |
| Zarządzanie informacjami firmy Microsoft | zarządzanie cyklem życia danych Microsoft Purview | Zarządzanie cyklem życia danych zapewnia narzędzia i możliwości przechowywania zawartości potrzebnej do przechowywania i usuwania zawartości, której nie używasz. Aby dowiedzieć się więcej, zobacz [zarządzanie cyklem życia danych Microsoft Purview](data-lifecycle-management.md). |
| Microsoft 365 Insider Risk Management | Zarządzanie ryzykiem wewnętrznym usługi Microsoft Purview | Zarządzanie ryzykiem wewnętrznym korzysta z pełnego zakresu wskaźników usług i innych firm, aby ułatwić szybkie identyfikowanie, klasyfikowanie i działanie na ryzykownych działaniach użytkowników. Aby dowiedzieć się więcej, zobacz [Zarządzanie ryzykiem wewnętrznym w Microsoft Purview](insider-risk-management.md). |
| szyfrowanie komunikatów Office 365 | Szyfrowanie wiadomości w Microsoft Purview | Szyfrowanie komunikatów umożliwia organizacji wysyłanie i odbieranie zaszyfrowanych wiadomości e-mail między osobami w organizacji i poza nią. Aby dowiedzieć się więcej, zobacz [Szyfrowanie wiadomości w Microsoft Purview](ome.md). |
| Zarządzanie dostępem uprzywilejowanym w Microsoft 365 | Zarządzanie uprzywilejowanym dostępem w usłudze Microsoft Purview | Usługa Privileged Access Management pomaga chronić organizację przed naruszeniami zabezpieczeń i pomaga spełnić najlepsze rozwiązania w zakresie zgodności, ograniczając stały dostęp do poufnych danych lub dostęp do krytycznych ustawień konfiguracji. Aby dowiedzieć się więcej, zobacz [Microsoft Purview Privileged Access Management( Zarządzanie dostępem uprzywilejowanym](privileged-access-management-solution-overview.md)). |
| Łączniki danych firmy Microsoft | łączniki danych Microsoft Purview | Microsoft 365 umożliwia administratorom używanie łączników danych do importowania i archiwizowania danych innych firm z platform mediów społecznościowych, platform wiadomości błyskawicznych i platform współpracy dokumentów do skrzynek pocztowych w organizacji Microsoft 365. Aby dowiedzieć się więcej, zobacz [Microsoft Purview łączniki danych](compliance-extensibility.md). |
| Microsoft 365 Advanced eDiscovery <br><br> Microsoft 365 Core eDiscovery | Zbieranie elektronicznych materiałów dowodowych w usłudze Microsoft Purview (warstwa Premium) <br><br> Zbieranie elektronicznych materiałów dowodowych w usłudze Microsoft Purview (warstwa standardowa) | Odnajdywanie elektroniczne to proces identyfikowania i dostarczania informacji elektronicznych, które mogą być wykorzystane jako dowód w sprawach prawnych. Aby dowiedzieć się więcej, zobacz [Microsoft Purview eDiscovery (Premium)](overview-ediscovery-20.md) i [Microsoft Purview eDiscovery (Standard)](get-started-core-ediscovery.md). |
| Centrum zgodności platformy Microsoft 365 | Portal zgodności platformy Microsoft Purview | Administracja portal, aby uzyskać dostęp do rozwiązań i wykazu rozwiązań w ramach pakietu Zgodność platformy Microsoft 365 E5. Aby dowiedzieć się więcej, zobacz [portal zgodności Microsoft Purview](microsoft-365-compliance-center.md). |

## <a name="march-2022"></a>Marzec 2022 r.

### <a name="communication-compliance"></a>Zgodność w komunikacji

- [Badanie i korygowanie alertów zgodności komunikacji](communication-compliance-investigate-remediate.md) — usunięto wskazówki dotyczące przestarzałego widoku adnotacji.

### <a name="compliance-manager"></a>Menedżer zgodności

- [Praca z akcjami poprawy](compliance-manager-improvement-actions.md) Wprowadzenie [z Menedżerem zgodności](compliance-manager-setup.md) — dodano informacje o większej ilości akcji ulepszania, które można automatycznie monitorować i testować ("ciągła ocena zgodności"),co obejmuje nowe możliwości nadrzędnego stanu testowania akcji względem innego działania.

### <a name="data-classification"></a>Klasyfikacja danych

- [Wprowadzenie z Eksploratorem zawartości](data-classification-content-explorer.md) — Teams dodano wskazówki, sekcja licencjonowania wskazywała na opisy usług.

### <a name="data-lifecycle-management-and-records-management"></a>Zarządzanie cyklem życia danych i zarządzanie rekordami

- [Zasady przechowywania dla Yammer](create-retention-policies.md#retention-policy-for-yammer-locations) są teraz ogólnie dostępne.
- Obsługa kanałów udostępnionych, obecnie w wersji zapoznawczej. Podczas konfigurowania zasad przechowywania dla lokalizacji komunikatów kanału Teams wszystkie kanały udostępnione dziedziczą ustawienia przechowywania po swoim zespole nadrzędnym.
- [Limity dla dzierżawy dotyczące rozporządzania zawartością](retention-limits.md#maximum-number-of-items-for-disposition).

### <a name="data-loss-prevention"></a>Zapobieganie utracie danych

- [Zapobieganie utracie danych i Microsoft Teams](dlp-microsoft-teams.md) — publiczna wersja zapoznawcza zawartości Udostępnianie kanałów Teams.
- [Wprowadzenie z rozszerzeniem zgodności firmy Microsoft](dlp-chrome-get-started.md) — publiczna wersja zapoznawcza ograniczonych grup aplikacji, usuń instrukcje dotyczące klucza rejestru, konfiguracja jest teraz domyślnie włączona.
- [Konfigurowanie ustawień ochrony przed utratą danych punktu końcowego](dlp-configure-endpoint-settings.md) — nowość dla publicznej wersji zapoznawczej grup aplikacji z ograniczeniami.
- [Dokumentacja zasad ochrony przed utratą danych](dlp-policy-reference.md) — zaktualizowana pod kątem publicznej wersji zapoznawczej ograniczonych grup aplikacji.
- [Wprowadzenie z zapobieganiem utracie danych dla Power BI](dlp-powerbi-get-started.md) — nowość dla publicznej wersji zapoznawczej.
- 
### <a name="information-protection"></a>Ochrona informacji

- [Obsługa informacji o wersji zestawu znaków dwu bajtowych](mip-dbcs-relnotes.md) — dodano wskazówki dotyczące macOS.
- 
### <a name="insider-risk-management"></a>Zarządzanie ryzykiem wewnętrznym

- [Wprowadzenie z zarządzaniem ryzykiem wewnętrznym](insider-risk-management-configure.md) — dodano nowe zadania w celu uzyskania wskazówek dotyczących zalecanych akcji.
- [Wprowadzenie z ustawieniami zarządzania ryzykiem wewnętrznym](insider-risk-management-settings.md) — nowe aktualizacje funkcji powiadomień i alertów e-mail, nowe aktualizacje powiadomień analitycznych.

### <a name="microsoft-priva"></a>Microsoft Priva

- [Konfigurowanie ustawień Priva](/privacy/priva/priva-settings) — zaktualizowano objaśnienie informacji o okresach przechowywania danych dla żądań praw podmiotu; dodano szczegóły dotyczące zarządzania tagami przeglądu danych i stosowania ich dla żądań praw podmiotu.
- [Utwórz żądanie praw podmiotu](/privacy/priva/subject-rights-requests-create) — dodano szczegóły dotyczące uściślania wyszukiwań oraz wybierania warunków i atrybutów; dodano informacje o nowych funkcjach, które umożliwiają użytkownikom wybieranie wszystkich wersji SharePoint elementów w wyszukiwaniu (w porównaniu z ustawieniem domyślnym, które zwraca tylko bieżącą wersję elementów SharePoint).
- [Przejrzyj dane dotyczące żądania praw podmiotu](/privacy/priva/subject-rights-requests-data-review) — dodano szczegóły w kroku 3 dotyczące przeglądania elementów na etapie przeglądu danych, w tym oznaczanie plików jako dołączanych/wykluczających, dodawanie adnotacji do stosowania redakcji, stosowanie tagów i wprowadzanie notatek.
- [Generowanie raportów i wypełnianie żądania praw podmiotu](/privacy/priva/subject-rights-requests-reports) — dodano szczegółowe informacje o sposobie zrozumienia raportów; wyjaśnić, kiedy jest generowany pakiet eksportu i jak pracować z jego zawartością; dodano informacje o dziennikach inspekcji, raportach o tagach plików i okresach przechowywania danych i raportów SRR.

### <a name="sensitivity-labels"></a>Etykiety wrażliwości

- [Etykiety poufności dla Teams](sensitivity-labels-teams-groups-sites.md):
  - Obsługa kanałów udostępnionych, obecnie w wersji zapoznawczej. Jeśli zespół ma jakiekolwiek kanały udostępnione, automatycznie dziedziczy ustawienia etykiet poufności po swoim zespole nadrzędnym, a etykiety nie można usunąć ani zastąpić inną etykietą.
  - Obsługa szablonów wymienionych wcześniej jako [nieobsługiwane w przypadku interfejsów API Teams Graph i poleceń cmdlet programu PowerShell]( /microsoftteams/sensitivity-labels#limitations).  
- W przypadku inspekcji programu Word, Excel i PowerPoint w sieci Web tekst uzasadnienia jest teraz w pełni wdrażany.
- Stosowanie etykiety domyślnej do istniejących dokumentów programu Word, Excel i PowerPoint w sieci Web jest teraz w pełni wdrażane.

## <a name="february-2022"></a>Luty 2022 r.

### <a name="ediscovery"></a>Zbierania elektronicznych materiałów dowodowych

- [Zarządzaj szablonami komunikacji opiekuna w usłudze eDiscovery (Premium)](advanced-ediscovery-communications-library.md) — menedżerowie zbierania elektronicznych materiałów dowodowych mogą teraz tworzyć szablony komunikacji opiekuna, które mogą być używane w dowolnym przypadku zbierania elektronicznych materiałów dowodowych (Premium) w organizacji.
- [Zarządzanie urzędnikami wystawiającym certyfikaty w usłudze eDiscovery (Premium)](advanced-ediscovery-issuing-officers.md) — menedżerowie zbierania elektronicznych materiałów dowodowych mogą dodać listę urzędników wystawiających, których można przypisać do komunikacji opiekuna w każdym przypadku zbierania elektronicznych materiałów dowodowych (Premium) w organizacji.

### <a name="data-lifecycle-management-and-records-management"></a>Zarządzanie cyklem życia danych i zarządzanie rekordami

- [Zakresy adaptacyjne](retention.md#adaptive-or-static-policy-scopes-for-retention) zasad przechowywania i zasad etykiet przechowywania są teraz ogólnie dostępne(GA). Instrukcje [dotyczące konfigurowania zakresu adaptacyjnego](retention-settings.md#to-configure-an-adaptive-scope) zawierają teraz więcej informacji na temat SharePoint zakresów witryn: dokumentacja wpisu w blogu dotycząca używania właściwości witryny niestandardowej i sposobu używania właściwości witryny SiteTemplate do dołączania lub wykluczania określonych typów witryn za pomocą zaawansowanego konstruktora zapytań.
- [Wyszukiwanie zasad](retention.md#policy-lookup) w rozwiązaniu do zarządzania cyklem życia danych jest teraz ogólnie dostępne (ogólna dostępność).
- Program PowerShell jest alternatywą dla ustawienia zarządzania rekordami, które umożliwia użytkownikom usuwanie elementów oznaczonych etykietami w SharePoint i OneDrive przy użyciu funkcji AllowFilesWithKeepLabelToBeDeletedSPO i AllowFilesWithKeepLabelToBeDeletedODB z [get-PnPTenant](/powershell/module/sharepoint-pnp/get-pnptenant) i [Set-PnPTenant]( /powershell/module/sharepoint-pnp/set-pnptenant).

### <a name="sensitivity-labels"></a>Etykiety wrażliwości

- Nowe wskazówki [Dlaczego wybierasz wbudowane etykietowanie w dodatku AIP dla aplikacji Office](sensitivity-labels-aip.md), jeśli używasz klienta ujednoliconego etykietowania usługi Azure Information Protection (AIP) dla Windows komputerów. Ta strona zawiera informacje o nowej prywatnej wersji zapoznawczej dla aplikacji Office.
- Nowe ustawienia [zasad automatycznego etykietowania](apply-sensitivity-label-automatically.md#how-to-configure-auto-labeling-policies-for-sharepoint-onedrive-and-exchange):
  - Dodatkowe ustawienia poczty e-mail do obsługi zawsze stosowania dopasowanej etykiety poufności oraz stosowania szyfrowania do wiadomości e-mail odebranych spoza organizacji.
  - Wykluczenia dla określonych wystąpień (użytkowników, grup, witryn) są obsługiwane przy użyciu nowej opcji **Wykluczone** , gdy domyślny wybór opcji **Wszystkie** jest określony dla **opcji Uwzględnione**.
- Teraz w wersji zapoznawczej: Urządzenia przenośne (iOS i Android) obsługują [współtworzenie](sensitivity-labels-coauthoring.md), gdy masz minimalną wersję i zdecydujesz się na tę wersję zapoznawczą.
- Obsługa ustawiania domyślnego typu łącza udostępniania jest rozszerzona na poszczególne dokumenty w SharePoint i OneDrive. Aby uzyskać więcej informacji, zobacz nowy artykuł [Używanie etykiet poufności do konfigurowania domyślnego typu linku udostępniania witryn i dokumentów w SharePoint i OneDrive]( sensitivity-labels-default-sharing-link.md).
- Teams centrum administracyjne obsługuje teraz etykiety kontenerów (etykiety poufności z zakresem grup & lokacji).

## <a name="january-2022"></a>Styczeń 2022

### <a name="microsoft-purview-data-lifecycle-management"></a>zarządzanie cyklem życia danych Microsoft Purview

- Dokumentacja poprzedniego zarządzania informacjami firmy Microsoft została znacząco poprawiona i zrestrukturyzowana, aby ułatwić znajdowanie informacji dotyczących rozwiązań skonfigurowanych w portal zgodności Microsoft Purview: łączniki danych, zarządzanie cyklem życia danych i zarządzanie rekordami. W ramach tej poprawki dokumentacja zawiera wyraźniejsze rozróżnienie scenariuszy przechowywania zarządzania cyklem życia danych a zarządzania rekordami.
- [Dowiedz się więcej o zarządzaniu cyklem życia danych](data-lifecycle-management.md) — nowość, aby obsługiwać restrukturyzację.
- [Wprowadzenie z zarządzaniem cyklem życia danych](get-started-with-data-lifecycle-management.md) — nowe, aby zastąpić "Wprowadzenie przechowywaniem", ten artykuł zawiera kroki wprowadzające dla wszystkich możliwości zarządzania cyklem życia danych, które obejmują przechowywanie.
- [Utwórz etykiety przechowywania dla wyjątków od zasad przechowywania](create-retention-labels-data-lifecycle-management.md) — nowy, zidentyfikowany scenariusz używania etykiet przechowywania do zarządzania cyklem życia danych, a nie zarządzania rekordami.
- [Dowiedz się więcej o archiwalnych skrzynkach pocztowych](archive-mailboxes.md) — nowość, aby obsługiwać restrukturyzację, zawiera informacje koncepcyjne, które były wcześniej zawarte w artykule "Włączanie archiwalnych skrzynek pocztowych".

### <a name="microsoft-priva"></a>Microsoft Priva

- [Zarządzanie prywatnością jest teraz Microsoft Priva](/privacy/priva/priva-overview) — zaktualizowane w celu zmiany marki produktu i jego rozwiązań, zarządzanie ryzykiem prywatności Priva i żądania praw podmiotów Priva.

### <a name="sensitivity-labels"></a>Etykiety wrażliwości

- Obsługa nowych [grup ról i ról](get-started-with-sensitivity-labels.md#permissions-required-to-create-and-manage-sensitivity-labels) w wersji zapoznawczej.
- Nowe [możliwości monitorowania](apply-sensitivity-label-automatically.md#monitoring-your-auto-labeling-policy) zasad automatycznego etykietowania.
- Teraz wprowadzanie: etykieta domyślna dla istniejących dokumentów i tekst uzasadnienia dla Office w sieci Web.
- Ogłoszono dla kanału Semi-Annual Enterprise lipca w wersji 2202+: Współtworzenie i inspekcja dla Outlook.

## <a name="december-2021"></a>Grudzień 2021

### <a name="compliance-and-service-assurance"></a>Zgodność i gwarancja usługi

- [Azure, Dynamics 365 i Windows powiadomienie o naruszeniu przepisów RODO](/compliance/regulatory/gdpr-breach-notification) — zaktualizowane w celu wyjaśnienia, że klienci nie muszą korzystać z usługi płatnej, takiej jak Defender dla Chmury, w celu otrzymywania powiadomień dotyczących zabezpieczeń i prywatności

### <a name="ediscovery"></a>Zbierania elektronicznych materiałów dowodowych

- [Przepływ pracy zbierania elektronicznych materiałów dowodowych (Premium) dla zawartości w Microsoft Teams](teams-workflow-in-advanced-ediscovery.md#reference-guide) — zaktualizowany o nowy przewodnik szybkiego odwołania do pobrania do zarządzania zawartością Teams w środowisku zbierania elektronicznych materiałów dowodowych (Premium)

### <a name="data-lifecycle-management"></a>Zarządzanie cyklem życia danych

- [Włączanie archiwalnych skrzynek pocztowych w centrum zgodności](enable-archive-mailboxes.md#run-diagnostics-on-archive-mailboxes) — dodano sekcję dotyczącą nowego narzędzia diagnostycznego dla archiwalnych skrzynek pocztowych
- [Importowanie plików PST organizacji do Microsoft 365 przy użyciu przekazywania sieci](use-network-upload-to-import-pst-files.md#step-2-upload-your-pst-files-to-microsoft-365) — importowanie PST obsługuje teraz narzędzie AzCopy w wersji 10
- [Przywracanie nieaktywnej skrzynki pocztowej](restore-an-inactive-mailbox.md) — poprawiona procedura przywracania nieaktywnej skrzynki pocztowej przez dodanie nazwy LegacyExchangeDN nieaktywnej skrzynki pocztowej do docelowej skrzynki pocztowej

### <a name="information-protection"></a>Ochrona informacji

- [Wdrażanie rozwiązania do ochrony informacji za pomocą Microsoft Purview](information-protection-solution.md) — nowe wskazówki krok po kroku dla klientów poszukujących opisowego planu wdrażania Microsoft Purview Information Protection

### <a name="retention-and-records-management"></a>Zarządzanie przechowywaniem i rekordami

- Nowe wskazówki dotyczące czasu obowiązywania [zasad przechowywania](create-retention-policies.md#how-long-it-takes-for-retention-policies-to-take-effect)
- Wprowadzanie nowych ustawień dzierżawy: ustawienie zarządzania rekordami, które uniemożliwia edytowanie właściwości dla oznaczonych SharePoint elementów oznaczonych jako rekord i zablokowane, oraz inne ustawienie uniemożliwiające użytkownikom odblokowywanie elementów oznaczonych jako rekord

### <a name="sensitivity-labels"></a>Etykiety wrażliwości

- Obowiązkowe etykietowanie i etykieta domyślna dla Power BI są teraz ogólnie dostępne (GA)

## <a name="november-2021"></a>Listopad 2021

### <a name="compliance-manager"></a>Menedżer zgodności

Nowe aktualizacje zawartości można wyświetlić w temacie [Co nowego w programie Microsoft Purview Compliance Manager](compliance-manager-whats-new.md).

### <a name="device-onboarding"></a>Dołączanie urządzenia

Dodano następujące artykuły dotyczące dołączania urządzeń:

- [Omówienie dołączania urządzeń z systemem macOS do platformy Microsoft 365 (wersja zapoznawcza)](device-onboarding-macos-overview.md)
- [Dołączanie i odłączanie urządzeń macOS do rozwiązań Microsoft Purview przy użyciu Intune (wersja zapoznawcza)](device-onboarding-offboarding-macos-intune.md)
- [Dołączanie i odłączanie urządzeń z systemem macOS do rozwiązań zgodności przy użyciu usługi Intune dla klientów usługi Ochrony punktu końcowego w usłudze Microsoft Defender (wersja zapoznawcza)](device-onboarding-offboarding-macos-intune-mde.md)
- [Dołączanie i odłączanie urządzeń macOS do rozwiązań Microsoft Purview przy użyciu Pro JAMF (wersja zapoznawcza)](device-onboarding-offboarding-macos-jamfpro.md)
- [Dołączanie i odłączanie urządzeń z systemem macOS do rozwiązań zgodności przy użyciu narzędzia JAMF Pro dla klientów usługi Ochrony punktu końcowego w usłudze Microsoft Defender (wersja zapoznawcza)](device-onboarding-offboarding-macos-jamfpro-mde.md)

### <a name="ediscovery"></a>Zbierania elektronicznych materiałów dowodowych

- [Użyj nowego formatu przypadku w nowym formacie zbierania elektronicznych materiałów dowodowych (Premium)](advanced-ediscovery-new-case-format.md) nowy format sprawy został wydany do ogólnej dostępności i zmieniono nazwę z "formatu dużych przypadków"

### <a name="retention-and-records-management"></a>Zarządzanie przechowywaniem i rekordami
- Wdrażanie: nowe ustawienia zarządzania rekordami, które kontrolują, czy elementy oznaczone etykietami w SharePoint i OneDrive mogą zostać usunięte przez użytkowników. Wcześniej etykiety przechowywania skonfigurowane do przechowywania zawartości, które nie oznaczyły elementów jako rekordów, uniemożliwiały użytkownikom usuwanie zawartości oznaczonej etykietami w SharePoint, gdy ta akcja była dozwolona w OneDrive. Aby uzyskać więcej informacji, zobacz [Jak działa przechowywanie SharePoint i OneDrive](retention-policies-sharepoint.md#how-retention-works-for-sharepoint-and-onedrive).

### <a name="sensitive-information-types"></a>Typy informacji poufnych

Dodano następujące nowe artykuły:

- [Dowiedz się więcej o dokładnych typach informacji poufnych opartych na dopasowaniu danych](sit-learn-about-exact-data-match-based-sits.md)
- [Wprowadzenie do dokładnych typów informacji poufnych opartych na dopasowaniu danych](sit-get-started-exact-data-match-based-sits-overview.md)
- [Eksportuj dane źródłowe dla dokładnego typu informacji poufnych opartych na dopasowaniu danych](sit-get-started-exact-data-match-export-data.md)
- [Twórz schemat dla dokładnych typów informacji poufnych opartych na dopasowaniu danych](sit-get-started-exact-data-match-create-schema.md)
- [Utwórz skrót i przekaż tabelę źródła informacji poufnych dla dokładnych typów informacji poufnych opartych na dopasowaniu danych ](sit-get-started-exact-data-match-hash-upload.md)
- [Twórz dokładny typ/pakiet reguł informacji poufnych opartych na dopasowaniu danych](sit-get-started-exact-data-match-create-rule-package.md)
- [Testuj dokładny typ informacji poufnych oparty na dopasowaniu danych](sit-get-started-exact-data-match-test.md)
- [Zarządzaj schematem dokładnego dopasowania danych](sit-use-exact-data-manage-schema.md)
- [Odśwież plik tabeli źródła informacji poufnych](sit-use-exact-data-refresh-data.md)

### <a name="sensitivity-labels"></a>Etykiety wrażliwości
- Nazwa zakresu [etykiet Microsoft Purview Data Map](/azure/purview/create-sensitivity-label) to teraz "Schematyzowane zasoby danych".
