---
title: Microsoft 365 integracji z konfiguracją ServiceNow — omówienie
f1.keywords:
- NOCSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_TOC
ms.custom: AdminSurgePortfolio
ROBOTS: NOINDEX, NOFOLLOW
search.appverid:
- MET150
description: Przewodnik po instalacji i konfiguracji certyfikowanej dla programu ServiceNow z zakresem.
ms.openlocfilehash: dc69f6210eda4ba04dfd0aecf9795bfcba2efe22
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63324329"
---
# <a name="microsoft-365-support-integration-with-servicenow-configuration-overview"></a>Microsoft 365 integracji z konfiguracją ServiceNow — omówienie

Następująca zawartość dotyczy aplikacji Microsoft 365 pomocy technicznej przy minimalnej wersji **1.0.7**.

**Microsoft 365 integracja pomocy** technicznej umożliwia integrację pomocy Microsoft 365, pomocy technicznej i kondycji usług ze swoimi wystąpieniami ServiceNow. Możesz zbadać znane i zgłoszone przez firmę Microsoft problemy, rozwiązać zdarzenia, wykonać zadania przy użyciu zalecanych rozwiązań firmy Microsoft i w razie potrzeby eskalować do pomocy technicznej firmy Microsoft pomaganych przez człowieka.

Aby uzyskać **Microsoft 365 pomocy technicznej** ze sklepu ServiceNow, przejdź do [sklepu ServiceNow Store](https://store.servicenow.com/sn_appstore_store.do#!/store/application/6d05c93f1b7784507ddd4227cc4bcb9f).

## <a name="key-features"></a>Najważniejsze funkcje

Oto najważniejsze funkcje, które otrzymasz w aplikacji integracji usługi Microsoft 365 w wystąpieniu ServiceNow:

- Zdarzenia dotyczące kondycji usługi: informacje o znanych zdarzeniach dotyczących kondycji usług firmy Microsoft, w tym o wpływie użytkownika, zakresie, bieżącym stanie i następnej oczekiwanej aktualizacji. Za pomocą uczenia maszynowego zdarzenia typu ServiceNow są do siebie dopasowane na podstawie pola krótkiego opisu zdarzeń kondycji usługi firmy Microsoft.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-overview-description-field-1.png" lightbox="../../media/ServiceNow-guide/servicenow-overview-description-field-1.png" alt-text="Pole opisu zdarzenia dotyczące kondycji usługi.":::

- Zalecane rozwiązania: Opisy zadań i zdarzeń są używane do polecania precyzyjnych ukierunkowanych rozwiązań i odpowiednich artykułów od firmy Microsoft obsługiwanych przez uczenie maszynowe. W razie potrzeby możesz również użyć funkcji wyszukiwania, aby znaleźć inne rozwiązania.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-overview-description-field-2.png" lightbox="../../media/ServiceNow-guide/servicenow-overview-description-field-2.png" alt-text="Pole opisu polecanych rozwiązań.":::

- Żądanie usługi firmy Microsoft: Eskaluj problemy do agentów pomocy technicznej firmy Microsoft i otrzymuj aktualizacje stanu dla Twojej sprawy.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-overview-service-request.png" lightbox="../../media/ServiceNow-guide/servicenow-overview-service-request.png" alt-text="Formularz żądania usługi.":::

## <a name="prerequisites"></a>Wymagania wstępne

### <a name="permissions-requirements"></a>Wymagania dotyczące uprawnień

Aby kontynuować ten przewodnik, upewnij się, że w trakcie całego procesu dostępne i skonfigurowane dla Twoich środowisk są następujące uprawnienia:

- Azure Active Directory usługi (AAD) może tworzyć aplikacje usługi Azure AD

- Administrator ServiceNow

- Microsoft 365 administratorem dzierżawy

### <a name="configuration-highlights"></a>Najważniejsze informacje o konfiguracji

Aby skonfigurować Microsoft 365 **pomocy technicznej**:

- Rejestruj aplikacje w Microsoft Azure Active Directory (AAD) w celu uwierzytelniania zarówno wychodzących, jak i przychodzących połączeń API.

- Utwórz jednostki ServiceNow Microsoft Azure AD aplikacją zarówno dla przychodzącego, jak i wychodzącego przepływu danych.

- Zintegruj wystąpienie ServiceNow z pomocą techniczną firmy Microsoft za pośrednictwem Microsoft 365 administracyjnego.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-overview-integration-diagram.png" alt-text="Diagram integracji z serwisem ServiceNow.":::

### <a name="application-dependencies-in-your-servicenow-environments"></a>Zależności aplikacji w środowiskach ServiceNow

Wymagane uprawnienia:

- oauthentity\_

- oauthentityprofile\_\_

Po zainstalowaniu Microsoft 365 Integracja pomocy technicznej tworzy się dwie dostępy między zakresami aplikacji. Jeśli nie utworzono ich pomyślnie, utwórz je ręcznie.

## <a name="setup-the-integration"></a>Konfigurowanie integracji

Po pobraniu aplikacji przejdź do kreatora konfiguracji systemu Microsoft 365 w środowisku SNOW, aby ukończyć proces konfiguracji.
:::image type="content" source="../../media/154124985-76e13e7d-b32e-4741-830b-bbb110d3ecbf.png" alt-text="Kreator konfiguracji śniegu":::

Aby dowiedzieć się więcej o tych krokach, zobacz następujące strony:
- Jeśli środowisko ServiceNow zezwala na uwierzytelnianie podstawowe (dostęp za pomocą poświadczeń użytkownika ServiceNow) dla przychodzących połączeń usługi sieci Web Microsoft 365, wykonaj instrukcje z tematu Konfigurowanie integracji pomocy technicznej z uwierzytelnianiem podstawowym [ServiceNow](servicenow-basic-authentication.md).
- Jeśli twoje środowisko ServiceNow NIE zezwala na uwierzytelnianie podstawowe (dostęp za pomocą poświadczeń użytkownika ServiceNow) dla przychodzących połączeń usługi sieci Web, wykonaj instrukcje z tematu Konfigurowanie integracji pomocy technicznej usługi Microsoft 365 z tokenem uwierzytelniania usługi [Azure AD](servicenow-aad-oauth-token.md).
  - Ta konfiguracja będzie wymagać dzierżawy logowania jednokrotnego, aby token uwierzytelniania AAD działał prawidłowo.

Aby poznać poszczególne funkcje, zobacz [Microsoft 365 integracji z usługą pomocy technicznej](https://store.servicenow.com/sn_appstore_store.do#!/store/application/6d05c93f1b7784507ddd4227cc4bcb9f).

> [!NOTE]
> Ta aplikacja nie jest obsługiwana przez przepisy i ograniczenia.
