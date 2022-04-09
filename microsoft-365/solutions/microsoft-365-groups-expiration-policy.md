---
title: zasady wygasania grupy Microsoft 365
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
description: Dowiedz się więcej o zasadach wygasania grup Microsoft 365.
ms.openlocfilehash: 9287d61b95d635eccbbef64d307c0aa0e3d12357
ms.sourcegitcommit: 46e796c6b76a01516c48977335bbf5076ca74a06
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2022
ms.locfileid: "64738564"
---
# <a name="microsoft-365-group-expiration-policy"></a>zasady wygasania grupy Microsoft 365

Wraz ze wzrostem użycia grup Microsoft 365 i Microsoft Teams administratorzy i użytkownicy potrzebują sposobu czyszczenia nieużywanych grup i zespołów. Zasady wygasania grup Microsoft 365 mogą pomóc usunąć nieaktywne grupy z systemu i usprawnić działania.

Po wygaśnięciu grupy wszystkie skojarzone z nią usługi (skrzynka pocztowa, planista, witryna SharePoint, zespół itp.) również zostaną usunięte.

Gdy grupa wygaśnie, zostanie ona "usunięta nietrwale", co oznacza, że można ją odzyskać przez maksymalnie 30 dni.

Administratorzy mogą określić okres wygaśnięcia, a każda nieaktywna grupa, która osiągnie koniec tego okresu i nie zostanie odnowiona, zostanie usunięta. (Obejmuje to zarchiwizowane zespoły). Okres wygaśnięcia rozpoczyna się po utworzeniu grupy lub w dniu jej ostatniego odnowienia. Właściciele grup automatycznie otrzymają wiadomość e-mail przed wygaśnięciem, która umożliwi im odnowienie grupy na inny interwał wygaśnięcia. Teams użytkownicy będą widzieć trwałe powiadomienia w Teams.

Grupy, które są aktywnie używane, są odnawiane automatycznie. Dowolna z następujących akcji spowoduje autorenew grupy:
- SharePoint — wyświetlanie, edytowanie, pobieranie, przenoszenie, udostępnianie lub przekazywanie plików. (Wyświetlanie strony SharePoint nie jest uwzględniane jako akcja automatycznego odnawiania).
- Outlook — dołącz lub edytuj grupę, odczyt lub zapis wiadomości grupy z grupy i polub wiadomość (Outlook w sieci Web).
- Teams — odwiedź kanał zespołu.
- Yammer — wyświetl wpis w społeczności Yammer lub interaktywną wiadomość e-mail w Outlook.
- Formularze — wyświetlanie, tworzenie lub edytowanie formularzy albo przesyłanie odpowiedzi do formularza. 

Należy pamiętać, że jedynym działaniem Yammer, które spowoduje automatyczne odnawianie grupy, jest przekazanie dokumentu do SharePoint w społeczności.

> [!IMPORTANT]
> Po zmianie zasad wygasania usługa ponownie oblicza datę wygaśnięcia dla każdej grupy. Zawsze rozpoczyna się liczenie od daty utworzenia grupy, a następnie stosuje nowe zasady wygasania.

Ważne jest, aby wiedzieć, że wygaśnięcie jest domyślnie wyłączone. Administratorzy muszą włączyć ją dla swojej organizacji, jeśli chcą z niej korzystać.

> [!NOTE]
> Konfigurowanie i używanie zasad wygasania dla grup Microsoft 365 wymaga posiadania, ale niekoniecznie przypisywania licencji Azure AD — wersja Premium dla członków wszystkich grup, do których są stosowane zasady wygasania. Aby uzyskać więcej informacji, zobacz [Wprowadzenie do Azure Active Directory — wersja Premium](/azure/active-directory/active-directory-get-started-premium).

## <a name="who-can-configure-and-use-the-microsoft-365-groups-expiration-policy"></a>KtoTo można skonfigurować i używać zasad wygasania grup Microsoft 365?

|Rola|Co mogą zrobić|
|---------|---------|
|Office 365 administrator globalny (na platformie Azure, administrator firmy), administrator użytkowników|Utwórz, przeczytaj, zaktualizuj lub usuń ustawienia zasad wygasania grup Microsoft 365.|
|Użytkownik|Odnawianie lub [przywracanie](/azure/active-directory/users-groups-roles/groups-restore-deleted) grupy Microsoft 365, która jest ich właścicielem|

## <a name="how-to-set-the-expiration-policy"></a>Jak ustawić zasady wygasania

