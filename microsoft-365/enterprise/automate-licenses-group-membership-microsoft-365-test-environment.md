---
title: Automatyzowanie licencjonowania i członkostwa w grupach dla Microsoft 365 dla środowiska testowego przedsiębiorstwa
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 12/09/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection: M365-identity-device-management
ms.custom:
- TLG
- Ent_TLGs
description: Skonfiguruj licencjonowanie oparte na grupach i dynamiczne członkostwo w grupach w Microsoft 365 dla środowiska testowego przedsiębiorstwa.
ms.openlocfilehash: 1d471076ac07acb023cdf785233ea2222690b596
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65097541"
---
# <a name="automate-licensing-and-group-membership-for-your-microsoft-365-for-enterprise-test-environment"></a>Automatyzowanie licencjonowania i członkostwa w grupach dla Microsoft 365 dla środowiska testowego przedsiębiorstwa

*Tego przewodnika laboratorium testowego można używać tylko w przypadku Microsoft 365 dla środowisk testowych przedsiębiorstwa.*

Licencjonowanie oparte na grupach automatycznie przypisuje lub usuwa licencje dla konta użytkownika na podstawie członkostwa w grupie. Dynamiczne członkostwo w grupie dodaje lub usuwa członków do grupy na podstawie właściwości konta użytkownika, takich jak **Dział** lub **Kraj**. W tym artykule przedstawiono pokazy dodawania i usuwania członków grupy w Microsoft 365 dla środowiska testowego przedsiębiorstwa.

Konfigurowanie automatycznego licencjonowania i dynamicznego członkostwa w grupach w Microsoft 365 dla środowiska testowego przedsiębiorstwa obejmuje dwie fazy:

