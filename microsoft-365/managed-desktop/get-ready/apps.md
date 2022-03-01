---
title: Aplikacje w aplikacji Microsoft Managed Desktop
description: W tym artykule wyjaśniono, jak są obsługiwane aplikacje, w tym jak je spakować, wdrożyć i obsługiwać.
keywords: Microsoft Managed Desktop, Microsoft 365, usługa, dokumentacja
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
audience: Admin
ms.openlocfilehash: ce43080c284c4c15be5a8799f70a43de611ff9ba
ms.sourcegitcommit: cafca45069819a44c7cf8c67f6c1e105de1b3393
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/10/2022
ms.locfileid: "63027101"
---
# <a name="apps-in-microsoft-managed-desktop"></a>Aplikacje w aplikacji Microsoft Managed Desktop

<!--This topic is the target for 2 "Learn more" links in the Admin Portal (aka.ms/app-overview;app-package); also target for link from Online resources (aka.ms/app-overviewmmd-app-prep) do not delete.-->

<!--Applications: supported/onboard/deployment -->

## <a name="apps-generally"></a>Ogólnie rzecz biorąc, aplikacje

Firma Microsoft zawiera pewne kluczowe aplikacje wraz z licencją Microsoft 365 E3 lub E5, która jest potrzebna do uczestnictwa w programie Microsoft Managed Desktop. Mimo że te aplikacje są przez nas dostępne, nadal masz pewne obowiązki i działania do wykonania.

Możesz także wdrożyć u użytkowników dodatkowe aplikacje inne niż firmy Microsoft, korzystając z Portal firmy lub wymaganej instalacji w tle przy użyciu potoku wdrożenia Microsoft Intune firmy Microsoft.

## <a name="apps-provided-by-microsoft"></a>Aplikacje udostępniane przez firmę Microsoft

Do Twojej licencji Microsoft Managed Desktop są dołączone 64-bitowe wersje aplikacji pakietu Aplikacje Microsoft 365 dla systemu Enterprise Standard Suite (Word, Excel, PowerPoint, Outlook, Publisher, Access, Teams i OneNote).

Wersje wersji programu Microsoft Project i Visio w wersji "Kliknij, aby uruchomić" nie  są domyślnie uwzględniane, ale możesz zażądać ich dodania. Aby uzyskać więcej informacji o tych aplikacjach, zobacz [Instalowanie aplikacji Microsoft Project microsoft Visio na Microsoft Managed Desktop urządzeniach](../get-started/project-visio.md).

### <a name="what-microsoft-does-to-support-the-apps-we-provide"></a>Co firma Microsoft robi w celu obsługi zapewnianych przez nas aplikacji

Firma Microsoft zapewni pełną obsługę wdrażania, aktualizacji i pomocy technicznej dla uwzględnionych Aplikacje Microsoft 365 dla przedsiębiorstw aplikacji. Wersje wersji programu Microsoft Project i Visio *w* trybie "Kliknij, aby uruchomić" nie są domyślnie uwzględniane. Jednak Microsoft Managed Desktop udostępni grupy wdrażania, aby umożliwić administratorowi IT zarządzanie licencjami i wdrożyć te aplikacje odpowiednio dla Twojej organizacji. Firma Microsoft będzie obsługiwać użytkowników tych aplikacji za pośrednictwem Microsoft Managed Desktop kanałów pomocy technicznej.

### <a name="what-you-need-to-do-to-support-the-apps-we-provide"></a>Co należy zrobić, aby obsługiwać zapewniane przez nas aplikacje

Nadal są pewne czynności, które należy wykonać w przypadku tych aplikacji:

| Zadanie | Opis |
| ------ | ------ |
| Przypisz licencje | Odpowiadasz za uzyskiwanie i przypisywanie użytkownikom odpowiednich licencji na Aplikacje Microsoft 365 dla przedsiębiorstw. |
| Dodawanie użytkowników do grup zabezpieczeń | Jeśli używasz programu Microsoft Project lub Visio, administrator IT musi dodać tych użytkowników do odpowiednich grup wdrożeń. Administratorzy IT są również odpowiedzialni za odzyskanie licencji od tych użytkowników, jeśli opuszczają firmę. |
| Wdrażanie Microsoft 365 dodatków | Jeśli potrzebujesz jakichkolwiek dodatków dla dowolnej aplikacji pakietu Aplikacje Microsoft 365 dla przedsiębiorstw, wdeksuj je centralnie, tak jak każdą inną Windows 32.

## <a name="apps-you-provide"></a>Aplikacje, które ty dostarczasz

Prawdopodobnie masz inne aplikacje potrzebne do prowadzenia działalności biznesowej. Te aplikacje można wdrożyć tylko na Microsoft Managed Desktop urządzeniach wyłącznie Microsoft Intune potoku wdrożenia. Aby uzyskać więcej informacji na temat wdrażania aplikacji, postępuj zgodnie z instrukcjami w tece [Wdrażanie aplikacji na Microsoft Managed Desktop urządzeniach](../get-started/deploy-apps.md).

### <a name="preparing-your-own-apps-for-inclusion-in-microsoft-managed-desktop"></a>Przygotowywanie własnych aplikacji do uwzględnienia w Microsoft Managed Desktop

Przejrzyj aplikacje, sprawdzając:

- Żadna z tych aplikacji nie jest zabroniona ani nie ma zachowania ograniczonego, jak to opisano [Microsoft Managed Desktop wymagania dotyczące aplikacji](../service-description/mmd-app-requirements.md).
- Aplikacje muszą być gotowe do zarządzania przez Microsoft Intune. Aby uzyskać więcej informacji, [zobacz Windows 10 wdrażania](/intune/apps-windows-10-app-deploy) aplikacji przy Microsoft Intune [i Dodawanie aplikacji do Microsoft Intune](/intune/apps-add).
- Inne wymagania dotyczące wstępnego pakowania, takie jak dostarczanie kluczy licencji, umowa z postanowieniami licencyjnymi i wstępne konfigurowanie połączeń z serwerem.

## <a name="steps-to-get-ready-for-microsoft-managed-desktop"></a>Procedura przygotuj się do Microsoft Managed Desktop

1. Przejrzyj [wymagania wstępne dotyczące Microsoft Managed Desktop](prerequisites.md).
1. Uruchom [narzędzia do oceny gotowości](readiness-assessment-tool.md).
1. Kup [Portal firmy](../get-started/company-portal.md).
1. Przejrzyj [wymagania wstępne dotyczące kont gości](guest-accounts.md).
1. Sprawdź [konfigurację sieci](network.md).
1. [Przygotowywanie certyfikatów i profilów sieci](certs-wifi-lan.md).
1. [Przygotowywanie dostępu użytkownika do danych](authentication.md).
1. Przygotowywanie aplikacji (ten artykuł).
1. [Przygotowywanie zamapowanych dysków](mapped-drives.md).
1. [Przygotowywanie zasobów do drukowania](printing.md).
1. Nazwy [urządzeń adresowych](address-device-names.md).
