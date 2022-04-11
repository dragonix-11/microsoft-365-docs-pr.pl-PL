---
title: Wyłączanie protokołów TLS 1.0 i 1.1 w Microsoft 365 GCC High i DoD
description: Omówiono, jak firma Microsoft wyłącza obsługę protokołów TLS 1.1 i 1.0 w środowiskach GCC High i DoD w Microsoft 365.
author: kccross
manager: laurawi
ms.localizationpriority: medium
search.appverid:
- MET150
audience: ITPro
ms.collection: M365-security-compliance
ms.service: information-protection
ms.topic: article
ms.reviewer: krowley
ms.author: krowley
appliesto:
- Office 365 Business
ms.openlocfilehash: bad0dc997f2c564670858d2ac35b2cd3177e0578
ms.sourcegitcommit: 9ba00298cfa9ae293e4a57650965fdb3e8ffe07b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/11/2022
ms.locfileid: "64760392"
---
# <a name="disabling-tls-10-and-11-in-microsoft-365-gcc-high-and-dod"></a>Wyłączanie protokołów TLS 1.0 i 1.1 w Microsoft 365 GCC High i DoD

## <a name="summary"></a>Podsumowanie

Aby zapewnić zgodność z najnowszymi standardami zgodności dla federalnego programu do zarządzania ryzykiem i autoryzacją (FedRAMP), wyłączamy protokoły Transport Layer Security (TLS) w wersjach 1.1 i 1.0 w Microsoft 365 dla środowisk GCC High i DoD. Ta zmiana została wcześniej ogłoszona za pośrednictwem pomoc techniczna firmy Microsoft w [artykule Przygotowanie do obowiązkowego użycia protokołu TLS 1.2 w Office 365](https://support.microsoft.com/help/4057306/preparing-for-tls-1-2-in-office-365).

Bezpieczeństwo twoich danych jest ważne i dbamy o przejrzystość zmian, które mogą mieć wpływ na korzystanie z usługi.

Chociaż [implementacja protokołu Microsoft TLS 1.0](https://support.microsoft.com/help/3117336) nie ma znanych luk w zabezpieczeniach, pozostajemy zaangażowani w standardy zgodności FedRAMP. W związku z tym 15 stycznia 2020 r. wyłączyliśmy protokół TLS 1.1 i 1.0 w Microsoft 365 w środowiskach GCC High i DoD. Aby uzyskać informacje o sposobie usuwania zależności TLS 1.1 i 1.0, zobacz następujący oficjalny dokument:

[Rozwiązywanie problemu z protokołem TLS 1.0](https://www.microsoft.com/download/details.aspx?id=55266)

## <a name="more-information"></a>Więcej informacji

Począwszy od 15 stycznia 2020 r., Microsoft 365 w środowiskach GCC High i DoD wyłączy protokoły TLS 1.1 i 1.0.

Do 15 stycznia 2020 r. wszystkie kombinacje serwerów klienckich i serwerów przeglądarki powinny używać protokołu TLS w wersji 1.2 (lub nowszej), aby upewnić się, że wszystkie połączenia mogą być nawiązywane bez problemów z Microsoft 365. Może to wymagać aktualizacji niektórych kombinacji serwerów klienckich i serwerów przeglądarki.

W przypadku SharePoint i OneDrive należy zaktualizować i skonfigurować platformę .NET do obsługi protokołu TLS 1.2. Aby uzyskać informacje, zobacz [Jak włączyć protokół TLS 1.2 na klientach](/mem/configmgr/core/plan-design/security/enable-tls-1-2-client).

Należy zaktualizować komputery klienckie, aby zapewnić nieprzerwany dostęp do Office 365 GCC High i DoD.

Aby korzystać z protokołu TLS 1.2, należy zaktualizować aplikacje wywołujące interfejsy API Microsoft 365 za pośrednictwem protokołu TLS 1.0 lub TLS 1.1. Wartość domyślna platformy .NET 4.5 to TLS 1.1. Aby zaktualizować konfigurację platformy .NET, zobacz [Jak włączyć protokół Transport Layer Security (TLS) 1.2 na klientach](/mem/configmgr/core/plan-design/security/enable-tls-1-2-client). Aby uzyskać więcej informacji, zobacz [Przygotowywanie do obowiązkowego użycia protokołu TLS 1.2 w Office 365](https://support.microsoft.com/help/4057306/preparing-for-tls-1-2-in-office-365).

Wiemy, że następujące aplikacje klienckie nie mogą używać protokołu TLS 1.2:

- Access 4.3 i starsze wersje
- Firefox wersja 5.0 i starsze wersje
- Program Internet Explorer 8-10 w systemach Windows 7 i starszych wersjach
- Internet Explorer 10 w Windows Phone 8.0
- Safari 6.0.4/OS X 10.8.4 i starsze wersje

Chociaż bieżąca analiza połączeń z usługami Microsoft Online pokazuje, że większość usług i punktów końcowych widzi niewielkie użycie protokołów TLS 1.1 i 1.0, powiadamiamy o tej zmianie, aby można było zaktualizować wszystkich klientów lub serwerów, których dotyczy problem, w razie potrzeby przed zakończeniem obsługi protokołu TLS 1.1 i 1.0. Jeśli używasz dowolnej infrastruktury lokalnej w scenariuszach hybrydowych lub Active Directory Federation Services (AD FS), upewnij się, że infrastruktura może obsługiwać zarówno połączenia przychodzące, jak i wychodzące korzystające z protokołu TLS 1.2 (lub nowszej wersji).

Oprócz awarii, które mogą wystąpić, jeśli używasz wymienionych klientów, którzy nie mogą korzystać z protokołu TLS 1.2, usunięcie protokołów TLS 1.1 i 1.0 uniemożliwi korzystanie z następującego produktu firmy Microsoft:

- Telefon programu Lync

## <a name="references"></a>Informacje

Aby uzyskać wskazówki i odwołania, aby upewnić się, że klienci korzystają z protokołu TLS 1.2, zobacz [Przygotowywanie do obowiązkowego użycia protokołu TLS 1.2 w Office 365](https://support.microsoft.com/help/4057306/preparing-for-tls-1-2-in-office-365).
