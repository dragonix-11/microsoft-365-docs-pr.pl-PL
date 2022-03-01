---
title: Konfigurowanie zarządzanej pomocy usługodawca zabezpieczeń
description: Kroki niezbędne do skonfigurowania integracji programu MSSP z programem Microsoft Defender for Endpoint
keywords: zarządzane zabezpieczenia usługodawca, mssp, konfigurowanie, integracja
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 1a9a7e24bc08338549a78fcf9e9b2756701cd83f
ms.sourcegitcommit: dd6514ae173f1c821d4ec25298145df6cb232e2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2022
ms.locfileid: "63013285"
---
# <a name="configure-managed-security-service-provider-integration"></a>Konfigurowanie integracji zarządzanej usługodawca zabezpieczeń

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-mssp-support-abovefoldlink)

[!include[Prerelease information](../../includes/prerelease.md)]

Aby włączyć integrację usługi zarządzania zabezpieczeniami (MSSP, Managed Security Usługodawca MSSP), należy wykonać następujące czynności konfiguracyjne.

> [!NOTE]
> W tym artykule są używane następujące terminy do odróżniania klientów usługodawca usług:
>
> - MsSP: Organizacje zabezpieczeń, które oferują monitorowanie urządzeń zabezpieczających i zarządzanie nimi w organizacji.
> - Klienci z programem MSSP: Organizacje, które angażują się w świadczenie usług mssp.

Integracja umożliwi msips w celu podjęcia następujących działań:

- Uzyskiwanie dostępu do portalu Microsoft 365 Defender klienta MSSP
- Powiadomienia e-mail i
- Pobieranie alertów za pomocą narzędzi do zarządzania informacjami zabezpieczeń i zdarzeniami

Zanim mssp będą mieć możliwość podjęcia tych działań, klient msSP będzie musiał udzielić dostępu do swojej dzierżawy programu Defender dla punktu końcowego, aby program MSSP miał dostęp do portalu.

Zazwyczaj klienci korzystający z programu MSSP wstępnie krokują konfigurację, aby udzielić tym usługom dostępu do swoich Windows Defender Central zabezpieczeń. Po przyznaniu dostępu klient programu MSSP lub program MSSP może wykonać inne czynności konfiguracyjne.

Ogólnie rzecz biorąc, należy wykonać następujące czynności konfiguracyjne:

- **Udzielanie dostępu do usługi MSSP Microsoft 365 Defender**

  Tę czynność musi wykonać klient programu MSSP. Udziela ona dostępu do programu MSSP dzierżawcy programu Defender for Endpoint klienta MSSP.

- **Konfigurowanie powiadomień alertów wysyłanych do msSP**

  Tę czynność może podjąć klient programu MSSP lub program MSSP. Dzięki temu użytkownicy SPP będą wiedzieć, jakie alerty należy wyasyłać dla klienta MSSP.

- **Pobieranie alertów z dzierżawy klienta MSSP do systemu SIEM**

  To działanie jest podejmowane przez program MSSP. Umożliwia tym wiadomościom SSP pobieranie alertów w narzędziach SIEM.

- **Pobieranie alertów z dzierżawy klienta MSSP przy użyciu interfejsów API**

  To działanie jest podejmowane przez program MSSP. Umożliwia ono msp pobieranie alertów przy użyciu interfejsów API.

## <a name="multi-tenant-access-for-mssps"></a>Dostęp wielodostępny dla mssp

Aby uzyskać informacje na temat implementowania dostępu delegowanego wielodostępnego, zobacz Dostęp wielodostępny dla [dostawców zarządzanych usług zabezpieczeń](https://techcommunity.microsoft.com/t5/microsoft-defender-atp/multi-tenant-access-for-managed-security-service-providers/ba-p/1533440).

## <a name="related-topics"></a>Tematy pokrewne

- [Udzielanie dostępu do portalu przez program MSSP](grant-mssp-access.md)
- [Uzyskiwanie dostępu do portalu klientów programu MSSP](access-mssp-portal.md)
- [Konfigurowanie powiadomień alertów](configure-mssp-notifications.md)
- [Pobieranie alertów z dzierżawy klienta](fetch-alerts-mssp.md)
