---
title: Tagi użytkowników w programie Microsoft Defender dla Office 365
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: 12/17/2021
audience: ITPro
ms.topic: how-to
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- M365-security-compliance
ms.custom: ''
description: Administratorzy mogą dowiedzieć się, jak zidentyfikować konkretne grupy użytkowników z tagami użytkowników w uchcie Microsoft Defender for Office 365 Plan 2. Filtrowanie tagów jest dostępne w alertach, raportach i badaniach w programie Microsoft Defender Office 365 w celu szybkiego identyfikowania otagowanych użytkowników.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: f6a5262b184e5785695d73be32080adb8b44109c
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/12/2022
ms.locfileid: "63021342"
---
# <a name="user-tags-in-microsoft-defender-for-office-365"></a>Tagi użytkowników w programie Microsoft Defender dla Office 365

Tagi użytkowników to identyfikatory dla określonych grup użytkowników w programie [Microsoft Defender dla Office 365](defender-for-office-365.md). Istnieją dwa typy tagów użytkowników:

- **Tagi systemowe**: Obecnie konta [priorytetów](../../admin/setup/priority-accounts.md) to jedyny typ tagu systemowego.
- **Tagi niestandardowe**. Te tagi użytkownika tworzysz samodzielnie.

Jeśli Twoja organizacja korzysta z usługi Defender Office 365 Plan 2 (zawartej w Twojej subskrypcji lub jako dodatek), możesz utworzyć niestandardowe tagi użytkownika oprócz używania tagu kont priorytetów.

> [!NOTE]
> Obecnie tagi użytkowników można stosować tylko do użytkowników skrzynek pocztowych.

Po zastosowaniu tagów systemowych lub niestandardowych do użytkowników możesz ich używać jako filtrów w alertach, raportach i badaniach:

