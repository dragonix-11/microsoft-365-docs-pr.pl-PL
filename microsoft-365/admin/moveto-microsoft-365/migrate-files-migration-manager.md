---
title: Migrowanie plików Google do platformy Microsoft 365 dla firm
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
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- adminvideo
monikerRange: o365-worldwide
search.appverid:
- BCS160
- MET150
- MOE150
description: Dowiedz się, jak migrować pliki Google na platformę Microsoft 365 dla firm przy użyciu programu SharePoint Migration Manager.
ms.openlocfilehash: 68b3a0455a2bf57e35308c428bf2b5de3e4b5983
ms.sourcegitcommit: e9692a40dfe1f8c2047699ae3301c114a01b0d3a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2022
ms.locfileid: "66602121"
---
# <a name="migrate-google-files-to-microsoft-365-for-business-with-migration-manager"></a>Migrowanie plików Google do usługi Microsoft 365 dla firm za pomocą programu Migration Manager

Zapoznaj się z [pomocą dla małych firm platformy Microsoft 365](https://go.microsoft.com/fwlink/?linkid=2197659) w serwisie YouTube.

## <a name="watch-migrate-google-files-to-microsoft-365-for-business"></a>Obejrzyj: Migrowanie plików Google na platformę Microsoft 365 dla firm

Zapoznaj się z tym filmem i innymi osobami na naszym [kanale YouTube](https://go.microsoft.com/fwlink/?linkid=2198217).

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWSx43?autoplay=false]

Po przejściu na platformę Microsoft 365 dla firm z obszaru roboczego Google należy przeprowadzić migrację plików z dysku Google. Za pomocą programu SharePoint Migration Manager można przenosić pliki z dysków osobistych i udostępnionych. To wideo i podsumowanie wymaganych kroków zawiera omówienie tego, jak to zrobić. Aby uzyskać więcej informacji, zobacz artykuł [Migrowanie usługi Google Drive do platformy Microsoft 365 za pomocą programu Migration Manager](/sharepointmigration/mm-google-overview).

> [!NOTE]
> Program Migration Manager utworzy kopię plików i przeniesie kopie na platformę Microsoft 365 dla firm. Oryginalne pliki pozostaną również na dyskach Google.

## <a name="before-you-start"></a>Przed rozpoczęciem

Wszyscy użytkownicy powinni zalogować się do platformy Microsoft 365 dla firm i skonfigurować OneDrive dla Firm. W tym celu przejdź do [office.com](https://office.com), zaloguj się przy użyciu poświadczeń usługi Microsoft 365 dla firm, a następnie wybierz pozycję OneDrive.

## <a name="install-the-microsoft-365-migration-app"></a>Instalowanie aplikacji do migracji platformy Microsoft 365

Wykonaj poniższe kroki, aby zainstalować aplikację Microsoft 365 Migration w środowisku obszaru roboczego Google. 
1. W centrum Administracja programu SharePoint wybierz pozycję **Migracja**.
2. Na stronie **Migracja** w sekcji **Obszar roboczy Google** wybierz pozycję **Rozpocznij**.
3. Na stronie **Migrowanie zawartości obszaru roboczego Google do platformy Microsoft 365** wybierz pozycję **Połącz z obszarem roboczym Google**.
4. Wybierz pozycję **Zainstaluj i autoryzuj**.
5. Na stronie **Google Workspace Marketplace** wybierz pozycję **Zaloguj się i wprowadź** poświadczenia administratora obszaru roboczego Google.
6. Wybierz pozycję **Zainstaluj domenę**.
7. Naciśnij przycisk **Kontynuuj**.
8. Zaznacz pole wyboru, a następnie wybierz pozycję **Zezwalaj**.
9. Po zakończeniu instalacji wybierz pozycję **Gotowe**.
10. Wróć do strony **Instalowanie aplikacji do migracji** i wybierz pozycję **Dalej**.
11. Wybierz pozycję **Zaloguj się do obszaru roboczego Google**, a następnie wprowadź poświadczenia administratora obszaru roboczego Google.
12. Wybierz **Zakończ**.

## <a name="select-and-scan-your-drives"></a>Wybieranie i skanowanie dysków

Po zainstalowaniu aplikacji Microsoft 365 Migration App w środowisku Google możesz teraz wybrać dyski, które chcesz przeprowadzić migrację, a następnie je zeskanować, aby upewnić się, że można je bezpiecznie skopiować na platformę Microsoft 365.

1. Na karcie **Skanowanie** wybierz dyski Google, które chcesz skopiować na platformę Microsoft 365.
2. Wybierz pozycję **Skanuj**. Po zakończeniu skanowania na dyskach zostanie wyświetlony stan skanowania **Gotowy do migracji**.
3. Wybierz pozycję **Kopiuj do migracji**.

## <a name="start-the-migration"></a>Rozpoczynanie migracji

Po wybraniu i zeskanowaniu dysków, które chcesz przeprowadzić migrację, wykonaj następujące kroki, aby je zmigrować.

1. Na karcie **Migracja** sprawdź ścieżki docelowe dysków, które chcesz migrować. Edytuj je w razie potrzeby.
2. Wybierz dyski, które chcesz przeprowadzić migrację, a następnie wybierz pozycję **Migruj**. 
3. Po pomyślnym zakończeniu migracji na każdym dysku zostanie wyświetlony **stan migracji** **Ukończono**.