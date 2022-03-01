---
title: Odszyfrowywanie w zbierania elektronicznych materiałów dowodowych
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.custom:
- seo-marvel-apr2020
description: Dowiedz się, Microsoft 365 narzędzi zbierania elektronicznych materiałów dowodowych obsługują zaszyfrowane dokumenty dołączone do wiadomości e-mail i przechowywane w usługach SharePoint Online i OneDrive dla Firm.
ms.openlocfilehash: aa6d6a72353378f98b9e567500233b4c26f6221c
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/12/2022
ms.locfileid: "63021234"
---
# <a name="decryption-in-microsoft-365-ediscovery-tools"></a>Odszyfrowywanie w Microsoft 365 zbierania elektronicznych materiałów dowodowych

Szyfrowanie jest ważną częścią strategii ochrony plików i ochrony informacji. Organizacje wszystkich typów korzystają z technologii szyfrowania w celu ochrony poufnej zawartości w organizacji i zapewnienia, że tylko odpowiednie osoby mają do nich dostęp.

Aby wykonywać typowe zadania zbierania elektronicznych materiałów dowodowych na zaszyfrowanej zawartości, menedżerowie zbierania elektronicznych materiałów dowodowych byli zobowiązani do odszyfrowywania zawartości wiadomości e-mail, ponieważ była eksportowana z przeszukiwania zawartości, podstawowych spraw zbierania elektronicznych materiałów dowodowych Advanced eDiscovery sprawy. Zawartość zaszyfrowana przy użyciu technologii szyfrowania firmy Microsoft nie była dostępna do przeglądu, dopóki nie została wyeksportowana.

Aby ułatwić zarządzanie zaszyfrowaną zawartością w przepływie pracy zbierania elektronicznych materiałów dowodowych, narzędzia zbierania elektronicznych materiałów dowodowych Microsoft 365 teraz zawierają odszyfrowywanie plików dołączonych do wiadomości e-mail i wysyłanych w Exchange Online.<sup> 1</sup> Ponadto zaszyfrowane dokumenty przechowywane w u SharePoint Online i OneDrive dla Firm odszyfrowywać w Advanced eDiscovery.

Przed rozpoczęciem tej nowej funkcji odszyfrowywać była tylko zawartość wiadomości e-mail chronionych za pomocą zarządzania prawami (a nie dołączonymi plikami). Zaszyfrowanych dokumentów w SharePoint i OneDrive nie można odszyfrować podczas przepływu pracy zbierania elektronicznych materiałów dowodowych. Teraz pliki, które są szyfrowane za pomocą technologii szyfrowania firmy Microsoft, znajdują się na koncie programu SharePoint lub OneDrive, można je przeszukiwać i odszyfrowywać, gdy wyniki wyszukiwania są przygotowane do podglądu, dodawane do zestawu recenzji w programie Advanced eDiscovery i eksportowane. Dodatkowo można wyszukiwać zaszyfrowane dokumenty SharePoint OneDrive dołączonych do wiadomości e-mail. Ta funkcja odszyfrowywania umożliwia menedżerom zbierania elektronicznych materiałów dowodowych wyświetlanie zawartości zaszyfrowanych załączników wiadomości e-mail i dokumentów witryny podczas wyświetlania podglądu wyników wyszukiwania oraz przeglądanie ich po ich dodaniu do zestawu recenzji w programie Advanced eDiscovery.

## <a name="supported-encryption-technologies"></a>Obsługiwane technologie szyfrowania

Narzędzia zbierania elektronicznych materiałów dowodowych firmy Microsoft obsługują elementy zaszyfrowane za pomocą technologii szyfrowania firmy Microsoft. Te technologie to usługa Azure Rights Management i Microsoft Information Protection (w szczególności etykiety wrażliwości). Aby uzyskać więcej informacji o technologiach szyfrowania firmy Microsoft, zobacz [Szyfrowanie](encryption.md). Zawartość zaszyfrowana przez technologie szyfrowania innych firm nie jest obsługiwana. Na przykład wyświetlanie podglądu lub eksportowanie zawartości zaszyfrowanej za pomocą technologii innych niż firmy Microsoft nie jest obsługiwane.

