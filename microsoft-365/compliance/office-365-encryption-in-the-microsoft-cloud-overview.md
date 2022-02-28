---
title: Szyfrowanie w chmurze firmy Microsoft
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: ''
search.appverid:
- MET150
ms.collection:
- Strat_O365_Enterprise
- M365-security-compliance
- Strat_O365_Enterprise
description: W tym artykule zapoznaj się z omówieniem różnych form szyfrowania używanych do ochrony danych klientów w chmurze firmy Microsoft.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: c888c1958eb5265c31ae981e42a96eeeeb57f3ef
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62987764"
---
# <a name="encryption-in-the-microsoft-cloud"></a>Szyfrowanie w chmurze firmy Microsoft

Dane klienta w usługach firmy Microsoft w chmurze przedsiębiorstwa są chronione przez kilka technologii i procesów, w tym różne formy szyfrowania. Exchange Online (Dane klienta w tym dokumencie obejmują zawartość skrzynek pocztowych, treść wiadomości e-mail, wpisy kalendarza i zawartość załączników wiadomości e-mail oraz( w razie potrzeby) zawartość witryny usługi Skype dla firm), zawartość witryn usługi SharePoint Online i pliki przechowywane w witrynach oraz pliki przekazane do usługi OneDrive dla Firm lub Skype dla firm). Firma Microsoft używa wielu metod szyfrowania, protokołów i szyfrowania w swoich produktach i usługach, aby zapewnić bezpieczną ścieżkę do danych klientów do podróży między naszymi usługami w chmurze oraz w celu ochrony poufności danych klienta przechowywanych w naszych usługach w chmurze. Firma Microsoft korzysta z najsilniejszych i najbezpieczniejszych dostępnych protokołów szyfrowania, aby zapewnić bariery przed nieautoryzowanym dostępem do danych klientów. Właściwe zarządzanie kluczami jest również podstawowym elementem najlepszych rozwiązań szyfrowania, a firma Microsoft pracuje nad zapewnieniem prawidłowego zabezpieczenia wszystkich kluczy szyfrowania zarządzanych przez firmę Microsoft.

