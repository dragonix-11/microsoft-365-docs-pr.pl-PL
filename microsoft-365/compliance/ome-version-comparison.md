---
title: Porównanie wersji szyfrowania komunikatów
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
description: W tym artykule wyjaśniono różnice między różnymi wersjami szyfrowania komunikatów.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 64a67ac9423463e4fcf1b5a3ff6c2262801933b0
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66629338"
---
# <a name="compare-versions-of-message-encryption"></a>Porównanie wersji szyfrowania wiadomości

> [!IMPORTANT]
> 28 lutego 2021 r. firma Microsoft wycofała obsługę usług AD RMS w Exchange Online. Jeśli wdrożono środowisko hybrydowe, w którym skrzynki pocztowe programu Exchange są w trybie online i używasz usługi IRM z lokalnym usługą Active Directory RMS, musisz przeprowadzić migrację na platformę Azure. Dotyczy to również organizacji wdrożonych w środowisku GCC Moderate. Aby uzyskać informacje, zobacz "Overview of AD RMS deprecation in Exchange Online" (Omówienie wycofywania usług AD RMS w Exchange Online) w tym artykule.

W pozostałej części tego artykułu porównaliśmy starsze Office 365 szyfrowania komunikatów (OME) z usługami Szyfrowanie wiadomości w Microsoft Purview i Microsoft Purview Advanced Message Encryption. Szyfrowanie wiadomości w Microsoft Purview jest fuzja i nowsza wersja zarówno OME, jak i Zarządzanie prawami do informacji (IRM). Przedstawiono również unikatowe cechy wdrażania w usłudze GCC High. Te dwa elementy mogą współistnieć w organizacji. Aby uzyskać informacje na temat sposobu działania nowych funkcji, zobacz [Office 365 Szyfrowanie komunikatów (OME).](ome.md)

Ten artykuł jest częścią większej serii artykułów na temat szyfrowania komunikatów. Ten artykuł jest przeznaczony dla administratorów i itpros. Jeśli szukasz tylko informacji na temat wysyłania lub odbierania zaszyfrowanej wiadomości, zapoznaj się z listą artykułów w [temacie Szyfrowanie komunikatów](ome.md) i znajdź artykuł, który najlepiej odpowiada Twoim potrzebom.

## <a name="overview-of-ad-rms-deprecation-in-exchange-online"></a>Omówienie wycofywania usług AD RMS w Exchange Online

Exchange Online obejmuje funkcję zarządzania prawami do informacji (IRM), która zapewnia ochronę wiadomości e-mail i załączników w trybie online i offline. Domyślnie Exchange Online używa usługi Azure Information Protection. Organizacja mogła jednak skonfigurować Exchange Online IRM do korzystania z usługi lokalna usługa Active Directory Rights Management Service (AD RMS). Obsługa usług AD RMS w Exchange Online jest wycofywana. Zamiast tego usługa Azure Information Protection całkowicie zastąpi usługę AD RMS.

Aby ocenić, czy to wycofanie ma wpływ na organizację, zobacz [Jak przeprowadzić migrację usług AD RMS do usługi Azure RMS w Exchange Online](/exchange/troubleshoot/administration/migrate-ad-rms-to-azure). Ten artykuł zawiera zalecenia dotyczące opcji migracji.

## <a name="side-by-side-comparison-of-message-encryption-features-and-capabilities"></a>Porównanie funkcji i możliwości szyfrowania komunikatów obok siebie

