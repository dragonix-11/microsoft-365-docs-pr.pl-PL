---
title: Tagi użytkowników w Ochrona usługi Office 365 w usłudze Microsoft Defender
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
description: Administratorzy mogą dowiedzieć się, jak identyfikować określone grupy użytkowników za pomocą tagów użytkowników w planie Ochrona usługi Office 365 w usłudze Microsoft Defender 2. Filtrowanie tagów jest dostępne dla alertów, raportów i badań w Ochrona usługi Office 365 w usłudze Microsoft Defender, aby szybko zidentyfikować otagowanych użytkowników.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 1f045e5dcb590c36fd0f3768c472057b07b12b21
ms.sourcegitcommit: dba1a846ae78ea14240d28efa8d4934fe303f308
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2022
ms.locfileid: "64891825"
---
# <a name="user-tags-in-microsoft-defender-for-office-365"></a>Tagi użytkowników w Ochrona usługi Office 365 w usłudze Microsoft Defender

Tagi użytkowników to identyfikatory określonych grup użytkowników w [Ochrona usługi Office 365 w usłudze Microsoft Defender](defender-for-office-365.md). Istnieją dwa typy tagów użytkowników:

- **Tagi systemowe**: Obecnie [konta priorytetowe](../../admin/setup/priority-accounts.md) są jedynym typem tagu systemowego.
- **Tagi niestandardowe**: te tagi użytkowników są tworzone samodzielnie.

Jeśli Twoja organizacja ma Ochrona usługi Office 365 w usłudze Defender plan 2 (uwzględniony w subskrypcji lub jako dodatek), możesz utworzyć niestandardowe tagi użytkowników oprócz używania tagu kont priorytetowych.

> [!NOTE]
> Obecnie tagi użytkowników można stosować tylko do użytkowników skrzynki pocztowej.

Po zastosowaniu tagów systemowych lub tagów niestandardowych do użytkowników możesz użyć tych tagów jako filtrów w alertach, raportach i badaniach:

