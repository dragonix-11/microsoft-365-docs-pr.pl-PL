---
title: Wyświetlanie akcji i zarządzanie nimi w centrum akcji
description: Wyświetlanie akcji korygowania i zarządzanie nimi za pomocą Centrum akcji
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
ms.openlocfilehash: 43c48081a86e33cd918bc4de8f01859bc1107583
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2022
ms.locfileid: "64666839"
---
# <a name="view-and-manage-actions-in-the-action-center"></a>Wyświetlanie akcji i zarządzanie nimi w centrum akcji

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Dotyczy:**
- Microsoft 365 Defender

Funkcje ochrony przed zagrożeniami w Microsoft 365 Defender mogą powodować pewne akcje korygowania. Oto kilka przykładów:

- [Zautomatyzowane badania](m365d-autoir.md) mogą skutkować akcjami korygowania, które są wykonywane automatycznie lub oczekują na zatwierdzenie.
- Oprogramowanie antywirusowe, oprogramowanie chroniące przed złośliwym kodem i inne funkcje ochrony przed zagrożeniami mogą powodować akcje korygowania, takie jak blokowanie pliku, adresu URL lub procesu albo wysyłanie artefaktu do kwarantanny.
- Zespół ds. operacji zabezpieczeń może ręcznie wykonywać akcje korygowania, takie jak podczas [zaawansowanego wyszukiwania zagrożeń](advanced-hunting-overview.md) lub podczas badania [alertów](investigate-alerts.md) lub [zdarzeń](investigate-incidents.md).

> [!NOTE]
> Musisz mieć odpowiednie uprawnienia do zatwierdzania lub odrzucania akcji [korygowania](m365d-action-center.md#required-permissions-for-action-center-tasks) . Aby uzyskać więcej informacji, zobacz [wymagania wstępne](m365d-configure-auto-investigation-response.md#prerequisites-for-automated-investigation-and-response-in-microsoft-365-defender).

## <a name="review-pending-actions-in-the-action-center"></a>Przeglądanie oczekujących akcji w Centrum akcji

Ważne jest, aby zatwierdzić (lub odrzucić) oczekujące akcje tak szybko, jak to możliwe, aby zautomatyzowane badania mogły być kontynuowane i wykonywane w odpowiednim czasie. 

1. Przejdź do <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portalu Microsoft 365 Defender</a> i zaloguj się. 

2. W okienku nawigacji wybierz pozycję **Centrum akcji**. 

3. W centrum akcji na karcie **Oczekujące** wybierz element z listy. Zostanie otwarte okienko wysuwane. Oto przykład.

   :::image type="content" source="../../media/air-actioncenter-itemselected.png" alt-text="Opcje zatwierdzania lub odrzucania akcji" lightbox="../../media/air-actioncenter-itemselected.png":::

4. Przejrzyj informacje w okienku wysuwanego, a następnie wykonaj jedną z następujących czynności:
   - Wybierz **pozycję Otwórz stronę badania** , aby wyświetlić więcej szczegółów na temat badania.
   - Wybierz pozycję **Zatwierdź** , aby zainicjować oczekującą akcję.
   - Wybierz pozycję **Odrzuć** , aby zapobiec podjęciu oczekującej akcji.
   - Wybierz pozycję **Go hunt** ,aby przejść do [pozycji Zaawansowane wyszukiwanie zagrożeń](advanced-hunting-overview.md). 

## <a name="undo-completed-actions"></a>Cofnij ukończone akcje

Jeśli ustalisz, że urządzenie lub plik nie stanowi zagrożenia, możesz cofnąć podjęte akcje korygowania, niezależnie od tego, czy te akcje zostały wykonane automatycznie, czy ręcznie. W centrum akcji na karcie **Historia** możesz cofnąć dowolną z następujących akcji:  

| Źródło akcji | Obsługiwane akcje |
|:---|:---|
| - Zautomatyzowane badanie <br/>- Program antywirusowy Microsoft Defender <br/>— Ręczne akcje reagowania | - Izolowanie urządzenia <br/>— Ograniczanie wykonywania kodu <br/>— Kwarantanna pliku <br/>— Usuwanie klucza rejestru <br/>— Zatrzymywanie usługi <br/>— Wyłączanie sterownika <br/>— Usuwanie zaplanowanego zadania |

### <a name="undo-one-remediation-action"></a>Cofnij jedną akcję korygowania

1. Przejdź do centrum akcji ([https://security.microsoft.com/action-center](https://security.microsoft.com/action-center)) i zaloguj się.

2. Na karcie **Historia** wybierz akcję, którą chcesz cofnąć.

3. W okienku po prawej stronie ekranu wybierz pozycję **Cofnij**.

### <a name="undo-multiple-remediation-actions"></a>Cofanie wielu akcji korygowania

1. Przejdź do centrum akcji (https://security.microsoft.com/action-center) i zaloguj się.

2. Na karcie **Historia** wybierz akcje, które chcesz cofnąć. Pamiętaj, aby wybrać elementy o tym samym typie akcji. Zostanie otwarte okienko wysuwane.

3. W okienku wysuwanym wybierz pozycję **Cofnij**.

### <a name="to-remove-a-file-from-quarantine-across-multiple-devices"></a>Aby usunąć plik z kwarantanny na wielu urządzeniach 

1. Przejdź do centrum akcji ([https://security.microsoft.com/action-center](https://security.microsoft.com/action-center)) i zaloguj się.

2. Na karcie **Historia** wybierz plik z typem akcji **pliku kwarantanny** .

3. W okienku po prawej stronie ekranu wybierz pozycję **Zastosuj do X więcej wystąpień tego pliku**, a następnie wybierz pozycję **Cofnij**.

## <a name="next-steps"></a>Następne kroki

- [Wyświetlanie szczegółów i wyników zautomatyzowanego badania](m365d-autoir-results.md)
- [Adres fałszywie dodatnie lub fałszywie ujemne](m365d-autoir-report-false-positives-negatives.md)
