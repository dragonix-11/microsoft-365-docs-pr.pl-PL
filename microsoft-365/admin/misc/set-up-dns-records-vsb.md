---
title: Połączenie domenę do Microsoft 365
f1.keywords:
- CSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: high
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_O365_Setup
search.appverid:
- MET150
ROBOTS: NOINDEX, NOFOLLOW
description: Dowiedz się, jak zweryfikować domenę i tworzyć rekordy DNS za pomocą Microsoft 365.
ms.custom:
- AdminSurgePortfolio
ms.openlocfilehash: 3aa43cd798c26dde8eb064754ae3fb74bd520c29
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63312505"
---
# <a name="connect-your-domain-to-microsoft-365"></a>Połączenie domenę do Microsoft 365

> [!NOTE]
> Jeśli nie dodasz domeny, osoby w Twojej organizacji będą używać domeny adresowej onmicrosoft.com swoich adresów e-mail, dopóki nie to zrobisz. Ważne jest dodanie domeny przed dodaniem użytkowników, aby nie trzeba było ich dwukrotnie  skonfigurować.

[Zajrzyj do często zadawanych](../setup/domains-faq.yml) pytań domeny, jeśli nie możesz znaleźć szukanych informacji poniżej.

## <a name="add-an-mx-record-so-email-for-your-domain-will-come-to-microsoft"></a>Dodawanie rekordu MX, aby poczta e-mail dla Twojej domeny trafiała do firmy Microsoft

Informacje dotyczące rekordu MX można uzyskać z kreatora konfiguracji domeny w centrum administracyjnym.

W witrynie internetowej dostawcy hostingu dodaj nowy rekord MX.
Upewnij się, że w polach są ustawione następujące wartości:

- Typ rekordu: `MX`
- Priority (Priorytet): ustawiana na najwyższą dostępną wartość, zazwyczaj `0`.
- Nazwa hosta: `@`
- Points to address (Wskazuje adres): skopiuj wartość z centrum administracyjnego i wklej ją w tym miejscu.
- TTL `3600` (Czas wygaśnięcia): (lub domyślny dostawca)

Zapisz rekord, a następnie usuń wszelkie inne rekordy MX.

## <a name="add-a-cname-record-to-connect-users-to-their-mailboxes"></a>Dodawanie rekordu CNAME w celu połączenia użytkowników ze skrzynkami pocztowymi

Informacje dotyczące rekordów CNAME można uzyskać z kreatora konfiguracji domeny w centrum administracyjnym.

W witrynie internetowej dostawcy hostingu dodaj następujący rekord CNAME. Upewnij się, że w polach są ustawione następujące wartości dla każdego z nich:

- Typ rekordu: `CNAME (Alias)`
- Host: wklej tutaj wartości skopiowane z centrum administracyjnego.
- Points to address (Wskazuje adres): skopiuj wartość z centrum administracyjnego i wklej ją w tym miejscu.
- TTL `3600` (Czas wygaśnięcia): (lub domyślny dostawca)

## <a name="add-a-txt-record-to-help-prevent-spam"></a>Dodawanie rekordu TXT w celu zapobiegania spamowi

**Przed rozpoczęciem:** Jeśli masz już rekord SPF dla swojej domeny, nie twórz nowego rekordu dla Microsoft 365. Zamiast tego dodaj wymagane wartości Microsoft 365 do bieżącego rekordu w witrynie sieci Web dostawców hostingu, aby mieć pojedynczy *rekord SPF,* który zawiera oba zestawy wartości.

W witrynie internetowej dostawcy hostingu edytuj istniejący rekord SPF lub utwórz rekord SPF.
Upewnij się, że w polach są ustawione następujące wartości:

- Typ rekordu: `TXT (Text)`
- Host: `@`
- TXT Value (Wartość TXT): `v=spf1 include:spf.protection.outlook.com -all`
- TTL `3600` (Czas wygaśnięcia): (lub domyślny dostawca)

Zapisz rekord.

Weryfikowanie rekordu SPF przy użyciu jednego z tych [narzędzi do weryfikowania rekordu SPF](/office365/admin/setup/domains-faq#how-can-i-validate-spf-records-for-my-domain)

Spf został zaprojektowany w celu zapobiegania fałszerszem, ale istnieją techniki podszywania się, przed które spf nie chroni. Aby zapewnić ochronę przed tymi ustawieniami, po skonfigurowaniu spf musisz również skonfigurować ustawienia DKIM i DMARC dla Microsoft 365.

Aby rozpocząć, zobacz Używanie funkcji [DKIM](../../security/office-365-security/use-dkim-to-validate-outbound-email.md) w celu weryfikacji wychodzących wiadomości e-mail wysłanych z domeny w programie Microsoft 365 i Używanie funkcji [DMARC](../../security/office-365-security/use-dmarc-to-validate-email.md) do sprawdzania poprawności wiadomości e-mail w Microsoft 365.

Na koniec wróć do kreatora konfiguracji domeny centrum administracyjnego, aby ukończyć konfigurację.
