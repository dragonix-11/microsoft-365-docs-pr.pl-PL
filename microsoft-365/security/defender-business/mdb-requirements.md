---
title: Wymagania dotyczące Microsoft Defender dla Firm
description: Microsoft Defender dla Firm wymagania dotyczące licencji, sprzętu i oprogramowania
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
ms.openlocfilehash: dd30af8003e6c5bc6a4348efe16626d2d45317f1
ms.sourcegitcommit: dd5fc139affb4cba4089cbdb2c478968b680699a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2022
ms.locfileid: "64747078"
---
# <a name="microsoft-defender-for-business-requirements"></a>wymagania Microsoft Defender dla Firm

> [!IMPORTANT]
> Microsoft Defender dla Firm jest wdrażana dla [klientów Microsoft 365 Business Premium](../../business-premium/index.md) od 1 marca 2022 r. Usługa Defender dla Firm jako subskrypcja autonomiczna jest dostępna w wersji zapoznawczej i będzie stopniowo wdrażana dla klientów i partnerów IT, którzy [zarejestrują się tutaj](https://aka.ms/mdb-preview) , aby zażądać tej subskrypcji. Wersja zapoznawcza zawiera [początkowy zestaw scenariuszy](mdb-tutorials.md#try-these-preview-scenarios), a my będziemy regularnie dodawać możliwości.
> 
> Niektóre informacje zawarte w tym artykule odnoszą się do wstępnie wydanych produktów/usług, które mogą zostać znacząco zmodyfikowane przed ich komercyjnym wydaniem. Firma Microsoft nie udziela żadnych gwarancji, wyraźnych ani dorozumianych, dotyczących informacji podanych tutaj. 

W tym artykule opisano wymagania dotyczące Microsoft Defender dla Firm.

## <a name="what-to-do"></a>Co robić

1. [Przejrzyj wymagania i upewnij się, że zostały spełnione](#review-the-requirements).

2. [Przejdź do kolejnych kroków](#next-steps).

>
> **Masz minutę?**
> Weźmy <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">krótką ankietę dotyczącą Microsoft Defender dla Firm</a>. Chcielibyśmy usłyszeć od Ciebie!
>

## <a name="review-the-requirements"></a>Przejrzyj wymagania

W poniższej tabeli wymieniono podstawowe wymagania dotyczące konfigurowania i używania Microsoft Defender dla Firm. <br/><br/>

| Wymóg | Opis |
|:---|:---|
| Subskrypcji | Microsoft 365 Business Premium <br/>--- lub ---<br/>Microsoft Defender dla Firm (autonomiczna; obecnie w wersji zapoznawczej). <br/><br/> Zobacz [Jak uzyskać Microsoft Defender dla Firm](get-defender-business.md).<br/><br/>Pamiętaj, że jeśli masz wiele subskrypcji, pierwszeństwo ma najwyższa subskrypcja. Jeśli na przykład masz Ochrona punktu końcowego w usłudze Microsoft Defender plan 2 (zakupiona lub próbna subskrypcja) i uzyskasz Microsoft Defender dla Firm, pierwszeństwo ma usługa Defender for Endpoint Plan 2. W takim przypadku nie zobaczysz środowiska usługi Defender dla Firm.  |
| Datacenter | Jedna z następujących lokalizacji centrum danych: <br/>- Unia Europejska <br/>- Zjednoczone Królestwo <br/>- Stany Zjednoczone |
| Konta użytkowników | Konta użytkowników są tworzone w Centrum administracyjne platformy Microsoft 365 ([https://admin.microsoft.com](https://admin.microsoft.com))<br/><br/>Microsoft Defender dla Firm licencje są przypisywane w Centrum administracyjne platformy Microsoft 365<br/><br/>Aby uzyskać pomoc dotyczącą tego zadania, zobacz [Dodawanie użytkowników i przypisywanie licencji](../../admin/add-users/add-users.md). |
| Uprawnienia  | Aby zarejestrować się w Microsoft Defender dla Firm, musisz być administratorem globalnym.<br/><br/>Aby uzyskać dostęp do portalu Microsoft 365 Defender, użytkownicy muszą mieć przypisaną jedną z następujących [ról w usłudze Azure AD](mdb-roles-permissions.md): <br/>- Czytelnik zabezpieczeń<br/>— Administrator zabezpieczeń<br/>— Administrator globalny<br/><br/>Aby dowiedzieć się więcej, zobacz [Role i uprawnienia w Microsoft Defender dla Firm](mdb-roles-permissions.md). |
| Wymagania przeglądarki | Microsoft Edge lub Google Chrome |
| System operacyjny | Aby zarządzać urządzeniami w Microsoft Defender dla Firm, na urządzeniach musi działać jeden z następujących systemów operacyjnych: <br/>— Windows 10 Business lub nowsze <br/>— Windows 10 Professional lub nowsze <br/>— Windows 10 Enterprise lub nowsze <br/><br/>Upewnij się, że zainstalowano [program KB5006738](https://support.microsoft.com/topic/october-26-2021-kb5006738-os-builds-19041-1320-19042-1320-and-19043-1320-preview-ccbce6bf-ae00-4e66-9789-ce8e7ea35541) . <br/><br/>Jeśli już zarządzasz urządzeniami w Microsoft Intune (lub Microsoft Endpoint Manager), możesz dołączyć te urządzenia do usługi Defender for Business. |

> [!NOTE]
> [Azure Active Directory (Azure AD)](/azure/active-directory/fundamentals/active-directory-whatis) służy do zarządzania uprawnieniami użytkowników i grupami urządzeń. Usługa Azure AD jest uwzględniona w subskrypcji usługi Defender for Business. 
> - Jeśli nie masz subskrypcji Microsoft 365 przed rozpoczęciem wersji próbnej, usługa Azure AD zostanie aprowizowana podczas procesu aktywacji. 
> - Jeśli masz inną subskrypcję Microsoft 365 podczas uruchamiania wersji próbnej usługi Defender for Business, możesz użyć istniejącej usługi Azure AD. 
> - Jeśli używasz [Microsoft 365 Business Premium](../../business/index.yml) podczas uruchamiania wersji próbnej usługi Defender for Business, będziesz mieć możliwość zarządzania urządzeniami w Microsoft Intune. 

## <a name="next-steps"></a>Następne kroki

Przejdź do [kroku 2. Przypisywanie ról i uprawnień w Microsoft Defender dla Firm](mdb-roles-permissions.md).
 