|           **Sytuacji**           | **Starsza wersja OME**    | **Usługa IRM w usłudze AD RMS**        | **Szyfrowanie wiadomości w Microsoft Purview** |
|-----------------------------------|-------------------|-------------------|--------------------------|
|*Wysyłanie zaszyfrowanej poczty*        |Za pośrednictwem reguł przepływu poczty programu Exchange|Użytkownik końcowy zainicjowany z programu Outlook Desktop lub programu Outlook w sieci Web; lub za pośrednictwem reguł przepływu poczty programu Exchange|Użytkownik końcowy inicjowany z programu Outlook Desktop, Outlook dla komputerów Mac lub Outlook w sieci Web za pośrednictwem reguł przepływu poczty programu Exchange (znanych również jako reguły transportu) i ochrony przed utratą danych (DLP)|
|*Szablon zarządzania prawami*       |   nd.      |Opcja Nie przesyłaj dalej i szablony niestandardowe|Opcja Nie przesyłaj dalej, opcja tylko szyfrowanie i szablony niestandardowe|
|*Typ adresata*                   |Adresaci wewnętrzni i zewnętrzni|Tylko adresaci wewnętrzni         |Adresaci wewnętrzni i zewnętrzni|
|*Środowisko dla wewnętrznego odbiorcy*|Adresaci otrzymują komunikat HTML, który pobierają i otwierają w przeglądarce internetowej lub aplikacji mobilnej|Natywne środowisko wbudowane w klientach programu Outlook|Natywne środowisko wbudowane dla adresatów w tej samej organizacji przy użyciu klientów programu Outlook.  Adresaci mogą odczytywać komunikaty z portalu OME przy użyciu klientów innych niż Outlook (nie jest wymagane pobieranie ani aplikacja).|
|*Środowisko dla zewnętrznego odbiorcy*|Adresaci otrzymują komunikat HTML, który pobierają i otwierają w przeglądarce internetowej lub aplikacji mobilnej|nd.|Natywne środowisko wbudowane dla adresatów platformy Microsoft 365. Wszyscy inni adresaci mogą odczytywać komunikaty z portalu OME (nie jest wymagane pobieranie ani aplikacja).|
|*Uprawnienia załącznika*           |Brak ograniczeń dotyczących załączników|Załączniki są chronione|Załączniki są chronione dla opcji Nie przesyłaj dalej i szablonów niestandardowych. Administratorzy mogą wybrać, czy załączniki dla opcji tylko do szyfrowania są chronione, czy nie.|
|*Obsługa własnego klucza (BYOK)*|Brak                |Brak               |Obsługiwane przez funkcję BYOK          |
||

## <a name="advantages-of-microsoft-purview-message-encryption-over-legacy-ome"></a>Zalety Szyfrowanie wiadomości w Microsoft Purview w stosunku do starszego OME

Nowe możliwości zapewniają następujące korzyści:

- Możliwość korzystania z opcji tylko do szyfrowania (która umożliwia bezpieczną współpracę), opcji Nie przesyłaj dalej i ograniczeń niestandardowych.
- Nadawcy mogą wysyłać wiadomości e-mail zaszyfrowane przy użyciu nowych funkcji ręcznie z programu Outlook Desktop, Outlook dla komputerów Mac i klientów Outlook w sieci Web.
- Adresaci platformy Microsoft 365 mogą korzystać z wbudowanego środowiska w obsługiwanych klientach programu Outlook. Alternatywnie administratorzy mogą pokazać odbiorcom platformy Microsoft 365 markowe środowisko.
- Konta spoza platformy Microsoft 365, takie jak konta Gmail, Yahoo i Microsoft, są sfederowane z portalem OME, który zapewnia lepsze środowisko użytkownika dla tych adresatów. Wszystkie inne tożsamości używają jednorazowego kodu dostępu w celu uzyskania dostępu do zaszyfrowanych komunikatów.
- Administratorzy mogą dostosowywać znakowanie i tworzyć wiele szablonów znakowania.
- Administratorzy mogą odwoływać wiadomości e-mail zaszyfrowane przy użyciu nowych możliwości.
- Nowe funkcje udostępniają szczegółowe raporty użycia za pośrednictwem Centrum zgodności zabezpieczeń &amp; .

## <a name="microsoft-purview-advanced-message-encryption-capabilities"></a>Zaawansowane funkcje szyfrowania komunikatów w usłudze Microsoft Purview

Zaawansowane szyfrowanie komunikatów w usłudze Microsoft Purview oferuje dodatkowe możliwości oprócz Szyfrowanie wiadomości w Microsoft Purview. Aby móc korzystać z zaawansowanego szyfrowania komunikatów, musisz skonfigurować Szyfrowanie wiadomości w Microsoft Purview w organizacji. Ponadto, aby móc korzystać z tych możliwości, adresaci muszą wyświetlać wiadomości e-mail i odpowiadać na nie za pośrednictwem portalu Szyfrowanie wiadomości w Microsoft Purview. Zaawansowane możliwości obejmują:

- Odwoływanie komunikatów

- Wygaśnięcie komunikatu

- Wiele szablonów znakowania

Zaawansowane szyfrowanie komunikatów nie jest obsługiwane w usłudze GCC High.

Aby uzyskać informacje na temat korzystania z zaawansowanego szyfrowania komunikatów, zobacz [Zaawansowane szyfrowanie komunikatów w usłudze Microsoft Purview](ome-advanced-message-encryption.md).

## <a name="unique-characteristics-of-microsoft-purview-message-encryption-in-a-gcc-high-deployment"></a>Unikatowe cechy Szyfrowanie wiadomości w Microsoft Purview we wdrożeniu GCC High

Jeśli planujesz używać Szyfrowanie wiadomości w Microsoft Purview w środowisku GCC High, istnieją pewne unikatowe cechy dotyczące środowiska odbiorcy.

