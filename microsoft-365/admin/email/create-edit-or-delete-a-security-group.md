---
title: Tworzenie, edytowanie lub usuwanie grupy zabezpieczeń w centrum administracyjne platformy Microsoft 365
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
- admindeeplinkMAC
- admindeeplinkEXCHANGE
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 55c96b32-e086-4c9e-948b-a018b44510cb
description: Dowiedz się, jak tworzyć, edytować lub usuwać grupę zabezpieczeń.
ms.openlocfilehash: 3f054842abc5111c654b8da02afc418c36f7db11
ms.sourcegitcommit: b1066b2a798568afdea9c09401d52fa38fe93546
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/13/2021
ms.locfileid: "63017756"
---
# <a name="create-edit-or-delete-a-security-group-in-the-microsoft-365-admin-center"></a>Tworzenie, edytowanie lub usuwanie grupy zabezpieczeń w centrum administracyjne platformy Microsoft 365

Na stronie Microsoft 365 grupy można tworzyć  grupy kont użytkowników, przy użyciu których można przypisywać te same uprawnienia w usługach SharePoint Online i CRM Online. Na przykład administrator może utworzyć grupę zabezpieczeń, aby udzielić określonej grupie osób dostępu do witryny SharePoint sieci Web. Tylko administratorzy globalni i administratorzy zarządzający użytkownikami mają uprawnienia do tworzenia, edytowania i usuwania grup zabezpieczeń. Aby uzyskać więcej informacji o rolach administratorów, zobacz [Przypisywanie ról administratora](../add-users/assign-admin-roles.md). 
  
