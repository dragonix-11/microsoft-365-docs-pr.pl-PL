---
title: Konfigurowanie powiadomień alertów wysyłanych do msSP
description: Konfigurowanie powiadomień alertów wysyłanych do msSP
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
ms.openlocfilehash: 0cead78048fcf8ef25637e969aae816b7a8d8e76
ms.sourcegitcommit: dfa9f28a5a5055a9530ec82c7f594808bf28d0dc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/29/2021
ms.locfileid: "62996776"
---
# <a name="configure-alert-notifications-that-are-sent-to-mssps"></a>Konfigurowanie powiadomień alertów wysyłanych do msSP

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-mssp-support-abovefoldlink)

> [!NOTE]
> Ten krok może wykonać klient mssp lub mssp. Do konfigurowania tego w imieniu klienta MSSP należy przyznać odpowiednie uprawnienia.

Po przyznaniu dostępu do portalu można utworzyć reguły powiadomień alertów, aby po utworzeniu alertów skojarzonych z dzierżawą zostały utworzone alerty i zostały spełnione określone warunki.

Aby uzyskać więcej informacji, [zobacz Tworzenie reguł powiadomień alertów](configure-email-notifications.md#create-rules-for-alert-notifications).

Należy sprawdzić następujące pola wyboru:

- **Dołącz nazwę organizacji** — nazwa klienta zostanie dodana do powiadomień e-mail
- **Dołącz link do portalu specyficznego** dla dzierżawy — adres URL linku alertu będzie zawierać parametr dzierżawy (tid=target_tenant_id), który umożliwia bezpośredni dostęp do portalu dzierżawy docelowej

## <a name="related-topics"></a>Tematy pokrewne

- [Udzielanie dostępu do portalu przez program MSSP](grant-mssp-access.md)
- [Uzyskiwanie dostępu do portalu klientów programu MSSP](access-mssp-portal.md)
- [Pobieranie alertów z dzierżawy klienta](fetch-alerts-mssp.md)
