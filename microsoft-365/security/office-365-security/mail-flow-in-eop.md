---
title: Przepływ poczty e-mail w usłudze EOP
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
description: Administrator może dowiedzieć się więcej o opcjach konfigurowania przepływu poczty i routingu w Exchange Online Protection (EOP).
ms.technology: mdo
ms.prod: m365-security
ms.collection: M365-security-compliance
ms.openlocfilehash: e0267af0297dce41657c76e97964e5c02fbe5815
ms.sourcegitcommit: 725a92b0b1555572b306b285a0e7a7614d34e5e5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2022
ms.locfileid: "65648750"
---
# <a name="mail-flow-in-eop"></a>Przepływ poczty e-mail w usłudze EOP

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Usługi Microsoft Defender dla usługi Office 365 (plan 1 i plan 2)](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

W Microsoft 365 organizacji z Exchange Online skrzynkami pocztowymi lub autonomicznymi organizacjami Exchange Online Protection (EOP) bez Exchange Online skrzynek pocztowych wszystkie wiadomości wysyłane do organizacji przechodzą przez funkcję EOP, zanim użytkownicy je zobaczą. Dostępne są opcje dotyczące sposobu kierowania komunikatów przechodzących przez operację EOP do przetwarzania, zanim zostaną one przekierowane do skrzynek pocztowych użytkowników.

## <a name="working-with-messages-and-message-access-options"></a>Praca z komunikatami i opcjami dostępu do komunikatów

EOP oferuje elastyczność w sposobie kierowania komunikatów. W poniższych tematach opisano kroki procesu przepływu poczty.

[Używanie blokowania krawędzi opartej na katalogu w celu odrzucenia komunikatów wysyłanych do nieprawidłowych adresatów](/exchange/mail-flow-best-practices/use-directory-based-edge-blocking) Opisuje funkcję blokowania krawędzi opartej na katalogach, która umożliwia odrzucanie komunikatów dla nieprawidłowych adresatów na obwodzie sieci usługi.

[Wyświetlanie lub edytowanie zaakceptowanych domen w ramach EOP](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains) opisuje sposób zarządzania domenami skojarzonymi z usługą EOP.

Jeśli dodasz poddomeny do organizacji, usługa EOP może również pomóc w zarządzaniu nimi. Dowiedz się więcej o domenach podrzędnych w temacie [Włączanie przepływu poczty dla poddomen w Exchange Online](/exchange/mail-flow-best-practices/manage-accepted-domains/enable-mail-flow-for-subdomains).

[Konfigurowanie przepływu poczty przy użyciu łączników](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/use-connectors-to-configure-mail-flow) wprowadza łączniki i pokazuje, jak można ich używać do dostosowywania routingu poczty. Scenariusze obejmują zapewnienie bezpiecznej komunikacji z organizacją partnerską i skonfigurowanie inteligentnego hosta.

[Rozszerzone filtrowanie łączników](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/enhanced-filtering-for-connectors) opisuje sposób konfigurowania łączników, jeśli poczta jest kierowana do usługi lub urządzenia przed rozpoczęciem e-wyjścia.

W środowiskach hybrydowych, w których funkcja EOP chroni lokalne Exchange skrzynki pocztowe, należy skonfigurować reguły przepływu poczty (nazywane również regułami transportu) w lokalnych Exchange. Te reguły przepływu poczty tłumaczą werdykt filtrowania spamu EOP, aby reguła wiadomości-śmieci w skrzynce pocztowej mogła przenieść wiadomość do folderu Wiadomości-śmieci. Aby uzyskać szczegółowe informacje, zobacz [Configure EOP to deliver spam to the Junk Email folder in hybrid environments (Konfigurowanie EOP w celu dostarczania spamu do folderu Wiadomości-śmieci w środowiskach hybrydowych](/exchange/standalone-eop/configure-eop-spam-protection-hybrid)). Jeśli nie chcesz przenosić wiadomości do folderu wiadomości-śmieci każdego użytkownika, możesz wybrać inną akcję, edytując zasady ochrony przed spamem (znane również jako zasady filtrowania zawartości). Aby uzyskać więcej informacji, zobacz [Konfigurowanie zasad ochrony przed spamem](configure-your-spam-filter-policies.md).

## <a name="verify-mail-flow"></a>Weryfikowanie przepływu poczty

Aby sprawdzić, czy konfiguracja EOP, w tym konfiguracja łącznika, działa prawidłowo, zobacz "Jak wiesz, że to zadanie zadziałało?" w sekcji [Konfigurowanie usługi EOP](/exchange/standalone-eop/set-up-your-eop-service).

[Testowanie przepływu poczty przez zweryfikowanie łączników Microsoft 365](/exchange/mail-flow-best-practices/test-mail-flow) zawiera instrukcje dotyczące testowania poprawnej konfiguracji przepływu poczty.
