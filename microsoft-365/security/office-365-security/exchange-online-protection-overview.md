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
ms.collection: M365-security-compliance
ms.localizationpriority: medium
ms.assetid: 1270a65f-ddc3-4430-b500-4d3a481efb1e
ms.custom:
- seo-marvel-apr2020
description: Dowiedz się, jak Exchange Online Protection (EOP) może pomóc w ochronie lokalnej organizacji poczty e-mail w środowiskach autonomicznych i hybrydowych.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 19bf82a530cd61b253047261bb44893266a240d8
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2022
ms.locfileid: "64941572"
---
# <a name="exchange-online-protection-overview"></a>Omówienie usługi Exchange Online Protection

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Usługi Microsoft Defender dla usługi Office 365 (plan 1 i plan 2)](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Exchange Online Protection (EOP) to oparta na chmurze usługa filtrowania, która chroni organizację przed spamem, złośliwym oprogramowaniem i innymi zagrożeniami e-mail. Funkcja EOP jest uwzględniana we wszystkich organizacjach Microsoft 365 z Exchange Online skrzynkami pocztowymi.

> [!NOTE]
> Funkcja EOP jest również dostępna samodzielnie w celu ochrony lokalnych skrzynek pocztowych i w środowiskach hybrydowych w celu ochrony lokalnych Exchange skrzynek pocztowych. Aby uzyskać więcej informacji, zobacz [Autonomiczne Exchange Online Protection](/exchange/standalone-eop/standalone-eop).

Kroki konfigurowania funkcji zabezpieczeń EOP i porównanie z dodatkowymi zabezpieczeniami, które uzyskujesz w Ochrona usługi Office 365 w usłudze Microsoft Defender, można znaleźć w [temacie Ochrona przed zagrożeniami](protect-against-threats.md). Zalecane ustawienia funkcji EOP są dostępne w [obszarze Zalecane ustawienia dotyczące EOP i zabezpieczeń Ochrona usługi Office 365 w usłudze Microsoft Defender](recommended-settings-for-eop-and-office365.md).

W pozostałej części tego artykułu wyjaśniono, jak działa funkcja EOP i jakie funkcje są dostępne w ramach EOP.

## <a name="how-eop-works"></a>Jak działa EOP

Aby zrozumieć, jak działa EOP, warto zobaczyć, jak przetwarza przychodzące wiadomości e-mail:

:::image type="content" source="../../media/tp_emailprocessingineopt3.png" alt-text="Grafika przedstawiająca pocztę e-mail z Internetu lub opinie klientów przesyłane do EOP i za pośrednictwem połączenia, ochrony przed złośliwym oprogramowaniem, filtrowania zasad przepływu poczty i filtrowania zawartości przed ogłoszeniem werdyktu dotyczącego wiadomości-śmieci lub kwarantanny albo dostarczania wiadomości e-mail przez użytkownika końcowego" lightbox="../../media/tp_emailprocessingineopt3.png":::

1. Gdy komunikat przychodzący wchodzi w operację EOP, początkowo przechodzi przez filtrowanie połączeń, co sprawdza reputację nadawcy. Większość spamu została zatrzymana w tym momencie i odrzucona przez EOP. Aby uzyskać więcej informacji, zobacz [Konfigurowanie filtrowania połączeń](configure-the-connection-filter-policy.md).

2. Następnie komunikat jest sprawdzany pod kątem złośliwego oprogramowania. Jeśli w wiadomości zostanie znalezione złośliwe oprogramowanie lub załączniki, wiadomość zostanie dostarczona do kwarantanny. Domyślnie tylko administratorzy mogą wyświetlać komunikaty poddane kwarantannie i wchodzić w interakcje z nimi. Administratorzy mogą jednak tworzyć [i używać zasad kwarantanny](quarantine-policies.md) , aby określić, co użytkownicy mogą robić w przypadku komunikatów poddanych kwarantannie. Aby dowiedzieć się więcej na temat ochrony przed [złośliwym oprogramowaniem, zobacz Ochrona przed złośliwym oprogramowaniem w usłudze EOP](anti-malware-protection.md).

3. Komunikat jest kontynuowany przez filtrowanie zasad, w którym jest oceniany pod kątem wszelkich reguł przepływu poczty (nazywanych również regułami transportu), które zostały utworzone. Na przykład reguła może wysłać powiadomienie do menedżera po odebraniu komunikatu od określonego nadawcy.

   W organizacji lokalnej z licencjami Exchange Enterprise CAL z usługami kontrole [ochrony przed utratą danych (DLP) usługi Microsoft Purview](/exchange/security-and-compliance/data-loss-prevention/data-loss-prevention) również odbywają się w tym momencie.

4. Wiadomość przechodzi przez filtrowanie zawartości (ochrona przed spamem i fałszowaniem), w której szkodliwe wiadomości są identyfikowane jako spam, spam o wysokim poziomie zaufania, wyłudzanie informacji, wyłudzanie informacji o wysokim poziomie zaufania lub zbiorcze (zasady ochrony przed spamem) lub fałszowanie (ustawienia fałszowania w zasadach ochrony przed wyłudzaniem informacji). Możesz skonfigurować akcję do wykonania na podstawie werdyktu filtrowania (kwarantanny, przejścia do folderu Wiadomości-śmieci itp.) oraz tego, co użytkownicy mogą zrobić z komunikatami poddanymi kwarantannie przy użyciu [zasad kwarantanny](quarantine-policies.md). Aby uzyskać więcej informacji, zobacz [Konfigurowanie zasad ochrony przed spamem](configure-your-spam-filter-policies.md) i [Konfigurowanie zasad ochrony przed wyłudzaniem informacji w usłudze EOP](configure-anti-phishing-policies-eop.md).

Komunikat, który pomyślnie przekazuje wszystkie te warstwy ochrony, jest dostarczany do adresatów.

Aby uzyskać więcej informacji, zobacz [Kolejność i pierwszeństwo ochrony poczty e-mail](how-policies-and-protections-are-combined.md).

### <a name="eop-datacenters"></a>Centra danych EOP

Funkcja EOP działa w ogólnoświatowej sieci centrów danych, które zostały zaprojektowane tak, aby zapewnić najlepszą dostępność. Jeśli na przykład centrum danych stanie się niedostępne, wiadomości e-mail są automatycznie kierowane do innego centrum danych bez żadnych przerw w działaniu usługi. Serwery w każdym centrum danych akceptują komunikaty w Twoim imieniu, zapewniając warstwę separacji między organizacją a Internetem, co zmniejsza obciążenie serwerów. Dzięki tej sieci o wysokiej dostępności firma Microsoft może zapewnić, że poczta e-mail dotrze do Twojej organizacji w odpowiednim czasie.

Funkcja EOP wykonuje równoważenie obciążenia między centrami danych, ale tylko w obrębie regionu. Jeśli aprowizowano Cię w jednym regionie, wszystkie wiadomości zostaną przetworzone przy użyciu routingu poczty dla tego regionu.

### <a name="eop-features"></a>Funkcje EOP

Ta sekcja zawiera ogólne omówienie głównych funkcji, które są dostępne w ramach EOP.

Aby uzyskać informacje o wymaganiach, ważnych limitach i dostępności funkcji we wszystkich planach subskrypcji EOP, zobacz [opis usługi Exchange Online Protection](/office365/servicedescriptions/exchange-online-protection-service-description/exchange-online-protection-service-description).

**Uwagi**:

- Funkcja EOP używa kilku list blokowych adresów URL, które ułatwiają wykrywanie znanych złośliwych linków w komunikatach.
- Funkcja EOP używa szerokiej listy domen, o których wiadomo, że wysyłają spam.
- Funkcja EOP używa wielu aparatów chroniących przed złośliwym oprogramowaniem, które pomagają automatycznie chronić naszych klientów przez cały czas.
- Funkcja EOP sprawdza aktywny ładunek w treści wiadomości i wszystkie załączniki wiadomości pod kątem złośliwego oprogramowania.
- Aby uzyskać zalecane wartości zasad ochrony, zobacz [Zalecane ustawienia dotyczące EOP i Ochrona usługi Office 365 w usłudze Microsoft Defender zabezpieczeń](recommended-settings-for-eop-and-office365.md).
- Aby uzyskać szybkie instrukcje dotyczące konfigurowania zasad ochrony, zobacz [Ochrona przed zagrożeniami](protect-against-threats.md).

|Funkcja|Komentarze|
|---|---|
|**Ochrony**||
|Ochrona przed złośliwym oprogramowaniem|[Ochrona przed złośliwym oprogramowaniem w ramach EOP](anti-malware-protection.md) <p> [Ochrona przed złośliwym oprogramowaniem — często zadawane pytania](anti-malware-protection-faq-eop.yml) <p> [Konfigurowanie zasad ochrony przed złośliwym oprogramowaniem w ramach operacji EOP](configure-anti-malware-policies.md)|
|Ochrona przed spamem dla ruchu przychodzącego|[Ochrona przed spamem w ramach EOP](anti-spam-protection.md) <p> [Ochrona przed spamem — często zadawane pytania](anti-spam-protection-faq.yml) <p> [Konfigurowanie zasad ochrony przed spamem w ramach EOP](configure-your-spam-filter-policies.md)|
|Wychodząca ochrona przed spamem|[Ochrona przed spamem wychodzącym w ramach EOP](outbound-spam-controls.md) <p> [Konfigurowanie filtrowania wychodzącego spamu w ramach operacji EOP](configure-the-outbound-spam-policy.md) <p> [Kontrolowanie automatycznego przekazywania zewnętrznych wiadomości e-mail w Microsoft 365](external-email-forwarding.md)|
|Filtrowanie połączeń|[Konfigurowanie filtrowania połączeń](configure-the-connection-filter-policy.md)|
|Ochrona przed wyłudzaniem informacji|[Zasady ochrony przed wyłudzaniem informacji w Microsoft 365](set-up-anti-phishing-policies.md) <p> [Konfigurowanie zasad ochrony przed wyłudzaniem informacji w usłudze EOP](configure-anti-phishing-policies-eop.md)|
|Ochrona przed spoofingiem|[Fałszowanie szczegółowych informacji wywiadowczych w ramach EOP](learn-about-spoof-intelligence.md) <p> [Zarządzanie listą dozwolonych/zablokowanych dzierżaw](tenant-allow-block-list.md)|
|Automatyczne przeczyszczanie bez godziny (ZAP) w przypadku dostarczonego złośliwego oprogramowania, spamu i wiadomości wyłudzających informacje|[Zap w Exchange Online](zero-hour-auto-purge.md)|
|Wstępnie ustawione zasady zabezpieczeń|[Wstępne ustawienie zasad zabezpieczeń w usłudze EOP i ochronie usługi Office 365 w usłudze Microsoft Defender](preset-security-policies.md) <p> [Analizator konfiguracji dla zasad ochrony w zakresie operacji we/wy na sekundę i Ochrona usługi Office 365 w usłudze Microsoft Defender](configuration-analyzer-for-security-policies.md)|
|Lista dozwolonych/zablokowanych dzierżaw|[Zarządzanie listą dozwolonych/zablokowanych dzierżaw](tenant-allow-block-list.md)|
|Blokuj listy dla nadawców wiadomości|[Tworzenie zablokowanych list nadawców w ramach EOP](create-block-sender-lists-in-office-365.md)|
|Zezwalaj na listy nadawców wiadomości|[Tworzenie list bezpiecznych nadawców w ramach EOP](create-safe-sender-lists-in-office-365.md)|
|Blokowanie krawędzi na podstawie katalogu (DBEB)|[Używanie blokowania krawędzi opartej na katalogu w celu odrzucenia komunikatów wysyłanych do nieprawidłowych adresatów](/exchange/mail-flow-best-practices/use-directory-based-edge-blocking)|
|**Kwarantanna i przesyłanie**||
|Przesyłanie przez administratora|[Przesyłanie przez administratora do firmy Microsoft podejrzanego spamu, phish, adresów URL i plików](admin-submission.md)|
|Przesyłanie przez użytkownika (niestandardowa skrzynka pocztowa)|[Zasady przesyłania użytkowników](user-submission.md)|
|Kwarantanna — administratorzy|[Zarządzanie komunikatami i plikami poddanymi kwarantannie jako administrator w ramach EOP](manage-quarantined-messages-and-files.md) <p> [Komunikaty poddane kwarantannie — często zadawane pytania](quarantine-faq.yml) <p> [Zgłaszanie wiadomości i plików firmie Microsoft](report-junk-email-messages-to-microsoft.md) <p> [Nagłówki wiadomości chroniących przed spamem w Microsoft 365](anti-spam-message-headers.md) <p> Nagłówki komunikatów komunikatów poddanych kwarantannie można analizować przy użyciu [analizatora nagłówków komunikatów pod adresem](https://mha.azurewebsites.net/).|
|Kwarantanna — użytkownicy końcowi|[Znajdowanie i zwalnianie komunikatów poddanych kwarantannie jako użytkownik w ramach EOP](find-and-release-quarantined-messages-as-a-user.md) <p> [Używanie powiadomień kwarantanny do wydawania i zgłaszania komunikatów poddanych kwarantannie](use-spam-notifications-to-release-and-report-quarantined-messages.md) <p> [Zasady kwarantanny](quarantine-policies.md)|
|**Przepływ poczty**||
|Reguły przepływu poczty|[Reguły przepływu (transportu) poczty e-mail w usłudze Exchange Online](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rules) <p> [Warunki i wyjątki reguł przepływu poczty (predykaty) w Exchange Online](/exchange/security-and-compliance/mail-flow-rules/conditions-and-exceptions) <p> [Akcje reguł przepływu poczty w Exchange Online](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rule-actions) <p> [Zarządzanie regułami przepływu poczty w Exchange Online](/exchange/security-and-compliance/mail-flow-rules/manage-mail-flow-rules) <p> [Procedury reguł przepływu poczty w Exchange Online](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rule-procedures)|
|Akceptowane domeny|[Zarządzanie akceptowanymi domenami w Exchange Online](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains)|
|Złącza|[Konfigurowanie przepływu poczty przy użyciu łączników w Exchange Online](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/use-connectors-to-configure-mail-flow)|
|Rozszerzone filtrowanie łączników|[Rozszerzone filtrowanie łączników w Exchange Online](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/enhanced-filtering-for-connectors)|
|**Monitorowania**||
|Śledzenie wiadomości|[Śledzenie wiadomości](message-trace-scc.md) <p> [Śledzenie komunikatów w centrum administracyjnym Exchange](/exchange/monitoring/trace-an-email-message/message-trace-modern-eac)|
|Raporty współpracy & poczty e-mail|[Wyświetlanie raportów zabezpieczeń poczty e-mail](view-email-security-reports.md)|
|Raporty przepływu poczty|[Wyświetlanie raportów przepływu poczty](view-mail-flow-reports.md) <p> [Raporty przepływu poczty w centrum administracyjnym Exchange](/exchange/monitoring/mail-flow-reports/mail-flow-reports)|
|Szczegółowe informacje o przepływie poczty|[Szczegółowe informacje o przepływie poczty](mail-flow-insights-v2.md) <p> [Szczegółowe informacje o przepływie poczty w centrum administracyjnym Exchange](/exchange/monitoring/mail-flow-insights/mail-flow-insights)|
|Raporty inspekcji|[Inspekcja raportów w centrum administracyjnym Exchange](/exchange/security-and-compliance/exchange-auditing-reports/exchange-auditing-reports)|
|Zasady alertów|[Zasady alertów](../../compliance/alert-policies.md)|
|**Umowy dotyczące poziomu usług (SLA) i pomoc techniczna**||
|Umowa SLA dotycząca skuteczności spamu|\> 99%|
|Umowa SLA dotycząca współczynnika fałszywie dodatniego|\< 1:250,000|
|Wykrywanie wirusów i blokowanie umowy SLA|100% znanych wirusów|
|Miesięczna umowa SLA dotycząca czasu pracy|99.999%|
|Telefon i internetowej pomocy technicznej przez 24 godziny na dobę, siedem dni w tygodniu|[Pomoc i obsługa EOP](help-and-support-for-eop.md).|
|**Inne funkcje**||
|Geograficznie nadmiarowa globalna sieć serwerów|Funkcja EOP działa w ogólnoświatowej sieci centrów danych, które zostały zaprojektowane w celu zapewnienia najlepszej dostępności. Aby uzyskać więcej informacji, zobacz sekcję [Centra danych EOP](#eop-datacenters) we wcześniejszej części tego artykułu.|
|Kolejkowanie wiadomości, gdy serwer lokalny nie może zaakceptować poczty|Komunikaty w odroczeniu pozostają w naszych kolejkach przez jeden dzień. Próby ponawiania wiadomości są oparte na błędzie, który otrzymujemy z systemu poczty adresata. Średnio komunikaty są ponawiane co 5 minut. Aby uzyskać więcej informacji, zobacz [Często zadawane pytania dotyczące obsługi operacji EOP w kolejce, odroczonych i odbitych komunikatów](eop-queued-deferred-and-bounced-messages-faq.yml).|
|Office 365 szyfrowanie komunikatów dostępne jako dodatek|Aby uzyskać więcej informacji, zobacz [Szyfrowanie w Office 365](../../compliance/encryption.md).|
|||
