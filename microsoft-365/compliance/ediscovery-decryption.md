---
title: Odszyfrowywanie w zbierania elektronicznych materiałów dowodowych
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
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
description: Dowiedz się, jak narzędzia zbierania elektronicznych materiałów dowodowych platformy Microsoft 365 obsługują zaszyfrowane dokumenty dołączone do wiadomości e-mail i przechowywane w usłudze SharePoint Online i OneDrive dla Firm.
ms.openlocfilehash: 689ac5420c3d9110a51586d8f008416363aafeec
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66626320"
---
# <a name="decryption-in-microsoft-365-ediscovery-tools"></a>Odszyfrowywanie w narzędziach zbierania elektronicznych materiałów dowodowych platformy Microsoft 365

Szyfrowanie jest ważną częścią strategii ochrony plików i ochrony informacji. Organizacje wszystkich typów używają technologii szyfrowania, aby chronić poufne treści w organizacji i zapewnić, że tylko odpowiednie osoby mają dostęp do tej zawartości.

Aby wykonać typowe zadania zbierania elektronicznych materiałów dowodowych w zaszyfrowanej zawartości, menedżerowie zbierania elektronicznych materiałów dowodowych musieli odszyfrować zawartość wiadomości e-mail, ponieważ została ona wyeksportowana z wyszukiwań zawartości, Zbieranie elektronicznych materiałów dowodowych w Microsoft Purview przypadków (standardowych) i Zbieranie elektronicznych materiałów dowodowych w Microsoft Purview (Premium). Zawartość zaszyfrowana przy użyciu technologii szyfrowania firmy Microsoft była dostępna do przeglądu dopiero po jej wyeksportowaniu.

Aby ułatwić zarządzanie zaszyfrowaną zawartością w przepływie pracy zbierania elektronicznych materiałów dowodowych, narzędzia zbierania elektronicznych materiałów dowodowych platformy Microsoft 365 zawierają teraz odszyfrowywanie zaszyfrowanych plików dołączonych do wiadomości e-mail i wysyłanych w Exchange Online.<sup> 1</sup> Ponadto zaszyfrowane dokumenty przechowywane w usłudze SharePoint Online i OneDrive dla Firm są odszyfrowywane w usłudze eDiscovery (Premium).

Przed tą nową funkcją odszyfrowano tylko zawartość wiadomości e-mail chronionej przez zarządzanie prawami (a nie dołączone pliki). Nie można odszyfrować zaszyfrowanych dokumentów w programach SharePoint i OneDrive podczas przepływu pracy zbierania elektronicznych materiałów dowodowych. Teraz pliki zaszyfrowane za pomocą technologii szyfrowania firmy Microsoft znajdują się na koncie programu SharePoint lub OneDrive, które można przeszukiwać i odszyfrowywać, gdy wyniki wyszukiwania są przygotowywane do wersji zapoznawczej, dodawane do zestawu przeglądów w systemie zbierania elektronicznych materiałów dowodowych (Premium) i eksportowane. Ponadto można wyszukiwać zaszyfrowane dokumenty w programach SharePoint i OneDrive dołączonych do wiadomości e-mail. Ta funkcja odszyfrowywania umożliwia menedżerom zbierania elektronicznych materiałów dowodowych wyświetlanie zawartości zaszyfrowanych załączników wiadomości e-mail i dokumentów witryny podczas przeglądania wyników wyszukiwania i przeglądanie ich po dodaniu ich do zestawu przeglądów w usłudze eDiscovery (Premium).

## <a name="supported-encryption-technologies"></a>Obsługiwane technologie szyfrowania

Narzędzia zbierania elektronicznych materiałów dowodowych firmy Microsoft obsługują elementy zaszyfrowane przy użyciu technologii szyfrowania firmy Microsoft. Te technologie to usługa Azure Rights Management i Microsoft Purview Information Protection (w szczególności etykiety poufności). Aby uzyskać więcej informacji na temat technologii szyfrowania firmy Microsoft, zobacz [Szyfrowanie](encryption.md). Zawartość szyfrowana za pomocą technologii szyfrowania innych firm nie jest obsługiwana. Na przykład podgląd lub eksportowanie zawartości zaszyfrowanej przy użyciu technologii innych niż Microsoft nie jest obsługiwane.

