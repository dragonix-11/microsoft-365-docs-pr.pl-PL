---
title: Krok nr 1. Implementowanie zasad ochrony aplikacji
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
description: Skonfiguruj ochronę aplikacji mobilnych przy użyciu zasad ochrony aplikacji (APP), aby zapobiec kopiowaniu i wklejaniu określonych danych firmowych do innych aplikacji.
ms.prod: microsoft-365-enterprise
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- m365solution-managedevices
- m365solution-scenario
ms.custom: ''
keywords: ''
ms.openlocfilehash: e421a62d3b1fa60df7a64a5b9a94e6e46b0a139f
ms.sourcegitcommit: a06bb81fbd727a790a8fe6a3746b8a3cf62a6b24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2022
ms.locfileid: "64651516"
---
# <a name="step-1-implement-app-protection-policies"></a>Krok nr 1. Implementowanie zasad ochrony aplikacji

Intune zasad ochrony aplikacji (APP), czasami nazywanych zarządzaniem aplikacjami mobilnymi (MAM), chronić dane firmowe, nawet jeśli samo urządzenie nie jest zarządzane. Dzięki temu możesz włączyć własne urządzenia byo i osobiste w pracy, na których użytkownicy mogą niechętnie "rejestrować" swoje urządzenie do zarządzania. Zasady ochrony aplikacji zapewniają, że dane firmowe w określonych aplikacjach nie mogą być kopiowane i wklejane do innych aplikacji na urządzeniu.

![Kroki tworzenia zasad ochrony aplikacji](../media/devices/intune-app-steps.png#lightbox)

Na tej ilustracji:
- Za pomocą aplikacji Intune tworzy ścianę między danymi organizacji a danymi osobowymi. Zasady ochrony aplikacji określają, które aplikacje mogą uzyskiwać dostęp do danych.
- Jeśli użytkownik loguje się przy użyciu poświadczeń organizacji, Intune stosuje zasady w warstwie aplikacji, aby uniemożliwić kopiowanie i wklejanie danych organizacji do aplikacji osobistych oraz wymagać dostępu do tych danych przy użyciu numeru PIN.
- Po utworzeniu zasad ochrony aplikacji wymuszasz ochronę danych przy użyciu zasad dostępu warunkowego. 

Ta konfiguracja znacznie zwiększa stan zabezpieczeń niemal bez wpływu na środowisko użytkownika.  Pracownicy mogą korzystać z aplikacji, takich jak Office i Microsoft Teams, które znają i kochają, a jednocześnie twoja organizacja może chronić dane zawarte w aplikacjach i urządzeniach.

Jeśli masz niestandardowe aplikacje biznesowe wymagające ochrony, obecnie możesz użyć narzędzia opakowującego aplikacje, aby włączyć aplikację z tymi aplikacjami. Możesz też zintegrować się przy użyciu zestawu Intune App SDK. Gdy aplikacja ma zastosowane zasady ochrony aplikacji, może być zarządzana przez Intune i jest rozpoznawana przez Intune jako aplikacja zarządzana. Aby uzyskać więcej informacji na temat ochrony aplikacji biznesowych przy użyciu Intune, zobacz [Przygotowywanie aplikacji do zarządzania aplikacjami mobilnymi za pomocą Microsoft Intune](/mem/intune/developer/apps-prepare-mobile-application-management).

## <a name="configuring-mobile-app-protection"></a>Konfigurowanie ochrony aplikacji mobilnych

Te wskazówki są ściśle skoordynowane z zalecanymi [zasadami Zero Trust tożsamości i dostępu do urządzeń](../security/office-365-security/microsoft-365-policies-configurations.md). Po utworzeniu zasad usługi Mobile Ochrona aplikacji w Intune skontaktuj się z zespołem ds. tożsamości, aby skonfigurować zasady dostępu warunkowego w usłudze Azure AD, które wymuszają ochronę aplikacji mobilnych. 

Na tej ilustracji przedstawiono dwie zasady (opisane również w tabeli poniżej ilustracji).

[![Zero Trust zasad dostępu do tożsamości i urządzeń](../media/devices/identity-device-starting-point.png#lightbox)](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/media/devices/identity-device-starting-point.png)

Aby skonfigurować te zasady, skorzystaj z zalecanych wskazówek i ustawień określonych w [zasadach Zero Trust tożsamości i dostępu do urządzeń](../security/office-365-security/microsoft-365-policies-configurations.md). Poniższa tabela zawiera linki bezpośrednio do instrukcji dotyczących konfigurowania tych zasad w usługach Intune i Azure AD.


|Krok  |Policies (zasady)  |Więcej informacji  |Licencjonowanie  |
|---------|---------|---------|---------|
|1   |  [Stosowanie ochrony danych zasad ochrony aplikacji (APP)](../security/office-365-security/identity-access-policies.md#apply-app-data-protection-policies)       | Jedna Intune zasad ochrony aplikacji na platformę (Windows, iOS/iPadOS, Android).        | Microsoft 365 E3 lub E5        |
|2     | [Wymagaj zatwierdzonych aplikacji i ochrony aplikacji ](../security/office-365-security/identity-access-policies.md#require-approved-apps-and-app-protection)       |  Wymusza ochronę aplikacji mobilnych dla telefonów i tabletów przy użyciu systemów iOS, iPadOS lub Android.   |  Microsoft 365 E3 lub E5       |
| | | | |

## <a name="next-steps"></a>Następne kroki

Przejdź do [kroku 2. Rejestrowanie urządzeń do Intune](manage-devices-with-intune-enroll.md). 