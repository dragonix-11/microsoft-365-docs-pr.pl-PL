---
title: Dodawanie użytkowników i przypisywanie licencji w Microsoft Defender dla Firm
description: Dowiedz się, jak dodawać użytkowników i przypisywać licencje
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: article
ms.date: 04/14/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.collection: M365-security-compliance.
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.openlocfilehash: d954d745cde6505fb91eff8e394aee4f06c59092
ms.sourcegitcommit: e3bc6563037bd2cce2abf108b3d1bcc2ccf538f6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/15/2022
ms.locfileid: "64862924"
---
# <a name="add-users-and-assign-licenses-in-microsoft-defender-for-business"></a>Dodawanie użytkowników i przypisywanie licencji w Microsoft Defender dla Firm

Po zarejestrowaniu się w Microsoft Defender dla Firm pierwszym krokiem jest dodanie użytkowników i przypisanie licencji. W tym artykule opisano sposób dodawania użytkowników i opisano kolejne kroki.

## <a name="add-users-and-assign-licenses"></a>Dodawanie użytkowników i przypisywanie licencji

> [!IMPORTANT]
> Aby wykonać to zadanie, musisz być administratorem globalnym.  Osoba, która utworzyła firmę w celu Microsoft 365 lub Microsoft Defender dla Firm, jest domyślnie administratorem globalnym.

1. Przejdź do Centrum administracyjne platformy Microsoft 365 i [https://admin.microsoft.com](https://admin.microsoft.com) zaloguj się.

2. Przejdź do pozycji **UżytkownicyAktywni** >  użytkownicy, a następnie wybierz **pozycję Dodaj użytkownika**.

3. W okienku **Konfigurowanie ustawień podstawowych** wypełnij podstawowe informacje o użytkowniku, a następnie wybierz pozycję **Dalej**.

   - **Nazwa**: podaj imię i nazwisko, nazwę wyświetlaną i nazwę użytkownika.
   - **Domena** Wybierz domenę dla konta użytkownika. Jeśli na przykład nazwa użytkownika `Pat`to , a domena to `contoso.com`, zaloguje się przy użyciu polecenia `pat@contoso.com`.
   - **Ustawienia hasła**: wybierz, czy chcesz użyć automatycznie wygenerowanego hasła, czy utworzyć własne silne hasło dla użytkownika. Użytkownik musi zmienić swoje hasło po 90 dniach. Możesz też wybrać opcję **Wymagaj od tego użytkownika zmiany hasła podczas pierwszego logowania**. Możesz również wybrać, czy chcesz wysłać hasło użytkownika w wiadomości e-mail po dodaniu użytkownika.

4. Na stronie **Przypisywanie licencji produktów** wybierz pozycję Microsoft Defender dla Firm (lub Microsoft 365 Business Premium). Następnie wybierz pozycję **Dalej**. 

   Jeśli nie masz dostępnych żadnych licencji, nadal możesz dodać użytkownika i kupić dodatkowe licencje. Aby uzyskać więcej informacji na temat dodawania użytkowników, zobacz [Dodawanie użytkowników i przypisywanie licencji w tym samym czasie](../../admin/add-users/add-users.md).

5. Na stronie **Ustawienia opcjonalne** możesz rozwinąć **pozycję Informacje o profilu** i wypełnić szczegóły, takie jak tytuł jo użytkownika, dział, lokalizacja itd. Następnie wybierz pozycję **Dalej**.

6. Na stronie **Przeglądanie i zakończenie** przejrzyj szczegóły, a następnie wybierz pozycję **Zakończ dodawanie** , aby dodać użytkownika. Jeśli chcesz wprowadzić jakiekolwiek zmiany, wybierz pozycję **Wstecz** , aby wrócić do poprzedniej strony.

## <a name="next-steps"></a>Następne kroki

- [Odwiedź portal Microsoft 365 Defender](mdb-get-started.md)
- [Użyj kreatora konfiguracji w Microsoft Defender dla Firm](mdb-use-wizard.md).