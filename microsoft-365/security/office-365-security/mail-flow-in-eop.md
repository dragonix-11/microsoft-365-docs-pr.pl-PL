---
title: Przepływ poczty e-mail w u usługi EOP
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: overview
ms.localizationpriority: medium
ms.assetid: e109077e-cc85-4c19-ae40-d218ac7d0548
ms.custom:
- seo-marvel-apr2020
description: Administrator może dowiedzieć się więcej na temat opcji konfigurowania przepływu poczty e-mail i routingu w u Exchange Online Protection (EOP).
ms.technology: mdo
ms.prod: m365-security
ms.collection: M365-security-compliance
ms.openlocfilehash: 296cd8aaa92005f094de2ee7d1c9f8bb9427df16
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2022
ms.locfileid: "63681023"
---
# <a name="mail-flow-in-eop"></a>Przepływ poczty e-mail w u usługi EOP

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender dla Office 365 plan 1 i plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

W Microsoft 365 z firmami Exchange Online lub autonomicznymi organizacjami usługi Exchange Online Protection (EOP) bez skrzynek pocztowych usługi Exchange Online wszystkie wiadomości wysłane do organizacji przechodzą przez usługę EOP, zanim ich pracownicy zobaczą. Dostępne są opcje rozsyłania wiadomości, które przechodzą przez program EOP, w celu przetworzenia ich do skrzynek pocztowych pracowników.

## <a name="working-with-messages-and-message-access-options"></a>Praca z wiadomościami i opcjami dostępu do wiadomości

Program EOP zapewnia elastyczność w zakresie sposobu rozsyłania wiadomości. W poniższych tematach wyjaśniono etapy procesu przepływu poczty e-mail.

[Odrzucanie wiadomości wysyłanych](/exchange/mail-flow-best-practices/use-directory-based-edge-blocking) do nieprawidłowych adresatów za pomocą blokowania na podstawie katalogu W tym artykule opisano funkcję blokowania opartych na katalogu (Edge Blocking), która pozwala odrzucać wiadomości od nieprawidłowych adresatów w obwodzie sieci usługi.

[W artykule Wyświetlanie i edytowanie zaakceptowanych domen w usłudze EOP](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains) opisano sposób zarządzania domenami skojarzonymi z usługą EOP.

Jeśli dodasz poddomeny do organizacji, Twoja usługa EOP także pomoże Ci nimi zarządzać. Dowiedz się więcej o poddomenach, zobacz Włączanie przepływu poczty [dla poddomen w Exchange Online](/exchange/mail-flow-best-practices/manage-accepted-domains/enable-mail-flow-for-subdomains).

[Konfigurowanie przepływu poczty e-mail](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/use-connectors-to-configure-mail-flow) za pomocą łączników wprowadza łączniki i pokazuje, jak można ich używać do dostosowywania routingu poczty. Scenariusze obejmują zapewnienie bezpiecznej komunikacji z organizacją partnerską i skonfigurowanie hosta inteligentnego.

[Ulepszone filtrowanie łączników opisuje](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/enhanced-filtering-for-connectors) sposób konfigurowania łączników, jeśli poczta jest rozsyłana do usługi lub urządzenia przed usługą EOP.

W środowiskach hybrydowych, w których program EOP chroni lokalne Exchange pocztowe, musisz skonfigurować reguły przepływu poczty e-mail (nazywane także regułami transportu) w lokalnym programie Exchange. Te reguły przepływu poczty tłumaczą werdykt filtrowania spamu usługi EOP, dzięki czemu reguła wiadomości-śmieci w skrzynce pocztowej może przenieść wiadomość do folderu Wiadomości-śmieci. Aby uzyskać szczegółowe informacje, zobacz [Konfigurowanie usługi EOP w celu dostarczania spamu do folderu Wiadomości-śmieci w środowiskach hybrydowych](/exchange/standalone-eop/configure-eop-spam-protection-hybrid). Jeśli nie chcesz przenosić wiadomości do folderu wiadomości-śmieci poszczególnych użytkowników, możesz wybrać inną akcję, edytując zasady ochrony przed spamem (nazywane również zasadami filtrowania zawartości). Aby uzyskać więcej informacji, [zobacz Konfigurowanie zasad ochrony przed spamem](configure-your-spam-filter-policies.md).

## <a name="verify-mail-flow"></a>Weryfikowanie przepływu poczty e-mail

Aby sprawdzić, czy konfiguracja usługi EOP, łącznie z konfiguracją łącznika, działa poprawnie, zobacz "Skąd wiadomo, że to zadanie zadziałało?". w sekcji [Konfigurowanie usługi EOP](/exchange/standalone-eop/set-up-your-eop-service).

[Testowanie przepływu poczty e-mail przez Microsoft 365 łączników](/exchange/mail-flow-best-practices/test-mail-flow) zawiera instrukcje testowania poprawności przepływu poczty.
