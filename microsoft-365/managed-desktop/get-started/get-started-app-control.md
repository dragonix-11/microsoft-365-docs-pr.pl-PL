---
title: Wprowadzenie do sterowania aplikacją
description: W tym artykule opisano, jak włączyć kontrolkę aplikacji
keywords: Microsoft Managed Desktop, Microsoft 365, usługa, dokumentacja
ms.service: m365-md
author: tiaraquan
ms.author: tiaraquan
manager: dougeby
audience: ITpro
ms.topic: article
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.openlocfilehash: a671bf36e957ffc416f51ec531aaeed6ddfa41b3
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63315403"
---
# <a name="get-started-with-app-control"></a>Wprowadzenie do sterowania aplikacją

Przed włączeniem kontroli aplikacji w środowisku należy zapoznać się ze swoimi potrzebami i zrozumieniem tego, [Microsoft Managed Desktop](../service-description/app-control.md) sposób wdrażania tej funkcji oraz ról i obowiązków.

Microsoft Managed Desktop upraszcza sterowanie aplikacją przez zadbanie o bardziej wymagające aspekty uzyskiwania bezpiecznych zasad podstawowych.

Administratorzy IT muszą przetestować Aplikacje w pierścieniu testowania i przejrzeć dzienniki pod celu sprawdzenia, czy nie ma ostrzeżeń i błędów. Jeśli aplikacja wymaga zwolnienia, możesz złożyć wniosek lub Microsoft Managed Desktop, w zależności od tego, kto najpierw je wykryje.

## <a name="initial-deployment-of-apps"></a>Wdrożenie początkowe aplikacji

Podczas pierwszego wdrażania aplikacji Microsoft Managed Desktop ocenę ich bieżącego zachowania. Dokładne instrukcje dotyczące włączania kontroli aplikacji zależą od tego, czy urządzenia zostały już wdrożone w środowisku.

### <a name="devices-not-yet-in-use"></a>Urządzenia nie są jeszcze używani

Jeśli nie masz jeszcze żadnych urządzeń, które są w użyciu, otwórz bilet pomocy technicznej za pomocą usługi Microsoft Managed Desktop Operations, aby zażądać włączyć kontrolkę aplikacji. Operacje będą stopniowo wdrażać zasady w grupach wdrożeń zgodnie z tym harmonogramem:

| Grupa Wdrażania | Typ zasad | Chronometraż |
| ------ | ------ | ------ |
| Test |  Inspekcja |  Dzień 0 |
| Pierwszy | Wymuszone | Dzień 1 |
| Szybkie | Wymuszone |  Dzień 2 |
| Broad | Wymuszone |  Dzień 3 |

Zawsze możesz otworzyć kolejne żądanie pomocy technicznej w celu wstrzymania lub wycofywania części tego wdrożenia w dowolnym momencie wdrożenia.

### <a name="devices-already-in-use"></a>Urządzenia, które są już używani

Jeśli masz już co najmniej jedno Microsoft Managed Desktop w użyciu, wykonaj następujące czynności:

1. Otwórz bilet usługi z usługą Microsoft Managed Desktop z żądaniem przez nas włączyliśmy kontrolę aplikacji. Operacje wdrażają [zasady inspekcji](../service-description/app-control.md#audit-policy) na wszystkich urządzeniach.
2. [Przetestuj aplikacje](../working-with-managed-desktop/work-with-app-control.md#add-a-new-app) , aby sprawdzić, czy którekolwiek z tych aplikacji zostałoby zablokowane. Jeśli aplikacja zostałaby zablokowana, otwórz żądanie [osoby podpiszcej](../working-with-managed-desktop/work-with-app-control.md#add-or-remove-a-trusted-signer) się.
3. Po ukończeniu testowania (bez względu na wyniki) powiadom operacje, notując wszystkie oczekujące żądania osób podpisujące. Operacje będą stopniowo wdrażać zasady w grupach wdrożeń zgodnie z tym harmonogramem:

| Grupa Wdrażania | Typ zasad | Chronometraż |
| ------ | ------ | ------ |
| Test     | Inspekcja |  Dzień 0 |
| Pierwszy     | Wymuszone | Dzień 1 |
| Szybkie     | Wymuszone |  Wstrzymane, wstrzymanie na żądanie |
| Broad     | Wymuszone |  Wstrzymane, wstrzymanie na żądanie |

Zawsze możesz otworzyć kolejne żądanie pomocy technicznej w celu wstrzymania lub wycofywania części tego wdrożenia w dowolnym momencie wdrożenia.

## <a name="steps-to-get-started-with-microsoft-managed-desktop"></a>Procedura rozpoczynania pracy z Microsoft Managed Desktop

1. Portalu [administracyjnego programu](access-admin-portal.md) Access.
1. [Dodaj i zweryfikuj kontakty administratora w portalu administracyjnym](add-admin-contacts.md).
1. [Dostosuj ustawienia po rejestracji](conditional-access.md).
1. Wdrażanie i [przypisywanie Intune — Portal firmy](company-portal.md).
1. [Przypisywanie licencji](assign-licenses.md).
1. [Wdychuj aplikacje](deploy-apps.md).
1. [Przygotowywanie urządzeń](prepare-devices.md).
1. Skonfiguruj środowisko [pierwszego uruchomienia za pomocą rozwiązania Autopilot i strony stanu rejestracji](esp-first-run.md).
1. [Włączanie funkcji pomocy technicznej dla użytkowników](enable-support.md).
1. [Przygotuj użytkowników do korzystania z urządzeń](get-started-devices.md).
1. Wprowadzenie do sterowania aplikacją (ten artykuł).
