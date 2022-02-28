---
title: Pobieranie danych raportowania dzierżawy klientów Windows PowerShell partnerom daP
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: 'Podsumowanie: użyj funkcji zdalnych Windows PowerShell, Microsoft Exchange Online pobierać raporty od poszczególnych dzierżaw klientów.'
ms.openlocfilehash: cc9046ab5c90dcb40cbf012772fd80b56f71ec79
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62983795"
---
# <a name="retrieve-customer-tenant-reporting-data-with-windows-powershell-for-delegated-access-permissions-dap-partners"></a>Pobieranie danych raportowania dzierżawy klienta Windows PowerShell dla partnerów dap (Delegated Access Permissions)

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

Pobieraj raporty Windows PowerShell klientów Microsoft Exchange Online aplikacji zdalnej.

Partnerzy programu Syndication i programu Dostawca rozwiązań w chmurze (CSP) mogą uzyskać dostęp do danych, które tworzy raporty dzierżawy klientów, bezpośrednio za pośrednictwem Windows PowerShell dla programu Exchange Online PowerShell. Dzięki temu partnerzy mogą zbierać i zapisywać dane raportowania, a następnie wykonywać inne operacje na tych danych. Po otwarciu połączenia zdalnego pobieranie danych raportowania dotyczących tajności klienta jest identyczne z uruchamianiem każdego polecenia cmdlet w odniesieniu do tego klienta.

W tym artykule używasz aplikacji zdalnej Windows PowerShell dla Exchange Online łączenia się z jedną usługą obsługą klienta i pobierania raportu. Domyślnie program Windows PowerShell nie obsługuje agregowania danych raportowania od wielu klientów. Raporty pobierane za pomocą tej procedury są tylko dla  _delegatedOrg_ , z który łączysz się.

## <a name="before-you-begin"></a>Przed rozpoczęciem

- Musisz połączyć się ze swoją dzierżawą Exchange Online, używając zdalnej Windows PowerShell. Aby uzyskać instrukcje, Połączenie do Exchange Online z zdalnymi Windows PowerShell dla partnerów [dap (Delegated Access Permissions)](/powershell/exchange/connect-to-exchange-online-powershell)

## <a name="run-the-get-stalemailboxreport-sample"></a>Uruchamianie przykładowego Get-StaleMailboxReport przykładowego

Po otwarciu sesji zdalnej z usługą Exchange Online uruchom to polecenie, aby pobrać **get-StaleMailboxReport** dla zakresu dat od 2015-03-25 do 31/03/2015.

```powershell
Get-StaleMailboxReport -StartDate 03/25/2015 -EndDate 03/31/2015
```

Istnieje wiele innych dostępnych polecenia cmdlet raportowania dla usług Exchange Online, Lync Online i SharePoint Online, a także innych do śledzenia wiadomości, których można użyć. Aby dowiedzieć się więcej o dostępnych poleceniach cmdlet raportowania i Office 365 sieci Web Raportowanie, zobacz tematy w poniższej sekcji.

## <a name="see-also"></a>Zobacz też

[Office 365 sieci Web Raportowanie](/previous-versions/office/developer/o365-enterprise-developers/jj984325(v=office.15))

[Polecenia cmdlet dotyczące raportowania w programie Exchange Online](/powershell/module/exchange/get-csclientdevicedetailreport)

[Pomoc dla partnerów](https://go.microsoft.com/fwlink/p/?LinkID=533477)
