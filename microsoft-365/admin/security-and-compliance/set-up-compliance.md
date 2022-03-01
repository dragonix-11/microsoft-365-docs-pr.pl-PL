---
title: Zwiększanie ochrony przed zagrożeniami dla Microsoft 365 Business Premium
f1.keywords:
- NOCSH
ms.author: sharik
author: skjerland
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- M365-identity-device-management
- Adm_TOC
ms.custom:
- MiniMaven
- MSB365
- OKR_SMB_M365
- seo-marvel-mar
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
description: Skonfiguruj funkcje zgodności, aby zapobiec utracie danych i zapewnić bezpieczeństwo poufnych informacji Twoich i Twoich klientów.
ms.openlocfilehash: 69960c4f158a30d9d47d749ed1e7eb2d2d74f430
ms.sourcegitcommit: b6ab10ba95e4b986065c51179ead3810cc1e2a85
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/15/2021
ms.locfileid: "63017853"
---
# <a name="set-up-compliance-features"></a>Konfigurowanie funkcji zgodności

Twój Microsoft 365 Business Premium ma funkcje ochrony danych i urządzeń oraz pomaga zabezpieczyć poufne informacje Twoich i klientów.

## <a name="watch-set-up-dlp-features"></a>Obejrzyj: Konfigurowanie funkcji DLP

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE3TGvL?autoplay=false]

Zasady ochrony przed utratą danych pomagają identyfikować i chronić poufne informacje firmy, takie jak numery PESEL czy dokumentacja medyczna.

1. Aby rozpocząć, przejdź do centrum [administracyjnego](https://admin.microsoft.com) i wybierz pozycję **Konfiguracja**.
1. Przewiń w dół **do strony Konfigurowanie ochrony przed utratą danych**, a następnie wybierz pozycję **Wyświetl**, a następnie pozycję **Zarządzaj**.
1. Aby edytować zasady, zaznacz je, wybierz **pozycję Edytuj zasady**, a następnie wybierz, co chcesz zmienić. Na przykład wybierz **pozycję Lokalizacje,** aby zmienić skanowane informacje.
1. Aby utworzyć nowe zasady, wybierz **pozycję Utwórz zasady**.
1. Możesz utworzyć zasady niestandardowe lub rozpocząć od szablonu. Aby na przykład utworzyć zasady HIPAA, wybierz szablon Medyczne i  medyczne, a następnie wybierz pozycję Amerykańska ustawa **hipaazyjna (HIPAA**). Wybierz pozycję **Dalej**.
1. Przejrzyj ustawienia i wybierz pozycję **Utwórz**. Gdy zasady zajdą w życie, wiadomości e-mail zawierające opisane informacje poufne będą blokowane, a nadawca, który próbował wysłać te informacje, zobaczy komunikat ostrzegawczy.

Zobacz [Tworzenie zasad DLP](../../compliance/create-a-dlp-policy-from-a-template.md) na podstawie szablonu, aby uzyskać przykład sposobu skonfigurowania zasad w celu ochrony przed utratą danych osobowych. 
  
Zasady DLP są dostępne z wieloma gotowymi do użycia szablonami zasad dla wielu różnych lokalizacji regionalnych. Na przykład Australia Financial Data, Canada Personal Information Act, Us.S. Financial Data i tak dalej. Zobacz [Co zawierają szablony zasad DLP](../../compliance/what-the-dlp-policy-templates-include.md) , aby uzyskać pełną listę. Wszystkie te szablony można włączyć podobnie jak w przykładzie szablonu piI.
 
## <a name="set-up-email-retention-with-exchange-online-archiving"></a>Konfigurowanie przechowywania poczty e-mail przy użyciu Exchange Online — archiwum

 **Exchange Online — archiwum** funkcje licencji pomagają w zachowaniu zgodności z normami i przepisami prawa, zachowując zawartość wiadomości e-mail na rzecz zbierania elektronicznych materiałów dowodowych. Pomaga to również zmniejszyć ryzyko w przypadku wystąpienia do sądu i umożliwia odzyskanie danych po naruszeniu zabezpieczeń lub potrzebie odzyskania usuniętych elementów. Aby zachować całą zawartość użytkownika, możesz użyć funkcji postępowania sądowego lub zasad przechowywania, aby dostosować to, co chcesz zachować.
  
**Zawieszenie w postępowaniem sądowym:** Całą zawartość skrzynki pocztowej, w tym elementy usunięte, można zachować, umieszczając całą skrzynkę pocztową użytkownika na postępowaniem sądowym. 
    
Aby umieścić skrzynkę pocztową w związku z postępowaniem sądowym, w centrum administracyjnym:
    
1. W lewym okienku narracji przejdź do **strony Użytkownicy Aktywni** \> **użytkownicy**.
    
2. Wybierz użytkownika, którego skrzynkę pocztową chcesz umieścić w postępowaniem sądowym. W okienku użytkownika rozwiń **pozycję Ustawienia poczty**, a następnie obok **przycisku Więcej** ustawień wybierz pozycję **Edytuj Exchange właściwości**.
    
3. Na stronie skrzynki pocztowej dla użytkownika wybierz ** funkcje skrzynki pocztowej ** w lewym obszarze wyszukiwania, a następnie **wybierz link Włącz** w obszarze Zawieszenie **w związku z postępowaniem sądowym**.
    
4. W **oknie dialogowym Zawieszenie** w związku z postępowaniem sądowym w polu Czas trwania trwania w związku z postępowaniem sądowym możesz określić czas trwania trwania w związku z postępowaniem **sądowym** . Pozostaw to pole puste, jeśli chcesz umieścić nieskończoną przestrzeń. Możesz również dodawać notatki i kierować właściciela skrzynki pocztowej do witryny internetowej, w przypadku których może być konieczne dodatkowe wyjaśnienie dotyczące postępowania sądowego. \>**Zapisz**.
    
**Przechowywanie:** Można włączyć niestandardowe zasady przechowywania, na przykład w celu zachowania określonego czasu lub trwałego usuwania zawartości na koniec okresu przechowywania. Aby dowiedzieć się więcej, zobacz [Omówienie zasad przechowywania](../../compliance/retention.md).

## <a name="watch-set-up-sensitivity-labels"></a>Obejrzyj: Konfigurowanie etykiet wrażliwości

Etykiety wrażliwości są dostępne w ramach usługi Azure Information Protection (AIP, Azure Information Protection) (plan 1) i pomagają klasyfikować oraz opcjonalnie chronić dokumenty i wiadomości e-mail, stosując etykiety. Etykiety mogą być stosowane automatycznie przez administratorów definiujących reguły i warunki, ręcznie przez użytkowników lub za pomocą kombinacji, w której użytkownicy mają zalecenia.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE3VRGT?autoplay=false]

