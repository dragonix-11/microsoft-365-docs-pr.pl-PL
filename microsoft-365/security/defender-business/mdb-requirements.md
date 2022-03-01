---
title: Wymagania dotyczące programu Microsoft Defender dla firm (wersja preview)
description: Wymagania dotyczące licencji, sprzętu i oprogramowania programu Microsoft Defender dla firm (wersja Preview)
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 02/14/2022
ms.prod: m365-security
ms.technology: mdb
localization_priority: Normal
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: 59de83ae127a20fd7d7c529a626544cc0a9d2434
ms.sourcegitcommit: 007822d16e332522546e948f5c216327254a4d49
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/17/2022
ms.locfileid: "63014818"
---
# <a name="microsoft-defender-for-business-preview-requirements"></a>Wymagania dotyczące programu Microsoft Defender dla firm (wersja Preview)

> [!IMPORTANT]
> Usługa Microsoft Defender dla firm jest teraz w wersji Preview i będzie stopniowo wprowadzana u klientów i partnerów IT, którzy zarejestrują się tutaj [, aby](https://aka.ms/mdb-preview) poprosić o to. W najbliższych tygodniach nawiązemy wstępną ofertę klientów i partnerów oraz rozszerzymy jej wersja zapoznawczą, aby rozszerzyć jej dostępność do ogólnej dostępności. Pamiętaj, że wersja Preview zostanie uruchamiana z [początkowym zestawem scenariuszy](mdb-tutorials.md#try-these-preview-scenarios), a funkcje będą regularnie dodajemy.
> 
> Niektóre informacje w tym artykule dotyczą wstępnie dzierżawionych produktów/usług, które mogą zostać znacząco zmodyfikowane przed ich komercyjną premierą. Firma Microsoft nie udziela żadnych gwarancji, jawnych ani domniemanych, dotyczących podanych tutaj informacji. 

W tym artykule opisano wymagania dotyczące programu Microsoft Defender dla firm (wersja Preview).

## <a name="what-to-do"></a>Co należy zrobić

1. [Przejrzyj wymagania i upewnij się, że są spełnione](#review-the-requirements).

2. [Przejdź do następnych kroków](#next-steps).

## <a name="review-the-requirements"></a>Przejrzyj wymagania

W poniższej tabeli wymieniono podstawowe wymagania dotyczące konfigurowania i używania programu Microsoft Defender dla firm (wersja Preview). <br/><br/>

| Wymaganie | Opis |
|:---|:---|
| Subskrypcja | Microsoft Defender for Business (obecnie w wersji Preview!). Zobacz [Jak uzyskać program Microsoft Defender dla firm (wersja preview)](get-defender-business.md).<br/><br/>**Nie musisz mieć innej subskrypcji usługi Microsoft 365, aby wypróbować usługę Microsoft Defender dla firm** (wersja Preview).<br/><br/>Jeśli masz wiele subskrypcji, najwyższa subskrypcja ma pierwszeństwo. Jeśli na przykład masz program Microsoft Defender for Endpoint Plan 2 (zakupioną lub próbną subskrypcję) i otrzymasz program Microsoft Defender dla firm (wersja Preview), program Defender dla punktu końcowego (plan 2) ma pierwszeństwo. W takim przypadku nie zobaczysz programu Defender dla firm (wersja Preview).  |
| Datacenter | Jedna z następujących lokalizacji centrów danych: <br/>- Unia Europejska <br/>— Zjednoczone Królestwo <br/>- Stany Zjednoczone |
| Konta użytkowników | Konta użytkowników są tworzone w centrum administracyjne platformy Microsoft 365 ([https://admin.microsoft.com](https://admin.microsoft.com))<br/><br/>Licencje programu Microsoft Defender dla firm (w wersji Preview) są przypisywane w centrum administracyjne platformy Microsoft 365<br/><br/>Aby uzyskać pomoc na temat tego zadania, zobacz [Dodawanie użytkowników i przypisywanie licencji](../../admin/add-users/add-users.md). |
| Uprawnienia  | Aby zarejestrować się w programie Microsoft Defender dla firm (w wersji Preview), musisz być administratorem globalnym.<br/><br/>Aby uzyskać dostęp do portalu Microsoft 365 Defender, użytkownicy muszą mieć przypisaną jedną z następujących ról [w usłudze Azure AD](mdb-roles-permissions.md): <br/>- Czytnik zabezpieczeń<br/>- Administrator zabezpieczeń<br/>— Administrator globalny<br/><br/>Aby dowiedzieć się więcej, zobacz [Role i uprawnienia w programie Microsoft Defender dla firm (wersja Preview).](mdb-roles-permissions.md) |
| Wymagania dotyczące przeglądarki | Microsoft Edge lub Google Chrome |
| System operacyjny | Aby można było zarządzać urządzeniami w programie Microsoft Defender dla firm (wersja Preview), na tych urządzeniach musi być uruchomiony jeden z następujących systemów operacyjnych: <br/>— Windows 10 Business lub nowszy <br/>— Windows 10 Professional lub nowszy <br/>— Windows 10 Enterprise lub nowszy <br/><br/>Upewnij się, [że zainstalowano kb5006738](https://support.microsoft.com/topic/october-26-2021-kb5006738-os-builds-19041-1320-19042-1320-and-19043-1320-preview-ccbce6bf-ae00-4e66-9789-ce8e7ea35541) . <br/><br/>Jeśli zarządzasz urządzeniami w programie Microsoft Intune (lub Microsoft Endpoint Manager) lub używasz rozwiązania do zarządzania urządzeniami innych niż firmy Microsoft, na tych urządzeniach musi być uruchomiony jeden z systemów operacyjnych obsługiwanych w programie [Microsoft Defender for Endpoint](../defender-endpoint/minimum-requirements.md). |
| Integracja z Microsoft Endpoint Manager  |  **Podczas wyświetlania podglądu można korzystać z urządzeń przy użyciu skryptu lokalnego, który nie wymaga integracji z programem Microsoft Endpoint Manager**. Jeśli zamierzasz ręcznie włączyć urządzenia do usługi Defender dla firm (wersja Preview) za pomocą pakietów do pobrania dla systemów Microsoft Endpoint Manager, zasady grupy, System Center Configuration Manager lub Mobile Device Management, muszą być spełnione następujące wymagania:<br/><br/>Wymagania wstępne muszą być spełnione w celu [zarządzania zabezpieczeniami dla programu Microsoft Defender dla punktu końcowego](/mem/intune/protect/mde-security-integration).<br/>— Usługa Azure AD musi być skonfigurowana w taki sposób, aby między urządzeniami organizacji a usługą Azure AD było tworzone zaufanie. <br/>— Program Defender dla firm (w wersji Preview) musi mieć włączoną funkcję zarządzania zabezpieczeniami w Microsoft Endpoint Manager.<br/><br/>Urządzenia muszą mieć możliwość łączenia się z następującymi adresami URL:<br/>- `enterpriseregistration.windows.net` (w przypadku rejestracji w usłudze Azure AD)<br/>- `login.microsoftonline.com` (w przypadku rejestracji w usłudze Azure AD)<br/>- `*.dm.microsoft.com` (Symbol wieloznaczny (*) obsługuje punkty końcowe usługi w chmurze, które są używane do rejestrowania, zaewidencjonowania i raportowania oraz mogą zmieniać się wraz ze skalami usług). |

> [!NOTE]
> [Azure Active Directory (Azure AD) służy](/azure/active-directory/fundamentals/active-directory-whatis) do zarządzania uprawnieniami użytkowników i grupami urządzeń. Usługa Azure AD jest zawarta w subskrypcji usługi Defender dla firm (wersja Preview). 
> - Jeśli przed rozpoczęciem okresu próbnego Microsoft 365 nie masz subskrypcji usługi Azure AD, w trakcie procesu aktywacji zostanie dla Ciebie aprowizowana usługa Azure AD. 
> - Jeśli po uruchomieniu wersji próbnej usługi Defender Microsoft 365 (w wersji Preview) masz inną subskrypcję usługi, możesz użyć istniejącej usługi Azure AD. 
> - Jeśli używasz programu [Microsoft 365 Business Premium](../../business/index.yml) po uruchomieniu wersji próbnej programu Defender dla firm (wersja preview), będziesz mieć możliwość zarządzania urządzeniami w Microsoft Intune. 

## <a name="next-steps"></a>Następne kroki

Przejdź do:

- [Krok 2. Przypisywanie ról i uprawnień w programie Microsoft Defender dla firm (wersja Preview)](mdb-roles-permissions.md) 
 