> [!NOTE]
> Odszyfrowywanie wiadomości e-mail wysyłanych za pomocą [Szyfrowanie wiadomości w Microsoft Purview niestandardowego szablonu znakowania](add-your-organization-brand-to-encrypted-messages.md) nie jest obsługiwane przez narzędzia microsoft eDiscovery. W przypadku korzystania z niestandardowego szablonu znakowania OME wiadomości e-mail są dostarczane do portalu OME zamiast do skrzynki pocztowej adresata. W związku z tym nie będzie można wyszukiwać zaszyfrowanych wiadomości za pomocą narzędzi zbierania elektronicznych materiałów dowodowych, ponieważ te wiadomości nigdy nie są odbierane przez skrzynkę pocztową adresata.

## <a name="ediscovery-activities-that-support-encrypted-items"></a>Działania zbierania elektronicznych materiałów dowodowych, które obsługują zaszyfrowane elementy

W poniższej tabeli przedstawiono obsługiwane zadania, które mogą być wykonywane w narzędziach zbierania elektronicznych materiałów dowodowych platformy Microsoft 365 w przypadku zaszyfrowanych plików dołączonych do wiadomości e-mail i zaszyfrowanych dokumentów w programach SharePoint i OneDrive. Te obsługiwane zadania można wykonywać na zaszyfrowanych plikach, które spełniają kryteria wyszukiwania. Wartość `N/A` wskazuje, że funkcja nie jest dostępna w odpowiednim narzędziu do zbierania elektronicznych materiałów dowodowych.

|Zadanie zbierania elektronicznych materiałów dowodowych  |Wyszukiwanie zawartości  |Zbieranie elektronicznych materiałów dowodowych (wersja standardowa)  |Zbieranie elektronicznych materiałów dowodowych (warstwa Premium)  |
|:---------|:---------|:---------|:---------|
|Wyszukiwanie zawartości w zaszyfrowanych plikach w witrynach i załącznikach wiadomości e-mail<sup>1</sup>     |Nie      |Nie      |Tak      |
|Podgląd zaszyfrowanych plików dołączonych do poczty e-mail     |Tak      |Tak     |Tak       |
|Podgląd zaszyfrowanych dokumentów w programach SharePoint i OneDrive|Nie      |Nie    |Tak       |
|Przeglądanie zaszyfrowanych plików w zestawie przeglądów    |nd.      |nd.        | Tak        |
|Eksportowanie zaszyfrowanych plików dołączonych do poczty e-mail    |Tak       |Tak  |Tak    |
|Eksportowanie zaszyfrowanych dokumentów w programach SharePoint i OneDrive    |Nie       |Nie  |Tak    |
|||||

