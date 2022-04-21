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
description: Dowiedz się, jak narzędzia zbierania elektronicznych materiałów dowodowych Microsoft 365 obsługują zaszyfrowane dokumenty dołączone do wiadomości e-mail i przechowywane w usłudze SharePoint Online i OneDrive dla Firm.
ms.openlocfilehash: e010ef1ff169467b442e137bc31d3640aa5a8cb4
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2022
ms.locfileid: "64994460"
---
# <a name="decryption-in-microsoft-365-ediscovery-tools"></a>Odszyfrowywanie w narzędziach Microsoft 365 eDiscovery

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Szyfrowanie jest ważną częścią strategii ochrony plików i ochrony informacji. Organizacje wszystkich typów używają technologii szyfrowania, aby chronić poufne treści w organizacji i zapewnić, że tylko odpowiednie osoby mają dostęp do tej zawartości.

Aby wykonać typowe zadania zbierania elektronicznych materiałów dowodowych w zaszyfrowanej zawartości, menedżerowie zbierania elektronicznych materiałów dowodowych musieli odszyfrować zawartość wiadomości e-mail, ponieważ została wyeksportowana z wyszukiwań zawartości, przypadków zbierania elektronicznych materiałów dowodowych w usłudze Microsoft Purview (standardowa) i przypadków zbierania elektronicznych materiałów dowodowych w usłudze Microsoft Purview (Premium). Zawartość zaszyfrowana przy użyciu technologii szyfrowania firmy Microsoft była dostępna do przeglądu dopiero po jej wyeksportowaniu.

Aby ułatwić zarządzanie zaszyfrowaną zawartością w przepływie pracy zbierania elektronicznych materiałów dowodowych, narzędzia Microsoft 365 zbierania elektronicznych materiałów dowodowych zawierają teraz odszyfrowywanie zaszyfrowanych plików dołączonych do wiadomości e-mail i wysyłanych w Exchange Online.<sup> 1</sup> Ponadto zaszyfrowane dokumenty przechowywane w usłudze SharePoint Online i OneDrive dla Firm są odszyfrowywane w ramach zbierania elektronicznych materiałów dowodowych (Premium).

Przed tą nową funkcją odszyfrowano tylko zawartość wiadomości e-mail chronionej przez zarządzanie prawami (a nie dołączone pliki). Nie można odszyfrować zaszyfrowanych dokumentów w SharePoint i OneDrive podczas przepływu pracy zbierania elektronicznych materiałów dowodowych. Teraz pliki zaszyfrowane za pomocą technologii szyfrowania firmy Microsoft znajdują się na koncie SharePoint lub OneDrive są przeszukiwane i odszyfrowywane, gdy wyniki wyszukiwania są przygotowywane do wersji zapoznawczej, dodawane do zestawu przeglądów zbierania elektronicznych materiałów dowodowych (Premium) i eksportowane. Ponadto można wyszukiwać zaszyfrowane dokumenty w SharePoint i OneDrive dołączone do wiadomości e-mail. Ta funkcja odszyfrowywania umożliwia menedżerom zbierania elektronicznych materiałów dowodowych wyświetlanie zawartości zaszyfrowanych załączników wiadomości e-mail i dokumentów witryny podczas przeglądania wyników wyszukiwania i przeglądanie ich po dodaniu ich do zestawu przeglądów w obszarze Zbierania elektronicznych materiałów dowodowych (Premium).

## <a name="supported-encryption-technologies"></a>Obsługiwane technologie szyfrowania

Narzędzia zbierania elektronicznych materiałów dowodowych firmy Microsoft obsługują elementy zaszyfrowane przy użyciu technologii szyfrowania firmy Microsoft. Te technologie to Azure Rights Management i Microsoft Purview Information Protection (w szczególności etykiety poufności). Aby uzyskać więcej informacji na temat technologii szyfrowania firmy Microsoft, zobacz [Szyfrowanie](encryption.md). Zawartość szyfrowana za pomocą technologii szyfrowania innych firm nie jest obsługiwana. Na przykład podgląd lub eksportowanie zawartości zaszyfrowanej przy użyciu technologii innych niż Microsoft nie jest obsługiwane.

