---
title: Raport o stanie urządzeń
description: Wyjaśnia stan urządzenia
keywords: Microsoft Managed Desktop, Microsoft 365, usługa, dokumentacja
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
ms.openlocfilehash: be685d39bbda3b96f689c13a3bc3485c011f1ec8
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63319883"
---
# <a name="device-status-report"></a>Raport o stanie urządzeń

Ten raport agreguje stan wszystkich zarejestrowanych urządzeń w celu pokazania korzystania z usługi zarządzanej komputera stacjonarnego firmy Microsoft.

Kategoryzowamy urządzenia na podstawie ich aktywności w ciągu ostatnich 28 dni oraz od możliwości aktualizowania urządzenia.

Aby jak najszybciej zaktualizować usługę Windows Update, urządzenie musi:

- Mieć połączenie z Internetem.
- Nie hibernating.
- Nie wstrzymano na co najmniej sześć godzin, z których dwie muszą być ciągłe.

Chociaż możliwe jest, że urządzenie, które nie spełnia tych wymagań, zostanie zaktualizowane. Urządzenia spełniające te wymagania mają największe prawdopodobieństwo aktualizacji.

:::image type="content" source="../../media/mmd-device-status.png" alt-text="Raport przedstawiający wykres pierścieniowy przedstawiający stan aktywności urządzenia w lewym górnym rogu, filtry w prawym górnym rogu z przyciskiem do wygenerowania raportu, a tabela szczegółów u dołu":::

## <a name="device-status-labels"></a>Etykiety stanu urządzenia

Stan urządzenia jest raportny za pomocą następujących etykiet:

| Etykieta stanu urządzenia | Opis |
| ------ | ------ |
| Gotowe dla użytkownika | Urządzenia, które zostały pomyślnie zarejestrowane w naszej usłudze i gotowe do użycia dla użytkownika.|
| Aktywny | Używane urządzenia. <ul><li>Spełnili kryteria działań (sześć godzin, dwie ciągłe) najnowszej aktualizacji zabezpieczeń.</li> <li>W ciągu ostatnich pięciu dni zaewidencjonowali oni usługę Microsoft Intune co najmniej raz.</li></ul> |
| Zsynchronizowano | Urządzenia używane i zaewidencjonowane za pomocą usługi Intune w ciągu ostatnich 28 dni.
| Nie można zsynchronizować | Urządzenia używane, ale nie zaewidencjonowane za pomocą usługi Intune w ciągu ostatnich 28 dni. |
| Inne | Etykieta agreguje kilka stanów błędów, które mogą występować zwykle podczas rejestracji urządzenia. Aby uzyskać więcej informacji, zobacz [Rozwiązywanie problemów z rejestracją urządzenia](../get-started/manual-registration.md#troubleshooting-device-registration). |
