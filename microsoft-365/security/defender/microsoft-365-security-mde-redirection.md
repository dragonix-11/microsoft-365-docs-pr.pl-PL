---
title: Przekierowywanie kont z usługi Microsoft Defender for Endpoint do usługi Microsoft 365 Defender
description: Jak przekierować konta i sesje z usługi Defender for Endpoint do usługi Microsoft 365 Defender.
keywords: Microsoft 365 Defender Wprowadzenie do Microsoft 365 Defender, przekierowywanie centrum zabezpieczeń
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
ms.custom: admindeeplinkDEFENDER
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: 64a9926253ea699fa6cc62d1ec2d80d07f25fd29
ms.sourcegitcommit: 6f3bc00a5cf25c48c61eb3835ac069e9f41dc4db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2022
ms.locfileid: "63010375"
---
# <a name="redirecting-accounts-from-microsoft-defender-for-endpoint-to-microsoft-365-defender"></a>Przekierowywanie kont z usługi Microsoft Defender for Endpoint do usługi Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Dotyczy:**
- Microsoft 365 Defender
- Defender for Endpoint

Zgodnie z ujednoliceniem przez firmę Microsoft podejścia do ochrony przed zagrożeniami za pomocą SIEM oraz rozszerzonego wykrywania i odpowiedzi (XDR, Extended Detection and Response) firma Microsoft Defender dodała nazwę Advanced Threat Protection jako program Microsoft Defender for Endpoint i zsufikowała ją w jeden zintegrowany portal: Microsoft 365 Defender.

W tym przewodniku wyjaśniono, jak kierować konta do usługi Microsoft 365 Defender, włączając automatyczne przekierowywanie z byłego portalu programu Microsoft Defender dla punktów końcowych (securitycenter.windows.com lub securitycenter.microsoft.com) do <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a>.

> [!NOTE]
> Program Microsoft Defender for Endpoint w usłudze Microsoft 365 Defender obsługuje udzielanie dostępu do zarządzanych dostawców usług zabezpieczeń [(MSSP)](/windows/security/threat-protection/microsoft-defender-atp/grant-mssp-access) w taki sam sposób, jak dostęp jest udzielany w [Centrum zabezpieczeń usługi Microsoft Defender.](./mssp-access.md)

## <a name="what-to-expect"></a>Czego można się spodziewać

Po włączeniu automatycznego przekierowywania konta, które uzyskają dostęp do byłego portalu programu Microsoft Defender dla punktu końcowego w systemie securitycenter.windows.com lub securitycenter.microsoft.com, zostaną automatycznie przekierowane do portalu usługi Microsoft 365 Defender w witrynie <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank"><security.microsoft.com></a>.

Dowiedz się więcej o tym, co się zmieniło: [Program Microsoft Defender for Endpoint w programie Microsoft 365 Defender](microsoft-365-security-center-mde.md).

Obejmuje to przekierowanie bezpośredniego dostępu za pośrednictwem przeglądarki do poprzedniego portalu, w tym linki skierowane do poprzedniego portalu usługi securitycenter.windows.com — takie jak linki w powiadomieniach e-mail oraz linki zwracane przez połączenia interfejsu API SIEM.  

 Linki zewnętrzne z powiadomień e-mail lub interfejsów API SIEM obecnie zawierają linki do obu portali. Po włączeniu przekierowywania oba linki będą zawierać linki do Microsoft 365 Defender, aż stary link zostanie w końcu usunięty. Zachęcamy do przyjęcia nowego linku, który wskaże nowe Microsoft 365 Defender.

Skorzystaj z poniższej tabeli, aby uzyskać więcej informacji na temat linków i routingu.
## <a name="siem-api-routing"></a>Routing interfejsu API SIEM

| Właściwość | Miejsce docelowe, gdy przekierowanie jest WYŁĄCZONE | Miejsce docelowe, gdy przekierowanie jest WŁ. |
|---------|---------|---------|
| LinkToWDATP | Strona alertu w aplikacji securitycenter.windows.com | Strona alertu w aplikacji security.microsoft.com |
| IncidentLinkToWDATP | Strona zdarzenia w programie securitycenter.windows.com | Strona zdarzenia w aplikacji security.microsoft.com |
| LinkToMTP | Strona alertu w aplikacji security.microsoft.com | Strona alertu w aplikacji security.microsoft.com |
| IncidentLinkToMTP | Strona zdarzenia w aplikacji security.microsoft.com | Strona zdarzenia w aplikacji security.microsoft.com |

## <a name="email-alert-notifications"></a>Powiadomienia alertów e-mail

