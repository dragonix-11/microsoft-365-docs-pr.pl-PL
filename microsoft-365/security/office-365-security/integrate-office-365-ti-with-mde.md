---
title: Użyj Ochrona usługi Office 365 w usłudze Microsoft Defender razem z Ochrona punktu końcowego w usłudze Microsoft Defender
f1.keywords:
- NOCSH
keywords: integrate, Microsoft Defender, Ochrona punktu końcowego w usłudze Microsoft Defender
ms.author: deniseb
author: denisebmsft
manager: dansimp
ms.date: 12/02/2021
audience: ITPro
ms.topic: article
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.collection:
- M365-security-compliance
description: Użyj Ochrona usługi Office 365 w usłudze Microsoft Defender razem z Ochrona punktu końcowego w usłudze Microsoft Defender, aby uzyskać bardziej szczegółowe informacje o zagrożeniach dla urządzeń i zawartości poczty e-mail.
ms.custom:
- seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 8df364538e6a799557956a8d624b0561c626e4fd
ms.sourcegitcommit: 45bc65972d4007b2aa7760d4457a0d2699f81926
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2022
ms.locfileid: "64971115"
---
# <a name="use-microsoft-defender-for-office-365-together-with-microsoft-defender-for-endpoint"></a>Użyj Ochrona usługi Office 365 w usłudze Microsoft Defender razem z Ochrona punktu końcowego w usłudze Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

[Ochrona usługi Office 365 w usłudze Microsoft Defender](defender-for-office-365.md) można skonfigurować do pracy z [Ochrona punktu końcowego w usłudze Microsoft Defender](/windows/security/threat-protection).

Integracja Ochrona usługi Office 365 w usłudze Microsoft Defender z Ochrona punktu końcowego w usłudze Microsoft Defender może pomóc zespołowi ds. operacji zabezpieczeń szybko monitorować i podejmować działania, jeśli urządzenia użytkowników są zagrożone. Na przykład po włączeniu integracji zespół ds. operacji zabezpieczeń będzie mógł zobaczyć urządzenia, na które może mieć wpływ wykryta wiadomość e-mail, a także liczbę ostatnio wygenerowanych alertów dla tych urządzeń w Ochrona punktu końcowego w usłudze Microsoft Defender.

Na poniższej ilustracji przedstawiono, jak wygląda karta **Urządzenia** po włączeniu integracji Ochrona punktu końcowego w usłudze Microsoft Defender:

:::image type="content" source="../../media/fec928ea-8f0c-44d7-80b9-a2e0a8cd4e89.PNG" alt-text="Lista urządzeń z alertami" lightbox="../../media/fec928ea-8f0c-44d7-80b9-a2e0a8cd4e89.PNG":::

W tym przykładzie widać, że adresaci wykrytej wiadomości e-mail mają cztery urządzenia, a jeden ma alert. Kliknięcie linku dla urządzenia spowoduje otwarcie jego strony w [portalu Microsoft 365 Defender](/microsoft-365/security/defender/microsoft-365-defender).

> [!TIP]
> Portal Microsoft 365 Defender zastępuje Centrum zabezpieczeń usługi Microsoft Defender. Zobacz [Ochrona punktu końcowego w usłudze Microsoft Defender w Microsoft 365 Defender](../defender/microsoft-365-security-center-mde.md).

## <a name="requirements"></a>Wymagania

- Organizacja musi mieć Ochrona usługi Office 365 w usłudze Microsoft Defender (lub Office 365 E5) i Ochrona punktu końcowego w usłudze Microsoft Defender.

- Musisz mieć przypisaną rolę administratora globalnego lub administratora zabezpieczeń w Microsoft 365. Aby uzyskać więcej informacji, zobacz [Uprawnienia w portalu Microsoft 365 Defender](permissions-microsoft-365-security-center.md).

- Musisz mieć dostęp do [Eksploratora (lub wykrywania w czasie rzeczywistym)](threat-explorer.md).

## <a name="to-integrate-microsoft-defender-for-office-365-with-microsoft-defender-for-endpoint"></a>Aby zintegrować Ochrona usługi Office 365 w usłudze Microsoft Defender z Ochrona punktu końcowego w usłudze Microsoft Defender

Integracja Ochrona usługi Office 365 w usłudze Microsoft Defender z Ochrona punktu końcowego w usłudze Microsoft Defender jest konfigurowana zarówno w usłudze Defender dla punktu końcowego, jak i Ochrona usługi Office 365 w usłudze Defender.

1. Przejdź do portalu Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) i zaloguj się.

2. Przejdź do **Eksploratora** współpracy \> **& poczty e-mail**.

3. Na stronie **Eksplorator** w prawym górnym rogu ekranu wybierz pozycję **MDE Ustawienia**.

3. W wyświetlonym **wysuwu połączenia Ochrona punktu końcowego w usłudze Microsoft Defender** włącz **Połączenie, aby Ochrona punktu końcowego w usłudze Microsoft Defender** (![Przełącznik włączony](../../media/scc-toggle-on.png)), a następnie wybierz pozycję **Zamknij**.

   :::image type="content" source="../../media/explorer-mdeconnection-dialognew.png" alt-text="Strona Połączenie MDE" lightbox="../../media/explorer-mdeconnection-dialognew.png":::

4. W okienku nawigacji wybierz **pozycję Ustawienia**. Na stronie **Ustawienia** wybierz pozycję **Punkty końcowe**

5. Na otwartej stronie **Punkty końcowe** wybierz pozycję **Funkcje zaawansowane**.

6. Przewiń w dół, aby **Office 365 połączenie analizy zagrożeń**, a następnie włączyć (![Włącz](../../media/scc-toggle-on.png)).

   Po zakończeniu wybierz pozycję **Zapisz preferencje**.

## <a name="see-also"></a>Zobacz też

[Możliwości badania zagrożeń i reagowania na nie w Office 365](office-365-ti.md)

[Ochrona usługi Office 365 w usłudze Microsoft Defender](defender-for-office-365.md)

[Ochrona punktu końcowego w usłudze Microsoft Defender](/windows/security/threat-protection)
