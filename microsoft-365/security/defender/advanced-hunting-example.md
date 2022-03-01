---
title: Przykład zaawansowanego wyszukiwania dla programu Microsoft Defender dla Office 365
description: Rozpoczynanie wyszukiwania zagrożeń w wiadomościach e-mail przy użyciu zaawansowanego wyszukiwania
keywords: zaawansowane szukanie, szukanie zagrożeń, cyberzagrożenia, Microsoft 365 Defender, microsoft 365, m365, wyszukiwanie, zapytanie, telemetria, wykrywanie niestandardowe, schemat, kusto
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
- m365initiative-m365-defender
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: 04e4fd2267cc3774e9a816539f0de044ae988dfb
ms.sourcegitcommit: 4af23696ff8b44872330202fe5dbfd2a69d9ddbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/30/2021
ms.locfileid: "62996827"
---
# <a name="advanced-hunting-example-for-microsoft-defender-for-office-365"></a>Przykład zaawansowanego wyszukiwania dla programu Microsoft Defender dla Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Dotyczy:**
- Microsoft 365 Defender

Chcesz rozpocząć wyszukiwanie zagrożeń związanych z pocztą e-mail przy użyciu zaawansowanego wyszukiwania? Metoda

Sekcja [Wprowadzenie w](/microsoft-365/security/office-365-security/defender-for-office-365#getting-started) artykule Microsoft [Defender for Office 365 zawiera](/microsoft-365/security/office-365-security/defender-for-office-365) logiczne fragmenty wczesnej konfiguracji, które wyglądają tak:

1. Skonfiguruj wszystko tak, aby w nazwie był w nazwie "Anti".
   - Ochrona przed złośliwym oprogramowaniem
   - Ochrona przed wyłudzaniem informacji
   - Ochrona przed spamem
2. Skonfiguruj wszystko, gdy Sejf "wszystko" w nazwie.
   - Bezpieczne linki
   - Sejf załączników
3. Obrona obciążeń pracą (np. SharePoint Online, OneDrive i Teams).
4. Ochrona za pomocą automatycznego przeczyszczania o zerowej godzinie.

Wraz z [linkiem,](../office-365-security/protect-against-threats.md) który od razu się połączy i przygotuje konfigurację do dnia 1.

Ostatnim krokiem w **wprowadzeniem** jest ochrona użytkowników za pomocą **funkcji** automatycznego przeczyszczania o zerowej godzinie, nazywanej także zap. Bardzo ważna może być wiedza o tym, czy działania podejmowane w celu zapukania podejrzanych lub złośliwych wiadomości po dostarczeniu się powiodło.

Szybkie przechodzenie do języka zapytań Kusto w celu wyszukiwania problemów jest zaletą zbiegania się tych dwóch centrów zabezpieczeń. Zespoły bezpieczeństwa mogą monitorować nieodebrane przez zap zap, biorąc udział w następnych czynnościach [, które](https://security.microsoft.com/advanced-hunting) poszło tutaj, w obszarze **Szukanie** \> **zaawansowane**.

1. Na stronie Wyszukiwanie zaawansowane kliknij pozycję **Zapytanie**.
1. Skopiuj poniższe zapytanie do okna zapytania.
1. Wybierz **pozycję Uruchom zapytanie**.

```kusto
EmailPostDeliveryEvents 
| where Timestamp > ago(7d)
//List malicious emails that were not zapped successfullyconverge-2-endpoints-new.png
| where ActionType has "ZAP" and ActionResult == "Error"
| project ZapTime = Timestamp, ActionType, NetworkMessageId , RecipientEmailAddress 
//Get logon activity of recipients using RecipientEmailAddress and AccountUpn
| join kind=inner IdentityLogonEvents on $left.RecipientEmailAddress == $right.AccountUpn
| where Timestamp between ((ZapTime-24h) .. (ZapTime+24h))
//Show only pertinent info, such as account name, the app or service, protocol, the target device, and type of logon
| project ZapTime, ActionType, NetworkMessageId , RecipientEmailAddress, AccountUpn, 
LogonTime = Timestamp, AccountDisplayName, Application, Protocol, DeviceName, LogonType
```

:::image type="content" source="../../media/ah-query-example-new.png" alt-text="Strona zaawansowanego wyszukiwania (w obszarze Wyszukiwania) z zapytaniem wybranym u góry panelu zapytania i uruchomieniem zapytania Kusto w celu przechwycenia akcji ZAP w ciągu ostatnich 7 dni." lightbox="../../media/ah-query-example-new.png":::

Dane z tego zapytania zostaną wyświetlone w panelu wyników pod samym zapytaniem. Wyniki obejmują informacje, takie jak "DeviceName", "AccountDisplayName" i "ZapTime" w dostosowywalnym zestawie wyników. Wyniki można również eksportować dla rekordów. Jeśli zapytanie jest potrzebne ponownie,  >  wybierz pozycję ZapiszZa zapisuj jako i dodaj zapytanie do listy zapytań, zapytań udostępnionych lub zapytań społecznościowych.

## <a name="related-information"></a>Informacje pokrewne
- [Zaawansowane wskazówki dotyczące wyszukiwania](advanced-hunting-best-practices.md)
- [Omówienie — wyszukiwanie zaawansowane](advanced-hunting-overview.md)
