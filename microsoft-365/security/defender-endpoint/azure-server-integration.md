---
title: Integracja z usługą Microsoft Defender dla chmury
description: Dowiedz się więcej o integracji programu Microsoft Defender dla punktu końcowego z programem Microsoft Defender dla chmury
keywords: integracja, serwer, azure, 2012r2, 2016, 2019, dołączanie do serwera, zarządzanie urządzeniami, konfigurowanie programu Microsoft Defender dla serwerów punktów końcowych, dołączanie programu Microsoft Defender do serwerów punktów końcowych, dołączanie programu Microsoft Defender dla serwerów punktów końcowych
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
author: mjcaparas
ms.author: macapara
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 8bf51b744e294e4bb2740b3e437305629eb23c2a
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/12/2022
ms.locfileid: "63021323"
---
# <a name="integration-with-microsoft-defender-for-cloud"></a>Integracja z usługą Microsoft Defender dla chmury

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Microsoft Defender dla chmury

Program Microsoft Defender for Endpoint może zintegrować się z usługą Microsoft Defender for Cloud, aby zapewnić kompleksowe Windows ochrony serwera. Dzięki tej integracji usługa Microsoft Defender for Cloud może korzystać z funkcji programu Defender for Endpoint w celu zapewnienia ulepszonego wykrywania zagrożeń dla serwerów Windows końcowych.

W integracji uwzględniono następujące funkcje:

- Automatyczne dołączanie — czujnik programu Defender for Endpoint jest automatycznie włączony na Windows, które są włączone do programu Microsoft Defender dla chmury. Aby uzyskać więcej informacji na temat dołączania do usługi Microsoft Defender w chmurze, zobacz Korzystanie ze zintegrowanej licencji [programu Microsoft Defender dla punktu końcowego](/azure/security-center/security-center-wdatp).

    > [!NOTE]
    > Integracja między programem Microsoft Defender dla serwerów i programem Microsoft Defender for Endpoint została rozwinięta w celu obsługi programu [Windows Server 2019 i Windows Virtual Desktop (WVD)](/azure/security-center/release-notes#microsoft-defender-for-endpoint-integration-with-azure-defender-now-supports-windows-server-2019-and-windows-10-virtual-desktop-wvd-in-preview).

- Windows monitorowane przez program Microsoft Defender dla chmury będą również dostępne w programie Defender for Endpoint — usługa Microsoft Defender dla chmury bezproblemowo łączy się z dzierżawą usługi Defender for Endpoint, zapewniając jeden widok dla klientów i serwerów.  Ponadto alerty programu Defender dla punktu końcowego będą dostępne w konsoli programu Microsoft Defender dla chmury.
- Analiza serwera — klienci korzystający z usługi Microsoft Defender dla chmury mogą uzyskać dostęp do portalu Microsoft 365 Defender, aby przeprowadzić szczegółowe badania w celu odkrycia zakresu potencjalnego naruszenia.

> [!IMPORTANT]
> - Podczas monitorowania serwerów za pomocą programu Microsoft Defender for Cloud jest automatycznie tworzona dzierżawa usługi Defender dla punktu końcowego (w Stanach Zjednoczonych dla użytkowników w Ue europejskiej i Zjednoczonego Królestwa).<br>
Dane zbierane przez usługę Defender for Endpoint są przechowywane w lokalizacji geograficznej dzierżawy zidentyfikowana podczas inicjowania obsługi administracyjnej.
> - Jeśli używasz usługi Defender for Endpoint przed użyciem programu Microsoft Defender dla chmury, Twoje dane będą przechowywane w lokalizacji określonej podczas tworzenia dzierżawy, nawet jeśli w późniejszym czasie zintegrowasz ją z programem Microsoft Defender dla chmury.
> - Po skonfigurowaniu tej konfiguracji nie można zmienić lokalizacji przechowywania danych. Jeśli chcesz przenieść dane do innej lokalizacji, skontaktuj się z pomocą techniczną firmy Microsoft, aby zresetować dzierżawę. <br>
Monitorowanie punktu końcowego serwera korzystające z tej integracji zostało wyłączone dla Office 365 GCC klientów.



## <a name="related-topics"></a>Tematy pokrewne
- [Wniesienie poprzednich wersji Windows](onboard-downlevel.md)
- [Onboard Windows Server 2012 R2, 2016, JEGO wersja 1803 i 2019](configure-server-endpoints.md)
