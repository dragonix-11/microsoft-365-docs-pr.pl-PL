---
title: Dodawanie obsługi anonimowych, przychodzących wiadomości e-mail za pośrednictwem protokołu IPv6
f1.keywords:
- NOCSH
author: chrisda
ms.author: chrisda
manager: chrisda
audience: ITPro
ms.topic: how-to
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: b68df621-0a5f-4824-8abc-41e0c4fd1398
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Administracja mogą dowiedzieć się, jak skonfigurować obsługę anonimowej przychodzącej poczty e-mail ze źródeł IPv6 w Exchange Online i Exchange Online Protection.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 093ab458e8894105536e1c3dd46d2c911de440fd
ms.sourcegitcommit: 725a92b0b1555572b306b285a0e7a7614d34e5e5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2022
ms.locfileid: "65649104"
---
# <a name="add-support-for-anonymous-inbound-email-over-ipv6-in-microsoft-365"></a>Dodawanie obsługi anonimowej przychodzącej poczty e-mail za pośrednictwem protokołu IPv6 w Microsoft 365

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Usługi Microsoft Defender dla usługi Office 365 (plan 1 i plan 2)](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Microsoft 365 organizacje z Exchange Online skrzynkami pocztowymi i autonomicznymi organizacjami Exchange Online Protection (EOP) bez Exchange Online skrzynek pocztowych obsługują anonimowe przychodzące wiadomości e-mail za pośrednictwem protokołu IPv6. Źródłowy serwer poczty e-mail IPv6 musi spełniać oba następujące wymagania:

- Źródłowy adres IPv6 musi mieć prawidłowy odwrotny rekord wyszukiwania DNS (PTR), który umożliwia lokalizacji docelowej znalezienie nazwy domeny z adresu IPv6.

- Nadawca musi przejść weryfikację SPF (zdefiniowaną w [dokumencie RFC 7208](https://tools.ietf.org/html/rfc7208)) lub [weryfikację DKIM](http://dkim.org/) (zdefiniowaną w [dokumencie RFC 6376](https://www.rfc-editor.org/rfc/rfc6376.txt)).

Aby twoja organizacja mogła otrzymywać anonimowe przychodzące wiadomości e-mail za pośrednictwem protokołu IPv6, administrator musi skontaktować się z pomocą techniczną firmy Microsoft i poprosić o to. Aby uzyskać instrukcje dotyczące sposobu otwierania wniosku o pomoc techniczną, zobacz [Kontakt z pomocą techniczną dla produktów biznesowych — Administracja Pomoc](../../admin/get-help-support.md).

Po włączeniu anonimowej obsługi komunikatów IPv6 dla ruchu przychodzącego w organizacji komunikat przejdzie przez normalne filtrowanie komunikatów udostępniane przez usługę.

## <a name="troubleshooting"></a>Rozwiązywanie problemów

- Jeśli źródłowy serwer poczty e-mail nie ma odwrotnego rekordu wyszukiwania DNS IPv6, komunikaty zostaną odrzucone z następującym błędem:

  > Usługa 450 4.7.25 jest niedostępna, wysyłanie adresu IPv6 [2a01:111:f200:2004::240] musi mieć odwrotny rekord DNS.

- Jeśli nadawca nie przejdzie weryfikacji SPF lub DKIM, komunikaty zostaną odrzucone z następującym błędem:

  > 450 4.7.26 Usługa niedostępna, komunikat wysłany za pośrednictwem protokołu IPv6 [2a01:111:f200:2004::240] musi przejść weryfikację SPF lub DKIM.

- Jeśli spróbujesz otrzymywać anonimowe komunikaty IPv6 przed zalogowaniem się, komunikat zostanie odrzucony z następującym błędem:

  > Usługa 550 5.2.1 jest niedostępna, [contoso.com] nie akceptuje wiadomości e-mail za pośrednictwem protokołu IPv6.

## <a name="related-topics"></a>Tematy pokrewne

[Obsługa weryfikacji podpisanych komunikatów DKIM](support-for-validation-of-dkim-signed-messages.md)
