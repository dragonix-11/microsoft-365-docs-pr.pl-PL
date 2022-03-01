---
title: Wyłączanie standardu TLS 1.0 i 1.1 w Microsoft 365 GCC i DoD
description: Omówiono, jak firma Microsoft wyłącza obsługę standardów TLS 1.1 i 1.0 w środowiskach GCC High and DoD w programie Microsoft 365.
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
ms.openlocfilehash: 29ee02c7c54fc7de6ee178f8219f7148a8cb4bfd
ms.sourcegitcommit: 19e16b16f144159b55bb4c544403e3642b69e335
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/15/2022
ms.locfileid: "63014757"
---
# <a name="disabling-tls-10-and-11-in-microsoft-365-gcc-high-and-dod"></a>Wyłączanie standardu TLS 1.0 i 1.1 w Microsoft 365 GCC i DoD

## <a name="summary"></a>Podsumowanie

W celu zachowania zgodności z najnowszymi standardami Federal Risk and Authorization Management Program (FedRAMP) wyłączamy wersje 1.1 i 1.0 zabezpieczeń warstwy transportu w środowiskach Microsoft 365 dla środowisk GCC High i DoD. Tę zmianę ogłoszono wcześniej za pośrednictwem pomocy technicznej firmy Microsoft w ramach przygotowań do obowiązkowego użycia ciągu [TLS 1.2 w Office 365](https://support.microsoft.com/help/4057306/preparing-for-tls-1-2-in-office-365).

Bezpieczeństwo Twoich danych jest ważne, dlatego dbamy o przejrzystość w zakresie zmian, które mogą mieć wpływ na korzystanie z usługi.

Implementacja [platformy Microsoft TLS 1.0](https://support.microsoft.com/help/3117336) nie ma żadnych znanych luk w zabezpieczeniach, ale nadal dbamy o standardy zgodności FedRAMP. Dlatego 15 stycznia 2020 r. wyłączyliśmy standard TLS 1.1 i 1.0 w Microsoft 365 w środowiskach wysokiego i dod w programach GCC DoD. Aby uzyskać informacje na temat usuwania zależności TLS 1.1 i 1.0, zobacz następujący oficjalny dokument:

[Rozwiązywanie problemu ZLS 1.0](https://www.microsoft.com/download/details.aspx?id=55266)

## <a name="more-information"></a>Więcej informacji

Począwszy od 15 stycznia 2020 r., Microsoft 365 w środowiskach GCC Wysokie i DoD będą wyłączane TLS 1.1 i 1.0.

Do 15 stycznia 2020 r. wszystkie kombinacje serwerów klienckich i serwerów przeglądarek powinny używać usługi TLS w wersji 1.2 (lub nowszej), aby zapewnić, że wszystkie połączenia można na bez problemów Microsoft 365. Może to wymagać aktualizacji niektórych kombinacji serwerów klienckich i serwerów przeglądarek.

W SharePoint i OneDrive musisz zaktualizować i skonfigurować program .NET na potrzeby obsługi TLS 1.2. Aby uzyskać informacje, [zobacz Jak włączyć funkcję TLS 1.2 w klientach](/mem/configmgr/core/plan-design/security/enable-tls-1-2-client).

Musisz zaktualizować komputery klienckie, aby upewnić się, że masz nieprzerwany dostęp do Office 365 GCC High i DoD.

Aby korzystać z TLS 1.2, należy zaktualizować aplikacje wywołujące interfejsy API usługi Microsoft 365 przez TLS 1.0 lub TLS 1.1. Program .NET 4.5 domyślnie ma wartość TLS 1.1. Aby zaktualizować konfigurację programu .NET, zobacz Jak włączyć na klientach transport [Layer Security (TLS) 1.2](/mem/configmgr/core/plan-design/security/enable-tls-1-2-client). Aby uzyskać więcej informacji, [zobacz Przygotowanie do obowiązkowego użycia TLS 1.2](https://support.microsoft.com/help/4057306/preparing-for-tls-1-2-in-office-365) w Office 365.

Wiemy, że następujące aplikacje klienckie nie mogą używać TLS 1.2:

- Access 4.3 i starsze wersje
- Firefox wersja 5.0 i starsze wersje
- Przeglądarka Internet Explorer 8–10 w Windows 7 i wcześniejszych wersjach
- Internet Explorer 10 on Windows Phone 8.0
- Safari 6.0.4/OS X 10.8.4 i wcześniejsze wersje

Mimo że bieżąca analiza połączeń z usługami Microsoft Online services pokazuje, że większość usług i punktów końcowych widzi niewielkie użycie serwerów TLS 1.1 i 1.0, jednak udostępniamy powiadomienie o tej zmianie, aby można było w razie potrzeby zaktualizować wszystkich klientów lub serwery, których to dotyczy, przed zakończeniem świadczenia pomocy technicznej dla serwerów TLS 1.1 i 1.0. Jeśli używasz dowolnej infrastruktury lokalnej na użytek scenariuszy hybrydowych lub usług federalnych Active Directory (AD FS), upewnij się, że ta infrastruktura może obsługiwać zarówno połączenia przychodzące, jak i wychodzące, które korzystają z usługi TLS 1.2 (lub nowszej).

Oprócz  usterek, które mogą wystąpić, jeśli korzystasz z wymienionych klientów, którzy nie mogą korzystać z usługi TLS 1.2, usunięcie adresów TLS 1.1 i 1.0 uniemożliwi korzystanie z następującego produktu firmy Microsoft:

- Telefon z programem Lync

## <a name="references"></a>Informacje

Aby uzyskać wskazówki i odwołania pomocne w upewniniu się, że klienci korzystają z technologii TLS 1.2, zobacz Przygotowanie do obowiązkowego użycia [TLS 1.2](https://support.microsoft.com/help/4057306/preparing-for-tls-1-2-in-office-365) w Office 365.