Jak wspomniano powyżej, wygaśnięcie jest domyślnie wyłączone. Administrator będzie musiał włączyć zasady wygasania i ustawić właściwości, aby mogły zostać zastosowane. Aby ją włączyć, przejdź do **obszaru** >  Azure Active Directory **GroupsExpiration** > . W tym miejscu możesz ustawić domyślny okres istnienia grupy i określić, jak daleko z wyprzedzeniem chcesz, aby powiadomienia o pierwszym i drugim wygaśnięciu były wysyłane do właściciela grupy.

Okres istnienia grupy jest określony w dniach i można go ustawić na wartość 180, 365 lub na określoną wartość niestandardową. Wartość niestandardowa musi wynosić co najmniej 30 dni.

Jeśli grupa nie ma właściciela, wiadomości e-mail dotyczące wygasania zostaną wysłane do określonego administratora.

Możesz ustawić zasady dla wszystkich grup, tylko wybranych grup (do 500), lub wyłączyć je całkowicie, wybierając pozycję **Brak**. Należy pamiętać, że obecnie nie można mieć różnych zasad dla różnych grup.

![Zrzut ekranu przedstawiający ustawienia wygasania grup w Azure Active Directory.](../media/azure-groups-expiration-settings.png)

## <a name="how-expiry-works-with-the-retention-policy"></a>Jak działa wygaśnięcie z zasadami przechowywania

Jeśli skonfigurowano zasady przechowywania dla grup w Centrum zabezpieczeń i zgodności, zasady wygasania działają bezproblemowo z zasadami przechowywania. Po wygaśnięciu grupy konwersacje i pliki skrzynki pocztowej grupy w lokacji grupy są przechowywane w kontenerze przechowywania przez określoną liczbę dni zdefiniowaną w zasadach przechowywania. Użytkownicy nie będą jednak widzieć grupy ani jej zawartości po wygaśnięciu.

## <a name="how-and-when-a-group-owner-learns-if-their-groups-are-going-to-expire"></a>Jak i kiedy właściciel grupy dowie się, czy ich grupy wygasną

Właściciele grupy będą powiadamiani tylko pocztą e-mail. Jeśli grupa została utworzona za pośrednictwem narzędzia Planner, SharePoint lub dowolnej innej aplikacji, powiadomienia o wygaśnięciu będą zawsze wysyłane pocztą e-mail. Jeśli grupa została utworzona za pośrednictwem Teams, właściciel grupy otrzyma powiadomienie o odnowieniu za pośrednictwem sekcji działania. Nie zaleca się włączania wygasania grupy, jeśli właściciel grupy nie ma prawidłowego adresu e-mail.

Na 30 dni przed wygaśnięciem grupy właściciele grupy (lub adresy e-mail określone dla grup, które nie mają właściciela) otrzymają wiadomość e-mail umożliwiającą łatwe odnowienie grupy. Jeśli nie odnowią go, otrzymają kolejną wiadomość e-mail z odnowieniem na 15 dni przed wygaśnięciem. Jeśli jeszcze go nie odnowili, otrzymają jeszcze jedno powiadomienie e-mail na dzień przed wygaśnięciem.

Jeśli z jakiegoś powodu żaden z właścicieli ani administratorów nie odnowi grupy przed jej wygaśnięciem, administrator będzie mógł przywrócić grupę przez maksymalnie 30 dni po wygaśnięciu. Aby uzyskać szczegółowe informacje, zobacz [Przywracanie usuniętej grupy Microsoft 365](https://support.office.com/article/restore-a-deleted-office-365-group-b7c66b59-657a-4e1a-8aa0-8163b1f4eb54).

## <a name="archiving-group-contents"></a>Archiwizowanie zawartości grupy

Jeśli masz grupę, z którą nie chcesz już korzystać, ale chcesz zachować jej zawartość, zobacz [Sekcje Archiwum grup, zespołów i Yammer](end-life-cycle-groups-teams-sites-yammer.md), aby uzyskać informacje o sposobie eksportowania informacji z różnych usług grup.

## <a name="related-topics"></a>Tematy pokrewne

[Zalecenia dotyczące planowania zarządzania współpracą](collaboration-governance-overview.md#collaboration-governance-planning-recommendations)

[Tworzenie planu zarządzania współpracą](collaboration-governance-first.md)

[Omówienie zasad przechowywania](https://support.office.com/article/5e377752-700d-4870-9b6d-12bfc12d2423)

[Przypisywanie nowego właściciela do grupy oddzielonej](https://support.office.com/article/86bb3db6-8857-45d1-95c8-f6d540e45732)

[Konfigurowanie wygaśnięcia grup Microsoft 365](/azure/active-directory/active-directory-groups-lifecycle-azure-portal)
