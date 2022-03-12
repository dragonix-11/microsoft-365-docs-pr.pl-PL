---
title: Wymagania dotyczące usługi Microsoft Defender dla firm
description: Wymagania dotyczące licencji, sprzętu i oprogramowania usługi Microsoft Defender dla firm
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 03/10/2022
ms.prod: m365-security
ms.technology: mdb
localization_priority: Normal
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: 3259b08bcbf62ce0547363f6020399ce444f7f79
ms.sourcegitcommit: 2697938d2d4fec523b501c5e7b0b8ec8f34e59b0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2022
ms.locfileid: "63450594"
---
# <a name="microsoft-defender-for-business-requirements"></a>Wymagania programu Microsoft Defender dla firm

> [!IMPORTANT]
> Program Microsoft Defender dla firm jest wprowadzany [dla Microsoft 365 Business Premium](../../business-premium/index.md) klientów od 1 marca 2022 r. Autonomiczna subskrypcja usługi Defender dla firm jest w wersji Preview i będzie stopniowo wprowadzana u klientów i partnerów IT, [](https://aka.ms/mdb-preview) którzy zarejestrują się tutaj, aby poprosić o to. Wersja Preview zawiera [początkowy zestaw scenariuszy](mdb-tutorials.md#try-these-preview-scenarios), a my będziemy regularnie dodawać funkcje.
> 
> Niektóre informacje w tym artykule dotyczą wstępnie dzierżawionych produktów/usług, które mogą zostać znacząco zmodyfikowane przed ich komercyjną premierą. Firma Microsoft nie udziela żadnych gwarancji, jawnych ani domniemanych, dotyczących podanych tutaj informacji. 

W tym artykule opisano wymagania dotyczące programu Microsoft Defender dla firm.

## <a name="what-to-do"></a>Co należy zrobić

1. [Przejrzyj wymagania i upewnij się, że są spełnione](#review-the-requirements).

2. [Przejdź do następnych kroków](#next-steps).

>
> **Masz minutę?**
> Prosimy o <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">krótką ankietę na temat programu Microsoft Defender dla firm</a>. Chcemy ją usłyszeć!
>

## <a name="review-the-requirements"></a>Przejrzyj wymagania

W poniższej tabeli wymieniono podstawowe wymagania dotyczące konfigurowania i używania programu Microsoft Defender dla firm. <br/><br/>

| Wymaganie | Opis |
|:---|:---|
| Subskrypcja | Microsoft 365 Business Premium <br/>--- lub ---<br/>Microsoft Defender for Business (autonomiczny, obecnie w wersji Preview). <br/><br/> Zobacz [Jak uzyskać usługę Microsoft Defender dla firm](get-defender-business.md).<br/><br/>Zwróć uwagę, że jeśli masz wiele subskrypcji, najwyższa subskrypcja ma pierwszeństwo. Jeśli na przykład masz usługę Microsoft Defender for Endpoint Plan 2 (zakupioną lub próbną subskrypcję) i otrzymasz usługę Microsoft Defender for Business, usługa Defender dla punktu końcowego (plan 2) ma pierwszeństwo. W takim przypadku nie zobaczysz usługi Defender dla firm.  |
| Datacenter | Jedna z następujących lokalizacji centrów danych: <br/>- Unia Europejska <br/>— Zjednoczone Królestwo <br/>- Stany Zjednoczone |
| Konta użytkowników | Konta użytkowników są tworzone w centrum administracyjne platformy Microsoft 365 ([https://admin.microsoft.com](https://admin.microsoft.com))<br/><br/>Licencje usługi Microsoft Defender dla firm są przypisywane w centrum administracyjne platformy Microsoft 365<br/><br/>Aby uzyskać pomoc na temat tego zadania, zobacz [Dodawanie użytkowników i przypisywanie licencji](../../admin/add-users/add-users.md). |
| Uprawnienia  | Aby zarejestrować się w programie Microsoft Defender dla firm, musisz być administratorem globalnym.<br/><br/>Aby uzyskać dostęp do portalu Microsoft 365 Defender, użytkownicy muszą mieć przypisaną jedną z następujących ról [w usłudze Azure AD](mdb-roles-permissions.md): <br/>- Czytnik zabezpieczeń<br/>- Administrator zabezpieczeń<br/>— Administrator globalny<br/><br/>Aby dowiedzieć się więcej, zobacz [Role i uprawnienia w programie Microsoft Defender dla firm](mdb-roles-permissions.md). |
| Wymagania dotyczące przeglądarki | Microsoft Edge lub Google Chrome |
| System operacyjny | Aby można było zarządzać urządzeniami w programie Microsoft Defender dla firm, na tych urządzeniach musi być uruchomiony jeden z następujących systemów operacyjnych: <br/>— Windows 10 Business lub nowszy <br/>— Windows 10 Professional lub nowszy <br/>— Windows 10 Enterprise lub nowszy <br/><br/>Upewnij się, [że zainstalowano kb5006738](https://support.microsoft.com/topic/october-26-2021-kb5006738-os-builds-19041-1320-19042-1320-and-19043-1320-preview-ccbce6bf-ae00-4e66-9789-ce8e7ea35541) . <br/><br/>Jeśli zarządzasz urządzeniami w programie Microsoft Intune (lub Microsoft Endpoint Manager) lub używasz rozwiązania do zarządzania urządzeniami innych niż firmy Microsoft, na tych urządzeniach musi być uruchomiony jeden z systemów operacyjnych obsługiwanych w programie [Microsoft Defender for Endpoint](../defender-endpoint/minimum-requirements.md). |
| Integracja z Microsoft Endpoint Manager  | Jeśli planujesz wboardować urządzenia przy użyciu konfiguracji zabezpieczeń programu [Microsoft Defender dla](mdb-onboard-devices.md#microsoft-defender-for-business-security-configuration) firm, muszą być spełnione następujące wymagania:<br/><br/>Wymagania wstępne muszą być spełnione w celu [zarządzania zabezpieczeniami dla programu Microsoft Defender dla punktu końcowego](/mem/intune/protect/mde-security-integration).<br/>— Usługa Azure AD musi być skonfigurowana w taki sposób, aby między urządzeniami organizacji a usługą Azure AD było tworzone zaufanie. <br/>— Program Defender dla firm musi mieć włączoną funkcję zarządzania zabezpieczeniami w Microsoft Endpoint Manager.<br/><br/>Urządzenia muszą mieć możliwość łączenia się z następującymi adresami URL:<br/>- `enterpriseregistration.windows.net` (w przypadku rejestracji w usłudze Azure AD)<br/>- `login.microsoftonline.com` (w przypadku rejestracji w usłudze Azure AD)<br/>- `*.dm.microsoft.com` (Symbol wieloznaczny (*) obsługuje punkty końcowe usługi w chmurze, które są używane do rejestrowania, zaewidencjonowania i raportowania oraz mogą zmieniać się wraz ze skalami usług). |

> [!NOTE]
> [Azure Active Directory (Azure AD) służy](/azure/active-directory/fundamentals/active-directory-whatis) do zarządzania uprawnieniami użytkowników i grupami urządzeń. Usługa Azure AD jest zawarta w subskrypcji usługi Defender dla firm. 
> - Jeśli przed rozpoczęciem okresu próbnego Microsoft 365 nie masz subskrypcji usługi Azure AD, w trakcie procesu aktywacji zostanie dla Ciebie aprowizowana usługa Azure AD. 
> - Jeśli po uruchomieniu wersji próbnej Microsoft 365 Defender dla firm masz inną subskrypcję usługi, możesz użyć istniejącej usługi Azure AD. 
> - Jeśli korzystasz z [programu Microsoft 365 Business Premium](../../business/index.yml) po uruchomieniu wersji próbnej usługi Defender dla firm, będziesz mieć możliwość zarządzania urządzeniami w programie Microsoft Intune. 

## <a name="next-steps"></a>Następne kroki

Przejdź do:

- [Krok 2. Przypisywanie ról i uprawnień w programie Microsoft Defender dla firm](mdb-roles-permissions.md) 
 