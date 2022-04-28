---
title: Pobieranie danych raportowania dzierżawy klienta za pomocą Windows PowerShell dla partnerów dap
ms.author: kvice
author: kelleyvice-msft
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
ms.assetid: 893e5275-30b3-433f-8ecd-644f78f513e2
description: 'Podsumowanie: Użyj Windows PowerShell zdalnego, aby Microsoft Exchange Online pobierać raporty z poszczególnych dzierżaw klientów.'
ms.openlocfilehash: 8529e95e8aefbd45cf381ff21bec49e669fd7c6a
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65096705"
---
# <a name="retrieve-customer-tenant-reporting-data-with-windows-powershell-for-delegated-access-permissions-dap-partners"></a>Pobieranie danych raportowania dzierżawy klienta za pomocą Windows PowerShell dla partnerów z uprawnieniami dostępu delegowanego (DAP)

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

Użyj Windows PowerShell zdalnego, aby Microsoft Exchange Online pobierać raporty z poszczególnych dzierżaw klientów.

Partnerzy syndykacji i Dostawca rozwiązań w chmurze (CSP) mogą uzyskiwać dostęp do danych, które tworzą raporty dzierżawy klientów bezpośrednio za pośrednictwem Windows PowerShell zdalnych dla programu Exchange Online programu PowerShell. Dzięki temu partnerzy mogą zbierać i zapisywać dane raportowania, a następnie wykonywać na ich podstawie inne operacje. Po otwarciu połączenia zdalnego pobieranie danych raportowania dotyczących dzierżawy klienta jest identyczne z uruchamianiem dowolnego polecenia cmdlet względem dzierżawy klienta.

W tym artykule użyjesz Windows PowerShell zdalnego do Exchange Online, aby nawiązać połączenie z dzierżawą jednego klienta i pobrać raport. Domyślnie Windows PowerShell nie obsługuje agregowania danych raportowania z wielu dzierżaw klientów. Raporty pobierane za pomocą tej procedury dotyczą tylko  _obiektu DelegedOrg_ , z którym nawiązujesz połączenie.

## <a name="before-you-begin"></a>Przed rozpoczęciem

- Musisz nawiązać połączenie z dzierżawą Exchange Online przy użyciu Windows PowerShell zdalnych. Aby uzyskać instrukcje, zobacz [Połączenie do Exchange Online dzierżaw z Windows PowerShell zdalnych dla partnerów z uprawnieniami dostępu delegowanego (DAP)](/powershell/exchange/connect-to-exchange-online-powershell)

## <a name="run-the-get-stalemailboxreport-sample"></a>Uruchamianie przykładu Get-StaleMailboxReport

Po otwarciu sesji zdalnej w celu Exchange Online uruchom to polecenie, aby pobrać raport **Get-StaleMailboxReport** dla zakresu dat od 25.03.2015 do 31.03.2015.

```powershell
Get-StaleMailboxReport -StartDate 03/25/2015 -EndDate 03/31/2015
```

Istnieje wiele innych poleceń cmdlet raportowania dostępnych dla Exchange Online, Lync Online i SharePoint Online, a także innych do śledzenia komunikatów, których można użyć. Aby dowiedzieć się więcej na temat dostępnych poleceń cmdlet raportowania i usługi internetowej Office 365 Reporting, zobacz tematy w poniższej sekcji.

## <a name="see-also"></a>Zobacz też

[usługa internetowa raportowania Office 365](/previous-versions/office/developer/o365-enterprise-developers/jj984325(v=office.15))

[Polecenia cmdlet raportowania w Exchange Online](/powershell/module/exchange/get-csclientdevicedetailreport)

[Pomoc dla partnerów](https://go.microsoft.com/fwlink/p/?LinkID=533477)
