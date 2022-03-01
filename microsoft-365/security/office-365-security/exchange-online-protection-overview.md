---
title: omówienie Exchange Online Protection (EOP)
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: 09/18/2020
audience: ITPro
ms.topic: overview
ms.localizationpriority: medium
ms.assetid: 1270a65f-ddc3-4430-b500-4d3a481efb1e
ms.custom:
- seo-marvel-apr2020
description: Dowiedz się Exchange Online Protection (EOP) może pomóc chronić lokalną organizację poczty e-mail w środowisku autonomicznym i hybrydowym.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: ef4443c0ee9b029133bb2abfabdd9a2f00a52203
ms.sourcegitcommit: 9f0e84835121ce6228fdc69182c24be7ad1cb20e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/18/2022
ms.locfileid: "63014881"
---
# <a name="exchange-online-protection-overview"></a>Exchange Online Protection omówienie

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender dla Office 365 plan 1 i plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Exchange Online Protection (EOP) to oparta na chmurze usługa filtrowania, która chroni organizację przed spamem, złośliwym oprogramowaniem i innymi zagrożeniami dla poczty e-mail. Program EOP jest uwzględniony we wszystkich Microsoft 365 z Exchange Online pocztowymi.

> [!NOTE]
> Ponadto program EOP jest dostępny samodzielnie w celu ochrony lokalnych skrzynek pocztowych i w środowiskach hybrydowych w celu ochrony lokalnych skrzynek Exchange pocztowych. Aby uzyskać więcej informacji, zobacz [Autonomiczne Exchange Online Protection](/exchange/standalone-eop/standalone-eop).

Instrukcje dotyczące skonfigurowania funkcji zabezpieczeń usługi EOP oraz porównanie dodatkowych zabezpieczeń, które można uzyskać w programie Microsoft Defender dla systemu Office 365, zobacz Ochrona [przed zagrożeniami](protect-against-threats.md). Zalecane ustawienia funkcji usługi EOP znajdują się w tece Zalecane ustawienia usługi [EOP i Microsoft Defender w Office 365 zabezpieczeń](recommended-settings-for-eop-and-office365.md).

W dalszej części tego artykułu wyjaśniono, jak działa program EOP i jakie funkcje są dostępne w uchcie EOP.

## <a name="how-eop-works"></a>Jak działa EOP

Aby dowiedzieć się, jak działa program EOP, warto sprawdzić, jak przetwarza przychodzącą pocztę e-mail:

:::image type="content" source="../../media/tp_emailprocessingineopt3.png" alt-text="Grafika przedstawiająca wiadomości e-mail z Internetu lub opinie klientów przechodzące do usługi EOP i za pośrednictwem połączenia, złośliwego oprogramowania, filtrowania reguł przepływu poczty (Mailflow Rules-slash-Policy Filtering) oraz filtrowania zawartości przed werdyktem wiadomości-śmieci lub kwarantanny albo dostarczania poczty przez użytkowników końcowych.":::

1. Gdy wiadomość przychodząca wprowadza usługę EOP, na początku przechodzi przez filtrowanie połączeń, które sprawdza reputację nadawcy. Obecnie większość spamu jest zatrzymywana i odrzucana przez firmę EOP. Aby uzyskać więcej informacji, zobacz [Konfigurowanie filtrowania połączeń](configure-the-connection-filter-policy.md).

2. Następnie wiadomość jest sprawdzana pod kątem złośliwego oprogramowania. Jeśli w wiadomości lub załącznikach znajduje się złośliwe oprogramowanie, wiadomość zostanie dostarczona do kwarantanny. Domyślnie tylko administratorzy mogą wyświetlać wiadomości poddanych kwarantannie złośliwego oprogramowania i wchodzić w interakcje z nimi. Jednak administratorzy mogą tworzyć zasady kwarantanny [](quarantine-policies.md) i używać ich w celu określenia, co użytkownicy mogą robić w przypadku wiadomości poddanych kwarantannie. Aby dowiedzieć się więcej na temat ochrony przed złośliwym oprogramowaniem, zobacz [Ochrona przed złośliwym oprogramowaniem w uiece EOP](anti-malware-protection.md).