- [Alerty](alerts.md)
- [Niestandardowe zasady alertów](../../compliance/alert-policies.md#viewing-alerts)
- [Eksplorator zagrożeń i wykrywanie w czasie rzeczywistym](threat-explorer.md)
- [Raport użytkownika z naruszeniem zabezpieczeń](view-email-security-reports.md#compromised-users-report)
- [Strona jednostki poczty e-mail](mdo-email-entity-page.md#other-innovations)
- [Raport o stanie ochrony przed zagrożeniami](view-email-security-reports.md#threat-protection-status-report)
- [Symulacja ataku](attack-simulation-training.md#target-users)
- [Widoki kampanii](campaigns.md)
- [Przesyłanie przez administratora i użytkownika](admin-submission.md)
- [Kwarantanna](quarantine.md)
- W przypadku kont o priorytecie możesz użyć [raportu Problemy z pocztą e-mail dla kont priorytetowych](/exchange/monitoring/mail-flow-reports/mfr-email-issues-for-priority-accounts-report) w centrum administracyjnym Exchange (EAC).

W tym artykule wyjaśniono, jak skonfigurować tagi użytkowników w portalu Microsoft 365 Defender. Brak poleceń cmdlet w portalu Microsoft 365 Defender do zarządzania tagami użytkowników.

Aby zobaczyć, jak tagi użytkowników są częścią strategii ochrony kont użytkowników o dużym wpływie, zobacz [Zalecenia dotyczące zabezpieczeń dla kont priorytetowych w Microsoft 365](security-recommendations-for-priority-accounts.md).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Co należy wiedzieć przed rozpoczęciem?

- Otwórz portal Microsoft 365 Defender pod adresem <https://security.microsoft.com>. Aby przejść bezpośrednio do strony **Tagi użytkownika** , użyj polecenia <https://security.microsoft.com/securitysettings/userTags>.

- Aby można było wykonać procedury opisane w tym artykule, musisz mieć przypisane uprawnienia w portalu Microsoft 365 Defender:
  - Aby tworzyć, modyfikować i usuwać niestandardowe tagi użytkowników, musisz być członkiem grup ról **Zarządzanie organizacją** lub **Administrator zabezpieczeń** .
  - Aby dodać i usunąć członków z tagu systemu Konta priorytetowego, musisz być członkiem grup ról **administratora zabezpieczeń** i **administratora Exchange**.
  - Aby dodać i usunąć członków z istniejących niestandardowych tagów użytkowników, musisz być członkiem grup ról **Zarządzanie organizacją** lub **Administrator zabezpieczeń** .
  - Aby uzyskać dostęp tylko do odczytu do tagów użytkowników, musisz być członkiem grup ról **Czytelnik globalny**, **Operator zabezpieczeń** lub **Czytelnik zabezpieczeń** .

  Aby uzyskać więcej informacji, zobacz [Uprawnienia w portalu Microsoft 365 Defender](permissions-microsoft-365-security-center.md).

  > [!NOTE]
  >
  > - Dodanie użytkowników do odpowiedniej roli Azure Active Directory w Centrum administracyjne platformy Microsoft 365 daje użytkownikom wymagane uprawnienia w portalu Microsoft 365 Defender _i_ uprawnienia do innych funkcji w Microsoft 365. Aby uzyskać więcej informacji, zobacz: [Role administratora — informacje](../../admin/add-users/about-admin-roles.md).
  >
  > - Zarządzanie tagami użytkowników jest kontrolowane przez role **Czytelnik tagów** i **Menedżer tagów** .

- Kontami priorytetów można również zarządzać i monitorować w Centrum administracyjne platformy Microsoft 365. Aby uzyskać instrukcje, zobacz [Zarządzanie kontami priorytetów i monitorowanie ich](../../admin/setup/priority-accounts.md).

- Aby uzyskać informacje na temat zabezpieczania _kont uprzywilejowanych_ (kont administratorów), zobacz [ten temat](/azure/architecture/framework/security/critical-impact-accounts).

## <a name="use-the-microsoft-365-defender-portal-to-create-user-tags"></a>Tworzenie tagów użytkowników przy użyciu portalu Microsoft 365 Defender

1. W portalu Microsoft 365 Defender pod adresem <https://security.microsoft.com>przejdź do **strony Ustawienia** \> **Email & collaboration** \> **Tagi użytkowników**. Aby przejść bezpośrednio do strony **Tagi użytkownika** , użyj polecenia <https://security.microsoft.com/securitysettings/userTags>.

2. Na stronie **Tagi użytkownika** kliknij ikonę ![Utwórz tag.](../../media/m365-cc-sc-create-icon.png) **Utwórz tag**.

3. Kreator **tworzenia tagów** zostanie otwarty w nowym wysuwie. Na stronie **Definiowanie tagu** skonfiguruj następujące ustawienia:
   - **Nazwa**: wprowadź unikatową, opisową nazwę tagu. Jest to wartość, którą zobaczysz i użyjesz. Pamiętaj, że nie można zmienić nazwy tagu po jego utworzeniu.
   - **Opis**: wprowadź opcjonalny opis tagu.

   Po zakończeniu kliknij przycisk **Dalej**.

4. Na stronie **Przypisywanie członków** wykonaj jedną z następujących czynności:
   - Kliknij ikonę ![Dodaj członków.](../../media/m365-cc-sc-create-icon.png) **Dodaj członków**. W wyświetlonym wylocie wykonaj dowolne z następujących kroków, aby dodać poszczególnych użytkowników lub grupy:
     - Kliknij w polu i przewiń listę, aby wybrać użytkownika lub grupę.
     - Kliknij w polu i rozpocznij wpisywanie, aby odfiltrować listę i wybrać użytkownika lub grupę.
     - Aby dodać dodatkowe wartości, kliknij pusty obszar w polu.
     - Aby usunąć poszczególne wpisy, kliknij przycisk ![Usuń ikonę wpisu.](../../media/m365-cc-sc-remove-selection-icon.png) obok wpisu w polu.
     - Aby usunąć wszystkie wpisy, kliknij pozycję ![Usuń ikonę wpisu.](../../media/m365-cc-sc-remove-selection-icon.png) w **elemencie Selected nn users and nn groups (Wybrani użytkownicy nn i grupy nn** ) poniżej pola .

     Po zakończeniu kliknij przycisk **Dodaj**.

     Po powrocie na stronę **Przypisywanie członków** możesz również usunąć wpisy, klikając ikonę ![Usuń.](../../media/m365-cc-sc-delete-icon.png) obok wpisu.

   - Kliknij pozycję **Importuj** , aby wybrać plik tekstowy zawierający adresy e-mail użytkowników lub grup. Upewnij się, że plik tekstowy zawiera jeden wpis na wiersz.

   Po zakończeniu kliknij przycisk **Dalej**.

5. Na wyświetlonej stronie **Tag przeglądu** przejrzyj ustawienia. W każdej sekcji możesz wybrać pozycję **Edytuj** , aby zmodyfikować ustawienia w sekcji. Możesz też kliknąć przycisk **Wstecz** lub wybrać określoną stronę w kreatorze.

   Po zakończeniu kliknij pozycję **Prześlij**, a następnie kliknij pozycję **Gotowe**.

## <a name="use-the-microsoft-365-defender-portal-to-view-user-tags"></a>Wyświetlanie tagów użytkowników za pomocą portalu Microsoft 365 Defender

1. W portalu Microsoft 365 Defender pod adresem <https://security.microsoft.com>przejdź do **strony Ustawienia** \> **Email & collaboration** \> **Tagi użytkowników**. Aby przejść bezpośrednio do strony **Tagi użytkownika** , użyj polecenia <https://security.microsoft.com/securitysettings/userTags>.

2. Na stronie **Tagi użytkownika** na liście tagów użytkowników są wyświetlane następujące właściwości:

   - **Tag**: nazwa tagu użytkownika. Należy pamiętać, że obejmuje to wbudowany tag systemu **konta priorytetu** .
   - **Zastosowane do**: liczba elementów członkowskich
   - **Ostatnia modyfikacja**
   - **Utworzono w dniu**

3. Po wybraniu tagu użytkownika przez kliknięcie nazwy szczegóły zostaną wyświetlone w wysuwnym oknie.

## <a name="use-the-microsoft-365-defender-portal-to-modify-user-tags"></a>Modyfikowanie tagów użytkowników przy użyciu portalu Microsoft 365 Defender

1. W portalu Microsoft 365 Defender pod adresem <https://security.microsoft.com>przejdź do **strony Ustawienia** \> **Email & collaboration** \> **Tagi użytkowników**. Aby przejść bezpośrednio do strony **Tagi użytkownika** , użyj polecenia <https://security.microsoft.com/securitysettings/userTags>.

2. Na stronie **Tagi użytkownika** wybierz tag użytkownika z listy, a następnie kliknij pozycję ![Edytuj ikonę tagu.](../../media/m365-cc-sc-edit-icon.png) **Edytuj tag**.

3. W wyświetlonym oknie wysuwowym szczegółów ten sam kreator i ustawienia są dostępne zgodnie z opisem w sekcji [Tworzenie tagów użytkowników](#use-the-microsoft-365-defender-portal-to-create-user-tags) we wcześniejszej części tego artykułu za pomocą portalu Microsoft 365 Defender.

   **Uwagi**:

   - Strona **Definiowanie tagu** nie jest dostępna dla wbudowanego tagu systemu **konta priorytetu** , więc nie można zmienić nazwy tego tagu ani zmienić opisu.
   - Nie można zmienić nazwy tagu niestandardowego, ale możesz zmienić opis.

## <a name="use-the-microsoft-365-defender-portal-to-remove-user-tags"></a>Usuwanie tagów użytkowników za pomocą portalu Microsoft 365 Defender

> [!NOTE]
> Nie można usunąć wbudowanego tagu systemu **konta priorytetu** .

1. W portalu Microsoft 365 Defender pod adresem <https://security.microsoft.com>przejdź do **strony Ustawienia** \> **Email & collaboration** \> **Tagi użytkowników**. Aby przejść bezpośrednio do strony **Tagi użytkownika** , użyj polecenia <https://security.microsoft.com/securitysettings/userTags>.

2. Na stronie **Tagi użytkownika** wybierz tag użytkownika z listy, a następnie kliknij ikonę ![Usuń tag.](../../media/m365-cc-sc-delete-icon.png) **Usuń tag**.

3. Przeczytaj ostrzeżenie w wyświetlonym oknie dialogowym potwierdzenia, a następnie kliknij przycisk **Tak, usuń**.

## <a name="more-information"></a>Więcej informacji

[Konfigurowanie i przeglądanie kont priorytetów w Ochrona usługi Office 365 w usłudze Microsoft Defender](configure-review-priority-account.md)
