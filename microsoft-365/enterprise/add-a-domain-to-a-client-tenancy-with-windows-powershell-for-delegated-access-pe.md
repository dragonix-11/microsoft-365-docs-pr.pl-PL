---
title: Dodawanie domeny do dzierżawy klienta za pomocą Windows PowerShell dla partnerów dap
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: 'Podsumowanie: Użyj programu PowerShell, aby Microsoft 365 dodać alternatywną nazwę domeny do istniejącej dzierżawy klienta.'
ms.openlocfilehash: c4dcdb34f9065009ccaa77d23222601506b537b5
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65099043"
---
# <a name="add-a-domain-to-a-client-tenancy-with-windows-powershell-for-delegated-access-permission-dap-partners"></a>Dodawanie domeny do dzierżawy klienta za pomocą Windows PowerShell dla partnerów z uprawnieniami dostępu delegowanego (DAP)

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

Nowe domeny można tworzyć i kojarzyć z dzierżawą klienta za pomocą programu PowerShell, aby Microsoft 365 szybciej niż przy użyciu Centrum administracyjne platformy Microsoft 365.

Partnerami z uprawnieniami dostępu delegowanego (DAP) są partnerzy syndykacji i dostawcy rozwiązań w chmurze (CSP). Są one często sieci lub dostawców telekomunikacyjnych do innych firm. Łączą Microsoft 365 subskrypcje w swoje oferty usług dla swoich klientów. Gdy sprzedają subskrypcję Microsoft 365, automatycznie otrzymują uprawnienia administrowania w imieniu (AOBO) do dzierżaw klienta, aby mogli administrować dzierżawami klientów i raportować je.
## <a name="what-do-you-need-to-know-before-you-begin"></a>Co należy wiedzieć przed rozpoczęciem?

Procedury opisane w tym temacie wymagają nawiązania połączenia z [Połączenie w celu Microsoft 365 za pomocą programu PowerShell](connect-to-microsoft-365-powershell.md).

Potrzebne są również poświadczenia administratora dzierżawy partnera.

Potrzebne są również następujące informacje:

- Potrzebna jest w pełni kwalifikowana nazwa domeny (FQDN) żądana przez klienta.

- Potrzebujesz identyfikatora **TenantId** klienta.

- Nazwa FQDN musi być zarejestrowana u rejestratora usługi nazw domen internetowych (DNS), takiego jak GoDaddy. Aby uzyskać więcej informacji na temat publicznego rejestrowania nazwy domeny, zobacz [Jak kupić nazwę domeny](../admin/get-help-with-domains/buy-a-domain-name.md).

- Musisz wiedzieć, jak dodać rekord TXT do zarejestrowanej strefy DNS dla rejestratora DNS. Aby uzyskać więcej informacji na temat dodawania rekordu TXT, zobacz [Dodawanie rekordów DNS w celu nawiązania połączenia z domeną](../admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md). Jeśli te procedury nie działają dla Ciebie, musisz znaleźć procedury dla rejestratora DNS.

## <a name="create-domains"></a>Tworzenie domen

 Klienci prawdopodobnie będą prosić Cię o utworzenie dodatkowych domen do skojarzenia z ich dzierżawą, ponieważ nie chcą, aby domyślna \<domain>domena .onmicrosoft.com była podstawową domeną reprezentującą ich tożsamości firmowe na świecie. Ta procedura przeprowadzi Cię przez proces tworzenia nowej domeny skojarzonej z dzierżawą klienta.