3. Wiadomość jest kontynuowana za pomocą filtrowania zasad, gdzie jest sprawdzana na podstawie wszelkich utworzonych przez Ciebie reguł przepływu poczty e-mail (nazywanych również regułami transportu). Na przykład reguła może wysłać do kierownika powiadomienie, gdy przychodzi wiadomość od określonego nadawcy.

   W organizacji lokalnej z licencjami cal Exchange Enterprise cal z licencjami usług testy ochrony przed utratą danych [(DLP, Data loss prevention)](/exchange/security-and-compliance/data-loss-prevention/data-loss-prevention) w uciekują również w tej chwili usługę EOP.

4. Wiadomość przechodzi przez filtrowanie zawartości (ochrony przed spamem i fałszowanie), w którym szkodliwe wiadomości są identyfikowane jako spam, spam o dużej pewności, wyłudzanie informacji, wyłudzanie informacji o wysokiej ufności lub masowo (zasady ochrony przed spamem) lub fałszowanie (fałszowanie ustawień w zasadach ochrony przed wyłudzaniem informacji). Możesz skonfigurować akcję, która będzie podjąć w związku z wiadomością na podstawie werdyktu filtrowania (kwarantanny, przenoszenia do folderu wiadomości-śmieci itp.) oraz tego, co użytkownicy mogą robić w kwarantannie wiadomości przy użyciu zasad kwarantanny[.](quarantine-policies.md) Aby uzyskać więcej informacji, zobacz [Konfigurowanie zasad ochrony przed spamem](configure-your-spam-filter-policies.md) i [Konfigurowanie zasad ochrony przed wyłudzaniem informacji w u usługi EOP](configure-anti-phishing-policies-eop.md).

Wiadomość, która pomyślnie przejdzie wszystkie te warstwy ochrony, jest dostarczana do adresatów.

Aby uzyskać więcej informacji, zobacz [Zamówienie i pierwszeństwo ochrony poczty e-mail](how-policies-and-protections-are-combined.md).

### <a name="eop-datacenters"></a>Centra danych programu EOP

EOP działa w globalnej sieci centrów danych zaprojektowanych tak, aby zapewnić najlepszą dostępność. Jeśli na przykład centrum danych stanie się niedostępne, wiadomości e-mail będą automatycznie kierowane do innego centrum danych bez zakłóceń w działaniu usługi. Serwery w każdym centrum danych akceptują wiadomości w Twoim imieniu, zapewniając warstwę wyciągów między Twoją organizacją a Internetem, zmniejszając w ten sposób obciążenie serwerów. Za pośrednictwem tej wysoce dostępnej sieci firma Microsoft może zapewnić terminowe dotarcie wiadomości e-mail do organizacji.

Program EOP przeprowadza równoważenie obciążenia między centrami danych, ale tylko w obrębie regionu. Jeśli inicjowanie obsługi administracyjnej jest realizowane w jednym regionie, wszystkie wiadomości będą przetwarzane przy użyciu routingu poczty dla tego regionu.

### <a name="eop-features"></a>Funkcje programu EOP

Ta sekcja zawiera ogólne omówienie głównych funkcji dostępnych w u usługi EOP.

Aby uzyskać informacje o wymaganiach, ważnych limitach i dostępności funkcji we wszystkich planach subskrypcji usługi EOP, Exchange Online Protection [opis usługi](/office365/servicedescriptions/exchange-online-protection-service-description/exchange-online-protection-service-description).

**Uwagi**:

- Program EOP używa kilku list zablokowanych adresów URL, które ułatwiają wykrywanie znanych złośliwych linków w wiadomościach.
- EOP korzysta z bogatej listy domen, które są znane z wysyłania spamu.
- Program EOP używa wielu aparatów chroniących przed złośliwym oprogramowaniem, które pomagają automatycznie chronić naszych klientów przez cały czas.
- Usługa EOP sprawdza aktywny ład w treści wiadomości i wszystkie załączniki wiadomości pod kątem złośliwego oprogramowania.
- Aby uzyskać zalecane wartości zasad ochrony, zobacz Zalecane ustawienia usług [EOP i Microsoft Defender](recommended-settings-for-eop-and-office365.md) w Office 365 zabezpieczeń.
- Aby uzyskać szybkie instrukcje dotyczące konfigurowania zasad ochrony, zobacz [Ochrona przed zagrożeniami](protect-against-threats.md).

<br>

