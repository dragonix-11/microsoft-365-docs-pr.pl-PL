---
title: Wyświetlanie akcji i zarządzanie nimi w Centrum akcji
description: Wyświetlanie akcji naprawczych i zarządzanie nimi za pomocą Centrum akcji
keywords: action, center, autoair, automated, investigation, response, remediation
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: how-to
ms.custom:
- autoir
- admindeeplinkDEFENDER
ms.reviewer: evaldm, isco
ms.technology: m365d
ms.openlocfilehash: a77a64e2323cc836df9b19694deb5c32ee877fb8
ms.sourcegitcommit: 3b8e009ea1ce928505b8fc3b8926021fb91155f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/28/2022
ms.locfileid: "64500810"
---
# <a name="view-and-manage-actions-in-the-action-center"></a>Wyświetlanie akcji i zarządzanie nimi w Centrum akcji

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Dotyczy:**
- Microsoft 365 Defender

Funkcje ochrony przed zagrożeniami w Microsoft 365 Defender mogą skutkować pewnymi działaniami naprawczymi. Oto kilka przykładów:

- [Automatyczne badania mogą](m365d-autoir.md) skutkować działaniami naprawczymi, które są podejmowane automatycznie lub oczekują na zatwierdzenie.
- Działania naprawcze, takie jak blokowanie pliku, adresu URL lub procesu albo wysyłanie artefaktu do kwarantanny mogą być związane z działaniem antywirusowym, złośliwym oprogramowaniem i innymi funkcjami ochrony przed zagrożeniami.
- Zespół operacyjny bezpieczeństwa może podjąć działania naprawcze ręcznie, na przykład podczas zaawansowanego wyszukiwania [](advanced-hunting-overview.md) lub badania [alertów](investigate-alerts.md) [bądź zdarzeń](investigate-incidents.md).

> [!NOTE]
> Musisz mieć odpowiednie [uprawnienia, aby](m365d-action-center.md#required-permissions-for-action-center-tasks) zatwierdzać lub odrzucać akcje naprawcze. Aby uzyskać więcej informacji, zobacz [wymagania wstępne](m365d-configure-auto-investigation-response.md#prerequisites-for-automated-investigation-and-response-in-microsoft-365-defender).

## <a name="review-pending-actions-in-the-action-center"></a>Przeglądanie oczekujących akcji w Centrum akcji

Jak najszybciej należy zatwierdzić (lub odrzucić) oczekujące akcje, aby zautomatyzowane badania były w stanie kontynuować i wykonać w terminie. 

1. Przejdź do <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender i</a> zaloguj się. 

2. W okienku nawigacji wybierz pozycję **Centrum akcji**. 

3. W Centrum akcji **na karcie** Oczekiwanie zaznacz element na liście. Zostanie otwarte okienko wysuwu. Oto przykład.

   :::image type="content" source="../../media/air-actioncenter-itemselected.png" alt-text="Opcje zatwierdzania lub odrzucania akcji" lightbox="../../media/air-actioncenter-itemselected.png":::

4. Przejrzyj informacje w okienku wysuwu, a następnie zrób tak:
   - Wybierz **pozycję Otwórz stronę badania,** aby wyświetlić więcej szczegółów dotyczących badania.
   - Wybierz **pozycję Zatwierdź** , aby zainicjować oczekującą akcję.
   - Wybierz **pozycję Odrzuć** , aby zapobiec podejmowanej akcji oczekującej.
   - Wybierz **pozycję Przejdź wyszukiwania,** aby przejść do wyszukiwania [zaawansowanego](advanced-hunting-overview.md). 

## <a name="undo-completed-actions"></a>Cofanie ukończonych akcji

Jeśli ustalisz, że urządzenie lub plik nie stanowią zagrożenia, możesz cofnąć wykonane akcje naprawcze, niezależnie od tego, czy zostały one wykonane automatycznie, czy ręcznie. W Centrum akcji **na karcie Historia** możesz cofnąć dowolną z następujących akcji:  

| Źródło akcji | Obsługiwane akcje |
|:---|:---|
| — Zautomatyzowane badanie <br/>— Program antywirusowy Microsoft Defender <br/>— Ręczne akcje odpowiedzi | - Wyizoluj urządzenie <br/>- Ograniczanie wykonywania kodu <br/>- Poddaj plikowi kwarantannę <br/>- Usunięcie klucza rejestru <br/>— Zatrzymywanie usługi <br/>- Wyłączanie sterownika <br/>— Usuwanie zaplanowanego zadania |

### <a name="undo-one-remediation-action"></a>Cofanie jednej akcji naprawczej

1. Przejdź do Centrum akcji ([https://security.microsoft.com/action-center](https://security.microsoft.com/action-center)) i zaloguj się.

2. Na **karcie Historia** wybierz akcję, którą chcesz cofnąć.

3. W okienku po prawej stronie ekranu wybierz pozycję **Cofnij**.

### <a name="undo-multiple-remediation-actions"></a>Cofanie wielu działań naprawczych

1. Przejdź do Centrum akcji (https://security.microsoft.com/action-center) i zaloguj się).

2. Na **karcie Historia** wybierz akcje, które chcesz cofnąć. Pamiętaj, aby zaznaczyć elementy, które mają ten sam typ akcji. Zostanie otwarte okienko wysuwu.

3. W wysuwanych okienkach wybierz pozycję **Cofnij**.

### <a name="to-remove-a-file-from-quarantine-across-multiple-devices"></a>Aby usunąć plik z kwarantanny na wielu urządzeniach 

1. Przejdź do Centrum akcji ([https://security.microsoft.com/action-center](https://security.microsoft.com/action-center)) i zaloguj się.

2. Na **karcie Historia** wybierz plik, który ma **typ akcji** Kwarantanna.

3. W okienku po prawej stronie ekranu wybierz pozycję Zastosuj do X większej liczby wystąpień **tego** pliku, a następnie wybierz pozycję **Cofnij**.

## <a name="next-steps"></a>Następne kroki

- [Wyświetlanie szczegółów i wyników automatycznego badania](m365d-autoir-results.md)
- [Adresuje wartości fałszywie dodatnie lub ujemne](m365d-autoir-report-false-positives-negatives.md)
