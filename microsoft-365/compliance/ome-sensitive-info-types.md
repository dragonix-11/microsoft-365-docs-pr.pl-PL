---
title: Tworzenie zasad typu informacji poufnych przy użyciu Szyfrowanie wiadomości usługi Office 365
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 8/28/2019
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: ''
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-security-compliance
- Strat_O365_Enterprise
description: Dowiedz się, jak tworzyć zasady typu informacji poufnych dla organizacji przy użyciu Szyfrowanie wiadomości usługi Office 365.
ms.custom:
- seo-marvel-apr2020
- admindeeplinkEXCHANGE
ms.openlocfilehash: 8978b1f9faae2e96fa1940bf7663855ec3bb61da
ms.sourcegitcommit: b1066b2a798568afdea9c09401d52fa38fe93546
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/13/2021
ms.locfileid: "63017753"
---
# <a name="create-a-sensitive-information-type-policy-for-your-organization-using-message-encryption"></a>Tworzenie zasad typu informacji poufnych dla organizacji przy użyciu szyfrowania wiadomości

Zasady ochrony przed utratą Exchange (DLP, Data Loss Prevention) można stosować do reguł przepływu poczty e-mail lub ochrony przed utratą danych (DLP, Data Loss Prevention) w celu utworzenia zasad typu informacji poufnych w Szyfrowanie wiadomości usługi Office 365. Aby utworzyć regułę przepływu Exchange poczty e-mail, możesz użyć centrum administracyjnego programu <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange administracyjnego (EAC)</a> lub programu PowerShell.

## <a name="to-create-the-policy-by-using-mail-flow-rules-in-the-eac"></a>Aby utworzyć zasady przy użyciu reguł przepływu poczty e-mail w

Zaloguj się do centrum <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange administracyjnego</a> i przejdź do pozycji **Przepływy** >  poczty **e-mail**. Na stronie Reguły utwórz regułę, która będzie Szyfrowanie wiadomości usługi Office 365. Regułę można utworzyć na podstawie warunków, takich jak obecność określonych słów kluczowych lub typów informacji poufnych w wiadomości lub załączniku.

### <a name="to-create-the-policy-by-using-mail-flow-rules-in-powershell"></a>Aby utworzyć zasady przy użyciu reguł przepływu poczty e-mail w programie PowerShell

Użyj konta służbowego z uprawnieniami administratora globalnego w Twojej organizacji, rozpocznij sesję Windows PowerShell i połącz się z Exchange Online. Aby uzyskać instrukcje, [Połączenie do Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). Utwórz zasady Set-IRMConfiguration i New-TransportRule cmdlet.

## <a name="example-mail-flow-rule-created-with-powershell"></a>Przykładowa reguła przepływu poczty e-mail utworzona za pomocą programu PowerShell

Uruchom następujące polecenia w programie PowerShell, aby utworzyć regułę przepływu poczty e-mail programu Exchange, która automatycznie szyfruje wiadomości e-mail wysyłane poza organizacją przy użyciu opcji tylko do szyfrowania, jeśli wiadomości e-mail lub ich załączniki zawierają następujące typy informacji poufnych:

- Numer routingu ABA
- Numer karty kredytowej
- Numer agencji egzekwowania praw osób (DEA)
- Stany Zjednoczone numer paszportu
- Numer konta bankowego w Stanach Zjednoczonych
- Numer identyfikacyjny identyfikacji indywidualnej (ITIN) Stanów Zjednoczonych
- Numer SSN (U.SSN)

```powershell
Set-IRMConfiguration -DecryptAttachmentForEncryptOnly $true
New-TransportRule -Name "Encrypt outbound sensitive emails (out of box rule)" -SentToScope  NotInOrganization  -ApplyRightsProtectionTemplate "Encrypt" -MessageContainsDataClassifications @(@{Name="ABA Routing Number"; minCount="1"},@{Name="Credit Card Number"; minCount="1"},@{Name="Drug Enforcement Agency (DEA) Number"; minCount="1"},@{Name="U.S. / U.K. Passport Number"; minCount="1"},@{Name="U.S. Bank Account Number"; minCount="1"},@{Name="U.S. Individual Taxpayer Identification Number (ITIN)"; minCount="1"},@{Name="U.S. Social Security Number (SSN)"; minCount="1"}) -SenderNotificationType "NotifyOnly"
```

Aby uzyskać więcej informacji, [zobacz Set-IRMConfiguration](/powershell/module/exchange/set-irmconfiguration) i [New-TransportRule](/powershell/module/exchange/new-transportrule).

## <a name="how-recipients-access-attachments"></a>Jak adresaci mają dostęp do załączników

Po zaszyfrowaniu wiadomości przez firmę Microsoft adresaci mają nieograniczony dostęp do załączników, gdy uzyskuje dostęp do zaszyfrowanych wiadomości e-mail i otwierają je.

## <a name="to-prepare-for-this-change"></a>Aby przygotować się na tę zmianę

Możesz zaktualizować wszelkie mające zastosowanie dokumenty i materiały szkoleniowe dla użytkowników końcowych, aby przygotować osoby w Twojej organizacji do tej zmiany. Udostępnij te Szyfrowanie wiadomości usługi Office 365 zasobów użytkownikom, odpowiednio do potrzeb:

- [Wysyłanie i wyświetlanie zaszyfrowanych wiadomości oraz odpowiadanie na nie Outlook wiadomości na komputerze PC](https://support.microsoft.com/en-us/office/send-view-and-reply-to-encrypted-messages-in-outlook-for-pc-eaa43495-9bbb-4fca-922a-df90dee51980)
- [Microsoft 365 klip wideo z podstawowymi informacjami Office wiadomości](https://youtu.be/CQR0cG_iEUc)

## <a name="view-these-changes-in-the-audit-log"></a>Wyświetlanie tych zmian w dzienniku inspekcji

Microsoft 365 inspekcji tej aktywności i udostępnia ją administratorom. Operacja to "New-TransportRule" i fragment przykładowego wpisu inspekcji z centrum zabezpieczeń i zgodności usługi & inspekcji znajduje się poniżej:

```text
*{"CreationTime":"2018-11-28T23:35:01","Id":"a1b2c3d4-daa0-4c4f-a019-03a1234a1b0c","Operation":"New-TransportRule","OrganizationId":"123456-221d-12345 ","RecordType":1,"ResultStatus":"True","UserKey":"Microsoft Operator","UserType":3,"Version":1,"Workload":"Exchange","ClientIP":"123.456.147.68:17584","ObjectId":"","UserId":"Microsoft Operator","ExternalAccess":true,"OrganizationName":"contoso.onmicrosoft.com","OriginatingServer":"CY4PR13MBXXXX (15.20.1382.008)","Parameters": {"Name":"Organization","Value":"123456-221d-12346"{"Name":"ApplyRightsProtectionTemplate","Value":"Encrypt"},{"Name":"Name","Value":"Encrypt outbound sensitive emails (out of box rule)"},{"Name":"MessageContainsDataClassifications"…etc.*
```

## <a name="to-disable-or-customize-the-sensitive-information-types-policy"></a>Aby wyłączyć lub dostosować zasady typów informacji poufnych

Po utworzeniu reguły przepływu poczty e-mail programu Exchange możesz ją wyłączyć lub [](/exchange/security-and-compliance/mail-flow-rules/manage-mail-flow-rules#enable-or-disable-a-mail-flow-rule) edytować,  >  przechodząc do pozycji Przepływy poczty w centrum administracyjnym programu <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange</a> i wyłączając regułę "Szyfrowanie poufnych wiadomości e-mail wychodzących (reguła "poza polem *)*".