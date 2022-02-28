---
title: Konfigurowanie szyfrowania w Office 365 Enterprise
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 4/2/2018
audience: Admin
ms.topic: hub-page
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: e86fc991-0161-4f01-9c1c-d25e87733d06
description: W Office 365 niektóre funkcje szyfrowania są domyślnie włączone. Inne funkcje można skonfigurować tak, aby spełniały określone wymagania prawne lub dotyczące zgodności z przepisami.
ms.openlocfilehash: 00035af0049abedff8a794710649f162576dc46c
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62983165"
---
# <a name="set-up-encryption-in-office-365-enterprise"></a>Konfigurowanie szyfrowania w Office 365 Enterprise

Szyfrowanie może chronić zawartość przed odczytaniem przez nieautoryzowanych użytkowników. Ponieważ [szyfrowanie w Office 365](encryption.md) być wykonywane przy użyciu różnych technologii i metod, nie ma jednego miejsca, w którym możesz włączyć lub skonfigurować szyfrowanie. Ten artykuł zawiera informacje o różnych sposobach konfigurowania lub konfigurowania szyfrowania w ramach strategii ochrony informacji.

> [!TIP]
> Jeśli szukasz szczegółowych informacji technicznych na temat szyfrowania, zobacz Informacje techniczne [dotyczące szyfrowania](technical-reference-details-about-encryption.md) w Office 365.

W Office 365 szyfrowanie jest domyślnie dostępnych kilka funkcji szyfrowania. Dodatkowe funkcje szyfrowania można skonfigurować tak, aby spełniały określone wymagania prawne lub dotyczące zgodności z przepisami. W poniższej tabeli opisano kilka metod szyfrowania dla różnych scenariuszy.

<br>

****

|Scenariusz|Metody szyfrowania|
|---|---|
|Pliki są zapisywane na Windows komputerach|Szyfrowanie na poziomie komputera można wykonać przy użyciu funkcji BitLocker na Windows urządzeniach. Jako administrator przedsiębiorstwa lub Pro, możesz skonfigurować to przy użyciu zestawu narzędzi wdrażania firmy Microsoft (MDT). Zobacz [Konfigurowanie funkcji MDT dla funkcji BitLocker](/windows/deployment/deploy-windows-mdt/set-up-mdt-for-bitlocker).|
|Pliki są zapisywane na urządzeniach przenośnych|Niektóre rodzaje urządzeń przenośnych szyfrują pliki, które są domyślnie zapisywane na tych urządzeniach. Dzięki [możliwościom wbudowanych funkcji Zarządzanie urządzeniami przenośnymi dla Office 365](https://support.microsoft.com/office/capabilities-of-built-in-mobile-device-management-for-microsoft-365-a1da44e5-7475-4992-be91-9ccec25905b0) możesz ustawić zasady, które określają, czy urządzenia przenośne mają zezwalać na dostęp do danych w aplikacji Office 365. Na przykład możesz ustawić zasady zezwalaujące tylko na urządzenia szyfrujące zawartość w celu uzyskiwania dostępu Office 365 danych. Zobacz [Tworzenie i wdrażanie zasad zabezpieczeń urządzeń](https://support.microsoft.com/office/create-and-deploy-device-security-policies-d310f556-8bfb-497b-9bd7-fe3c36ea2fd6). <p> Aby mieć dodatkową kontrolę nad interakcjami urządzeń przenośnych z usługą Office 365, możesz rozważyć dodanie [Microsoft Intune.](/mem/intune/fundamentals/setup-steps)|
|Potrzebujesz kontroli nad kluczami szyfrowania używanymi do szyfrowania danych w centrach danych firmy Microsoft|Jako administrator Office 365, możesz sterować kluczami szyfrowania Twojej organizacji, a następnie skonfigurować Office 365 ich używać do szyfrowania danych w spoczynku w centrach danych firmy Microsoft. <p> [Szyfrowanie usługi przy użyciu klucza klienta w Office 365](customer-key-overview.md)|
|Osoby komunikują się za pośrednictwem poczty e-mail (Exchange Online)|Jako administrator Exchange Online masz kilka opcji konfigurowania szyfrowania poczty e-mail. Obejmują one: <ul><li>Korzystanie [Office 365 szyfrowania wiadomości (OME)](set-up-new-message-encryption-capabilities.md) z usługą Azure Rights Management (Azure Rights Management) w celu umożliwienia użytkownikom wysyłania zaszyfrowanych wiadomości w organizacji lub poza nią</li><li>Szyfrowanie [i cyfrowe podpisywanie wiadomości e-mail za pomocą funkcji S/MIME](/exchange/security-and-compliance/smime-exo/smime-exo)</li><li>Konfigurowanie łączników w celu zapewnienia bezpiecznego przepływu poczty [e-mail z inną organizacją za pomocą usługi](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/set-up-connectors-for-secure-mail-flow-with-a-partner) TLS</li></ul> <p> Zobacz [Szyfrowanie wiadomości e-mail w Office 365](./email-encryption.md).|
|Dostęp do plików można uzyskiwać z witryn zespołu lub bibliotek dokumentów (OneDrive dla Firm lub SharePoint online)|Gdy inne osoby pracują z plikami zapisanymi OneDrive dla Firm lub SharePoint Online, używane są połączenia TLS. Jest on wbudowany Office 365 automatycznie. Zobacz [Szyfrowanie danych w OneDrive dla Firm i SharePoint Online](./data-encryption-in-odb-and-spo.md).|
|Pliki są udostępniane w spotkaniach online i konwersacjach za pomocą wiadomości błyskawicznych (Skype dla firm online)|Gdy osoby pracują z plikami przy Skype dla firm Online, do połączenia jest używany TLS. Jest on wbudowany Office 365 automatycznie. Zobacz [Zabezpieczenia i archiwizacja (Skype dla firm w trybie online).](/office365/servicedescriptions/skype-for-business-online-service-description/skype-for-business-online-features)|
|Pliki są udostępniane w spotkaniach online i konwersacjach za pomocą wiadomości błyskawicznych (Microsoft Teams)|Gdy osoby pracują z plikami za pomocą Microsoft Teams, do połączenia jest używany adres TLS. Jest on wbudowany Office 365 automatycznie. Microsoft Teams obecnie nie obsługuje renderowania w tekście zaszyfrowanych wiadomości e-mail. Aby zapobiec dotrzeniu zaszyfrowanych Microsoft Teams e-mail jako zaszyfrowanych, zobacz Często [zadawane pytania dotyczące szyfrowania wiadomości](./ome-faq.yml#can-i-automatically-remove-encryption-on-incoming-and-outgoing-mail-).|
|

## <a name="additional-information"></a>Informacje dodatkowe

Aby dowiedzieć się więcej o rozwiązaniach ochrony plików, które zawierają opcje szyfrowania, zobacz [Rozwiązania ochrony plików w programie Office 365](https://www.microsoft.com/download/details.aspx?id=55523).
