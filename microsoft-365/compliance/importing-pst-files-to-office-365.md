---
title: Dowiedz się więcej o importowaniu plików PST organizacji
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
f1_keywords:
- ms.o365.cc.IngestionHelp
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid: MET150
ms.assetid: ba688e0a-0fcb-4bd7-8e57-2b669564ea84
ms.custom:
- seo-marvel-apr2020
- admindeeplinkMAC
description: Dowiedz się, jak używać usługi Import w portalu zgodności usługi Microsoft Purview do zbiorczego importowania danych poczty e-mail (plików PST) do skrzynek pocztowych użytkowników.
ms.openlocfilehash: ba517359d54c698abd2ce50f07fe76d87fba472c
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2022
ms.locfileid: "64946226"
---
# <a name="learn-about-importing-your-organizations-pst-files"></a>Dowiedz się więcej o importowaniu plików PST organizacji

> [!NOTE]
> Ten artykuł jest przeznaczony dla administratorów. Czy próbujesz zaimportować pliki PST do własnej skrzynki pocztowej? Zobacz [Importowanie wiadomości e-mail, kontaktów i kalendarza z pliku pst Outlook](https://go.microsoft.com/fwlink/p/?LinkID=785075).

Usługa Import w <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">portalu zgodności usługi Microsoft Purview</a> umożliwia szybkie zbiorcze importowanie plików PST do Exchange Online skrzynek pocztowych w organizacji. Istnieją dwa sposoby importowania plików PST do Microsoft 365:

- **Przekazywanie** ![ sieci Przekazywanie w chmurze.](../media/54ab16ee-3822-4551-abef-3d926f4e1c01.png) — Upload pliki PST za pośrednictwem sieci do tymczasowej lokalizacji Storage platformy Azure w chmurze firmy Microsoft. Następnie użyjesz usługi Microsoft 365 Import, aby zaimportować dane PST do skrzynek pocztowych w organizacji.

- **Wysyłka** ![ dysku Dysk twardy.](../media/e72b76f3-1f73-4296-b749-c325d95d9ef6.png) — Skopiuj pliki PST na dysk twardy zaszyfrowany za pomocą funkcji BitLocker, a następnie fizycznie wyślij dysk do firmy Microsoft. Gdy firma Microsoft otrzyma dysk twardy, pracownicy centrum danych przekazują dane do tymczasowej lokalizacji Storage platformy Azure w chmurze firmy Microsoft. Następnie użyjesz usługi Microsoft 365 Import, aby zaimportować dane do skrzynek pocztowych w organizacji.

## <a name="step-by-step-instructions"></a>Instrukcje

Zobacz jeden z następujących tematów, aby uzyskać szczegółowe instrukcje krok po kroku dotyczące zbiorczego importowania plików PST organizacji do Microsoft 365.

- [Importowanie plików PST do Microsoft 365 przy użyciu przekazywania sieci](use-network-upload-to-import-pst-files.md)

- [Importuj pliki PST za pomocą wysyłki dysków](use-drive-shipping-to-import-pst-files-to-office-365.md)

## <a name="how-importing-pst-files-works"></a>Jak działa importowanie plików PST

Oto ilustracja i opis kompletnego procesu importowania PST. Ilustracja przedstawia podstawowy przepływ pracy i wyróżnia różnice między metodami przekazywania sieci i wysyłania dysków.

![Przepływ pracy procesu importowania PST.](../media/76997b69-67d7-433a-a0ca-9389f85a36a1.png)

1. **Pobierz narzędzia i klucz importu PST do prywatnej lokalizacji Storage platformy Azure** — pierwszym krokiem jest pobranie narzędzia i klucza dostępu używanego do przekazania plików PST lub skopiowania ich na dysk twardy. Można je uzyskać na stronie **Import** w portalu zgodności. Klucz zapewnia użytkownikowi (lub personelowi centrum danych firmy Microsoft w przypadku wysyłki dysku) uprawnienia niezbędne do przekazywania plików PST do prywatnej i bezpiecznej lokalizacji usługi Azure Storage. Ten klucz dostępu jest unikatowy dla Twojej organizacji i zapobiega nieautoryzowanemu dostępowi do plików PST po ich przekazaniu do chmury firmy Microsoft. Importowanie plików PST do Microsoft 365 nie wymaga od organizacji posiadania oddzielnej subskrypcji platformy Azure.

2. **Upload lub skopiuj pliki PST** — następny krok zależy od tego, czy używasz przekazywania sieci, czy wysyłania dysków do importowania plików PST. W obu przypadkach użyjesz narzędzia i bezpiecznego klucza magazynu uzyskanego w poprzednim kroku.

    - **Przekazywanie sieci:** Narzędzie AzCopy.exe (pobrane w kroku 1) służy do przekazywania i przechowywania plików PST w lokalizacji Storage platformy Azure w chmurze firmy Microsoft. Lokalizacja Storage platformy Azure, do którą przekazujesz pliki PST, znajduje się w tym samym regionalnym centrum danych firmy Microsoft co Organizacja.

      Aby je przekazać, pliki PST, które chcesz zaimportować, muszą znajdować się w udziale plików lub serwerze plików w organizacji.

    - **Wysyłka dysku:** Narzędzie WAImportExport.exe (pobrane w kroku 1) służy do kopiowania plików PST na dysk twardy. To narzędzie szyfruje dysk twardy za pomocą funkcji BitLocker, a następnie kopiuje je na dysk twardy. Podobnie jak w przypadku przekazywania sieci, pliki PST, które chcesz skopiować na dysk twardy, muszą znajdować się w udziale plików lub na serwerze plików w organizacji.

3. **Tworzenie pliku mapowania importu PST** — po przekazaniu plików PST do lokalizacji usługi Azure Storage lub skopiowaniu ich na dysk twardy następnym krokiem jest utworzenie pliku wartości rozdzielanej przecinkami (CSV), który określa, do których skrzynek pocztowych użytkowników zostaną zaimportowane pliki PST (a plik PST można zaimportować do podstawowej skrzynki pocztowej użytkownika lub jego skrzynki pocztowej archiwum). [Pobierz kopię pliku mapowania importu PST](https://go.microsoft.com/fwlink/p/?LinkId=544717). Usługa Microsoft 365 Import użyje informacji do zaimportowania plików PST.

4. **Tworzenie zadania importu PST** — następnym krokiem jest utworzenie zadania importu PST na stronie **Importowanie plików PST** w portalu zgodności i przesłanie pliku mapowania importu PST utworzonego w poprzednim kroku. W przypadku przekazywania sieci (ponieważ pliki PST zostały przekazane na platformę Azure) Microsoft 365 analizuje dane w plikach PST, a następnie umożliwia ustawienie filtrów, które kontrolują, jakie dane są faktycznie importowane do skrzynek pocztowych określonych w pliku mapowania importu PST.

    W przypadku wysyłki dysku w tym momencie dzieje się kilka innych rzeczy.

    - Fizycznie wysyłasz dysk twardy do centrum danych firmy Microsoft (adres wysyłki centrum danych firmy Microsoft jest wyświetlany po utworzeniu zadania importu).

    - Gdy firma Microsoft otrzyma dysk twardy, pracownicy centrum danych przekażą pliki PST na dysku twardym do lokalizacji usługi Azure Storage dla Twojej organizacji. Jak wyjaśniono wcześniej, pliki PST są przekazywane do lokalizacji Storage platformy Azure, która znajduje się w tym samym regionalnym centrum danych firmy Microsoft, w którym znajduje się Twoja organizacja.

      > [!NOTE]
      > Pliki PST na dysku twardym są przekazywane na platformę Azure w ciągu 7–10 dni roboczych od otrzymania przez firmę Microsoft dysku twardego.

      Podobnie jak w przypadku procesu przekazywania sieci, Microsoft 365 następnie analizuje dane w plikach PST i umożliwia ustawienie filtrów, które kontrolują, jakie dane są faktycznie importowane do skrzynek pocztowych określonych w pliku mapowania importu PST.

    - Firma Microsoft dostarcza dysk twardy z powrotem do Ciebie.

5. **Przefiltruj dane PST, które zostaną zaimportowane do skrzynek pocztowych** — po utworzeniu zadania importu (i po przekazaniu plików PST z zadania wysyłki dysku do lokalizacji usługi Azure Storage) Microsoft 365 analizuje dane w plikach PST (bezpiecznie i bezpiecznie) przez zidentyfikowanie wieku elementów i różnych typów wiadomości zawartych w plikach PST. Po zakończeniu analizy i przygotowaniu danych do zaimportowania można zaimportować wszystkie dane zawarte w plikach PST lub przyciąć zaimportowane dane, ustawiając filtry kontrolujące importowane dane.

6. **Uruchom zadanie importowania PST** — po uruchomieniu zadania importowania Microsoft 365 używa informacji w pliku mapowania importu PST do importowania plików PST z lokalizacji usługi Azure Storage do skrzynek pocztowych użytkowników. Informacje o stanie zadania importu (w tym informacje o każdym importowanym pliku PST) są wyświetlane na stronie **Importowanie plików PST** w portalu zgodności. Po zakończeniu zadania importowania stan zadania jest ustawiony na **Ukończono**.

## <a name="why-import-email-data-to-microsoft-365"></a>Dlaczego warto importować dane poczty e-mail do Microsoft 365?

- Jest to dobry sposób importowania archiwalnych danych komunikatów organizacji do Microsoft 365.

- Funkcja [Inteligentnego importu](filter-data-when-importing-pst-files.md) umożliwia filtrowanie elementów w plikach PST, które są faktycznie importowane do docelowych skrzynek pocztowych. Dzięki temu można przyciąć zaimportowane dane, ustawiając filtry kontrolujące importowane dane.

- Importowanie danych poczty e-mail do Microsoft 365 pomaga spełnić wymagania organizacji dotyczące zgodności, umożliwiając:

  - Włącz [archiwalne skrzynki pocztowe](enable-archive-mailboxes.md) i [automatyczne rozszerzanie archiwizacji](autoexpanding-archiving.md) , aby zapewnić użytkownikom dodatkowe miejsce do magazynowania skrzynki pocztowej.

  - Umieść skrzynki pocztowe w [blokadzie postępowania sądowego,](./create-a-litigation-hold.md) aby zachować zawartość.

  - Użyj [narzędzia do wyszukiwania zawartości](content-search.md) , aby wyszukać zawartość skrzynki pocztowej.

  - Zarządzanie dochodzeniami prawnymi organizacji przy użyciu [przypadków zbierania elektronicznych](./get-started-core-ediscovery.md) materiałów dowodowych

  - Użyj [zasad przechowywania](retention.md) w portalu zgodności, aby kontrolować czas przechowywania zawartości skrzynki pocztowej, a następnie usuwać zawartość po upływie okresu przechowywania.

  - Użyj [zasad zgodności komunikacji](communication-compliance.md) , aby sprawdzić komunikaty, aby upewnić się, że są one zgodne ze standardami komunikatów i dodać typ klasyfikacji.

- Importowanie danych do Microsoft 365 pomaga chronić przed utratą danych. Dane wiadomości e-mail zaimportowane do Microsoft 365 dziedziczą funkcje wysokiej dostępności Exchange Online.

- Dane poczty e-mail są dostępne dla użytkowników ze wszystkich urządzeń, ponieważ są przechowywane w chmurze.

## <a name="importing-sharepoint-data-to-microsoft-365"></a>Importowanie danych SharePoint do Microsoft 365

Możesz również importować pliki i dokumenty do SharePoint witryn i kont OneDrive w organizacji. Aby uzyskać więcej informacji, zapoznaj się z następującymi artykułami:

- [Migrowanie do usługi SharePoint Online](/sharepointmigration/migrate-to-sharepoint-online)

- [Wprowadzenie do narzędzia do migracji SharePoint](/sharepointmigration/introducing-the-sharepoint-migration-tool)

- [Migrowanie do usługi SharePoint Online przy użyciu programu PowerShell](/sharepointmigration/overview-spmt-ps-cmdlets)

- [Migrowanie zawartości udziału plików do usługi SharePoint Online przy użyciu urządzenia Azure Data Box](/sharepointmigration/how-to-migrate-file-share-content-to-spo-using-azuredatabox)

## <a name="frequently-asked-questions-about-importing-pst-files"></a>Często zadawane pytania dotyczące importowania plików PST

Poniżej przedstawiono kilka często zadawanych pytań dotyczących używania usługi Microsoft 365 Import do zbiorczego importowania plików PST do Microsoft 365 skrzynek pocztowych.

- [Importowanie plików PST przy użyciu przekazywania sieci](#using-network-upload-to-import-pst-files)

- [Importowanie plików PST przy użyciu wysyłki dysku](#using-drive-shipping-to-import-pst-files)

### <a name="using-network-upload-to-import-pst-files"></a>Importowanie plików PST przy użyciu przekazywania sieci

#### <a name="what-permissions-are-required-to-create-import-jobs-in-the-microsoft-365-import-service-using-network-upload"></a>Jakie uprawnienia są wymagane do tworzenia zadań importu w usłudze Microsoft 365 Import przy użyciu przekazywania sieci?

Musisz mieć przypisaną rolę Importuj eksport skrzynki pocztowej w Exchange Online, aby zaimportować pliki PST do Microsoft 365 skrzynek pocztowych. Domyślnie ta rola nie jest przypisana do żadnej grupy ról w Exchange Online. Rolę Import eksportu skrzynki pocztowej można dodać do grupy ról Zarządzanie organizacją. Możesz też utworzyć nową grupę ról, przypisać rolę Importuj eksport skrzynki pocztowej, a następnie dodać siebie lub innych użytkowników jako członka. Aby uzyskać więcej informacji, zobacz sekcje "Dodawanie roli do grupy ról" lub "Tworzenie grupy ról" w [temacie Zarządzanie grupami ról w Exchange Online](/Exchange/permissions-exo/role-groups).

Ponadto aby utworzyć zadania importu w portalu zgodności, musi być spełniony jeden z następujących elementów:

- Musisz mieć przypisaną rolę Adresaci poczty w Exchange Online. Domyślnie ta rola jest przypisywana do grup ról Zarządzanie organizacją i Zarządzanie adresatami.

    Lub

- Musisz być administratorem globalnym w swojej organizacji.

> [!TIP]
> Rozważ utworzenie nowej grupy ról w Exchange Online, która jest przeznaczona specjalnie do importowania plików PST do Microsoft 365. Aby uzyskać minimalny poziom uprawnień wymaganych do importowania plików PST, przypisz role Eksportuj i Adresaci poczty skrzynki pocztowej do nowej grupy ról, a następnie dodaj członków.

#### <a name="where-is-network-upload-available"></a>Gdzie jest dostępne przekazywanie sieci?

Przekazywanie sieci jest obecnie dostępne w następujących regionach: Stany Zjednoczone, Kanada, Brazylia, Wielka Brytania, Francja, Niemcy, Szwajcaria, Norwegia, Europa, Indie, Azja Wschodnia, Azja Południowo-Wschodnia, Japonia, Republika Korei, Australia i Zjednoczone Emiraty Arabskie (ZEA). Przekazywanie sieci będzie dostępne w kolejnych regionach w przyszłości.

#### <a name="what-is-the-pricing-for-importing-pst-files-by-using-network-upload"></a>Jakie są ceny importowania plików PST przy użyciu przekazywania sieci?

Importowanie plików PST za pomocą przekazywania sieci jest bezpłatne.

Oznacza to również, że po usunięciu plików PST z obszaru usługi Azure Storage nie będą one już wyświetlane na liście plików dla ukończonego zadania importowania w [Centrum administracyjne platformy Microsoft 365](https://go.microsoft.com/fwlink/p/?linkid=2024339). Chociaż zadanie importowania może nadal znajdować się na stronie **Importuj dane do Microsoft 365**, lista plików PST może być pusta podczas wyświetlania szczegółów starszych zadań importu.

#### <a name="what-version-of-the-pst-file-format-is-supported-for-importing-to-microsoft-365"></a>Jaka wersja formatu pliku PST jest obsługiwana w przypadku importowania do Microsoft 365?

Istnieją dwie wersje formatu pliku PST: ANSI i Unicode. Zalecamy importowanie plików korzystających z formatu pliku PST unicode. Jednak pliki korzystające z formatu pliku ANSI PST, takie jak te dla języków używających zestawu znaków dwubajtowych (DBCS), można również zaimportować do Microsoft 365. Aby uzyskać więcej informacji na temat importowania plików ANSI PST, zobacz Krok 4 w temacie [Używanie przekazywania sieci do importowania plików PST do Microsoft 365](./use-network-upload-to-import-pst-files.md).

Ponadto pliki PST z Outlook 2007 r. i nowszych wersji można zaimportować do Microsoft 365.

#### <a name="after-i-upload-my-pst-files-to-the-azure-storage-area-how-long-are-they-kept-in-azure-before-theyre-deleted"></a>Jak długo są przechowywane na platformie Azure przed ich usunięciem po przekazaniu plików PST do obszaru usługi Azure Storage?

W przypadku importowania plików PST za pomocą metody przekazywania sieci należy przekazać je do kontenera obiektów blob platformy Azure o nazwie `ingestiondata`. Jeśli na stronie **Importowanie plików PST** w portalu zgodności nie są w toku żadne zadania importu, wszystkie pliki PST w `ingestiondata` kontenerze na platformie Azure zostaną usunięte 30 dni po utworzeniu ostatniego zadania importu w portalu zgodności. Oznacza to również, że musisz utworzyć nowe zadanie importu w portalu zgodności (opisanym w kroku 5 w instrukcjach przekazywania sieci) w ciągu 30 dni od przekazania plików PST na platformę Azure.

Oznacza to również, że po usunięciu plików PST z obszaru usługi Azure Storage nie będą one już wyświetlane na liście plików dla ukończonego zadania importowania w portalu zgodności. Mimo że zadanie importu może nadal znajdować się na stronie **Importowanie plików PST** w portalu zgodności, lista plików PST może być pusta podczas wyświetlania szczegółów starszych zadań importowania.

#### <a name="how-long-does-it-take-to-import-a-pst-file-to-a-mailbox-using-network-upload"></a>Jak długo trwa importowanie pliku PST do skrzynki pocztowej przy użyciu przekazywania sieci?

Zależy to od pojemności sieci, ale przekazywanie każdego terabajtu (TB) danych do obszaru usługi Azure Storage dla organizacji trwa zwykle kilka godzin. Po skopiowaniu plików PST do obszaru usługi Azure Storage plik PST jest importowany do skrzynki pocztowej Microsoft 365 z szybkością około 24 GB dziennie<sup>\*</sup>. Jeśli ta stawka nie spełnia Twoich potrzeb, możesz rozważyć inne metody pobierania danych poczty e-mail do Microsoft 365. Aby uzyskać więcej informacji, zobacz [Sposoby migracji wielu kont e-mail do Microsoft 365](/Exchange/mailbox-migration/mailbox-migration).

Jeśli różne pliki PST są importowane do różnych docelowych skrzynek pocztowych, proces importowania odbywa się równolegle; Innymi słowy, każda para PST/skrzynka pocztowa jest importowana jednocześnie. Jeśli wiele plików PST zostanie zaimportowanych do tej samej skrzynki pocztowej, zostaną one zaimportowane sekwencyjnie (pojedynczo), a nie jednocześnie.

> [!NOTE]
> <sup>\*</sup> Ta stawka nie jest gwarantowana. Problemy z obciążeniem serwera i przejściową wydajnością mogą zmniejszyć tę szybkość.

#### <a name="how-does-the-pst-import-process-handle-duplicate-email-items"></a>Jak proces importowania PST obsługuje zduplikowane elementy poczty e-mail?

Proces importowania PST sprawdza zduplikowane elementy i nie kopiuje elementów z pliku PST do skrzynki pocztowej lub archiwum, jeśli w folderze docelowym w docelowej skrzynce pocztowej lub archiwum docelowym istnieje zgodny element. Jeśli ponownie zaimportujesz ten sam plik PST i określisz inny folder docelowy (przy użyciu właściwości TargetRootFolder w pliku mapowania importu PST) niż ten określony w poprzednim zadaniu importowania, wszystkie elementy w pliku PST zostaną ponownie zaimportowane.

#### <a name="is-there-a-message-size-limit-when-importing-pst-files-using-network-upload"></a>Czy istnieje limit rozmiaru komunikatu podczas importowania plików PST przy użyciu przekazywania sieci?

Tak. Jeśli plik PST zawiera element skrzynki pocztowej o rozmiarze większym niż 150 MB, element zostanie pominięty i nie zostanie zaimportowany podczas procesu importowania. Elementy większe niż 150 MB nie są importowane, ponieważ 150 MB to limit rozmiaru komunikatu w Exchange Online. Aby uzyskać więcej informacji, zobacz [Limity komunikatów w Exchange Online](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#message-limits).

#### <a name="are-message-properties-such-as-when-the-message-was-sent-or-received-the-list-of-recipients-and-other-properties-preserved-when-pst-files-are-imported-to-a-microsoft-365-mailbox-using-network-upload"></a>Czy właściwości wiadomości, takie jak kiedy wiadomość została wysłana lub odebrana, lista adresatów i inne właściwości, są zachowywane, gdy pliki PST są importowane do Microsoft 365 skrzynki pocztowej przy użyciu przekazywania sieci?

Tak. Oryginalne metadane komunikatu nie są zmieniane podczas procesu importowania.

#### <a name="is-there-a-limit-to-the-number-of-levels-in-a-folder-hierarchy-for-a-pst-file-that-i-want-to-import-to-a-mailbox-using-network-upload"></a>Czy istnieje ograniczenie liczby poziomów w hierarchii folderów dla pliku PST, który chcę zaimportować do skrzynki pocztowej przy użyciu przekazywania sieci?

Tak. Nie można zaimportować pliku PST zawierającego co najmniej 300 poziomów zagnieżdżonych folderów.

#### <a name="can-i-use-network-upload-to-import-pst-files-to-an-inactive-mailbox-in-microsoft-365"></a>Czy można użyć przekazywania sieci do zaimportowania plików PST do nieaktywnej skrzynki pocztowej w Microsoft 365?

Tak, ta funkcja jest teraz dostępna.

#### <a name="can-i-use-network-upload-to-import-pst-files-to-an-online-archive-mailbox-in-an-exchange-hybrid-deployment"></a>Czy można użyć przekazywania sieci do zaimportowania plików PST do skrzynki pocztowej archiwum online w Exchange wdrożenia hybrydowego?

Tak, ta funkcja jest teraz dostępna.

#### <a name="can-i-use-network-upload-to-import-pst-files-to-public-folders-in-exchange-online"></a>Czy można zaimportować pliki PST do folderów publicznych w Exchange Online za pomocą przekazywania sieci?

Nie, nie można importować plików PST do folderów publicznych.

### <a name="using-drive-shipping-to-import-pst-files"></a>Importowanie plików PST przy użyciu wysyłki dysku

#### <a name="what-permissions-are-required-to-create-import-jobs-in-the-microsoft-365-import-service-using-drive-shipping"></a>Jakie uprawnienia są wymagane do tworzenia zadań importu w usłudze Microsoft 365 Import przy użyciu wysyłki dysku?

Musisz mieć przypisaną rolę Importuj eksport skrzynki pocztowej, aby zaimportować pliki PST do Microsoft 365 skrzynek pocztowych. Domyślnie ta rola nie jest przypisana do żadnej grupy ról w Exchange Online. Rolę Import eksportu skrzynki pocztowej można dodać do grupy ról Zarządzanie organizacją. Możesz też utworzyć nową grupę ról, przypisać rolę Importuj eksport skrzynki pocztowej, a następnie dodać siebie lub innych użytkowników jako członka. Aby uzyskać więcej informacji, zobacz sekcje "Dodawanie roli do grupy ról" lub "Tworzenie grupy ról" w [temacie Zarządzanie grupami ról w Exchange Online](/Exchange/permissions-exo/role-groups).

Ponadto aby utworzyć zadania importu w portalu zgodności, musi być spełniony jeden z następujących elementów:

- Musisz mieć przypisaną rolę Adresaci poczty w Exchange Online. Domyślnie ta rola jest przypisywana do grup ról Zarządzanie organizacją i Zarządzanie adresatami.

    Lub

- Musisz być administratorem globalnym w swojej organizacji.

> [!TIP]
> Rozważ utworzenie nowej grupy ról w Exchange Online, która jest przeznaczona specjalnie do importowania plików PST do Microsoft 365. Aby uzyskać minimalny poziom uprawnień wymaganych do importowania plików PST, przypisz role Eksportuj i Adresaci poczty skrzynki pocztowej do nowej grupy ról, a następnie dodaj członków.

#### <a name="where-is-drive-shipping-available"></a>Gdzie jest dostępna wysyłka dysku?

Wysyłka dysków jest obecnie dostępna w Stany Zjednoczone, Kanadzie, Brazylii, Wielkiej Brytanii, Europie, Indiach, Azji Wschodniej, Azji Południowo-Wschodniej, Japonii, Republice Korei i Australii. Wysyłka dysku będzie dostępna w kolejnych regionach w przyszłości.

> [!NOTE]
> W tej chwili wysyłka dysku w celu zaimportowania plików PST nie jest dostępna w Niemczech i Szwajcarii. To często zadawane pytania zostaną zaktualizowane, gdy wysyłka dysku będzie dostępna w tych krajach.

#### <a name="what-commercial-licensing-agreements-support-drive-shipping"></a>Jakie komercyjne umowy licencyjne obsługują wysyłkę?

Wysyłanie dysków w celu zaimportowania plików PST do Microsoft 365 jest dostępne za pośrednictwem usługi Microsoft Enterprise Agreement (EA). Wysyłka dysku nie jest dostępna za pośrednictwem umowy Microsoft Products and Services Agreement (MPSA).

#### <a name="what-is-the-pricing-for-using-drive-shipping-to-import-pst-files-to-microsoft-365"></a>Jakie są ceny za korzystanie z wysyłania dysków do importowania plików PST do Microsoft 365?

Koszt użycia wysyłki dysku do importowania plików PST do Microsoft 365 skrzynek pocztowych wynosi 2 USD za GB danych. Jeśli na przykład zostanie dostarczony dysk twardy zawierający 1000 GB (1 TB) plików PST, koszt to 2000 USD. Możesz współpracować z partnerem w celu uiszczenia opłaty importowej. Aby uzyskać informacje na temat znajdowania partnera, zobacz [Znajdowanie partnera lub odsprzedawcy firmy Microsoft](../admin/manage/find-your-partner-or-reseller.md).

#### <a name="what-kind-of-hard-drives-are-supported-for-drive-shipping"></a>Jakiego rodzaju dyski twarde są obsługiwane w przypadku wysyłki dysków?

Tylko 2,5-calowe dyski półprzewodnikowe (SSD) lub 2,5 cala lub 3,5 cala wewnętrzne dyski twarde SATA II/III są obsługiwane do użytku z usługą importu Microsoft 365. Dysków twardych można używać do 10 TB. W przypadku zadań importowania będzie przetwarzany tylko pierwszy wolumin danych na dysku twardym. Wolumin danych musi być sformatowany przy użyciu systemu PLIKÓW NTFS. Podczas kopiowania danych na dysk twardy można dołączyć je bezpośrednio przy użyciu 2,5-calowego dysku SSD lub 2,5 cala lub 3,5 cala łącznika SATA II/III lub można go dołączyć zewnętrznie przy użyciu zewnętrznego 2,5-calowego dysku SSD lub 2,5 cala lub 3,5 cala adaptera USB SATA II/III.

> [!IMPORTANT]
> Zewnętrzne dyski twarde z wbudowaną kartą USB nie są obsługiwane przez usługę Microsoft 365 Import. Ponadto nie można użyć dysku wewnątrz obudowy zewnętrznego dysku twardego. Nie wysyłaj zewnętrznych dysków twardych.

#### <a name="how-many-hard-drives-can-i-ship-for-a-single-import-job"></a>Ile dysków twardych można dostarczyć do jednego zadania importu?

Można wysłać maksymalnie 10 dysków twardych dla jednego zadania importu.

#### <a name="after-i-ship-my-hard-drive-how-long-does-it-take-to-get-to-the-microsoft-datacenter"></a>Jak długo trwa dostarczenie dysku twardego do centrum danych firmy Microsoft?

Zależy to od kilku rzeczy, takich jak bliskość centrum danych firmy Microsoft i rodzaj opcji wysyłki użytej do wysłania dysku twardego (na przykład dostawa następnego dnia, dostawa dwudniowa lub dostawa naziemna). W przypadku większości nadawców możesz użyć numeru śledzenia, aby śledzić stan dostawy.

#### <a name="after-my-hard-drive-arrives-at-the-microsoft-datacenter-how-long-does-it-take-to-upload-my-pst-files-to-azure"></a>Jak długo trwa przekazywanie plików PST na platformę Azure po dotarciu mojego dysku twardego do centrum danych firmy Microsoft?

Po odebraniu dysku twardego w centrum danych firmy Microsoft przekazanie plików PST do lokalizacji usługi Azure Storage dla organizacji potrwa od 7 do 10 dni roboczych. Pliki PST zostaną przekazane do kontenera obiektów blob platformy Azure o nazwie `ingestiondata`.

#### <a name="how-long-does-it-take-to-import-a-pst-file-to-a-mailbox-using-drive-shipping"></a>Jak długo trwa importowanie pliku PST do skrzynki pocztowej przy użyciu wysyłania dysku?

Po przekazaniu plików PST do obszaru usługi Azure Storage Microsoft 365 analizuje dane w plikach PST (w bezpieczny i bezpieczny sposób), aby zidentyfikować wiek elementów i różne typy komunikatów zawarte w plikach PST. Po zakończeniu tej analizy będziesz mieć możliwość zaimportowania wszystkich danych w plikach PST lub ustawienia filtrów, które kontrolują, jakie dane są importowane. Po rozpoczęciu zadania importowania plik PST jest importowany do skrzynki pocztowej Microsoft 365 z szybkością około 24 GB dziennie.<sup>\*</sup> Jeśli ta stawka nie spełnia Twoich potrzeb, możesz rozważyć inne metody pobierania danych poczty e-mail do Microsoft 365. Aby uzyskać więcej informacji, zobacz [Sposoby migracji wielu kont e-mail do Microsoft 365](/Exchange/mailbox-migration/mailbox-migration).

Jeśli różne pliki PST są importowane do różnych docelowych skrzynek pocztowych, proces importowania odbywa się równolegle; Innymi słowy, każda para PST/skrzynka pocztowa jest importowana jednocześnie. Jeśli wiele plików PST zostanie zaimportowanych do tej samej skrzynki pocztowej, zostaną one zaimportowane sekwencyjnie (pojedynczo), a nie jednocześnie.

> [!NOTE]
> <sup>\*</sup> Ta stawka nie jest gwarantowana. Problemy z obciążeniem serwera i przejściową wydajnością mogą zmniejszyć tę szybkość.

#### <a name="after-microsoft-uploads-my-pst-files-to-azure-how-long-are-they-kept-in-azure-before-theyre-deleted"></a>Jak długo są przechowywane na platformie Azure przed ich usunięciem po przekazaniu przez firmę Microsoft plików PST na platformę Azure?

Wszystkie pliki PST w lokalizacji usługi Azure Storage dla organizacji (w kontenerze obiektów blob o nazwie `ingestiondata`), zostaną usunięte 30 dni po utworzeniu ostatniego zadania importu na stronie **Importowanie plików PST** w portalu zgodności.

Oznacza to również, że po usunięciu plików PST z obszaru usługi Azure Storage nie będą one już wyświetlane na liście plików dla ukończonego zadania importowania w portalu zgodności. Mimo że zadanie importu może nadal znajdować się na stronie **Importowanie plików PST** w portalu zgodności, lista plików PST może być pusta podczas wyświetlania szczegółów starszych zadań importowania.

#### <a name="what-version-of-the-pst-file-format-is-supported-for-importing-to-microsoft-365"></a>Jaka wersja formatu pliku PST jest obsługiwana w przypadku importowania do Microsoft 365?

Istnieją dwie wersje formatu pliku PST: ANSI i Unicode. Zalecamy importowanie plików korzystających z formatu pliku PST unicode. Jednak pliki korzystające z formatu pliku ANSI PST, takie jak te dla języków używających zestawu znaków dwubajtowych (DBCS), można również zaimportować do Microsoft 365. Aby uzyskać więcej informacji na temat importowania plików ANSI PST, zobacz Krok 3 w [temacie Use drive shipping to import your organization PST files to Microsoft 365 (Importowanie plików PST organizacji do Microsoft 365](use-drive-shipping-to-import-pst-files-to-office-365.md#step-3-create-the-pst-import-mapping-file)).

Ponadto pliki PST z Outlook 2007 r. i nowszych wersji można zaimportować do Microsoft 365.

#### <a name="is-there-a-message-size-limit-when-importing-pst-files-using-drive-shipping"></a>Czy istnieje limit rozmiaru komunikatu podczas importowania plików PST przy użyciu wysyłania dysku?

Tak. Jeśli plik PST zawiera element skrzynki pocztowej o rozmiarze większym niż 150 MB, element zostanie pominięty i nie zostanie zaimportowany podczas procesu importowania. Elementy większe niż 150 MB nie są importowane, ponieważ 150 MB to limit rozmiaru komunikatu w Exchange Online. Aby uzyskać więcej informacji, zobacz [Limity komunikatów w Exchange Online](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#message-limits).

  **Jak proces importowania PST obsługuje zduplikowane elementy poczty e-mail?

Proces importowania PST sprawdza zduplikowane elementy i nie kopiuje elementów z pliku PST do skrzynki pocztowej lub archiwum, jeśli w folderze docelowym w docelowej skrzynce pocztowej lub archiwum docelowym istnieje zgodny element. Jeśli ponownie zaimportujesz ten sam plik PST i określisz inny folder docelowy (przy użyciu właściwości TargetRootFolder w pliku mapowania importu PST) niż ten określony w poprzednim zadaniu importowania, wszystkie elementy w pliku PST zostaną ponownie zaimportowane.

#### <a name="are-message-properties-such-as-when-the-message-was-sent-or-received-the-list-of-recipients-and-other-properties-preserved-when-pst-files-are-imported-to-a-microsoft-365-mailbox-using-drive-shipping"></a>Czy właściwości wiadomości, takie jak kiedy wiadomość została wysłana lub odebrana, lista adresatów i inne właściwości, są zachowywane, gdy pliki PST są importowane do skrzynki pocztowej Microsoft 365 przy użyciu wysyłania dysku?

Tak. Oryginalne metadane komunikatu nie są zmieniane podczas procesu importowania

#### <a name="is-there-a-limit-to-the-number-of-levels-in-a-folder-hierarchy-for-a-pst-file-that-i-want-to-import-to-a-mailbox-using-drive-shipping"></a>Czy istnieje ograniczenie liczby poziomów w hierarchii folderów dla pliku PST, który chcę zaimportować do skrzynki pocztowej przy użyciu wysyłania dysku?

Tak. Nie można zaimportować pliku PST zawierającego co najmniej 300 poziomów zagnieżdżonych folderów.

#### <a name="can-i-use-drive-shipping-to-import-pst-files-to-an-inactive-mailbox-in-microsoft-365"></a>Czy mogę zaimportować pliki PST do nieaktywnej skrzynki pocztowej w Microsoft 365 za pomocą wysyłki dysku?

Tak, ta funkcja jest teraz dostępna.

#### <a name="can-i-use-drive-shipping-to-import-pst-files-to-an-online-archive-mailbox-in-an-exchange-hybrid-deployment"></a>Czy można użyć wysyłania dysków do importowania plików PST do skrzynki pocztowej archiwum online w Exchange wdrożenia hybrydowego?

Tak, ta funkcja jest teraz dostępna.

#### <a name="can-i-use-drive-shipping-to-import-pst-files-to-public-folders-in-exchange-online"></a>Czy można użyć wysyłania dysków do importowania plików PST do folderów publicznych w Exchange Online?

Nie, nie można importować plików PST do folderów publicznych.

#### <a name="can-microsoft-wipe-my-hard-drive-before-they-ship-it-back-to-me"></a>Czy firma Microsoft może wyczyścić mój dysk twardy przed wysłaniem go z powrotem do mnie?

Nie, firma Microsoft nie może wyczyścić dysków twardych przed wysłaniem ich z powrotem do klientów. Dyski twarde są zwracane w tym samym stanie, w jakiej znajdowały się, gdy zostały odebrane przez firmę Microsoft.

#### <a name="can-microsoft-shred-my-hard-drive-instead-of-shipping-it-back-to-me"></a>Czy firma Microsoft może zniszczyć mój dysk twardy zamiast wysyłać go z powrotem do mnie?

Nie, firma Microsoft nie może zniszczyć twojego dysku twardego. Dyski twarde są zwracane w tym samym stanie, w jakiej znajdowały się, gdy zostały odebrane przez firmę Microsoft.

#### <a name="what-courier-services-are-supported-for-return-shipping"></a>Jakie usługi kurierskie są obsługiwane w przypadku wysyłki zwrotnej?

Jeśli jesteś klientem w Stany Zjednoczone lub Europie, firma Microsoft zwraca twój dysk twardy za pomocą programu FedEx. W przypadku wszystkich innych regionów firma Microsoft używa protokołu DHL.

#### <a name="what-are-the-return-shipping-costs"></a>Jakie są koszty wysyłki zwrotnej?

Koszty wysyłki zwrotnej różnią się w zależności od bliskości centrum danych firmy Microsoft, do których wysłano dysk twardy. Firma Microsoft rozliczy Twoje konto FedEx lub DHL w celu zwrócenia dysku twardego. Koszt wysyłki zwrotnej jest twoim obowiązkiem.

#### <a name="can-i-use-a-custom-courier-shipping-service-such-as-fedex-custom-shipping-to-ship-my-hard-drive-to-microsoft"></a>Czy mogę wysłać dysk twardy do firmy Microsoft za pomocą niestandardowej usługi wysyłki kurierskiej, takiej jak FedEx Custom Shipping?

Tak.

#### <a name="if-i-have-to-ship-my-hard-drive-to-another-country-is-there-anything-i-need-to-do"></a>Jeśli muszę wysłać dysk twardy do innego kraju, czy jest coś, co muszę zrobić?

Dysk twardy dostarczany firmie Microsoft może wymagać przekroczenia granic międzynarodowych. Jeśli tak, jesteś odpowiedzialny za zapewnienie, że dysk twardy i jego dane zostaną zaimportowane i/lub wyeksportowane zgodnie z obowiązującymi przepisami. Przed wysłaniem dysku twardego skontaktuj się z doradcami, aby sprawdzić, czy dysk i dane mogą być legalnie dostarczane do określonego centrum danych firmy Microsoft. Pomoże to zapewnić, że dotrze ona do firmy Microsoft w odpowiednim czasie.
