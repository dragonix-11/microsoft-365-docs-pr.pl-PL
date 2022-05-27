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
description: 'Podsumowanie: Office 365 GCC High i DoD mają dodatkowe wymagania dotyczące zabezpieczeń sieci'
hideEdit: true
ms.openlocfilehash: 86d3eb3fb4db42eda2be0c2c66fc754fbfd35f1e
ms.sourcegitcommit: 6a981ca15bac84adbbed67341c89235029aad476
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2022
ms.locfileid: "65754273"
---
# <a name="additional-network-security-requirements-for-office-365-gcc-high-and-dod"></a>Dodatkowe wymagania dotyczące zabezpieczeń sieci dla usługi Office 365 GCC High i DoD

*Ten artykuł dotyczy Office 365 GCC High, Office 365 DOD, Microsoft 365 GCC High i Microsoft 365 DOD.*

Office 365 GCC High i DOD to bezpieczne środowiska w chmurze, które spełniają potrzeby Stany Zjednoczone Government oraz jej dostawców i wykonawców.  Te środowiska w chmurze mają dodatkowe ograniczenia sieci, do których mogą uzyskiwać dostęp zewnętrzne punkty końcowe usług.

GCC klienci o wysokiej dostępności i dod planujących korzystanie z tożsamości federacyjnych lub współistnienia hybrydowego mogą wymagać od firmy Microsoft zezwolenia na dostęp przychodzący i/lub wychodzący do istniejących wdrożeń lokalnych.  Przykłady tych działań obejmują:

* Korzystanie z tożsamości federacyjnych (z Active Directory Federation Services lub podobnym obsługiwanym usługą STS)
* Współistnienie hybrydowe z lokalnym wdrożeniem Exchange Server lub Skype dla firm
* Migracja istniejącej zawartości użytkownika z systemu lokalnego

Aby umożliwić usłudze komunikowanie się z lokalnymi punktami końcowymi, **należy wysłać** wiadomość e-mail do Office 365 inżynierów w celu wprowadzenia zmian w sieci.

> [!WARNING]
> Wszystkie żądania mają **trzytygodniową** umową SLA i nie mogą być przyspieszone ze względu na wymagane mechanizmy kontroli zabezpieczeń i zgodności oraz potoki wdrażania.  Obejmuje to początkowe żądania sieciowe dołączania, a także wszelkie zmiany po migracji do usługi.  Upewnij się, że zespoły sieciowe wiedzą o tej osi czasu i uwzględniją ją w swoich cyklach planowania.

Wyślij wiadomość e-mail do [Office 365 dla instytucji rządowych Allow-List Requests z następującymi informacjami](mailto:o365gwlt@microsoft.com):

* **Do**: [Office 365 dla instytucji rządowych Allow-List żądań](mailto:o365gwlt@microsoft.com)
* **Od**: Administrator dzierżawy — wyślij wiadomość e-mail **musi być** zgodna z kontaktem administratora globalnego w dzierżawie
* **Temat wiadomości e-mail**: Office 365 GCC żądanie wysokiej sieci — contoso.onmicrosoft.us (zastąp ciąg nazwą dzierżawy)

Treść wiadomości powinna zawierać następujące dane:

* Nazwa dzierżawy usługi Microsoft Online Services (na przykład contoso.onmicrosoft.com, fabrikam.onmicrosoft.us)
* Lista dystrybucyjna wiadomości e-mail, z którą firma Microsoft będzie komunikować się w celu komunikacji w trybie ciągłej komunikacji związanej ze zmianami sieci i/lub kontynuacją nieprawidłowych podsieci
* Określ, czy zamierzasz używać Microsoft Teams współistnienia hybrydowego z wdrożeniami lokalnymi
* Adres URL systemu tożsamości federacyjnej dostępny zewnętrznie (na przykład sts.contoso.com) i zakres adresów IP w notacji CIDR (na przykład. 10.1.1.0/28)
* Lokalny adres URL listy odwołania certyfikatów PKI i zakres adresów IP w notacji CIDR
* Zewnętrznie dostępny adres URL i zakres adresów IP dla Exchange Server wdrożenia lokalnego w notacji CIDR
* Zewnętrznie dostępny adres URL i zakres adresów IP dla Skype dla firm wdrożenia lokalnego w notacji CIDR

Ze względów bezpieczeństwa i zgodności należy pamiętać o następujących ograniczeniach dotyczących żądania:

* Istnieje ograniczenie czterech podsieci na dzierżawę
* Podsieci muszą znajdować się w notacji CIDR (na przykład 10.1.1.0/28)
* Zakresy podsieci nie mogą być większe niż /24
* Nie **możemy** uwzględnić żądań zezwalania na dostęp do komercyjnych usług w chmurze (komercyjnych Office 365, Google G-Suite, Amazon Web Services itp.)

Po otrzymaniu i zatwierdzeniu żądania przez firmę Microsoft istnieje trzytygodniowa umowa SLA na potrzeby implementacji i nie można jej przyspieszyć.  Otrzymasz początkowe potwierdzenie, gdy otrzymamy Twoje żądanie i ostateczne potwierdzenie po jego zakończeniu.
