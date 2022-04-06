---
title: Sejf załączników
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: Admin
ms.date: ''
ms.topic: overview
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: 6e13311e-92ae-495e-a619-56d770199170
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
- seo-marvel-apr2020
description: Administratorzy mogą dowiedzieć się więcej o funkcji załączników Sejf w programie Microsoft Defender dla Office 365.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 01721d36967413a7f939d3618340e5630c3d6007
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2022
ms.locfileid: "63683806"
---
# <a name="safe-attachments-in-microsoft-defender-for-office-365"></a>Sejf załączników w programie Microsoft Defender dla Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Microsoft Defender dla Office 365 plan 1 i plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Sejf w programie [Microsoft Defender dla programu Office 365](defender-for-office-365.md) zapewnia dodatkową warstwę ochrony załączników wiadomości e-mail, które już były skanowane przez ochronę przed złośliwym oprogramowaniem w programie [Exchange Online Protection (EOP).](anti-malware-protection.md) W szczególności Sejf załączniki wykorzystują środowisko wirtualne do sprawdzania załączników w wiadomościach e-mail przed ich dostarczenia do adresatów (proces nazywany _detonacją_).

Sejf załączników wiadomości e-mail jest kontrolowana przez Sejf załączników. Chociaż nie istnieją domyślne zasady załączników załączników programu Sejf, wstępnie ustawione  zasady zabezpieczeń wbudowanej ochrony zapewniają ochronę załączników programu Sejf wszystkim adresatom (użytkownikom, którzy nie są zdefiniowani w niestandardowych zasadach załączników Sejf). Aby uzyskać więcej informacji, zobacz [Wstępnie ustawione zasady zabezpieczeń w usługach EOP i Microsoft Defender for Office 365](preset-security-policies.md). Możesz również tworzyć załączniki Sejf, które dotyczą konkretnych użytkowników, grup lub domen. Aby uzyskać instrukcje, [zobacz Konfigurowanie zasad Sejf załączników w programie Microsoft Defender for Office 365](set-up-safe-attachments-policies.md).

W poniższej tabeli opisano scenariusze dotyczące załączników programu Sejf w organizacjach Microsoft 365 i Office 365, które zawierają program Microsoft Defender dla programu Office 365 (innymi słowy, brak licencjonowania nigdy nie stanowi problemu w tych przykładach).

|Scenariusz|Result (Wynik)|
|---|---|
|W organizacji Microsoft 365 E5 Pat nie skonfigurowano żadnych Sejf załączników.|Pat jest chroniony Sejf załącznikami dzięki wstępnie ustawionym zasadom  zabezpieczeń Wbudowany ochrona, które dotyczą wszystkich adresatów, którzy nie są w inny sposób zdefiniowani w zasadach Sejf Załączniki.|
|Organizacja Lee ma zasady dotyczące załączników Sejf, które dotyczą tylko pracowników finansi. Lee jest członkiem działu sprzedaży.|Lee i pozostała część działu sprzedaży są chronieni przez załączniki programu Sejf dzięki wstępnie ustawionym zasadom zabezpieczeń Wbudowany ochrona, które mają zastosowanie do wszystkich adresatów, którzy nie są w inny sposób zdefiniowani w zasadach załączników Sejf wiadomości.|
|Wczoraj administrator w organizacji Marcin utworzył zasady załączników wiadomości Sejf dotyczące wszystkich pracowników. Wcześniej dziś Marcin otrzymał wiadomość e-mail z załącznikiem.|Marcin jest chroniony przez Sejf załączników ze względu na niestandardowe Sejf załączników. <p> Zazwyczaj nowe zasady są stosowane po około 30 minutach.|
|Organizacja krzysztofa ma od dawna zasady dotyczące załączników Sejf załączników dla wszystkich osób w organizacji. Michał otrzymuje wiadomość e-mail z załącznikiem, a następnie przesyła wiadomość dalej do adresatów zewnętrznych.|Chis jest chroniony przez Sejf załączników. <p> Jeśli adresaci zewnętrzni w organizacji Microsoft 365, wiadomości przekazane są również chronione przez załączniki Sejf wiadomości.|

