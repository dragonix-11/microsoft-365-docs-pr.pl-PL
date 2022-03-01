---
title: Wdrażaj aktualizacje dla ochrony punktu końcowego w usłudze Microsoft Defender na Linuxie
ms.reviewer: ''
description: W tym artykule opisano, jak wdrażać aktualizacje programu Microsoft Defender dla punktu końcowego w systemie Linux w środowiskach przedsiębiorstwa.
keywords: microsoft, defender, Microsoft Defender for Endpoint, linux, updates, deploy
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 71c689143feca3d8c87d219a55c4ea42b4f9d950
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2022
ms.locfileid: "63019232"
---
# <a name="deploy-updates-for-microsoft-defender-for-endpoint-on-linux"></a>Wdrażaj aktualizacje dla ochrony punktu końcowego w usłudze Microsoft Defender na Linuxie

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

Firma Microsoft regularnie publikuje aktualizacje oprogramowania w celu zwiększenia wydajności, zabezpieczeń i dostarczania nowych funkcji.

> [!WARNING]
> Każda wersja programu Defender for Endpoint w systemie Linux ma datę wygaśnięcia, po której nie będzie już chronić urządzenia. Należy zaktualizować produkt przed tą datą. Aby sprawdzić datę wygaśnięcia, uruchom następujące polecenie:
> ```bash
> mdatp health --field product_expiration
> ```


Ogólnie dostępny program Microsoft Defender for Endpoint capabilities jest odpowiedni niezależnie od kanału aktualizacji używanego dla wdrożenia (Beta (niejawny program testów), wersji Preview (zewnętrzne), bieżącej (produkcyjnej)).


Aby ręcznie zaktualizować program Defender dla punktu końcowego w systemie Linux, wykonaj jedno z następujących poleceń:

## <a name="rhel-and-variants-centos-and-oracle-linux"></a>R ZAO PRZYC i warianty (CentOS i Oracle Linux)

```bash
sudo yum update mdatp
```

## <a name="sles-and-variants"></a>SLES i warianty

```bash
sudo zypper update mdatp
```

## <a name="ubuntu-and-debian-systems"></a>Systemy Ubuntu i Debian

```bash
sudo apt-get install --only-upgrade mdatp
```

> [!IMPORTANT]
> Podczas integrowania usługi Microsoft Defender for Endpoint i Defender dla chmury agent mdatp automatycznie otrzymuje aktualizacje domyślnie.