Istnieją również [Grupy w usłudze Exchange Online i SharePoint Online](#groups-in-exchange-online-and-sharepoint-online), których można użyć do wysyłania wiadomości e-mail lub przypisywania uprawnień do grupy użytkowników, oraz [Grupy w usłudze Exchange Online i SharePoint Online](#groups-in-exchange-online-and-sharepoint-online), które udzielają użytkownikom uprawnień oraz dostępu do witryn i zbiorów witryn. 
  
> [!IMPORTANT]
>  Planujesz korzystać ze skrzynek pocztowych witryn? Wszyscy użytkownicy, których dodano do witryny programu SharePoint za pośrednictwem grupy zabezpieczeń, a nie pojedynczo, mogą korzystać tylko ze skrzynki pocztowej witryny z programu SharePoint. Ci użytkownicy nie będą mogli uzyskać dostępu do skrzynki pocztowej witryny z programu Outlook. Aby uzyskać więcej informacji, zobacz [Używanie grup Microsoft 365 zamiast skrzynek pocztowych witryny](https://support.microsoft.com/office/737d6b1f-67cc-41fe-8db8-f2d09dd1673b). 
  
## <a name="manage-security-groups-in-the-admin-center"></a>Zarządzanie grupami zabezpieczeń w centrum administracyjnym

### <a name="add-a-security-group"></a>Dodawanie grupy zabezpieczeń

1. W centrum administracyjne platformy Microsoft 365 przejdź do **strony Grupygrup** > .<a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank"></a>
  
2. Na stronie **Grupy** wybierz pozycję **Dodaj grupę**.
    
3. Na **stronie Wybierz typ grupy** wybierz pozycję **Zabezpieczenia**. 
    
4. Postępuj zgodnie z instrukcjami, aby ukończyć tworzenie grupy. 
 
### <a name="add-members-to-a-security-group"></a>Dodawanie członków do grupy zabezpieczeń
    
1. Wybierz nazwę grupy zabezpieczeń na stronie **Grupy** , a następnie na **karcie Członkowie** wybierz pozycję **Wyświetl wszystkich członków i zarządzaj nimi**. 
    
2. W okienku grupy wybierz pozycję  Dodaj członków i wybierz osobę z listy lub wpisz nazwisko osoby, którą chcesz dodać, w polu Wyszukaj, a następnie  wybierz pozycję **Zapisz**.
    
    Aby usunąć członków, wybierz znak X obok jego imienia i nazwiska. 
  
### <a name="edit-a-security-group"></a>Edytowanie grupy zabezpieczeń

1. W centrum administracyjnym przejdź do strony **Grupy** \> grupy.<a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank"></a>
  
2. Na **stronie Grupy** wybierz nazwę grupy. 
    
3. W okienku ustawień wybierz **kartę** Ogólne **lub Członkowie,** aby edytować szczegóły grupy lub członków.

### <a name="delete-a-security-group"></a>Usuwanie grupy zabezpieczeń

1. W centrum administracyjnym przejdź do **strony** <a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank">GrupyGrupy</a> > .
    
2. Na **stronie Grupy** wybierz nazwę grupy. 
    
3. Wybierz **pozycję Usuń grupę** (ikona wasetbin), a następnie potwierdź, wybierając pozycję **Usuń**.
    
    Po **usunięciu** grupy wybierz pozycję Zamknij. 
    
## <a name="groups-in-exchange-online-and-sharepoint-online"></a>Grupy w usłudze Exchange Online i SharePoint Online

Jeśli chcesz utworzyć grupy użytkowników, aby wysyłać do nich wszystkich jednocześnie wiadomości e-mail,  możesz to \> zrobić w centrum administracyjnym usługi Exchange, przechodząc do pozycji Administrator **Exchange** \>  \> grupy <a href="https://go.microsoft.com/fwlink/?linkid=2183233" target="_blank">**adresatów**</a>. Następnie wybierz **pozycję NewAdd**![ i](../../media/328ffb57-5f31-430a-b653-4a6b8e76d338.png) wybierz rodzaj grupy, którą chcesz utworzyć: 
  
- **Grupa dystrybucyjna**: służy do rozpowszechniania wiadomości w grupie użytkowników. Nazywana jest także grupą dystrybucyjną z  *obsługą* poczty lub  *listą dystrybucyjną*. Aby uzyskać więcej informacji, zobacz [Zarządzanie grupami dystrybucyjnmi](/exchange/recipients-in-exchange-online/manage-distribution-groups/manage-distribution-groups).
    
- **Grupa zabezpieczeń**: może być używana do rozpowszechniania wiadomości w grupie użytkowników lub do udzielania uprawnień dostępu do zasobów. Ta grupa jest także nazywana grupą zabezpieczeń *z obsługą poczty*. Aby uzyskać więcej informacji, zobacz [Zarządzanie grupami zabezpieczeń z obsługą poczty](/Exchange/recipients/mail-enabled-security-groups).
    
- **Grupa dynamicznej dystrybucji**: typ grupy dystrybucyjnej, której lista adresatów jest ponownie obliczana po każdym wysłaniu wiadomości na podstawie zdefiniowanych filtrów i warunków. Aby uzyskać więcej informacji, zobacz [Zarządzanie dynamicznymi grupami dystrybucyjnym](/Exchange/recipients/dynamic-distribution-groups/dynamic-distribution-groups).
    
Po utworzeniu grup dystrybucyjnych i grup zabezpieczeń z obsługą poczty w centrum administracyjnym programu <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange</a> ich nazwy i listy użytkowników są wyświetlane na **stronie Grupy** zabezpieczeń. Te grupy można usunąć w obu lokalizacjach, jednak edytować je można tylko w centrum administracyjnym programu Exchange. Dynamiczne grupy dystrybucyjne nie są wyświetlane na **stronie Grupy zabezpieczeń** . 
  
 Grupy programu SharePoint są tworzone automatycznie podczas tworzenia zbioru witryn. Te grupy domyślne używają domyślnych poziomów uprawnień w programie SharePoint  nazywanych czasem rolami programu SharePoint  do udzielania użytkownikom praw i dostępu. Aby uzyskać więcej informacji, [zobacz Domyślne grupy SharePoint w u SharePoint Online](/sharepoint/default-sharepoint-groups).
  
## <a name="how-is-a-security-group-different-from-security-groups-i-create-in-sharepoint"></a>Czym różni się grupa zabezpieczeń od grup zabezpieczeń tworzyć je w aplikacji SharePoint?

Grup zabezpieczeń można używać z SharePoint, Exchange, MDM, Windows i nie tylko. Grupa zabezpieczeń tworzyć w SharePoint jest rozpoznawana tylko przez ten SharePoint witryn.
  
## <a name="do-i-have-to-use-security-groups-for-my-organization-to-be-secure"></a>Czy muszę używać grup zabezpieczeń, aby moja organizacja była bezpieczna?

L.p. Jest to jeszcze jeden sposób na zarządzanie zabezpieczeniami organizacji. Zawsze możesz przyznać uprawnienia użytkownika i dostęp do witryn pojedynczo. Jednak dzięki grupom zabezpieczeń możesz łatwo zarządzać większymi grupami użytkowników.
  
## <a name="can-i-send-email-to-a-security-group"></a>Czy mogę wysyłać wiadomości e-mail do grupy zabezpieczeń?

Tak. Jeśli jednak chcesz używać grup do współpracy i poczty e-mail, zalecamy utworzenie grupy Microsoft 365 [grupy](../create-groups/create-groups.md). 

## <a name="related-content"></a>Zawartość pokrewna

[Tworzenie grupy w centrum administracyjne platformy Microsoft 365](../create-groups/create-groups.md) (artykuł)\
[Objaśnienie Microsoft 365 grup użytkownikom](../create-groups/explain-groups-knowledge-worker.md) (artykuł)\
[Zarządzanie grupą w centrum administracyjne platformy Microsoft 365](../create-groups/manage-groups.md) (artykuł)