> [!NOTE]
> Odszyfrowywanie wiadomości e-mail wysyłanych za pomocą [niestandardowego szablonu znakowania szyfrowania komunikatów usługi Microsoft Purview](add-your-organization-brand-to-encrypted-messages.md) nie jest obsługiwane przez narzędzia zbierania elektronicznych materiałów dowodowych firmy Microsoft. W przypadku korzystania z niestandardowego szablonu znakowania OME wiadomości e-mail są dostarczane do portalu OME zamiast do skrzynki pocztowej adresata. W związku z tym nie będzie można wyszukiwać zaszyfrowanych wiadomości za pomocą narzędzi zbierania elektronicznych materiałów dowodowych, ponieważ te wiadomości nigdy nie są odbierane przez skrzynkę pocztową adresata.

## <a name="ediscovery-activities-that-support-encrypted-items"></a>Działania zbierania elektronicznych materiałów dowodowych, które obsługują zaszyfrowane elementy

W poniższej tabeli przedstawiono obsługiwane zadania, które mogą być wykonywane w narzędziach Microsoft 365 eDiscovery na zaszyfrowanych plikach dołączonych do wiadomości e-mail i zaszyfrowanych dokumentów w SharePoint i OneDrive. Te obsługiwane zadania można wykonywać na zaszyfrowanych plikach, które spełniają kryteria wyszukiwania. Wartość `N/A` wskazuje, że funkcja nie jest dostępna w odpowiednim narzędziu do zbierania elektronicznych materiałów dowodowych.

|Zadanie zbierania elektronicznych materiałów dowodowych  |Wyszukiwanie zawartości  |Zbieranie elektronicznych materiałów dowodowych w warstwie Standardowa  |Zbieranie elektronicznych materiałów dowodowych (Premium)  |
|:---------|:---------|:---------|:---------|
|Wyszukiwanie zawartości w zaszyfrowanych plikach w witrynach<sup></sup> i załącznikach wiadomości e-mail1     |Nie      |Nie      |Tak      |
|Podgląd zaszyfrowanych plików dołączonych do poczty e-mail     |Tak      |Tak     |Tak       |
|Podgląd zaszyfrowanych dokumentów w SharePoint i OneDrive|Nie      |Nie    |Tak       |
|Przeglądanie zaszyfrowanych plików w zestawie przeglądów    |nd.      |nd.        | Tak        |
|Eksportowanie zaszyfrowanych plików dołączonych do poczty e-mail    |Tak       |Tak  |Tak    |
|Eksportowanie zaszyfrowanych dokumentów w SharePoint i OneDrive    |Nie       |Nie  |Tak    |
|||||