1. W centrum [administracyjnym](https://admin.microsoft.com) wybierz pozycję **Centrum administracyjne** zgodności.
1. Wybierz **pozycję Klasyfikacja**, a następnie **Etykiety wrażliwości**.
1. Wybierz **pozycję Utwórz etykietę, a** gdy zostanie wyświetlone ostrzeżenie, wybierz pozycję **Tak**.
1. Przejrzyj ustawienia i wybierz pozycję **Utwórz**. Twoja etykieta została utworzona. Powtórz tę procedurę dla wszystkich dodatkowych etykiet.
1. Domyślnie etykiety są wyświetlane w Office w kolejności: **Poufne**, **Wewnętrzne** i **Publiczne**. Aby zmienić kolejność, dla każdej etykiety wybierz trzy kropki (więcej akcji), a następnie przenieś etykietę w górę lub w dół. Zazwyczaj uprawnienia znajdują się na liście od najniższego do najwyższego poziomu uprawnień.
1. Przejrzyj ustawienia, a następnie wybierz pozycję **Opublikuj**.

Aby etykiety działały, każdy użytkownik musi pobrać ujednoliconego klienta etykiet usługi Azure Information Protection. Wyszukaj w Internecie plik **AzinfoProtection_UL.exe**, a następnie pobierz go z Centrum pobierania Microsoft i uruchom na komputerach użytkowników.

Przy następnym otwarciu aplikacja pakietu Office, na przykład programu Word, zobaczysz utworzone etykiety wrażliwości. Aby zmienić lub zastosować etykietę, wybierz pozycję Charakter, a następnie wybierz etykietę.

### <a name="install-the-azure-information-protection-client-manually"></a>Ręczne instalowanie klienta usługi Azure Information Protection

Aby ręcznie zainstalować klienta AIP:

1. Pobierz **AzinfoProtection_UL.exe** z [Centrum pobierania Microsoft](https://www.microsoft.com/download/details.aspx?id=53018).
 
2. Możesz sprawdzić, czy instalacja się działała, wyświetlając dokument programu Word i upewnijąc  się, że opcja Charakter jest dostępna na **karcie Narzędzia** główne.
<br/>![Lista rozwijana na karcie Ochrona w dokumencie programu Word.](../../media/word-sensitivity.png)

Aby uzyskać więcej informacji, [zobacz Instalowanie klienta](/azure/information-protection/infoprotect-tutorial-step3).