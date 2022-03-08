---
title: Szyfrowanie usługi
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.date: 10/3/2019
ms.localizationpriority: ''
search.appverid:
- MET150
ms.collection: Strat_O365_Enterprise
description: 'Podsumowanie: należy zrozumieć odporność danych w Microsoft Office 365.'
ms.openlocfilehash: 54bae9fa0203d76c598c4dee337ee15f24a2fc24
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63317643"
---
# <a name="service-encryption"></a>Szyfrowanie usługi

Oprócz szyfrowania na poziomie głośności, Exchange Online, Microsoft Teams, SharePoint Online i OneDrive dla Firm szyfrowanie usług do szyfrowania danych klienta. Szyfrowanie usługi umożliwia korzystanie z dwóch kluczowych opcji zarządzania:

## <a name="microsoft-managed-keys"></a>Klucze zarządzane przez firmę Microsoft
Firma Microsoft zarządza wszystkimi kluczami kryptograficznymi, w tym kluczami głównymi do szyfrowania usługi. Ta opcja jest obecnie włączona domyślnie dla Exchange Online, SharePoint Online, OneDrive dla Firm. Klucze zarządzane przez firmę Microsoft zapewniają domyślne szyfrowanie usługi, chyba że zdecydujesz się na użycie klucza klienta. Jeśli w późniejszym terminie zdecydujesz się przestać korzystać z klucza klienta bez podążania za ścieżką przeczyszczania danych, Twoje dane pozostają zaszyfrowane przy użyciu kluczy zarządzanych przez firmę Microsoft. Dane są zawsze szyfrowane na tym domyślnym poziomie co najmniej. 

## <a name="customer-key"></a>Klucz klienta
Ty dostarczasz klucze główne używane z szyfrowaniem usługi i zarządzasz nimi przy użyciu magazynu kluczy platformy Azure. Wszystkimi innymi kluczami zarządza firma Microsoft. Ta opcja nosi nazwę Klucz klienta i jest obecnie dostępna dla Exchange Online, SharePoint Online i OneDrive dla Firm. (Wcześniej nazywane szyfrowaniem zaawansowanym przy użyciu funkcji BYOK. Zobacz [Zwiększanie przejrzystości i kontroli nad Office 365 dla klientów,](https://www.microsoft.com/en-us/microsoft-365/blog/2015/04/21/enhancing-transparency-and-control-for-office-365-customers/) aby uzyskać oryginalne ogłoszenie).

Szyfrowanie usługi zapewnia wiele korzyści:

- Zapewnia dodatkową warstwę ochrony na funkcji BitLocker.

- Zapewnia wyciągi Windows systemu operacyjnego z dostępu do danych aplikacji przechowywanych lub przetwarzanych przez system operacyjny.

- Zawiera opcję Klucz klienta, która umożliwia usługom w wielu dzierżawach zarządzanie kluczami dla 1 dzierżawy.

- Zwiększa możliwość spełniania Microsoft 365 wymagań klientów, którzy mają określone wymagania dotyczące zgodności z przepisami dotyczące szyfrowania.

Za pomocą klucza klienta można generować własne klucze kryptograficzne przy użyciu lokalnego modułu usługi sprzętowej (HSM) lub magazynu kluczy platformy Azure (AKV). Niezależnie od sposobu wygenerowania klucza akv służy do kontrolowania kluczy kryptograficznych używanych przez funkcje szyfrowania i zarządzania nimi Office 365. Klucze przechowywane w aplikacji AKV mogą być używane jako katalog główny jednego z kluczy szyfrujący dane lub pliki skrzynki pocztowej.

Inną zaletą klucza klienta jest kontrola nad możliwością przetwarzania danych przez firmę Microsoft. Jeśli chcesz usunąć dane z usługi Office 365, na przykład jeśli chcesz zakończyć usługę z firmą Microsoft lub usunąć część danych przechowywanych w chmurze, możesz to zrobić i użyć klucza klienta jako kontroli technicznej. Usunięcie danych gwarantuje, że nikt, w tym firma Microsoft, nie będzie miał dostępu do tych danych ani ich nie przetwarzał. Klucz klienta jest uzupełnieniem funkcji Skrytka klienta, która umożliwia kontrolowanie dostępu do danych przez pracowników firmy Microsoft.

Aby dowiedzieć się, jak skonfigurować klucz klienta dla Microsoft 365 dla usług Exchange Online, Microsoft Teams i SharePoint Online, w tym witryn  zespołu i OneDrive dla Firm, zobacz następujące artykuły:

- [Szyfrowanie usługi przy użyciu klucza klienta](customer-key-overview.md)

- [Konfigurowanie klucza klienta](customer-key-set-up.md)

- [Zarządzanie kluczem klienta](customer-key-manage.md)

- [Obracanie lub obracanie klucza klienta lub klucza dostępności](customer-key-availability-key-roll.md)

- [Opis klucza dostępności](customer-key-availability-key-understand.md)
