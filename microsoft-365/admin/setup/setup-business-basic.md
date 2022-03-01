---
title: Konfigurowanie Microsoft 365 Business Basic
f1.keywords:
- NOCSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: high
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
- Adm_O365_Setup
- TRN_SMB
ms.custom:
- TRN_M365B
- OKR_SMB_Videos
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- MET150
- MOE150
- BEA160
description: Dowiedz się, jak skonfigurować Microsoft 365 Business Basic subskrypcji.
ms.openlocfilehash: e7c616936f045bc4266c24b65342451ffeff43ef
ms.sourcegitcommit: 0ee2dabe402d44fecb6856af98a2ef7720d25189
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/09/2021
ms.locfileid: "62995976"
---
# <a name="set-up-microsoft-365-business-basic"></a>Konfigurowanie Microsoft 365 Business Basic

## <a name="watch-set-up-microsoft-365-business-basic"></a>Obejrzyj: Konfigurowanie Microsoft 365 Business Basic

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4vk3W]

Jeśli ten klip wideo okazał się przydatny, poznaj [kompletną serię szkoleń dla małych firm i nowych użytkowników usługi Microsoft 365](../../business-video/index.yml).

## <a name="add-your-domain-to-personalize-sign-in"></a>Dodawanie domeny w celu spersonalizowania logowania

Podczas zakupu Microsoft 365 Business Basic masz możliwość używania domeny, która należy do Ciebie, lub kupowania jej podczas rejestracji.

- Jeśli podczas rejestracji w domenie kupiono nową domenę, to jest ona w ogóle ustawiona. Możesz przejść do dodawania użytkowników i [przypisywania licencji](#add-users-and-assign-licenses).

 ::: moniker range="o365-worldwide"

1. Przejdź do centrum administracyjnego w stronie <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a>.

::: moniker-end

::: moniker range="o365-21vianet"

1. Przejdź do centrum administracyjnego w stronie <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">https://portal.partner.microsoftonline.cn</a>.

::: moniker-end 

2. Wybierz **pozycję Przejdź do konfiguracji,** aby uruchomić kreatora.
    
3. W kroku **Dodaj domenę** wprowadź nazwę domeny, której chcesz użyć (na przykład contoso.com).

    > [!IMPORTANT]
    > Jeśli podczas rejestracji zakupiono domenę, nie zobaczysz tutaj kroku **Dodaj** domenę. Zamiast tego [przejdź do przycisku Dodaj użytkowników](#add-users-and-assign-licenses) .

    
4. Postępuj zgodnie z instrukcjami kreatora, aby utworzyć rekordy DNS u dowolnego dostawcy [hostingu DNS](/office365/admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider) dla Office 365, który potwierdza, że jesteś właścicielem domeny. Jeśli znasz hosta domeny, zobacz też [Dodawanie domeny do](/microsoft-365/admin/setup/add-domain) Microsoft 365.

    Jeśli Twój dostawca hostingu to Firma GoDaddy lub inny host z włączonym nawiązywaniem połączenia z domeną [, ten](/office365/admin/get-help-with-domains/domain-connect) proces jest łatwy i zostanie automatycznie poproszony o zalogowanie się i uwierzytelnienie firmy Microsoft w Twoim imieniu.

    ![Na stronie Potwierdzanie dostępu w daddy wybierz pozycję Autoryzuj.](../../media/godaddyauth.png)

## <a name="add-users-and-assign-licenses"></a>Dodawanie użytkowników i przypisywanie licencji

Użytkowników można dodać w kreatorze, ale można też [dodać](../add-users/add-users.md) ich później w centrum administracyjnym. Ponadto, jeśli masz lokalny kontroler domeny, możesz dodawać użytkowników z [usługą Azure AD Połączenie](/azure/active-directory/hybrid/how-to-connect-install-express).

## <a name="add-users-in-the-wizard"></a>Dodawanie użytkowników w kreatorze

Każdy użytkownik, który dodasz w kreatorze, automatycznie otrzyma licencję Microsoft 365 Business Basic licencji.

1. Jeśli Twoja subskrypcja Microsoft 365 Business Basic ma już użytkowników (na przykład jeśli używasz usługi Azure AD Połączenie), możesz teraz przypisać im licencje. Możesz dodać licencje dla tych użytkowników.

2. Po dodaniu użytkowników zostanie również dodana opcja udostępnienia poświadczeń nowym użytkownikom. Możesz wydrukować te informacje, wysłać je pocztą e-mail lub pobrać.

## <a name="connect-your-domain"></a>Łączenie domeny

> [!NOTE]
> Jeśli do skonfigurowania użytkowników wybrano domenę .onmicrosoft lub do skonfigurowania użytkowników była używana usługa Azure AD Połączenie, ten krok nie zostanie wyświetlony.
  
Aby skonfigurować usługi, musisz zaktualizować niektóre rekordy na swoim hoście DNS lub u rejestratora domen.
  
1. Kreator konfiguracji zwykle wykrywa rejestratora i udostępnia linki do instrukcji krok po kroku dotyczących aktualizowania rekordów serwera nazw w witrynie internetowej rejestratora. Jeśli tak się nie stanie, zmień serwery nazw, aby Office 365 [u dowolnego rejestratora domen](../get-help-with-domains/change-nameservers-at-any-domain-registrar.md). 

    - Jeśli masz istniejące rekordy DNS, na przykład istniejącą witrynę internetową, ale dla Twojego hosta DNS włączono łączenie [domen, wybierz](/office365/admin/get-help-with-domains/domain-connect) pozycję **Dodaj rekordy**. Na stronie **Wybierz usługi online** zaakceptuj wszystkie ustawienia domyślne, wybierz pozycję **Dalej, a** następnie wybierz pozycję **Autoryzuj** na stronie swojego hosta DNS.
    - Jeśli masz istniejące rekordy DNS z innymi hostami DNS (bez włączonego łączenia domen), chcieć zarządzać własnymi rekordami DNS, aby upewnić się, że istniejące usługi pozostają połączone. Aby [uzyskać więcej informacji, zobacz](/office365/admin/get-help-with-domains/dns-basics) Podstawowe informacje o domenie.

2. Postępuj zgodnie z instrukcjami kreatora, aby skonfigurować pocztę e-mail i inne usługi.

    Po zakończeniu procesu tworzenia konta zostaniesz przekierowyny do centrum administracyjnego, w którym możesz dodawać użytkowników i przypisywać licencje. Po ukończeniu konfiguracji początkowej możesz użyć strony Konfiguracja w centrum  administracyjnym, aby kontynuować konfigurowanie usług oferowanych w ramach subskrypcji.

    Aby uzyskać więcej informacji na temat kreatora konfiguracji i strony **Konfiguracja centrum** administracyjnego, zobacz Różnice między kreatorem [konfiguracji a stroną Konfiguracja](o365-setup-wizard-and-setup-page.md).