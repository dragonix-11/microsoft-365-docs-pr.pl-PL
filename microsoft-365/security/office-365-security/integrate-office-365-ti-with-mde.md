---
title: Używanie programu Microsoft Defender dla Office 365 wraz z programem Microsoft Defender for Endpoint
f1.keywords:
- NOCSH
keywords: Integracja, Microsoft Defender, Microsoft Defender for Endpoint
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
description: Używaj programu Microsoft Defender dla Office 365 wraz z programem Microsoft Defender for Endpoint, aby uzyskać bardziej szczegółowe informacje o zagrożeniach dla Twoich urządzeń i zawartości poczty e-mail.
ms.custom:
- seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 67406984e73f39858f4a7329a8c8520fcd35ac5c
ms.sourcegitcommit: 4c207a9bdbb6c8ba372ae37907ccefca031a49f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2022
ms.locfileid: "63027030"
---
# <a name="use-microsoft-defender-for-office-365-together-with-microsoft-defender-for-endpoint"></a>Używanie programu Microsoft Defender dla Office 365 wraz z programem Microsoft Defender for Endpoint

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


[Program Microsoft Defender dla Office 365](defender-for-office-365.md) można skonfigurować do współpracy z programem [Microsoft Defender for Endpoint](/windows/security/threat-protection).

Integracja programu Microsoft Defender for Office 365 z programem Microsoft Defender for Endpoint może ułatwić zespołowi ds. bezpieczeństwa monitorowanie i szybkie działanie w przypadku zagrożenia urządzeń użytkowników. Na przykład po włączeniu integracji Twój zespół operacyjny ds. zabezpieczeń będzie mógł zobaczyć urządzenia, na które potencjalnie wpływa wykryta wiadomość e-mail, a także ile ostatnio wygenerowanych alertów dla tych urządzeń zostało wygenerowanych w programie Microsoft Defender for Endpoint.

Na poniższej ilustracji przedstawiono, jak wygląda karta **Urządzenia** , gdy jest włączona integracja z programem Microsoft Defender for Endpoint:

![Po włączeniu programu Microsoft Defender for Endpoint możesz wyświetlić listę urządzeń z alertami.](../../media/fec928ea-8f0c-44d7-80b9-a2e0a8cd4e89.PNG)

W tym przykładzie widać, że adresaci wykrytej wiadomości e-mail mają cztery urządzenia i jedno z nich ma alert. Kliknięcie linku dla urządzenia spowoduje otwarcie jego strony w Microsoft 365 Defender [sieci Web](/microsoft-365/security/defender/microsoft-365-defender).

> [!TIP]
> Portal Microsoft 365 Defender zastępuje Centrum zabezpieczeń usługi Microsoft Defender. Zobacz [Program Microsoft Defender dla punktu końcowego w Microsoft 365 Defender](../defender/microsoft-365-security-center-mde.md).

## <a name="requirements"></a>Wymagania

- Twoja organizacja musi mieć program Microsoft Defender for Office 365 (lub Office 365 E5) i Microsoft Defender for Endpoint.

- Administrator globalny lub administrator zabezpieczeń musi mieć przypisaną rolę administratora globalnego lub administratora zabezpieczeń w Microsoft 365. Aby uzyskać więcej informacji, [zobacz Uprawnienia w portalu Microsoft 365 Defender użytkowników](permissions-microsoft-365-security-center.md).

- Musisz mieć dostęp do [Eksploratora (lub wykrywania w czasie rzeczywistym).](threat-explorer.md)

## <a name="to-integrate-microsoft-defender-for-office-365-with-microsoft-defender-for-endpoint"></a>Aby zintegrować program Microsoft Defender dla Office 365 z programem Microsoft Defender for Endpoint

Integracja programu Microsoft Defender for Office 365 z usługą Microsoft Defender for Endpoint jest  skonfigurowania zarówno w programie Defender for Endpoint, jak i Defender for Office 365.

1. Przejdź do Microsoft 365 Defender konta ([https://security.microsoft.com](https://security.microsoft.com)) i zaloguj się.

2. Przejdź do **eksploratora współpracy & e-mail**\>. 

3. Na stronie **Eksplorator** w prawym górnym rogu ekranu wybierz pozycję **MdE Ustawienia**.

3. W **wyświetlonym wysuwam połączeniu programu Microsoft Defender for Endpoint** włącz opcję Połączenie do programu **Microsoft Defender dla** punktu końcowego (![włączoną](../../media/scc-toggle-on.png)), a następnie wybierz **pozycję Zamknij**.

    :::image type="content" source="../../media/explorer-mdeconnection-dialognew.png" alt-text="Połączenie MDE.":::

4. W okienku nawigacji wybierz pozycję **Ustawienia**. Na stronie **Ustawienia** punkt **końcowy**

5. Na **otwartej stronie Punkty** końcowe wybierz pozycję **Funkcje zaawansowane**.

6. Przewiń w dół **Office 365 połączenie analizy** zagrożeń i włącz je (![włącz).](../../media/scc-toggle-on.png)

   Po zakończeniu wybierz pozycję Zapisz **preferencje**.

## <a name="see-also"></a>Zobacz też

[Możliwości analizy zagrożeń i reakcji w Office 365](office-365-ti.md)

[Usługa Microsoft Defender dla Office 365](defender-for-office-365.md)

[Ochrona punktu końcowego w usłudze Microsoft Defender](/windows/security/threat-protection)
