---
title: Porównanie wersji szyfrowania wiadomości (OME)
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MET150
description: W tym artykule wyjaśniono różnice między różnymi wersjami programu Szyfrowanie wiadomości usługi Office 365.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 508a129cd472c8843e2af4a012560b17a44c49aa
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62987380"
---
# <a name="compare-versions-of-ome"></a>Porównywanie wersji OME

> [!IMPORTANT]
> 28 lutego 2021 r. firma Microsoft przestarzała obsługiwać usługi AD RMS w Exchange Online. Jeśli wdrożono środowisko hybrydowe, w którym skrzynki pocztowe usługi Exchange są w trybie online, i korzystasz z usługi IRM z lokalnym usługą RMS usługi Active Directory, musisz przeprowadzić migrację do platformy Azure. Organizacje, które wdrożono w środowisku GCC tym środowisku. Aby uzyskać informacje, zobacz "Omówienie sytuacji, w Exchange Online usług AD RMS w aplikacji" w tym artykule.

Pozostała część tego artykułu porównuje starsze wersje Szyfrowanie wiadomości usługi Office 365 (OME) z nowymi możliwościami IME oraz nowymi Zaawansowane szyfrowanie wiadomości usługi Office 365. Nowe funkcje to fuzja i nowsza wersja zarówno usługi OME, jak i usługi Zarządzanie prawami do informacji (IRM). Przedstawiono też unikatowe cechy wdrażania w GCC wysoki. Te dwie osoby mogą współistnieć w Twojej organizacji. Aby uzyskać informacje o tym, jak działają nowe funkcje, zobacz Szyfrowanie wiadomości usługi Office 365 [(OME).](ome.md)

Ten artykuł jest częścią większego szeregu artykułów na temat Szyfrowanie wiadomości usługi Office 365. Ten artykuł jest przeznaczony dla administratorów i firm IT. Jeśli po prostu szukasz informacji na temat wysyłania lub odbierania zaszyfrowanej wiadomości, zapoznaj się z listą artykułów w programie [Szyfrowanie wiadomości usługi Office 365 (OME)](ome.md) i znajdź artykuł najlepiej dopasowany do Twoich potrzeb.

## <a name="overview-of-ad-rms-deprecation-in-exchange-online"></a>Omówienie cofania usług AD RMS w programie Exchange Online

Exchange Online funkcje zarządzania prawami do informacji (IRM), które zapewniają ochronę w trybie online i offline wiadomości e-mail i załączników. Domyślnie program Exchange Online Azure Information Protection. Organizacja może jednak skonfigurować usługę IRM Exchange Online do używania lokalnej usługi zarządzania prawami dostępu w usłudze Active Directory (AD RMS). Obsługa usług AD RMS w Exchange Online jest wycofywana. Zamiast tego usługa Azure Information Protection całkowicie zastąpi usługi AD RMS.

Aby ocenić, czy to wyłączenie ma wpływ na organizację, zobacz Jak przeprowadzić migrację usług [AD RMS do usługi Azure RMS w programie Exchange Online](/exchange/troubleshoot/administration/migrate-ad-rms-to-azure). Ten artykuł zawiera zalecenia dotyczące opcji migracji.

## <a name="side-by-side-comparison-of-ome-features-and-capabilities"></a>Porównanie funkcji i możliwości OME

