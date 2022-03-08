---
title: Omówienie szyfrowania dwukluczowych i często zadawane pytania
description: Często zadawane pytania dotyczące szyfrowania podwójnych klawiszy dla Microsoft 365.
author: kccross
ms.author: krowley
manager: laurawi
ms.date: 02/28/2022
ms.topic: conceptual
ms.service: information-protection
audience: Admin
ms.reviewer: esaggese
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
ms.openlocfilehash: 269937e78ffee6956df5a4dc8dc978fa30043912
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63320987"
---
# <a name="double-key-encryption-frequently-asked-questions"></a>Szyfrowanie dwukluczowych często zadawanych pytań

Masz pytanie na temat działania szyfrowania dwucyfrowego? Tu znajdziesz odpowiedź.

## <a name="what-is-double-key-encryption-for-microsoft-365-dke"></a>Co to jest szyfrowanie przy Microsoft 365 (DKE)?

Szyfrowanie dwukluczowych danych dla Microsoft 365 umożliwia klientom ochronę bardzo ważnych danych w celu spełnienia wyspecjalizowanych wymagań. Ułatwia klientom zachowanie pełnej kontroli nad ich kluczami szyfrowania. Używa dwóch klawiszy do ochrony danych. jeden klucz w kontrolce i drugi bezpiecznie przechowywany w Microsoft Azure. Wyświetlanie danych chronionych za pomocą szyfrowania dwukrotnie wymaga dostępu do obu kluczy. Ponieważ firma Microsoft może uzyskać dostęp tylko do jednego z tych kluczy, chronione dane pozostają niedostępne dla firmy Microsoft, zapewniając pełną kontrolę nad prywatnością i zabezpieczeniami danych.  

Usługę szyfrowania dwukluczowych używaną do żądania klucza możesz hostować w wybranej lokalizacji (na lokalnym serwerze zarządzania kluczami lub w chmurze). Usługa jest utrzymywana tak samo jak każda inna aplikacja. Szyfrowanie dwukluczowych umożliwia kontrolowanie dostępu do usługi szyfrowania dwukluczowych. Dane o wysokiej poufnej ochronie możesz przechowywać lokalnie lub przenosić do chmury. Możesz mieć pewność, że uniemożliwisz dostęp innej firmy, ponieważ będziesz mieć pełną kontrolę nad swoim kluczem. Szyfrowanie podwójnym kluczem umożliwia przechowywanie danych i klucza w tej samej lokalizacji.

DKE ułatwia spełnianie wymagań prawnych w ramach kilku przepisów i standardów, takich jak Ogólne Rozporządzenie o Ochronie Danych (RODO), ustawę HIPAA , ustawę o przenoszeniu i odpowiedzialności ubezpieczenia społecznego, ustawę Gramm-Leach-Bliley Act (GLBA), prawo lokalizacji danych w Rosji — nie prawo federalne. 242-FZ, federalna aktu prywatności Australii 1988 i nowozelandzkiej ustawy o ochronie prywatności 1993.

## <a name="can-i-use-double-key-encryption-with-microsoft-office-built-in-sensitivity-labeling"></a>Czy mogę używać szyfrowania dwucyfrowego Microsoft Office wbudowanych etykiet wrażliwości?

Do ochrony dokumentów za pomocą szyfrowania dwukluczowych należy użyć ujednoliconego klienta etykiet usługi Azure Information Protection. Obecnie nie można używać wbudowanych Microsoft Office etykiet wrażliwości.

## <a name="what-microsoft-365-apps-can-i-use-with-dke"></a>Jakich Aplikacje Microsoft 365 używać z użyciem funkcji DKE?

Za pomocą etykiet funkcji DKE można chronić dokumenty za pomocą wersji klasycznych programu Word, Excel i PowerPoint na Windows. Upewnij się, że korzystasz z programu *.12711 lub nowszego (wersje klasyczne programu Word, PowerPoint i Excel) na Windows.

## <a name="how-is-double-key-encryption-different-from-the-existing-hold-your-own-key-hyok-solution"></a>Czym różni się szyfrowanie podwójnym kluczem od istniejącego rozwiązania hold your own key (HYOK)?

