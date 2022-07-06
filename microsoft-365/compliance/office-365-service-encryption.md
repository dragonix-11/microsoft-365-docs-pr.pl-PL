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
description: 'Podsumowanie: Omówienie odporności danych w Microsoft Office 365.'
ms.openlocfilehash: 66899a337e9349a78178df67aa83e44b580c7148
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66629384"
---
# <a name="service-encryption"></a>Szyfrowanie usługi

Oprócz szyfrowania na poziomie woluminu Exchange Online, Microsoft Teams, SharePoint Online i OneDrive dla Firm również używają szyfrowania usługi do szyfrowania danych klientów. Szyfrowanie usługi umożliwia dwie opcje zarządzania kluczami:

## <a name="microsoft-managed-keys"></a>Klucze zarządzane przez firmę Microsoft
Firma Microsoft zarządza wszystkimi kluczami kryptograficznymi, w tym kluczami głównymi szyfrowania usługi. Ta opcja jest obecnie domyślnie włączona dla Exchange Online, SharePoint Online OneDrive dla Firm. Klucze zarządzane przez firmę Microsoft zapewniają domyślne szyfrowanie usługi, chyba że zdecydujesz się dołączyć przy użyciu klucza klienta. Jeśli w późniejszym terminie zdecydujesz się na zaprzestanie korzystania z klucza klienta bez korzystania ze ścieżki przeczyszczania danych, dane pozostaną zaszyfrowane przy użyciu kluczy zarządzanych przez firmę Microsoft. Dane są zawsze szyfrowane na tym domyślnym poziomie co najmniej. 

## <a name="customer-key"></a>Klucz klienta
Podasz klucze główne używane z szyfrowaniem usługi i zarządzasz tymi kluczami przy użyciu usługi Azure Key Vault. Firma Microsoft zarządza wszystkimi innymi kluczami. Ta opcja nosi nazwę Klucz klienta i jest obecnie dostępna dla Exchange Online, SharePoint Online i OneDrive dla Firm. (Wcześniej nazywane szyfrowaniem zaawansowanym za pomocą usługi BYOK. Zobacz [Zwiększanie przejrzystości i kontroli dla klientów Office 365](https://www.microsoft.com/en-us/microsoft-365/blog/2015/04/21/enhancing-transparency-and-control-for-office-365-customers/), aby zapoznać się z oryginalnym ogłoszeniem).

Szyfrowanie usługi zapewnia wiele korzyści:

- Zapewnia dodatkową warstwę ochrony na BitLocker.

- Zapewnia oddzielenie administratorów systemu operacyjnego Windows od dostępu do danych aplikacji przechowywanych lub przetwarzanych przez system operacyjny.

- Zawiera opcję Klucz klienta, która umożliwia usługom wielodostępnym zapewnianie zarządzania kluczami dla dzierżawy.

- Zwiększa możliwość rozwiązania Microsoft 365 w celu spełnienia wymagań klientów, którzy mają określone wymagania dotyczące zgodności dotyczące szyfrowania.

Klucz klienta umożliwia generowanie własnych kluczy kryptograficznych przy użyciu lokalnego modułu usługi sprzętowej (HSM) lub usługi Azure Key Vault (AKV). Niezależnie od sposobu generowania klucza używasz usługi AKV do kontrolowania kluczy kryptograficznych używanych przez Office 365 i zarządzania nimi. Gdy klucze są przechowywane w usłudze AKV, mogą być używane jako katalog główny jednego z pęku kluczy, który szyfruje dane lub pliki skrzynki pocztowej.

Kolejną zaletą klucza klienta jest kontrola nad możliwością przetwarzania danych przez firmę Microsoft. Jeśli chcesz usunąć dane z Office 365, na przykład jeśli chcesz zakończyć usługę z firmą Microsoft lub usunąć część danych przechowywanych w chmurze, możesz to zrobić i użyć klucza klienta jako kontroli technicznej. Usunięcie danych gwarantuje, że nikt, w tym firma Microsoft, nie może uzyskiwać dostępu do danych ani przetwarzać ich. Klucz klienta stanowi uzupełnienie skrytki klienta używanej do kontrolowania dostępu do danych przez personel firmy Microsoft.

Aby dowiedzieć się, jak skonfigurować klucz klienta dla platformy Microsoft 365 dla usług Exchange Online, Microsoft Teams, SharePoint Online, w tym witryny zespołu i OneDrive dla Firm, zobacz następujące artykuły:

- [Szyfrowanie usługi przy użyciu klucza klienta](customer-key-overview.md)

- [Konfigurowanie klucza klienta](customer-key-set-up.md)

- [Zarządzanie kluczem klienta](customer-key-manage.md)

- [Rzutowanie lub obracanie klucza klienta lub klucza dostępności](customer-key-availability-key-roll.md)

- [Omówienie klucza dostępności](customer-key-availability-key-understand.md)
