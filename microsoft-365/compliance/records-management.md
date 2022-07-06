---
title: Dowiedz się więcej o Zarządzanie rekordami w Microsoft Purview
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- m365initiative-compliance
search.appverid:
- MOE150
- MET150
ms.custom:
- admindeeplinkCOMPLIANCE
- seo-marvel-apr2020
- seo-marvel-jun2020
description: Dowiedz się, jak Zarządzanie rekordami w Microsoft Purview obsługuje elementy o wysokiej wartości dla wymagań dotyczących prowadzenia dokumentacji biznesowej, prawnej lub regulacyjnej.
ms.openlocfilehash: 1a9d37f138647a36fb7440f15fd74851957b542f
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66642333"
---
# <a name="learn-about-records-management"></a>Dowiedz się więcej o zarządzaniu rekordami

>*[Wskazówki dotyczące licencjonowania platformy Microsoft 365 dotyczące zgodności & zabezpieczeń](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

> [!TIP]
> *Czy wiesz, że możesz bezpłatnie wypróbować wersje premium wszystkich dziewięciu rozwiązań Usługi Microsoft Purview?* Skorzystaj z 90-dniowej wersji próbnej rozwiązań Purview, aby dowiedzieć się, jak niezawodne możliwości usługi Purview mogą pomóc organizacji spełnić jej potrzeby w zakresie zgodności. Microsoft 365 E3 i Office 365 E3 klienci mogą rozpocząć pracę w [centrum portal zgodności Microsoft Purview prób](https://compliance.microsoft.com/trialHorizontalHub?sku=ComplianceE5&ref=DocsRef). Dowiedz się więcej o [tym, kto może zarejestrować się i zapoznać się z postanowieniami dotyczącymi wersji próbnej](compliance-easy-trials.md).

Organizacje wszystkich typów wymagają rozwiązania do zarządzania rekordami w celu zarządzania rekordami regulacyjnymi, prawnymi i biznesowymi w danych firmowych. Zarządzanie rekordami w usłudze Microsoft Purview pomaga organizacji zarządzać swoimi zobowiązaniami prawnymi, umożliwia demonstrowanie zgodności z przepisami i zwiększa wydajność przy regularnym rozporządzaniu elementami, które nie są już wymagane do przechowywania, nie mają już wartości lub nie są już wymagane do celów biznesowych.

Skorzystaj z następujących możliwości, aby obsługiwać rozwiązanie do zarządzania rekordami dla usług i aplikacji platformy Microsoft 365:

- **Etykieta zawartości jako rekordu**. Utwórz i skonfiguruj etykiety przechowywania, aby oznaczyć zawartość jako [rekord](#records) , który może być następnie stosowany przez użytkowników lub automatycznie stosowany przez identyfikowanie informacji poufnych, słów kluczowych lub typów zawartości.

- **Migrowanie wymagań dotyczących przechowywania i zarządzanie nimi za pomocą planu plików**. Korzystając z [planu plików](file-plan-manager.md), możesz wprowadzić istniejący plan przechowywania na platformie Microsoft 365 lub utworzyć nowy, aby zwiększyć możliwości zarządzania.

- **Skonfiguruj ustawienia przechowywania i usuwania przy użyciu etykiet przechowywania**. Skonfiguruj [etykiety przechowywania](retention.md#retention-labels) z okresami przechowywania i akcjami na podstawie różnych czynników, które obejmują datę ostatniej modyfikacji lub utworzenia.

- **Rozpocznij różne okresy przechowywania, gdy wystąpi zdarzenie** z [przechowywaniem opartym na zdarzeniach](event-driven-retention.md).

- **Przejrzyj i zweryfikuj dyspozycję** za pomocą [przeglądów dyspozycji](disposition.md#disposition-reviews) i weryfikacji [usunięcia rekordów](disposition.md#disposition-of-records).

- **Wyeksportuj informacje o wszystkich usuniętych elementach** z [opcją eksportu](disposition.md#filter-and-export-the-views).

- **Ustaw określone uprawnienia** dla funkcji menedżera rekordów w organizacji, aby [mieć odpowiedni dostęp](../security/office-365-security/permissions-in-the-security-and-compliance-center.md).

Korzystając z tych możliwości, możesz włączyć harmonogramy przechowywania i wymagania organizacji do rozwiązania do zarządzania rekordami, które zarządza przechowywaniem, deklaracją rekordów i dyspozycją, aby obsługiwać pełny cykl życia zawartości.

Oprócz dokumentacji online przydatne może być pobranie [talii z często zadawanymi pytaniami](https://aka.ms/MIPC/Blog-RecordsManagementWebinar) z seminarium internetowego zarządzania rekordami. Nagrywanie rzeczywistego seminarium internetowego nie jest już dostępne.

## <a name="records"></a>Rekordy

Gdy zawartość jest zadeklarowana jako rekord:

- Ograniczenia są nakładane na elementy pod względem tego, jakie [akcje są dozwolone lub blokowane](#compare-restrictions-for-what-actions-are-allowed-or-blocked).

- Rejestrowane są dodatkowe działania dotyczące elementu.

- Masz dowód dyspozycji, gdy elementy zostaną usunięte po zakończeniu okresu przechowywania.

Etykiety przechowywania są używane do [oznaczania](retention.md#retention-labels) zawartości jako **rekordu** lub **rekordu regulacyjnego**. Różnica między tymi dwoma elementami została wyjaśniona w następnej sekcji. Możesz opublikować te etykiety, aby użytkownicy i administratorzy mogli ręcznie zastosować je do zawartości lub automatycznie zastosować te etykiety do zawartości, którą chcesz oznaczyć jako rekord lub rekord regulacyjny.

Za pomocą etykiet przechowywania do deklarowania rekordów można zaimplementować pojedynczą i spójną strategię zarządzania rekordami w środowisku platformy Microsoft 365.

### <a name="compare-restrictions-for-what-actions-are-allowed-or-blocked"></a>Porównanie ograniczeń dotyczących dozwolonych lub zablokowanych akcji

Poniższa tabela służy do identyfikowania ograniczeń dotyczących zawartości w wyniku zastosowania standardowej etykiety przechowywania i etykiet przechowywania, które oznaczają zawartość jako rekord lub rekord regulacyjny.

Standardowa etykieta przechowywania ma ustawienia przechowywania i akcje, ale nie oznacza zawartości jako rekordu ani rekordu regulacyjnego.

> [!NOTE]
> Aby uzyskać kompletność, tabela zawiera kolumny dla zablokowanego i odblokowanego rekordu, który ma zastosowanie do programu SharePoint i usługi OneDrive, ale nie do programu Exchange. Możliwość blokowania i odblokowywania rekordu używa [przechowywania wersji rekordów](record-versioning.md) , które nie są obsługiwane w przypadku elementów programu Exchange. Dlatego w przypadku wszystkich elementów programu Exchange oznaczonych jako rekord zachowanie jest mapowane na kolumnę **Rekord — zablokowany** , a **kolumna Rekord — odblokowana** nie ma znaczenia.


|Akcja| Etykieta przechowywania |Rekord — zablokowany| Rekord — odblokowany| Dokumentacja regulacyjna |
|:-----|:-----|:-----|:-----|:-----|:-----|
|Edytowanie zawartości|Dozwolone | **Zablokowany** | Dozwolone | **Zablokowany**|
|Edytowanie właściwości, w tym zmienianie nazwy|Dozwolone |Dozwolone <sup>1</sup> | Dozwolone | **Zablokowany**|
|Usuń|Dozwolone <sup>2</sup> |**Zablokowany** |**Zablokowany**| **Zablokowany**|
|Kopii|Dozwolone |Dozwolone | Dozwolone| Dozwolone|
|Przenoszenie w kontenerze <sup>3</sup>|Dozwolone |Dozwolone | Dozwolone| Dozwolone|
|Przenoszenie kontenerów <sup>3</sup>|Dozwolone |Dozwolone, jeśli nigdy nie odblokowano | **Zablokowany** | **Zablokowany**|
|Otwieranie/odczytywanie|Dozwolone |Dozwolone | Dozwolone| Dozwolone|
|Zmienianie etykiety|Dozwolone |Dozwolone — tylko administrator kontenera | **Zablokowany**| **Zablokowany**
|Usuń etykietę|Dozwolone |Dozwolone — tylko administrator kontenera | **Zablokowany**| **Zablokowany**

Przypisy dolne:

<sup>1</sup> Edytowanie właściwości zablokowanego rekordu jest domyślnie dozwolone, ale może zostać zablokowane przez ustawienie dzierżawy w [ustawieniach zarządzania rekordami zarządzania](https://compliance.microsoft.com/) >  portal zgodności Microsoft Purview **Rejestrowane** ustawienia  > **zarządzania** >  rekordami **Etykiety** >  przechowywania **Zezwalaj na edytowanie właściwości rekordu**.

<sup>2</sup> Usuwanie elementów oznaczonych etykietami w programach SharePoint i OneDrive można zablokować jako ustawienie dzierżawy w **ustawieniach zarządzania rekordami** >  [zarządzania](https://compliance.microsoft.com/) >  portal zgodności Microsoft Purview **Records** Ustawienia  > **przechowywania Etykiety** >  przechowywania **Usuwanie elementów**.

Po zastosowaniu etykiety przechowywania do elementu listy zawierającego załącznik dokumentu ten dokument nie dziedziczy ustawień przechowywania i można go usunąć z elementu listy. Dla porównania, jeśli ten element listy został zadeklarowany jako rekord z etykietą przechowywania, załącznik dokumentu dziedziczy ustawienia przechowywania i nie można go usunąć.

<sup>3</sup> Kontenery obejmują biblioteki dokumentów programu SharePoint, konta usługi OneDrive i skrzynki pocztowe programu Exchange.

> [!IMPORTANT]
> Najważniejszą różnicą dla rekordu regulacyjnego jest to, że po zastosowaniu go do zawartości nikt, nawet administrator globalny, nie może usunąć etykiety.
>
> Etykiety przechowywania skonfigurowane dla rekordów regulacyjnych mają również następujące ograniczenia administratora:
>
> - Okres przechowywania nie może być krótszy po zapisaniu etykiety, tylko przedłużony.
> - Etykiety te nie są obsługiwane przez zasady automatycznego etykietowania i muszą być stosowane przy użyciu [zasad etykiet przechowywania](create-apply-retention-labels.md).
>
> Ponadto nie można zastosować etykiety regulacyjnej do dokumentu wyewidencjonowanego w programie SharePoint.
>
> Ze względu na ograniczenia i nieodwracalne akcje przed wybraniem tej opcji dla etykiet przechowywania upewnij się, że naprawdę musisz używać rekordów regulacyjnych. Aby zapobiec przypadkowej konfiguracji, ta opcja nie jest domyślnie dostępna, ale najpierw musi być włączona przy użyciu programu PowerShell. Instrukcje są zawarte w [temacie Deklarowanie rekordów przy użyciu etykiet przechowywania](declare-records.md).

## <a name="configuration-guidance"></a>Wskazówki dotyczące konfiguracji

Zobacz [Wprowadzenie do zarządzania rekordami](get-started-with-records-management.md). Ten artykuł zawiera informacje o subskrypcjach, uprawnieniach i łączach do kompleksowych wskazówek dotyczących konfiguracji scenariuszy zarządzania rekordami.