- [Alerty](alerts.md)
- [Niestandardowe zasady alertów](../../compliance/alert-policies.md#viewing-alerts)
- [Eksplorator zagrożeń i wykrywanie w czasie rzeczywistym](threat-explorer.md)
- [Strona jednostki e-mail](mdo-email-entity-page.md#other-innovations)
- [Raport o stanie ochrony przed zagrożeniami](view-email-security-reports.md#threat-protection-status-report)
- [Widoki kampanii](campaigns.md)
- [Przesyłanie administratorów i użytkowników](admin-submission.md)
- [Kwarantanna](quarantine.md)
- W przypadku kont priorytetowych możesz użyć raportu Problemy z pocztą e-mail dla kont priorytetowych [w Centrum](/exchange/monitoring/mail-flow-reports/mfr-email-issues-for-priority-accounts-report) administracyjnym usługi Exchange(EAC).

W tym artykule opisano sposób konfigurowania tagów użytkowników w portalu Microsoft 365 Defender użytkowników. W portalu nie ma żadnych Microsoft 365 Defender cmdlet do zarządzania tagami użytkowników.

Aby zobaczyć, jak tagi użytkowników są częścią strategii dotyczącej ochrony wyeksymrowych kont użytkowników, zobacz Zalecenia dotyczące zabezpieczeń dla kont priorytetowych w [programie Microsoft 365](security-recommendations-for-priority-accounts.md).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Co należy wiedzieć przed rozpoczęciem?

- Otwierasz portal Microsoft 365 Defender w witrynie <https://security.microsoft.com>. Aby przejść bezpośrednio do **strony Tagi użytkownika**, użyj .<https://security.microsoft.com/securitysettings/userTags>

- Aby można było wykonać procedury z tego artykułu, musisz mieć przypisane uprawnienia Microsoft 365 Defender portalu administracyjnego:
  - Aby tworzyć, modyfikować i usuwać niestandardowe tagi użytkownika, musisz być członkiem grup ról Zarządzanie **organizacją** lub **Administrator** zabezpieczeń.
  - Aby dodać i usunąć członków z tagu systemu konta priorytetowego, musisz być członkiem administratora zabezpieczeń i  mieć Exchange **ról** administratora.
  - Aby dodawać i usuwać członków z istniejących niestandardowych tagów użytkowników, musisz być członkiem grup ról Zarządzanie **organizacją** lub **Administrator** zabezpieczeń.
  - Aby mieć dostęp tylko do odczytu do tagów użytkowników, musisz być członkiem grup ról Czytnik **globalny,** **Operator** zabezpieczeń lub **Czytnik** zabezpieczeń.

  Aby uzyskać więcej informacji, [zobacz Uprawnienia w portalu Microsoft 365 Defender użytkowników](permissions-microsoft-365-security-center.md).

  > [!NOTE]
  >
  > - Dodanie użytkowników do odpowiedniej Azure Active Directory głównej w aplikacji centrum administracyjne platformy Microsoft 365 zapewnia użytkownikom wymagane uprawnienia w portalu Microsoft 365 Defender oraz uprawnienia do innych funkcji w  Microsoft 365. Aby uzyskać więcej informacji, zobacz [Informacje o rolach administratorów](../../admin/add-users/about-admin-roles.md).
  >
  > - Zarządzanie tagami użytkowników jest kontrolowane przez role **czytnika tagów** **i menedżera** tagów.

- Możesz również zarządzać kontami priorytetu i monitorować je w centrum administracyjne platformy Microsoft 365. Aby uzyskać instrukcje, [zobacz Zarządzanie kontami o priorytecie i monitorowanie ich](../../admin/setup/priority-accounts.md).

- Aby uzyskać informacje na _temat zabezpieczania_ kont uprzywilejowanych (kont administratora), zobacz [ten temat](/azure/architecture/framework/security/critical-impact-accounts).

## <a name="use-the-microsoft-365-defender-portal-to-create-user-tags"></a>Tworzenie tagów Microsoft 365 Defender za pomocą portalu

1. W portalu Microsoft 365 Defender pod adresem <https://security.microsoft.com>, przejdź  \> do Ustawienia **e-mail & tagów** \> **użytkowników współpracy**. Aby przejść bezpośrednio do **strony Tagi użytkownika**, użyj .<https://security.microsoft.com/securitysettings/userTags>

2. Na stronie **Tagi użytkownika** kliknij ikonę ![Utwórz tag.](../../media/m365-cc-sc-create-icon.png) **Utwórz tag**.

3. Zostanie **otwarty kreator** Tworzenie tagów w nowym wysuwanych menu. Na stronie **Definiowanie tagu** skonfiguruj następujące ustawienia:
   - **Nazwa**: Wprowadź unikatową nazwę opisową tagu. Jest to wartość, która będzie przez Ciebie widzieć i używać. Pamiętaj, że po utworzeniu tagu nie można zmienić jego nazwy.
   - **Opis**. Wprowadź opcjonalny opis tagu.

   Po zakończeniu kliknij przycisk **Dalej**.

4. Na stronie **Przypisywanie członków** wykonaj jedną z następujących czynności:
   - Kliknij ikonę ![Dodaj członków.](../../media/m365-cc-sc-create-icon.png) **Dodaj członków**. W wyświetlonym wysuwu wykonaj dowolną z następujących czynności, aby dodać poszczególnych użytkowników lub grupy:
     - Kliknij w polu i przewiń listę, aby wybrać użytkownika lub grupę.
     - Kliknij w polu i zacznij pisać, aby przefiltrować listę, a następnie wybierz użytkownika lub grupę.
     - Aby dodać kolejne wartości, kliknij pusty obszar w polu.
     - Aby usunąć poszczególne wpisy, kliknij pozycję ![Ikona usuwania wpisu.](../../media/m365-cc-sc-remove-selection-icon.png) obok pozycji w polu.
     - Aby usunąć wszystkie wpisy, kliknij ikonę ![Usuń wpis.](../../media/m365-cc-sc-remove-selection-icon.png) na pozycji **Wybrani użytkownicy nn i nn grup** poniżej pola.

     Po zakończeniu kliknij przycisk **Dodaj**.

     Na stronie **Przypisywanie członków** możesz również usuwać wpisy, klikając ikonę ![Usuń.](../../media/m365-cc-sc-delete-icon.png) obok wpisu.

   - Kliknij **pozycję** Importuj, aby wybrać plik tekstowy zawierający adresy e-mail użytkowników lub grup. Upewnij się, że plik tekstowy zawiera jedną pozycję w wierszu.

   Po zakończeniu kliknij przycisk **Dalej**.

5. Na **wyświetlonej stronie znacznika** Recenzja przejrzyj ustawienia. Możesz wybrać pozycję **Edytuj** w każdej sekcji, aby zmodyfikować ustawienia w sekcji. Możesz też kliknąć przycisk **Wstecz** lub wybrać określoną stronę w kreatorze.

   Po zakończeniu kliknij pozycję **Prześlij**, a następnie kliknij pozycję **Gotowe**.

## <a name="use-the-microsoft-365-defender-portal-to-view-user-tags"></a>Wyświetlanie tagów Microsoft 365 Defender portalu użytkownika

1. W portalu Microsoft 365 Defender pod adresem <https://security.microsoft.com>, przejdź  \> do Ustawienia **e-mail & tagów** \> **użytkowników współpracy**. Aby przejść bezpośrednio do **strony Tagi użytkownika**, użyj .<https://security.microsoft.com/securitysettings/userTags>

2. Na **stronie Tagi** użytkownika na liście tagów użytkowników są wyświetlane następujące właściwości:

   - **Tag**: nazwa tagu użytkownika. Pamiętaj, że obejmuje to wbudowany **tag systemowy** konta Priorytet.
   - **Dotyczy**: Liczba członków
   - **Ostatnia modyfikacja**
   - **Utworzono w dniu**

3. Po wybraniu tagu użytkownika przez kliknięcie nazwy szczegóły są wyświetlane w wysuwanych informacjach.

## <a name="use-the-microsoft-365-defender-portal-to-modify-user-tags"></a>Modyfikowanie tagów Microsoft 365 Defender za pomocą portalu

1. W portalu Microsoft 365 Defender pod adresem <https://security.microsoft.com>, przejdź  \> do Ustawienia **e-mail & tagów** \> **użytkowników współpracy**. Aby przejść bezpośrednio do **strony Tagi użytkownika**, użyj .<https://security.microsoft.com/securitysettings/userTags>

2. Na stronie **Tagi użytkownika** wybierz tag użytkownika z listy, a następnie kliknij ikonę ![Edytuj tag.](../../media/m365-cc-sc-edit-icon.png) **Edytuj tag**.

3. W wyświetlonym wysuwanych szczegółach dostępny jest ten sam kreator i ustawienia, jak opisano [](#use-the-microsoft-365-defender-portal-to-create-user-tags) w sekcji Tworzenie tagów użytkowników za pomocą portalu Microsoft 365 Defender do tworzenia tagów użytkowników we wcześniejszej części tego artykułu.

   **Uwagi**:

   - Strona **Definiowanie tagu** nie jest dostępna dla wbudowanego tagu systemowego konta priorytetowego, więc nie można zmienić nazwy tego tagu ani opisu.
   - Nie można zmienić nazwy tagu niestandardowego, ale można zmienić opis.

## <a name="use-the-microsoft-365-defender-portal-to-remove-user-tags"></a>Usuwanie tagów Microsoft 365 Defender za pomocą portalu użytkownika

> [!NOTE]
> Nie można usunąć wbudowanego tagu systemowego **konta** priorytetowego.

1. W portalu Microsoft 365 Defender pod adresem <https://security.microsoft.com>, przejdź  \> do Ustawienia **e-mail & tagów** \> **użytkowników współpracy**. Aby przejść bezpośrednio do **strony Tagi użytkownika**, użyj .<https://security.microsoft.com/securitysettings/userTags>

2. Na stronie **Tagi użytkownika** wybierz tag użytkownika z listy, a następnie kliknij ikonę ![Usuń tag.](../../media/m365-cc-sc-delete-icon.png) **Usuń tag**.

3. Przeczytaj ostrzeżenie w wyświetlonym oknie dialogowym potwierdzenia, a następnie kliknij przycisk **Tak, usuń**.