| Właściwość | Miejsce docelowe, gdy przekierowanie jest WYŁĄCZONE** | Miejsce docelowe, gdy przekierowanie jest WŁ. |
|---------|---------|---------|
| Strona alertu | Strona alertu w aplikacji securitycenter.windows.com | Strona alertu w aplikacji security.microsoft.com |
| Strona zdarzenia |Strona zdarzenia w programie securitycenter.windows.com | Strona zdarzenia w aplikacji security.microsoft.com |
| Strona alertu w portalu usługi Defender dla chmury | Strona alertu w aplikacji security.microsoft.com | Strona alertu w aplikacji security.microsoft.com |
| Strona zdarzenia w portalu usługi Defender dla chmury | Strona zdarzenia w aplikacji security.microsoft.com | Strona zdarzenia w aplikacji security.microsoft.com |

## <a name="when-does-this-take-effect"></a>Kiedy to się dzieje?

Po włączeniu ta aktualizacja może zostać niemal natychmiast włączona w przypadku niektórych kont. Jednak propagacja przekierowania może potrwać dłużej na każdym koncie w organizacji. Konta w aktywnych sesjach po zastosowaniu tego ustawienia nie zostaną wylogowane z ich sesji i zostaną kierowane tylko do usługi Microsoft 365 Defender po zakończeniu bieżącej sesji i zalogowaniu się ponownie.  

### <a name="set-up-portal-redirection"></a>Konfigurowanie przekierowywania portalu

Aby rozpocząć rozsyłanie kont w Microsoft 365 Defender:

1. Upewnij się, że jesteś administratorem globalnym lub masz uprawnienia administratora zabezpieczeń w programie Azure Active Directory.

2. Zaloguj się w <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a>.

3. Przejdź do **Ustawienia** >  **EndpointsGeneralPortal** >  >  **lub** [kliknij tutaj](https://security.microsoft.com/preferences2/portal_redirection).  

4. Przełącz ustawienie Automatyczne przekierowywanie na **Włącz**.

5. Kliknij **pozycję Włącz**, aby zastosować automatyczne przekierowywanie do Microsoft 365 Defender.

>[!IMPORTANT]
>Włączenie tego ustawienia nie spowoduje zakończenia aktywnych sesji użytkowników. Konta, które są w aktywnej sesji, gdy to ustawienie jest stosowane, będą kierowane do usługi Microsoft 365 Defender tylko po zakończeniu bieżącej sesji i zalogowaniu się ponownie.

>[!NOTE]
>Aby włączyć lub wyłączyć to ustawienie, musisz być Azure Active Directory administratorem globalnym lub mieć uprawnienia administratora zabezpieczeń.  

## <a name="can-i-go-back-to-using-the-former-portal"></a>Czy mogę wrócić do korzystania z poprzedniego portalu?

Jeśli coś nie działa lub nie można wykonać żadnych zadania za pośrednictwem Microsoft 365 Defender, chcemy się o tym dowiedzieć. W przypadku napotkania jakichkolwiek problemów z przekierowywaniem zachęcamy do nas do sowania nas o tym, korzystając z formularza przesyłania opinii.

Aby przywrócić wcześniejszą usługę Microsoft Defender for Endpoint portal:

1. Zaloguj się, <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a> administrator globalny lub używając konta i z uprawnieniami administratora zabezpieczeń w usłudze Azure Active Directory.

2. Przejdź do **Ustawienia** >  **EndpointsGeneralPortal** >  >  **lub** [otwórz tutaj stronę](https://security.microsoft.com/preferences2/portal_redirection).  

3. Przełącz ustawienie Automatyczne przekierowywanie na **Wyłączone**.

4. Po **wyświetleniu** monitu & wyłącz lub udostępnij opinię.

To ustawienie można włączyć ponownie w dowolnym momencie. 

Po wyłączeniu konta nie będą już kierowane do security.microsoft.com i ponownie będziesz mieć dostęp do poprzedniego portalu — do securitycenter.windows.com lub securitycenter.microsoft.com. 

## <a name="related-information"></a>Informacje pokrewne
- [Microsoft 365 Defender omówienie](microsoft-365-defender.md)
- [Program Microsoft Defender dla punktu końcowego w programie Microsoft 365 Defender](microsoft-365-security-center-mde.md)
- [Firma Microsoft zapewnia ujednolicone zabezpieczenia SIEM i XDR w celu unowocześnienia operacji zabezpieczeń](https://www.microsoft.com/security/blog/?p=91813) 
- [XDR a SIEM infografika](https://afrait.com/blog/xdr-versus-siem/) 
- [`The New Defender`](https://afrait.com/blog/the-new-defender/) 
- [Informacje Microsoft 365 Defender](https://www.microsoft.com/microsoft-365/security/microsoft-365-defender) 
- [Portale zabezpieczeń firmy Microsoft i centra administracyjne](portals.md)
