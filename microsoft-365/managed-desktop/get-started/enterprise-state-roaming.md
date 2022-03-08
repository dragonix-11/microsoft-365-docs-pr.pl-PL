---
title: Włącz usługę Enterprise State Roaming
description: W tym artykule opisano, jak włączyć roaming stanowy przedsiębiorstwa
keywords: Microsoft Managed Desktop, Microsoft 365, usługa, dokumentacja
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
ms.openlocfilehash: 65056fc913b88ce0594c9a8b1a89bd2e92b221af
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63326807"
---
# <a name="enable-enterprise-state-roaming"></a>Włącz usługę Enterprise State Roaming

[Enterprise roamingu stanu](/azure/active-directory/devices/enterprise-state-roaming-overview) umożliwia użytkownikom bezpieczną synchronizację danych ustawień użytkowników i aplikacji z chmurą. Oznacza to, że będą mieli to samo środowisko niezależnie od tego, Windows do którego się zalogowali. Jeśli na przykład zamienisz jedno z urządzeń przenośnych Microsoft Managed Desktop na nowe, będzie ono wyglądać i działać dokładnie tak samo jak ostatnie.

Enterprise roamingu województwa to opcjonalna funkcja usługi Microsoft Managed Desktop, która może zostać skonfigurowana dla użytkowników. Nie jest ona uwzględniana ani zarządzana w ramach Microsoft Managed Desktop.

Aby włączyć Enterprise roamingu stanowego, wykonaj czynności opisane [Enterprise Roamingu województwa w Azure Active Directory](/azure/active-directory/devices/enterprise-state-roaming-enable).

>[!NOTE]
>Jeśli włączysz roaming Enterprise stan, preferowana lista języków zastąpi język wybrany podczas konfigurowania urządzenia. Użytkownicy mogą rozwiązać ten problem łatwo, ale na początku może to spowodować niespójne środowisko lokalizacji. Przed skonfigurowaniem Enterprise sprawdź, czy roaming stanowy jest odpowiedni dla użytkowników.

## <a name="steps-to-get-started-with-microsoft-managed-desktop"></a>Procedura rozpoczynania pracy z Microsoft Managed Desktop

1. [Dodaj i zweryfikuj kontakty administratora w portalu administracyjnym](add-admin-contacts.md).
2. [Dostosowywanie dostępu warunkowego](conditional-access.md).
3. [Przypisywanie licencji](assign-licenses.md).
4. [Wdrażanie Intune — Portal firmy](company-portal.md).
5. Włącz Enterprise roamingu województwa (ten temat).
6. [Przygotowywanie urządzeń](prepare-devices.md).
7. [Przygotuj użytkowników do korzystania z urządzeń](get-started-devices.md).
8. [Wdychuj aplikacje](deploy-apps.md).
