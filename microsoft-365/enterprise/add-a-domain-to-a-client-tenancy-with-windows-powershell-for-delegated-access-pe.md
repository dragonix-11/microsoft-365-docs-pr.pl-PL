---
title: Dodawanie domeny do usługi klienta z usługą Windows PowerShell partnerów daP
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- Ent_O365
- M365-subscription-management
f1.keywords:
- NOCSH
ms.custom:
- seo-marvel-apr2020
- admindeeplinkMAC
ms.assetid: f49b4d24-9aa0-48a6-95dd-6bae9cf53d2c
description: 'Podsumowanie: Użyj programu PowerShell Microsoft 365, aby dodać alternatywną nazwę domeny do istniejącej dzierżawy klienta.'
ms.openlocfilehash: 1a121407ebe242747a693084289e972e56e1cbee
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62973786"
---
# <a name="add-a-domain-to-a-client-tenancy-with-windows-powershell-for-delegated-access-permission-dap-partners"></a>Dodawanie domeny do licencji klienta z usługą Windows PowerShell dla partnerów dap (Delegated Access Permission)

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

Możesz tworzyć nowe domeny i skojarzyć je z klientem klientem korzystającym z programu PowerShell dla Microsoft 365 szybciej niż za pomocą centrum administracyjne platformy Microsoft 365.

Partnerzy w programie DaP (Delegated Access Permission) to partnerzy usług Syndication i Dostawcy rozwiązań w chmurze (CSP). Są często dostawcami sieci lub telekomunikacyjnych dla innych firm. Oferują one Microsoft 365 subskrypcji do swoich ofert usług swoim klientom. Gdy sprzeda subskrypcję usługi Microsoft 365, są mu automatycznie udzielane uprawnienia administrowania w imieniu klienta (AOBO), aby ten klient może administrować tymi usługami i raportować na ich temat.
## <a name="what-do-you-need-to-know-before-you-begin"></a>Co należy wiedzieć przed rozpoczęciem?

Procedury w tym temacie wymagają nawiązania połączenia z [programem Połączenie Microsoft 365 programem PowerShell](connect-to-microsoft-365-powershell.md).

Potrzebne są również poświadczenia administratora dzierżawy partnerskiej.

Potrzebne są również następujące informacje:

- Potrzebujesz w pełni kwalifikowanej nazwy domeny (FQDN), która jest potrzebna Twojem klientom.

- Potrzebny jest numer **TenantId klienta**.

- Nazwa FQDN musi być zarejestrowana u rejestratora internetowej usługi nazw domen (DNS), takiego jak GoDaddy. Aby uzyskać więcej informacji na temat publicznego rejestrowania nazwy domeny, zobacz [Jak kupić nazwę domeny](../admin/get-help-with-domains/buy-a-domain-name.md).

- Musisz wiedzieć, jak dodać rekord TXT do zarejestrowanej strefy DNS u rejestratora DNS. Aby uzyskać więcej informacji na temat dodawania rekordu TXT, zobacz [Dodawanie rekordów DNS w celu połączenia domeny](../admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md). Jeśli te procedury Ci nie zadziałają, musisz znaleźć procedury dla swojego rejestratora DNS.

## <a name="create-domains"></a>Tworzenie domen

 \<domain>Klienci będą prawdopodobnie prosić o utworzenie dodatkowych domen w celu skojarzenia ich z ich zobowiązaniami, ponieważ nie chcą, aby domyślna domena .onmicrosoft.com być podstawową domeną reprezentującą ich tożsamości firmowe na świecie. Ta procedura umożliwia utworzenie nowej domeny skojarzonej z założeniem przez klienta nowej domeny.

> [!NOTE]
> Aby można było wykonać niektóre z tych operacji, dla konta administratora partnera, przy użyciu których się logujesz, musi  być ustawiona wartość Pełne administrowanie ustawieniem Przypisz dostęp administracyjny do firm, do których obsługujesz pomoc techniczną, które znajdują się w szczegółach konta administratora <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">w</a> centrum administracyjne platformy Microsoft 365. Aby uzyskać więcej informacji na temat zarządzania rolami administratorów partnerów, [zobacz Partnerzy: oferuj administrację delegowaną](https://go.microsoft.com/fwlink/p/?LinkId=532435).

