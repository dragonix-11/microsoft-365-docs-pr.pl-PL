---
title: Dodatkowe wymagania dotyczące zabezpieczeń sieci dla Office 365 GCC High i DoD
ms.author: dzazzo
author: dzazzo
manager: dzazzo
ms.date: 05/19/2020
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom: Adm_O365
search.appverid:
- OGA150m
- OGC150
- OGD150
- MOE150
ms.assetid: ''
description: 'Podsumowanie: Office 365 GCC i DoD mają dodatkowe wymagania dotyczące zabezpieczeń sieci'
hideEdit: true
ms.openlocfilehash: c4fbfc52085b634329130c2785ce683109b8febe
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62985629"
---
# <a name="additional-network-security-requirements-for-office-365-gcc-high-and-dod"></a>Dodatkowe wymagania dotyczące zabezpieczeń sieci dla Office 365 GCC High i DOD

*Ten artykuł dotyczy najwyższego Office 365 GCC, Office 365 DOD, Microsoft 365 GCC i Microsoft 365 DOD.*

Office 365 GCC High and DOD to bezpieczne środowiska w chmurze zaspokajane przez rząd Stanów Zjednoczonych oraz jego dostawców i wykonawców.  W tych środowiskach w chmurze obowiązują dodatkowe ograniczenia sieciowe, do których mają dostęp zewnętrzne punkty końcowe, do których mogą uzyskać dostęp usługi.

GCC klienci korzystający z usługi High and DOD, którzy planują korzystać z tożsamości federujących lub współistnienia hybrydowego, mogą wymagać od firmy Microsoft zezwolenia na dostęp przychodzący i/lub wychodzący do Twoich istniejących wdrożeń lokalnych.  Oto przykłady tych działań:

* Korzystanie z tożsamości federowanych (z usługami federacyjną Active Directory lub podobnymi obsługiwanymi usługami STS)
* Współistnienie hybrydowe z wdrożeniem lokalnym programu Exchange Server lub Skype dla firm lokalnym
* Migracja istniejącej zawartości użytkownika z systemu lokalnego

Aby zezwolić usłudze na komunikowanie się z lokalnymi punktami końcowymi, musisz wysłać wiadomość e-mail Office 365 inżyniera w celu zmiany sieci.

> [!WARNING]
> Wszystkie żądania mają **t-tygodniową** sla i nie można ich przyspieszyć ze względu na wymagane mechanizmy kontroli zabezpieczeń i zgodności oraz potoki wdrażania.  Obejmuje to wstępne dołączanie żądań sieciowych, a także wszelkie zmiany po migracji do usługi.  Upewnij się, że zespoły sieciowe wiedzą o tej osi czasu i uwzględnij ją w cyklach planowania.

Wyślij wiadomość e-mail [do Office 365 dla instytucji rządowych Allow-List prośby](mailto:o365gwlt@microsoft.com) o następujące informacje:

* **Do**: [Office 365 dla instytucji rządowych Allow-List wniosków](mailto:o365gwlt@microsoft.com)
* **Od**: Administrator dzierżawy — wysyłanie wiadomości e-mail **musi** być zgodne z kontaktem administratora globalnego w dzierżawie
* **Temat wiadomości e** Office 365 GCC e-mail: żądanie dużej contoso.onmicrosoft.us sieciowe — contoso.onmicrosoft.us (zamienianie na nazwę Twojej dzierżawy)

Treść wiadomości powinna zawierać następujące dane:

* Nazwa dzierżawy usług Microsoft Online Services (na przykład contoso.onmicrosoft.com, fabrikam.onmicrosoft.us)
* Lista dystrybucyjna poczty e-mail, z która firma Microsoft będzie komunikować w celu komunikacji w ruchu w związku ze zmianami sieci i/lub działań w przypadku nieprawidłowych podsieci
* Wskazuje, czy planujesz używać Microsoft Teams hybrydowych z wdrożeniami lokalnymi
* Adres URL (na przykład adres URL usługi sts.contoso.com) i zakres adresów IP w notacji CIDR (na przykład w systemie tożsamości federacji). 10.1.1.0/28)
* Adres URL listy odwołań certyfikatów i zakres adresów IP lokalnej listy odwołań certyfikatów PKI w notacji CIDR
* Zewnętrznie dostępny adres URL i zakres adresów IP Exchange Server wdrożenia lokalnego w notacji CIDR
* Zewnętrznie dostępny adres URL i zakres adresów IP dla Skype dla firm wdrożenia lokalnego w notacji CIDR

Ze względów bezpieczeństwa i zgodności pamiętaj o następujących ograniczeniach dotyczących Twojego żądania:

* Istnieje cztery ograniczenie podsieci na dzierżawę
* Podsieci muszą być w notacji CIDR (na przykład 10.1.1.0/28)
* Zakresy podsieci nie mogą być większe niż /24
* Nie **możemy uwzględniać** żądań zezwalania na dostęp do komercyjnych usług w chmurze (komercyjnych usług Office 365, Google G-Suite, Amazon Web Services itp.).

Po otrzymaniu i zatwierdzeniu żądania przez firmę Microsoft 3-tygodniowa umowa SLA jest na jej wdrożenie i nie można jej przyspieszyć.  Po otrzymaniu prośby otrzymasz potwierdzenie wstępne i potwierdzanie końcowe po jego ukończeniu.
