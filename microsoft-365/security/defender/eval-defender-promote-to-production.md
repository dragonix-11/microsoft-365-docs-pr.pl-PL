---
title: Krok 7. Podniesienie środowiska Microsoft 365 Defender oceny do produkcji
description: W tym artykule opanuje promowanie środowiska na żywo aplikacji MDI, MDO, MDE i Defender w chmurze w środowisku na Microsoft 365 Defender lub M365D.
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: bcarter
author: brendacarter
f1.keywords:
- NOCSH
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-scenario
- m365solution-evalutatemtp
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 47f36d965c9b2b6ef5f106c590e47fe0251163d8
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63323979"
---
# <a name="step-7-promote-your-microsoft-365-defender-evaluation-environment-to-production"></a>Krok 7. Podniesienie środowiska oceny Microsoft 365 Defender do produkcji

**Dotyczy:**
- Microsoft 365 Defender

Aby promować środowisko Microsoft 365 Defender oceny do produkcji, najpierw kup potrzebną licencję. Postępuj zgodnie z instrukcjami [w tece Tworzenie środowiska eval](eval-create-eval-environment.md) i zakup Office 365 E5 (zamiast wybierania opcji Rozpocznij bezpłatną wersję próbną).

Następnie wykonaj dowolną dodatkową konfigurację i rozwiń grupy pilotażowe, aż do momentu ukończenia pełnej produkcji.

## <a name="microsoft-defender-for-identity"></a>Microsoft Defender for Identity

Program Defender dla tożsamości nie wymaga żadnej dodatkowej konfiguracji. Po prostu upewnij się, że zakupiono wymagane licencje i zainstalowaliśmy czujnik we wszystkich kontrolerach domeny w usłudze Active Directory i serwerach usług Federatorów Active Directory (AD FS).

## <a name="microsoft-defender-for-office-365"></a>Usługa Microsoft Defender dla Office 365

Po pomyślnym dokonaniu oceny lub pilotażu urządzenia MDO można go promować do całego środowiska produkcyjnego.

1. Zakup i inicjowanie obsługi administracyjnej niezbędnych licencji oraz przypisywanie ich do użytkowników produkcyjnych.
2. Ponownie uruchom zalecane konfiguracje zasad planu bazowego (standardowe lub ścisłe) względem produkcyjnej domeny poczty e-mail lub określonych grup użytkowników.
3. Opcjonalnie możesz tworzyć i konfigurować niestandardowe zasady MDO w stosunku do produkcyjnej domeny poczty e-mail lub grup użytkowników.  Pamiętaj jednak, że wszelkie przypisane zasady planu bazowego zawsze będą miały pierwszeństwo przed zasadami niestandardowymi.
4. Zaktualizuj publiczny rekord MX dla produkcyjnej domeny poczty e-mail, aby rozpoznać bezpośrednio do usługi EOP.
5. Zlikwiduj bramy SMTP innych firm i wyłącz lub usuń wszelkie łączniki EXO skojarzone z tym przekazywaniem.

## <a name="microsoft-defender-for-endpoint"></a>Ochrona punktu końcowego w usłudze Microsoft Defender

Aby promować środowisko oceny punktu końcowego programu Microsoft Defender z programu pilotażowego do środowiska produkcyjnego, po prostu wdowaj więcej punktów końcowych do usługi przy użyciu dowolnych z [obsługiwanych narzędzi i metod](../defender-endpoint/onboard-configure.md).

Skorzystaj z poniższych ogólnych wytycznych, aby wdowyszeć więcej urządzeń do programu Microsoft Defender for Endpoint.

1. Upewnij się, że urządzenie spełnia [minimalne wymagania](../defender-endpoint/minimum-requirements.md).
2. W zależności od urządzenia postępuj zgodnie z instrukcjami konfiguracji w sekcji dotyczącej dołączania do portalu usługi Defender for Endpoint.
3. Użyj odpowiedniego narzędzia do zarządzania i metody wdrażania dla swoich urządzeń.
4. Uruchom test wykrywania, aby sprawdzić, czy urządzenia są prawidłowo zainstalowane i że zgłaszają się do usługi.

## <a name="microsoft-defender-for-cloud-apps"></a>Usługa Microsoft Defender dla aplikacji w chmurze

Program Microsoft Defender dla aplikacji w chmurze nie wymaga żadnej dodatkowej konfiguracji. Po prostu upewnij się, że masz kupione niezbędne licencje. Jeśli zawężyłeś wdrożenie do określonych grup użytkowników, zwiększ zakres tych grup, aż osiągniesz skalę produkcyjną.
