---
title: BitLocker do szyfrowania
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
description: Dowiedz się, Office 365 korzysta z szyfrowania BitLocker, co ogranicza możliwość kradzieży danych w wyniku zgubienia lub kradzieży komputera lub dyskietki.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 343a5966dc24954e98d7d31977aacbc09daaba11
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62986654"
---
# <a name="bitlocker-and-distributed-key-manager-dkm-for-encryption"></a>Menedżer kluczy funkcji BitLocker i menedżera kluczy rozłożonych (DKM) do szyfrowania

Serwery firmy Microsoft używają funkcji BitLocker do szyfrowania dysków zawierających dane klienta na poziomie głośności. Szyfrowanie BitLocker to funkcja ochrony danych wbudowana w funkcje Windows. BitLocker to jedna z technologii zabezpieczania przed zagrożeniami na wypadek awarii innych procesów lub kontrolek (np. kontroli dostępu lub ponownego przetwarzania sprzętu), które mogą doprowadzić do tego, że ktoś uzyskuje dostęp fizyczny do dysków zawierających dane klienta. W takim przypadku dzięki funkcji BitLocker można wyeliminować możliwość kradzieży lub naświetlenia danych z powodu zagubionych, skradzionych lub nieodpowiednich likwidowanych komputerów i dyskietek.

Funkcję BitLocker wdrożono przy użyciu 256-bitowego szyfrowania Advanced Encryption Standard (AES) na dyskach zawierających dane klienta w usługach Exchange Online, SharePoint Online i Skype dla firm. Dysk jest szyfrowany przy użyciu klucza FVEK (Full Volume Encryption Key), który jest szyfrowany przy użyciu klucza wzorca woluminu (VMK), który z kolei jest powiązany z modułem trusted platform Module (TPM) na serwerze. Maszyny wirtualnej bezpośrednio chroni FVEK, dlatego ochrona maszyny wirtualnej staje się bardzo ważna. Na poniższej ilustracji przedstawiono przykład łańcucha ochrony klucza funkcji BitLocker dla danego serwera (w tym przypadku przy użyciu Exchange Online serwera).

W poniższej tabeli opisano łańcuch ochrony klucza funkcji BitLocker dla danego serwera (w tym przypadku jest to Exchange Online serwera).

| KLUCZOWY KLUCZ | SZCZEGÓŁOWOŚĆ | JAK WYGENEROWANO? | GDZIE JEST ON PRZECHOWYWANY? | OCHRONA |
|--------------------------------------------------------------------------------|-------------------------------------------------|----------------|-------------------------|--------------------------------------------------------------------------------------------------|
| 256-bitowy klawisz zewnętrzny AES | Na serwer | Interfejsy API funkcji BitLocker | TPM lub Tajny Sejf | Skrytka / kontrola dostępu |
|  |  |  | Rejestr serwera skrzynek pocztowych | TPM encrypted |
| 48-cyfrowe hasło liczbowe | Na dysk | Interfejsy API funkcji BitLocker | Active Directory | Skrytka / kontrola dostępu |
| Certyfikat X.509 jako agent odzyskiwania danych (DRA) nazywany także kluczem publicznym | Środowisko (np. Exchange Online wielotensywowa) | Microsoft CA | System kompilacji | Żaden użytkownik nie ma pełnego hasła do klucza prywatnego. Hasło jest chronione fizycznie. |


Zarządzanie kluczami funkcji BitLocker obejmuje zarządzanie kluczami odzyskiwania, które są używane do odblokowywania/odzyskiwania zaszyfrowanych dyskietek w centrum danych firmy Microsoft. Microsoft 365 klucze główne są przechowywane w zabezpieczonym udziałze, dostępnym tylko dla osób, które zostały zabezpieczone ekranem i zatwierdzone. Poświadczenia kluczy są przechowywane w repozytorium zabezpieczonym na dane kontroli dostępu (tzw. "tajny magazyn"), który wymaga wysokiego poziomu zatwierdzeń podwyższenia i zatwierdzeń zarządzania w celu uzyskania dostępu za pomocą narzędzia podwyższenia dostępu w czasie rzeczywistym.

Funkcję BitLocker obsługuje klucze, które można podzielone na dwie kategorie zarządzania:

- Klucze zarządzane przez funkcję BitLocker, które są zwykle krótkie i powiązane z okresem istnienia wystąpienia systemu operacyjnego zainstalowanego na serwerze lub na danym dysku. Te klucze są usuwane i resetowane podczas ponownej instalacji serwera lub formatowania dysku.

- Klucze odzyskiwania funkcji BitLocker, które są zarządzane poza funkcją BitLocker, ale używane do odszyfrowywania dysków. W funkcji BitLocker są używane klucze odzyskiwania w scenariuszu, w którym system operacyjny jest ponownie instalowany, i istnieją już zaszyfrowane dyskietki z danymi. Klucze odzyskiwania są również używane przez pracowników monitorowania dostępności zarządzanej w Exchange Online, gdzie może być konieczne odblokowanie dysku przez odpowiadającą.

Woluminy chronione funkcją BitLocker są szyfrowane przy użyciu pełnego klucza szyfrowania woluminu, który z kolei jest szyfrowany przy użyciu klucza wzorca woluminu. W funkcji BitLocker używane są algorytmy zgodne z fipsą, aby zapewnić, że klucze szyfrowania nie są nigdy przechowywane ani wysyłane za pośrednictwem przelewu w wyczyszczeniu. Implementacja Microsoft 365 danych klienta w czasie przechowywania danych nie odbiega od domyślnej implementacji funkcji BitLocker.
