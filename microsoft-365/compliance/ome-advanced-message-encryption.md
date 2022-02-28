---
title: Zaawansowane szyfrowanie wiadomości
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.date: 08/11/2021
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MET150
description: Zaawansowane szyfrowanie wiadomości ułatwia organizacjom spełnienie wymagań dotyczących zgodności, umożliwiając administratorom jeszcze większe możliwości związane z chronionymi wiadomościami.
ms.openlocfilehash: 9e0f1933d68ba696e6446b321857eb3f6836f378
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62986409"
---
# <a name="advanced-message-encryption"></a>Zaawansowane szyfrowanie wiadomości

Zaawansowane szyfrowanie wiadomości usługi Office 365 jest zawarta w usługach [Microsoft 365 Enterprise E5](https://www.microsoft.com/microsoft-365/enterprise/home), Office 365 E5 i Microsoft 365 E5 (Nonprofit Staff Pricing), Office 365 Enterprise E5 (Nonprofit Staff Pricing) i Office 365 Education A5. Jeśli Twoja organizacja ma subskrypcję, która nie zawiera subskrypcji usługi Zaawansowane szyfrowanie wiadomości usługi Office 365, możesz ją kupić za pomocą dodatku Zgodność platformy Microsoft 365 E5 SKU dla Microsoft 365 E3, Microsoft 365 E3 (Nonprofit Staff Pricing) lub dodatku Office 365 Advanced Compliance SKU dla usług Microsoft 365 E3, Microsoft 365 E3 (Nonprofit Staff Pricing), Office 365 jednostki SKU produktów lub Microsoft 365 E5/A5 dodatku do SKU ochrony informacji i zarządzania dla systemu Microsoft 365 A3/E3.

Zaawansowane szyfrowanie wiadomości ułatwia klientom spełnienie wymagań dotyczących zgodności, które wymagają bardziej elastycznej kontroli nad adresatami zewnętrznymi i ich dostępu do zaszyfrowanych wiadomości e-mail. Dzięki funkcji zaawansowanego szyfrowania wiadomości Office 365 możesz kontrolować poufne wiadomości e-mail udostępniane poza organizacją przy użyciu automatycznych zasad. Te zasady są konfigurowane w celu identyfikowania typów informacji poufnych, takich jak identyfikatory PII, identyfikatory finansowe lub identyfikatory kondycji, albo można używać słów kluczowych w celu zwiększenia ochrony. Po skonfigurowaniu zasad możesz sparować zasady z niestandardowymi, znakowanych szablonami wiadomości e-mail, a następnie dodać datę wygaśnięcia, aby uzyskać dodatkową kontrolę nad wiadomościami e-mail, które pasują do zasad. Ponadto administratorzy mogą dodatkowo kontrolować zaszyfrowane wiadomości e-mail uzyskiwane do nich zewnętrznie za pośrednictwem bezpiecznego portalu sieci Web przez odwołanie dostępu do poczty w dowolnym momencie.

Datę wygaśnięcia można odwołać i ustawić tylko w przypadku wiadomości e-mail wysyłanych do adresatów zewnętrznych.

## <a name="get-started-with-office-365-advanced-message-encryption"></a>Wprowadzenie do Zaawansowane szyfrowanie wiadomości usługi Office 365

W poniższych artykułach opisano sposób skonfigurowania zaawansowanego szyfrowania wiadomości i korzystania z nich.

Twoja organizacja musi mieć subskrypcję, która obejmuje Zaawansowane szyfrowanie wiadomości usługi Office 365. Aby uzyskać szczegółowe informacje na temat obsługiwanych subskrypcji, zobacz Opis [usługi zasad wiadomości i zgodności](/office365/servicedescriptions/exchange-online-service-description/message-policy-and-compliance).

Jeśli nie masz jeszcze Szyfrowanie wiadomości usługi Office 365, zobacz [Konfigurowanie nowych i Szyfrowanie wiadomości usługi Office 365 możliwości](set-up-new-message-encryption-capabilities.md).

Dzięki funkcji zaawansowanego szyfrowania wiadomości możesz nie ograniczać się do jednego szablonu  marki. Zamiast tego można utworzyć wiele szablonów marki i używać ich. Aby uzyskać informacje, [zobacz Dodawanie marki organizacji do zaszyfrowanych wiadomości](add-your-organization-brand-to-encrypted-messages.md). W przypadku używania niestandardowych  brandingów adresaci zewnętrzni otrzymają powiadomienie e-mail zawierające link do portalu OME. Reguła przepływu poczty e-mail określa, którego szablonu  brandingu używają wiadomości e-mail z powiadomieniem i portalu OME. Dzięki temu bezpieczna zawartość nie jest wysyłana poza organizację.

Możesz odwołać wiadomości i zastosować daty wygaśnięcia tylko do wiadomości, które użytkownicy otrzymują za pośrednictwem portalu. Innymi słowy, wiadomość e-mail z zastosowanym niestandardowym szablonem  marki. Aby uzyskać więcej informacji i przykład, zobacz wskazówki w tece Zapewnianie, że wszyscy adresaci zewnętrzni używają [portalu OME do odczytywania zaszyfrowanej poczty](manage-office-365-message-encryption.md#ensure-all-external-recipients-use-the-ome-portal-to-read-encrypted-mail).

[Ustaw datę wygaśnięcia zaszyfrowanej wiadomości e-mail, Zaawansowane szyfrowanie wiadomości usługi Office 365](ome-advanced-expiration.md). Kontrolowanie poufnych wiadomości e-mail udostępnionych na zewnątrz organizacji za pomocą automatycznych zasad zwiększających ochronę przez wygasanie dostępu za pośrednictwem bezpiecznego portalu sieci Web do zaszyfrowanych wiadomości e-mail.

[Odwołaj wiadomości e-mail zaszyfrowane za pomocą Zaawansowane szyfrowanie wiadomości usługi Office 365](revoke-ome-encrypted-mail.md). Kontrolowanie poufnych wiadomości e-mail udostępnionych poza organizacją i zwiększanie ochrony przez odwołanie dostępu za pośrednictwem bezpiecznego portalu sieci Web do zaszyfrowanych wiadomości e-mail.  
