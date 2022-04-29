---
title: załączniki Sejf
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
description: Administratorzy mogą dowiedzieć się więcej o funkcji załączników Sejf w Ochrona usługi Office 365 w usłudze Microsoft Defender.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 9d069d92eb012211af8dd4e12109ebcae7eb221e
ms.sourcegitcommit: fdd0294e6cda916392ee66f5a1d2a235fb7272f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/29/2022
ms.locfileid: "65128723"
---
# <a name="safe-attachments-in-microsoft-defender-for-office-365"></a>Sejf załączników w Ochrona usługi Office 365 w usłudze Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Usługi Microsoft Defender dla usługi Office 365 (plan 1 i plan 2)](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Sejf Załączniki w [Ochrona usługi Office 365 w usłudze Microsoft Defender](defender-for-office-365.md) zapewnia dodatkową warstwę ochrony załączników wiadomości e-mail, które zostały już przeskanowane za pomocą [ochrony przed złośliwym oprogramowaniem w Exchange Online Protection (EOP)](anti-malware-protection.md). W szczególności Sejf Załączniki używają środowiska wirtualnego do sprawdzania załączników w wiadomościach e-mail przed ich dostarczeniem do adresatów (proces znany jako _detonacja_).

Sejf ochrona załączników dla wiadomości e-mail jest kontrolowana przez zasady załączników Sejf. Mimo że nie ma domyślnych zasad Sejf Załączniki, wbudowane zasady zabezpieczeń **wstępnie ustawione ochrony** zapewniają ochronę Sejf załączników wszystkim adresatom (użytkownikom, którzy nie są zdefiniowani w niestandardowych zasadach załączników Sejf). Aby uzyskać więcej informacji, zobacz [Preset security policies in EOP and Ochrona usługi Office 365 w usłudze Microsoft Defender (Ustawienia wstępne zasad zabezpieczeń w usłudze EOP i Ochrona usługi Office 365 w usłudze Microsoft Defender](preset-security-policies.md)). Możesz również utworzyć zasady Sejf Załączniki, które mają zastosowanie do określonych użytkowników, grup lub domen. Aby uzyskać instrukcje, zobacz [Konfigurowanie zasad załączników Sejf w Ochrona usługi Office 365 w usłudze Microsoft Defender](set-up-safe-attachments-policies.md).

W poniższej tabeli opisano scenariusze dotyczące załączników Sejf w organizacjach Microsoft 365 i Office 365, które obejmują Ochrona usługi Office 365 w usłudze Microsoft Defender (innymi słowy brak licencji nigdy nie jest problemem w przykładach).

|Scenariusz|Result (Wynik)|
|---|---|
|Organizacja Microsoft 365 E5 pata nie ma skonfigurowanych zasad załączników Sejf.|Pat jest chroniony przez Sejf Załączniki ze względu na **wbudowane** zasady zabezpieczeń wstępnie ustawione ochrony, które mają zastosowanie do wszystkich adresatów, którzy nie są inaczej zdefiniowane w zasadach załączników Sejf.|
|Organizacja Lee ma zasady załączników Sejf, które mają zastosowanie tylko do pracowników finansowych. Lee jest członkiem działu sprzedaży.|Lee i reszta działu sprzedaży są chronione przez Sejf Załączniki ze względu na wbudowane zasady zabezpieczeń wstępnie ustawione **ochrony**, które mają zastosowanie do wszystkich adresatów, którzy nie są inaczej zdefiniowane w zasadach załączników Sejf.|
|Wczoraj administrator w organizacji Jean utworzył zasady załączników Sejf, które mają zastosowanie do wszystkich pracowników. Wcześniej dzisiaj Jean otrzymał wiadomość e-mail zawierającą załącznik.|Jean jest chroniony przez załączniki Sejf dzięki tym niestandardowym zasadom załączników Sejf. <br/><br/> Zwykle zastosowanie nowych zasad zajmuje około 30 minut.|
|Organizacja Chrisa od dawna Sejf zasad załączników dla wszystkich w organizacji. Chris otrzymuje wiadomość e-mail z załącznikiem, a następnie przekazuje wiadomość do zewnętrznych adresatów.|Chis jest chroniony przez załączniki Sejf. <br/><br/> Jeśli adresaci zewnętrzni w organizacji Microsoft 365, przekazywane komunikaty są również chronione przez Sejf Załączniki.|

