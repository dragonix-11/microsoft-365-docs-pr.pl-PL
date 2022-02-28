---
title: Scheduler for Microsoft 365 FAQ
ms.author: v-aiyengar
author: AshaIyengar21
manager: serdars
audience: Admin
ms.topic: article
ms.service: scheduler
ms.localizationpriority: medium
description: Scheduler for Microsoft 365 FAQ
ms.openlocfilehash: 2392c48de3d80cf41d179eb053c46967626b5159
ms.sourcegitcommit: bf3965b46487f6f8cf900dd9a3af8b213a405989
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2021
ms.locfileid: "62989731"
---
# <a name="scheduler-for-microsoft-365-faq"></a>Scheduler for Microsoft 365 FAQ

**Pytanie:** Jak program Scheduler integruje się z innymi Cortana, takimi jak program *Cortana for Windows**, krótki* adres e-mail i odtwarzanie wiadomości *e-mail*?</br>
Scheduler to usługa niezależna od innych funkcji Cortana funkcje. Inne Cortana usługi mogą być wyłączone na poziomie dzierżawy, a program Scheduler nadal można włączyć przy użyciu cortana@yourdomain.com e-mail. Obecnie użytkownicy mogą wchodzić w interakcje z programem Scheduler tylko za pośrednictwem poczty e-mail.

**Pytanie:** Czy ta działa tylko w Outlook? Czy inne produkty poczty e-mail są obsługiwane?</br>
O ile masz licencję, inną niż trzy powyższe wymagania, użytkownicy mogą wysyłać wiadomości e-mail cortana@yourdomain.com e-mail z dowolnego klienta poczty e-mail na dowolnym urządzeniu.

**Pytanie:** Czy kontakty mogą się znaleźć na osobistej liście Outlook liście adresowej i na liście adresowej lub w innym odpowiedniku w firmie?</br>
Uczestnikami spotkania może być każdy, kto ma adres e-mail w firmie lub poza nim. Niestety, program Scheduler nie może automatycznie tłumaczyć nazw na adresy e-mail/aliasy, patrząc obecnie na galę adresową.

**Pytanie:** Czy mogę używać programu Scheduler z zainstalowaną (lokalną) wersją programu Outlook?</br>
Program Scheduler wymaga Exchange Online. Nie działa z Exchange Server (w pre-prem). Współpracuje z dowolnym klientem poczty e-mail, Outlook, OWA, iOS, android, gmail i tak dalej.

**Pytanie:** Czy Outlook być otwarte w tle?</br>
Outlook nie muszą być otwarte w tle. Wystarczy wysłać wiadomość e-mail Cortana i polegać na tym, aby wykonać większość pracy.

## <a name="frequently-asked-trust-and-privacy-questions"></a>Często zadawane pytania dotyczące zaufania i prywatności

**Pytanie:** Jak działa program Scheduler?</br>
Program Scheduler korzysta z funkcji analizy planowania (AI, Scheduling Intelligence) rozszerzonych o asystentów ludzkich. Jeśli modele AI wygenerowały potrzebę obsługi w naturalnym języku komunikacji z programem Cortana, wezwanie na spotkanie eskalacji na użytkownika w celu jego przejrzenia i ukończenia.

**Pytanie:** KtoTo jest tym, co przegląda eskalowane żądania? </br>
Asystenci harmonogramu programu Microsoft Supplier Security and Privacy Assurance (SSPA) są certyfikowani do obsługi informacji osobistych i ściśle poufnych.

**Pytanie:** Co mogą wyświetlać asystenci SSPA?</br>
Program Scheduler i asystenci SSPA mogą wyświetlać wiadomości e-mail zaadresowane do Cortana. W przypadku wymiany wiadomości e-mail z wątkami będą przetwarzane tylko Cortana e-mail, które zawierają adres e-mail użytkownika, a nie poprzednie wiadomości e-mail z wątku przed Cortana.

**Pytanie:** Czy dane klienta są zachowywane w harmonogramie danych Flow? </br>
Program Scheduler przechowuje całą zawartość klienta w granicach dzierżawy i zachowuje dane zgodnie z wytycznymi RODO Microsoft 365, zasady zaufania & prywatności i zasady poczty e-mail dzierżawy.

**Pytanie:** Jak program Scheduler przetwarza dane wolny/zajęty uczestników wewnętrznych? </br>
Automatyzacja narzędzia Scheduler używa usługi *findMeetingTimes do* identyfikowania wzajemnie dostępnych godzin dla uczestników i organizatora. Ta usługa jest potęgowana Outlook innych możliwości, takich jak *Sugerowane* godziny w formularzu Outlook spotkania. Informacje o wolnych/zajętych uczestnikach nie są używane jawnie jako bloki wolny/zajęty.

**Pytanie:** Czy harmonogram jest zgodny z RODO? </br>
Tak.

**Pytanie:** KtoTo ma dostęp do skrzynki Cortana pocztowej? </br>
Program Scheduler przetwarza wezwania na spotkania i skojarzone z nimi wiadomości e-mail wysyłane do skrzynki Cortana dzierżawy. Firma Microsoft nie ma żadnego innego dostępu do skrzynki Cortana pocztowej za pośrednictwem zatwierdzenia skrytki na żądanie administratora dzierżawy.

**Pytanie:** Czy dane klienta są używane do szkoleń dotyczących modeli ze źródła danych?</br>
Żadnej zawartości klienta z programu Scheduler Microsoft 365 nie można używać do zestawów szkoleniowych dotyczących danych. Cała zawartość klienta znajduje się w dzierżawie klienta.

**Pytanie:** Czy program Scheduler będzie przetwarzał zaszyfrowaną pocztę?</br>
Nie, zaszyfrowana poczta zostanie odrzucona przez przepływ pracy Harmonogram.
