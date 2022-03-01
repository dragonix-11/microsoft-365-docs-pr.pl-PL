---
title: Informacje o importowaniu plików PST organizacji
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
description: Dowiedz się, jak używać usługi importowania w p Centrum zgodności platformy Microsoft 365 do zbiorczego importowania danych poczty e-mail (plików PST) do skrzynek pocztowych użytkowników.
ms.openlocfilehash: b88cd9f6b12f382f8fdeb696af32c1fd95ad805d
ms.sourcegitcommit: 400ef9ac34247978e3de7ecc0b376c4abb6c99d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/27/2022
ms.locfileid: "63010646"
---
# <a name="learn-about-importing-your-organizations-pst-files"></a>Informacje o importowaniu plików PST organizacji

> [!NOTE]
> Ten artykuł jest dla administratorów. Czy próbujesz zaimportować pliki PST do własnej skrzynki pocztowej? Zobacz [Importowanie wiadomości e-mail, kontaktów i kalendarza Outlook pliku pst](https://go.microsoft.com/fwlink/p/?LinkID=785075).

Za pomocą usługi importowania w aplikacji usługi <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Centrum zgodności platformy Microsoft 365</a> szybko zbiorczo zaimportuj pliki PST do Exchange Online pocztowych w organizacji. Istnieją dwa sposoby importowania plików PST do Microsoft 365:

- **Przekazywanie sieciowe** ![ Przekazywanie w chmurze.](../media/54ab16ee-3822-4551-abef-3d926f4e1c01.png) — Upload pliki PST przez sieć do tymczasowej lokalizacji Storage Azure w chmurze firmy Microsoft. Następnie za pomocą usługi importowania Microsoft 365 zaimportujesz dane z pliku PST do skrzynek pocztowych w Twojej organizacji.

- **Wysyłka dysków** ![ Dysk twardy.](../media/e72b76f3-1f73-4296-b749-c325d95d9ef6.png) - Skopiuj pliki PST na zaszyfrowany dysk twardy funkcji BitLocker, a następnie fizycznie wyślij dysk do firmy Microsoft. Gdy firma Microsoft otrzyma dysk twardy, pracownicy centrum danych przekażą dane do tymczasowej lokalizacji Storage Azure w chmurze firmy Microsoft. Następnie za pomocą usługi importowania Microsoft 365 zaimportujesz dane do skrzynek pocztowych w Organizacji.

## <a name="step-by-step-instructions"></a>Instrukcje krok po kroku

Zobacz jeden z poniższych tematów, aby uzyskać szczegółowe instrukcje krok po kroku dotyczące zbiorczego importowania plików PST organizacji w celu Microsoft 365.

- [Użyj przekazywania sieciowego, aby zaimportować pliki PST do Microsoft 365](use-network-upload-to-import-pst-files.md)

- [Importowanie plików PST za pomocą wysyłki dysków](use-drive-shipping-to-import-pst-files-to-office-365.md)

## <a name="how-importing-pst-files-works"></a>Jak działa importowanie plików PST

Poniżej przedstawiono ilustrację i opis pełnego procesu importowania pliku PST. Na ilustracji przedstawiono podstawowy przepływ pracy i wyróżnione są różnice między metodami przekazywania sieciowego i wysyłki dysków.

![Przepływ pracy procesu importowania pliku PST.](../media/76997b69-67d7-433a-a0ca-9389f85a36a1.png)

1. Pobierz narzędzia do importowania plików PST i klucz do prywatnej lokalizacji usługi **Azure Storage** — pierwszym krokiem jest pobranie narzędzia i klucza dostępu służącego do przekazywania plików PST lub kopiowania ich na dysk twardy. Można je uzyskać na **stronie Importowanie** w Centrum zgodności platformy Microsoft 365. Ten klucz zapewnia Ci (lub pracownikowi centrum danych firmy Microsoft w przypadku wysyłki dysków) niezbędne uprawnienia do przekazywania plików PST do prywatnej i bezpiecznej lokalizacji Storage danych platformy Azure. Ten klucz dostępu jest unikatowy dla Twojej organizacji i pomaga zapobiec nieautoryzowanemu dostępowi do plików PST po ich przesłaniu do chmury firmy Microsoft. Importowanie plików PST do Microsoft 365 nie wymaga, aby Twoja organizacja posiadała osobną subskrypcję platformy Azure.

2. **Upload lub** skopiuj pliki PST — Następny krok zależy od tego, czy do importowania plików PST używasz przekazywania sieciowego, czy wysyłki dysków. W obu przypadkach użyjesz narzędzia i bezpiecznego klucza magazynu uzyskanego w poprzednim kroku.

    - **Przekazywanie sieciowe:** Narzędzie AzCopy.exe (pobrane w kroku 1) służy do przekazywania i przechowywania plików PST w lokalizacji usługi Azure Storage w chmurze firmy Microsoft. Lokalizacja pliku PST Storage Azure, do która jest przesyłana do firmy Microsoft, znajduje się w tym samym regionalnym centrum danych firmy Microsoft, w którym znajduje się Twoja organizacja.

      Aby można było je przekazać, pliki PST, które chcesz zaimportować, muszą być umieszczone w udziałach plików lub na serwerze plików w organizacji.

    - **Wysyłka dysków:** Narzędzie WAImportExport.exe (pobrane w kroku 1) służy do kopiowania plików PST na dysk twardy. To narzędzie szyfruje dysk twardy przy użyciu funkcji BitLocker, a następnie kopiuje pliki PST na dysk twardy. Podobnie jak w przypadku przekazywania sieciowego pliki PST, które chcesz skopiować na dysk twardy, muszą być umieszczone w udziału plików lub na serwerze plików w organizacji.

3. Tworzenie pliku mapowania na importowanie pliku **PST** — po przesłaniu plików PST do lokalizacji usługi Azure Storage lub skopiowaniu ich na dysk twardy następnym krokiem jest utworzenie pliku wartości rozdzielanych przecinkami (CSV), który określa, do których skrzynek pocztowych użytkowników zostaną zaimportowane pliki PST (i plik PST można zaimportować do podstawowej skrzynki pocztowej użytkownika lub jego archiwaowej skrzynki pocztowej). [Pobierz kopię pliku mapowania importu pliku PST](https://go.microsoft.com/fwlink/p/?LinkId=544717). Usługa Microsoft 365 importowania użyje tych informacji do zaimportowania plików PST.

4. **Tworzenie zadania importu pliku PST** — następnym krokiem jest utworzenie zadania importu pliku PST na stronie Importowanie plików **PST** w programie Centrum zgodności platformy Microsoft 365 i przesłanie pliku mapowania importu pliku PST utworzonego w poprzednim kroku. W przypadku przekazywania sieciowego (ponieważ pliki PST zostały przekazane do platformy Azure) program Microsoft 365 analizuje dane w plikach PST, Microsoft 365 następnie umożliwia ustawienie filtrów sterujących tym, jakie dane są faktycznie importowane do skrzynek pocztowych określonych w pliku mapowania importu pliku PST.

    W przypadku wysyłki dysków na tym etapie procesu stanie się kilka innych rzeczy.

    - Fizycznie wysyłasz dysk twardy do centrum danych firmy Microsoft (adres wysyłkowy centrum danych firmy Microsoft jest wyświetlany po utworzeniu zadania importu).

    - Gdy firma Microsoft otrzyma dysk twardy, pracownik centrum danych przekaże pliki PST z tego dysku do lokalizacji usługi Azure Storage organizacji. Jak wyjaśniono wcześniej, pliki PST są przekazywane do lokalizacji usługi Azure Storage, która znajduje się w tym samym regionalnym centrum danych firmy Microsoft, w którym znajduje się Twoja organizacja.

      > [!NOTE]
      > Pliki PST na dysku twardym są przekazywane na platformę Azure w ciągu 7 do 10 dni roboczych po otrzymaniu dysku twardego przez firmę Microsoft.

      Podobnie jak w przypadku procesu przekazywania sieciowego program Microsoft 365 następnie analizuje dane w plikach PST i daje możliwość ustawienia filtrów sterujących tym, jakie dane faktycznie są importowane do skrzynek pocztowych określonych w pliku mapowania importu PST.

    - Firma Microsoft wysyła dysk twardy z powrotem do Ciebie.

5. Filtrowanie danych **pst**, które zostaną zaimportowane do skrzynek pocztowych — po utworzeniu zadania importu (i przekazeniu plików PST z zadania wysyłki dysków do lokalizacji usługi Azure Storage) program Microsoft 365 analizuje dane w plikach PST (bezpiecznie i bezpiecznie), identyfikując wiek elementów i różne typy wiadomości zawarte w plikach PST. Po zakończeniu analizy i przygotowaniu danych do zaimportowania możesz zaimportować wszystkie dane zawarte w plikach PST lub przyciąć importowane dane, ustawiając filtry kontrolek, które kontrolują, które dane są importowane.

6. **Uruchamianie** zadania importu pliku PST — po uruchomieniu zadania importu program Microsoft 365 używa informacji z pliku mapowania importu pliku PST do importowania plików PST z lokalizacji usługi Azure Storage do skrzynek pocztowych użytkowników. Informacje o stanie zadania importu (w tym informacje o każdym importowanych plikach PST) są wyświetlane na stronie Importowanie plików **PST** w Centrum zgodności platformy Microsoft 365. Po zakończeniu zadania importu stan zadania ma ustawioną wartość **Ukończono**.

## <a name="why-import-email-data-to-microsoft-365"></a>Dlaczego warto importować dane poczty e-mail Microsoft 365?

- Jest to dobry sposób na zaimportowanie danych archiwalnych wiadomości organizacji w celu Microsoft 365.

- Funkcja inteligentnego importowania [umożliwia](filter-data-when-importing-pst-files.md) filtrowanie elementów w plikach PST, które w rzeczywistości są importowane do docelowych skrzynek pocztowych. Umożliwia to przycinanie importowanych danych przez ustawienie filtrów określających, które dane są importowane.

- Importowanie danych poczty e Microsoft 365 ułatwia spełnianie wymagań dotyczących zgodności w organizacji, pozwalając na:

  - Włącz [archiwalne skrzynki pocztowe](enable-archive-mailboxes.md) [i automatyczne rozszerzanie archiwizacji](autoexpanding-archiving.md) , aby zapewnić użytkownikom dodatkowe miejsce do magazynowania skrzynki pocztowej.

  - Umieszczaj skrzynki pocztowe [w postępowaniem sądowym w celu](./create-a-litigation-hold.md) zachowania zawartości.

  - Użyj narzędzia [Wyszukiwanie zawartości, aby](content-search.md) wyszukać zawartość skrzynki pocztowej.

  - Zarządzanie [dochodzeniami](./get-started-core-ediscovery.md) prawnie w organizacji za pomocą spraw zbierania elektronicznych materiałów dowodowych

  - Zasady [przechowywania w](retention.md) p Centrum zgodności platformy Microsoft 365 kontrolują, jak długo zawartość skrzynki pocztowej jest zachowywana, a następnie usuwana po wygaśnięciu okresu przechowywania.

  - Użyj [zasad zgodności komunikacji,](communication-compliance.md) aby zbadać wiadomości, aby upewnić się, że są one zgodne ze standardami wiadomości i dodać typ klasyfikacji.

- Importowanie danych do Microsoft 365 pozwala zabezpieczyć się przed utratą danych. Dane poczty e-mail, które są importowane Microsoft 365 dziedziczą funkcje wysokiej dostępności usługi Exchange Online.

- Dane poczty e-mail są dostępne dla użytkowników ze wszystkich urządzeń, ponieważ są przechowywane w chmurze.

## <a name="importing-sharepoint-data-to-microsoft-365"></a>Importowanie SharePoint danych do Microsoft 365

Możesz również importować pliki i dokumenty do witryn SharePoint i OneDrive kontach w organizacji. Aby uzyskać więcej informacji, zapoznaj się z następującymi artykułami:

- [Migrowanie do usługi SharePoint Online](/sharepointmigration/migrate-to-sharepoint-online)

- [Wprowadzenie do narzędzia SharePoint migracji](/sharepointmigration/introducing-the-sharepoint-migration-tool)

- [Migrowanie do SharePoint Online przy użyciu programu PowerShell](/sharepointmigration/overview-spmt-ps-cmdlets)

- [Migrowanie zawartości udziału plików do usługi SharePoint Online przy użyciu usługi Azure Data Box](/sharepointmigration/how-to-migrate-file-share-content-to-spo-using-azuredatabox)

## <a name="frequently-asked-questions-about-importing-pst-files"></a>Często zadawane pytania dotyczące importowania plików PST

Oto niektóre często zadawane pytania dotyczące używania usługi importowania Microsoft 365 do zbiorczego importowania plików PST do Microsoft 365 pocztowych.

- [Importowanie plików PST za pomocą przekazywania sieciowego](#using-network-upload-to-import-pst-files)

- [Importowanie plików PST za pomocą wysyłki dysków](#using-drive-shipping-to-import-pst-files)

### <a name="using-network-upload-to-import-pst-files"></a>Importowanie plików PST za pomocą przekazywania sieciowego

#### <a name="what-permissions-are-required-to-create-import-jobs-in-the-microsoft-365-import-service-using-network-upload"></a>Jakie uprawnienia są wymagane do tworzenia zadań importu w usłudze importowania Microsoft 365 przy użyciu przekazywania sieciowego?

Aby importować pliki Microsoft 365 PST do Exchange Online pocztowych, musisz mieć przypisaną rolę importowania i eksportowania skrzynek pocztowych Exchange Online pocztowe. Domyślnie ta rola nie jest przypisana do żadnej grupy ról w Exchange Online. Rolę importowania i eksportowania skrzynek pocztowych możesz dodać do grupy ról Zarządzanie organizacją. Możesz też utworzyć nową grupę ról, przypisać rolę importowania i eksportowania skrzynek pocztowych, a następnie dodać siebie lub innych użytkowników jako członków. Aby uzyskać więcej informacji, zobacz sekcje "Dodawanie roli do grupy ról" lub "Tworzenie grupy ról" w tece Zarządzanie grupami ról w [Exchange Online.](/Exchange/permissions-exo/role-groups)

Ponadto, aby tworzyć zadania importu w Centrum zgodności platformy Microsoft 365, musi być spełni jedna z następujących czynności:

- Musisz mieć przypisaną rolę adresatów poczty w Exchange Online. Domyślnie ta rola jest przypisana do grup ról Zarządzanie organizacją i Zarządzanie adresatami.

    Lub

- Musisz być administratorem globalnym w swojej organizacji.

> [!TIP]
> Rozważ utworzenie w programie Exchange Online grupy ról przeznaczonej specjalnie do importowania plików PST do Microsoft 365. Aby uzyskać minimalny poziom uprawnień wymaganych do importowania plików PST, przypisz role importowania i eksportowania skrzynek pocztowych oraz adresatów poczty do nowej grupy ról, a następnie dodaj do nich członków.

#### <a name="where-is-network-upload-available"></a>Gdzie jest dostępne przekazywanie sieciowe?

Przekazywanie sieciowe jest obecnie dostępne w tych regionach: Stany Zjednoczone, Kanada, Brazylia, Zjednoczone Królestwo, Francja, Niemcy, Szwajcaria, Norwegia, Europa, Europa, Indie, Azja Wschodnia, Azja Południowo-Wschodnia, Japonia, Republika Korei, Australia i Zjednoczone Emiraty Arabskie. Przekazywanie sieciowe będzie w przyszłości dostępne w większej liczby regionów.

#### <a name="what-is-the-pricing-for-importing-pst-files-by-using-network-upload"></a>Jaka jest cena za importowanie plików PST przy użyciu przekazywania sieciowego?

Importowanie plików PST za pomocą przekazywania sieciowego jest bezpłatne.

Oznacza to również, że po usunięciu plików PST z obszaru usługi Azure Storage nie są one już wyświetlane na liście plików dla ukończonego zadania importu w centrum [centrum administracyjne platformy Microsoft 365.](https://go.microsoft.com/fwlink/p/?linkid=2024339) Mimo że zadanie importu może być nadal wyświetlane na stronie  Importowanie danych do Microsoft 365, lista plików PST może być pusta, gdy wyświetlasz szczegóły starszych zadań importu.

#### <a name="what-version-of-the-pst-file-format-is-supported-for-importing-to-microsoft-365"></a>Która wersja formatu pliku PST jest obsługiwana na przykład w przypadku importowania do Microsoft 365?

Format pliku PST ma dwie wersje: ANSI i Unicode. Zalecamy importowanie plików w formacie PST Unicode. Jednak pliki w formacie PST ANSI, na przykład w przypadku języków o zestawach znaków dwu bajtowych (DBCS), również można importować do Microsoft 365. Aby uzyskać więcej informacji na temat importowania plików PST ANSI, zobacz krok 4 w tece Importowanie plików PST do importowania plików PST za pomocą przekazywania [sieciowego Microsoft 365](./use-network-upload-to-import-pst-files.md).

Ponadto do programu można importować pliki PST Outlook 2007 i nowszych wersjach Microsoft 365.

#### <a name="after-i-upload-my-pst-files-to-the-azure-storage-area-how-long-are-they-kept-in-azure-before-theyre-deleted"></a>Po przesłaniu plików PST do obszaru Storage Azure, jak długo są one przechowywane w usłudze Azure, zanim zostaną usunięte?

Gdy importujesz pliki PST przy użyciu metody przekazywania sieciowego, przekaż je do kontenera obiektów blob platformy Azure o nazwie `ingestiondata`. Jeśli na stronie Importowanie plików **PST** w aplikacji Centrum zgodności platformy Microsoft 365 nie ma zadań importu, wszystkie pliki PST `ingestiondata` w kontenerze na platformie Azure są usuwane 30 dni po utworzeniu ostatniego zadania importu w Centrum zgodności platformy Microsoft 365. Oznacza to również, że musisz utworzyć nowe zadanie importu w usłudze Centrum zgodności platformy Microsoft 365 (opisane w kroku 5 w instrukcjach dotyczących przekazywania sieci) w ciągu 30 dni od przekazania plików PST do platformy Azure.

Oznacza to również, że po usunięciu plików PST z obszaru usługi Azure Storage nie są one już wyświetlane na liście plików dla ukończonego zadania importu w centrum Centrum zgodności platformy Microsoft 365. Mimo że zadanie importu może być nadal wyświetlane na stronie Importowanie plików **PST** w programie Centrum zgodności platformy Microsoft 365, lista plików PST może być pusta, gdy wyświetlasz szczegóły starszych zadań importu.

#### <a name="how-long-does-it-take-to-import-a-pst-file-to-a-mailbox-using-network-upload"></a>Jak długo trwa importowanie pliku PST do skrzynki pocztowej przy użyciu przekazywania sieciowego?

Zależy to od wydajności sieci, ale zwykle każdy terabajt (TB) danych jest przekazywany do obszaru usługi Azure Storage organizacji po kilku godzinach. Po skopiowaniu plików PST do obszaru usługi Azure Storage plik PST jest importowany do skrzynki pocztowej usługi Microsoft 365 z szybkością około 24 GB na dzień<sup>\*</sup>. Jeśli ta szybkość nie spełnia wymagań, rozważ inne metody, aby pobrać dane poczty e-mail do Microsoft 365. Aby uzyskać więcej informacji, zobacz [Sposoby migrowania wielu kont e-mail do Microsoft 365](/Exchange/mailbox-migration/mailbox-migration).

Jeśli różne pliki PST są importowane do różnych docelowych skrzynek pocztowych, proces importowania odbywa się równolegle. Innymi słowy, każda para PLIK PST/skrzynka pocztowa jest importowana jednocześnie. Jeśli wiele plików PST zostanie zaimportowanych do tej samej skrzynki pocztowej, zostaną one zaimportowane sekwencyjnie (po kolei), nie jednocześnie.

> [!NOTE]
> <sup>\*</sup> Ta stopa nie jest gwarantowana. Obciążenie serwera i problemy przejściowych z wydajnością mogą zmniejszyć tę szybkość.

#### <a name="how-does-the-pst-import-process-handle-duplicate-email-items"></a>Jak proces importowania pliku PST obsługuje zduplikowane elementy poczty e-mail?

Proces importowania pliku PST sprawdza zduplikowane elementy i nie kopiuje elementów z pliku PST do skrzynki pocztowej lub archiwum, jeśli w folderze docelowym w docelowej skrzynce pocztowej lub archiwum docelowym istnieje pasujący element. Jeśli ponownie zaimportowano ten sam plik PST i określono inny folder docelowy (przy użyciu właściwości TargetRootFolder w pliku mapowania importu pliku PST) niż ten określony w poprzednim zadaniu importu, wszystkie elementy w pliku PST zostaną ponownie zaimportowane.

#### <a name="is-there-a-message-size-limit-when-importing-pst-files-using-network-upload"></a>Czy istnieje limit rozmiaru wiadomości podczas importowania plików PST przy użyciu przekazywania sieciowego?

Tak. Jeśli plik PST zawiera element skrzynki pocztowej o rozmiarze ponad 150 MB, ten element zostanie pominięty i nie zostanie zaimportowany w trakcie procesu importowania. Elementy o rozmiarze większym niż 150 MB nie są importowane, ponieważ 150 MB to limit rozmiaru wiadomości w Exchange Online. Aby uzyskać więcej informacji, zobacz [Limity wiadomości w Exchange Online](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#message-limits).

#### <a name="are-message-properties-such-as-when-the-message-was-sent-or-received-the-list-of-recipients-and-other-properties-preserved-when-pst-files-are-imported-to-a-microsoft-365-mailbox-using-network-upload"></a>Czy właściwości wiadomości, takie jak kiedy wiadomość została wysłana lub odebrana, lista adresatów i inne właściwości, są zachowywane, gdy pliki PST są importowane do skrzynki pocztowej programu Microsoft 365 przy użyciu przekazywania sieciowego?

Tak. Oryginalne metadane wiadomości nie są zmieniane w trakcie procesu importowania.

#### <a name="is-there-a-limit-to-the-number-of-levels-in-a-folder-hierarchy-for-a-pst-file-that-i-want-to-import-to-a-mailbox-using-network-upload"></a>Czy istnieje limit liczby poziomów w hierarchii folderów dla pliku PST, który chcę zaimportować do skrzynki pocztowej przy użyciu przekazywania sieciowego?

Tak. Nie można zaimportować pliku PST, który ma co najmniej 300 poziomów folderów zagnieżdżonych.

#### <a name="can-i-use-network-upload-to-import-pst-files-to-an-inactive-mailbox-in-microsoft-365"></a>Czy mogę używać przekazywania sieciowego do importowania plików PST do nieaktywnej skrzynki pocztowej w Microsoft 365?

Tak, ta funkcja jest teraz dostępna.

#### <a name="can-i-use-network-upload-to-import-pst-files-to-an-online-archive-mailbox-in-an-exchange-hybrid-deployment"></a>Czy mogę używać przekazywania sieciowego do importowania plików PST do skrzynki pocztowej archiwum online w Exchange hybrydowym?

Tak, ta funkcja jest teraz dostępna.

#### <a name="can-i-use-network-upload-to-import-pst-files-to-public-folders-in-exchange-online"></a>Czy mogę używać przekazywania sieciowego do importowania plików PST do folderów publicznych w programie Exchange Online?

Nie, nie można importować plików PST do folderów publicznych.

### <a name="using-drive-shipping-to-import-pst-files"></a>Importowanie plików PST za pomocą wysyłki dysków

#### <a name="what-permissions-are-required-to-create-import-jobs-in-the-microsoft-365-import-service-using-drive-shipping"></a>Jakie uprawnienia są wymagane do tworzenia zadań importu w usłudze importowania Microsoft 365 za pomocą wysyłki dysków?

Aby importować pliki Microsoft 365 PST do skrzynek pocztowych, musisz mieć przypisaną rolę importowania i eksportowania skrzynek pocztowych. Domyślnie ta rola nie jest przypisana do żadnej grupy ról w Exchange Online. Rolę importowania i eksportowania skrzynek pocztowych możesz dodać do grupy ról Zarządzanie organizacją. Możesz też utworzyć nową grupę ról, przypisać rolę importowania i eksportowania skrzynek pocztowych, a następnie dodać siebie lub innych użytkowników jako członków. Aby uzyskać więcej informacji, zobacz sekcje "Dodawanie roli do grupy ról" lub "Tworzenie grupy ról" w tece Zarządzanie grupami ról w [Exchange Online.](/Exchange/permissions-exo/role-groups)

Ponadto, aby tworzyć zadania importu w Centrum zgodności platformy Microsoft 365, musi być spełni jedna z następujących czynności:

- Musisz mieć przypisaną rolę adresatów poczty w Exchange Online. Domyślnie ta rola jest przypisana do grup ról Zarządzanie organizacją i Zarządzanie adresatami.

    Lub

- Musisz być administratorem globalnym w swojej organizacji.

> [!TIP]
> Rozważ utworzenie w programie Exchange Online grupy ról przeznaczonej specjalnie do importowania plików PST do Microsoft 365. Aby uzyskać minimalny poziom uprawnień wymaganych do importowania plików PST, przypisz role importowania i eksportowania skrzynek pocztowych oraz adresatów poczty do nowej grupy ról, a następnie dodaj do nich członków.

#### <a name="where-is-drive-shipping-available"></a>Gdzie jest dostępna wysyłka dysków?

Wysyłka dysków jest obecnie dostępna w Stanach Zjednoczonych, Kanadzie, Brazylii, Zjednoczonym Królestwie, Europie, Indiach, Azji Wschodniej, Azji Południowo-Wschodniej, Japonii, Republice Korei i Australii. Wysyłka dysków będzie dostępna w większej liczby regionów w przyszłości.

> [!NOTE]
> Obecnie wysyłka dysków w celu importowania plików PST nie jest dostępna w Niemczech i Szwajcarii. Te odpowiedzi na często zadawane pytania zostaną zaktualizowane, gdy wysyłka dysków będzie dostępna w tych krajach.

#### <a name="what-commercial-licensing-agreements-support-drive-shipping"></a>Jakie komercyjne umowy licencjonowania obsługują wysyłkę dysków?

Wysyłka dysków w celu zaimportowania plików PST Microsoft 365 jest dostępna za pośrednictwem Enterprise Agreement Microsoft (EA). Wysyłka dysków nie jest dostępna w ramach umowy Microsoft Products and Services Agreement (MPSA).

#### <a name="what-is-the-pricing-for-using-drive-shipping-to-import-pst-files-to-microsoft-365"></a>Jaka jest cena za używanie wysyłki dysków do importowania plików PST do Microsoft 365?

Koszt korzystania z wysyłki dysków do importowania plików PST do Microsoft 365 pocztowych wynosi 2 USD za jeden GB danych. Jeśli na przykład wysyłasz dysk twardy zawierający 1000 GB (1 TB) plików PST, koszt wynosi 2000 USD. Opłatę za importowanie możesz zapłacić we współpracy z partnerem. Aby uzyskać informacje na temat znajdowania partnera, [zobacz Znajdowanie partnera lub odsprzedawcy firmy Microsoft](../admin/manage/find-your-partner-or-reseller.md).

#### <a name="what-kind-of-hard-drives-are-supported-for-drive-shipping"></a>Jakiego rodzaju dyski twarde są obsługiwane na wysyłkę dysków?

Usługa importowania danych firmy Microsoft 365 obsługuje tylko dyski półprzewodnikowe (SSD) 2,5 cala albo wewnętrzne dyski twarde SATA II/III 2,5 cala lub 3,5 cala. Możesz korzystać z dysków twardych o pojemności do 10 TB. W przypadku zadań importu zostanie przetworzony tylko pierwszy wolumin danych na dysku twardym. Wolumin danych musi być sformatowany w systemie plików NTFS. Podczas kopiowania danych na dysk twardy możesz podłączyć go bezpośrednio za pomocą łącznika dysku SSD 2,5 cala albo SATA II/III 2,5 cala lub 3,5 cala. Możesz też podłączyć go zewnętrznie za pomocą zewnętrznego adaptera USB dysku SSD 2,5 cala albo SATA II/III 2,5 cala lub 3,5 cala.

> [!IMPORTANT]
> Zewnętrzne dyski twarde z wbudowaną kartą USB nie są obsługiwane przez usługę importowania danych Microsoft 365 importowania. Ponadto nie można używać dysku wewnątrz obudowy zewnętrznego dysku twardego. Prosimy nie wysyłać zewnętrznych dysków twardych.

#### <a name="how-many-hard-drives-can-i-ship-for-a-single-import-job"></a>Ile dysków twardych można wysłać w ramach jednego zadania importu?

Dla jednego zadania importu można wysłać maksymalnie 10 dysków twardych.

#### <a name="after-i-ship-my-hard-drive-how-long-does-it-take-to-get-to-the-microsoft-datacenter"></a>Ile czasu trwa dostęp do centrum danych firmy Microsoft po wysłaniu dysku twardego?

Zależy to od kilku czynników, takich jak odległość od centrum danych firmy Microsoft i rodzaj opcji wysyłki użytej do wysłania dysku twardego (na przykład dostawa w następnym dniu, dostawa w ciągu dwóch dni lub dostawa lądowa). W przypadku większości spedytorów do śledzenia stanu dostawy można użyć numeru śledzenia.

#### <a name="after-my-hard-drive-arrives-at-the-microsoft-datacenter-how-long-does-it-take-to-upload-my-pst-files-to-azure"></a>Ile czasu trwa przekazanie plików PST do platformy Azure, gdy dysk twardy pojawi się w centrum danych firmy Microsoft?

Po otrzymaniu dysku twardego w centrum danych firmy Microsoft przekazanie plików PST do lokalizacji usługi Azure Storage organizacji może potrwać od 7 do 10 dni roboczych. Pliki PST zostaną przekazane do kontenera obiektów blob platformy Azure o nazwie `ingestiondata`.

#### <a name="how-long-does-it-take-to-import-a-pst-file-to-a-mailbox-using-drive-shipping"></a>Jak długo trwa importowanie pliku PST do skrzynki pocztowej przy użyciu wysyłki dysków?

Po przekazeniu plików PST do obszaru usługi Azure Storage program Microsoft 365 analizuje dane w plikach PST (w bezpieczny sposób) w celu zidentyfikowania wieku elementów i różnych typów wiadomości zawartych w plikach PST. Po zakończeniu tej analizy będziesz mieć możliwość zaimportowania wszystkich danych z plików PST lub ustawienia filtrów w celu kontrolowania tego, jakie dane są importowane. Po uruchomieniu zadania importu plik PST jest importowany do skrzynki Microsoft 365 pocztowej z około 24 GB na dzień.<sup>\*</sup> Jeśli ta szybkość nie spełnia wymagań, rozważ inne metody, aby pobrać dane poczty e-mail do Microsoft 365. Aby uzyskać więcej informacji, zobacz [Sposoby migrowania wielu kont e-mail do Microsoft 365](/Exchange/mailbox-migration/mailbox-migration).

Jeśli różne pliki PST są importowane do różnych docelowych skrzynek pocztowych, proces importowania odbywa się równolegle. Innymi słowy, każda para PLIK PST/skrzynka pocztowa jest importowana jednocześnie. Jeśli wiele plików PST zostanie zaimportowanych do tej samej skrzynki pocztowej, zostaną one zaimportowane sekwencyjnie (po kolei), nie jednocześnie.

> [!NOTE]
> <sup>\*</sup> Ta stopa nie jest gwarantowana. Obciążenie serwera i problemy przejściowych z wydajnością mogą zmniejszyć tę szybkość.

#### <a name="after-microsoft-uploads-my-pst-files-to-azure-how-long-are-they-kept-in-azure-before-theyre-deleted"></a>Kiedy firma Microsoft przekaże moje pliki PST do platformy Azure, jak długo są one przechowywane na platformie Azure, zanim zostaną usunięte?

Wszystkie pliki PST w lokalizacji usługi Azure Storage organizacji (w kontenerze obiektów blob `ingestiondata`o nazwie ), są usuwane 30 dni po utworzeniu najnowszego zadania importu na stronie Importowanie plików **PST** w Centrum zgodności platformy Microsoft 365.

Oznacza to również, że po usunięciu plików PST z obszaru usługi Azure Storage nie są one już wyświetlane na liście plików dla ukończonego zadania importu w centrum Centrum zgodności platformy Microsoft 365. Mimo że zadanie importu może być nadal wyświetlane na stronie Importowanie plików **PST** w programie Centrum zgodności platformy Microsoft 365, lista plików PST może być pusta, gdy wyświetlasz szczegóły starszych zadań importu.

#### <a name="what-version-of-the-pst-file-format-is-supported-for-importing-to-microsoft-365"></a>Która wersja formatu pliku PST jest obsługiwana na przykład w przypadku importowania do Microsoft 365?

Format pliku PST ma dwie wersje: ANSI i Unicode. Zalecamy importowanie plików w formacie PST Unicode. Jednak pliki w formacie PST ANSI, na przykład w przypadku języków o zestawach znaków dwu bajtowych (DBCS), również można importować do Microsoft 365. Aby uzyskać więcej informacji na temat importowania plików PST ANSI, zobacz krok 3 w tece Importowanie plików [PST organizacji](use-drive-shipping-to-import-pst-files-to-office-365.md#step-3-create-the-pst-import-mapping-file) do programu Microsoft 365.

Ponadto do programu można importować pliki PST Outlook 2007 i nowszych wersjach Microsoft 365.

#### <a name="is-there-a-message-size-limit-when-importing-pst-files-using-drive-shipping"></a>Czy istnieje limit rozmiaru wiadomości podczas importowania plików PST za pomocą wysyłki dysków?

Tak. Jeśli plik PST zawiera element skrzynki pocztowej o rozmiarze ponad 150 MB, ten element zostanie pominięty i nie zostanie zaimportowany w trakcie procesu importowania. Elementy o rozmiarze większym niż 150 MB nie są importowane, ponieważ 150 MB to limit rozmiaru wiadomości w Exchange Online. Aby uzyskać więcej informacji, zobacz [Limity wiadomości w Exchange Online](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#message-limits).

  **Jak proces importowania pliku PST obsługuje zduplikowane elementy poczty e-mail?

Proces importowania pliku PST sprawdza zduplikowane elementy i nie kopiuje elementów z pliku PST do skrzynki pocztowej lub archiwum, jeśli w folderze docelowym w docelowej skrzynce pocztowej lub archiwum docelowym istnieje pasujący element. Jeśli ponownie zaimportowano ten sam plik PST i określono inny folder docelowy (przy użyciu właściwości TargetRootFolder w pliku mapowania importu pliku PST) niż ten określony w poprzednim zadaniu importu, wszystkie elementy w pliku PST zostaną ponownie zaimportowane.

#### <a name="are-message-properties-such-as-when-the-message-was-sent-or-received-the-list-of-recipients-and-other-properties-preserved-when-pst-files-are-imported-to-a-microsoft-365-mailbox-using-drive-shipping"></a>Czy właściwości wiadomości, takie jak kiedy wiadomość została wysłana lub odebrana, lista adresatów i inne właściwości, są zachowywane podczas importowania plików PST do skrzynki pocztowej programu Microsoft 365 za pomocą wysyłki dysków?

Tak. Oryginalne metadane wiadomości nie są zmieniane w trakcie procesu importowania

#### <a name="is-there-a-limit-to-the-number-of-levels-in-a-folder-hierarchy-for-a-pst-file-that-i-want-to-import-to-a-mailbox-using-drive-shipping"></a>Czy istnieje limit liczby poziomów w hierarchii folderów dla pliku PST, który chcę zaimportować do skrzynki pocztowej za pomocą wysyłki dysków?

Tak. Nie można zaimportować pliku PST, który ma co najmniej 300 poziomów folderów zagnieżdżonych.

#### <a name="can-i-use-drive-shipping-to-import-pst-files-to-an-inactive-mailbox-in-microsoft-365"></a>Czy mogę używać wysyłki dysków do importowania plików PST do nieaktywnej skrzynki pocztowej w Microsoft 365?

Tak, ta funkcja jest teraz dostępna.

#### <a name="can-i-use-drive-shipping-to-import-pst-files-to-an-online-archive-mailbox-in-an-exchange-hybrid-deployment"></a>Czy mogę używać wysyłki dysków do importowania plików PST do skrzynki pocztowej archiwum online w Exchange hybrydowym?

Tak, ta funkcja jest teraz dostępna.

#### <a name="can-i-use-drive-shipping-to-import-pst-files-to-public-folders-in-exchange-online"></a>Czy mogę używać wysyłki dysków do importowania plików PST do folderów publicznych w Exchange Online?

Nie, nie można importować plików PST do folderów publicznych.

#### <a name="can-microsoft-wipe-my-hard-drive-before-they-ship-it-back-to-me"></a>Czy firma Microsoft może wyczyścić mój dysk twardy przed wysyłką z powrotem do mnie?

Nie, firma Microsoft nie może wyczyścić dysków twardych przed wysyłką ich z powrotem do klientów. Dyski twarde są zwracane w tym samym stanie, w którym zostały otrzymane przez firmę Microsoft.

#### <a name="can-microsoft-shred-my-hard-drive-instead-of-shipping-it-back-to-me"></a>Czy firma Microsoft może wyniszczać mój dysk twardy zamiast wysyłać go z powrotem do mnie?

Nie, firma Microsoft nie może zniszczyć Twojego dysku twardego. Dyski twarde są zwracane w tym samym stanie, w którym zostały otrzymane przez firmę Microsoft.

#### <a name="what-courier-services-are-supported-for-return-shipping"></a>Jakie usługi kurierskie są obsługiwane w przypadku wysyłki zwrotów?

Jeśli jesteś klientem w Stanach Zjednoczonych lub w Europie, firma Microsoft korzysta z usług firmy FedEx do zwracania dysków twardych. We wszystkich innych regionach firma Microsoft korzysta z usług firmy DHL.

#### <a name="what-are-the-return-shipping-costs"></a>Jakie są koszty wysyłki zwrotu?

Koszty wysyłki zwrotu różnią się w zależności od Twojej odległości od centrum danych firmy Microsoft, do których wysłano dysk twardy. Firma Microsoft nalicza rachunek za zwrot dysku twardego twoje konto w firmie FedEx lub DHL. Ty ponosisz koszt wysyłki zwrotu.

#### <a name="can-i-use-a-custom-courier-shipping-service-such-as-fedex-custom-shipping-to-ship-my-hard-drive-to-microsoft"></a>Czy mogę wysłać dysk twardy do firmy Microsoft za pomocą niestandardowej usługi wysyłki kurierskiej, takiej jak FedEx Custom Shipping?

Tak.

#### <a name="if-i-have-to-ship-my-hard-drive-to-another-country-is-there-anything-i-need-to-do"></a>Jeśli muszę wysłać dysk twardy do innego kraju, czy muszę coś zrobić?

Dysk twardy, który wysyłasz do firmy Microsoft, może być konieczne przekroowanie granic międzynarodowych. Jeśli tak, ponosisz odpowiedzialność za zapewnienie, że dysk twardy i jego dane są importowane i/lub eksportowane zgodnie z obowiązującymi przepisami prawa. Przed wysyłką dysku twardego skontaktuj się z doradcami, aby upewnić się, że dysk i dane można legalnie wysłać do określonego centrum danych firmy Microsoft. Pozwoli to zapewnić terminowe dotarcie do firmy Microsoft.
