---
title: Wymagania dotyczące Microsoft Defender dla Firm
description: Microsoft Defender dla Firm wymagania dotyczące licencji, sprzętu i oprogramowania
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: ab24e3898d897df6813338fd0d2131c3787f0a09
ms.sourcegitcommit: 66228a5506fdceb4cbf0d55b9de3f2943740134f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/15/2022
ms.locfileid: "66089589"
---
# <a name="microsoft-defender-for-business-requirements"></a>wymagania Microsoft Defender dla Firm

W tym artykule opisano wymagania dotyczące Microsoft Defender dla Firm.

## <a name="what-to-do"></a>Co robić

1. [Przejrzyj wymagania i upewnij się, że zostały spełnione](#review-the-requirements).
2. [Przejdź do kolejnych kroków](#next-steps).


## <a name="review-the-requirements"></a>Przejrzyj wymagania

W poniższej tabeli wymieniono podstawowe wymagania dotyczące konfigurowania i używania Microsoft Defender dla Firm.

| Wymóg | Opis |
|:---|:---|
| Subskrypcji | Microsoft 365 Business Premium lub Microsoft Defender dla Firm (autonomiczna). Zobacz [Jak uzyskać Microsoft Defender dla Firm](get-defender-business.md).<br/><br/>Pamiętaj, że jeśli masz wiele subskrypcji, pierwszeństwo ma najwyższa subskrypcja. Jeśli na przykład masz Ochrona punktu końcowego w usłudze Microsoft Defender plan 2 (zakupiona lub próbna subskrypcja) i uzyskasz Microsoft Defender dla Firm, pierwszeństwo ma usługa Defender for Endpoint Plan 2. W takim przypadku nie zobaczysz środowiska usługi Defender dla Firm.  |
| Datacenter | Jedna z następujących lokalizacji centrum danych: <br/>- Unia Europejska <br/>- Zjednoczone Królestwo <br/>- Stany Zjednoczone |
| Konta użytkowników | — Konta użytkowników są tworzone w Centrum administracyjne platformy Microsoft 365 ([https://admin.microsoft.com](https://admin.microsoft.com))<br/>— Microsoft Defender dla Firm licencje są przypisywane w Centrum administracyjne platformy Microsoft 365<br/><br/>Aby uzyskać pomoc dotyczącą tego zadania, zobacz [Dodawanie użytkowników i przypisywanie licencji](mdb-add-users.md). |
| Uprawnienia  | Aby zarejestrować się w Microsoft Defender dla Firm, musisz być Administracja globalny.<br/><br/>Aby uzyskać dostęp do portalu Microsoft 365 Defender, użytkownicy muszą mieć przypisaną jedną z następujących [ról w Azure AD](mdb-roles-permissions.md): <br/>- Czytelnik zabezpieczeń<br/>- Administracja zabezpieczeń<br/>- Globalne Administracja<br/><br/>Aby dowiedzieć się więcej, zobacz [Role i uprawnienia w Microsoft Defender dla Firm](mdb-roles-permissions.md). |
| Wymagania przeglądarki | Microsoft Edge lub Google Chrome |
| System operacyjny | Aby zarządzać urządzeniami w portalu Microsoft 365 Defender, na urządzeniach musi działać jeden z następujących systemów operacyjnych: <br/>— Windows 10 Business lub nowsze <br/>— Windows 10 Professional lub nowsze <br/>— Windows 10 Enterprise lub nowsze <br/>— macOS (obsługiwane są trzy najpopularniejsze wersje)<br/><br/>Upewnij się, że [kb5006738](https://support.microsoft.com/topic/october-26-2021-kb5006738-os-builds-19041-1320-19042-1320-and-19043-1320-preview-ccbce6bf-ae00-4e66-9789-ce8e7ea35541) jest zainstalowany na urządzeniach Windows. <br/><br/>Jeśli już zarządzasz urządzeniami w Microsoft Intune, możesz nadal korzystać z centrum administracyjnego Microsoft Endpoint Manager. |

> [!NOTE]
> [Azure Active Directory (Azure AD)](/azure/active-directory/fundamentals/active-directory-whatis) służy do zarządzania uprawnieniami użytkowników i grupami urządzeń. Azure AD jest uwzględniona w subskrypcji usługi Defender dla Firm. 
> - Jeśli nie masz subskrypcji Microsoft 365 przed rozpoczęciem okresu próbnego, Azure AD zostaną ci aprowizowane podczas procesu aktywacji. 
> - Jeśli masz inną subskrypcję Microsoft 365 podczas uruchamiania wersji próbnej usługi Defender for Business, możesz użyć istniejącej usługi Azure AD. 
> - Jeśli używasz [Microsoft 365 Business Premium](../../business/index.yml) podczas uruchamiania wersji próbnej usługi Defender for Business, będziesz mieć możliwość zarządzania urządzeniami przy użyciu Intune. 

## <a name="next-steps"></a>Następne kroki

Przejdź do [kroku 2. Przypisywanie ról i uprawnień w Microsoft Defender dla Firm](mdb-roles-permissions.md).
 
