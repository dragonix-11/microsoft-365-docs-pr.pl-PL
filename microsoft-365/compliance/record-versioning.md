---
title: Używanie przechowywania wersji rekordów w programie SharePoint lub OneDrive
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
description: Dowiedz się więcej o rekordach, które pomogą Ci zaimplementować rozwiązanie do zarządzania rekordami na platformie Microsoft 365.
ms.openlocfilehash: 176e0a005d388681fcda119798fd838d73b7f733
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66629360"
---
# <a name="use-record-versioning-to-update-records-stored-in-sharepoint-or-onedrive"></a>Aktualizowanie rekordów przechowywanych w programie SharePoint lub OneDrive przy użyciu wersji rekordów

>*[Wskazówki dotyczące licencjonowania platformy Microsoft 365 dotyczące zgodności & zabezpieczeń](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

> [!NOTE]
> Ponieważ rekordy regulacyjne blokują edytowanie, przechowywanie wersji rekordów nie jest dostępne dla rekordów regulacyjnych.
>
> Możesz również uniemożliwić przechowywanie wersji rekordów dla dzierżawy, nawet jeśli nie używasz rekordów regulacyjnych: przejdź do **obszaru Zarządzanie rekordami** w **ustawieniach zarządzania rekordami portal zgodności Microsoft Purview > Etykiety** >  > **przechowywania****Konfiguruj przechowywanie wersji rekordów**, a następnie wyłącz ustawienie **Włącz przechowywanie wersji rekordów**.

Możliwość oznaczania dokumentu jako [rekordu](records-management.md#records) i ograniczania akcji, które mogą być wykonywane na rekordzie, jest podstawowym celem dla każdego rozwiązania do zarządzania rekordami. Jednak współpraca może być również potrzebna, aby użytkownicy mogli tworzyć kolejne wersje.

Na przykład możesz oznaczyć kontrakt sprzedaży jako rekord, ale następnie musisz zaktualizować umowę przy użyciu nowych warunków i oznaczyć najnowszą wersję jako nowy rekord, zachowując przy tym poprzednią wersję rekordu. W przypadku tego typu scenariuszy program SharePoint i usługa OneDrive *obsługują przechowywanie wersji rekordów*. Foldery notesu programu OneNote nie obsługują przechowywania wersji rekordów.

Aby użyć przechowywania wersji rekordów, należy najpierw [oznaczyć dokument etykietą przechowywania skonfigurowaną do oznaczania elementów jako rekordu](declare-records.md). W tym momencie obok etykiety przechowywania jest wyświetlana właściwość dokumentu o nazwie *Stan rekordu* . W zależności od tego, czy etykieta jest domyślnie skonfigurowana do odblokowywania rekordu (obecnie wdrażana), początkowy stan rekordu jest **zablokowany** lub **odblokowany**.

Teraz możesz wykonać następujące czynności:

- **Stale edytuj i zachowaj poszczególne wersje dokumentu jako rekordy, odblokowując i blokując właściwość Stan rekordu.** Tylko wtedy, gdy właściwość **Stan rekordu** jest **ustawiona na Zablokowane** jest nowa wersja rekordu zachowane. To przełączenie zablokowanego i odblokowanego zmniejsza ryzyko zachowania niepotrzebnych wersji i kopii dokumentu.
    
    > [!NOTE]
    > Jeśli etykieta jest domyślnie skonfigurowana do odblokowywania rekordu, ale przechowywanie wersji nie jest włączone przez administratora lub jest uniemożliwione przez ustawienie zarządzania rekordami, użytkownicy nie będą mogli odblokować dokumentu po jego zablokowaniu.

- **Aby rekordy były automatycznie przechowywane w repozytorium rekordów w miejscu znajdującym się w lokacji.** Każda witryna w programach SharePoint i OneDrive zachowuje zawartość w swojej bibliotece archiwum zachowywania. Wersje rekordów są przechowywane w folderze Rekordy w tej bibliotece. Aby uzyskać więcej informacji o tym, jak działa biblioteka archiwizacyjna, zobacz [Jak działa przechowywanie dla programu SharePoint i usługi OneDrive](retention-policies-sharepoint.md#how-retention-works-for-sharepoint-and-onedrive).

- **Zachowaj wiecznie zielony dokument zawierający wszystkie wersje.** Domyślnie każdy dokument programu SharePoint i usługi OneDrive ma historię wersji dostępną w menu elementów. W tej historii wersji można łatwo zobaczyć, które wersje są rekordami, i wyświetlić te dokumenty.

> [!TIP]
> Jeśli używasz przechowywania wersji rekordów z etykietą przechowywania, która ma akcję usuwania, rozważ skonfigurowanie ustawienia przechowywania **Rozpocznij okres przechowywania na podstawie: na wartość** **Kiedy elementy zostały oznaczone etykietą**. Dzięki temu ustawieniu etykiety początek okresu przechowywania jest resetowany dla każdej nowej wersji rekordu, co gwarantuje, że starsze wersje zostaną usunięte przed nowszymi wersjami.

Domyślnie przechowywanie wersji rekordów jest automatycznie dostępne dla każdego dokumentu z zastosowaną etykietą przechowywania, która oznacza element jako rekord, a etykieta jest [publikowana w witrynie](create-apply-retention-labels.md). Gdy użytkownik wyświetla właściwości dokumentu przy użyciu okienka szczegółów, może przełączać **stan Rekord** między **zablokowanym** i **odblokowanym**.

Gdy dokument jest odblokowany, każdy użytkownik ze standardowymi uprawnieniami do edycji może edytować plik. Jednak użytkownicy nie mogą usunąć pliku, ponieważ nadal jest to rekord. Po zakończeniu edycji użytkownik może przełączać **stan rekordu** z **Odblokowano** na **Zablokowany**, co uniemożliwia dalsze zmiany w tym stanie.
<br/><br/>

:::image type="content" alt-text="Rejestrowanie właściwości stanu w dokumencie oznaczonym jako rekord." source="../media/recordversioning8.png" lightbox="../media/recordversioning8.png":::

Aby uzyskać więcej informacji na temat dozwolonych akcji użytkownika po zablokowaniu lub odblokowaniu rekordu, zobacz [Porównanie ograniczeń dotyczących dozwolonych lub zablokowanych akcji](records-management.md#compare-restrictions-for-what-actions-are-allowed-or-blocked).

## <a name="locking-and-unlocking-a-record"></a>Blokowanie i odblokowywanie rekordu

Po zastosowaniu etykiety przechowywania oznaczającej zawartość jako rekord do dokumentu każdy użytkownik z uprawnieniami współtworzenia lub węższym poziomem uprawnień może odblokować rekord lub zablokować odblokowany rekord.
<br/><br/>

:::image type="content" alt-text="Stan rekordu pokazuje, że dokument rekordu jest odblokowany." source="../media/recordversioning9.png" lightbox="../media/recordversioning9.png":::

Po odblokowaniu rekordu są wykonywane następujące akcje:

1. Jeśli bieżąca witryna nie ma biblioteki archiwum zachowywania, zostanie utworzona.

2. Jeśli biblioteka archiwum zachowywania nie ma folderu Rekordy, zostanie utworzona.

3. Akcja **Kopiuj do** kopiuje najnowszą wersję dokumentu do folderu Rekordy. Akcja **Kopiuj do** zawiera tylko najnowszą wersję i brak wcześniejszych wersji. Skopiowany dokument jest teraz uważany za wersję rekordu dokumentu, a jego nazwa pliku ma format: Title GUID Version (Wersja identyfikatora GUID tytułu) \[\#\]

4. Kopia utworzona w folderze Rekordy jest dodawana do historii wersji oryginalnego dokumentu, a w tej wersji w polu komentarzy jest wyświetlany wyraz **Rekord** .

5. Oryginalny dokument to nowa wersja, którą można edytować, ale nie usuwać. Element kolumny biblioteki dokumentów **to rekord, który** nadal pokazuje wartość **Tak** , ponieważ dokument nadal jest rekordem, nawet jeśli można go teraz edytować.

Gdy użytkownik zablokuje rekord, nie można ponownie edytować oryginalnego dokumentu. Jest to jednak akcja odblokowywania rekordu, który kopiuje wersję do folderu Rekordy w bibliotece Archiwum zachowywania.

## <a name="record-versions"></a>Wersje rekordów

Za każdym razem, gdy rekord jest odblokowany, najnowsza wersja jest kopiowana do biblioteki archiwum zachowywania, a ta wersja zawiera wartość **Rekord** w polu **Komentarze** historii wersji.
<br/><br/>

:::image type="content" alt-text="Rekord pokazany w bibliotece archiwum zachowywania." source="../media/recordversioning10.png" lightbox="../media/recordversioning10.png":::

Aby wyświetlić historię wersji, wybierz dokument w bibliotece dokumentów, a następnie kliknij pozycję **Historia wersji** w menu elementów.

## <a name="searching-the-audit-log-for-record-versioning-events"></a>Wyszukiwanie w dzienniku inspekcji zdarzeń przechowywania wersji rekordów

Akcje blokowania i odblokowywania rekordów są rejestrowane w dzienniku inspekcji. W **obszarze Działania dotyczące plików i stron** wybierz pozycję **Zmieniono stan rekordu na zablokowany** , a **następnie zmieniono stan rekordu na odblokowany**.

Aby uzyskać więcej informacji na temat wyszukiwania tych zdarzeń, zobacz [Przeszukiwanie dziennika inspekcji](search-the-audit-log-in-security-and-compliance.md#file-and-page-activities).

## <a name="next-steps"></a>Następne kroki

W przypadku innych scenariuszy obsługiwanych przez zarządzanie rekordami zobacz [Typowe scenariusze zarządzania rekordami](get-started-with-records-management.md#common-scenarios).