### <a name="create-the-domain-in-azure-active-directory"></a>Tworzenie domeny w u Azure Active Directory

To polecenie tworzy domenę w u Azure Active Directory, ale nie skojarzy jej z publicznie zarejestrowaną domeną. Dzieje się tak, gdy potwierdzasz, że jesteś właścicielem publicznie zarejestrowanej domeny w witrynie Microsoft Microsoft 365 dla przedsiębiorstw.

```powershell
New-MsolDomain -TenantId <customer TenantId> -Name <FQDN of new domain>
```

> [!NOTE]
> Program PowerShell Core nie obsługuje modułu Microsoft Azure Active Directory dla programu Windows PowerShell i poleceń cmdlet **z nazwą Msol**. Aby nadal korzystać z tych cmdlet, należy je uruchomić z programu Windows PowerShell.

### <a name="get-the-data-for-the-dns-txt-verification-record"></a>Uzyskiwanie danych dla rekordu weryfikacji DNS TXT

 Microsoft 365 wygeneruje określone dane, które należy umieścić w rekordzie weryfikacji DNS TXT. Aby pobrać dane, uruchom to polecenie.

```powershell
Get-MsolDomainVerificationDNS -TenantId <customer TenantId> -DomainName <FQDN of new domain> -Mode DnsTxtRecord
```

Pozwoli to na przykład:

 `Label: domainname.com`

 `Text: MS=ms########`

 `Ttl: 3600`

> [!NOTE]
> Ten tekst będzie potrzebny do utworzenia rekordu TXT w publicznie zarejestrowanej strefie DNS. Pamiętaj, aby je skopiować i zapisać.

### <a name="add-a-txt-record-to-the-publically-registered-dns-zone"></a>Dodawanie rekordu TXT do publicznie zarejestrowanej strefy DNS

Zanim Microsoft 365 rozpocznie się akceptowanie ruchu skierowanego do publicznie zarejestrowanej nazwy domeny, musisz udowodnić, że jesteś właścicielem tej domeny i masz uprawnienia administratora. Potwierdzasz, że jesteś właścicielem domeny, tworząc rekord TXT w tej domenie. Rekord TXT nie robisz niczego w domenie i można go usunąć po najecheniu na prawo własności do domeny. Aby utworzyć rekordy TXT, wykonaj procedury w temacie [Dodawanie rekordów DNS w celu połączenia domeny](../admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md). Jeśli te procedury Ci nie zadziałają, musisz znaleźć procedury dla swojego rejestratora DNS.

Potwierdź pomyślne utworzenie rekordu TXT za pośrednictwem funkcji nslookup. Postępuj zgodnie z tą składnią.

```console
nslookup -type=TXT <FQDN of registered domain>
```

Pozwoli to na przykład:

 `Non-authoritative answer:`

 `FQDN of the registered domain`

 `text=MS=ms########`

### <a name="validate-domain-ownership-in-microsoft-365"></a>Sprawdzanie poprawności własności domeny w Microsoft 365

W tym ostatnim kroku potwierdzisz, czy Microsoft 365 jesteś właścicielem publicznie zarejestrowanej domeny. Po zakończeniu tego Microsoft 365 ruchu kierowanego do nowej nazwy domeny. Aby ukończyć proces tworzenia i rejestracji domeny, uruchom to polecenie.

```powershell
Confirm-MsolDomain -TenantId <customer TenantId> -DomainName <FQDN of new domain>
```

To polecenie nie zwróci żadnych danych wyjściowych, więc aby potwierdzić, że to zadziałało, uruchom to polecenie.

```powershell
Get-MsolDomain -TenantId <customer TenantId> -DomainName <FQDN of new domain>
```

Zwracany jest ten zwrot w ten sposób.

```console
Name                   Status      Authentication
--------------------   ---------   --------------
FQDN of new domain     Verified    Managed
```

## <a name="see-also"></a>Zobacz też

[Pomoc dla partnerów](https://go.microsoft.com/fwlink/p/?LinkID=533477)
