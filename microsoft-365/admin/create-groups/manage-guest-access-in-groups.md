---
title: Zarządzanie dostępem gości w Microsoft 365 grup
ms.reviewer: arvaradh
f1.keywords: NOCSH
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
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
search.appverid:
- MET150
- MOE150
ms.assetid: 9de497a9-2f5c-43d6-ae18-767f2e6fe6e0
description: Dowiedz się, jak dodawać gości do grupy Microsoft 365, wyświetlać gości i kontrolować dostęp gości za pomocą programu PowerShell.
ms.openlocfilehash: ea5986c4b9e0c5124abc581f9ed35391e0885633
ms.sourcegitcommit: 7aa2441c1f2cc5b4b5495d6fdb993e563f86647f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/04/2022
ms.locfileid: "64637945"
---
# <a name="manage-guest-access-in-microsoft-365-groups"></a>Zarządzanie dostępem gości w Microsoft 365 grup

Domyślnie dostęp gości do grup Microsoft 365 jest włączony dla organizacji. Administratorzy mogą sterować tym, czy zezwolić na dostęp gości do grup w całej organizacji, czy dla poszczególnych grup.

Gdy jest włączona, członkowie grupy mogą zapraszać gości do grupy Microsoft 365 za pośrednictwem Outlook sieci Web. Zaproszenia są wysyłane do właściciela grupy w celu zatwierdzenia.

Po zatwierdzeniu gość jest dodawany do katalogu i grupy.

> [!Note]
> Yammer Enterprise sieci, które są w trybie natywnym lub [geolokalizacji](/yammer/manage-security-and-compliance/manage-data-compliance) UE, nie obsługują gości sieci.
> Microsoft 365 połączone Yammer nie obsługują obecnie dostępu gości, ale możesz tworzyć niepołączono, zewnętrzne grupy w twojej Yammer sieci. Aby [uzyskać instrukcje,](/yammer/work-with-external-users/create-and-manage-external-groups) zobacz Tworzenie grup zewnętrznych Yammer i zarządzanie nimi.

Dostęp gości w grupach jest często używany jako część szerszego scenariusza, który obejmuje SharePoint lub Teams. Te usługi mają własne ustawienia udostępniania gościa. Aby uzyskać pełne instrukcje dotyczące konfigurowania udostępniania gości w grupach, grupach SharePoint i Teams, zobacz:

- [Współpraca z gośćmi w witrynie](../../solutions/collaborate-in-site.md)
- [Współpraca z gośćmi w zespole](../../solutions/collaborate-as-team.md)

## <a name="manage-groups-guest-access"></a>Zarządzanie dostępem gości do grup

Jeśli chcesz włączyć lub wyłączyć dostęp gościa w grupach, możesz to zrobić w <a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank">**grupach**</a>.

1. W centrum administracyjnym przejdź do pozycji **Pokaż wszystkie** \>  \> ustawienia Ustawienia organizacji i na karcie Usługi <a href="https://go.microsoft.com/fwlink/p/?linkid=2053743" target="_blank"></a>**wybierz pozycję Grupy Microsoft 365**.
  
2. Na stronie **Grupy Microsoft 365** grupy określ, czy osoby spoza organizacji mają mieć dostęp do zasobów grupy, czy właściciele grup mogą dodawać do grup osoby spoza organizacji.

## <a name="add-guests-to-a-microsoft-365-group-from-the-admin-center"></a>Dodawanie gości do grupy Microsoft 365 z centrum administracyjnego

Jeśli gość już istnieje w katalogu, możesz dodać go do swoich grup <a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank">z Centrum administracyjne platformy Microsoft 365.</a> Grupy z dynamicznym członkostwem muszą być [zarządzane w Azure Active Directory](/azure/active-directory/enterprise-users/groups-create-rule)).
  
1. W centrum administracyjnym przejdź do pozycji <a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank">**GrupyGrupy**</a> > .
  
2. Kliknij grupę, do której chcesz dodać gościa, a następnie na karcie **Członkowie** **wybierz pozycję Wyświetl** wszystkich członków i zarządzaj nimi. 
  
4. Wybierz **pozycję Dodaj** członków, a następnie wybierz imię i nazwisko gościa, którego chcesz dodać.
    
5. Wybierz **Zapisz**.

Jeśli chcesz dodać gościa bezpośrednio do katalogu, możesz dodać Azure Active Directory użytkowników do współpracy [B2B w](/azure/active-directory/b2b/add-users-administrator) Azure Portal.

Jeśli chcesz edytować dowolne informacje o gościu, możesz dodać lub zaktualizować informacje w profilu użytkownika przy użyciu [Azure Active Directory.](/azure/active-directory/fundamentals/active-directory-users-profile-azure-portal)

## <a name="related-content"></a>Zawartość pokrewna

[Blokowanie gości z określonej grupy](../../solutions/per-group-guest-access.md) (artykuł)\
[Zarządzanie członkostwem w grupach w Centrum administracyjne platformy Microsoft 365](add-or-remove-members-from-groups.md) (artykuł)\
[Azure Active Directory recenzji dostępu](/azure/active-directory/active-directory-azure-ad-controls-perform-access-review) (artykuł)\
[Set-AzureADUser](/powershell/module/azuread/set-azureaduser) (artykuł)