> [!NOTE]
> Odszyfrowywanie wiadomości e-mail wysyłanych za [pomocą Szyfrowanie wiadomości usługi Office 365 niestandardowych brandingów OME](add-your-organization-brand-to-encrypted-messages.md) nie jest obsługiwane przez narzędzia zbierania elektronicznych materiałów dowodowych firmy Microsoft. W przypadku używania niestandardowego szablonu  marki OME wiadomości e-mail są dostarczane do portalu OME, a nie do skrzynki pocztowej adresata. Dlatego nie będzie można używać narzędzi zbierania elektronicznych materiałów dowodowych do wyszukiwania wiadomości zaszyfrowanych za pomocą narzędzia OME, ponieważ te wiadomości nigdy nie są odbierane przez skrzynkę pocztową adresata.

## <a name="ediscovery-activities-that-support-encrypted-items"></a>Działania zbierania elektronicznych materiałów dowodowych, które obsługują zaszyfrowane elementy

W poniższej tabeli przedstawiono obsługiwane zadania, które można wykonywać w narzędziach zbierania elektronicznych materiałów dowodowych w zaszyfrowanych plikach dołączonych do wiadomości e-mail i zaszyfrowanych dokumentach w usługach Microsoft 365 SharePoint i OneDrive. Te obsługiwane zadania można wykonywać w zaszyfrowanych plikach, które spełniają kryteria wyszukiwania. Wartość oznacza `N/A` , że funkcja nie jest dostępna w odpowiednim narzędziu zbierania elektronicznych materiałów dowodowych.

|Zadanie zbierania elektronicznych materiałów dowodowych  |Przeszukiwanie zawartości  |Core eDiscovery  |Advanced eDiscovery  |
|:---------|:---------|:---------|:---------|
|Wyszukiwanie zawartości w zaszyfrowanych plikach w witrynach i<sup></sup> załącznikach wiadomości e-mail1     |Nie      |Nie      |Tak      |
|Wyświetlanie podglądu zaszyfrowanych plików dołączonych do wiadomości e-mail     |Tak      |Tak     |Tak       |
|Wyświetlanie podglądu zaszyfrowanych dokumentów SharePoint i OneDrive|Nie      |Nie    |Tak       |
|Przeglądanie zaszyfrowanych plików w zestawie recenzji    |nd.      |nd.        | Tak        |
|Eksportowanie zaszyfrowanych plików dołączonych do wiadomości e-mail    |Tak       |Tak  |Tak    |
|Eksportowanie zaszyfrowanych dokumentów SharePoint i OneDrive    |Nie       |Nie  |Tak    |
|||||