> [!NOTE]
> <sup>1</sup> Zaszyfrowane pliki znajdujące się na komputerze lokalnym i w chmurze załączniki skopiowane do wiadomości e-mail nie są odszyfrowywane i indeksowane na potrzeby zbierania elektronicznych materiałów dowodowych. Aby uzyskać więcej informacji i obejść te scenariusze, zobacz sekcję [Ograniczenia odszyfrowywania z załącznikami wiadomości e-mail](#decryption-limitations-with-email-attachments) w tym artykule.

## <a name="decryption-limitations-with-sensitivity-labels-in-sharepoint-and-onedrive"></a>Ograniczenia odszyfrowywania etykiet poufności w SharePoint i OneDrive

Funkcja zbierania elektronicznych materiałów dowodowych nie obsługuje zaszyfrowanych plików w SharePoint i OneDrive, gdy etykieta poufności, która zastosowała szyfrowanie, jest skonfigurowana przy użyciu jednego z następujących ustawień:

- Użytkownicy mogą przypisywać uprawnienia, gdy ręcznie zastosują etykietę do dokumentu. Jest to czasami *określane jako uprawnienia zdefiniowane przez użytkownika*.

- Dostęp użytkownika do dokumentu ma ustawienie wygaśnięcia, które jest ustawione na wartość inną niż **Nigdy**.

Aby uzyskać więcej informacji na temat tych ustawień, zobacz sekcję "Konfigurowanie ustawień szyfrowania" w [temacie Ograniczanie dostępu do zawartości przy użyciu etykiet poufności w celu zastosowania szyfrowania](encryption-sensitivity-labels.md#configure-encryption-settings).

Dokumenty zaszyfrowane przy użyciu poprzednich ustawień mogą być nadal zwracane przez wyszukiwanie zbierania elektronicznych materiałów dowodowych. Może się tak zdarzyć, gdy właściwość dokumentu (na przykład tytuł, autor lub data modyfikacji) jest zgodna z kryteriami wyszukiwania. Chociaż te dokumenty mogą zostać uwzględnione w wynikach wyszukiwania, nie mogą być przeglądane ani przeglądane. Te dokumenty pozostaną również zaszyfrowane, gdy zostaną wyeksportowane w ramach zbierania elektronicznych materiałów dowodowych (Premium).

> [!IMPORTANT]
> Odszyfrowywanie nie jest obsługiwane w przypadku plików, które są szyfrowane lokalnie, a następnie przekazywane do SharePoint lub OneDrive. Na przykład pliki lokalne, które są szyfrowane przez klienta usługi Azure Information Protection (AIP), a następnie przekazywane do Microsoft 365, nie są obsługiwane. Do odszyfrowywania są obsługiwane tylko pliki zaszyfrowane w usłudze SharePoint lub OneDrive.

## <a name="decryption-limitations-with-email-attachments"></a>Ograniczenia odszyfrowywania załączników wiadomości e-mail

W poniższych scenariuszach opisano ograniczenia dotyczące odszyfrowywania plików dołączonych do wiadomości e-mail. Te opisy scenariuszy obejmują również obejścia w celu złagodzenia tych ograniczeń.

- Jeśli plik znajdujący się na komputerze lokalnym (nie przechowywany w witrynie SharePoint lub koncie OneDrive) jest dołączony do wiadomości e-mail, a etykieta poufności, która stosuje szyfrowanie, jest stosowana do wiadomości e-mail, dołączony plik nie może zostać odszyfrowany za pomocą zbierania elektronicznych materiałów dowodowych. Oznacza to, że jeśli uruchomisz zapytanie wyszukiwania słów kluczowych skrzynki pocztowej adresata, zaszyfrowany załącznik pliku nie zostanie zwrócony przez zapytanie wyszukiwania słów kluczowych.

  Obejście tego ograniczenia polega na wyszukaniu w skrzynce pocztowej nadawcy tego samego załącznika pliku. Dzieje się tak dlatego, że szyfrowanie stosowane przez etykietę poufności jest stosowane podczas transportu wiadomości e-mail. Oznacza to, że załącznik jest szyfrowany po wysłaniu wiadomości e-mail. W rezultacie wystąpienie dołączonego pliku w skrzynce pocztowej nadawcy jest niezaszyfrowane, mimo że ten sam plik w skrzynce pocztowej adresata jest zaszyfrowany.

- Podobnie nie można odszyfrować załączników w chmurze (plików przechowywanych w witrynie SharePoint lub koncie OneDrive), które są kopiowane do wiadomości e-mail (przy użyciu opcji **Dołącz jako kopię** w Outlook). Dzieje się tak również dlatego, że szyfrowanie stosowane przez etykietę poufności jest stosowane podczas wysyłania wiadomości e-mail. Wyszukiwanie w skrzynce pocztowej nadawcy nieszyfrowanego wystąpienia kopii załącznika w chmurze jest również obejściem tego ograniczenia.

W obu tych scenariuszach wiadomości e-mail z zaszyfrowanymi załącznikami plików mogą być zwracane przez wyszukiwanie zbierania elektronicznych materiałów dowodowych, jeśli właściwość wiadomości e-mail (na przykład data wysłania, nadawca, adresat lub temat) jest zgodna z zapytaniem wyszukiwania.

## <a name="requirements-for-decryption-in-ediscovery"></a>Wymagania dotyczące odszyfrowywania w środowisku zbierania elektronicznych materiałów dowodowych

Musisz mieć przypisaną rolę odszyfrowywania usługi RMS do podglądu, przeglądania i eksportowania plików zaszyfrowanych przy użyciu technologii szyfrowania firmy Microsoft. Musisz również mieć przypisaną tę rolę, aby przeglądać zaszyfrowane pliki i wykonywać względem nich zapytania, które są dodawane do zestawu przeglądów w usłudze eDiscovery (Premium).

Ta rola jest domyślnie przypisywana do grupy ról Menedżera zbierania **elektronicznych materiałów** dowodowych na stronie Uprawnienia w portalu zgodności usługi Microsoft Purview. Aby uzyskać więcej informacji na temat roli odszyfrowywania usługi RMS, zobacz [Przypisywanie uprawnień zbierania elektronicznych materiałów dowodowych](assign-ediscovery-permissions.md#rms-decrypt).

### <a name="decrypting-rms-protected-email-messages-and-encrypted-file-attachments-using-content-search-or-ediscovery-standard"></a>Odszyfrowywanie wiadomości e-mail chronionych przez usługę RMS i zaszyfrowanych załączników plików przy użyciu wyszukiwania zawartości lub zbierania elektronicznych materiałów dowodowych (Standard)

Wszystkie wiadomości e-mail chronione prawami (chronione przez usługę RMS) zawarte w wynikach wyszukiwania zawartości zostaną odszyfrowane podczas ich eksportowania. Ponadto każdy plik zaszyfrowany za pomocą [technologii szyfrowania firmy Microsoft](encryption.md) i dołączony do wiadomości e-mail dołączonej do wyników wyszukiwania zostanie odszyfrowany podczas eksportowania. Ta funkcja odszyfrowywania jest domyślnie włączona dla członków grupy ról menedżera zbierania elektronicznych materiałów dowodowych. Dzieje się tak, ponieważ rola zarządzania odszyfrowywanie usługi RMS jest domyślnie przypisana do tej grupy ról. Podczas eksportowania zaszyfrowanych wiadomości e-mail i załączników należy pamiętać o następujących kwestiach:
  
- Jak wcześniej wyjaśniono, jeśli podczas eksportowania włączysz odszyfrowywanie komunikatów chronionych przez usługę RMS, musisz wyeksportować wyniki wyszukiwania jako pojedyncze komunikaty. Jeśli wyeksportujesz wyniki wyszukiwania do pliku PST, wiadomości chronione przez usługę RMS zostaną wyeksportowane jako pojedyncze wiadomości e-mail.

- Komunikaty odszyfrowane są identyfikowane w raporcie **ResultsLog** . Ten raport zawiera kolumnę o nazwie **Decode Status (Dekodowanie** stanu), a wartość **Dekodowane** identyfikuje odszyfrowane komunikaty.

- Oprócz odszyfrowywania załączników plików podczas eksportowania wyników wyszukiwania można również wyświetlić podgląd odszyfrowanego pliku podczas podglądu wyników wyszukiwania. Wiadomość e-mail chronioną prawami można wyświetlić tylko po jej wyeksportowaniu.

- Jeśli chcesz uniemożliwić komuś odszyfrowanie komunikatów rms-protect i zaszyfrowanych załączników plików, musisz utworzyć niestandardową grupę ról (przez skopiowanie wbudowanej grupy ról menedżera zbierania elektronicznych materiałów dowodowych), a następnie usunąć rolę zarządzania odszyfrowywanie usługi RMS z niestandardowej grupy ról. Następnie dodaj osobę, której nie chcesz odszyfrowywać komunikatów jako członka niestandardowej grupy ról.