- [Faza 1. Tworzenie Microsoft 365 dla środowiska testowego przedsiębiorstwa](#phase-1-build-out-your-microsoft-365-for-enterprise-test-environment)
- [Faza 2. Konfigurowanie i testowanie dynamicznego członkostwa w grupach oraz automatycznego licencjonowania](#phase-2-configure-and-test-dynamic-group-membership-and-automatic-licensing)

![Przewodniki laboratorium testowego dla chmury firmy Microsoft.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png) 
    
> [!TIP]
> Aby uzyskać wizualną mapę na wszystkie artykuły w stosie przewodnika Microsoft 365 dla laboratorium testowego dla przedsiębiorstw, przejdź do [Microsoft 365 stosu przewodników laboratorium testowego dla przedsiębiorstw](../downloads/Microsoft365EnterpriseTLGStack.pdf).
  
## <a name="phase-1-build-out-your-microsoft-365-for-enterprise-test-environment"></a>Faza 1. Tworzenie Microsoft 365 dla środowiska testowego przedsiębiorstwa

Jeśli chcesz przetestować tylko automatyczne licencjonowanie i członkostwo w grupie w sposób uproszczony z minimalnymi wymaganiami, postępuj zgodnie z instrukcjami w temacie [Uproszczona konfiguracja podstawowa](lightweight-base-configuration-microsoft-365-enterprise.md).
  
Jeśli chcesz przetestować automatyczne licencjonowanie i członkostwo w grupie w symulowanym przedsiębiorstwie, postępuj zgodnie z instrukcjami w temacie [Uwierzytelnianie przekazywane](pass-through-auth-m365-ent-test-environment.md).
  
> [!NOTE]
> Testowanie automatycznego licencjonowania i członkostwa w grupach nie wymaga symulowanego środowiska testowego przedsiębiorstwa, które obejmuje symulowany intranet połączony z Internetem i synchronizację katalogów dla lasu Active Directory Domain Services (AD DS). Jest ona dostępna tutaj jako opcja, dzięki czemu można przetestować automatyczne licencjonowanie i członkostwo w grupie i eksperymentować z nim w środowisku reprezentującym typową organizację.
  
## <a name="phase-2-configure-and-test-dynamic-group-membership-and-automatic-licensing"></a>Faza 2. Konfigurowanie i testowanie dynamicznego członkostwa w grupach oraz automatycznego licencjonowania

Najpierw utwórz nową grupę o nazwie Sales i dodaj regułę członkostwa w grupie dynamicznej, aby konta użytkowników **z działem** ustawione na **Sales** automatycznie dołączyły do grupy Sales.

1. W prywatnym wystąpieniu przeglądarki internetowej zaloguj się do [Centrum administracyjne platformy Microsoft 365](https://admin.microsoft.com) przy użyciu konta administratora globalnego subskrypcji laboratorium testowego Microsoft 365 E5.
2. Na osobnej karcie przeglądarki przejdź do Azure Portal pod adresem [https://portal.azure.com](https://portal.azure.com).
3. W Azure Portal wprowadź **grupy** w polu wyszukiwania, a następnie wybierz pozycję **Grupy**.
4. W okienku **Wszystkie grupy** wybierz pozycję **Nowa grupa**.
5. W **obszarze Typ grupy** wybierz pozycję **Microsoft 365**.
6. W **polu Nazwa grupy** wprowadź **sales (Sprzedaż**).
7. W **obszarze Typ członkostwa** wybierz pozycję **Użytkownik dynamiczny**.
8. Wybierz pozycję **Dynamiczni członkowie użytkownika**.
9. W okienku **Dynamiczne reguły członkostwa** : 
   - Wybierz właściwość **działu** .
   - Wybierz operator **Równości** .
   - W polu **Wartość** **wprowadź** Wartość.
10. Wybierz **Zapisz**.
11. Wybierz pozycję **Utwórz**.

Następnie skonfiguruj grupę Sales, aby członkowie mogli automatycznie przypisać licencję Microsoft 365 E5.

1. Wybierz grupę **Sprzedaż** , a następnie wybierz pozycję **Licencje**.
2. W okienku **Aktualizowanie przypisań licencji** wybierz pozycję **Microsoft 365 E5**, a następnie wybierz pozycję **Zapisz**.
3. W przeglądarce zamknij kartę Azure Portal.

Następnie przetestuj dynamiczne członkostwo w grupach i automatyczne licencjonowanie na koncie użytkownika 4:

1. Na karcie **Microsoft Office Narzędzia** główne w przeglądarce wybierz pozycję **Administrator**.
2. Na karcie **Centrum administracyjne platformy Microsoft 365** wybierz pozycję **Aktywni użytkownicy**.
3. Na stronie **Aktywni użytkownicy** wybierz konto **Użytkownika 4** .
4. W okienku **Użytkownik 4** wybierz pozycję **Edytuj** dla **pozycji Licencje produktów**.
5. W okienku **Licencje produktów** wyłącz licencję **Microsoft 365 E5**, a następnie wybierz pozycję **SaveClose** > .
6. We właściwościach konta użytkownika 4 sprawdź, czy nie przypisano żadnych licencji produktów i nie ma członkostwa w grupach.
7. W obszarze **Informacje kontaktowe** wybierz pozycję **Edytuj**.
8. W okienku **Edytowanie informacji kontaktowych** wybierz pozycję **Informacje kontaktowe**.
9. W polu **Dział** wprowadź pozycję **Sprzedaż**, a następnie wybierz pozycję **SaveClose** > .
10. Poczekaj kilka minut, a następnie okresowo wybieraj ikonę **Odśwież** w prawym górnym rogu okienka Konta użytkownika 4.

Z czasem powinny zostać wyświetlone następujące elementy:

- **Właściwość Członkostwa w grupach** została zaktualizowana o grupę **Sales** .
- **Właściwość licencji produktów** została zaktualizowana przy użyciu licencji **Microsoft 365 E5**.

Zobacz następujące artykuły, aby wdrożyć dynamiczne członkostwo w grupach i automatyczne licencjonowanie w środowisku produkcyjnym:

- [Licencjonowanie oparte na grupach w Azure Active Directory](/azure/active-directory/fundamentals/active-directory-licensing-whatis-azure-portal)
- [Grupy dynamiczne w Azure Active Directory](/azure/active-directory/users-groups-roles/groups-create-rule)

## <a name="next-step"></a>Następny krok

Zapoznaj się z dodatkowymi funkcjami i możliwościami [tożsamości](m365-enterprise-test-lab-guides.md#identity) w środowisku testowym.

## <a name="see-also"></a>Zobacz też

[Wdrażanie tożsamości](deploy-identity-solution-overview.md)

[Microsoft 365 dla przewodników laboratorium testowego w przedsiębiorstwie](m365-enterprise-test-lab-guides.md)

[Microsoft 365 dla przedsiębiorstw — omówienie](microsoft-365-overview.md)

[Dokumentacja dotycząca subskrypcji Microsoft 365 dla Przedsiębiorstw](/microsoft-365-enterprise/)