> [!NOTE]
> <sup>1</sup> Zaszyfrowane pliki znajdujące się na komputerze lokalnym i załączniki w chmurze skopiowane do wiadomości e-mail nie są odszyfrowywać i indeksowane na potrzeby zbierania elektronicznych materiałów dowodowych. Aby uzyskać więcej informacji i obejście dla tych scenariuszy, [zobacz sekcję](#decryption-limitations-with-email-attachments) Ograniczenia odszyfrowywania z załącznikami wiadomości e-mail w tym artykule.

## <a name="decryption-limitations-with-sensitivity-labels-in-sharepoint-and-onedrive"></a>Ograniczenia odszyfrowywania z etykietami wrażliwości SharePoint i OneDrive

Zbierania elektronicznych materiałów dowodowych nie obsługuje plików zaszyfrowanych w usługach SharePoint i OneDrive, gdy etykieta wrażliwości, która ma zastosowane szyfrowanie, jest skonfigurowana przy użyciu jednego z następujących ustawień:

- Użytkownicy mogą przypisywać uprawnienia, gdy ręcznie zastosują etykietę do dokumentu. Te uprawnienia są czasami nazywane *uprawnieniami zdefiniowanymi przez użytkownika*.

- Dla dostępu użytkownika do dokumentu jest dostępne ustawienie wygasania, które jest ustawione na wartość inną niż **Nigdy**.

Aby uzyskać więcej informacji o tych ustawieniach, zobacz sekcję "Konfigurowanie ustawień szyfrowania" w sekcji Ograniczanie dostępu do zawartości przy użyciu etykiet wrażliwości w celu [zastosowania szyfrowania](encryption-sensitivity-labels.md#configure-encryption-settings).

Dokumenty zaszyfrowane poprzednimi ustawieniami nadal mogą być zwracane przez wyszukiwanie zbierania elektronicznych materiałów dowodowych. Może się tak zdarzyć, gdy właściwość dokumentu (taka jak tytuł, autor lub data modyfikacji) odpowiada kryteriom wyszukiwania. Mimo że te dokumenty mogą zostać uwzględnione w wynikach wyszukiwania, nie można ich przeglądać ani wyświetlać ich podglądu. Te dokumenty również pozostaną zaszyfrowane podczas ich eksportowania za pomocą Advanced eDiscovery.

> [!IMPORTANT]
> Odszyfrowywanie nie jest obsługiwane w przypadku plików, które są szyfrowane lokalnie, a następnie przekazywane SharePoint lub OneDrive. Na przykład pliki lokalne, które są szyfrowane przez klienta usługi Azure Information Protection (AIP), a następnie przekazywane Microsoft 365 nie są obsługiwane. Do odszyfrowywania są obsługiwane tylko pliki SharePoint lub OneDrive, które są szyfrowane.

## <a name="decryption-limitations-with-email-attachments"></a>Ograniczenia odszyfrowywania z załącznikami wiadomości e-mail

W poniższych scenariuszach opisano ograniczenia dotyczące odszyfrowywania plików dołączonych do wiadomości e-mail. Opisy tych scenariuszy zawierają również obejścia tych ograniczeń.

- Jeśli do wiadomości e-mail został dołączony plik znajdujący się na komputerze lokalnym (a nie w witrynie programu SharePoint lub koncie programu OneDrive), a do wiadomości e-mail jest stosowana etykieta wrażliwości, która stosuje szyfrowanie, dołączony plik nie może zostać odszyfrowany przez usługę eDiscovery. Oznacza to, że po uruchomieniu zapytania wyszukiwania słów kluczowych skrzynki pocztowej adresata zaszyfrowany załącznik pliku nie zostanie zwrócony przez zapytanie wyszukiwania słów kluczowych.

  Obejściem tego ograniczenia jest przeszukanie skrzynki pocztowej nadawcy pod taki sam załącznik plików. Jest tak, ponieważ szyfrowanie stosowane na etykiecie wrażliwości jest stosowane podczas transportu wiadomości e-mail. Oznacza to, że załącznik jest zaszyfrowany po wysłaniu wiadomości e-mail. Wynikiem jest wystąpienie dołączonego pliku w skrzynce pocztowej nadawcy niezaszyfrowane, mimo że ten sam plik w skrzynce pocztowej adresata jest zaszyfrowany.

- Podobnie, nie można odszyfrowywać załączników w chmurze (plików przechowywanych w witrynie programu SharePoint lub koncie programu OneDrive) skopiowanych do wiadomości e-mail (przy użyciu opcji Dołącz jako kopię w programie Outlook) przez usługę eDiscovery. Dzieje się tak również dlatego, że podczas wysłania wiadomości e-mail jest stosowane szyfrowanie stosowane przez etykietę wrażliwości. Obejściem tego ograniczenia jest również wyszukiwanie w skrzynce pocztowej nadawcy nieszyfrowanego wystąpienia kopii załącznika w chmurze.

W obu tych scenariuszach wiadomości e-mail z zaszyfrowanymi plikami załączników mogą być zwracane przez wyszukiwanie zbierania elektronicznych materiałów dowodowych, jeśli właściwość poczty e-mail (taka jak data wysłania, nadawca, adresat lub temat) pasuje do zapytania wyszukiwania.

## <a name="requirements-for-decryption-in-ediscovery"></a>Wymagania dotyczące odszyfrowywania w zbierania elektronicznych materiałów dowodowych

Aby wyświetlać, przeglądać i eksportować pliki szyfrowane przy użyciu technologii szyfrowania firmy Microsoft, musisz mieć przypisaną rolę odszyfrowywania usługi RMS. Ta rola musi być też przypisana do przeglądania i szyfrowania plików zapytań dodawanych do zestawu recenzji w aplikacji Advanced eDiscovery.

Ta rola jest domyślnie przypisana do grupy ról Menedżer zbierania elektronicznych materiałów dowodowych **na stronie** Uprawnienia w Centrum zgodności platformy Microsoft 365. Aby uzyskać więcej informacji na temat roli odszyfrowywania usługi RMS, zobacz [Przypisywanie uprawnień zbierania elektronicznych materiałów dowodowych](assign-ediscovery-permissions.md#rms-decrypt).

### <a name="decrypting-rms-protected-email-messages-and-encrypted-file-attachments-using-content-search-or-core-ediscovery"></a>Odszyfrowywanie wiadomości e-mail chronionych usługą RMS i zaszyfrowanych załączników plików przy użyciu wyszukiwania zawartości lub podstawowego zbierania elektronicznych materiałów dowodowych

Wszelkie wiadomości e-mail chronione prawami (chronione przez usługę RMS) zawarte w wynikach wyszukiwania zawartości będą odszyfrowywać podczas eksportowania. Ponadto każdy plik, który jest zaszyfrowany przy użyciu technologii szyfrowania [firmy Microsoft](encryption.md) i dołączony do wiadomości e-mail dołączonej do wyników wyszukiwania, zostanie odszyfrowany podczas eksportowania. Ta funkcja odszyfrowywania jest domyślnie włączona dla członków grupy ról Menedżera zbierania elektronicznych materiałów dowodowych. Jest tak, ponieważ do tej grupy ról jest domyślnie przypisana rola zarządzania odszyfrowywaniem usługi RMS. Podczas eksportowania zaszyfrowanych wiadomości e-mail i załączników należy pamiętać o następujących kwestiach:
  
- Jak wyjaśniono wcześniej, aby podczas eksportowania odszyfrowywać wiadomości chronione przez usługę RMS, należy wyeksportować wyniki wyszukiwania jako pojedyncze wiadomości. W przypadku eksportowania wyników wyszukiwania do pliku PST wiadomości chronione przez usługę RMS będą szyfrowane.

- Odszyfrowane wiadomości są identyfikowane w **raporcie ResultsLog** . Ten raport zawiera kolumnę o nazwie **Stan dekodowania**, a wartość w kolumnie **Dekodowane** identyfikuje wiadomości, które zostały odszyfrowane.

- Oprócz odszyfrowywania załączników plików podczas eksportowania wyników wyszukiwania możesz także wyświetlić podgląd odszyfrowany plik podczas wyświetlania podglądu wyników wyszukiwania. Wiadomość e-mail, która jest chroniona prawami dostępu, jest dostępna tylko po jej wyeksportowaniu.

- Jeśli chcesz uniemożliwić odszyfrowywanie wiadomości z ochroną usługi RMS i zaszyfrowanych załączników plików, musisz utworzyć niestandardową grupę ról (przez skopiowanie wbudowanej grupy ról Menedżera zbierania elektronicznych materiałów dowodowych), a następnie usunąć rolę zarządzania odszyfrowywaniem usługi RMS z niestandardowej grupy ról. Następnie dodaj osobę, która nie ma odszyfrowywać wiadomości jako członka niestandardowej grupy ról.
