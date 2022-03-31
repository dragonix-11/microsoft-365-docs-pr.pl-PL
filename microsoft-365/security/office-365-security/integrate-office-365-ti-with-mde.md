---
title: Używanie Ochrona usługi Office 365 w usłudze Microsoft Defender jednocześnie z Ochrona punktu końcowego w usłudze Microsoft Defender
f1.keywords:
- NOCSH
keywords: integruj usługę Microsoft Defender, Ochrona punktu końcowego w usłudze Microsoft Defender
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
description: Używaj Ochrona usługi Office 365 w usłudze Microsoft Defender wraz z Ochrona punktu końcowego w usłudze Microsoft Defender, aby uzyskać bardziej szczegółowe informacje o zagrożeniach dla Twoich urządzeń i zawartości poczty e-mail.
ms.custom:
- seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: ef1f89a9b218e559855789d0beabad1bc947dad1
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2022
ms.locfileid: "64465932"
---
# <a name="use-microsoft-defender-for-office-365-together-with-microsoft-defender-for-endpoint"></a>Używanie Ochrona usługi Office 365 w usłudze Microsoft Defender jednocześnie z Ochrona punktu końcowego w usłudze Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


[Ochrona usługi Office 365 w usłudze Microsoft Defender](defender-for-office-365.md) można skonfigurować do [współpracy z Ochrona punktu końcowego w usłudze Microsoft Defender](/windows/security/threat-protection).

Integracja Ochrona usługi Office 365 w usłudze Microsoft Defender z programem Ochrona punktu końcowego w usłudze Microsoft Defender może ułatwić zespołowi ds. bezpieczeństwa monitorowanie i szybkie działanie w przypadku zagrożenia urządzeń użytkowników. Na przykład po włączeniu integracji Twój zespół operacyjny zabezpieczeń będzie mógł zobaczyć urządzenia, na które potencjalnie wpływa wykryta wiadomość e-mail, oraz ile ostatnio alertów dla tych urządzeń zostało wygenerowanych w aplikacji Ochrona punktu końcowego w usłudze Microsoft Defender.

Na poniższej ilustracji przedstawiono wygląd karty **Urządzenia** po włączeniu Ochrona punktu końcowego w usłudze Microsoft Defender integracji:

:::image type="content" source="../../media/fec928ea-8f0c-44d7-80b9-a2e0a8cd4e89.PNG" alt-text="Lista urządzeń z alertami" lightbox="../../media/fec928ea-8f0c-44d7-80b9-a2e0a8cd4e89.PNG":::

W tym przykładzie widać, że adresaci wykrytej wiadomości e-mail mają cztery urządzenia i jedno z nich ma alert. Kliknięcie linku dla urządzenia spowoduje otwarcie jego strony w Microsoft 365 Defender [sieci Web](/microsoft-365/security/defender/microsoft-365-defender).

> [!TIP]
> Portal Microsoft 365 Defender zastępuje Centrum zabezpieczeń usługi Microsoft Defender. Zobacz [Ochrona punktu końcowego w usłudze Microsoft Defender w programie Microsoft 365 Defender](../defender/microsoft-365-security-center-mde.md).

## <a name="requirements"></a>Wymagania

- Twoja organizacja musi mieć Ochrona usługi Office 365 w usłudze Microsoft Defender (lub Office 365 E5) i Ochrona punktu końcowego w usłudze Microsoft Defender.

- Administrator globalny lub administrator zabezpieczeń musi mieć przypisaną rolę administratora globalnego lub administratora zabezpieczeń w Microsoft 365. Aby uzyskać więcej informacji, [zobacz Uprawnienia w portalu Microsoft 365 Defender użytkowników](permissions-microsoft-365-security-center.md).

- Musisz mieć dostęp do [Eksploratora (lub wykrywania w czasie rzeczywistym).](threat-explorer.md)

## <a name="to-integrate-microsoft-defender-for-office-365-with-microsoft-defender-for-endpoint"></a>Aby zintegrować Ochrona usługi Office 365 w usłudze Microsoft Defender z Ochrona punktu końcowego w usłudze Microsoft Defender

Integracja programu Ochrona usługi Office 365 w usłudze Microsoft Defender z usługą Ochrona punktu końcowego w usłudze Microsoft Defender jest ustawiona zarówno w programie Defender for Endpoint, jak i Ochrona usługi Office 365 w usłudze Defender.

1. Przejdź do Microsoft 365 Defender konta ([https://security.microsoft.com](https://security.microsoft.com)) i zaloguj się.

2. Przejdź do **eksploratora współpracy & e-mail**\>. 

3. Na stronie **Eksplorator** w prawym górnym rogu ekranu wybierz pozycję **MdE Ustawienia**.

3. W **wyświetlonym Ochrona punktu końcowego w usłudze Microsoft Defender wysuwu** połączenia włącz opcję Połączenie, **Ochrona punktu końcowego w usłudze Microsoft Defender pozycję (**![](../../media/scc-toggle-on.png)Włącz), a następnie wybierz pozycję **Zamknij**.

   :::image type="content" source="../../media/explorer-mdeconnection-dialognew.png" alt-text="Strona Połączenie MDE" lightbox="../../media/explorer-mdeconnection-dialognew.png":::

4. W okienku nawigacji wybierz pozycję **Ustawienia**. Na stronie **Ustawienia** punkt **końcowy**

5. Na **otwartej stronie Punkty** końcowe wybierz pozycję **Funkcje zaawansowane**.

6. Przewiń w dół **Office 365 połączenie analizy** zagrożeń i włącz je (![włącz).](../../media/scc-toggle-on.png)

   Po zakończeniu wybierz pozycję Zapisz **preferencje**.

## <a name="see-also"></a>Zobacz też

[Możliwości analizy zagrożeń i reakcji w Office 365](office-365-ti.md)

[Ochrona usługi Office 365 w usłudze Microsoft Defender](defender-for-office-365.md)

[Ochrona punktu końcowego w usłudze Microsoft Defender](/windows/security/threat-protection)
