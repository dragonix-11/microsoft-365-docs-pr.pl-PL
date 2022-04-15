---
title: Przypisywanie ról i uprawnień w Microsoft Defender dla Firm
description: Dowiedz się, jak przypisywać role i uprawnienia w Microsoft Defender dla Firm
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 04/12/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: e4a3be91ff46626654f0c0f7b027557958429b33
ms.sourcegitcommit: e3bc6563037bd2cce2abf108b3d1bcc2ccf538f6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/15/2022
ms.locfileid: "64862681"
---
# <a name="assign-roles-and-permissions-in-microsoft-defender-for-business"></a>Przypisywanie ról i uprawnień w Microsoft Defender dla Firm

> [!NOTE]
> Microsoft Defender dla Firm jest teraz uwzględniony w [Microsoft 365 Business Premium](../../business-premium/index.md). 

Aby wykonywać zadania w portalu Microsoft 365 Defender, takie jak konfigurowanie Microsoft Defender dla Firm, wyświetlanie raportów lub podejmowanie akcji reagowania na wykryte zagrożenia, należy przypisać odpowiednie uprawnienia do zespołu ds. zabezpieczeń. Uprawnienia są przyznawane za pośrednictwem ról przypisanych w portalu Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) lub w [Azure Active Directory](/azure/active-directory/roles/manage-roles-portal). 

## <a name="what-to-do"></a>Co robić

1. [Dowiedz się więcej o rolach w usłudze Defender dla Firm](#roles-in-defender-for-business).

2. [Wyświetlanie lub edytowanie przypisań ról dla zespołu ds. zabezpieczeń](#view-or-edit-role-assignments).

3. [Przejdź do kolejnych kroków](#next-steps).

>
> **Masz minutę?**
> Weź udział w <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">krótkiej ankiecie dotyczącej bezpieczeństwa</a>. Chcielibyśmy usłyszeć od Ciebie!
>

## <a name="roles-in-defender-for-business"></a>Role w usłudze Defender dla firm

W poniższej tabeli opisano trzy role, które można przypisać w usłudze Defender for Business. [Dowiedz się więcej o rolach administratora](../../admin/add-users/about-admin-roles.md).

| Poziom uprawnień | Opis |
|:---|:---|
| **Administratorzy globalni** (nazywani również administratorami globalnymi) <br/><br/> *Najlepszym rozwiązaniem jest ograniczenie liczby administratorów globalnych.* | Administratorzy globalni mogą wykonywać różnego rodzaju zadania. Osoba, która utworzyła firmę w celu Microsoft 365 lub Microsoft Defender dla Firm, jest domyślnie administratorem globalnym. <br/><br/> Administratorzy globalni mogą uzyskiwać dostęp do ustawień i zmieniać je we wszystkich portalach Microsoft 365, takich jak: <br/>- Centrum administracyjne platformy Microsoft 365 ([https://admin.microsoft.com](https://admin.microsoft.com)) <br/>— portal Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) |
| **Administratorzy zabezpieczeń** (nazywani również administratorami zabezpieczeń) | Administratorzy zabezpieczeń mogą wykonywać następujące zadania: <br/>— Wyświetlanie zasad zabezpieczeń i zarządzanie nimi <br/>— Wyświetlanie zagrożeń i alertów związanych z zabezpieczeniami i zarządzanie nimi (działania te obejmują podejmowanie akcji reagowania w punktach końcowych) <br/>— Wyświetlanie informacji o zabezpieczeniach i raportów |
| **Czytelnik zabezpieczeń** | Czytelnicy zabezpieczeń mogą wykonywać następujące zadania: <br/>— Wyświetlanie zasad zabezpieczeń <br/>— Wyświetlanie zagrożeń i alertów związanych z zabezpieczeniami <br/>— Wyświetlanie informacji o zabezpieczeniach i raportów  |


## <a name="view-or-edit-role-assignments"></a>Wyświetlanie lub edytowanie przypisań ról

1. Przejdź do portalu Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) i zaloguj się.

2. W okienku nawigacji wybierz pozycję **Uprawnienia & ról**, a następnie w obszarze **Azure AD** wybierz pozycję **Role**.

3. Wybierz jedną z następujących ról, aby otworzyć okienko boczne:

   - Administrator globalny
   - Administrator zabezpieczeń
   - Czytelnik zabezpieczeń

   > [!IMPORTANT]
   > Firma Microsoft zaleca udzielanie użytkownikom dostępu tylko do tego, czego potrzebują do wykonywania swoich zadań. Nazywamy to pojęcie *najmniejszym uprawnieniem* dla uprawnień. Aby dowiedzieć się więcej, zobacz [Best practices for least-privileged access for applications (Najlepsze rozwiązania dotyczące dostępu z najniższymi uprawnieniami dla aplikacji](/azure/active-directory/develop/secure-least-privileged-access)). 

4. W okienku bocznym wybierz link **Zarządzanie członkami w usłudze Azure AD** . Ta akcja powoduje przejście do Azure Active Directory (Azure AD), w której można wyświetlać przypisania ról i zarządzać nimi.

5. Wybierz użytkownika, aby otworzyć swój profil, a następnie wybierz pozycję **Przypisane role**.

   - Aby dodać rolę, wybierz pozycję **+ Dodaj przypisania**.
   - Aby usunąć rolę, wybierz pozycję **X Usuń przypisania**. 

## <a name="need-to-add-users"></a>Chcesz dodać użytkowników?

Jeśli nie dodano jeszcze użytkowników do subskrypcji, zobacz [Dodawanie użytkowników i przypisywanie licencji w tym samym czasie](mdb-add-users.md).

## <a name="next-steps"></a>Następne kroki

Przejdź do:

- [Krok 3. Konfigurowanie powiadomień e-mail](mdb-email-notifications.md)
- [Krok 4. Dołączanie urządzeń do Microsoft Defender dla Firm](mdb-onboard-devices.md)