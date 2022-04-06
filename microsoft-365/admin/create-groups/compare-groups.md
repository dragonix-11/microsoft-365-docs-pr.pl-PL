---
title: Porównanie grup
ms.reviewer: arvaradh
f1.keywords: CSH
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: high
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- okr_smb
- AdminTemplateSet
- admindeeplinkMAC
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 758759ad-63ee-4ea9-90a3-39f941897b7d
description: Microsoft 365 grupy otrzymają grupową pocztę e-mail i udostępniony obszar roboczy na konwersacje, pliki i zdarzenia kalendarza, usługę Stream i usługę Planner.
ms.openlocfilehash: 72da8af8acd0725a5d7509b84f08e4220f7772d4
ms.sourcegitcommit: 33bc25167812b31c51cf096c728e3a5854e94f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2022
ms.locfileid: "64594714"
---
# <a name="compare-groups"></a>Porównanie grup

W <a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank">**sekcji Grupy**</a> na Centrum administracyjne platformy Microsoft 365 możesz tworzyć grupy tego typu i zarządzać nimi: 

- **Grupy Microsoft 365** są używane do współpracy między użytkownikami, zarówno z firmy, jak i spoza firmy. Obejmują one usługi współpracy, takie jak SharePoint i Planner.
- **Grupy dystrybucyjne** służą do wysyłania powiadomień e-mail do grupy osób.
- **Grupy zabezpieczeń** służą do udzielania dostępu do zasobów, takich jak witryny SharePoint sieci Web.
- **Grupy zabezpieczeń z obsługą poczty służą** do udzielania dostępu do zasobów, takich jak SharePoint, i powiadomień e-mail do tych użytkowników.
- **Udostępnione skrzynki pocztowe** są używane, gdy wiele osób potrzebuje dostępu do tej samej skrzynki pocztowej, na przykład do informacji firmowej lub adresu e-mail pomocy technicznej.
- **Dynamiczne grupy dystrybucyjne** są tworzone, aby przyspieszyć masową wysyłkę wiadomości e-mail i innych informacji w organizacji.

Niektóre grupy zezwalają na dynamiczne członkostwo lub pocztę e-mail.

||Grupy Microsoft 365|Grupy dystrybucyjne|Grupy zabezpieczeń|Grupy zabezpieczeń z obsługą poczty|Udostępnione skrzynki pocztowe|Dynamiczne grupy dystrybucyjne|
|:----|:----|:----|:----|:----|:----|:----|
|**Z obsługą poczty**|Tak|Tak|Nie|Tak|Tak|Tak|
|**Dynamiczne członkostwo w usłudze Azure AD**|Tak|Nie|Tak|Nie|Nie|Nie|

Wszystkich tych typów grup można używać razem z Power Automate.

## <a name="microsoft-365-groups"></a>Grupy Microsoft 365

Grupy Microsoft 365 są używane do współpracy między użytkownikami, zarówno z firmy, jak i spoza firmy. Wraz z Microsoft 365 grupy członkowie otrzymają grupową pocztę e-mail i udostępniony obszar roboczy na konwersacje, pliki i zdarzenia kalendarza, usługę Stream i usługę Planner.

Do grupy można dodawać osoby spoza organizacji, o ile administrator włączył tę [funkcję](manage-guest-access-in-groups.md). Można także zezwolić nadawcom zewnętrznym na wysyłanie wiadomości e-mail na adres e-mail grupy.

Grupy Microsoft 365 skonfigurować dynamiczne członkostwo w programie [Azure Active Directory](/azure/active-directory/users-groups-roles/groups-change-type), co pozwala na automatyczne dodawać lub usuwać członków grupy na podstawie atrybutów użytkowników, takich jak dział, lokalizacja, stanowisko itp.

Grupy Microsoft 365 można uzyskać do nich dostęp za pośrednictwem aplikacji mobilnych, takich Outlook dla systemu iOS i Outlook dla systemu Android.

Członkowie grupy mogą wysyłać wiadomości e-mail w imieniu grupy, jeśli [ta funkcja została włączona przez administratora](../../solutions/allow-members-to-send-as-or-send-on-behalf-of-group.md).

Grupy Microsoft 365 zagnieżdżania w innych grupach Grupy Microsoft 365 ani w grupach dystrybucyjnych ani zabezpieczeń.

Grupy Microsoft 365 można dodać do jednej z trzech grup usługi SharePoint (Właściciele, Członkowie lub Odwiedzający), aby nadać uprawnienia do witryny.

## <a name="distribution-groups"></a>Grupy dystrybucyjne

[Grupy dystrybucyjne](/exchange/recipients-in-exchange-online/manage-distribution-groups/manage-distribution-groups) służą do wysyłania powiadomień do grupy osób. Mogą one otrzymywać zewnętrzne wiadomości e-mail, jeśli ta funkcja została włączona przez administratora.

Grupy dystrybucyjne najlepiej sprawdzają się w sytuacjach, w których trzeba rozpowszechnić informacje wśród określonej grupy osób, na przykład „Osoby w budynku A” lub „Wszyscy w firmie Contoso”.