> [!NOTE]
> Aby wykonać niektóre z tych operacji, konto administratora partnera, za pomocą które się logujesz, musi mieć **ustawioną pełną administrację** dla ustawienia **Przypisywanie dostępu administracyjnego do obsługiwanych firm**, które znajduje się w szczegółach konta administratora w <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Centrum administracyjne platformy Microsoft 365</a>. Aby uzyskać więcej informacji na temat zarządzania rolami administratora partnera, zobacz [Partners: Offer delegated administration (Partnerzy: delegowanie oferty).](https://go.microsoft.com/fwlink/p/?LinkId=532435)

### <a name="create-the-domain-in-azure-active-directory"></a>Tworzenie domeny w Azure Active Directory

To polecenie tworzy domenę w Azure Active Directory, ale nie kojarzy jej z domeną zarejestrowaną publicznie. Dzieje się tak, gdy udowodnisz, że jesteś właścicielem publicznie zarejestrowanej domeny w firmie Microsoft Microsoft 365 dla przedsiębiorstw.

```powershell
New-MsolDomain -TenantId <customer TenantId> -Name <FQDN of new domain>
```

> [!NOTE]
> Program PowerShell Core nie obsługuje modułu Microsoft Azure Active Directory dla modułu Windows PowerShell i poleceń cmdlet z nazwą **msol**. Aby kontynuować korzystanie z tych poleceń cmdlet, należy uruchomić je z Windows PowerShell.

### <a name="get-the-data-for-the-dns-txt-verification-record"></a>Pobieranie danych rekordu weryfikacji TXT systemu DNS

 Microsoft 365 wygeneruje określone dane, które należy umieścić w rekordzie weryfikacji TXT dns. Aby pobrać dane, uruchom to polecenie.

```powershell
Get-MsolDomainVerificationDNS -TenantId <customer TenantId> -DomainName <FQDN of new domain> -Mode DnsTxtRecord
```

Dzięki temu otrzymasz dane wyjściowe w następujący sposób:

 `Label: domainname.com`

 `Text: MS=ms########`

 `Ttl: 3600`

> [!NOTE]
> Ten tekst będzie potrzebny do utworzenia rekordu TXT w publicznie zarejestrowanej strefie DNS. Pamiętaj, aby go skopiować i zapisać.

### <a name="add-a-txt-record-to-the-publically-registered-dns-zone"></a>Dodawanie rekordu TXT do publicznie zarejestrowanej strefy DNS

Zanim Microsoft 365 zacznie akceptować ruch kierowany do publicznie zarejestrowanej nazwy domeny, musisz udowodnić, że jesteś właścicielem i masz uprawnienia administratora do domeny. Udowodnisz, że jesteś właścicielem domeny, tworząc rekord TXT w domenie. Rekord TXT nie wykonuje żadnych czynności w domenie i może zostać usunięty po ustanowieniu własności domeny. Aby utworzyć rekordy TXT, postępuj zgodnie z procedurami opisanymi w temacie [Dodawanie rekordów DNS w celu nawiązania połączenia z domeną](../admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md). Jeśli te procedury nie działają dla Ciebie, musisz znaleźć procedury dla rejestratora DNS.

Potwierdź pomyślne utworzenie rekordu TXT za pośrednictwem narzędzia nslookup. Postępuj zgodnie z tą składnią.

```console
nslookup -type=TXT <FQDN of registered domain>
```

Dzięki temu otrzymasz dane wyjściowe w następujący sposób:

 `Non-authoritative answer:`

 `FQDN of the registered domain`

 `text=MS=ms########`

### <a name="validate-domain-ownership-in-microsoft-365"></a>Weryfikowanie własności domeny w Microsoft 365

W tym ostatnim kroku sprawdzisz, czy Microsoft 365 jesteś właścicielem publicznie zarejestrowanej domeny. Po wykonaniu tego kroku Microsoft 365 rozpocznie akceptowanie ruchu kierowanego do nowej nazwy domeny. Aby ukończyć proces tworzenia i rejestracji domeny, uruchom to polecenie.

```powershell
Confirm-MsolDomain -TenantId <customer TenantId> -DomainName <FQDN of new domain>
```

To polecenie nie zwróci żadnych danych wyjściowych, więc aby potwierdzić, że to zadziałało, uruchom to polecenie.

```powershell
Get-MsolDomain -TenantId <customer TenantId> -DomainName <FQDN of new domain>
```

Spowoduje to zwrócenie czegoś takiego

```console
Name                   Status      Authentication
--------------------   ---------   --------------
FQDN of new domain     Verified    Managed
```

## <a name="see-also"></a>Zobacz też

[Pomoc dla partnerów](https://go.microsoft.com/fwlink/p/?LinkID=533477)