|           **Sytuacja**           | **Starsza wersja OME**    | **IRM w usługach AD RMS**        | **Nowe funkcje OME** |
|-----------------------------------|-------------------|-------------------|--------------------------|
|*Wysyłanie zaszyfrowanej poczty*        |Za Exchange przepływu poczty e-mail|Użytkownik końcowy inicjowany z Outlook komputera lub Outlook sieci Web lub za pośrednictwem Exchange przepływu poczty e-mail|Użytkownik końcowy inicjowany z komputera Outlook, Outlook dla komputerów Mac lub Outlook w sieci Web, za pośrednictwem reguł przepływu poczty e-mail Exchange (znanych także jako reguły transportu) i ochrony przed utratą danych (DLP, Data Loss Prevention)|
|*Szablon zarządzania prawami*       |   Nie dotyczy      |Opcja Nie przesyłaj dalej i szablony niestandardowe|Opcja Nie przesyłaj dalej, opcja tylko szyfrowania i szablony niestandardowe|
|*Typ adresata*                   |Adresaci wewnętrzni i zewnętrzni|Tylko adresaci wewnętrzni         |Adresaci wewnętrzni i zewnętrzni|
|*Środowisko dla adresata wewnętrznego*|Adresaci otrzymają wiadomość HTML, którą pobierają i otwierają w przeglądarce sieci Web lub aplikacji dla urządzeń przenośnych|Natywne środowisko wbudowane w Outlook klientach|Natywne środowisko wbudowane dla adresatów w tej samej organizacji przy Outlook klientów.  Adresaci mogą odczytywać wiadomości z portalu OME przy użyciu klientów Outlook niż klienty (nie są wymagane pobieranie ani używanie aplikacji).|
|*Środowisko dla adresata zewnętrznego*|Adresaci otrzymają wiadomość HTML, którą pobierają i otwierają w przeglądarce sieci Web lub aplikacji dla urządzeń przenośnych|Nie dotyczy|Natywne środowisko wbudowane dla Microsoft 365 adresatów. Wszyscy inni adresaci mogą odczytywać wiadomości z portalu OME (nie są wymagane pobieranie ani pobieranie aplikacji).|
|*Uprawnienia dotyczące załączników*           |Bez ograniczeń dotyczących załączników|Załączniki są chronione|Załączniki są chronione dla opcji Nie przesyłaj dalej i szablonów niestandardowych. Administratorzy mogą wybrać, czy załączniki dla opcji tylko szyfrowania są chronione.|
|*Wniesienie własnego klucza do pomocy technicznej (BYOK)*|Brak                |Brak               |Obsługiwane są program BYOK          |
||

## <a name="advantages-of-the-new-ome-capabilities-over-legacy-ome"></a>Zalety nowych funkcji OME w  skorzystaj ze starszych wersji OME

Nowe funkcje mają następujące zalety:

- Możliwość używania opcji tylko do szyfrowania (co umożliwia bezpieczną współpracę), opcji Nie przesyłaj dalej i ograniczeń niestandardowych.
- Nadawcy mogą ręcznie wysyłać wiadomości e-mail zaszyfrowane za pomocą nowych funkcji z Outlook komputerów Outlook dla komputerów Mac i Outlook w sieci Web klientów.
- Microsoft 365 mogą korzystać z wbudowanego obsługi w obsługiwanych Outlook klientach. Administratorzy mogą również zdecydować się na Microsoft 365 odbiorców marką.
- Konta spoza Microsoft 365, takie jak Gmail, Yahoo czy Microsoft, są federowane z portalem OME, który zapewnia tym adresatom lepsze środowisko użytkownika. W przypadku wszystkich innych tożsamości dostęp do zaszyfrowanych wiadomości jest wysyłany przy użyciu kodu z kodem dostępu w postaci kodów kierunkowych.
- Administratorzy mogą dostosowywać znakowanie i tworzyć wiele szablonów  marki.
- Administratorzy mogą odwołać wiadomości e-mail zaszyfrowane przy użyciu nowych funkcji.
- Nowe funkcje zapewniają szczegółowe raporty użycia za pośrednictwem Centrum zgodności &amp; zabezpieczeń.

## <a name="office-365-advanced-message-encryption-capabilities"></a>Zaawansowane szyfrowanie wiadomości usługi Office 365 funkcje

Zaawansowane szyfrowanie wiadomości usługi Office 365 oferuje dodatkowe możliwości poza nowymi możliwościami OME. Aby korzystać z funkcji zaawansowanego szyfrowania Szyfrowanie wiadomości usługi Office 365, musisz mieć nowe funkcje szyfrowania wiadomości w organizacji. Ponadto, aby skorzystać z tych funkcji, adresaci muszą wyświetlać i odpowiadać na bezpieczną pocztę za pośrednictwem portalu OME. Zaawansowane funkcje obejmują:

- Odwołania wiadomości

- Wygasanie wiadomości

- Wiele szablonów marki

Zaawansowane szyfrowanie wiadomości usługi Office 365 nie jest obsługiwane w GCC wysoki.

Aby uzyskać informacje na temat korzystania z zaawansowanego szyfrowania wiadomości, [zobacz Zaawansowane szyfrowanie wiadomości usługi Office 365](ome-advanced-message-encryption.md).

## <a name="unique-characteristics-of-office-365-message-encryption-in-a-gcc-high-deployment"></a>Unikatowe cechy Szyfrowanie wiadomości usługi Office 365 w GCC wdrożenie

Jeśli planujesz używać poczty e Szyfrowanie wiadomości usługi Office 365 w GCC o wysokiej jakości, istnieją pewne unikatowe cechy charakterystyczne dotyczące środowiska adresata.

