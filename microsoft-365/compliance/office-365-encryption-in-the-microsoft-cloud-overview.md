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
description: W tym artykule zapoznaliśmy się z omówieniem różnych form szyfrowania używanych do zapewnienia bezpieczeństwa danych klientów w chmurze firmy Microsoft.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 3105da5d17b1656ffa0d29da4f4aa02c9a9f9064
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66633922"
---
# <a name="encryption-in-the-microsoft-cloud"></a>Szyfrowanie w chmurze firmy Microsoft

Dane klientów w ramach usług firmy Microsoft w chmurze dla przedsiębiorstw są chronione przez kilka technologii i procesów, w tym różne formy szyfrowania. (Dane klienta w tym dokumencie obejmują zawartość skrzynki pocztowej Exchange Online, treść wiadomości e-mail, wpisy kalendarza oraz zawartość załączników wiadomości e-mail, a w stosownych przypadkach Skype dla firm zawartości), zawartość witryny usługi SharePoint Online oraz pliki przechowywane w witrynach oraz pliki przekazane do OneDrive dla Firm lub Skype dla firm). Firma Microsoft korzysta z wielu metod szyfrowania, protokołów i szyfrów w swoich produktach i usługach, aby zapewnić bezpieczną ścieżkę do danych klientów w celu przechodzenia przez nasze usługi w chmurze oraz chronić poufność danych klientów przechowywanych w naszych usługach w chmurze. Firma Microsoft korzysta z jednych z najsilniejszych, najbezpieczniejszych dostępnych protokołów szyfrowania, aby zapewnić bariery przed nieautoryzowanym dostępem do danych klientów. Właściwe zarządzanie kluczami jest również istotnym elementem najlepszych rozwiązań w zakresie szyfrowania, a firma Microsoft pracuje nad zapewnieniem, że wszystkie klucze szyfrowania zarządzane przez firmę Microsoft są prawidłowo zabezpieczone.

