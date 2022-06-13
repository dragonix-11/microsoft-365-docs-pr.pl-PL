---
title: Deklaruj rekordy przy użyciu etykiet przechowywania
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
- SPO_Content
search.appverid:
- MOE150
- MET150
description: Deklarowanie rekordów przy użyciu etykiet przechowywania.
ms.openlocfilehash: 0e8453bee843131a5781318f7adde8d19bb04d92
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/10/2022
ms.locfileid: "66016817"
---
# <a name="declare-records-by-using-retention-labels"></a>Deklaruj rekordy przy użyciu etykiet przechowywania

>*[Microsoft 365 wskazówki dotyczące licencjonowania dotyczące zgodności & zabezpieczeń](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Aby zadeklarować dokumenty i wiadomości e-mail jako [rekordy](records-management.md#records), należy użyć [etykiet przechowywania](retention.md#retention-labels) , które oznaczają zawartość jako **rekord** lub **rekord regulacyjny**.

Jeśli nie masz pewności, czy chcesz używać rekordu, czy rekordu regulacyjnego, zobacz [Porównanie ograniczeń dotyczących dozwolonych lub zablokowanych akcji](records-management.md#compare-restrictions-for-what-actions-are-allowed-or-blocked). Jeśli musisz użyć rekordów regulacyjnych, musisz najpierw uruchomić polecenie programu PowerShell, zgodnie z opisem w następnej sekcji.

Następnie można opublikować te etykiety w zasadach etykiet przechowywania, aby użytkownicy i administratorzy mogli zastosować je do zawartości lub etykiet, które oznaczają elementy jako rekordy (ale nie rekordy regulacyjne), automatycznie zastosuj te etykiety do zawartości, którą chcesz zadeklarować rekord.

## <a name="how-to-display-the-option-to-mark-content-as-a-regulatory-record"></a>Jak wyświetlić opcję oznaczania zawartości jako rekordu regulacyjnego

> [!NOTE]
> Poniższa procedura to akcja z możliwością inspekcji, która rejestruje **opcję Włączone rejestrowanie rekordu regulacyjnego dla etykiet przechowywania** w sekcji [Działania zasad przechowywania i etykiet przechowywania](search-the-audit-log-in-security-and-compliance.md#retention-policy-and-retention-label-activities) dziennika inspekcji.

Domyślnie opcja etykiety przechowywania oznaczania zawartości jako rekordu regulacyjnego nie jest wyświetlana w kreatorze etykiet przechowywania. Aby wyświetlić tę opcję, należy najpierw uruchomić polecenie programu PowerShell:

1. [Połączenie do programu PowerShell Office 365 Security & Compliance](/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell).

2. Uruchom następujące polecenie cmdlet:

    ```powershell
    Set-RegulatoryComplianceUI -Enabled $true
    ````

    Nie ma monitu o potwierdzenie, a ustawienie staje się skuteczne natychmiast.

Jeśli zmienisz zdanie dotyczące wyświetlania tej opcji w kreatorze etykiet przechowywania, możesz ją ukryć ponownie, uruchamiając to samo polecenie cmdlet z wartością **false** : `Set-RegulatoryComplianceUI -Enabled $false`

## <a name="configuring-retention-labels-to-declare-records"></a>Konfigurowanie etykiet przechowywania w celu deklarowania rekordów

Podczas tworzenia etykiety przechowywania z poziomu rozwiązania **Do zarządzania rekordami** w portalu zgodności usługi Microsoft Purview można oznaczyć elementy jako rekord. Jeśli uruchomiono polecenie programu PowerShell z poprzedniej sekcji, możesz oznaczyć elementy jako rekord regulacyjny.

Przykład:

![Skonfiguruj etykietę przechowywania, aby oznaczyć zawartość jako rekord lub przepis.](../media/declare-records.png)

Przy użyciu tej etykiety przechowywania można teraz zastosować ją do SharePoint lub OneDrive dokumentów i Exchange wiadomości e-mail w razie potrzeby.

Aby uzyskać pełne instrukcje:

- [Publikowanie etykiet przechowywania i stosowanie ich w aplikacjach](create-apply-retention-labels.md)

- [Automatyczne stosowanie etykiety przechowywania do zawartości](apply-retention-labels-automatically.md) (nieobsługiwane dla rekordów regulacyjnych)

## <a name="tenant-setting-for-editing-record-properties"></a>Ustawienie dzierżawy na potrzeby edytowania właściwości rekordu

Jeśli użyjesz etykiet przechowywania do deklarowania elementów jako rekordów (zamiast rekordów regulacyjnych) w SharePoint i OneDrive, rozważ, czy musisz zmienić domyślne ustawienie dzierżawy, które umożliwia użytkownikom edytowanie właściwości [zablokowanego rekordu](record-versioning.md), gdy pliki są większe niż 0 bajtów.

Aby zmienić to ustawienie domyślne, przejdź do portalu  > [zgodności usługi Microsoft Purview](https://compliance.microsoft.com/)**Ustawienia zarządzania rekordami Ustawienia** >  zarządzania **rekordami** > **Etykiety** >  przechowywania **Zezwalaj na edytowanie właściwości rekordów**, a następnie wyłącz ustawienie **Zezwalaj użytkownikom na edytowanie właściwości rekordów**.

## <a name="applying-the-configured-retention-label-to-content"></a>Stosowanie skonfigurowanej etykiety przechowywania do zawartości

Gdy etykiety przechowywania, które oznaczają elementy jako rekord lub rekord regulacyjny, są udostępniane użytkownikom w celu zastosowania ich w aplikacjach:

- W przypadku Exchange każdy użytkownik z dostępem do zapisu do skrzynki pocztowej może zastosować te etykiety.
- W przypadku SharePoint i OneDrive każdy użytkownik w domyślnej grupie Członkowie (poziom uprawnień Współtworzenie) może zastosować te etykiety.

Przykład dokumentu oznaczonego jako rekord przy użyciu etykiety przechowywania:

![Okienko szczegółów dokumentu oznaczonego jako rekord.](../media/recordversioning7.png)

## <a name="searching-the-audit-log-for-labeled-items-that-were-declared-records"></a>Wyszukiwanie w dzienniku inspekcji elementów oznaczonych etykietami, które zostały zadeklarowane w rekordach

Akcje etykietowania w celu zadeklarowania elementów jako rekordów są rejestrowane w dzienniku inspekcji.

W przypadku elementów SharePoint:
- W obszarze **Działania dotyczące plików i stron** wybierz pozycję **Zmieniono etykietę przechowywania dla pliku**. To zdarzenie inspekcji dotyczy etykiet przechowywania, które oznaczają elementy jako rekordy, rekordy regulacyjne lub są standardowymi etykietami przechowywania.

W przypadku elementów Exchange:
- Z **Exchange działań skrzynki pocztowej** wybierz pozycję **Wiadomość oznaczona etykietą jako rekord**. To zdarzenie inspekcji dotyczy etykiet przechowywania, które oznaczają elementy jako rekordy lub rekordy regulacyjne.

Aby uzyskać więcej informacji na temat wyszukiwania tych zdarzeń, zobacz [Przeszukiwanie dziennika inspekcji w Centrum zgodności & zabezpieczeń](search-the-audit-log-in-security-and-compliance.md#file-and-page-activities).

## <a name="next-steps"></a>Następne kroki

Informacje na temat sposobu używania [przechowywania wersji rekordów do aktualizowania rekordów przechowywanych w SharePoint lub OneDrive](record-versioning.md).
