---
title: Przypisywanie ról i uprawnień w programie Microsoft Defender dla firm (wersja Preview)
description: Dowiedz się, jak przypisywać role i uprawnienia w programie Microsoft Defender dla firm (wersja Preview)
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 02/07/2022
ms.prod: m365-security
ms.technology: mdb
localization_priority: Normal
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: 134b5ec8bcd390cc7f7908a09be5c2d1bd85169c
ms.sourcegitcommit: 4c207a9bdbb6c8ba372ae37907ccefca031a49f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2022
ms.locfileid: "63027032"
---
# <a name="assign-roles-and-permissions-in-microsoft-defender-for-business-preview"></a>Przypisywanie ról i uprawnień w programie Microsoft Defender dla firm (wersja Preview)

> [!IMPORTANT]
> Usługa Microsoft Defender dla firm jest teraz w wersji Preview i będzie stopniowo wprowadzana u klientów i partnerów IT, którzy zarejestrują się tutaj [, aby](https://aka.ms/mdb-preview) poprosić o to. W najbliższych tygodniach nawiązemy wstępną ofertę klientów i partnerów oraz rozszerzymy jej wersja zapoznawczą, aby rozszerzyć jej dostępność do ogólnej dostępności. Pamiętaj, że wersja Preview zostanie uruchamiana z [początkowym zestawem scenariuszy](mdb-tutorials.md#try-these-preview-scenarios), a funkcje będą regularnie dodajemy.
> 
> Niektóre informacje w tym artykule dotyczą wstępnie dzierżawionych produktów/usług, które mogą zostać znacząco zmodyfikowane przed ich komercyjną premierą. Firma Microsoft nie udziela żadnych gwarancji, jawnych ani domniemanych, dotyczących podanych tutaj informacji. 

Aby można było wykonywać zadania w portalu usługi Microsoft 365 Defender, takie jak konfigurowanie programu Microsoft Defender dla firm (wersja Preview), wyświetlanie raportów lub podejmowanie działań dotyczących wykrytych zagrożeń, zespołowi zabezpieczeń należy przypisać odpowiednie uprawnienia. Uprawnienia są udzielane za pośrednictwem ról przypisanych w portalu Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) lub w innych [Azure Active Directory](/azure/active-directory/roles/manage-roles-portal). 

## <a name="what-to-do"></a>Co należy zrobić

1. [Dowiedz się więcej o rolach w programie Defender dla firm (wersja preview)](#roles-in-defender-for-business).

2. [Wyświetlaj i edytuj przypisania ról dla zespołu zabezpieczeń](#view-or-edit-role-assignments).

3. [Przejdź do następnych kroków](#next-steps).

>
> **Masz minutę?**
> Prosimy o <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">krótką ankietę na temat programu Microsoft Defender dla firm</a>. Chcemy ją usłyszeć!
>


## <a name="roles-in-defender-for-business"></a>Role w programie Defender dla firm

W poniższej tabeli opisano trzy role, które można przypisać w programie Defender dla firm (wersja Preview). [Dowiedz się więcej o rolach administratorów](../../admin/add-users/about-admin-roles.md). <br/><br/>

| Poziom uprawnień | Opis |
|:---|:---|
| **Administratorzy globalni** (nazywani również administratorami globalnymi) <br/><br/> *Najlepszym rozwiązaniem jest ograniczenie liczby administratorów globalnych.* | Administratorzy globalni mogą wykonywać wszelkiego rodzaju zadania. Osoba, która załozyła konto w organizacji w Microsoft 365 usługi Microsoft Defender dla firm (wersja Preview) jest domyślnie administratorem globalnym. <br/><br/> Administratorzy globalni mogą uzyskać dostęp do ustawień oraz zmieniać je we wszystkich Microsoft 365 portalach, takich jak: <br/>— centrum administracyjne platformy Microsoft 365 ([https://admin.microsoft.com](https://admin.microsoft.com)) <br/>- Microsoft 365 Defender portalu ([https://security.microsoft.com](https://security.microsoft.com)) |
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

## <a name="next-steps"></a>Następne kroki

Przejdź do:

- [Krok 3. Konfigurowanie powiadomień e-mail](mdb-email-notifications.md)

- [Krok 4. Na urządzeniach w programie Microsoft Defender dla firm (wersja Preview)](mdb-onboard-devices.md)