### <a name="encrypted-email-between-gcc-high-and-gcc-high-recipients"></a>Szyfrowana wiadomość e-mail między adresatami GCC High i GCC High

Nadawcy mogą ręcznie szyfrować wiadomości e-mail w programie Outlook dla komputerów PC i Mac oraz Outlook w sieci Web lub organizacje mogą skonfigurować zasady szyfrowania wiadomości e-mail przy użyciu reguł przepływu poczty programu Exchange.

Adresaci w usłudze GCC High otrzymują takie samo wbudowane środowisko do czytania w programie Outlook dla komputerów PC i Mac oraz Outlook w sieci Web jak wszyscy inni użytkownicy.

### <a name="encrypted-email-between-gcc-high-and-non-gcc-high-recipients"></a>Szyfrowana wiadomość e-mail między adresatami GCC High i Non-GCC High

Nadawcy wewnątrz GCC High mogą wysyłać zaszyfrowane wiadomości e-mail poza granicami GCC High i na odwrót.

Wszyscy adresaci spoza GCC High, w tym komercyjni użytkownicy platformy Microsoft 365, użytkownicy Outlook.com i inni użytkownicy innych dostawców poczty e-mail, takich jak Gmail i Yahoo, otrzymują wiadomość e-mail z otoką. Ta wiadomość e-mail otoki przekierowuje adresata do portalu Szyfrowanie wiadomości w Microsoft Purview, gdzie adresat może odczytać wiadomość i odpowiedzieć na nią. Dotyczy to również nadawców spoza GCC High wysyłających zaszyfrowaną pocztę OME do GCC High.

## <a name="coexistence-of-legacy-ome-and-microsoft-purview-message-encryption-in-the-same-tenant"></a>Współistnienie starszego środowiska OME i Szyfrowanie wiadomości w Microsoft Purview w tej samej dzierżawie

W tej samej dzierżawie można używać zarówno starszego protokołu OME, jak i Szyfrowanie wiadomości w Microsoft Purview. Jako administrator możesz to zrobić, wybierając wersję szyfrowania wiadomości, której chcesz użyć podczas tworzenia reguł przepływu poczty.

- Aby określić starszą wersję protokołu OME, użyj akcji Reguła przepływu poczty programu Exchange **Zastosuj poprzednią wersję protokołu OME**.

- Aby określić Szyfrowanie wiadomości w Microsoft Purview, użyj akcji Reguła przepływu poczty programu Exchange **Zastosuj Office 365 szyfrowanie komunikatów i ochronę praw**.

Użytkownicy mogą ręcznie wysyłać pocztę zaszyfrowaną za pomocą Szyfrowanie wiadomości w Microsoft Purview z programu Outlook Desktop, Outlook dla komputerów Mac i Outlook w sieci Web.

## <a name="migrate-from-legacy-ome-to-microsoft-purview-message-encryption"></a>Migrowanie ze starszej wersji OME do Szyfrowanie wiadomości w Microsoft Purview

Mimo że obie wersje mogą współistnieć, zdecydowanie zalecamy edytowanie starych reguł przepływu poczty, które używają akcji **reguły Zastosuj poprzednią wersję protokołu OME** do używania Szyfrowanie wiadomości w Microsoft Purview. Zaktualizuj te reguły, aby używać akcji reguły przepływu poczty **Zastosuj Office 365 szyfrowanie komunikatów i ochronę praw**. Aby uzyskać instrukcje, zobacz [Definiowanie reguł przepływu poczty w celu szyfrowania wiadomości e-mail](define-mail-flow-rules-to-encrypt-email.md).

## <a name="get-started-with-ome"></a>Wprowadzenie do OME

Zazwyczaj Szyfrowanie wiadomości w Microsoft Purview jest automatycznie włączana dla Twojej organizacji. Aby uzyskać więcej informacji na temat Szyfrowanie wiadomości w Microsoft Purview w organizacji, zobacz [Konfigurowanie Szyfrowanie wiadomości w Microsoft Purview](set-up-new-message-encryption-capabilities.md).

Starsza wersja OME jest automatycznie włączana dla Organizacji, jeśli włączono usługę Azure Information Protection. W przeszłości starsze środowisko OME działało nawet wtedy, gdy Information Protection platformy Azure nie było włączone. Tak już nie jest.

Aby rozpocząć korzystanie ze starszej wersji protokołu OME, jeśli włączono usługę Azure Information Protection, skonfiguruj reguły przepływu poczty korzystające z akcji **reguły Zastosuj poprzednią wersję protokołu OME**. Aby uzyskać instrukcje, zobacz [Definiowanie reguł przepływu poczty w celu szyfrowania wiadomości e-mail](define-mail-flow-rules-to-encrypt-email.md).