> [!NOTE]
> <sup>1</sup> Zaszyfrowane pliki znajdujące się na komputerze lokalnym i w chmurze załączniki skopiowane do wiadomości e-mail nie są odszyfrowywane i indeksowane na potrzeby zbierania elektronicznych materiałów dowodowych. Aby uzyskać więcej informacji i obejść te scenariusze, zobacz sekcję [Ograniczenia odszyfrowywania z załącznikami wiadomości e-mail](#decryption-limitations-with-email-attachments) w tym artykule.

## <a name="decryption-limitations-with-sensitivity-labels-in-sharepoint-and-onedrive"></a>Ograniczenia odszyfrowywania etykiet poufności w programach SharePoint i OneDrive

Funkcja zbierania elektronicznych materiałów dowodowych nie obsługuje zaszyfrowanych plików w programach SharePoint i OneDrive, gdy etykieta poufności, która zastosowała szyfrowanie, jest skonfigurowana przy użyciu jednego z następujących ustawień:

- Użytkownicy mogą przypisywać uprawnienia, gdy ręcznie zastosują etykietę do dokumentu. Jest to czasami *określane jako uprawnienia zdefiniowane przez użytkownika*.

- Dostęp użytkownika do dokumentu ma ustawienie wygaśnięcia, które jest ustawione na wartość inną niż **Nigdy**.

Aby uzyskać więcej informacji na temat tych ustawień, zobacz sekcję "Konfigurowanie ustawień szyfrowania" w [temacie Ograniczanie dostępu do zawartości przy użyciu etykiet poufności w celu zastosowania szyfrowania](encryption-sensitivity-labels.md#configure-encryption-settings).

Dokumenty zaszyfrowane przy użyciu poprzednich ustawień mogą być nadal zwracane przez wyszukiwanie zbierania elektronicznych materiałów dowodowych. Może się tak zdarzyć, gdy właściwość dokumentu (na przykład tytuł, autor lub data modyfikacji) jest zgodna z kryteriami wyszukiwania. Chociaż te dokumenty mogą zostać uwzględnione w wynikach wyszukiwania, nie mogą być przeglądane ani przeglądane. Te dokumenty pozostaną również zaszyfrowane, gdy zostaną wyeksportowane w usłudze eDiscovery (Premium).

> [!IMPORTANT]
> Odszyfrowywanie nie jest obsługiwane w przypadku plików, które są szyfrowane lokalnie, a następnie przekazywane do programu SharePoint lub oneDrive. Na przykład pliki lokalne, które są szyfrowane przez klienta usługi Azure Information Protection (AIP), a następnie przekazywane do platformy Microsoft 365, nie są obsługiwane. Do odszyfrowywania są obsługiwane tylko pliki zaszyfrowane w usłudze SharePoint lub OneDrive.

## <a name="decryption-limitations-with-email-attachments"></a>Ograniczenia odszyfrowywania załączników wiadomości e-mail

W poniższych scenariuszach opisano ograniczenia dotyczące odszyfrowywania plików dołączonych do wiadomości e-mail. Te opisy scenariuszy obejmują również obejścia w celu złagodzenia tych ograniczeń.

- Jeśli plik znajdujący się na komputerze lokalnym (a nie przechowywany w witrynie programu SharePoint lub na koncie usługi OneDrive) jest dołączony do wiadomości e-mail, a etykieta poufności, która stosuje szyfrowanie, jest stosowana do wiadomości e-mail, dołączony plik nie może zostać odszyfrowany przez funkcję eDiscovery. Oznacza to, że jeśli uruchomisz zapytanie wyszukiwania słów kluczowych skrzynki pocztowej adresata, zaszyfrowany załącznik pliku nie zostanie zwrócony przez zapytanie wyszukiwania słów kluczowych.

  Obejście tego ograniczenia polega na wyszukaniu w skrzynce pocztowej nadawcy tego samego załącznika pliku. Dzieje się tak dlatego, że szyfrowanie stosowane przez etykietę poufności jest stosowane podczas transportu wiadomości e-mail. Oznacza to, że załącznik jest szyfrowany po wysłaniu wiadomości e-mail. W rezultacie wystąpienie dołączonego pliku w skrzynce pocztowej nadawcy jest niezaszyfrowane, mimo że ten sam plik w skrzynce pocztowej adresata jest zaszyfrowany.

- Podobnie załączniki w chmurze (pliki przechowywane w witrynie programu SharePoint lub na koncie usługi OneDrive), które są kopiowane do wiadomości e-mail (przy użyciu opcji **Dołącz jako kopię** w programie Outlook), nie mogą być odszyfrowywane przez funkcję zbierania elektronicznych materiałów dowodowych. Dzieje się tak również dlatego, że szyfrowanie stosowane przez etykietę poufności jest stosowane podczas wysyłania wiadomości e-mail. Wyszukiwanie w skrzynce pocztowej nadawcy nieszyfrowanego wystąpienia kopii załącznika w chmurze jest również obejściem tego ograniczenia.

W obu tych scenariuszach wiadomości e-mail z zaszyfrowanymi załącznikami plików mogą być zwracane przez wyszukiwanie zbierania elektronicznych materiałów dowodowych, jeśli właściwość wiadomości e-mail (na przykład data wysłania, nadawca, adresat lub temat) jest zgodna z zapytaniem wyszukiwania.

## <a name="requirements-for-decryption-in-ediscovery"></a>Wymagania dotyczące odszyfrowywania w środowisku zbierania elektronicznych materiałów dowodowych

Musisz mieć przypisaną rolę odszyfrowywania usługi RMS do podglądu, przeglądania i eksportowania plików zaszyfrowanych przy użyciu technologii szyfrowania firmy Microsoft. Musisz również mieć przypisaną tę rolę, aby przeglądać i wykonywać zapytania dotyczące zaszyfrowanych plików dodanych do zestawu przeglądów w usłudze eDiscovery (Premium).

Ta rola jest domyślnie przypisywana do grupy ról Menedżera zbierania **elektronicznych materiałów** dowodowych na stronie Uprawnienia w portal zgodności Microsoft Purview. Aby uzyskać więcej informacji na temat roli odszyfrowywania usługi RMS, zobacz [Przypisywanie uprawnień zbierania elektronicznych materiałów dowodowych](assign-ediscovery-permissions.md#rms-decrypt).

### <a name="decrypting-rms-protected-email-messages-and-encrypted-file-attachments-using-content-search-or-ediscovery-standard"></a>Odszyfrowywanie wiadomości e-mail chronionych przez usługę RMS i zaszyfrowanych załączników plików przy użyciu wyszukiwania zawartości lub zbierania elektronicznych materiałów dowodowych (Standard)

Wszystkie wiadomości e-mail chronione prawami (chronione przez usługę RMS) zawarte w wynikach wyszukiwania zawartości zostaną odszyfrowane podczas ich eksportowania. Ponadto każdy plik zaszyfrowany za pomocą [technologii szyfrowania firmy Microsoft](encryption.md) i dołączony do wiadomości e-mail dołączonej do wyników wyszukiwania zostanie odszyfrowany podczas eksportowania. Ta funkcja odszyfrowywania jest domyślnie włączona dla członków grupy ról menedżera zbierania elektronicznych materiałów dowodowych. Dzieje się tak, ponieważ rola zarządzania odszyfrowywanie usługi RMS jest domyślnie przypisana do tej grupy ról. Podczas eksportowania zaszyfrowanych wiadomości e-mail i załączników należy pamiętać o następujących kwestiach:
  
- Jak wcześniej wyjaśniono, jeśli podczas eksportowania włączysz odszyfrowywanie komunikatów chronionych przez usługę RMS, musisz wyeksportować wyniki wyszukiwania jako pojedyncze komunikaty. Jeśli wyeksportujesz wyniki wyszukiwania do pliku PST, wiadomości chronione przez usługę RMS zostaną wyeksportowane jako pojedyncze wiadomości e-mail.

- Komunikaty odszyfrowane są identyfikowane w raporcie **ResultsLog** . Ten raport zawiera kolumnę o nazwie **Decode Status (Dekodowanie** stanu), a wartość **Dekodowane** identyfikuje odszyfrowane komunikaty.

- Oprócz odszyfrowywania załączników plików podczas eksportowania wyników wyszukiwania można również wyświetlić podgląd odszyfrowanego pliku podczas podglądu wyników wyszukiwania. Wiadomość e-mail chronioną prawami można wyświetlić tylko po jej wyeksportowaniu.

- Jeśli chcesz uniemożliwić komuś odszyfrowanie komunikatów rms-protect i zaszyfrowanych załączników plików, musisz utworzyć niestandardową grupę ról (przez skopiowanie wbudowanej grupy ról menedżera zbierania elektronicznych materiałów dowodowych), a następnie usunąć rolę zarządzania odszyfrowywanie usługi RMS z niestandardowej grupy ról. Następnie dodaj osobę, której nie chcesz odszyfrowywać komunikatów jako członka niestandardowej grupy ról.
