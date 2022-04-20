---
title: Wysyłanie zaszyfrowanej wiadomości e-mail
f1.keywords:
- NOCSH
ms.author: sharik
author: skjerland
manager: scotv
ms.date: 9/20/2018
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Adm_O365
- M365-subscription-management
- M365-Campaigns
- m365solution-smb
ms.custom:
- Adm_O365
- Core_O365Admin_Migration
- MiniMaven
- MSB365
- admindeeplinkEXCHANGE
search.appverid:
- BCS160
- MET150
ms.assetid: 496e690b-b75d-4ff5-bf34-cc32905d0364
description: Dowiedz się, jak wysyłać zaszyfrowane wiadomości e-mail przy użyciu Outlook.
ms.openlocfilehash: 9cf39d3147b5ef7a099a06737316ee20e6154775
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2022
ms.locfileid: "64946907"
---
# <a name="encrypt-or-label-your-sensitive-email"></a>Szyfrowanie lub etykietowanie poufnej wiadomości e-mail

Dane i informacje o kampanii są ważne i często poufne. Pomóż chronić te poufne informacje przy użyciu etykiet szyfrowania i poufności, aby ty i adresaci wiadomości e-mail traktowali informacje z wymaganiem poufności.

## <a name="best-practices"></a>Najważniejsze wskazówki

Przed wysłaniem wiadomości e-mail z informacjami poufnymi lub poufnymi rozważ włączenie:

- **Szyfrowania:** Możesz zaszyfrować wiadomość e-mail, aby chronić prywatność informacji w wiadomości e-mail. Podczas szyfrowania wiadomości e-mail jest ona konwertowana z czytelnego zwykłego tekstu na kodowany tekst cypher. Tylko adresat, który ma klucz prywatny zgodny z kluczem publicznym używanym do szyfrowania wiadomości, może rozszyfrować komunikat do odczytu. Każdy adresat bez odpowiedniego klucza prywatnego widzi jednak nieczytelny tekst. Administrator może zdefiniować reguły do automatycznego szyfrowania komunikatów spełniających określone kryteria. Na przykład administrator może utworzyć regułę, która szyfruje wszystkie komunikaty wysyłane poza organizację lub wszystkie komunikaty, które wymieniają określone słowa lub frazy. Wszystkie reguły szyfrowania zostaną zastosowane automatycznie.
- **Etykiety poufności:** Twoja kampania może również skonfigurować etykiety poufności, które można zastosować do plików i wiadomości e-mail, aby zachować ich zgodność z zasadami ochrony informacji kampanii. Po ustawieniu etykiety etykieta będzie się powtarzać przy użyciu wiadomości e-mail, nawet gdy zostanie wysłana — na przykład przez wyświetlenie jej jako nagłówka.

![Diagram wiadomości e-mail z objaśnieniami etykiet i szyfrowania.](../media/m365-campaign-email-encrypt.png)

## <a name="set-it-up"></a>Konfigurowanie

Jeśli chcesz zaszyfrować komunikat, który nie spełnia wstępnie zdefiniowanej reguły lub administrator nie skonfigurował żadnych reguł, możesz zastosować różne reguły szyfrowania przed wysłaniem komunikatu. Aby wysłać zaszyfrowaną wiadomość z Outlook 2013 lub 2016 r. lub Outlook 2016 dla komputerów Mac, wybierz pozycję **Opcje > Uprawnienia**, a następnie wybierz odpowiednią opcję ochrony. Możesz również wysłać zaszyfrowaną wiadomość, wybierając przycisk **Chroń** w Outlook w sieci Web. Aby uzyskać więcej informacji, zobacz [Wysyłanie, wyświetlanie i odpowiadanie na zaszyfrowane wiadomości w Outlook dla komputera](https://support.microsoft.com/en-us/office/send-view-and-reply-to-encrypted-messages-in-outlook-for-pc-eaa43495-9bbb-4fca-922a-df90dee51980).

## <a name="admin-settings"></a>Ustawienia administratora

Wszystkie informacje na temat konfigurowania szyfrowania poczty e-mail można znaleźć w [temacie Szyfrowanie poczty e-mail w Microsoft 365](../compliance/email-encryption.md).

### <a name="automatically-encrypt-email-messages"></a>Automatyczne szyfrowanie wiadomości e-mail

Administratorzy mogą tworzyć reguły przepływu poczty, aby automatycznie chronić wiadomości e-mail wysyłane i odbierane z kampanii. Skonfiguruj reguły szyfrowania wszelkich wychodzących wiadomości e-mail i usuwania szyfrowania z zaszyfrowanych wiadomości pochodzących z organizacji lub odpowiedzi na zaszyfrowane wiadomości wysyłane z organizacji.

Tworzysz reguły przepływu poczty w celu szyfrowania wiadomości e-mail za pomocą usługi Microsoft Purview Message Encryption. Zdefiniuj reguły przepływu poczty na potrzeby wyzwalania szyfrowania wiadomości przy użyciu <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">centrum administracyjnego Exchange (EAC).</a>

1. W przeglądarce internetowej zaloguj się przy użyciu konta służbowego, któremu udzielono uprawnień administratora globalnego.
2. Wybierz kafelek Administrator.
3. W centrum administracyjnym wybierz pozycję **Centra administracyjne > Exchange**.

Aby uzyskać więcej informacji, zobacz [Definiowanie reguł przepływu poczty w celu szyfrowania wiadomości e-mail](../compliance/define-mail-flow-rules-to-encrypt-email.md).

### <a name="brand-your-encryption-messages"></a>Oznaczanie wiadomości szyfrowania

Możesz również zastosować znakowanie kampanii, aby dostosować wygląd i tekst w wiadomościach e-mail. Aby uzyskać więcej informacji, zobacz [Dodawanie marki organizacji do zaszyfrowanych komunikatów](../compliance/email-encryption.md).