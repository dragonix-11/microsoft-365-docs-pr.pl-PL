---
title: Identyfikowanie dostępnych poleceń cmdlet programu PowerShell do przechowywania
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: reference
ms.service: O365-seccomp
ms.localizationpriority: normal
ms.collection:
- M365-security-compliance
- SPO_Content
- m365initiative-compliance
description: Zidentyfikuj polecenia cmdlet programu PowerShell do przechowywania, które obsługują konfigurację na dużą skalę, automatyzację lub mogą być potrzebne w przypadku zaawansowanych scenariuszy konfiguracji.
ms.openlocfilehash: 5e31fb7b92dbc1dc83af8f7047041a7d0b4b23b2
ms.sourcegitcommit: 0c87abc17fbfe8aa43d61510101acdad0d491cd2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/05/2022
ms.locfileid: "66612156"
---
# <a name="powershell-cmdlets-for-retention-policies-and-retention-labels"></a>Polecenia cmdlet programu PowerShell dla zasad przechowywania i etykiet przechowywania

>*[Wskazówki dotyczące licencjonowania platformy Microsoft 365 dotyczące zgodności & zabezpieczeń](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Poniższe sekcje służą do identyfikowania głównych poleceń cmdlet programu PowerShell, które są dostępne dla zasad przechowywania i etykiet przechowywania, które mogą być potrzebne do konfiguracji na dużą skalę, zautomatyzowanych skryptów lub zaawansowanych scenariuszy konfiguracji. Aby uzyskać pełną listę poleceń cmdlet, zobacz [listę policy-and-compliance-retention](/powershell/module/exchange#policy-and-compliance-retention) z dokumentacji programu PowerShell.

Przed użyciem tych poleceń cmdlet należy najpierw [nawiązać połączenie z programem PowerShell Security & Compliance Center](/powershell/exchange/connect-to-scc-powershell).

W poniższych opisach zasady przechowywania mogą odwoływać się do zasad przechowywania (bez etykiet) lub zasad etykiet przechowywania. Każda zasada definiuje, czy są statyczne, czy adaptacyjne, oraz lokalizacje, w których mają być stosowane zasady. Następnie zasady wymagają jednej reguły do ukończenia konfiguracji.

Przykład:
- Zasady przechowywania wymagają reguły definiującej ustawienia przechowywania, takie jak zachowywanie przez pięć lat, a następnie usuwanie.

Jeśli używasz etykiet przechowywania, zawierają one ustawienia przechowywania, a ich zasady wymagają różnych reguł:
- Opublikowane zasady etykiet przechowywania wymagają reguły określającej, które etykiety powinny być wyświetlane w aplikacjach.
- Zasady automatycznego stosowania etykiet przechowywania wymagają reguły definiującej etykietę do zastosowania oraz warunków stosowania etykiety.

## <a name="retention-cmdlets-for-most-locations"></a>Polecenia cmdlet przechowywania dla większości lokalizacji

Użyj poleceń cmdlet w poniższej tabeli, gdy lokalizacje to **poczta e-mail programu Exchange**, **witryny programu SharePoint**, **konta usługi OneDrive**, **Grupy Microsoft 365**, **Skype dla firm**, **foldery publiczne programu Exchange**, **wiadomości czatu w usłudze Teams** lub **wiadomości kanału usługi Teams**.

Nie używaj tych poleceń cmdlet, gdy lokalizacje są przeznaczone dla komunikatów kanału prywatnego usługi Teams, komunikatów użytkowników usługi Yammer lub wiadomości społeczności usługi Yammer. Te lokalizacje mają alternatywne polecenia cmdlet, które zostały zidentyfikowane w [następnej sekcji](#retention-cmdlets-specific-to-teams-private-channels-and-yammer).

|Polecenie cmdlet|Opis|Odpowiednie lokalizacje|
|:-----|:-----|:-----|:-----|
|[Enable-ComplianceTagStorage](/powershell/module/exchange/enable-compliancetagstorage) <br /><br /> [Get-ComplianceTagStorage](/powershell/module/exchange/enable-compliancetagstorage) |Jednorazowa operacja tworzenia magazynu lub wyświetlania tego magazynu dla etykiet przechowywania |Poczta e-mail programu Exchange <br /><br />Witryny programu SharePoint <br /><br /> Konta usługi OneDrive <br /><br /> Grupy Microsoft 365|
|[Get-ComplianceTag](/powershell/module/exchange/get-compliancetag)<br /><br> [New-ComplianceTag](/powershell/module/exchange/new-compliancetag) <br /><br> [Remove-ComplianceTag](/powershell/module/exchange/remove-compliancetag) <br /><br> [Set-ComplianceTag](/powershell/module/exchange/set-compliancetag) |Wyświetlanie, tworzenie, usuwanie, konfigurowanie etykiet przechowywania |Poczta e-mail programu Exchange <br /><br /> Witryny programu SharePoint <br /><br /> Konta usługi OneDrive<br /><br /> Grupy Microsoft 365|
|[Get-RecordReviewNotificationTemplateConfig](/powershell/module/exchange/get-recordreviewnotificationtemplateconfig) <br /><br /> [Set-RecordReviewNotificationTemplateConfig](/powershell/module/exchange/remove-retentioncompliancepolicy)  |Wyświetlanie lub konfigurowanie konfiguracji ustawień powiadomień i przypomnień dotyczących przeglądu dyspozycji |Poczta e-mail programu Exchange <br /><br /> Witryny programu SharePoint <br /><br /> Konta usługi OneDrive <br /><br /> Grupy Microsoft 365|
|[Get-RetentionCompliancePolicy](/powershell/module/exchange/get-retentioncompliancepolicy) <br /><br /> [New-RetentionCompliancePolicy](/powershell/module/exchange/new-retentioncompliancepolicy) <br /><br /> [Remove-RetentionCompliancePolicy](/powershell/module/exchange/remove-retentioncompliancepolicy) <br /><br /> [Set-RetentionCompliancePolicy](/powershell/module/exchange/set-retentioncompliancepolicy) |Wyświetlanie, tworzenie, usuwanie, konfigurowanie zasad przechowywania |Poczta e-mail programu Exchange <br /><br /> Witryny programu SharePoint <br /><br /> Konta usługi OneDrive<br /><br /> Grupy Microsoft 365 <br /><br /> Skype dla firm <br /><br /> Foldery publiczne programu Exchange <br /><br /> Wiadomości czatu w usłudze Teams <br /><br /> Komunikaty kanału usługi Teams |
|[Get-RetentionComplianceRule](/powershell/module/exchange/get-retentioncompliancepolicy) <br /><br /> [New-RetentionComplianceRule](/powershell/module/exchange/get-retentioncompliancepolicy) <br /><br /> [Set-RetentionComplianceRule](/powershell/module/exchange/set-retentioncompliancerule) <br /><br /> [Remove-RetentionComplianceRule](/powershell/module/exchange/remove-retentioncompliancerule)  | Wyświetlanie, tworzenie, konfigurowanie, usuwanie ustawień zasad dotyczących etykiet przechowywania lub przechowywania |Poczta e-mail programu Exchange <br /><br /> Witryny programu SharePoint <br /><br /> Konta usługi OneDrive <br /><br /> Grupy Microsoft 365 <br /><br /> Skype dla firm <br /><br /> Foldery publiczne programu Exchange <br /><br /> Wiadomości czatu w usłudze Teams <br /><br /> Komunikaty kanału usługi Teams |

## <a name="retention-cmdlets-specific-to-teams-private-channels-and-yammer"></a>Polecenia cmdlet przechowywania specyficzne dla prywatnych kanałów usługi Teams i usługi Yammer

Użyj następujących poleceń cmdlet, gdy lokalizacje są przeznaczone dla **komunikatów kanału prywatnego usługi Teams**, **komunikatów użytkowników usługi Yammer** lub **wiadomości społeczności usługi Yammer**.

Jeśli lokalizacje są przeznaczone dla wiadomości czatu w usłudze Teams, wiadomości kanału usługi Teams, poczty e-mail programu Exchange, witryn programu SharePoint, kont usługi OneDrive, Grupy Microsoft 365, Skype dla firm lub folderów publicznych programu Exchange, użyj poleceń cmdlet wymienionych w [poprzedniej sekcji](#retention-cmdlets-for-most-locations).

|Polecenie cmdlet|Opis|Odpowiednie lokalizacje|
|:-----|:-----|:-----|:-----|
|[Get-AppRetentionCompliancePolicy](/powershell/module/exchange/get-appretentioncompliancepolicy) <br /><br> [New-AppRetentionCompliancePolicy](/powershell/module/exchange/new-appretentioncompliancepolicy) <br /><br> [Remove-AppRetentionCompliancePolicy](/powershell/module/exchange/remove-appretentioncompliancepolicy) <br /><br> [Set-AppRetentionCompliancePolicy](/powershell/module/exchange/remove-appretentioncompliancepolicy) | Wyświetlanie, tworzenie, usuwanie, konfigurowanie zasad przechowywania |Komunikaty kanału prywatnego usługi Teams <br /><br /> Komunikaty użytkowników usługi Yammer <br /><br /> Komunikaty społeczności usługi Yammer|
|[Get-AppRetentionComplianceRule](/powershell/module/exchange/get-appretentioncompliancerule) <br /><br /> [New-AppRetentionComplianceRule](/powershell/module/exchange/new-appretentioncompliancerule) <br /><br /> [Remove-AppRetentionComplianceRule](/powershell/module/exchange/remove-appretentioncompliancerule) <br /><br /> [Set-AppRetentionComplianceRule](/powershell/module/exchange/remove-appretentioncompliancerule) | Wyświetlanie, tworzenie, usuwanie, konfigurowanie ustawień przechowywania dla zasad przechowywania |Komunikaty kanału prywatnego usługi Teams <br /><br /> Komunikaty użytkowników usługi Yammer <br /><br /> Komunikaty społeczności usługi Yammer|

## <a name="configuration-guidance"></a>Wskazówki dotyczące konfiguracji

Aby uzyskać szczegółowe informacje i przykłady, użyj stron pomocy skojarzonych z każdym poleceniem cmdlet.

Aby uzyskać pomoc z przewodnikiem dotyczącą tworzenia, a następnie publikowania etykiet przechowywania, zobacz [Tworzenie i publikowanie etykiet przechowywania przy użyciu programu PowerShell](bulk-create-publish-labels-using-powershell.md).