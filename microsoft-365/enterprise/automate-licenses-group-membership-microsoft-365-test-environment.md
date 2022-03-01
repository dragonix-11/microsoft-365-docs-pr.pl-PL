---
title: Automatyzowanie licencjonowania i członkostwa w grupach w Microsoft 365 testowania przedsiębiorstwa
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/09/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection: M365-identity-device-management
ms.custom:
- TLG
- Ent_TLGs
description: Konfigurowanie licencjonowania grupowego i dynamicznego członkostwa w grupach w Microsoft 365 testowania przedsiębiorstwa.
ms.openlocfilehash: cbf10436ded2fbdcbe34c2a0bfa15b0a70a30eeb
ms.sourcegitcommit: 6c57f1e90339d5a95c9e7875599dac9d3e032c3a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/04/2022
ms.locfileid: "63015943"
---
# <a name="automate-licensing-and-group-membership-for-your-microsoft-365-for-enterprise-test-environment"></a>Automatyzowanie licencjonowania i członkostwa w grupach w Microsoft 365 testowania przedsiębiorstwa

*Ten przewodnik laboratorium testowego może być używany tylko w Microsoft 365 testowych w przedsiębiorstwie.*

Licencjonowanie oparte na grupach automatycznie przypisuje lub usuwa licencje dla konta użytkownika na podstawie członkostwa w grupie. Dynamiczne członkostwo w grupach dodaje lub usuwa członków grupy na podstawie właściwości konta użytkownika, takich **jak Dział** lub **Kraj**. Ten artykuł zawiera kroki pokazów dodawania i usuwania członków grupy w środowisku testowania Microsoft 365 przedsiębiorstwa.

Konfigurowanie automatycznego licencjonowania i dynamicznego członkostwa w grupach w Microsoft 365 testowania przedsiębiorstwa składa się z dwóch etapów:

- [Etap 1. Tworzenie środowiska testowego Microsoft 365 przedsiębiorstwa](#phase-1-build-out-your-microsoft-365-for-enterprise-test-environment)
- [Etap 2. Konfigurowanie i testowanie dynamicznego członkostwa w grupach i licencjonowanie automatyczne](#phase-2-configure-and-test-dynamic-group-membership-and-automatic-licensing)

![Przewodniki laboratorium testowego dotyczące chmury firmy Microsoft.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png) 
    
> [!TIP]
> Aby uzyskać wizualną mapę do wszystkich artykułów w stosie przewodników laboratorium testowego Microsoft 365 dla przedsiębiorstw, przejdź do tematu Microsoft 365 — przewodnik laboratorium testowego w [przedsiębiorstwie](../downloads/Microsoft365EnterpriseTLGStack.pdf).
  
## <a name="phase-1-build-out-your-microsoft-365-for-enterprise-test-environment"></a>Etap 1. Tworzenie środowiska testowego Microsoft 365 przedsiębiorstwa

Jeśli chcesz przetestować w sposób podstawowy tylko automatyczne licencjonowanie i członkostwo w grupach przy minimalnych wymaganiach, postępuj zgodnie z instrukcjami w teście Konfiguracja podstawowa [podstawowa](lightweight-base-configuration-microsoft-365-enterprise.md).
  
Jeśli chcesz przetestować automatyczne licencjonowanie i członkostwo w grupach w symulowanym przedsiębiorstwie, postępuj zgodnie z instrukcjami w tece uwierzytelnianie [za pośrednictwem programu Pass-through](pass-through-auth-m365-ent-test-environment.md).
  
> [!NOTE]
> Testowanie automatycznego licencjonowania i członkostwa w grupach nie wymaga symulowanego środowiska testowania przedsiębiorstwa, które obejmuje symulowany intranet połączony z Internetem i synchronizację katalogów dla lasu Usługi domenowe w usłudze Active Directory (AD DS). Ta opcja jest dostępna jako opcja, która umożliwia testowanie automatycznego licencjonowania i członkostwa w grupach oraz eksperymentowanie z nim w środowisku reprezentującym typową organizację.
  
## <a name="phase-2-configure-and-test-dynamic-group-membership-and-automatic-licensing"></a>Etap 2. Konfigurowanie i testowanie dynamicznego członkostwa w grupach i licencjonowanie automatyczne

Najpierw utwórz nową grupę o nazwie Sprzedaż i dodaj regułę dynamicznego członkostwa w grupie, aby konta użytkowników z  działem ustawionym  na Sprzedaż automatycznie dołączały do grupy Sprzedaż.

1. W prywatnym wystąpieniu przeglądarki internetowej zaloguj się do usługi [centrum administracyjne platformy Microsoft 365](https://admin.microsoft.com) za pomocą konta administratora globalnego subskrypcji Microsoft 365 E5 laboratorium testowego.
2. Na osobnej karcie przeglądarki przejdź do portalu Azure Portal w witrynie [https://portal.azure.com](https://portal.azure.com).
3. W portalu Azure wpisz **grupy w** polu wyszukiwania, a następnie wybierz pozycję **Grupy**.
4. w **okienku Wszystkie** grupy wybierz pozycję **Nowa grupa**.
5. W **grupie typ** wybierz pozycję **Microsoft 365**.
6. W **polach Nazwa** grupy wprowadź **tekst Sprzedaż**.
7. W **grupie Typ członkostwa** wybierz pozycję **Użytkownik dynamiczny**.
8. Wybierz pozycję **Dynamic user members (Członkowie dynamicznych użytkowników**).
9. W **okienku Reguły członkostwa dynamicznego** : 
   - Wybierz **właściwość działu** .
   - Wybierz **operator Równa się** .
   - W **polu Wartość** wprowadź wartość **Sprzedaż**.
10. Wybierz **Zapisz**.
11. Wybierz pozycję **Utwórz**.

Następnie skonfiguruj grupę Sprzedaż tak, aby członkowie automatycznie przypisywali Microsoft 365 E5 sprzedaży.

1. Wybierz **grupę Sprzedaż** , a następnie wybierz **pozycję Licencje**.
2. W **okienku Aktualizowanie przypisań** **licencji wybierz pozycję** Microsoft 365 E5, a następnie wybierz pozycję **Zapisz**.
3. W przeglądarce zamknij kartę Azure Portal.

Następnie przetestuj dynamiczne członkostwo w grupach i automatyczne licencjonowanie na koncie użytkownika 4:

1. Na karcie **Microsoft Office** główne w przeglądarce wybierz pozycję **Administrator**.
2. Na karcie **centrum administracyjne platformy Microsoft 365** wybierz pozycję **Aktywni użytkownicy**.
3. Na stronie **Aktywni** użytkownicy wybierz konto **użytkownika 4** .
4. W **okienku Użytkownik 4** wybierz **pozycję Edytuj** **dla licencji produktu**.
5. W **okienku Licencje produktu** wyłącz **licencję produktu Microsoft 365 E5**, a następnie wybierz pozycję **ZapiszZamów** > .
6. We właściwościach konta użytkownika 4 sprawdź, czy nie przypisano żadnych licencji produktu i nie ma członkostwa w grupach.
7. W **przypadku informacji o kontakcie** wybierz pozycję **Edytuj**.
8. W **okienku Edytowanie informacji o kontakcie** wybierz pozycję **Informacje kontaktowe**.
9. W polu **Dział** wprowadź tekst **Sprzedaż**, a następnie wybierz pozycję **ZapiszZamówienie** > .
10. Poczekaj kilka minut, a następnie okresowo wybierz ikonę  Odśwież w prawym górnym rogu okienka Konta użytkownika 4.

Z czasem powinny zostać wyświetlony:

- **Właściwość członkostwa w grupach** zaktualizowana za pomocą **grupy** Sprzedaż.
- **Właściwość licencji produktu** zaktualizowana przy użyciu **Microsoft 365 E5** produktu.

Zobacz następujące artykuły dotyczące wdrażania dynamicznego członkostwa w grupach i automatycznego licencjonowania w środowisku produkcyjnym:

- [Licencjonowanie oparte na grupach w programie Azure Active Directory](/azure/active-directory/fundamentals/active-directory-licensing-whatis-azure-portal)
- [Grupy dynamiczne w Azure Active Directory](/azure/active-directory/users-groups-roles/groups-create-rule)

## <a name="next-step"></a>Następny krok

Poznaj [dodatkowe funkcje tożsamości](m365-enterprise-test-lab-guides.md#identity) i możliwości w środowisku testowym.

## <a name="see-also"></a>Zobacz też

[Wdrażanie tożsamości](deploy-identity-solution-overview.md)

[Microsoft 365 laboratorium testowego dla przedsiębiorstw](m365-enterprise-test-lab-guides.md)

[Omówienie Microsoft 365 dla przedsiębiorstw](microsoft-365-overview.md)

[Microsoft 365 dla przedsiębiorstw](/microsoft-365-enterprise/)