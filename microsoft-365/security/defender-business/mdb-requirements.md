---
title: Wymagania dotyczące Microsoft Defender dla Firm
description: Microsoft Defender dla Firm licencji, sprzętu i oprogramowania
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 04/01/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: 9fd082160640c239424ec75ff58c695a0175d630
ms.sourcegitcommit: adea59259a5900cad5de29ddf46d1ca9e9e1c82f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/04/2022
ms.locfileid: "64634938"
---
# <a name="microsoft-defender-for-business-requirements"></a>Microsoft Defender dla Firm wymagań

> [!IMPORTANT]
> Microsoft Defender dla Firm jest wprowadzana u [klientów Microsoft 365 Business Premium](../../business-premium/index.md) począwszy od 1 marca 2022 r. Autonomiczna subskrypcja usługi Defender dla firm jest w wersji Preview i będzie stopniowo wprowadzana u klientów i partnerów IT, [](https://aka.ms/mdb-preview) którzy zarejestrują się tutaj, aby poprosić o to. Wersja Preview zawiera [początkowy zestaw scenariuszy](mdb-tutorials.md#try-these-preview-scenarios), a my będziemy regularnie dodawać funkcje.
> 
> Niektóre informacje w tym artykule dotyczą wstępnie dzierżawionych produktów/usług, które mogą zostać znacząco zmodyfikowane przed ich komercyjną premierą. Firma Microsoft nie udziela żadnych gwarancji, jawnych ani domniemanych, dotyczących podanych tutaj informacji. 

W tym artykule opisano wymagania dotyczące Microsoft Defender dla Firm.

## <a name="what-to-do"></a>Co należy zrobić

1. [Przejrzyj wymagania i upewnij się, że są spełnione](#review-the-requirements).

2. [Przejdź do następnych kroków](#next-steps).

>
> **Masz minutę?**
> Prosimy o <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">ankietę na temat Microsoft Defender dla Firm</a>. Chcemy ją usłyszeć!
>

## <a name="review-the-requirements"></a>Przejrzyj wymagania

W poniższej tabeli wymieniono podstawowe wymagania dotyczące konfigurowania i używania tych Microsoft Defender dla Firm. <br/><br/>

| Wymaganie | Opis |
|:---|:---|
| Subskrypcja | Microsoft 365 Business Premium <br/>--- lub ---<br/>Microsoft Defender dla Firm (autonomiczna, obecnie w wersji Preview). <br/><br/> Zobacz [Jak uzyskać Microsoft Defender dla Firm](get-defender-business.md).<br/><br/>Zwróć uwagę, że jeśli masz wiele subskrypcji, najwyższa subskrypcja ma pierwszeństwo. Jeśli na przykład masz plan 2 Ochrona punktu końcowego w usłudze Microsoft Defender (kupioną lub próbną subskrypcję) i masz Microsoft Defender dla Firm, pierwszeństwo ma program Defender dla planu 2 punktów końcowych. W takim przypadku nie zobaczysz usługi Defender dla firm.  |
| Datacenter | Jedna z następujących lokalizacji centrów danych: <br/>- Unia Europejska <br/>— Zjednoczone Królestwo <br/>— Stany Zjednoczone |
| Konta użytkowników | Konta użytkowników są tworzone w Centrum administracyjne platformy Microsoft 365 ([https://admin.microsoft.com](https://admin.microsoft.com))<br/><br/>Microsoft Defender dla Firm licencje są przypisywane w Centrum administracyjne platformy Microsoft 365<br/><br/>Aby uzyskać pomoc na temat tego zadania, zobacz [Dodawanie użytkowników i przypisywanie licencji](../../admin/add-users/add-users.md). |
| Uprawnienia  | Aby zarejestrować się w Microsoft Defender dla Firm, musisz być administratorem globalnym.<br/><br/>Aby uzyskać dostęp do portalu Microsoft 365 Defender, użytkownicy muszą mieć przypisaną jedną z następujących ról [w usłudze Azure AD](mdb-roles-permissions.md): <br/>- Czytnik zabezpieczeń<br/>- Administrator zabezpieczeń<br/>— Administrator globalny<br/><br/>Aby dowiedzieć się więcej, zobacz [Role i uprawnienia w aplikacji Microsoft Defender dla Firm](mdb-roles-permissions.md). |
| Wymagania dotyczące przeglądarki | Microsoft Edge lub Google Chrome |
| System operacyjny | Aby zarządzać urządzeniami Microsoft Defender dla Firm urządzeniach musi być uruchomiony jeden z następujących systemów operacyjnych: <br/>— Windows 10 Business lub nowszy <br/>— Windows 10 Professional lub nowszy <br/>— Windows 10 Enterprise lub nowszy <br/><br/>Upewnij się, [że zainstalowano kb5006738](https://support.microsoft.com/topic/october-26-2021-kb5006738-os-builds-19041-1320-19042-1320-and-19043-1320-preview-ccbce6bf-ae00-4e66-9789-ce8e7ea35541) . <br/><br/>Jeśli zarządzasz już urządzeniami w programie Microsoft Intune (lub Microsoft Endpoint Manager), możesz je dodać do usługi Defender dla firm. |

> [!NOTE]
> [Azure Active Directory (Azure AD) służy](/azure/active-directory/fundamentals/active-directory-whatis) do zarządzania uprawnieniami użytkowników i grupami urządzeń. Usługa Azure AD jest zawarta w subskrypcji usługi Defender dla firm. 
> - Jeśli przed rozpoczęciem okresu próbnego Microsoft 365 nie masz subskrypcji usługi Azure AD, w trakcie procesu aktywacji zostanie dla Ciebie aprowizowana usługa Azure AD. 
> - Jeśli po uruchomieniu wersji próbnej Microsoft 365 Defender dla firm masz inną subskrypcję usługi, możesz użyć istniejącej usługi Azure AD. 
> - Jeśli korzystasz z [programu Microsoft 365 Business Premium](../../business/index.yml) po uruchomieniu wersji próbnej usługi Defender dla firm, będziesz mieć możliwość zarządzania urządzeniami w programie Microsoft Intune. 

## <a name="next-steps"></a>Następne kroki

Przejdź do:

- [Krok 2. Przypisywanie ról i uprawnień w aplikacji Microsoft Defender dla Firm](mdb-roles-permissions.md) 
 