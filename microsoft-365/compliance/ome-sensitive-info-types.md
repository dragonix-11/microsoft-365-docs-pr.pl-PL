---
title: Tworzenie zasad typów informacji poufnych przy użyciu szyfrowania komunikatów Office 365
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
description: Dowiedz się, jak utworzyć zasady typów informacji poufnych dla organizacji przy użyciu Office 365 szyfrowania komunikatów.
ms.custom:
- seo-marvel-apr2020
- admindeeplinkEXCHANGE
ms.openlocfilehash: 0974c30882177eb9fc46c2a2fcf65bc2edb43078
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66633438"
---
# <a name="create-a-sensitive-information-type-policy-for-your-organization-using-message-encryption"></a>Tworzenie zasad typów informacji poufnych dla organizacji przy użyciu szyfrowania komunikatów

Aby utworzyć zasady typów informacji poufnych z Office 365 szyfrowaniem komunikatów, można użyć reguł przepływu poczty programu Exchange lub ochrony przed utratą danych (DLP) usługi Microsoft Purview. Aby utworzyć regułę przepływu poczty programu Exchange, możesz użyć <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">centrum administracyjnego programu Exchange (EAC)</a> lub programu PowerShell.

## <a name="to-create-the-policy-by-using-mail-flow-rules-in-the-eac"></a>Aby utworzyć zasady przy użyciu reguł przepływu poczty w usłudze EAC

Zaloguj się do <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">centrum administracyjnego programu Exchange</a> i przejdź do pozycji **Reguły** **przepływu poczty** > . Na stronie Reguły utwórz regułę, która ma zastosowanie Office 365 szyfrowania komunikatów. Regułę można utworzyć na podstawie warunków, takich jak obecność niektórych słów kluczowych lub typów informacji poufnych w wiadomości lub załączniku.

### <a name="to-create-the-policy-by-using-mail-flow-rules-in-powershell"></a>Aby utworzyć zasady przy użyciu reguł przepływu poczty w programie PowerShell

Użyj konta służbowego z uprawnieniami administratora globalnego w organizacji, aby nawiązać połączenie z programem Exchange Online programu PowerShell. Aby uzyskać instrukcje, zobacz [Connect to Exchange Online PowerShell (Nawiązywanie połączenia z programem PowerShell](/powershell/exchange/connect-to-exchange-online-powershell)). Użyj poleceń cmdlet Set-IRMConfiguration i New-TransportRule, aby utworzyć zasady.

## <a name="example-mail-flow-rule-created-with-powershell"></a>Przykładowa reguła przepływu poczty utworzona przy użyciu programu PowerShell

Uruchom następujące polecenia w programie PowerShell, aby utworzyć regułę przepływu poczty programu Exchange, która automatycznie szyfruje wiadomości e-mail wysyłane poza organizację za pomocą opcji tylko do szyfrowania, jeśli wiadomości e-mail lub ich załączniki zawierają następujące typy informacji poufnych:

- Numer routingu usługi ABA
- Numer karty kredytowej
- Numer Agencji Egzekwowania Narkotyków (DEA)
- Stany Zjednoczone /Zjednoczone Zjednoczone numer paszportu
- Numer konta bankowego w Stanach Zjednoczonych
- Numer identyfikacyjny indywidualnego podatnika w Stanach Zjednoczonych (ITIN)
- Numer ubezpieczenia społecznego (SSN)

```powershell
Set-IRMConfiguration -DecryptAttachmentForEncryptOnly $true
New-TransportRule -Name "Encrypt outbound sensitive emails (out of box rule)" -SentToScope  NotInOrganization  -ApplyRightsProtectionTemplate "Encrypt" -MessageContainsDataClassifications @(@{Name="ABA Routing Number"; minCount="1"},@{Name="Credit Card Number"; minCount="1"},@{Name="Drug Enforcement Agency (DEA) Number"; minCount="1"},@{Name="U.S. / U.K. Passport Number"; minCount="1"},@{Name="U.S. Bank Account Number"; minCount="1"},@{Name="U.S. Individual Taxpayer Identification Number (ITIN)"; minCount="1"},@{Name="U.S. Social Security Number (SSN)"; minCount="1"}) -SenderNotificationType "NotifyOnly"
```

Aby uzyskać więcej informacji, zobacz [Set-IRMConfiguration](/powershell/module/exchange/set-irmconfiguration) i [New-TransportRule](/powershell/module/exchange/new-transportrule).

## <a name="how-recipients-access-attachments"></a>Jak adresaci uzyskują dostęp do załączników

Gdy firma Microsoft szyfruje wiadomość, adresaci mają nieograniczony dostęp do załączników podczas uzyskiwania dostępu do zaszyfrowanej wiadomości e-mail i otwierania ich.

## <a name="to-prepare-for-this-change"></a>Aby przygotować się do tej zmiany

Możesz zaktualizować dowolną odpowiednią dokumentację użytkownika końcowego i materiały szkoleniowe, aby przygotować osoby w organizacji do tej zmiany. W razie potrzeby udostępnij użytkownikom następujące zasoby szyfrowania komunikatów Office 365:

- [Wysyłanie, wyświetlanie i odpowiadanie na zaszyfrowane wiadomości w programie Outlook dla komputerów PC](https://support.microsoft.com/office/send-view-and-reply-to-encrypted-messages-in-outlook-for-pc-eaa43495-9bbb-4fca-922a-df90dee51980)
- [Wideo dotyczące podstaw platformy Microsoft 365: szyfrowanie komunikatów](https://youtu.be/CQR0cG_iEUc)

## <a name="view-these-changes-in-the-audit-log"></a>Wyświetl te zmiany w dzienniku inspekcji

Platforma Microsoft 365 przeprowadza inspekcję tego działania i udostępnia ją administratorom. Operacja to "New-TransportRule", a fragment przykładowego wpisu inspekcji z usługi Audit Log Search w Usłudze Security & Compliance Center znajduje się poniżej:

```text
*{"CreationTime":"2018-11-28T23:35:01","Id":"a1b2c3d4-daa0-4c4f-a019-03a1234a1b0c","Operation":"New-TransportRule","OrganizationId":"123456-221d-12345 ","RecordType":1,"ResultStatus":"True","UserKey":"Microsoft Operator","UserType":3,"Version":1,"Workload":"Exchange","ClientIP":"123.456.147.68:17584","ObjectId":"","UserId":"Microsoft Operator","ExternalAccess":true,"OrganizationName":"contoso.onmicrosoft.com","OriginatingServer":"CY4PR13MBXXXX (15.20.1382.008)","Parameters": {"Name":"Organization","Value":"123456-221d-12346"{"Name":"ApplyRightsProtectionTemplate","Value":"Encrypt"},{"Name":"Name","Value":"Encrypt outbound sensitive emails (out of box rule)"},{"Name":"MessageContainsDataClassifications"...etc.*
```

## <a name="to-disable-or-customize-the-sensitive-information-types-policy"></a>Aby wyłączyć lub dostosować zasady typów informacji poufnych

Po utworzeniu reguły przepływu poczty programu Exchange można [wyłączyć lub edytować regułę](/exchange/security-and-compliance/mail-flow-rules/manage-mail-flow-rules#enable-or-disable-a-mail-flow-rule), przechodząc do pozycji **Reguły** **przepływu** >  poczty w <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">centrum administracyjnym programu Exchange</a> i wyłączając regułę "*Szyfrowanie wychodzących poufnych wiadomości e-mail (reguła out of box)*".
