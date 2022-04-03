---
title: Zarządzanie rekordami w Microsoft 365
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
description: Dzięki zarządzaniu rekordami Microsoft 365 harmonogramy przechowywania można stosować do planu ewidencji, który zarządza przechowywaniem, deklaracjami rekordów i ich rozsyłaniem.
ms.openlocfilehash: ce00fdfc6db90b9c65051a31e8768d6cd661072d
ms.sourcegitcommit: d32654bdfaf08de45715dd362a7d42199bdc1ee7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/23/2022
ms.locfileid: "63755684"
---
# <a name="learn-about-records-management-in-microsoft-365"></a>Informacje na temat zarządzania rekordami w Microsoft 365

>*[Microsoft 365 licencjonowania w zakresie zabezpieczeń & zgodności](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

Organizacje wszystkich typów wymagają rozwiązania do zarządzania rekordami w celu zarządzania rekordami regulowymi, prawnie i biznesowymi o krytycznym znaczeniu w danych firmowych. Zarządzanie rekordami w firmie Microsoft 365 ułatwia organizacji zarządzanie jej zobowiązaniami prawnymi, umożliwia przedstawianie zgodności z przepisami oraz zwiększenie wydajności dzięki regularnemu zsyłaniu elementów, które nie są już wymagane do zachowania, które nie są już potrzebne lub nie są już wymagane ze względu na działalność biznesową.

Skorzystaj z następujących funkcji w celu obsługi swojego rozwiązania do zarządzania rekordami w Microsoft 365:

- **Etykieta zawartości jako rekordu**. Tworzenie i konfigurowanie etykiet przechowywania w celu oznaczania zawartości [](#records) jako rekordu, który może być następnie stosowany przez użytkowników lub automatycznie stosowany przez identyfikowanie informacji poufnych, słów kluczowych lub typów zawartości.

- **Migrowanie wymagań przechowywania i zarządzanie nimi za pomocą planu plików**. Plan przechowywania [plików](file-plan-manager.md) umożliwia zastosowanie istniejącego planu przechowywania w celu Microsoft 365 lub tworzenie nowego, który zapewnia ulepszone funkcje zarządzania.

- **Konfigurowanie ustawień przechowywania i usuwania za pomocą etykiet przechowywania**. Skonfiguruj [etykiety przechowywania](retention.md#retention-labels) z okresami przechowywania i akcjami na podstawie różnych czynników, które zawierają datę ostatniej modyfikacji lub utworzenia.

- **Uruchamianie różnych okresów przechowywania w przypadku wystąpienia zdarzenia** z [przechowywaniem opartym na zdarzeniach](event-driven-retention.md).

- **Przejrzyj i sprawdź poprawność usuwania** [za pomocą recenzji usuwania](disposition.md#disposition-reviews) i [dowodu usunięcia rekordów](disposition.md#disposition-of-records).

- **Eksportowanie informacji o wszystkich usuniętych elementach** z [opcją eksportu](disposition.md#filter-and-export-the-views).

- **Ustaw określone uprawnienia dla** funkcji menedżera rekordów w organizacji, aby [mieć odpowiedni dostęp](../security/office-365-security/permissions-in-the-security-and-compliance-center.md).

Za pomocą tych funkcji można włączyć harmonogramy i wymagania przechowywania swojej organizacji do rozwiązania do zarządzania rekordami, które zarządza przechowywaniem, deklaracjami rekordów i ich rozsyłaniem, aby obsługiwać pełny cykl życia zawartości.

Oprócz dokumentacji online przydatne może być pobranie materiałów z często zadawanymi pytaniami [](https://aka.ms/MIPC/Blog-RecordsManagementWebinar) z seminarium w sieci Web dotyczącej zarządzania rekordami. Nagrywanie rzeczywistego seminarium w sieci Web nie jest już dostępne.

## <a name="records"></a>Rekordy

Jeśli zawartość jest deklarowana jako rekord:

- Na elementach obowiązują ograniczenia dotyczące dozwolonych lub [zablokowanych akcji](#compare-restrictions-for-what-actions-are-allowed-or-blocked).

- Rejestrowane są dodatkowe działania dotyczące elementu.

- Po usunięciu elementów po zakończeniu okresu przechowywania masz dowód usunięcia tych elementów.

Etykiet przechowywania [używa się do](retention.md#retention-labels) oznaczania zawartości jako **rekordu** lub **rekordu prawnego**. Różnice między tymi dwoma typami zostały wyjaśnione w następnej sekcji. Etykiety te można opublikować, aby użytkownicy i administratorzy mogą ręcznie zastosować je do zawartości, lub automatycznie zastosować te etykiety do zawartości, którą chcesz oznaczyć jako rekord lub rekord przepisów prawa.

Deklarowanie rekordów za pomocą etykiet przechowywania umożliwia wdrożenie jednej i spójnej strategii zarządzania rekordami w całym środowisku Microsoft 365 przechowywania.

### <a name="compare-restrictions-for-what-actions-are-allowed-or-blocked"></a>Porównywanie ograniczeń dotyczących dozwolonych lub zablokowanych akcji

Skorzystaj z poniższej tabeli, aby określić, jakie ograniczenia są nakładane na zawartość w wyniku zastosowania standardowej etykiety przechowywania, a etykiet przechowywania, które oznaczają zawartość jako rekord lub rekord przepisów prawa.

Standardowa etykieta przechowywania zawiera ustawienia i akcje przechowywania, ale nie oznacza zawartości jako rekordu ani rekordu prawnego.

> [!NOTE]
> W przypadku kompletności tabela zawiera kolumny zablokowanego i odblokowaowego rekordu, które mają zastosowanie SharePoint i OneDrive, ale nie Exchange. W celu zablokowania i odblokowania rekordu [](record-versioning.md) jest używane rejestrowanie wersji, które nie jest obsługiwane w przypadku Exchange elementów. Z tego względu Exchange elementów oznaczonych jako rekord zachowanie jest mapowane na kolumnę Rekord **—** zablokowana, a kolumna Rekord **—** odblokowana nie ma znaczenia.


|Akcja| Etykieta przechowywania |Nagrywanie — zablokowane| Nagrywanie — odblokowane| Rejestr przepisów prawa |
|:-----|:-----|:-----|:-----|:-----|:-----|
|Edytowanie zawartości|Dozwolone | **Zablokowane** | Dozwolone | **Zablokowane**|
|Edytowanie właściwości, w tym zmienianie nazwy|Dozwolone |Dozwolone <sup>1</sup> | Dozwolone | **Zablokowane**|
|Usuń|Dozwolone <sup>2</sup> |**Zablokowane** |**Zablokowane**| **Zablokowane**|
|Kopiuj|Dozwolone |Dozwolone | Dozwolone| Dozwolone|
|Poruszanie się w obrębie <sup>kontenera 3</sup>|Dozwolone |Dozwolone | Dozwolone| Dozwolone|
|Przechodzenie między kontenerami <sup>3</sup>|Dozwolone |Dozwolone, jeśli nigdy nie odblokowano | **Zablokowane** | **Zablokowane**|
|Otwieranie/odczytywanie|Dozwolone |Dozwolone | Dozwolone| Dozwolone|
|Zmień etykietę|Dozwolone |Dozwolone — tylko administrator kontenerów | **Zablokowane**| **Zablokowane**
|Usuń etykietę|Dozwolone |Dozwolone — tylko administrator kontenerów | **Zablokowane**| **Zablokowane**

Przypisy dolne:

<sup>1</sup> Edytowanie właściwości zablokowanego rekordu jest domyślnie dozwolone, ale może zostać zablokowane przez ustawienie dzierżawy w ustawieniach zarządzania [rekordami](https://compliance.microsoft.com/) w programie Centrum zgodności platformy Microsoft 365  > **RecordsUmianie** >  >  >  zarządzaniaWłaściwość etykietOchniż edytowanie właściwości rekordu **.**

<sup>2</sup> Usuwanie elementów oznaczonych etykietami w programach SharePoint i OneDrive można zablokować jako ustawienie dzierżawy w ustawieniach zarządzania [rekordami w](https://compliance.microsoft.com/) programie Centrum zgodności platformy Microsoft 365  > **RecordsUmianie** >  >  >  zarządzaniaRekordamiNalepki ponownego wczytania **elementów**.

Po zastosowaniu etykiety przechowywania do elementu listy, który ma załącznik dokumentu, ten dokument nie odziedziczy ustawień przechowywania i można go usunąć z tego elementu listy. Natomiast jeśli ten element listy został zadeklarowany jako rekord z etykietą przechowywania, załącznik dokumentu odziedziczy ustawienia przechowywania i nie będzie można go usunąć.

<sup>3 Kontenery</sup> obejmują SharePoint biblioteki dokumentów, OneDrive konta i Exchange pocztowe.

> [!IMPORTANT]
> Najważniejszą różnicą w rekordzie regulacyjną jest to, że po jego zastosowaniu do zawartości nikt, nawet administrator globalny, nie może usunąć etykiety.
>
> Etykiety przechowywania skonfigurowane dla rekordów prawnych mają również następujące ograniczenia administracyjne:
>
> - Po zapisaniu etykiety nie można skrócić okresu przechowywania, tylko wydłużyć ten okres.
> - Te etykiety nie są obsługiwane przez zasady automatycznego oznaczania etykiet i należy je stosować przy użyciu zasad [przechowywania etykiet](create-apply-retention-labels.md).
>
> Ponadto do dokumentu, który jest wyewidencjonowany w dokumencie wyewidencjonowany w programie SharePoint, nie można stosować etykiet SharePoint.
>
> Ze względu na ograniczenia i nieodwracalne działania należy przed wybraniem tej opcji na potrzeby etykiet przechowywania upewnić się, że konieczne jest korzystanie z rekordów prawnych. Aby zapobiec przypadkowej konfiguracji, ta opcja jest domyślnie wyłączona, ale musi zostać włączona przy użyciu programu PowerShell. Instrukcje znajdują się w [tece Deklarowanie rekordów przy użyciu etykiet przechowywania](declare-records.md).

## <a name="configuration-guidance"></a>Wskazówki dotyczące konfiguracji

Zobacz [Wprowadzenie do zarządzania rekordami](get-started-with-records-management.md). Ten artykuł zawiera informacje o subskrypcjach, uprawnieniach i linkach do wskazówek dotyczących szczegółowej konfiguracji scenariuszy zarządzania rekordami.