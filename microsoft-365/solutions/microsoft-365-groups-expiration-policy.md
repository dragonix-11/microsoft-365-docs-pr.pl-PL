---
title: Microsoft 365 wygasania grupy
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
- m365solution-collabgovernance
search.appverid:
- MET150
recommendations: false
description: Dowiedz się Microsoft 365 zasad wygasania grup.
ms.openlocfilehash: 1c0ac1aa7e38fddb85bb9b434c46665cacd1ca69
ms.sourcegitcommit: c2b5ce3150ae998e18a51bad23277cedad1f06c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/17/2021
ms.locfileid: "63004964"
---
# <a name="microsoft-365-group-expiration-policy"></a>Microsoft 365 wygasania grupy

Wraz ze zwiększeniem użycia grup Microsoft 365 i Microsoft Teams administratorzy i użytkownicy potrzebują sposobu na oczyszczenie nieużywanych grup i zespołów. Zasady Microsoft 365 wygasania grup mogą ułatwić usuwanie nieaktywnych grup z systemu i sprawić, że grupy będą bardziej schowek.

Gdy grupa wygaśnie, usuwane są również wszystkie skojarzone z nią usługi (skrzynka pocztowa, program Planner, witryna SharePoint, zespół itp.).

Gdy grupa wygaśnie, jest "miękko usunięta", co oznacza, że nadal można ją odzyskać przez maksymalnie 30 dni.

Administratorzy mogą określić okres wygaśnięcia, a każda nieaktywna grupa, która osiągnie koniec tego okresu i nie zostanie odnowiona, zostanie usunięta. Dotyczy to także zarchiwizowanej zespołów. Okres wygasania grupy rozpoczyna się od daty jej utworzenia lub od daty jej ostatniego odnowienia. Właściciele grupy automatycznie zostaną wysłani do nich wiadomość e-mail przed wygaśnięciem, która umożliwi im odnowienie grupy na inny okres ważności. Teams widzą trwałe powiadomienia w Teams.

Grupy, które są aktywnie wykorzystywane, są automatycznie odnawiane. Dowolna z następujących akcji spowoduje automatyczne automatyczneenie grupy:
- SharePoint — wyświetlać, edytować, pobierać, przenosić, udostępniać lub przekazywać pliki. Wyświetlanie strony SharePoint nie jest liczone jako akcja automatycznego odnawiania.
- Outlook — dołączyć do grupy, przeczytać lub napisać wiadomość grupy od tej grupy i polubić wiadomość (Outlook w sieci Web).
- Teams — odwiedzanie kanału zespołu.

Zwróć uwagę, że jedynym Yammer, które wyzwoli automatyczne odnawianie grupy, jest przekazanie dokumentu do SharePoint społeczności.

> [!IMPORTANT]
> Po zmianie zasad wygasania usługa ponownie obliczy datę wygaśnięcia dla każdej grupy. Zawsze zaczyna ona liczać od daty utworzenia grupy, a następnie stosuje nowe zasady wygasania.

Należy pamiętać, że wygasanie jest domyślnie wyłączone. Administratorzy muszą włączyć tę funkcję w swojej organizacji, jeśli chcą jej używać.

> [!NOTE]
> Konfigurowanie i używanie zasad wygasania dla grup programu Microsoft 365 wymaga posiadania ich, ale nie musi Azure AD — wersja Premium przypisywać licencji członkom wszystkich grup, do których mają zastosowanie zasady wygasania. Aby uzyskać więcej informacji, zobacz [Wprowadzenie do Azure Active Directory — wersja Premium](/azure/active-directory/active-directory-get-started-premium).

## <a name="who-can-configure-and-use-the-microsoft-365-groups-expiration-policy"></a>KtoTo skonfigurować i używać zasad wygasania Microsoft 365 grupy?

|Rola|Co mogą robić|
|---------|---------|
|Office 365 administratorem globalnym (na platformie Azure administrator firmy), administratorem użytkownika|Tworzenie, odczytywanie, aktualizowanie lub usuwanie Microsoft 365 wygasania grup.|
|Użytkownik|Odnawianie [lub przywracanie](/azure/active-directory/users-groups-roles/groups-restore-deleted) Microsoft 365, która należy do tej grupy|

## <a name="how-to-set-the-expiration-policy"></a>Jak ustawić zasady wygasania