Sejf Skanowanie załączników odbywa się w tym samym regionie, w którym znajdują się dane Microsoft 365. Aby uzyskać więcej informacji na temat lokalizacji geograficznej centrum danych, zobacz [Gdzie znajdują się twoje dane?](https://products.office.com/where-is-your-data-located?geo=All)

> [!NOTE]
> Następujące funkcje znajdują się w ustawieniach globalnych zasad Sejf Załączniki w portalu Microsoft 365 Defender. Jednak te ustawienia są włączone lub wyłączone globalnie i nie wymagają Sejf zasad załączników:
>
> - [Sejf załączniki dla SharePoint, OneDrive i Microsoft Teams](mdo-for-spo-odb-and-teams.md).
> - [Bezpieczne dokumenty w usłudze Microsoft 365 E5](safe-docs.md)

## <a name="safe-attachments-policy-settings"></a>ustawienia zasad załączników Sejf

W tej sekcji opisano ustawienia zasad Sejf Załączniki:

- **Sejf Odpowiedzi na nieznane złośliwe oprogramowanie załączników**: to ustawienie kontroluje akcję skanowania złośliwego oprogramowania Sejf Załączniki w wiadomościach e-mail. Dostępne opcje opisano w poniższej tabeli:

  |Opcja|Efekt|Użyj, gdy chcesz:|
  |---|---|---|
  |**Wył.**|Załączniki nie są skanowane pod kątem złośliwego oprogramowania według Sejf załączników. Komunikaty są nadal skanowane pod kątem złośliwego oprogramowania przez [ochronę przed złośliwym oprogramowaniem w ramach EOP](anti-malware-protection.md).|Wyłącz skanowanie dla wybranych adresatów. <br/><br/> Zapobiegaj niepotrzebnym opóźnieniom w routingu poczty wewnętrznej. <br/><br/> **Ta opcja nie jest zalecana dla większości użytkowników. Ta opcja powinna być używana tylko do wyłączania skanowania załączników Sejf w poszukiwaniu adresatów, którzy odbierają wiadomości tylko od zaufanych nadawców. Zap nie będzie kwarantanny komunikatów, jeśli Sejf Załączniki jest wyłączona i sygnał złośliwego oprogramowania nie jest odbierany. Aby uzyskać szczegółowe informacje, zobacz [Automatyczne przeczyszczanie zerogodzinne](zero-hour-auto-purge.md)**|
  |**Monitor**|Dostarcza komunikaty z załącznikami, a następnie śledzi, co się dzieje z wykrytym złośliwym oprogramowaniem. <br/><br/> Dostarczanie bezpiecznych komunikatów może być opóźnione z powodu skanowania Sejf załączników.|Zobacz, gdzie w twojej organizacji trafia wykryte złośliwe oprogramowanie.|
  |**Blokuj**|Zapobiega dostarczaniu komunikatów z wykrytymi załącznikami złośliwego oprogramowania. <br/><br/> Komunikaty są poddawane kwarantannie. Domyślnie tylko administratorzy (nie użytkownicy) mogą przeglądać, wydawać lub usuwać komunikaty.<sup>\*</sup> <br/><br/> Automatycznie blokuje przyszłe wystąpienia komunikatów i załączników. <br/><br/> Dostarczanie bezpiecznych komunikatów może być opóźnione z powodu skanowania Sejf załączników.|Chroni organizację przed powtarzającymi się atakami przy użyciu tych samych załączników złośliwego oprogramowania. <br/><br/> Jest to wartość domyślna i zalecana wartość w standardowych i ścisłych [wstępnie ustawionych zasad zabezpieczeń](preset-security-policies.md).|
  |**Zastąpić**|Usuwa wykryte załączniki złośliwego oprogramowania. <br/><br/> Powiadamia adresatów o usunięciu załączników. <br/><br/>  Komunikaty zawierające złośliwe załączniki są poddawane kwarantannie. Domyślnie tylko administratorzy (nie użytkownicy) mogą przeglądać, wydawać lub usuwać komunikaty.<sup>\*</sup> <br/><br/> Dostarczanie bezpiecznych komunikatów może być opóźnione z powodu skanowania Sejf załączników.|Zgłoś odbiorcom widoczność, że załączniki zostały usunięte z powodu wykrytego złośliwego oprogramowania.|
  |**Dostarczanie dynamiczne**|Dostarcza komunikaty natychmiast, ale zastępuje załączniki symbolami zastępczymi do momentu ukończenia skanowania Sejf Załączniki. <br/><br/> Komunikaty zawierające złośliwe załączniki są poddawane kwarantannie. Domyślnie tylko administratorzy (nie użytkownicy) mogą przeglądać, wydawać lub usuwać komunikaty.<sup>\*</sup> <br/><br/> Aby uzyskać szczegółowe informacje, zobacz sekcję [Dynamiczne dostarczanie w zasadach Sejf Załączniki](#dynamic-delivery-in-safe-attachments-policies) w dalszej części tego artykułu.|Unikaj opóźnień komunikatów, chroniąc adresatów przed złośliwymi plikami.|

  <sup>\*</sup>Administratorzy mogą tworzyć i przypisywać _zasady kwarantanny_ w zasadach Sejf Załączniki, które definiują, co użytkownicy mogą robić w przypadku komunikatów poddanych kwarantannie. Aby uzyskać więcej informacji, zobacz [Zasady kwarantanny](quarantine-policies.md).

- **Przekierowywanie załącznika po wykryciu: Włącz przekierowanie** i **Wyślij załącznik na następujący adres e-mail**: W przypadku akcji **Blokuj**, **Monitoruj** lub **Zastąp** wysyłaj wiadomości zawierające załączniki złośliwego oprogramowania do określonego wewnętrznego lub zewnętrznego adresu e-mail na potrzeby analizy i badania.

  Zalecenia dotyczące standardowych i ścisłych ustawień zasad to włączenie przekierowania. Aby uzyskać więcej informacji, zobacz [Sejf Ustawienia załączników](recommended-settings-for-eop-and-office365.md#safe-attachments-settings).

- **Zastosuj powyższą opcję, jeśli przekroczono limit czasu lub wystąpi błąd skanowania pod kątem złośliwego oprogramowania**: akcja określona przez **Sejf Załączniki nieznana odpowiedź na złośliwe oprogramowanie** jest wykonywana w przypadku komunikatów, nawet jeśli skanowanie załączników Sejf nie może zostać ukończone. Zawsze wybieraj tę opcję, jeśli wybierzesz pozycję **Włącz przekierowanie**. W przeciwnym razie komunikaty mogą zostać utracone.

- **Filtry adresatów**: należy określić warunki i wyjątki adresatów, które określają, do kogo mają zastosowanie zasady. Możesz użyć tych właściwości w przypadku warunków i wyjątków:
  - **Adresat jest**
  - **Domena adresata jest**
  - **Odbiorca jest członkiem**

  Warunek lub wyjątek można użyć tylko raz, ale warunek lub wyjątek może zawierać wiele wartości. Wiele wartości tego samego warunku lub wyjątku używa logiki OR (na przykład _\<recipient1\>_ lub _\<recipient2\>_). Różne warunki lub wyjątki używają logiki AND (na przykład _\<recipient1\>_ i _\<member of group 1\>_).

- **Priorytet**: jeśli tworzysz wiele zasad, możesz określić kolejność ich stosowania. Żadne dwie zasady nie mogą mieć takiego samego priorytetu, a przetwarzanie zasad zostanie zatrzymane po zastosowaniu pierwszych zasad.

  Aby uzyskać więcej informacji na temat kolejności pierwszeństwa oraz sposobu oceniania i stosowania wielu zasad, zobacz [Kolejność i pierwszeństwo ochrony poczty e-mail](how-policies-and-protections-are-combined.md).

### <a name="dynamic-delivery-in-safe-attachments-policies"></a>Dynamiczne dostarczanie w zasadach załączników Sejf

> [!NOTE]
> Dynamiczne dostarczanie działa tylko w przypadku skrzynek pocztowych Exchange Online.

Akcja dynamicznego dostarczania w zasadach załączników Sejf ma na celu wyeliminowanie wszelkich opóźnień dostarczania wiadomości e-mail, które mogą być spowodowane skanowaniem załączników Sejf. Treść wiadomości e-mail jest dostarczana do adresata z symbolem zastępczym dla każdego załącznika. Symbol zastępczy pozostaje do momentu, gdy załącznik zostanie uznany za bezpieczny, a następnie załącznik będzie dostępny do otwarcia lub pobrania.

Jeśli załącznik zostanie uznany za złośliwy, komunikat zostanie poddany kwarantannie.

Większość plików PDF i dokumentów Office można wyświetlić w trybie awaryjnym podczas skanowania Sejf Załączniki. Jeśli załącznik nie jest zgodny z podglądem dynamicznego dostarczania, adresaci będą widzieć symbol zastępczy załącznika do momentu ukończenia skanowania Sejf Załączniki.

Jeśli używasz urządzenia przenośnego, a pliki PDF nie są renderowane w podglądzie dynamicznego dostarczania na urządzeniu przenośnym, spróbuj otworzyć komunikat w Outlook w sieci Web (dawniej nazywanym Outlook Web App) przy użyciu przeglądarki mobilnej.

Poniżej przedstawiono niektóre zagadnienia dotyczące dostarczania dynamicznego i przekazywanych dalej komunikatów:

- Jeśli przesłany dalej adresat jest chroniony przez zasady Sejf Załączniki korzystające z opcji Dynamiczne dostarczanie, odbiorca zobaczy symbol zastępczy z możliwością podglądu zgodnych plików.
- Jeśli przesłany dalej adresat nie jest chroniony przez zasady załączników Sejf, wiadomość i załączniki zostaną dostarczone bez żadnych Sejf skanowania załączników lub symboli zastępczych załączników.

Istnieją scenariusze, w których usługa Dynamic Delivery nie może zastąpić załączników w komunikatach. Te scenariusze obejmują:

- Komunikaty w folderach publicznych.
- Wiadomości, które są kierowane poza, a następnie z powrotem do skrzynki pocztowej użytkownika przy użyciu reguł niestandardowych.
- Wiadomości, które są przenoszone (automatycznie lub ręcznie) ze skrzynek pocztowych w chmurze do innych lokalizacji, w tym folderów archiwum.
- Reguły skrzynki odbiorczej przenoszą komunikat ze skrzynki odbiorczej do innego folderu.
- Usunięte komunikaty.
- Folder wyszukiwania skrzynki pocztowej użytkownika jest w stanie błędu.
- Exchange Online organizacji, w których włączono funkcję wykrzykującego. Aby rozwiązać ten problem, zobacz [KB4014438](https://support.microsoft.com/help/4014438).
- [S/MIME)](/exchange/security-and-compliance/smime-exo/smime-exo) zaszyfrowanych wiadomości.
- Akcję Dynamiczne dostarczanie skonfigurowano w zasadach Sejf Załączniki, ale adresat nie obsługuje dostarczania dynamicznego (na przykład adresat jest skrzynką pocztową w lokalnej Exchange organizacji). Jednak [Sejf Łącza w Ochrona usługi Office 365 w usłudze Microsoft Defender](set-up-safe-links-policies.md) może skanować Office załączniki plików zawierające adresy URL (w zależności od sposobu konfigurowania [ustawień globalnych linków Sejf](configure-global-settings-for-safe-links.md)).

## <a name="submitting-files-for-malware-analysis"></a>Przesyłanie plików do analizy złośliwego oprogramowania

- Jeśli otrzymasz plik, który chcesz wysłać do firmy Microsoft w celu analizy, zobacz [Przesyłanie złośliwego oprogramowania i nie złośliwego oprogramowania do firmy Microsoft w celu analizy](submitting-malware-and-non-malware-to-microsoft-for-analysis.md).
- Jeśli otrzymasz wiadomość e-mail (z załącznikiem lub bez niej), którą chcesz przesłać do firmy Microsoft w celu analizy, zobacz [Raport wiadomości i pliki do firmy Microsoft](report-junk-email-messages-to-microsoft.md).
