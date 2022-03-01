---
title: Opis profilów urządzeń
description: Różne profile, które administratorzy mogą przypisywać do urządzeń
keywords: Microsoft Managed Desktop, Microsoft 365, usługa, dokumentacja
ms.service: m365-md
author: tiaraquan
f1.keywords:
- NOCSH
ms.author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
manager: dougeby
ms.topic: article
audience: Admin
ms.openlocfilehash: 0b2bf3b0b4912d9e9b25c38b06262efb696f0cf2
ms.sourcegitcommit: a6651b841f111ea2776cab88bf2c80f805fa8e09
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/13/2022
ms.locfileid: "63026795"
---
# <a name="device-profiles"></a>Profile urządzeń

Do urządzeń można przypisać różne wstępnie ustawione konfiguracje ("profile urządzeń") zoptymalizowane pod kątem potrzeb określonych typów użytkowników. Dostępne są trzy profile urządzeń:

- Standard
- Dane poufne
- Użytkownik zasilania

Profile urządzeń można sobie pomylić z hierarchią opcji konfiguracji urządzeń.

:::image type="content" source="../../media/mmd-profile-options-heirarchy.png" alt-text="Konfiguracje urządzeń wyświetlane jako piramida. Poniżej o treści opis.":::

Podstawową podstawą każdego Microsoft Managed Desktop urządzenia jest standardowa linia bazowa zabezpieczeń, zasady zgodności, Windows ustawienia aktualizacji i grupy. Aby pracować z Microsoft Managed Desktop, każde urządzenie musi zawierać wszystkie te elementy, które nie mogą być zmieniane przez administratorów bez żądania Microsoft Managed Desktop.

Profile urządzeń są wyświetlane na wyższym poziomie. Każde Microsoft Managed Desktop musi mieć przypisany jeden (i tylko jeden) profil. Administratorzy mogą wybrać profil przypisany do urządzenia.

Jeszcze wyższy poziom to [dodatkowe dostosowania](customizing.md). Każde urządzenie może mieć co najmniej jedno (lub nie) dostosowania. Mogą one modyfikować warstwę niższego poziomu (Profile urządzeń lub konfigurację programową) albo być żądaniem całkowicie nowym, które jest nakładane na standardową konfigurację.

Na górze znajdują się Twoje własne modyfikacje, takie jak szczegóły sieci czy aplikacje. Urządzenie może mieć dowolną liczbę tych zmian, które nie są zarządzane ani blokowane przez Microsoft Managed Desktop.


## <a name="device-profile-details"></a>Szczegóły profilu urządzenia

W poniższej tabeli podsumowano ustawienia i ich wartości domyślne dla każdego ustawienia skonfigurowanego przez profile urządzeń. (W tle te ustawienia są konfigurowane razem OMA-URIs przy użyciu niestandardowych profilów konfiguracji w Microsoft Endpoint Manager).

<br>

****

|Funkcja|Dane poufne|Użytkownik zasilania|Standard|
|---|:---:|:---:|:---:|
|**Blokowanie zewnętrznych Storage**|Tak|Tak|Nie|
|**[Poziom bloków chmury](/windows/client-management/mdm/policy-csp-defender#defender-cloudblocklevel)**|High (Wysoki)|High (Wysoki)|High (Wysoki)|
|**Wyłącz konta Microsoft**|Tak|Tak|Nie|
|**Wyłączanie osobistych OneDrive**|Tak|Tak|Nie|
|**[Przełączanie do zabezpieczania pulpitu w celu podwyższenia](/windows/client-management/mdm/policy-csp-localpoliciessecurityoptions#localpoliciessecurityoptions-useraccountcontrol-switchtothesecuredesktopwhenpromptingforelevation)**|Nie|Tak|Nie|
|**Microsoft Defender for Endpoint Device Tag**|M365Managed-SensitiveData|M365Managed-PowerUser|M365Managed-Standard|
|**Administrator na urządzeniu?**|Nie|Tak|Nie|
|**Profil rozwiązania Autopilot**|MMD Standard|Użytkownik zasilania w programie MMD|MMD Standard|
|**AppLocker**|Tak|Nie|Nie|
|**Blokuj magazyn publiczny**|Tak|Tak|Nie|
|

Każdy profil urządzenia obejmuje również następujące elementy:

- Grupa urządzeń Azure Active Directory AAD członkostwa dynamicznego
- Członkostwo statyczne w AAD urządzenia
- Profil Microsoft Endpoint Manager konfiguracji

> [!IMPORTANT]
> Nie modyfikuj bezpośrednio członkostwa w tych grupach. Użyj interfejsu zgodnie z opisem [w tece Ponowne przypisanie profilów](../working-with-managed-desktop/change-device-profile.md).

## <a name="limitations"></a>Ograniczenia

Możesz zażądać wyjątków od profilów urządzeń i ich danych szczegółowych, tak jak w przypadku wszelkich innych zasad. Pamiętaj, że możesz mieć tylko jeden profil urządzenia w swojej organizacji Azure Active Directory ("dzierżawa"). Nie można na przykład zażądać, aby profil urządzenia danych poufnych wyłączył funkcję AppLocker tylko dla niektórych użytkowników. Wszystkie urządzenia z profilem danych poufnych muszą mieć tę samą konfigurację.

Każde urządzenie może mieć tylko jeden profil. Jeśli danego urządzenia używa więcej niż jeden użytkownik, wszyscy użytkownicy na tym urządzeniu będą mieli tę samą konfigurację.
