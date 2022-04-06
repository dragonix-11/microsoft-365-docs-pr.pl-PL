---
title: Poziom ufności spamu
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: conceptual
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: 34681000-0022-4b92-b38a-e32b3ed96bf6
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Administratorzy mogą dowiedzieć się więcej na temat poziomu ufności filtru spamu stosowanego do wiadomości w Exchange Online Protection (EOP).
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 7783eb0655a6e3b0457a45057b920c87388e4c05
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2022
ms.locfileid: "63682928"
---
# <a name="spam-confidence-level-scl-in-eop"></a>Poziom ufności filtru spamu (SCL) w uchcie EOP

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender dla Office 365 plan 1 i plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

W organizacjach Microsoft 365 ze skrzynkami pocztowymi w organizacjach Exchange Online lub autonomicznych organizacjach usługi Exchange Online Protection (EOP) bez skrzynek pocztowych usługi Exchange Online wiadomości przychodzące są filtrowane spamem w u ramach usługi EOP i mają przypisany wynik spamu. Ten wynik jest mapowany na indywidualny poziom ufności spamu dodawany do wiadomości w nagłówku X. Wyższa wartość SCL wskazuje, że wiadomość jest bardziej prawdopodobna jako spam. Usługa EOP podejmuje działanie na podstawie listy SCL.

Co oznacza wartość SCL i domyślne akcje podejmowane na wiadomościach, opisano w poniższej tabeli. Aby uzyskać więcej informacji na temat akcji, jakie można podjąć na podstawie werdyktu filtrowania spamu, zobacz Konfigurowanie zasad ochrony przed [spamem w uciekaniu poczty eOP](configure-your-spam-filter-policies.md).

|SCL|Definicja|Akcja domyślna|
|:---:|---|---|
|-1|Wiadomość pominięta w filtrowaniu spamu. Na przykład wiadomość pochodzi od bezpiecznego nadawcy, została wysłana do bezpiecznego adresata lub pochodzi z serwera źródła poczty e-mail na liście zezwalań adresów IP. Aby uzyskać więcej informacji, zobacz [Tworzenie bezpiecznych list nadawców w uciekacej u eop](create-safe-sender-lists-in-office-365.md).|Dostarczanie wiadomości do skrzynki odbiorczej adresatów.|
|0, 1|Filtrowanie spamu określone, że wiadomość nie jest spamem.|Dostarczanie wiadomości do skrzynki odbiorczej adresatów.|
|5, 6|Filtrowanie spamu oznaczało wiadomość jako **spam**|Dostarczanie wiadomości do folderu wiadomości-śmieci adresatów.|
|9|Filtrowanie spamu oznaczało wiadomość jako **spam o dużej pewności**|Dostarczanie wiadomości do folderu wiadomości-śmieci adresatów.|

Przy filtrowaniu spamu nie jest używany filtr filtr spamu.

Możesz użyć reguł przepływu poczty (nazywanych również regułami transportu) do sygnatury SCL wiadomości. Jeśli za pomocą reguły przepływu poczty ustawisz wartość SCL, wartości 5 lub 6 wyzwoliją akcję filtrowania spamu dla spamu **, a** wartości 7, 8 lub 9 będą wyzwalać akcję filtrowania spamu dla spamu o dużej **pewności.** Aby uzyskać więcej informacji, zobacz Ustawianie poziomu ufności filtru spamu (SCL) w wiadomościach za pomocą [reguł przepływu poczty](/exchange/security-and-compliance/mail-flow-rules/use-rules-to-set-scl).

Podobnie jak w przypadku listy wiadomości zbiorczych, poziom skarg zbiorczych określa źle masową pocztę e-mail (znaną _także jako szara poczta_). Wyższa wartość BCL wskazuje, że wiadomości masowej wysyłki z większą prawdopodobieństwem generują skargi (przez co są tym bardziej prawdopodobne, że są spamem). Próg BCL konfiguruje się w zasadach ochrony przed spamem. Aby uzyskać więcej informacji, zobacz Konfigurowanie zasad ochrony przed spamem w uścisce [usługi EOP](configure-your-spam-filter-policies.md), Poziom skarg zbiorczych [w](bulk-complaint-level-values.md) UŁAP oraz Jaka jest różnica między wiadomościami-śmieciami a masową pocztą [e-mail?](what-s-the-difference-between-junk-email-and-bulk-email.md).

****

![Ikona skrótu do usługi LinkedIn Learning.](../../media/eac8a413-9498-4220-8544-1e37d1aaea13.png) **Nie chcesz Microsoft 365?** Zapoznaj się z bezpłatnymi **kursami wideo Microsoft 365 administratorami i informatykami**, które są dostępne w serwisie LinkedIn Edukacja.
