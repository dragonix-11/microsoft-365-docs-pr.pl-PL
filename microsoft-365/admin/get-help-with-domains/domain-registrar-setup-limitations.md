---
title: Rejestratorzy domen z ograniczeniami konfiguracji
f1.keywords:
- CSH
ms.author: pebaum
author: pebaum
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: high
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- okr_smb
- AdminTemplateSet
search.appverid:
- MET150
ROBOTS: NOINDEX
description: Niektórzy rejestratorzy domen oferują ograniczone usługi, co oznacza, że nie wszystkie funkcje firmy Microsoft będą działać z każdą domeną.
ms.openlocfilehash: 2d192f03c5a586e4355c1f9a08d312a07af3d501
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62973545"
---
# <a name="domain-registrars-with-setup-limitations"></a>Rejestratorzy domen z ograniczeniami konfiguracji

[Tworzenie rekordów DNS dla firmy Microsoft w witrynie DNSMadeEasy](#create-dns-records-at-dnsmadeeasy-for-microsoft)\
[Tworzenie rekordów DNS dla firmy Microsoft w witrynie easyDNS](#create-dns-records-at-easydns-for-microsoft)\
[Tworzenie rekordów DNS dla firmy Microsoft w witrynie Freenom](#create-dns-records-at-freenom-for-microsoft)\
[Tworzenie rekordów DNS dla firmy Microsoft w witrynie MyDomain](#create-dns-records-at-mydomain-for-microsoft)\
[Tworzenie rekordów DNS dla firmy Microsoft przy Windows DNS](#create-dns-records-for-microsoft-using-windows-based-dns)\
[Tworzenie rekordów DNS, gdy domeną zarządza firma Google (eNom)](#create-dns-records-when-your-domain-is-managed-by-google-enom)\
[Tworzenie rekordów DNS dla firmy Microsoft&1 IONOS](#create-dns-records-at-11-ionos-for-microsoft)

Niektórzy rejestratorzy domen mają istotne ograniczenia usługi, co oznacza, że nie wszystkie funkcje firmy Microsoft będą działać z każdą domeną. Konkretne ograniczenia dotyczące niektórych rejestratorów pozidentyfikowano w tym artykule. 

## <a name="create-dns-records-at-dnsmadeeasy-for-microsoft"></a>Tworzenie rekordów DNS dla firmy Microsoft w witrynie DNSMadeEasy

W przypadku kont w witrynie DNSMadeEasy dodana domena została zakupiona u oddzielnego rejestratora domen. Witryna DNSMadeEasy nie oferuje usługi rejestracji domen. Możliwość zalogowania się w witrynie DNSMadeEasy i utworzenia rekordu DNS jest wystarczającym dowodem własności.

## <a name="create-dns-records-at-easydns-for-microsoft"></a>Tworzenie rekordów DNS dla firmy Microsoft w witrynie easyDNS

Rekordy SRV nie są obecnie dostępne w ramach żadnego pakietu usługi easyDNS. Może być konieczne uaktualnienie do wyższego poziomu usługi za pomocą usługi easyDNS w celu dodania rekordów SRV, które są wymagane dla Teams.

## <a name="create-dns-records-at-freenom-for-microsoft"></a>Tworzenie rekordów DNS dla firmy Microsoft w witrynie Freenom

Witryna internetowa Freenom nie obsługuje dodawania rekordów SRV, co oznacza, że kilka Teams i poczty e-mail nie będzie działać. Niezależnie od tego, z którego planu firmy Microsoft korzystasz, istnieją istotne ograniczenia usług i możesz zechcieć przełączyć się na innego dostawcę hostingu DNS.

## <a name="create-dns-records-at-mydomain-for-microsoft"></a>Tworzenie rekordów DNS dla firmy Microsoft w witrynie MyDomain

Witryna internetowa MyDomain nie obsługuje rekordów SRV, co oznacza, że kilka Teams i poczty e-mail nie będzie działać. Niezależnie od tego, z którego planu firmy Microsoft korzystasz, jeśli zarządzasz rekordami DNS w witrynie MyDomain, istnieją istotne ograniczenia usług i możesz chcieć przełączyć się na innego dostawcę hostingu DNS.

## <a name="create-dns-records-for-microsoft-using-windows-based-dns"></a>Tworzenie rekordów DNS dla firmy Microsoft przy Windows DNS

Przechodzenie do strony zawierającej rekordy DNS domeny. Jeśli pracujesz w programie Windows Server 2008, przejdź do **przycisku Start** **i uruchom**. Jeśli pracujesz w programie Windows Server 2012, naciśnij klawisz **Windows i** **klawisz r**. Wpisz **dnsmgmnt.msc**, a następnie wybierz przycisk **OK**. W Menedżerze DNS rozwiń nazwę **serwera DNS**,  **Forward Lookup Zones (Strefy odnośników**). Wybierz domenę. Możesz teraz przystąpić do tworzenia rekordów DNS.

## <a name="create-dns-records-when-your-domain-is-managed-by-google-enom"></a>Tworzenie rekordów DNS, gdy domeną zarządza firma Google (eNom)

Jeśli domena została zakupiona za pośrednictwem firmy Google podczas rejestrowania się w usłudze Google Apps dla firm, rekordy DNS są zarządzane przez firmę Google, ale zarejestrowane w witrynie eNom. Za pośrednictwem strony Domeny w usłudze Google możesz uzyskać dostęp do witryny eNom i utworzyć system DNS.

## <a name="create-dns-records-at-11-ionos-for-microsoft"></a>Tworzenie rekordów DNS dla firmy Microsoft&1 IONOS

1&1 IONOS nie pozwala, aby domena miała zarówno rekord MX, jak i rekord CNAME wykrywania automatycznego najwyższego poziomu. Ogranicza to sposoby konfigurowania usługi dla Exchange Online Microsoft. Istnieje obejście, ale zalecamy jego stosowanie tylko wtedy, gdy masz już doświadczenie w tworzeniu poddomen w 1&1 IONOS.

Jeśli mimo tego ograniczenia usługi zdecydujesz się zarządzać swoimi rekordami DNS firmy Microsoft w witrynie 1&1 IONOS, wykonaj czynności opisane w tym artykule, aby zweryfikować domenę i skonfigurować rekordy DNS dla poczty e-mail, usługi Skype dla firm Online itp.

1&1 IONOS wymaga obejścia, aby można było używać rekordu MX razem z rekordami CNAME wymaganymi dla usług poczty e-mail firmy Microsoft. To obejście wymaga utworzenia zestawu poddomen w 1&1 IONOS i przypisania ich do rekordów CNAME.

> [!NOTE]
> Przed rozpoczęciem tej procedury upewnij się, że masz co najmniej dwie dostępne poddomeny. Zalecamy to rozwiązanie tylko wtedy, gdy masz już doświadczenie w tworzeniu poddomen w 1&1 IONOS.

### <a name="basic-cname-records"></a>Podstawowe rekordy CNAME

1.  Aby rozpocząć pracę, przejdź do swojej strony domen w 1&1 IONOS. Zostanie wyświetlony monit o zalogowanie się.

1.  Wybierz **pozycję Zarządzaj domenami**.

1.  Na stronie Domain Center (Centrum domen) znajdź domenę, którą chcesz zaktualizować, a następnie wybierz pozycję **Manage Subdomains (Zarządzaj poddomenami**). Teraz utworzysz dwie poddomeny i ustawisz wartość **Alias** dla każdej z nich (jest to wymagane, ponieważ 1&1 IONOS obsługuje tylko jeden rekord CNAME najwyższego poziomu, ale firma Microsoft wymaga kilku rekordów CNAME).

1.  Najpierw utworzysz poddomenę Autodiscover. W sekcji **Subdomain Overview (Przegląd poddomen** ) wybierz **pozycję Create Subdomain (Utwórz poddomenę**).

1.  W polu **Create Subdomain** (Utwórz poddomenę) dla nowej poddomeny wpisz lub skopiuj i wklej tylko wartość **Create Subdomain** (Utwórz poddomenę) z poniższej tabeli. (Wartość **Alias** dodasz w kolejnym kroku).

    |Create Subdomain (Utwórz poddomenę)|Alias|
    |:----|:----|
    |autodiscover|autodiscover.outlook.com|

1.  Wybierz **pozycję Create Subdomain (Utwórz poddomenę**).

1.  W sekcji **Subdomain Overview (Przegląd** poddomen) znajdź poddomenę autodiscover, która właśnie została utworzona, a następnie wybierz kontrolkę Panel (v) dla tej poddomeny.

1.  W obszarze **Subdomain Ustawienia** (Poddomena) wybierz **pozycję Edit DNS Ustawienia (Edytuj rekordy DNS Ustawienia**).

1.  W sekcji **A/AAAA Records (IP Addresses) (Rekordy A/AAAA; adresy IP)** w obszarze **IP address (A Record) (Adres IP, rekord A)** wybierz pozycję **CNAME**.

1. W polu **Alias** wpisz lub skopiuj i wklej tylko wartość **Alias** z poniższej tabeli.

    |Create Subdomain (Utwórz poddomenę)|Alias|
    |:----|:----|
    |autodiscover|autodiscover.outlook.com|

1. Zaznacz pole wyboru dla zastrzeżenia **I am aware** (Rozumiem).

1. Wybierz **Zapisz**.

### <a name="additional-cname-records"></a>Dodatkowe rekordy CNAME

Dodatkowe rekordy CNAME w poniższej procedurze umożliwiają Skype dla firm Online. Należy wykonać te same czynności co w przypadku dwóch rekordów CNAME, które zostały już utworzone.

**Tworzenie trzeciej poddomeny (Lyncdiscover)**

1.  W sekcji **Subdomain Overview (Przegląd poddomen** ) wybierz **pozycję Create Subdomain (Utwórz poddomenę**).

1.  W polu **Create Subdomain** (Utwórz poddomenę) dla nowej poddomeny wpisz lub skopiuj i wklej tylko wartość **Create Subdomain** (Utwórz poddomenę) z poniższej tabeli. (Wartość **Alias** dodasz w kolejnym kroku).

    |Create Subdomain (Utwórz poddomenę)|Alias|
    |:----|:----|
    |lyncdiscover|webdir.online.lync.com|

1.  Wybierz **pozycję Create Subdomain (Utwórz poddomenę**).

1.  Na stronie Domain Center (Centrum domen) wybierz pozycję **Manage Subdomains (Zarządzaj poddomenami**).

1.  W sekcji **Subdomain Overview (Przegląd** poddomen) znajdź poddomenę lyncdiscover, która właśnie została utworzona, a następnie wybierz kontrolkę Panel (v) dla tej poddomeny. W obszarze **Subdomain Ustawienia** (Poddomena) wybierz **pozycję Edit DNS Ustawienia (Edytuj rekordy DNS Ustawienia**).

1.  W sekcji **A/AAAA Records (IP Addresses) (Rekordy A/AAAA; adresy IP)** w obszarze **IP address (A Record) (Adres IP, rekord A)** wybierz pozycję **CNAME**.

1.  W polu **Alias** wpisz lub skopiuj i wklej tylko wartość **Alias** z poniższej tabeli.

    |Create Subdomain (Utwórz poddomenę)|Alias|
    |:----|:----|
    |lyncdiscover|webdir.online.lync.com|

1.  Zaznacz pole wyboru dla zastrzeżenia **I am aware (Rozumiem** ), a następnie wybierz pozycję **Save (Zapisz**).

1.  W **oknie dialogowym Edytowanie Ustawienia** DNS wybierz pozycję **Tak**.

**Tworzenie czwartej poddomeny (SIP)**

1.  W sekcji **Subdomain Overview (Przegląd poddomen** ) wybierz **pozycję Create Subdomain (Utwórz poddomenę**).

1.  W polu **Create Subdomain** (Utwórz poddomenę) dla nowej poddomeny wpisz lub skopiuj i wklej tylko wartość **Create Subdomain** (Utwórz poddomenę) z poniższej tabeli. (Wartość **Alias** dodasz w kolejnym kroku).

    |Create Subdomain (Utwórz poddomenę)|Alias|
    |:----|:----|
    |sip|sipdir.online.lync.com|  

1.  Wybierz **pozycję Create Subdomain (Utwórz poddomenę**).

1.  Na stronie Domain Center (Centrum domen) wybierz pozycję **Manage Subdomains (Zarządzaj poddomenami**).

1.  W sekcji **Subdomain Overview (Przegląd** poddomen) znajdź poddomenę sip, która właśnie została utworzona, a następnie wybierz kontrolkę Panel (v) dla tej poddomeny. <br/> W obszarze **Subdomain Ustawienia** (Poddomena) wybierz **pozycję Edit DNS Ustawienia (Edytuj rekordy DNS Ustawienia**).

1.  W sekcji **A/AAAA Records (IP Addresses) (Rekordy A/AAAA; adresy IP)** w obszarze **IP address (A Record) (Adres IP, rekord A)** wybierz pozycję **CNAME**.

1.  W polu **Alias** wpisz lub skopiuj i wklej tylko wartość **Alias** z poniższej tabeli.

    |Create Subdomain (Utwórz poddomenę)|Alias|
    |:----|:----|
    |sip|sipdir.online.lync.com|

1.  Zaznacz pole wyboru dla zastrzeżenia **I am aware (Rozumiem** ), a następnie wybierz pozycję **Save (Zapisz**).

1.  W **oknie dialogowym Edytowanie Ustawienia** DNS wybierz pozycję **Tak**.

### <a name="cname-records-needed-for-mdm"></a>Rekordy CNAME potrzebne dla usługi MDM

Postępuj zgodnie z procedurą ujmową dla czterech pozostałych rekordów CNAME, ale podać następujące wartości:

|Create Subdomain (Utwórz poddomenę)|Alias|
|:----|:----|
|enterpriseregistration|enterpriseregistration.windows.net|
|enterpriseenrollment|enterpriseenrollment-s.manage.microsoft.com|