Dane klienta przechowywane w usługach firmy Microsoft w chmurze przedsiębiorstwa są chronione za pomocą jednej lub kilku metod szyfrowania. (Sprawdzanie poprawności naszych zasad szyfrowania i ich wymuszania jest niezależnie weryfikowane przez wielu audytorów innych podmiotów, a raporty o tych inspekcjach są dostępne w [Portalu zaufania](https://aka.ms/stp) usług).

Firma Microsoft udostępnia technologie po stronie usług, które szyfrują dane klienta w czasie spoczynku i podczas przesyłania. Na przykład w przypadku danych klientów w spoczynku usługa Microsoft Azure korzysta z funkcji [BitLocker](/windows/device-security/bitlocker/bitlocker-overview) i [DM-Crypt](https://en.wikipedia.org/wiki/Dm-crypt), Microsoft 365 korzysta z funkcji BitLocker, szyfrowania usługi [Azure Storage](/azure/)[, Menedżera](./exchange-online-secures-email-secrets.md) kluczy rozłożonych (DKM) i szyfrowania Microsoft 365 usług. W przypadku danych klientów podczas przesyłania, platformy Azure, usługi Office 365, komercyjnej pomocy technicznej firmy Microsoft, usługi Microsoft Dynamics 365, usługi Microsoft Power BI i usługi Visual Studio Team Services należy używać protokołów bezpiecznego transportu standardu branżowego, takich jak IPsec (Internet Protocol Security) i Transport Layer Security (TLS), między centrami danych firmy Microsoft i między urządzeniami użytkowników. Centra danych firmy Microsoft.

Poza bazowym poziomem zabezpieczeń kryptograficznych dostarczanych przez firmę Microsoft nasze usługi w chmurze zawierają również opcje kryptograficzne, które można zarządzać. Na przykład możesz włączyć szyfrowanie ruchu między ich maszynami wirtualnymi platformy Azure i ich użytkownikami. Za [pomocą wirtualnych sieci Azure](https://azure.microsoft.com/services/virtual-network/) możesz użyć standardowego protokołu IPsec, aby szyfrować ruch między firmową bramą VPN a platformą Azure. Możesz również zaszyfrować ruch między maszynami wirtualnymi w twojej sieci wirtualnej. Ponadto nowe [funkcje Szyfrowanie wiadomości usługi Office 365 umożliwiają](set-up-new-message-encryption-capabilities.md) wysyłanie zaszyfrowanych wiadomości e-mail do innych osób.

Zgodnie ze standardem zabezpieczeń operacyjnymi dla infrastruktury publicznej, który jest składnikiem zasad zabezpieczeń firmy Microsoft, firma [Microsoft](https://servicetrust.microsoft.com/ViewPage/TrustDocuments?command=Download&downloadType=Document&downloadId=5868ecc8-50b7-4f91-b43f-640e2b99e86e&docTab=6d000410-c9e9-11e7-9a91-892aae8839ad_FAQ%20and%20White%20Papers) korzysta z funkcji kryptograficznych zawartych w systemie operacyjnym Windows do obsługi certyfikatów i mechanizmów uwierzytelniania. Mechanizmy te obejmują użycie modułów kryptograficznych spełniających standard FIPS (Federal Information Processing Standards) amerykańskiego departamentu informacji (FIPS, [Federal Information Processing Standards](https://csrc.nist.gov/publications/PubsFIPS.html) ) 140-2. Odpowiednie numery certyfikatów NIST można wyszukać dla firmy Microsoft, korzystając z polecenia [CMVP programu sprawdzania poprawności modułu kryptograficznego](https://csrc.nist.gov/projects/cryptographic-module-validation-program/validated-modules/search).

> [UWAGA] Aby uzyskać dostęp do zasad zabezpieczeń Firmy Microsoft jako zasobu, musisz zalogować się przy użyciu konta służbowego. Jeśli nie masz jeszcze abonamentu, [możesz utworzyć bezpłatne wersje próbne](https://servicetrust.microsoft.com/Home/TrialSubscriptions).

FIPS 140-2 to standard zaprojektowany specjalnie do sprawdzania poprawności modułów produktów implementujących kryptografię, a nie do produktów, które z nich korzystają. Moduły kryptograficzne zaimplementowane w ramach usługi można certyfikowane jako spełniać wymagania dotyczące siły skrótów, zarządzania kluczami i tym podobne. Moduły kryptograficzne i szyfrowania używane do ochrony poufności, integralności lub dostępności danych w usługach firmy Microsoft w chmurze spełniają standard FIPS 140-2.

Firma Microsoft ma interfejs do podstawowych modułów kryptograficznych używanych w naszych usługach w chmurze w każdej nowej wersji tego Windows operacyjnego:

- Azure i Azure U.S. Government
- Dynamics 365 i Dynamics 365 U.S. Government
- Office 365, Office 365 Rząd Stanów Zjednoczonych i Office 365 Rząd Stanów Zjednoczonych

Szyfrowanie danych klientów w spoczynku jest udostępniane przez wiele technologii po stronie usługi, w tym przez funkcję BitLocker, DKM, szyfrowanie usług Azure Storage oraz szyfrowanie usług w usługach Exchange Online, Skype dla firm, OneDrive dla Firm i SharePoint Online. Office 365 tej usłudze zawiera opcję używania zarządzanych przez klienta kluczy szyfrowania, które są przechowywane w magazynie kluczy platformy Azure. Ta opcja klucza zarządzanego przez klienta, o nazwie [Klucz](./customer-key-overview.md) klienta, jest dostępna dla Exchange Online, SharePoint Online, Skype dla firm i OneDrive dla Firm.

W przypadku danych klienta podczas przesyłania wszystkie serwery Office 365 bezpiecznego sesji, w których są domyślnie używane sesje TLS z komputerami klienckimi w celu zabezpieczenia danych klienta. Na przykład Office 365 bezpieczne sesje, Skype dla firm, Outlook i Outlook w sieci Web, klientów przenośnych i przeglądarek sieci Web.

(Wszystkie serwery skierowane do klienta domyślnie wynegocjowają negocjacje w sprawie standardu TLS 1.2).

## <a name="related-links"></a>Linki pokrewne

- [Szyfrowanie na platformie Azure](office-365-azure-encryption.md)
- [Menedżer kluczy funkcji BitLocker i menedżera kluczy rozłożonych (DKM) do szyfrowania](office-365-bitlocker-and-distributed-key-manager-for-encryption.md)
- [Office 365 szyfrowania usługi](office-365-service-encryption.md)
- [Office 365 do Skype dla firm, OneDrive dla Firm, SharePoint online i Exchange Online](/compliance/assurance/assurance-encryption-for-microsoft-365-services) 
- [Szyfrowanie danych podczas przesyłania](/compliance/assurance/assurance-encryption-in-transit)
- [Funkcje szyfrowania zarządzane przez klienta](office-365-customer-managed-encryption-features.md)
- [Czynniki ryzyka związane z szyfrowaniem i ochrona](office-365-encryption-risks-and-protections.md)
- [Szyfrowanie w uwitrynie Microsoft Dynamics 365](office-365-encryption-in-microsoft-dynamics-365.md)