---
title: Omówienie integracji usługi Microsoft Defender for Cloud Apps
ms.reviewer: ''
description: Program Microsoft Defender for Endpoint integruje się z usługą Defender for Cloud Apps, przesyłając dalej wszystkie działania sieciowe aplikacji w chmurze.
keywords: chmura, aplikacja, sieć, widoczność, użycie
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
ms.topic: conceptual
ms.date: 10/18/2018
ms.technology: mde
ms.openlocfilehash: d3cf5259aeb070175d5d2a4a95154974c6cd4d56
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/12/2022
ms.locfileid: "63020860"
---
# <a name="microsoft-defender-for-cloud-apps-in-defender-for-endpoint-overview"></a>Omówienie programu Microsoft Defender dla aplikacji w chmurze w usłudze Defender dla punktu końcowego

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

[!include[Prerelease information](../../includes/prerelease.md)]

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Program Microsoft Defender dla aplikacji w chmurze to kompleksowe rozwiązanie, które zapewnia wgląd w aplikacje i usługi w chmurze, umożliwiając kontrolowanie i ograniczanie dostępu do aplikacji w chmurze, jednocześnie wymuszając wymagania dotyczące zgodności danych przechowywanych w chmurze. Aby uzyskać więcej informacji, zobacz [Defender for Cloud Apps](/cloud-app-security/what-is-cloud-app-security).

> [!NOTE]
> Ta funkcja jest dostępna z licencją E5 dla pakietu [Enterprise Mobility + Security](https://www.microsoft.com/cloud-platform/enterprise-mobility-security) na urządzeniach z systemem Windows 10 w wersji 1809 lub nowszej albo Windows 11.

## <a name="microsoft-defender-for-endpoint-and-defender-for-cloud-apps-integration"></a>Integracja programu Microsoft Defender dla punktu końcowego i programu Defender dla aplikacji w chmurze

Usługa Defender dla aplikacji w chmurze korzysta z dzienników ruchu w chmurze przesyłanych dalej z zapory przedsiębiorstwa i serwerów proxy. Program Microsoft Defender for Endpoint integruje się z usługą Defender for Cloud Apps, zbierając i przesyłając dalej wszystkie działania sieciowe aplikacji w chmurze, zapewniając wyjątkową widoczność użycia aplikacji w chmurze. Funkcja monitorowania jest wbudowana w urządzenie, zapewniając pełny zakres aktywności sieciowej.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4r4yQ]

Integracja zapewnia następujące znaczne ulepszenia istniejącego odnajdowania usługi Defender dla aplikacji w chmurze:

- Dostępne wszędzie — ponieważ aktywność sieciowa jest zbierana bezpośrednio z punktu końcowego, jest dostępna niezależnie od tego, gdzie urządzenie znajduje się, w sieci firmowej lub poza siecią firmową, ponieważ nie jest już zależne od ruchu kierowanego przez zaporę przedsiębiorstwa lub serwery proxy.

- Działa od  pudełku, konfiguracja nie jest wymagana — przesyłanie dalej dzienników ruchu w chmurze do usługi Defender dla aplikacji w chmurze wymaga konfiguracji zapory i serwera proxy. Dzięki integracji usług Defender for Endpoint i Defender for Cloud Apps nie jest wymagana konfiguracja. Po prostu włącz ją w Microsoft 365 Defender ustawienia i możesz to zrobić.

- Kontekst urządzenia — dzienniki ruchu w chmurze nie mają kontekstu urządzenia. Aktywność sieciowa usługi Defender for Endpoint jest raportowana w kontekście urządzenia (które urządzenie uzyskało dostęp do aplikacji w chmurze), więc oprócz tego, kto (użytkownik) wykonał dane działanie sieciowe, można dokładnie zrozumieć, gdzie (na urządzeniu) miała miejsce aktywność sieciowa.

Aby uzyskać więcej informacji na temat odnajdowania chmury, zobacz [Praca z wykrytymi aplikacjami](/cloud-app-security/discovered-apps).

## <a name="related-topic"></a>Temat pokrewny

- [Konfigurowanie integracji usługi Microsoft Defender dla aplikacji w chmurze](microsoft-cloud-app-security-config.md)
