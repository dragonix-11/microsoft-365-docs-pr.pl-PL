---
title: Krok nr 4. Wymagaj zgodnych urządzeń o dobrej kondycji i w usłudze Intune
ms.author: bcarter
author: brendacarter
f1.keywords:
- Conditional access policy
- Microsoft Intune
- Intune device management
manager: dougeby
audience: ITPro
description: Utwórz zasady dostępu warunkowego w usłudze Azure AD, aby wymagać zgodnych urządzeń, co zapewnia bezpieczeństwo danych firmowych, gdy użytkownicy pracują z dowolnego urządzenia w dowolnej lokalizacji.
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: high
ms.collection:
- Conditional access policy
- Microsoft Intune
- M365-security-compliance
- m365solution-managedevices
- m365solution-scenario
ms.custom: ''
ms.openlocfilehash: 8a953c76a3461b0f6dbf1b3663d5cef41f038371
ms.sourcegitcommit: 23166424125b80b2d615643f394a3c023cba641d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/14/2022
ms.locfileid: "63015771"
---
# <a name="step-4-require-healthy-and-compliant-devices-with-intune"></a>Krok nr 4. Wymagaj zgodnych urządzeń o dobrej kondycji i w usłudze Intune

Dostęp warunkowy zapewnia dodatkową weryfikację stanu urządzenia przed zezwoleniem na dostęp do usługi. Dostęp warunkowy nie działa, chyba że użytkownik określi warunki. W [kroku 3. Skonfiguruj zasady zgodności,](manage-devices-with-intune-compliance-policies.md) zdefiniowane zasady zgodności określające minimalne wymagania, które urządzenie musi spełnić, aby uzyskać dostęp do środowiska. W tym artykule utworzysz odpowiadające im zasady dostępu warunkowego w usłudze Azure AD, aby wymagać zgodnych urządzeń. Pomaga to zabezpieczyć firmowe dane, zapewniając użytkownikom możliwość pracy z dowolnego urządzenia i z dowolnej lokalizacji.

Po skonfigurowaniu zasad zgodności urządzeń i przypisaniu ich do grup użytkowników usługa Intune informuje usługę Azure AD, czy urządzenie jest zgodne, czy nie. Aby użyć tego statusu jako warunku dostępu, musisz współpracować z administratorem usługi Azure AD w celu utworzenia reguły dostępu warunkowego wymagającej zgodności komputerów i urządzeń przenośnych.


![Procedura zarządzania urządzeniami](../media/devices/intune-mdm-step-3.png#lightbox)

Ta reguła jest uwzględniana w zalecanym zestawie reguł dostępu do urządzeń i tożsamości bez zaufania. Zobacz [Wymaganie zgodności komputerów i urządzeń przenośnych](../security/office-365-security/identity-access-policies.md#require-compliant-pcs-and-mobile-devices), jak pokazano poniżej.


[![Zasady zerowego zaufania w zakresie tożsamości i dostępu do urządzeń](../media/devices/identity-device-require-compliance.png#lightbox)](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/media/devices/identity-device-require-compliance.png)



Pamiętaj, aby:
- Koordynowanie grup użytkowników przypisanych do zasad zgodności z grupami użytkowników przypisanymi do zasad dostępu warunkowego.
- Przetestuj zasady dostępu warunkowego przy użyciu funkcji Warunkowe i Tryb inspekcji przed pełnym przypisaniem zasad dostępu warunkowego. Pomaga to w zrozumieniu wyników zasad.
- Ustaw okres prolongaty z zachowaniem poufności danych i/lub aplikacji, do których uzyskujesz dostęp. 
- Upewnij się, że Twoje zasady zgodności z przepisami nie zakłócają żadnych wymogów prawnych ani innych wymogów dotyczących zgodności z przepisami. 
- Zrozumienie interwałów sprawdzania zgodności przez urządzenie.
- Unikaj konfliktów między zasadami zgodności a profilami konfiguracji. Zrozum wyniki, jeśli chcesz.

Aby rozwiązać problemy z profilami urządzeń w usłudze Intune, w tym z konfliktami między zasadami, zobacz Typowe pytania i odpowiedzi dotyczące zasad urządzeń i [profilów w Microsoft Intune](/mem/intune/configuration/device-profile-troubleshoot).

Uwaga: Jeśli chcesz rozpocząć od wymagania zgodności komputerów, ale nie urządzeń przenośnych, zobacz [Wymaganie zgodności komputerów (ale nie telefonów i tabletów)](../security/office-365-security/identity-access-policies.md) 

## <a name="next-steps"></a>Następne kroki

Przejdź do kroku [5. Wdrażanie profilów urządzeń w Microsoft Intune](manage-devices-with-intune-configuration-profiles.md)
