---
title: Dodawanie obsługi anonimowych przychodzących wiadomości e-mail za pośrednictwem protokołu IPv6
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
description: Administrator może dowiedzieć się, jak skonfigurować obsługę anonimowych wiadomości przychodzących ze źródeł IPv6 w sieciach Exchange Online i Exchange Online Protection.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 78b2e653aa284e34af2315ac696d7390dce71884
ms.sourcegitcommit: 0ee2dabe402d44fecb6856af98a2ef7720d25189
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/09/2021
ms.locfileid: "63008741"
---
# <a name="add-support-for-anonymous-inbound-email-over-ipv6-in-microsoft-365"></a>Dodawanie obsługi anonimowych przychodzących wiadomości e-mail przez protokół IPv6 w sieci Microsoft 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender dla Office 365 plan 1 i plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Microsoft 365 organizacje z Exchange Online i autonomicznymi organizacjami usługi poczty Exchange Online Protection (EOP) bez Exchange Online obsługują anonimową pocztę e-mail za pośrednictwem protokołu IPv6. Źródłowy serwer poczty e-mail IPv6 musi spełniać oba następujące wymagania:

- Źródłowy adres IPv6 musi mieć prawidłowy rekord odwrotnego wyszukiwania DNS (PTR), który umożliwia lokalizacji docelowej znalezienie nazwy domeny z adresu IPv6.

- Nadawca musi przejść weryfikację SPF (zdefiniowaną w dokumencie [RFC 7208](https://tools.ietf.org/html/rfc7208)) lub weryfikację [DKIM](http://dkim.org/) (zdefiniowaną w dokumencie [RFC 6376](https://www.rfc-editor.org/rfc/rfc6376.txt)).

Zanim Twoja organizacja będzie miała możliwość odbierania anonimowych przychodzących wiadomości e-mail za pośrednictwem protokołu IPv6, administrator musi skontaktować się z pomocą techniczną firmy Microsoft i poprosić o nią. Aby uzyskać instrukcje dotyczące otwierania wniosku o pomoc techniczną, zobacz Kontakt z pomocą techniczną [dla produktów biznesowych — Pomoc dla administratorów](../../admin/get-help-support.md).

Po włączeniu obsługi anonimowych wiadomości IPv6 przychodzących w organizacji wiadomość zostanie przełączona przez normalne filtrowanie wiadomości udostępniane przez usługę.

## <a name="troubleshooting"></a>Rozwiązywanie problemów

- Jeśli źródłowy serwer poczty e-mail nie ma rekordu wyszukiwania zwrotnego DNS protokołu IPv6, komunikaty zostaną odrzucone z następującym błędem:

  > 450 4.7.25 Usługa niedostępna, wysyłanie adresu IPv6 [2a01:111:f200:2004::240] musi mieć odwrotny rekord DNS.

- Jeśli nadawca nie przejdzie weryfikacji SPF lub DKIM, wiadomości zostaną odrzucone z następującym błędem:

  > 450 4.7.26 Usługa niedostępna, wiadomość wysłana przez protokół IPv6 [2a01:111:f200:2004::240] musi przejść sprawdzanie poprawności SPF lub DKIM.

- Jeśli spróbujesz odbierać anonimowe wiadomości IPv6 przed ich podjęciem, wiadomość zostanie odrzucona z następującym błędem:

  > 550 5.2.1 Usługa niedostępna, [contoso.com] nie akceptuje wiadomości e-mail przez protokół IPv6.

## <a name="related-topics"></a>Tematy pokrewne

[Obsługa sprawdzania poprawności wiadomości podpisanych przez DKIM](support-for-validation-of-dkim-signed-messages.md)