### <a name="encrypted-email-between-gcc-high-and-gcc-high-recipients"></a>Zaszyfrowane wiadomości e-mail między GCC adresatami o wysokiej GCC e-mail

Nadawcy mogą ręcznie szyfrować wiadomości e-mail Outlook na komputerach PC i Mac i Outlook w sieci Web lub organizacje mogą skonfigurować zasady szyfrowania wiadomości e-mail przy użyciu reguł przepływu Exchange poczty e-mail.

Adresaci w GCC Wysoki otrzymują to samo środowisko czytania w tekście w programie Outlook dla komputerów PC i Mac Outlook w sieci Web i wszystkich innych użytkowników.

### <a name="encrypted-email-between-gcc-high-and-non-gcc-high-recipients"></a>Zaszyfrowana wiadomość e GCC między adresatami o wysokiej GCC i niedotyczysza

Nadawcy w GCC Wysoki mogą wysyłać zaszyfrowane wiadomości e-mail poza GCC Wysoka granica i na odwrót.

Wszyscy adresaci spoza GCC o wysokiej rozdzielczości, w tym użytkownicy komercyjnych usług Microsoft 365, użytkownicy usługi Outlook.com i inni użytkownicy innych dostawców poczty e-mail, takich jak Gmail i Yahoo, otrzymują wiadomość zawijaną. Ta wiadomość zawijaca przekierowuje adresata do portalu OME, gdzie adresat może odczytać wiadomość i odpowiedzieć na nie. Dotyczy to również nadawców spoza GCC o wysokiej jakości wysyłania poczty zaszyfrowanej OME na GCC wysoki.

## <a name="coexistence-of-legacy-ome-and-the-new-capabilities-in-the-same-tenant"></a>Współistnienie starszych wersji OME i nowych funkcji w tej samej dzierżawie

Możesz używać zarówno starszego OME, jak i nowych funkcji w tej samej dzierżawie. Jako administrator możesz to zrobić, wybierając wersję OME, której chcesz używać podczas tworzenia reguł przepływu poczty.

- Aby określić starszą wersję OME, użyj akcji reguły przepływu poczty e Exchange **Zastosuj poprzednią wersję OME**.

- Aby określić nowe funkcje, użyj akcji Reguły przepływu poczty Exchange Zastosuj Szyfrowanie wiadomości usługi Office 365 **i ochronę praw**.

Użytkownicy mogą ręcznie wysyłać wiadomości e-mail zaszyfrowane za pomocą nowych funkcji z usługi Outlook, Outlook dla komputerów Mac i Outlook w sieci Web.

## <a name="migrate-from-legacy-ome-to-the-new-capabilities"></a>Migrowanie ze starszego OME do nowych możliwości

Mimo że obie wersje usługi OME mogą być współistniene, zdecydowanie zalecamy edytowanie starych reguł przepływu poczty, które używają akcji reguły Zastosuj poprzednią wersję usługi **OME** do używania nowych możliwości. Aktualizuj te reguły, aby używać akcji reguły przepływu poczty e-mail **Zastosuj Szyfrowanie wiadomości usługi Office 365 i ochronę praw**. Aby uzyskać instrukcje, [zobacz Definiowanie reguł przepływu poczty e-mail w celu szyfrowania wiadomości e-mail Office 365](define-mail-flow-rules-to-encrypt-email.md).

## <a name="get-started-with-ome"></a>Wprowadzenie do OME

Zazwyczaj nowe funkcje OME są automatycznie włączane dla organizacji. Aby uzyskać więcej informacji o nowych możliwościach OME w organizacji, zobacz Konfigurowanie nowych i [Szyfrowanie wiadomości usługi Office 365 OME](set-up-new-message-encryption-capabilities.md).

Starsza wersja OME jest automatycznie włączana dla organizacji, jeśli włączono usługę Azure Information Protection. W przeszłości starsza wersja OME działała nawet wtedy, gdy nie włączono usługi Azure Information Protection. Nie ma to już sprawy.

Aby zacząć korzystać ze starszego OME, jeśli masz włączoną usługę Azure Information Protection, skonfiguruj reguły przepływu poczty, które używają akcji reguły Zastosuj **poprzednią wersję OME**. Aby uzyskać instrukcje, [zobacz Definiowanie reguł przepływu poczty e-mail w celu szyfrowania wiadomości e-mail](define-mail-flow-rules-to-encrypt-email.md).
