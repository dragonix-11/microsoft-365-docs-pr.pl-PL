---
title: Przypisywanie ról i uprawnień w aplikacji Microsoft Defender dla Firm
description: Dowiedz się, jak przypisywać role i uprawnienia w aplikacji Microsoft Defender dla Firm
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 04/01/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: 33fb7548d2dbd231368a459cd58b9d50e7c4673e
ms.sourcegitcommit: 7aa2441c1f2cc5b4b5495d6fdb993e563f86647f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/04/2022
ms.locfileid: "64638251"
---
# <a name="assign-roles-and-permissions-in-microsoft-defender-for-business"></a>Przypisywanie ról i uprawnień w aplikacji Microsoft Defender dla Firm

> [!IMPORTANT]
> Microsoft Defender dla Firm jest wprowadzana u [klientów Microsoft 365 Business Premium](../../business-premium/index.md) począwszy od 1 marca 2022 r. Autonomiczna subskrypcja usługi Defender dla firm jest w wersji Preview i będzie stopniowo wprowadzana u klientów i partnerów IT, [](https://aka.ms/mdb-preview) którzy zarejestrują się tutaj, aby poprosić o to. Wersja Preview zawiera [początkowy zestaw scenariuszy](mdb-tutorials.md#try-these-preview-scenarios), a my będziemy regularnie dodawać funkcje.
> 
> Niektóre informacje w tym artykule dotyczą wstępnie dzierżawionych produktów/usług, które mogą zostać znacząco zmodyfikowane przed ich komercyjną premierą. Firma Microsoft nie udziela żadnych gwarancji, jawnych ani domniemanych, dotyczących podanych tutaj informacji. 

Aby wykonywać zadania w portalu Microsoft 365 Defender, takie jak konfigurowanie usługi Microsoft Defender dla Firm, wyświetlanie raportów lub podejmowanie działań dotyczących wykrytych zagrożeń, zespół zabezpieczeń musi mieć odpowiednie uprawnienia. Uprawnienia są udzielane za pośrednictwem ról przypisanych w portalu Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) lub w innych [Azure Active Directory](/azure/active-directory/roles/manage-roles-portal). 

## <a name="what-to-do"></a>Co należy zrobić

1. [Dowiedz się więcej o rolach w programie Defender dla firm](#roles-in-defender-for-business).

2. [Wyświetlaj i edytuj przypisania ról dla zespołu zabezpieczeń](#view-or-edit-role-assignments).

3. [Przejdź do następnych kroków](#next-steps).

>
> **Masz minutę?**
> Prosimy o <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">ankietę na temat Microsoft Defender dla Firm</a>. Chcemy ją usłyszeć!
>

## <a name="roles-in-defender-for-business"></a>Role w programie Defender dla firm

W poniższej tabeli opisano trzy role, które można przypisać w uchcie Defender dla firm. [Dowiedz się więcej o rolach administratorów](../../admin/add-users/about-admin-roles.md). <br/><br/>

| Poziom uprawnień | Opis |
|:---|:---|
| **Administratorzy globalni** (nazywani również administratorami globalnymi) <br/><br/> *Najlepszym rozwiązaniem jest ograniczenie liczby administratorów globalnych.* | Administratorzy globalni mogą wykonywać wszelkiego rodzaju zadania. Osoba, która załozyła konto w firmie w Microsoft 365 lub u Microsoft Defender dla Firm jest domyślnie administratorem globalnym. <br/><br/> Administratorzy globalni mogą uzyskać dostęp do ustawień oraz zmieniać je we wszystkich Microsoft 365 portalach, takich jak: <br/>- Centrum administracyjne platformy Microsoft 365 ([https://admin.microsoft.com](https://admin.microsoft.com)) <br/>- Microsoft 365 Defender portalu ([https://security.microsoft.com](https://security.microsoft.com)) |
| **Administratorzy** zabezpieczeń (nazywani również administratorami zabezpieczeń) | Administratorzy zabezpieczeń mogą wykonywać następujące zadania: <br/>— Wyświetlanie zasad zabezpieczeń i zarządzanie nimi <br/>— Wyświetlać zagrożenia zabezpieczeń i alerty oraz zarządzać nimi (działania te obejmują podejmowanie działań dotyczących punktów końcowych) <br/>— Wyświetlanie informacji dotyczących zabezpieczeń i raportów |
| **Czytelnik zabezpieczeń** | Czytniki zabezpieczeń mogą wykonywać następujące zadania: <br/>- Wyświetlanie zasad zabezpieczeń <br/>- Wyświetlanie zagrożeń bezpieczeństwa i alertów <br/>— Wyświetlanie informacji dotyczących zabezpieczeń i raportów  |


## <a name="view-or-edit-role-assignments"></a>Wyświetlanie i edytowanie przypisań ról

1. Przejdź do Microsoft 365 Defender konta ([https://security.microsoft.com](https://security.microsoft.com)) i zaloguj się.

2. W okienku nawigacji wybierz pozycję **Uprawnienia &**, a następnie w obszarze **Azure AD** wybierz pozycję **Role**.

3. Wybierz jedną z następujących ról, aby otworzyć jej okienko boczne:

   - Administrator globalny
   - Administrator zabezpieczeń
   - Czytelnik zabezpieczeń

   > [!IMPORTANT]
   > Firma Microsoft zaleca udzielanie osobom dostępu tylko do tego, co jest im potrzebne do wykonywania swoich zadań. To pojęcie jest *najbędszego poziomu uprawnień* . Aby dowiedzieć się więcej, [zobacz Najlepsze rozwiązania dotyczące najmniej uprzywilejowanych dostępu do aplikacji](/azure/active-directory/develop/secure-least-privileged-access). 

4. W okienku bocznym wybierz link **Zarządzaj członkami w usłudze Azure AD** . Ta akcja przenosi Cię do Azure Active Directory (Azure AD), gdzie możesz wyświetlać przypisania ról i zarządzać nimi.

5. Wybierz użytkownika, aby otworzyć jego profil, a następnie wybierz pozycję **Przypisane role**.

   - Aby dodać rolę, wybierz **pozycję + Dodaj zadania**.
   - Aby usunąć rolę, wybierz pozycję **X Usuń przypisania**. 

## <a name="need-to-add-users"></a>Chcesz dodać użytkowników?

Jeśli jeszcze nie dodano użytkowników do subskrypcji, zobacz Dodawanie użytkowników i [przypisywanie licencji jednocześnie](../../admin/add-users/add-users.md).

## <a name="next-steps"></a>Następne kroki

Przejdź do:

- [Krok 3. Konfigurowanie powiadomień e-mail](mdb-email-notifications.md)

- [Krok 4. Urządzenia na pokładzie, na których Microsoft Defender dla Firm](mdb-onboard-devices.md)