Szyfrowanie przy użyciu dwóch klawiszy szyfruje dane za pomocą dwóch kluczy. Klucz szyfrowania znajduje się w Twojej kontrolce, a drugi klucz jest przechowywany w Microsoft Azure, co pozwala na przeniesienie zaszyfrowanych danych do chmury. Program HYOK chroni zawartość za pomocą tylko jednego klucza, a klucz jest zawsze w środowisku lokalnym.  

## <a name="can-double-key-encrypted-documents-be-shared-externally"></a>Czy można udostępniać dokumenty w postaci zaszyfrowanej podwójnie na zewnątrz?

Dokumenty szyfrowane przy użyciu dwóch kluczy można udostępniać użytkownikom w osobnej dzierżawie, o ile:

- Uzyskaj wymagane uprawnienia, aby uzyskać dostęp do klucza w usłudze szyfrowania dwucyfrowego.

- Miej wymagane uprawnienia dostępu do klucza w programie Microsoft Azure.

## <a name="what-happens-to-documents-that-are-protected-with-hyok"></a>Co się dzieje z dokumentami chronionymi za pomocą hyok?

Wdrażanie szyfrowania dwukluczowych nie ma wpływu na istniejącą konfigurację HYOK. Jednak zalecamy rozpoczęcie korzystania z szyfrowania dwukluczowych równolegle z funkcją HYOK.

## <a name="can-i-run-double-key-encryption-in-my-non-microsoft-air-gapped-environment"></a>Czy mogę korzystać z szyfrowania dwukrotnie w środowisku niegędnym przez firmę Microsoft?

Usługa DKE nie obsługuje tych środowisk, ponieważ usługa wymaga dostępu do Microsoft Azure.

## <a name="where-can-i-store-double-key-encrypted-documents"></a>Gdzie można przechowywać dokumenty zaszyfrowane przy użyciu dwóch kluczy?

Dokumenty w postaci zaszyfrowanej dwukrotnie można przechowywać lokalnie lub w chmurze. W chmurze możesz przenieść zaszyfrowaną zawartość do usługi SharePoint Online i OneDrive dla Firm. Firma Microsoft nie ma dostępu do klucza prywatnego, więc zaszyfrowane dane pozostają nieprzezroczyste dla firmy Microsoft. Oznacza to również, że nie można wyświetlać zaszyfrowanych dokumentów w trybie online w Office Web Apps.

## <a name="what-regions-and-languages-is-double-key-encryption-available-in-is-double-key-encryption-available-worldwide"></a>W jakich regionach i językach jest dostępne szyfrowanie dwucyfrowe? Czy szyfrowanie podwójnie klucza jest dostępne na całym świecie?

Etykiety DKE są zlokalizowane na tych samych językach, co inne etykiety wrażliwości w Microsoft Information Protection. Szyfrowanie dwukluczowych jest dostępne na całym świecie.

## <a name="can-i-convert-a-non-dke-label-to-a-dke-label"></a>Czy mogę przekonwertować etykietę niezabędaną DKE na etykietę DKE?

L.p. Nie można dodać etykiety DKE po jej utworzeniu. Zamiast tego podczas tworzenia etykiety należy wybrać pozycję Użyj szyfrowania dwucyfrowego i podać adres URL usługi szyfrowania dwukluczowych.

## <a name="how-do-i-roll-my-dke-keys"></a>Jak mogę przewęczyć klawisze DKE?

Aby uzyskać instrukcje dotyczące obracania (nazywanego również obracanie i rekeying) klucza przechowywanego na platformie Azure, zobacz Operacje dla klucza dzierżawy [usługi Azure Information Protection](/azure/information-protection/operations-customer-managed-tenant-key).

Zobacz [Dzierżawa i ustawienia klucza,](double-key-encryption.md#tenant-and-key-settings) aby uzyskać informacje na temat tworzenia nowego klucza dla usługi DKE.

Podczas tworzenia klucza należy skonfigurować nazwę i identyfikator GUID. Następnie w przypadku obracania klucza należy zachować stary rekord z nazwą i identyfikatorem GUID, ale dodać nowy rekord o tej samej nazwie, ale z innym identyfikatorem GUID. Nowy klucz zostanie ustawiony jako aktywny, dzięki czemu interfejs API klucza publicznego zacznie go zwracać w celu nowego szyfrowania. Oba klucze są dostępne do odszyfrowania, dzięki czemu można odszyfrować nową zawartość i starą zawartość.