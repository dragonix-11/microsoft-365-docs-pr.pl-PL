---
title: BitLocker szyfrowania
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
description: Dowiedz się, jak Office 365 używa szyfrowania BitLocker, co zmniejsza ryzyko kradzieży danych z powodu utraty lub kradzieży komputerów i dysków.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: dec62da7bc4d29891dcd86ec378faeb52a2d3d9f
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66633900"
---
# <a name="bitlocker-and-distributed-key-manager-dkm-for-encryption"></a>Funkcja BitLocker i rozproszony menedżer kluczy (DKM) na potrzeby szyfrowania

Serwery firmy Microsoft używają BitLocker do szyfrowania dysków zawierających dane klientów magazynowane na poziomie woluminu. BitLocker szyfrowania jest funkcją ochrony danych wbudowaną w system Windows. BitLocker jest jedną z technologii używanych do ochrony przed zagrożeniami w przypadku wygaśnięcia innych procesów lub kontroli (np. kontroli dostępu lub recyklingu sprzętu), które mogą prowadzić do uzyskania przez kogoś fizycznego dostępu do dysków zawierających dane klienta. W takim przypadku BitLocker eliminuje możliwość kradzieży lub ujawnienia danych z powodu utraty, kradzieży lub niewłaściwego zlikwidowania komputerów i dysków.

BitLocker jest wdrażana za pomocą 256-bitowego szyfrowania AES (Advanced Encryption Standard) na dyskach zawierających dane klientów w usługach Exchange Online, SharePoint Online i Skype dla firm. Sektory dysków są szyfrowane za pomocą klucza szyfrowania pełnego woluminu (FVEK), który jest szyfrowany za pomocą klucza głównego woluminu (VMK), który z kolei jest powiązany z modułem TPM (Trusted Platform Module) na serwerze. Maszyna wirtualna bezpośrednio chroni klucz FVEK i dlatego ochrona zestawu VMK staje się krytyczna. Na poniższej ilustracji przedstawiono przykład łańcucha ochrony kluczy BitLocker dla danego serwera (w tym przypadku przy użyciu serwera Exchange Online).

W poniższej tabeli opisano łańcuch ochrony kluczy BitLocker dla danego serwera (w tym przypadku serwera Exchange Online).

| OCHRONA KLUCZY | ZIARNISTOŚĆ | JAK WYGENEROWANO? | GDZIE JEST PRZECHOWYWANY? | OCHRONY |
|--------------------------------------------------------------------------------|-------------------------------------------------|----------------|-------------------------|--------------------------------------------------------------------------------------------------|
| 256-bitowy klucz zewnętrzny AES | Na serwer | interfejsy API BitLocker | TPM lub Secret Safe | Skrytka/Access Control |
|  |  |  | Rejestr serwera skrzynki pocztowej | Zaszyfrowany moduł TPM |
| 48-cyfrowe hasło liczbowe | Na dysk | interfejsy API BitLocker | Active Directory | Skrytka/Access Control |
| Certyfikat X.509 jako agent odzyskiwania danych (DRA) nazywany również ochroną klucza publicznego | Środowisko (np. Exchange Online wielodostępne) | Microsoft CA | System kompilacji | Żaden użytkownik nie ma pełnego hasła do klucza prywatnego. Hasło jest objęte ochroną fizyczną. |


BitLocker zarządzanie kluczami obejmuje zarządzanie kluczami odzyskiwania używanymi do odblokowywania/odzyskiwania zaszyfrowanych dysków w centrum danych firmy Microsoft. Platforma Microsoft 365 przechowuje klucze główne w zabezpieczonym udziale, dostępnym tylko dla osób, które zostały sprawdzone i zatwierdzone. Poświadczenia kluczy są przechowywane w zabezpieczonym repozytorium danych kontroli dostępu (co nazywamy "magazynem wpisów tajnych"), co wymaga wysokiego poziomu uprawnień i zatwierdzeń zarządzania w celu uzyskania dostępu przy użyciu narzędzia do podniesienia uprawnień dostępu just in time.

BitLocker obsługuje klucze, które dzielą się na dwie kategorie zarządzania:

- BitLocker kluczy zarządzanych, które są zazwyczaj krótkotrwałe i powiązane z okresem istnienia wystąpienia systemu operacyjnego zainstalowanego na serwerze lub na danym dysku. Te klucze są usuwane i resetowane podczas ponownej instalacji serwera lub formatowania dysku.

- BitLocker klucze odzyskiwania, które są zarządzane poza BitLocker, ale używane do odszyfrowywania dysku. BitLocker używa kluczy odzyskiwania w scenariuszu, w którym system operacyjny jest ponownie instalowany, a szyfrowane dyski danych już istnieją. Klucze odzyskiwania są również używane przez sondy monitorowania dostępności zarządzanej w Exchange Online gdzie osoba odpowiadająca może wymagać odblokowania dysku.

woluminy chronione BitLocker są szyfrowane przy użyciu klucza szyfrowania pełnego woluminu, który z kolei jest szyfrowany za pomocą klucza głównego woluminu. BitLocker używa algorytmów zgodnych ze standardem FIPS, aby upewnić się, że klucze szyfrowania nigdy nie są przechowywane ani wysyłane za pośrednictwem przewodu. Implementacja rozwiązania Microsoft 365 dotycząca ochrony danych przy spoczynku klienta nie odbiega od domyślnej implementacji BitLocker.