Sejf Załączniki są skanowane w tym samym regionie, w Microsoft 365, w którym znajdują się Twoje dane. Aby uzyskać więcej informacji na temat lokalizacji geograficznych centrum danych, zobacz [Gdzie znajdują się Twoje dane?](https://products.office.com/where-is-your-data-located?geo=All)

> [!NOTE]
> Poniższe funkcje znajdują się w ustawieniach globalnych zasad załączników Sejf w portalu Microsoft 365 Defender załączników. Jednak te ustawienia są włączane lub wyłączane globalnie i nie wymagają przechowywania Sejf załączników:
>
> - [Sejf załączników do SharePoint, OneDrive i Microsoft Teams](mdo-for-spo-odb-and-teams.md).
> - [Bezpieczne dokumenty w usłudze Microsoft 365 E5](safe-docs.md)

## <a name="safe-attachments-policy-settings"></a>Sejf zasad Załączniki

W tej sekcji opisano ustawienia w zasadach Sejf załączników:

- **Sejf załączników odpowiedź z** nieznanym złośliwym oprogramowaniem: To ustawienie steruje akcją skanowania załączników złośliwym oprogramowaniem w Sejf e-mail. Dostępne opcje opisano w poniższej tabeli:

  |Opcja|Efekt|Użyj, gdy chcesz:|
  |---|---|---|
  |**Wyłączone**|Załączniki nie są skanowane w poszukiwaniu złośliwego oprogramowania przez Sejf załączników. Wiadomości są nadal skanowane w poszukiwaniu złośliwego oprogramowania za pomocą ochrony [przed złośliwym oprogramowaniem w uciekaniu poczty eOP](anti-malware-protection.md).|Wyłącz skanowanie wybranych adresatów. <p> Zapobieganie niepotrzebnym opóźnieniom routingu poczty wewnętrznej. <p> **Ta opcja nie jest zalecana w przypadku większości użytkowników. Tej opcji należy używać tylko w celu wyłączenia funkcji skanowania załączników Sejf w przypadku adresatów, którzy otrzymają tylko wiadomości od zaufanych nadawców. Zap nie będzie poddać wiadomościom kwarantanny Sejf załączniki zostaną wyłączone, a sygnał złośliwego oprogramowania nie zostanie odebrany. Aby uzyskać szczegółowe informacje, zobacz [Automatyczne czyszczenie o godzinie zero](zero-hour-auto-purge.md)**|
  |**Monitor**|Dostarcza wiadomości z załącznikami, a następnie śledzi to, co dzieje się przy użyciu wykrytego złośliwego oprogramowania. <p> Dostarczenie bezpiecznych wiadomości może się opóźnić ze względu na Sejf załączników.|Sprawdź, gdzie w organizacji znajduje się wykryte złośliwe oprogramowanie.|
  |**Blokuj**|Zapobiega dostarczaniu wiadomości z załącznikami z wykrytym złośliwym oprogramowaniem. <p> Wiadomości są poddane kwarantannie. Domyślnie tylko administratorzy (nie użytkownicy) mogą przeglądać, zwalniać lub usuwać wiadomości.<sup>\*</sup> <p> Automatycznie blokuje przyszłe wystąpienia wiadomości i załączników. <p> Dostarczenie bezpiecznych wiadomości może się opóźnić ze względu na Sejf załączników.|Chroni organizację przed powtarzających się atakami przy użyciu tych samych załączników złośliwego oprogramowania. <p> Jest to wartość domyślna i zalecana w przypadku standardowych i ściśle [wstępnie ustawionych zasad zabezpieczeń](preset-security-policies.md).|
  |**Zamień**|Usuwa wykryte załączniki złośliwego oprogramowania. <p> Powiadamia adresatów o usunięciu załączników. <p>  Wiadomości zawierające złośliwe załączniki są poddane kwarantannie. Domyślnie tylko administratorzy (nie użytkownicy) mogą przeglądać, zwalniać lub usuwać wiadomości.<sup>\*</sup> <p> Dostarczenie bezpiecznych wiadomości może się opóźnić ze względu na Sejf załączników.|Podnieś widoczność adresatom, że załączniki zostały usunięte z powodu wykrytego złośliwego oprogramowania.|
  |**Dostarczanie dynamiczne**|Natychmiast dostarcza wiadomości, ale zamienia załączniki na symbole zastępcze do Sejf załączników. <p> Wiadomości zawierające złośliwe załączniki są poddane kwarantannie. Domyślnie tylko administratorzy (nie użytkownicy) mogą przeglądać, zwalniać lub usuwać wiadomości.<sup>\*</sup> <p> Aby uzyskać szczegółowe informacje, zobacz sekcję Zasady dynamicznego [dostarczania Sejf](#dynamic-delivery-in-safe-attachments-policies) załączników w dalszej części tego artykułu.|Unikaj opóźnień wiadomości podczas ochrony adresatów przed złośliwymi plikami.|

  <sup>\*</sup>Administratorzy mogą tworzyć i przypisywać zasady _kwarantanny_ w Sejf załączników, które określają, co użytkownicy mogą robić w kwarantannie wiadomości. Aby uzyskać więcej informacji, zobacz [Zasady kwarantanny](quarantine-policies.md).

- **Przekieruj** załącznik po wykryciu: Włącz przekierowywanie i Wyślij załącznik na następujący adres e-mail **: W** przypadku akcji Blokuj **,** **Monitoruj** lub Zamień wysyłaj wiadomości zawierające załączniki złośliwego oprogramowania na określony wewnętrzny lub zewnętrzny adres e-mail do analizy.

  Zaleceniem dla ustawień zasad standardowych i ścisłych jest włączenie przekierowywania. Aby uzyskać więcej informacji, [zobacz Sejf Ustawienia załączników](recommended-settings-for-eop-and-office365.md#safe-attachments-settings).

- Zastosowanie powyższego **wyboru w** przypadku przecowania czasu skanowania w poszukiwaniu załączników lub wystąpienia błędu: Akcja określona przez program **Sejf** Sejf Załączniki w przypadku nieznanych reakcji złośliwego oprogramowania jest podejmowane na wiadomościach nawet wtedy, gdy skanowanie załączników nie może zostać ukończone. Zawsze zaznacz tę opcję, jeśli wybierzesz pozycję **Włącz przekierowywanie**. W przeciwnym razie wiadomości mogą zostać utracone.

- **Filtry adresatów**: Należy określić warunki i wyjątki adresata, które określają, kogo dotyczą zasady. Możesz użyć tych właściwości dla warunków i wyjątków:
  - **Adresatem jest**
  - **Domena adresata to**
  - **Adresat jest członkiem**

  Możesz użyć tylko raz warunku lub wyjątku, ale warunek lub wyjątek może zawierać wiele wartości. Wiele wartości takich samych warunków lub wyjątków używa logiki OR (na przykład _\<recipient1\>_ lub _\<recipient2\>_). W różnych warunkach lub wyjątkach jest używanie logiki AND (na przykład _\<recipient1\>_ i _\<member of group 1\>_).

- **Priorytet**: Jeśli tworzysz wiele zasad, możesz określić kolejność ich stosowania. Dwa zasady nie mogą mieć tego samego priorytetu i przetwarzanie zasad zostanie zatrzymane po zastosowaniu pierwszej zasady.

  Aby uzyskać więcej informacji na temat kolejności pierwszeństwa oraz sposobu oceniania i stosowania wielu zasad, zobacz Kolejność i [pierwszeństwo ochrony poczty e-mail](how-policies-and-protections-are-combined.md).

### <a name="dynamic-delivery-in-safe-attachments-policies"></a>Dynamiczne dostarczanie w Sejf załączników wiadomości

> [!NOTE]
> Dynamiczne dostarczanie działa tylko w przypadku Exchange Online pocztowych.

Akcja Dynamiczne dostarczanie w załącznikach Sejf ma na celu wyeliminowanie opóźnień dostarczania wiadomości e-mail, które mogą być spowodowane skanowaniem załączników w Sejf wiadomości. Treść wiadomości e-mail jest dostarczana do adresata z symbolem zastępczym dla każdego załącznika. Symbol zastępczy pozostaje do momentu, aż załącznik zostanie odnaleziony jako bezpieczny, a załącznik będzie dostępny do otwarcia lub pobrania.

Jeśli załącznik zostanie znaleziony jako złośliwy, wiadomość zostanie poddana kwarantannie.

Większość plików PDF i dokumentów Office można wyświetlać w trybie awaryjnym, gdy Sejf trakcie skanowania załączników. Jeśli załącznik jest niezgodny z programem podglądu dostarczania dynamicznego, do momentu zakończenia skanowania załączników adresaci zobaczą symbol zastępczy załącznika Sejf.

Jeśli korzystasz z urządzenia przenośnego i pliki PDF nie są renderowane w funkcji dynamicznego podglądu dostarczania na urządzeniu przenośnym, spróbuj otworzyć wiadomość w programie Outlook w sieci Web (dawniej znanym jako Outlook Web App) przy użyciu przeglądarki dla urządzeń przenośnych.

Oto niektóre zagadnienia dotyczące dostarczania dynamicznego i wiadomości przesyłanych dalej:

- Jeśli adresat przesyłany dalej jest chroniony za pomocą zasad załączników wiadomości Sejf, które korzysta z opcji Dostarczanie dynamiczne, adresat widzi symbol zastępczy z możliwością wyświetlania podglądu zgodnych plików.
- Jeśli adresat przesyłany dalej nie jest chroniony przez zasady załączników wiadomości Sejf, wiadomości i załączniki zostaną dostarczone bez żadnych Sejf zastępczych załączników lub zeskanowanych załączników.

Istnieją sytuacje, w których funkcja dostarczania dynamicznego nie może zamienić załączników w wiadomościach. Są to między innymi następujące scenariusze:

- Wiadomości w folderach publicznych.
- Wiadomości, które są kierowane z, a następnie z powrotem do skrzynki pocztowej użytkownika, przy użyciu reguł niestandardowych.
- Wiadomości przenoszone (automatycznie lub ręcznie) poza skrzynki pocztowe w chmurze do innych lokalizacji, w tym do folderów archiwum.
- Reguły skrzynki odbiorczej przenoszenie wiadomości ze skrzynki odbiorczej do innego folderu.
- Usunięte wiadomości.
- Folder wyszukiwania skrzynki pocztowej użytkownika jest w stanie błędu.
- Exchange Online organizacjach, w których włączono funkcję Odzyskaj. Aby rozwiązać ten problem, zobacz [KB4014438](https://support.microsoft.com/help/4014438).
- [S/MIME)](/exchange/security-and-compliance/smime-exo/smime-exo) zaszyfrowanych wiadomości.
- Akcję Dostarczanie dynamiczne skonfigurowano w zasadach Załączniki usługi Sejf, ale adresat nie obsługuje dostarczania dynamicznego (na przykład adresat jest skrzynką pocztową w organizacji Exchange organizacji). Jednak linki Sejf w programie [Microsoft Defender dla programu Office 365](set-up-safe-links-policies.md) mogą skanować załączniki plików programu Office zawierające adresy URL (w zależności od konfiguracji ustawień globalnych programu [Sejf](configure-global-settings-for-safe-links.md) Links).

## <a name="submitting-files-for-malware-analysis"></a>Przesyłanie plików na kątem analizy złośliwego oprogramowania

- Jeśli otrzymasz plik, który chcesz wysłać do firmy Microsoft w celu analizy, zobacz Przesyłanie do firmy Microsoft analiz złośliwego oprogramowania i oprogramowania, które nie jest [złośliwym oprogramowaniem](submitting-malware-and-non-malware-to-microsoft-for-analysis.md).
- Jeśli otrzymasz wiadomość e-mail (z załącznikiem lub bez niego), którą chcesz przesłać do firmy Microsoft w celu analizy, zobacz Zgłaszanie wiadomości [i plików do firmy Microsoft](report-junk-email-messages-to-microsoft.md).