Grupy dystrybucyjne można [uaktualnić do Grupy Microsoft 365](../manage/upgrade-distribution-lists.md).

Grupy dystrybucyjne można dodawać do zespołu w programie Microsoft Teams, ale do grupy są dodawana tylko ich członkowie, a nie sama grupa.

Grupy Microsoft 365 nie mogą być członkami grup dystrybucyjnych.

## <a name="dynamic-distribution-groups"></a>Dynamiczne grupy dystrybucyjne 

[Dynamiczne grupy dystrybucyjne](/exchange/recipients-in-exchange-online/manage-dynamic-distribution-groups/manage-dynamic-distribution-groups) to grupy z obsługą poczty, które służą do wysyłania poczty do osób z określonymi atrybutami, takimi jak dział lub lokalizacja. Te atrybuty są definiowane w centrum administracyjnym Exchange a nie w usłudze Azure AD.

W przeciwieństwie do zwykłych grup dystrybucyjnych, które zawierają zdefiniowany zestaw członków, lista członkostwa dla dynamicznych grup dystrybucyjnych jest obliczana za każdym razem, gdy wiadomość zostanie wysłana do grupy, na podstawie zdefiniowanych filtrów i warunków. Gdy wiadomość e-mail jest wysyłana do dynamicznej grupy dystrybucyjnej, jest dostarczana do wszystkich adresatów w organizacji, które spełniają kryteria zdefiniowane dla tej grupy.

## <a name="security-groups"></a>Grupy zabezpieczeń

[Grupy zabezpieczeń](../email/create-edit-or-delete-a-security-group.md) służą do udzielania dostępu do zasobów Microsoft 365, takich jak SharePoint. Mogą one ułatwić administrowanie, ponieważ wystarczy administrować grupą, zamiast dodawać użytkowników do każdego zasobu oddzielnie.

Grupy zabezpieczeń mogą zawierać użytkowników lub urządzenia. Tworzenie grupy zabezpieczeń dla urządzeń może być używane na potrzeby usług zarządzania urządzeniami mobilnymi, takich jak usługa Intune.

Grupy zabezpieczeń można [skonfigurować na potrzeby członkostwa dynamicznego w usłudze Azure Active Directory](/azure/active-directory/users-groups-roles/groups-change-type), co umożliwia automatyczne dodawanie i usuwanie członków grupy lub urządzeń na podstawie atrybutów użytkowników, takich jak dział, lokalizacja lub tytuł, bądź atrybutów urządzeń, takich jak wersja systemu operacyjnego.

Grupy zabezpieczeń można dodawać do zespołu.

Grupy Microsoft 365 nie mogą być członkami grup zabezpieczeń.

## <a name="mail-enabled-security-groups"></a>Grupy zabezpieczeń z obsługą poczty

Grupy zabezpieczeń z obsługą poczty działają tak samo, jak zwykłe grupy zabezpieczeń, jednak nie można nimi zarządzać dynamicznie za pośrednictwem usługi Azure Active Directory i nie mogą zawierać urządzeń.

Umożliwiają one wysyłanie wiadomości e-mail do wszystkich członków grupy.

Grupy zabezpieczeń z obsługą poczty można dodawać do zespołu.

## <a name="shared-mailboxes"></a>Udostępnione skrzynki pocztowe

[Udostępnione skrzynki pocztowe](../email/create-a-shared-mailbox.md) są używane, gdy wiele osób potrzebuje dostępu do tej samej skrzynki pocztowej, na przykład do informacji firmowej, adresu e-mail pomocy technicznej, recepcji lub w przypadku innej funkcji, którą może pełnić wiele osób.

Udostępnione skrzynki pocztowe mogą otrzymywać zewnętrzne wiadomości e-mail, jeśli administrator włączył tę funkcję.

Udostępnione skrzynki pocztowe zawierają kalendarz, który może być używany do współpracy.

Użytkownicy z uprawnieniami do skrzynki pocztowej grupy mogą wysyłać jako lub w imieniu adresu e-mail skrzynki pocztowej, jeśli administrator nadał mu odpowiednie uprawnienia. Jest to szczególnie przydatne w przypadku pomocy i obsługi skrzynek pocztowych, ponieważ użytkownicy mogą wysyłać wiadomości e-mail z witryny "Pomoc techniczna Contoso" lub "Budowanie recepcji".

Nie jest możliwe migrowanie udostępnionej skrzynki pocztowej do Microsoft 365 grupy.

## <a name="related-content"></a>Zawartość pokrewna

[Dowiedz się więcej o Grupy Microsoft 365](https://support.microsoft.com/office/b565caa1-5c40-40ef-9915-60fdb2d97fa2)

[Uaktualnianie list dystrybucyjnych do Grupy Microsoft 365 w Outlook](/microsoft-365/admin/manage/upgrade-distribution-lists)

[Dlaczego należy uaktualnić listy dystrybucyjne do grup w programie Outlook](https://support.microsoft.com/office/7fb3d880-593b-4909-aafa-950dd50ce188)
