---
title: Konfigurowanie szyfrowania w Office 365 Enterprise
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 4/2/2018
audience: Admin
ms.topic: landing-page
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: e86fc991-0161-4f01-9c1c-d25e87733d06
description: W przypadku Office 365 niektóre funkcje szyfrowania są domyślnie włączone. Inne możliwości można skonfigurować tak, aby spełniały określone wymagania prawne lub zgodności.
ms.openlocfilehash: 86e39603025c29d47a2e1b2b5b946bfe2549245d
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66622112"
---
# <a name="set-up-encryption-in-office-365-enterprise"></a>Konfigurowanie szyfrowania w Office 365 Enterprise

Szyfrowanie może chronić zawartość przed odczytywaniem przez nieautoryzowanych użytkowników. Ponieważ [szyfrowanie w Office 365](encryption.md) może odbywać się przy użyciu różnych technologii i metod, nie ma jednego miejsca, w którym można włączyć lub skonfigurować szyfrowanie. Ten artykuł zawiera informacje o różnych sposobach konfigurowania lub konfigurowania szyfrowania w ramach strategii ochrony informacji.

> [!TIP]
> Jeśli szukasz dodatkowych szczegółów technicznych dotyczących szyfrowania, zobacz [Szczegóły dokumentacji technicznej dotyczące szyfrowania w Office 365](technical-reference-details-about-encryption.md).

W przypadku Office 365 domyślnie dostępnych jest kilka funkcji szyfrowania. Dodatkowe możliwości szyfrowania można skonfigurować tak, aby spełniały określone wymagania dotyczące zgodności lub prawnych. W poniższej tabeli opisano kilka metod szyfrowania dla różnych scenariuszy.

<br>

****

|Scenariusz|Metody szyfrowania|
|---|---|
|Pliki są zapisywane na komputerach z systemem Windows|Szyfrowanie na poziomie komputera można wykonać przy użyciu BitLocker na urządzeniach z systemem Windows. Jako administrator przedsiębiorstwa lub informatyk można skonfigurować tę konfigurację przy użyciu zestawu narzędzi microsoft deployment toolkit (MDT). Zobacz [Konfigurowanie mdt dla BitLocker](/windows/deployment/deploy-windows-mdt/set-up-mdt-for-bitlocker).|
|Pliki są zapisywane na urządzeniach przenośnych|Niektóre rodzaje urządzeń przenośnych szyfrują pliki, które są domyślnie zapisywane na tych urządzeniach. Dzięki [możliwościom wbudowanych Zarządzanie urządzeniami przenośnymi dla Office 365](https://support.microsoft.com/office/capabilities-of-built-in-mobile-device-management-for-microsoft-365-a1da44e5-7475-4992-be91-9ccec25905b0) można ustawić zasady, które określają, czy zezwalać urządzeniom przenośnym na dostęp do danych w Office 365. Można na przykład ustawić zasady, które zezwalają tylko urządzeniom szyfrowanym na szyfrowanie zawartości na dostęp do Office 365 danych. Zobacz [Tworzenie i wdrażanie zasad zabezpieczeń urządzeń](https://support.microsoft.com/office/create-and-deploy-device-security-policies-d310f556-8bfb-497b-9bd7-fe3c36ea2fd6). <p> Aby uzyskać dodatkową kontrolę nad sposobem interakcji urządzeń przenośnych z Office 365, możesz rozważyć dodanie [Microsoft Intune](/mem/intune/fundamentals/setup-steps).|
|Potrzebujesz kontroli nad kluczami szyfrowania używanymi do szyfrowania danych w centrach danych firmy Microsoft|Jako administrator Office 365 możesz kontrolować klucze szyfrowania organizacji, a następnie skonfigurować Office 365 do szyfrowania danych magazynowanych w centrach danych firmy Microsoft. <p> [Szyfrowanie usługi przy użyciu klucza klienta usługi Microsoft Purview](customer-key-overview.md)|
|Osoby komunikują się za pośrednictwem poczty e-mail (Exchange Online)|Jako administrator Exchange Online masz kilka opcji konfigurowania szyfrowania poczty e-mail. Obejmują one: <ul><li>Używanie [Office 365 szyfrowania komunikatów (OME)](set-up-new-message-encryption-capabilities.md) z usługą Azure Rights Management (Azure RMS) w celu umożliwienia użytkownikom wysyłania zaszyfrowanych wiadomości w organizacji lub poza nią</li><li>Szyfrowanie i podpisywanie cyfrowe wiadomości e-mail przy użyciu [protokołu S/MIME](/exchange/security-and-compliance/smime-exo/smime-exo)</li><li>[Konfigurowanie łączników dla bezpiecznego przepływu poczty w innej organizacji](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/set-up-connectors-for-secure-mail-flow-with-a-partner) przy użyciu protokołu TLS</li></ul> <p> Zobacz [Szyfrowanie poczty e-mail w Office 365](./email-encryption.md).|
|Dostęp do plików jest uzyskiwany z witryn zespołu lub bibliotek dokumentów (OneDrive dla Firm lub SharePoint Online)|Gdy użytkownicy pracują z plikami zapisanymi w OneDrive dla Firm lub SharePoint Online, używane są połączenia TLS. Jest to wbudowane w Office 365 automatycznie. Zobacz [Szyfrowanie danych w usługach OneDrive dla Firm i SharePoint Online](./data-encryption-in-odb-and-spo.md).|
|Pliki są udostępniane podczas spotkań online i konwersacji wiadomości błyskawicznych (Skype dla firm Online)|Gdy użytkownicy pracują z plikami przy użyciu usługi Skype dla firm Online, protokół TLS jest używany na potrzeby połączenia. Jest to wbudowane w Office 365 automatycznie. Zobacz [Zabezpieczenia i archiwizowanie (Skype dla firm Online)](/office365/servicedescriptions/skype-for-business-online-service-description/skype-for-business-online-features).|
|Pliki są udostępniane podczas spotkań online i konwersacji wiadomości błyskawicznych (Microsoft Teams)|Gdy użytkownicy pracują z plikami przy użyciu usługi Microsoft Teams, protokół TLS jest używany na potrzeby połączenia. Jest to wbudowane w Office 365 automatycznie. Usługa Microsoft Teams nie obsługuje obecnie wbudowanego renderowania zaszyfrowanej wiadomości e-mail. Aby zapobiec lądowaniu zaszyfrowanej wiadomości e-mail w usłudze Microsoft Teams jako zaszyfrowanej, zobacz [Często zadawane pytania dotyczące szyfrowania komunikatów](./ome-faq.yml#can-i-automatically-remove-encryption-on-incoming-and-outgoing-mail-).|
|

## <a name="additional-information"></a>Informacje dodatkowe

Aby dowiedzieć się więcej na temat rozwiązań ochrony plików zawierających opcje szyfrowania, zobacz [Rozwiązania ochrony plików w Office 365](https://www.microsoft.com/download/details.aspx?id=55523).
