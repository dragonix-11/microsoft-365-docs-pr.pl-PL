---
title: Krok nr 1. Wdrażanie zasad ochrony aplikacji
ms.author: bcarter
author: brendacarter
f1.keywords:
- Intune App Protection policies
- APP
- mobile application management
- MAM
- set up mobile ap protection
manager: dougeby
audience: ITPro
ms.topic: article
description: Skonfiguruj ochronę aplikacji dla urządzeń przenośnych przy użyciu zasad ochrony aplikacji (APP), aby zapobiec kopiowaniu i wklejaniu określonych danych firmowych do innych aplikacji.
ms.prod: microsoft-365-enterprise
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- m365solution-managedevices
- m365solution-scenario
ms.custom: ''
keywords: ''
ms.openlocfilehash: 4535e4a05ac8408e57c767999de66c39a4bf0274
ms.sourcegitcommit: 23166424125b80b2d615643f394a3c023cba641d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/14/2022
ms.locfileid: "63015774"
---
# <a name="step-1-implement-app-protection-policies"></a>Krok nr 1. Wdrażanie zasad ochrony aplikacji

Zasady intune App Protection (APP), czasami nazywane zarządzaniem aplikacjami mobilnymi (MAM), chronią dane firmowe, nawet jeśli samo urządzenie nie jest zarządzane. Umożliwia to włączenie własnych (BYO) i osobistych urządzeń w pracy, gdzie użytkownicy mogą ponownie "zarejestrować" swoje urządzenie do zarządzania. Zasady ochrony aplikacji zapewniają, że danych firmowych w aplikacjach, które określisz, nie będzie można kopiować ani wklejać do innych aplikacji na urządzeniu.

![Procedura tworzenia zasad ochrony aplikacji](../media/devices/intune-app-steps.png#lightbox)

Na poniższej ilustracji:
- Za pomocą aplikacji Usługa Intune tworzy ścianę między danymi organizacji a danymi osobistymi. Zasady ochrony aplikacji określają, które aplikacje mogą mieć dostęp do Twoich danych.
- Jeśli użytkownik się do logowania używa poświadczeń organizacji, usługa Intune stosuje zasady w warstwie aplikacji, aby uniemożliwić kopiowanie i wklejanie danych organizacji do aplikacji osobistych oraz wymagać dostępu za pomocą numeru PIN do tych danych.
- Po utworzeniu zasad ochrony aplikacji można wymusić ochronę danych za pomocą zasad dostępu warunkowego. 

Ta konfiguracja znacznie zwiększa poziom zabezpieczeń, niemal bez wpływu na środowisko użytkownika.  Pracownicy mogą korzystać z aplikacji, takich jak Office i Microsoft Teams, które znają i lubią, a jednocześnie chronić dane zawarte w aplikacjach i urządzeniach w Organizacji.

Jeśli masz niestandardowe aplikacje biznesowe, które wymagają ochrony, obecnie możesz użyć narzędzia do zawijania aplikacji, aby włączyć aplikację dla tych aplikacji. Możesz też zintegrować ją przy użyciu zestawu SDK aplikacji Intune. Jeśli do aplikacji zastosowano zasady ochrony aplikacji, można ją zarządzać w usłudze Intune i jest rozpoznawana przez usługę Intune jako aplikacja zarządzana. Aby uzyskać więcej informacji na temat ochrony aplikacji biznesowych za pomocą usługi Intune, zobacz Przygotowanie aplikacji do zarządzania aplikacjami mobilnymi za pomocą [usługi Microsoft Intune](/mem/intune/developer/apps-prepare-mobile-application-management).

## <a name="configuring-mobile-app-protection"></a>Konfigurowanie ochrony aplikacji dla urządzeń przenośnych

Te wskazówki są ściśle skoordynowane z zalecanymi zasadami [dostępu do tożsamości i](../security/office-365-security/microsoft-365-policies-configurations.md) urządzeń bez zaufania. Po utworzeniu zasad ochrony aplikacji dla urządzeń przenośnych w usłudze Intune we współpracy ze swoim zespołem tożsamości skonfiguruj zasady dostępu warunkowego w usłudze Azure AD, które wymuszają ochronę aplikacji dla urządzeń przenośnych. 

Na poniższej ilustracji opisano dwie zasady (opisane również w tabeli poniżej ilustracji).

[![Zasady zerowego zaufania w zakresie tożsamości i dostępu do urządzeń](../media/devices/identity-device-starting-point.png#lightbox)](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/media/devices/identity-device-starting-point.png)

Aby skonfigurować te zasady, użyj zalecanych wskazówek i ustawień określonych w zasadach [zerowego zaufania i dostępu do urządzeń](../security/office-365-security/microsoft-365-policies-configurations.md). Tabela poniżej zawiera linki bezpośrednio do instrukcji dotyczących konfigurowania tych zasad w usłudze Intune i Azure AD.


|Krok  |Policies (zasady)  |Więcej informacji  |Licencjonowanie  |
|---------|---------|---------|---------|
|1   |  [Stosowanie ochrony danych zasad ochrony aplikacji (APP)](../security/office-365-security/identity-access-policies.md#apply-app-data-protection-policies)       | One Intune App Protection policy per platform (Windows, iOS/iPadOS, Android).        | Microsoft 365 E3 lub E5        |
|2     | [Wymaganie zatwierdzonych aplikacji i ochrony aplikacji ](../security/office-365-security/identity-access-policies.md#require-approved-apps-and-app-protection)       |  Wymusza ochronę aplikacji mobilnej dla telefonów i tabletów za pomocą systemu iOS, iPadOS lub Android.   |  Microsoft 365 E3 lub E5       |
| | | | |

## <a name="next-steps"></a>Następne kroki

Przejdź do [kroku 2. Zarejestruj urządzenia do zarządzania za pomocą usługi Intune](manage-devices-with-intune-enroll.md). 