Jak wspomniano wcześniej, wygasanie jest domyślnie wyłączone. Administrator musi włączyć zasady wygasania i określić właściwości, które mają być wprowadzone. Aby ją włączyć, przejdź **do** >  Azure Active Directory **GroupsExpiration** > . Tutaj możesz ustawić domyślny okres istnienia grupy i określić, z jak dużym wyprzedzeniem chcesz, aby pierwsze i drugie powiadomienia o wygaśnięciu trafiły do właściciela grupy.

Okres istnienia grupy jest określony w dniach i można ustawić wartość 180, 365 lub wartość niestandardową określoną przez użytkownika. Wartość niestandardowa musi mieć wartość co najmniej 30 dni.

Jeśli grupa nie ma właściciela, wiadomości e-mail o wygaśnięciu zostaną podane do wskazanego administratora.

Możesz ustawić zasady dla wszystkich grup, tylko wybranych grup (do 500) lub całkowicie je wyłączyć, wybierając pozycję **Brak**. Pamiętaj, że obecnie nie możesz mieć różnych zasad dla różnych grup.

![Zrzut ekranu przedstawiający ustawienia wygasania grup w aplikacji Azure Active Directory.](../media/azure-groups-expiration-settings.png)

## <a name="how-expiry-works-with-the-retention-policy"></a>Jak działa wygasanie z zasadami przechowywania

Po skonfigurowaniu zasad przechowywania dla grup w Centrum zabezpieczeń i zgodności zasady wygasania są bezproblemowo zgodne z zasadami przechowywania. Po wygaśnięciu grupy konwersacje i pliki skrzynki pocztowej grupy w witrynie grupy są zachowywane w kontenerze przechowywania przez określoną liczbę dni zdefiniowaną w zasadach przechowywania. Po wygaśnięciu grupy ani jej zawartości użytkownicy nie będą jednak widzieć jej.

## <a name="how-and-when-a-group-owner-learns-if-their-groups-are-going-to-expire"></a>Jak i kiedy właściciel grupy dowiesz się, czy ich grupy wygasną

Właściciele grupy będą o tym powiadamiani tylko za pośrednictwem poczty e-mail. Jeśli grupa została utworzona za pośrednictwem usługi Planner, SharePoint lub dowolnej innej aplikacji, powiadomienia o wygaśnięciu zawsze będą wysyłane pocztą e-mail. Jeśli grupa została utworzona za pośrednictwem Teams, właściciel grupy otrzyma powiadomienie o odnowieniu za pośrednictwem sekcji aktywności. Nie zaleca się włączania wygasania grupy, jeśli właściciel grupy nie ma prawidłowego adresu e-mail.

30 dni przed wygaśnięciem grupy właściciele grupy (lub adresy e-mail określone dla grup, które nie mają właściciela) otrzymają wiadomość e-mail umożliwiającą im łatwe odnowienie grupy. Jeśli nie odnowi go, otrzyma on kolejną wiadomość e-mail o odnowieniu 15 dni przed jej wygaśnięciem. Jeśli ten użytkownik nadal nie odnowił subskrypcji, dzień przed wygaśnięciem otrzyma jeszcze jedno powiadomienie e-mail.

Jeśli z jakiegoś powodu żaden z właścicieli ani administratorów nie odnowi grupy przed jej wygaśnięciem, administrator nadal może przywrócić grupę przez 30 dni od jej wygaśnięcia. Aby uzyskać szczegółowe informacje, [zobacz: Przywracanie usuniętej Microsoft 365 grupy](https://support.office.com/article/restore-a-deleted-office-365-group-b7c66b59-657a-4e1a-8aa0-8163b1f4eb54).

## <a name="archiving-group-contents"></a>Archiwizowanie zawartości grupy

Jeśli masz grupę, która nie będzie już używać, ale chcesz zachować jej zawartość, zobacz Archiwizowanie grup, zespołów i usługi [Yammer](end-life-cycle-groups-teams-sites-yammer.md), aby uzyskać informacje na temat eksportowania informacji z różnych usług grup.

## <a name="related-topics"></a>Tematy pokrewne

[Zalecenia dotyczące planowania zarządzania współpracą](collaboration-governance-overview.md#collaboration-governance-planning-recommendations)

[Tworzenie planu zarządzania współpracą](collaboration-governance-first.md)

[Omówienie zasad przechowywania](https://support.office.com/article/5e377752-700d-4870-9b6d-12bfc12d2423)

[Przypisywanie nowego właściciela do grupy oddzielonej](https://support.office.com/article/86bb3db6-8857-45d1-95c8-f6d540e45732)

[Konfigurowanie wygasania Microsoft 365 grupy](/azure/active-directory/active-directory-groups-lifecycle-azure-portal)