Dane klientów przechowywane w usługach firmy Microsoft w chmurze dla przedsiębiorstw są chronione przy użyciu co najmniej jednej formy szyfrowania. (Weryfikacja naszych zasad kryptograficznych i ich wymuszanie jest niezależnie weryfikowana przez wielu audytorów innych firm, a raporty z tych inspekcji są dostępne w [portalu zaufania usługi](https://aka.ms/stp)).

Firma Microsoft udostępnia technologie po stronie usługi, które szyfrują dane klientów magazynowanych i przesyłanych. Na przykład w przypadku danych klientów magazynowanych platforma Microsoft Azure używa [BitLocker](/windows/device-security/bitlocker/bitlocker-overview) i [DM-Crypt](https://en.wikipedia.org/wiki/Dm-crypt), a platforma Microsoft 365 używa BitLocker, [szyfrowania usługi Azure Storage](/azure/), [rozproszonego menedżera kluczy](./exchange-online-secures-email-secrets.md) (DKM) i szyfrowania usługi Microsoft 365. W przypadku danych klientów przesyłanych, platformy Azure, Office 365, komercyjnej pomocy technicznej firmy Microsoft, usługi Microsoft Dynamics 365, usługi Microsoft Power BI i Visual Studio Team Services używają standardowych w branży protokołów bezpiecznego transportu, takich jak Internet Protocol Security (IPsec) i Transport Layer Security (TLS), między centrami danych firmy Microsoft i między urządzeniami użytkowników a centrami danych firmy Microsoft.

Oprócz podstawowego poziomu zabezpieczeń kryptograficznych zapewnianego przez firmę Microsoft nasze usługi w chmurze obejmują również opcje kryptografii, które można zarządzać. Możesz na przykład włączyć szyfrowanie ruchu między maszynami wirtualnymi platformy Azure a ich użytkownikami. Dzięki [usłudze Azure Virtual Networks](https://azure.microsoft.com/services/virtual-network/) można użyć standardowego w branży protokołu IPsec do szyfrowania ruchu między firmową bramą sieci VPN a platformą Azure. Możesz również zaszyfrować ruch między maszynami wirtualnymi w sieci wirtualnej. Ponadto [nowe funkcje szyfrowania wiadomości Office 365](set-up-new-message-encryption-capabilities.md) umożliwiają wysyłanie zaszyfrowanej poczty do każdego.

Zgodnie ze standardem zabezpieczeń operacyjnych infrastruktury klucza publicznego, który jest składnikiem [zasad zabezpieczeń firmy Microsoft](https://servicetrust.microsoft.com/ViewPage/TrustDocuments?command=Download&downloadType=Document&downloadId=5868ecc8-50b7-4f91-b43f-640e2b99e86e&docTab=6d000410-c9e9-11e7-9a91-892aae8839ad_FAQ%20and%20White%20Papers), firma Microsoft używa funkcji kryptograficznych zawartych w systemie operacyjnym Windows na potrzeby certyfikatów i mechanizmów uwierzytelniania. Mechanizmy te obejmują korzystanie z modułów kryptograficznych, które spełniają standard [FIPS (Federal Information Processing Standards](https://csrc.nist.gov/publications/PubsFIPS.html) ) (FIPS) rządu STANÓW Zjednoczonych. Odpowiednie numery certyfikatów NIST dla firmy Microsoft można wyszukać przy użyciu programu [cmvp programu kryptograficznego modułu walidacji](https://csrc.nist.gov/projects/cryptographic-module-validation-program/validated-modules/search).

> [UWAGA] Aby uzyskać dostęp do zasad zabezpieczeń firmy Microsoft jako zasobu, musisz zalogować się przy użyciu konta służbowego. Jeśli nie masz jeszcze subskrypcji, [możesz utworzyć konto bezpłatnej wersji próbnej](https://servicetrust.microsoft.com/Home/TrialSubscriptions).

FIPS 140-2 to standard przeznaczony specjalnie do weryfikowania modułów produktów, które implementują kryptografię, a nie produkty, które z nich korzystają. Moduły kryptograficzne, które są implementowane w ramach usługi, mogą być certyfikowane jako spełniające wymagania dotyczące siły skrótu, zarządzania kluczami i tym podobnych. Moduły kryptograficzne i szyfry używane do ochrony poufności, integralności lub dostępności danych w usługach firmy Microsoft w chmurze spełniają standard FIPS 140-2.

Firma Microsoft certyfikuje podstawowe moduły kryptograficzne używane w naszych usługach w chmurze z każdą nową wersją systemu operacyjnego Windows:

- Azure i Azure U.S. Government
- Dynamics 365 i Dynamics 365 U.S. Government
- Office 365, Office 365 rząd USA i Office 365 obrony rządu USA

Szyfrowanie danych klientów magazynowanych jest zapewniane przez wiele technologii po stronie usługi, w tym BitLocker, DKM, szyfrowanie usługi Azure Storage i szyfrowanie usług w Exchange Online, Skype dla firm, OneDrive dla Firm i SharePoint Online. Office 365 szyfrowanie usługi obejmuje opcję używania kluczy szyfrowania zarządzanych przez klienta, które są przechowywane w usłudze Azure Key Vault. Ta opcja klucza zarządzanego przez klienta o nazwie [Klucz klienta](./customer-key-overview.md) jest dostępna dla Exchange Online, sharepoint online, Skype dla firm i OneDrive dla Firm.

W przypadku danych klientów przesyłanych wszystkie serwery Office 365 negocjują bezpieczne sesje przy użyciu protokołu TLS domyślnie z maszynami klienckimi w celu zabezpieczenia danych klientów. Na przykład Office 365 będzie negocjować bezpieczne sesje w celu Skype dla firm, programu Outlook i Outlook w sieci Web, klientów mobilnych i przeglądarek internetowych.

(Domyślnie wszystkie serwery dostępne dla klientów negocjują protokół TLS 1.2).

## <a name="related-links"></a>Linki pokrewne

- [Szyfrowanie na platformie Azure](office-365-azure-encryption.md)
- [Funkcja BitLocker i rozproszony menedżer kluczy (DKM) na potrzeby szyfrowania](office-365-bitlocker-and-distributed-key-manager-for-encryption.md)
- [szyfrowanie usługi Office 365](office-365-service-encryption.md)
- [szyfrowanie Office 365 dla Skype dla firm, OneDrive dla Firm, sharepoint online i Exchange Online](/compliance/assurance/assurance-encryption-for-microsoft-365-services) 
- [Szyfrowanie danych podczas przesyłania](/compliance/assurance/assurance-encryption-in-transit)
- [Funkcje szyfrowania zarządzanego przez klienta](office-365-customer-managed-encryption-features.md)
- [Zagrożenia i zabezpieczenia związane z szyfrowaniem](office-365-encryption-risks-and-protections.md)
- [Szyfrowanie w usłudze Microsoft Dynamics 365](office-365-encryption-in-microsoft-dynamics-365.md)