****
|Funkcja|Komentarze|
|---|---|
|**Ochrona**||
|Ochrona przed złośliwym oprogramowaniem|[Ochrona przed złośliwym oprogramowaniem w uchcie EOP](anti-malware-protection.md) <p> [Ochrona przed złośliwym oprogramowaniem — często zadawane pytania](anti-malware-protection-faq-eop.yml) <p> [Konfigurowanie zasad ochrony przed złośliwym oprogramowaniem w u usługi EOP](configure-anti-malware-policies.md)|
|Przychodzące ochrona przed spamem|[Ochrona przed spamem w uciekaniu poczty eop](anti-spam-protection.md) <p> [Ochrona przed spamem — często zadawane pytania](anti-spam-protection-faq.yml) <p> [Konfigurowanie zasad ochrony przed spamem w u usługi EOP](configure-your-spam-filter-policies.md)|
|Ochrona przed spamem ruchu wychodzącego|[Ochrona przed spamem ruchu wychodzącego w uceniu EOP](outbound-spam-controls.md) <p> [Konfigurowanie filtrowania spamu ruchu wychodzącego w u usługi EOP](configure-the-outbound-spam-policy.md) <p> [Sterowanie automatycznym zewnętrznym przesyłaniem dalej wiadomości e-mail w Microsoft 365](external-email-forwarding.md)|
|Filtrowanie połączeń|[Konfigurowanie filtrowania połączeń](configure-the-connection-filter-policy.md)|
|Ochrona przed wyłudzaniem informacji|[Zasady ochrony przed wyłudzaniem informacji w programie Microsoft 365](set-up-anti-phishing-policies.md) <p> [Konfigurowanie zasad ochrony przed wyłudzaniem informacji w u usługi EOP](configure-anti-phishing-policies-eop.md)|
|Ochrona przed fałszerami|[Spoof intelligence insight in EOP](learn-about-spoof-intelligence.md) <p> [Zarządzanie listą zezwalania/blokowania dzierżawy](tenant-allow-block-list.md)|
|Automatyczne przeczyszczanie (ZAP) o zerowej godzinie dla dostarczonego złośliwego oprogramowania, wiadomości o spamie i wiadomości wyłudzających informacje|[ZAP w Exchange Online](zero-hour-auto-purge.md)|
|Wstępnie ustawione zasady zabezpieczeń|[Wstępnie ustawione zasady zabezpieczeń w usługach EOP i Microsoft Defender dla systemu Office 365](preset-security-policies.md) <p> [Analizator konfiguracji do obsługi zasad ochrony w usługach EOP i Microsoft Defender dla Office 365](configuration-analyzer-for-security-policies.md)|
|Lista zezwalania/blokowania dzierżawy|[Zarządzanie listą zezwalania/blokowania dzierżawy](tenant-allow-block-list.md)|
|Blokowanie list nadawców wiadomości|[Tworzenie list zablokowanych nadawców w uciekinie eop](create-block-sender-lists-in-office-365.md)|
|Listy zezwalania nadawcom wiadomości|[Tworzenie bezpiecznych list nadawców w uchcie EOP](create-safe-sender-lists-in-office-365.md)|
|Blokowanie oparte na katalogu (DBEB)|[Odrzucanie wiadomości wysyłanych do nieprawidłowych adresatów za pomocą blokowania na podstawie katalogu](/exchange/mail-flow-best-practices/use-directory-based-edge-blocking)|
|**Kwarantanna i elementy przesyłania**||
|Przesyłanie administratora|[Przesyłanie przez administratora w celu przesłania podejrzanych wiadomości-śmieci, wiadomości wyłudowych, adresów URL i plików do firmy Microsoft](admin-submission.md)|
|Przesyłanie użytkowników (niestandardowa skrzynka pocztowa)|[Zasady przesyłania użytkowników](user-submission.md)|
|Kwarantanna — administratorzy|[Zarządzanie wiadomościami i plikami poddanymi kwarantannie jako administrator w u usługi EOP](manage-quarantined-messages-and-files.md) <p> [Wiadomości poddane kwarantannie — często zadawane pytania](quarantine-faq.yml) <p> [Zgłaszanie wiadomości i plików do firmy Microsoft](report-junk-email-messages-to-microsoft.md) <p> [Nagłówki wiadomości w programie Microsoft 365](anti-spam-message-headers.md) <p> Za pomocą Analizatora nagłówka wiadomości możesz analizować nagłówki wiadomości poddanych [kwarantannie](https://mha.azurewebsites.net/).|
|Kwarantanna — użytkownicy końcowi|[Znajdowanie i wypuszczenie wiadomości poddanych kwarantannie jako użytkownik w u kontie EOP](find-and-release-quarantined-messages-as-a-user.md) <p> [Używanie powiadomień kwarantanny do zwalniania i zgłaszania poddanych kwarantannie wiadomości](use-spam-notifications-to-release-and-report-quarantined-messages.md) <p> [Zasady kwarantanny](quarantine-policies.md)|
|**Przepływ poczty e-mail**||
|Reguły przepływu poczty e-mail|[Reguły przepływu poczty (reguły transportu) w programie Exchange Online](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rules) <p> [Warunki i wyjątki (wyjątki) reguły przepływu poczty e-mail w programie Exchange Online](/exchange/security-and-compliance/mail-flow-rules/conditions-and-exceptions) <p> [Akcje reguły przepływu poczty e-mail Exchange Online](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rule-actions) <p> [Zarządzanie regułami przepływu poczty e-mail w Exchange Online](/exchange/security-and-compliance/mail-flow-rules/manage-mail-flow-rules) <p> [Procedury reguł przepływu poczty e-mail Exchange Online](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rule-procedures)|
|Zaakceptowane domeny|[Zarządzanie zaakceptowanymi domenami w Exchange Online](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains)|
|Łączniki|[Konfigurowanie przepływu poczty e-mail przy użyciu łączników w Exchange Online](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/use-connectors-to-configure-mail-flow)|
|Ulepszone filtrowanie łączników|[Ulepszone filtrowanie łączników w Exchange Online](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/enhanced-filtering-for-connectors)|
|**Monitorowanie**||
|Śledzenie wiadomości|[Śledzenie wiadomości](message-trace-scc.md) <p> [Śledzenie wiadomości w centrum Exchange administracyjnego](/exchange/monitoring/trace-an-email-message/message-trace-modern-eac)|
|Raporty & e-mail|[Wyświetlanie raportów zabezpieczeń poczty e-mail](view-email-security-reports.md)|
|Raporty przepływu poczty e-mail|[Wyświetlanie raportów przepływu poczty e-mail](view-mail-flow-reports.md) <p> [Raporty przepływu poczty e-mail Exchange centrum administracyjnym usługi](/exchange/monitoring/mail-flow-reports/mail-flow-reports)|
|Szczegółowe informacje dotyczące przepływu poczty e-mail|[Szczegółowe informacje dotyczące przepływu poczty e-mail](mail-flow-insights-v2.md) <p> [Szczegółowe informacje o przepływie poczty e Exchange centrum administracyjnym](/exchange/monitoring/mail-flow-insights/mail-flow-insights)|
|Raporty inspekcji|[Raporty inspekcji w centrum Exchange administracyjnego](/exchange/security-and-compliance/exchange-auditing-reports/exchange-auditing-reports)|
|Zasady alertów|[Zasady alertów](../../compliance/alert-policies.md)|
|**Umowy dotyczące poziomu usług i pomoc techniczna**||
|Umowa SLA w celu ochrony przed spamem|\> 99%|
|Wynik fałszywie dodatni na mocy umowy SLA|\< 1:250,000|
|Wykrywanie wirusów i blokowanie umowy SLA|100% znanych wirusów|
|Miesięczna umowa SLA beza czasowej pracy|99.999%|
|Telefon pomocy technicznej w sieci Web przez 24 godziny na dobę, siedem dni w tygodniu|[Pomoc i obsługa techniczna dla programu EOP](help-and-support-for-eop.md).|
|**Inne funkcje**||
|Geograficznie nadmiarowa globalna sieć serwerów|EOP działa w globalnej sieci centrów danych zaprojektowanych tak, aby zapewnić najlepszą dostępność. Aby uzyskać więcej informacji, zobacz sekcję centrów [danych programu EOP](#eop-datacenters) we wcześniejszej części tego artykułu.|
|Kolejkowanie wiadomości, gdy serwer lokalny nie może zaakceptować poczty|Wiadomości odroczone pozostają w naszych kolejkach przez jeden dzień. Próby ponowienia wiadomości są oparte na błędzie zwracany przez nas z systemu poczty adresata. Średnio co 5 minut są pobieranie wiadomości. Aby uzyskać więcej informacji, zobacz [Wiadomość odroczona i](eop-queued-deferred-and-bounced-messages-faq.yml) odroczona w kolejce usługi EOP — często zadawane pytania.|
|Szyfrowanie wiadomości usługi Office 365 jako dodatek|Aby uzyskać więcej informacji, zobacz [Szyfrowanie w Office 365](../../compliance/encryption.md).|
|||
