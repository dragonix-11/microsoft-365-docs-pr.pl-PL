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
ms.openlocfilehash: d12a197db8dbcb6356882082c212754fef726d4e
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63320833"
---
# <a name="device-profiles"></a>Profile urządzeń

Profile urządzeń można sobie pomylić z hierarchią opcji konfiguracji urządzeń.

:::image type="content" source="../../media/mmd-profile-options-heirarchy.png" alt-text="Konfiguracje urządzeń wyświetlane jako piramida. Poniżej o treści opis.":::

| Opcje konfiguracji urządzenia | Opis
| ----- | ----- |
| Twoje konfiguracje | U góry znajdują się Twoje własne konfiguracje, takie jak szczegóły sieci lub aplikacje. Urządzenie może mieć dowolną liczbę tych konfiguracji, które nie są zarządzane ani blokowane przez Microsoft Managed Desktop. |
| Dostosowania | Następny wyższy poziom to dodatkowe [dostosowania](customizing.md). Każde urządzenie może mieć co najmniej jedno (lub nie) dostosowania. Dostosowania mogą modyfikować warstwę niższego poziomu (Profile urządzeń lub konfigurację programową) albo być całkowicie nowym żądaniem, które jest nakładane na konfigurację standardową. |
| Profile urządzeń | Każde Microsoft Managed Desktop musi mieć przypisany jeden profil (i tylko jeden profil). Administratorzy mogą wybrać profil przypisany do urządzenia.<br><br>Do urządzeń można przypisać różne wstępnie ustawione profile. Każdy profil jest zoptymalizowany pod kątem konkretnych typów użytkowników. Dostępne są trzy profile urządzeń:<ul><li>Standard</li><li>Dane poufne</li><li>Użytkownik zasilania</li> |
| Foundation | Podstawowa podstawa każdego Microsoft Managed Desktop ma podstawę, która obejmuje:<br><ul><li>Standardowy plan bazowy zabezpieczeń</li><li>Zasady zgodności</li><li>Windows ustawienia aktualizacji</li><li>Grupy</li></ul><br>Aby pracować z Microsoft Managed Desktop, każde urządzenie musi zawierać wszystkie te elementy. Administratorzy nie mogą zmieniać tych elementów. Musisz przesłać wniosek o Microsoft Managed Desktop. |

## <a name="device-profile-details"></a>Szczegóły profilu urządzenia

W poniższej tabeli podsumowano ustawienia i ich wartości domyślne dla każdego ustawienia skonfigurowanego przez profile urządzeń. Te ustawienia są konfigurowane w tle razem z OMA-URIs przy użyciu niestandardowych profilów konfiguracji w Microsoft Endpoint Manager.

<br>

****

| Funkcja | Dane poufne | Użytkownik zasilania | Standard |
| ----- | :-----: | :-----: | :-----: |
|**Blokowanie zewnętrznych Storage**| Tak | Tak | Nie |
|**[Poziom bloków chmury](/windows/client-management/mdm/policy-csp-defender#defender-cloudblocklevel)**| High (Wysoki) | High (Wysoki) | High (Wysoki) |
|**Wyłącz konta Microsoft**| Tak | Tak | Nie |
|**Wyłączanie osobistych OneDrive**| Tak | Tak | Nie |
|**[Przełączanie do zabezpieczania pulpitu w celu podwyższenia](/windows/client-management/mdm/policy-csp-localpoliciessecurityoptions#localpoliciessecurityoptions-useraccountcontrol-switchtothesecuredesktopwhenpromptingforelevation)**| Nie | Tak | Nie |
|**Microsoft Defender for Endpoint Device Tag**| M365Managed-SensitiveData | M365Managed-PowerUser | M365Managed-Standard |
|**Administrator na urządzeniu?**| Nie | Tak | Nie |
|**Profil rozwiązania Autopilot**| MMD Standard | Użytkownik zasilania w programie MMD | MMD Standard |
|**AppLocker**| Tak | Nie | Nie |
|**Blokuj magazyn publiczny**| Tak | Tak | Nie |
|

Każdy profil urządzenia obejmuje również następujące elementy:

- Członkostwo dynamiczne Azure Active Directory grupie urządzeń.
- Statyczne członkostwo w Azure Active Directory urządzeniu.
- Profil Microsoft Endpoint Manager konfiguracji.

> [!IMPORTANT]
> Nie modyfikuj bezpośrednio członkostwa w tych grupach. Użyj interfejsu zgodnie z opisem [w tece Ponowne przypisanie profilów](../working-with-managed-desktop/change-device-profile.md).

## <a name="limitations"></a>Ograniczenia

Możesz zażądać wyjątków od profilów urządzeń i ich danych szczegółowych, tak jak w przypadku wszelkich innych zasad.

Pamiętaj, że możesz mieć tylko jeden profil urządzenia w swojej organizacji Azure Active Directory ("dzierżawa"). Nie można na przykład zażądać, aby profil urządzenia danych poufnych wyłączył funkcję AppLocker tylko dla niektórych użytkowników. Wszystkie urządzenia z profilem urządzenia danych poufnych muszą mieć tę samą konfigurację.

Każde urządzenie może mieć tylko jeden profil. Jeśli danego urządzenia używa więcej niż jeden użytkownik, wszyscy użytkownicy na tym urządzeniu będą mieli tę samą konfigurację.
