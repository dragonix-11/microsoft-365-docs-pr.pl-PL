---
title: Zalecenia firmy Microsoft dotyczące funkcji EOP i ustawień zabezpieczeń Ochrona usługi Office 365 w usłudze Defender
keywords: Office 365 zaleceń dotyczących zabezpieczeń, struktury zasad nadawcy, raportowania i zgodności komunikatów opartych na domenie, kluczy domen zidentyfikowanych poczty, kroków, sposobu jej działania, punktów odniesienia zabezpieczeń, punktów odniesienia dla EOP, punktów odniesienia dla Ochrona usługi Office 365 w usłudze Defender , konfiguracji Ochrona usługi Office 365 w usłudze Defender , konfigurowanie EOP, konfigurowanie Ochrona usługi Office 365 w usłudze Defender, konfigurowanie operacji EOP, konfiguracja zabezpieczeń
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
ms.date: ''
manager: dansimp
audience: ITPro
ms.topic: conceptual
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: 6f64f2de-d626-48ed-8084-03cc72301aa4
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
description: Jakie są najlepsze rozwiązania dotyczące ustawień zabezpieczeń Exchange Online Protection (EOP) i Ochrona usługi Office 365 w usłudze Defender? Jakie są bieżące zalecenia dotyczące standardowej ochrony? Co powinno być używane, jeśli chcesz być bardziej rygorystyczne? A jakie dodatki otrzymujesz, jeśli również używasz Ochrona usługi Office 365 w usłudze Defender?
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 7798bc177cf6d3a864644fdfa6563ced14cd0ab8
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2022
ms.locfileid: "66489796"
---
# <a name="recommended-settings-for-eop-and-microsoft-defender-for-office-365-security"></a>Zalecane ustawienia zabezpieczeń EOP i Ochrona usługi Office 365 w usłudze Microsoft Defender

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Usługi Microsoft Defender dla usługi Office 365 (plan 1 i plan 2)](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

**Exchange Online Protection (EOP)** jest podstawą zabezpieczeń subskrypcji platformy Microsoft 365 i pomaga zapobiegać docieraniu złośliwych wiadomości e-mail do skrzynek odbiorczych pracownika. Jednak w przypadku nowych, bardziej zaawansowanych ataków pojawiających się każdego dnia często wymagane są ulepszone zabezpieczenia. **Ochrona usługi Office 365 w usłudze Microsoft Defender** Plan 1 lub Plan 2 zawierają dodatkowe funkcje, które zapewniają administratorom więcej warstw zabezpieczeń, kontroli i badania.

Mimo że umożliwiamy administratorom zabezpieczeń dostosowywanie ich ustawień zabezpieczeń, zalecamy stosowanie dwóch poziomów zabezpieczeń w ramach EOP i Ochrona usługi Office 365 w usłudze Microsoft Defender: **Standardowa** i **Ścisła**. Mimo że środowiska i potrzeby klientów są różne, te poziomy filtrowania pomogą zapobiec docieraniu niechcianej poczty do skrzynki odbiorczej pracowników w większości sytuacji.

Aby automatycznie zastosować ustawienia standardowe lub ścisłe do użytkowników, zobacz [Wstępnie ustawione zasady zabezpieczeń w usłudze EOP i Ochrona usługi Office 365 w usłudze Microsoft Defender](preset-security-policies.md).

W tym artykule opisano ustawienia domyślne, a także zalecane ustawienia standardowe i ścisłe, które ułatwiają ochronę użytkowników. Tabele zawierają ustawienia w portalu Microsoft 365 Defender i programie PowerShell (Exchange Online programu PowerShell lub autonomicznej Exchange Online Protection programu PowerShell dla organizacji bez Exchange Online skrzynek pocztowych).

> [!NOTE]
> Moduł Office 365 Advanced Threat Protection Recommended Configuration Analyzer (ORCA) dla programu PowerShell może ułatwić (administratorom) znalezienie bieżących wartości tych ustawień. W szczególności polecenie cmdlet **Get-ORCAReport** generuje ocenę ochrony przed spamem, ochrony przed wyłudzaniem informacji i innych ustawień higieny wiadomości. Moduł ORCA można pobrać pod adresem <https://www.powershellgallery.com/packages/ORCA/>.
>
> W organizacjach platformy Microsoft 365 zalecamy pozostawienie filtru wiadomości-śmieci w programie Outlook na wartość **Brak automatycznego filtrowania** , aby zapobiec niepotrzebnym konfliktom (zarówno pozytywnym, jak i negatywnym) z werdyktami filtrowania spamu z EOP. Aby uzyskać więcej informacji, zapoznaj się z następującymi artykułami:
>
> - [Konfigurowanie ustawień wiadomości-śmieci w skrzynkach pocztowych Exchange Online](configure-junk-email-settings-on-exo-mailboxes.md)
> - [Informacje o ustawieniach wiadomości-śmieci w programie Outlook](configure-junk-email-settings-on-exo-mailboxes.md#about-junk-email-settings-in-outlook)
> - [Zmienianie poziomu ochrony w filtrze wiadomości-śmieci](https://support.microsoft.com/en-us/office/e89c12d8-9d61-4320-8c57-d982c8d52f6b)
> - [Tworzenie list bezpiecznych nadawców w ramach EOP](create-safe-sender-lists-in-office-365.md)
> - [Tworzenie zablokowanych list nadawców w ramach EOP](create-block-sender-lists-in-office-365.md)

## <a name="anti-spam-anti-malware-and-anti-phishing-protection-in-eop"></a>Ochrona przed spamem, ochroną przed złośliwym oprogramowaniem i ochroną przed wyłudzaniem informacji w ramach EOP

Ochrona przed spamem, ochrona przed złośliwym oprogramowaniem i ochrona przed wyłudzaniem informacji to funkcje EOP, które mogą być konfigurowane przez administratorów. Zalecamy następujące konfiguracje standardowe lub ścisłe.

### <a name="eop-anti-spam-policy-settings"></a>Ustawienia zasad ochrony przed spamem w usłudze EOP

Aby utworzyć i skonfigurować zasady ochrony przed spamem, zobacz [Konfigurowanie zasad ochrony przed spamem w usłudze EOP](configure-your-spam-filter-policies.md).

|Nazwa funkcji zabezpieczeń|Domyślne|Standard|Ścisłe|Komentowanie|
|---|:---:|:---:|:---:|---|
|**Próg zbiorczej poczty e-mail & właściwości spamu**|||||
|**Próg zbiorczej poczty e-mail** <p> _BulkThreshold_|7|6|4|Aby uzyskać szczegółowe informacje, zobacz [Poziom skarg zbiorczych (BCL) w EOP](bulk-complaint-level-values.md).|
|_MarkAsSpamBulkMail_|`On`|`On`|`On`|To ustawienie jest dostępne tylko w programie PowerShell.|
|**Zwiększanie ustawień oceny spamu**|Wył.|Wył.|Wył.|Wszystkie te ustawienia są częścią zaawansowanego filtru spamu (ASF). Aby uzyskać więcej informacji, zobacz [sekcję Ustawienia asf w zasadach ochrony przed spamem](#asf-settings-in-anti-spam-policies) w tym artykule.|
|**Oznacz jako ustawienia spamu**|Wył.|Wył.|Wył.|Większość z tych ustawień jest częścią usługi ASF. Aby uzyskać więcej informacji, zobacz [sekcję Ustawienia asf w zasadach ochrony przed spamem](#asf-settings-in-anti-spam-policies) w tym artykule.|
|**Zawiera określone języki** <p> _EnableLanguageBlockList_ <p> _LanguageBlockList_|**Wył.** <p> `$false` <p> Puste|**Wył.** <p> `$false` <p> Puste|**Wył.** <p> `$false` <p> Puste|Nie mamy żadnych konkretnych zaleceń dotyczących tego ustawienia. Komunikaty można blokować w określonych językach w zależności od potrzeb biznesowych.|
|**Z tych krajów** <p> _EnableRegionBlockList_ <p> _RegionBlockList_|**Wył.** <p> `$false` <p> Puste|**Wył.** <p> `$false` <p> Puste|**Wył.** <p> `$false` <p> Puste|Nie mamy żadnych konkretnych zaleceń dotyczących tego ustawienia. Komunikaty z określonych krajów można blokować w zależności od potrzeb biznesowych.|
|**Tryb testu** (_TestModeAction_)|**Brak**|**Brak**|**Brak**|To ustawienie jest częścią usługi ASF. Aby uzyskać więcej informacji, zobacz [sekcję Ustawienia asf w zasadach ochrony przed spamem](#asf-settings-in-anti-spam-policies) w tym artykule.|
|**Działania**||||Wszędzie tam, gdzie **wybrano komunikat kwarantanny**, dostępne jest pole **Wyboru zasad kwarantanny** . Zasady kwarantanny definiują, co użytkownicy mogą robić w przypadku komunikatów poddanych kwarantannie. <p> Standardowe i ścisłe wstępnie ustawione zasady zabezpieczeń używają domyślnych zasad kwarantanny (AdminOnlyAccessPolicy lub DefaultFullAccessPolicy bez powiadomień kwarantanny) zgodnie z opisem w tabeli [tutaj](quarantine-policies.md#step-2-assign-a-quarantine-policy-to-supported-features). <p> Podczas tworzenia nowych zasad ochrony przed spamem pusta wartość oznacza, że domyślne zasady kwarantanny są używane do definiowania historycznych możliwości komunikatów, które zostały poddane kwarantannie przez ten konkretny werdykt (AdminOnlyAccessPolicy bez powiadomień kwarantanny dotyczących **wyłudzania informacji o wysokim poziomie zaufania**; DefaultFullAccessPolicy bez powiadomień o kwarantannie dla wszystkiego innego). <p> Administratorzy mogą tworzyć i wybierać niestandardowe zasady kwarantanny, które definiują bardziej restrykcyjne lub mniej restrykcyjne możliwości dla użytkowników w domyślnych lub niestandardowych zasadach ochrony przed spamem. Aby uzyskać więcej informacji, zobacz [Zasady kwarantanny](quarantine-policies.md).|
|Akcja wykrywania **spamu** <p> _SpamAction_|**Przenoszenie wiadomości do folderu Wiadomości-śmieci** <p> `MoveToJmf`|**Przenoszenie wiadomości do folderu Wiadomości-śmieci** <p> `MoveToJmf`|**Komunikat kwarantanny** <p> `Quarantine`||
|**Akcja wykrywania spamu o wysokim poziomie ufności** <p> _HighConfidenceSpamAction_|**Przenoszenie wiadomości do folderu Wiadomości-śmieci** <p> `MoveToJmf`|**Komunikat kwarantanny** <p> `Quarantine`|**Komunikat kwarantanny** <p> `Quarantine`||
|Akcja wykrywania **wyłudzania informacji** <p> _PhishSpamAction_|**Przenoszenie wiadomości do folderu Wiadomości-śmieci**<sup>\*</sup> <p> `MoveToJmf`|**Komunikat kwarantanny** <p> `Quarantine`|**Komunikat kwarantanny** <p> `Quarantine`|<sup>\*</sup> Wartość domyślna to **Przenieś wiadomość do folderu Wiadomości-śmieci** w domyślnych zasadach ochrony przed spamem oraz w nowych zasadach ochrony przed spamem utworzonych w programie PowerShell. Wartość domyślna to **Komunikat kwarantanny** w nowych zasadach ochrony przed spamem tworzonych w portalu Microsoft 365 Defender.|
|**Akcja wykrywania wyłudzania informacji o wysokim poziomie zaufania** <p> _HighConfidencePhishAction_|**Komunikat kwarantanny** <p> `Quarantine`|**Komunikat kwarantanny** <p> `Quarantine`|**Komunikat kwarantanny** <p> `Quarantine`||
|Akcja wykrywania **zbiorczego** <p> _BulkSpamAction_|**Przenoszenie wiadomości do folderu Wiadomości-śmieci** <p> `MoveToJmf`|**Przenoszenie wiadomości do folderu Wiadomości-śmieci** <p> `MoveToJmf`|**Komunikat kwarantanny** <p> `Quarantine`||
|**Przechowywanie spamu w kwarantannie przez tyle dni** <p> _KwarantannaRetentionPeriod_|15 dni<sup>\*</sup>|30 dni|30 dni|<sup>\*</sup> Wartość domyślna to 15 dni w domyślnych zasadach ochrony przed spamem i w nowych zasadach ochrony przed spamem utworzonych w programie PowerShell. Wartość domyślna to 30 dni w nowych zasadach ochrony przed spamem tworzonych w portalu Microsoft 365 Defender. <p> Ta wartość ma również wpływ na komunikaty poddane kwarantannie przez zasady ochrony przed wyłudzaniem informacji. Aby uzyskać więcej informacji, zobacz [Kwarantanna wiadomości e-mail w EOP](quarantine-email-messages.md).|
|**Włączanie wskazówek dotyczących bezpieczeństwa spamu** <p> _InlineSafetyTipsEnabled_|Wybrane <p> `$true`|Wybrane <p> `$true`|Wybrane <p> `$true`||
|Włączanie automatycznego przeczyszczania w godzinach zerowych (ZAP) na potrzeby wiadomości wyłudzających informacje <p> _PhishZapEnabled_|Wybrane <p> `$true`|Wybrane <p> `$true`|Wybrane <p> `$true`||
|Włączanie zap dla wiadomości niepożądanych <p> _SpamZapEnabled_|Wybrane <p> `$true`|Wybrane <p> `$true`|Wybrane <p> `$true`||
|**Zezwalaj na listę zablokowanych &**|||||
|Dozwoloni nadawcy <p> _AllowedSenders_|Brak|Brak|Brak||
|Dozwolone domeny nadawcy <p> _AllowedSenderDomains_|Brak|Brak|Brak|Dodawanie domen do listy dozwolonych nadawców jest bardzo złym pomysłem. Osoby atakujące będą mogły wysłać Ci wiadomość e-mail, która w przeciwnym razie zostałaby odfiltrowana. <p> Skorzystaj ze [szczegółowych informacji analitycznych na temat fałszowania](learn-about-spoof-intelligence.md) i [listy dozwolonych/zablokowanych dzierżaw](tenant-allow-block-list.md) , aby przejrzeć wszystkich nadawców, którzy podszywają się pod adresy e-mail nadawcy w domenach poczty e-mail w organizacji lub podszywają się pod adresy e-mail nadawcy w domenach zewnętrznych.|
|Zablokowani nadawcy <p> _BlockedSenders_|Brak|Brak|Brak||
|Zablokowane domeny nadawcy <p> _BlockedSenderDomains_|Brak|Brak|Brak||

#### <a name="asf-settings-in-anti-spam-policies"></a>Ustawienia usługi ASF w zasadach ochrony przed spamem

Aby uzyskać więcej informacji na temat ustawień zaawansowanego filtru spamu (ASF) w zasadach ochrony przed spamem, zobacz [Ustawienia zaawansowanego filtru spamu (ASF) w usłudze EOP](advanced-spam-filtering-asf-options.md).

|Nazwa funkcji zabezpieczeń|Domyślne|Zalecane<br/>Standard|Zalecane<br/>Ścisłe|Komentowanie|
|---|:---:|:---:|:---:|---|
|**Linki obrazów do lokacji zdalnych** <p> _IncreaseScoreWithImageLinks_|Wył.|Wył.|Wył.||
|**Numeryczny adres IP w adresie URL** <p> _IncreaseScoreWithNumericIps_|Wył.|Wył.|Wył.||
|**Przekierowanie adresu URL do innego portu** <p> _IncreaseScoreWithRedirectToOtherPort_|Wył.|Wył.|Wył.||
|**Linki do witryn .biz lub .info** <p> _IncreaseScoreWithBizOrInfoUrls_|Wył.|Wył.|Wył.||
|**Puste komunikaty** <p> _MarkAsSpamEmptyMessages_|Wył.|Wył.|Wył.||
|**Osadzanie tagów w kodzie HTML** <p> _MarkAsSpamEmbedTagsInHtml_|Wył.|Wył.|Wył.||
|**Język JavaScript lub VBScript w języku HTML** <p> _MarkAsSpamJavaScriptInHtml_|Wył.|Wył.|Wył.||
|**Tagi formularzy w języku HTML** <p> _MarkAsSpamFormTagsInHtml_|Wył.|Wył.|Wył.||
|**Tagi ramek lub ramek w języku HTML** <p> _MarkAsSpamFramesInHtml_|Wył.|Wył.|Wył.||
|**Błędy internetowe w kodzie HTML** <p> _MarkAsSpamWebBugsInHtml_|Wył.|Wył.|Wył.||
|**Tagi obiektów w kodzie HTML** <p> _MarkAsSpamObjectTagsInHtml_|Wył.|Wył.|Wył.||
|**Wyrazy wrażliwe** <p> _MarkAsSpamSensitiveWordList_|Wył.|Wył.|Wył.||
|**Rekord SPF: niepowodzenie twarde** <p> _MarkAsSpamSpfRecordHardFail_|Wył.|Wył.|Wył.||
|**Filtrowanie identyfikatora nadawcy kończy się niepowodzeniem** <p> _MarkAsSpamFromAddressAuthFail_|Wył.|Wył.|Wył.||
|**Backscatter** <p> _MarkAsSpamNdrBackscatter_|Wył.|Wył.|Wył.||
|**Tryb testowania** <p> _TestModeAction_)|Brak|Brak|Brak|W przypadku ustawień asf, które obsługują akcję **Testuj** jako akcję, możesz skonfigurować akcję trybu **testowego na wartość Brak**, **Dodaj domyślny tekst X-Header** lub **Wyślij komunikat Bcc** (`None`, `AddXHeader`lub `BccMessage`). Aby uzyskać więcej informacji, zobacz [Włączanie, wyłączanie lub testowanie ustawień asf](advanced-spam-filtering-asf-options.md#enable-disable-or-test-asf-settings).|

#### <a name="eop-outbound-spam-policy-settings"></a>Ustawienia zasad wychodzących zasad dotyczących spamu w usłudze EOP

Aby utworzyć i skonfigurować zasady wychodzącego spamu, zobacz [Konfigurowanie filtrowania spamu wychodzącego w ramach EOP](configure-the-outbound-spam-policy.md).

Aby uzyskać więcej informacji na temat domyślnych limitów wysyłania w usłudze, zobacz [Wysyłanie limitów](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#sending-limits-1).

> [!NOTE]
> Zasady wychodzącego spamu nie są częścią standardowych ani rygorystycznych wstępnie ustawionych zasad zabezpieczeń. Wartości **Standardowe** i **Ścisłe** wskazują **zalecane** wartości w domyślnych zasadach spamu wychodzącego lub niestandardowych utworzonych przez Ciebie zasadach spamu wychodzącego.

|Nazwa funkcji zabezpieczeń|Domyślne|Zalecane<br/>Standard|Zalecane<br/>Ścisłe|Komentowanie|
|---|:---:|:---:|:---:|---|
|**Ustawianie limitu komunikatów zewnętrznych** <p> _AdresatLimitExternalPerHour_|0|500|400|Wartość domyślna 0 oznacza użycie wartości domyślnych usługi.|
|**Ustawianie wewnętrznego limitu komunikatów** <p> _AdresatLimitInternalPerHour_|0|1000|800|Wartość domyślna 0 oznacza użycie wartości domyślnych usługi.|
|**Ustawianie dziennego limitu komunikatów** <p> _AdresatLimitPerDay_|0|1000|800|Wartość domyślna 0 oznacza użycie wartości domyślnych usługi.|
|**Ograniczenie nałożone na użytkowników, którzy osiągną limit komunikatów** <p> _ActionWhenThresholdReached_|**Ogranicz użytkownikowi wysyłanie wiadomości e-mail do następnego dnia** <p> `BlockUserForToday`|**Ograniczanie użytkownikowi możliwości wysyłania wiadomości e-mail** <p> `BlockUser`|**Ograniczanie użytkownikowi możliwości wysyłania wiadomości e-mail** <p> `BlockUser`||
|**Reguły automatycznego przekazywania** <p> _AutoForwardingMode_|**Automatyczne — sterowane przez system** <p> `Automatic`|**Automatyczne — sterowane przez system** <p> `Automatic`|**Automatyczne — sterowane przez system** <p> `Automatic`|
|**Wysyłanie kopii komunikatów wychodzących przekraczających te limity do tych użytkowników i grup** <p> _BccSuspiciousOutboundMail_ <p> _BccSuspiciousOutboundAdditionalRecipients_|Nie zaznaczono <p> `$false` <p> Puste|Nie zaznaczono <p> `$false` <p> Puste|Nie zaznaczono <p> `$false` <p> Puste|Nie mamy żadnych konkretnych zaleceń dotyczących tego ustawienia. <p> To ustawienie działa tylko w domyślnych zasadach spamu wychodzącego. Nie działa to w ramach niestandardowych zasad spamu wychodzącego, które tworzysz.|
|**Powiadamiaj tych użytkowników i grupy, jeśli nadawca jest zablokowany z powodu wysyłania spamu wychodzącego** <p> _NotifyOutboundSpam_ <p> _NotifyOutboundSpamRecipients_|Nie zaznaczono <p> `$false` <p> Puste|Nie zaznaczono <p> `$false` <p> Puste|Nie zaznaczono <p> `$false` <p> Puste|Domyślne [zasady alertów](../../compliance/alert-policies.md) o nazwie **Użytkownik z ograniczeniami wysyłania wiadomości e-mail** wysyłają już powiadomienia e-mail do członków grupy **TenantAdmins** (**administratorzy globalni**), gdy użytkownicy są blokowani z powodu przekroczenia limitów w zasadach. **Zdecydowanie zalecamy używanie zasad alertów zamiast tego ustawienia w zasadach spamu wychodzącego w celu powiadamiania administratorów i innych użytkowników**. Aby uzyskać instrukcje, zobacz [Weryfikowanie ustawień alertów dla użytkowników z ograniczeniami](removing-user-from-restricted-users-portal-after-spam.md#verify-the-alert-settings-for-restricted-users).|

### <a name="eop-anti-malware-policy-settings"></a>Ustawienia zasad ochrony przed złośliwym oprogramowaniem EOP

Aby utworzyć i skonfigurować zasady ochrony przed złośliwym oprogramowaniem, zobacz [Konfigurowanie zasad ochrony przed złośliwym oprogramowaniem w ramach EOP](configure-anti-malware-policies.md).

|Nazwa funkcji zabezpieczeń|Domyślne|Standard|Ścisłe|Komentowanie|
|---|:---:|:---:|:---:|---|
|**Ustawienia ochrony**|||||
|**Włączanie wspólnego filtru załączników** <p> _EnableFileFilter_|Nie zaznaczono <p> `$false`|Wybrane <p> `$true`|Wybrane <p> `$true`|To ustawienie powoduje kwarantannę komunikatów zawierających załączniki na podstawie typu pliku, niezależnie od zawartości załącznika. Aby uzyskać listę typów plików, zobacz [Zasady ochrony przed złośliwym oprogramowaniem](anti-malware-protection.md#anti-malware-policies).|
|**Włączanie automatycznego przeczyszczania z zerową godziną w przypadku złośliwego oprogramowania** <p> _ZapEnabled_|Wybrane <p> `$true`|Wybrane <p> `$true`|Wybrane <p> `$true`||
|**Zasady kwarantanny**|AdminOnlyAccessPolicy|AdminOnlyAccessPolicy|AdminOnlyAccessPolicy|Podczas tworzenia nowych zasad ochrony przed złośliwym oprogramowaniem pusta wartość oznacza, że domyślne zasady kwarantanny są używane do definiowania historycznych możliwości komunikatów, które zostały poddane kwarantannie jako złośliwe oprogramowanie (AdminOnlyAccessPolicy bez powiadomień kwarantanny). <p> Standardowe i ścisłe wstępnie ustawione zasady zabezpieczeń używają domyślnych zasad kwarantanny (AdminOnlyAccessPolicy bez powiadomień o kwarantannie) zgodnie z opisem w tabeli [tutaj](quarantine-policies.md#step-2-assign-a-quarantine-policy-to-supported-features). <p> Administratorzy mogą tworzyć i wybierać niestandardowe zasady kwarantanny, które definiują więcej możliwości dla użytkowników w domyślnych lub niestandardowych zasadach ochrony przed złośliwym oprogramowaniem. Aby uzyskać więcej informacji, zobacz [Zasady kwarantanny](quarantine-policies.md).|
|**powiadomienia Administracja**|||||
|**Powiadamianie administratora o niedostarczonych komunikatach od nadawców wewnętrznych** <p> _EnableInternalSenderAdminNotifications_ <p> _InternalSenderAdminAddress_|Nie zaznaczono <p> `$false`|Nie zaznaczono <p> `$false`|Nie zaznaczono <p> `$false`|Nie mamy żadnych konkretnych zaleceń dotyczących tego ustawienia.|
|**Powiadamianie administratora o niedostarczonych komunikatach od nadawców zewnętrznych** <p> _EnableExternalSenderAdminNotifications_ <p> _ExternalSenderAdminAddress_|Nie zaznaczono <p> `$false`|Nie zaznaczono <p> `$false`|Nie zaznaczono <p> `$false`|Nie mamy żadnych konkretnych zaleceń dotyczących tego ustawienia.|
|**Dostosowywanie powiadomień**||||Nie mamy żadnych konkretnych zaleceń dotyczących tych ustawień.|
|**Korzystanie z dostosowanego tekstu powiadomień** <p> _CustomNotifications_|Nie zaznaczono <p> `$false`|Nie zaznaczono <p> `$false`|Nie zaznaczono <p> `$false`||
|**Z nazwy** <p> _CustomFromName_|Puste <p> `$null`|Puste <p> `$null`|Puste <p> `$null`||
|**Z adresu** <p> _CustomFromAddress_|Puste <p> `$null`|Puste <p> `$null`|Puste <p> `$null`||
|**Dostosowywanie powiadomień dotyczących komunikatów od nadawców wewnętrznych**||||Te ustawienia są używane tylko wtedy, gdy zostanie **wybrana opcja Powiadom administratora o niedostarczonych komunikatach od nadawców wewnętrznych** .|
|**Temat** <p> _CustomInternalSubject_|Puste <p> `$null`|Puste <p> `$null`|Puste <p> `$null`||
|**Komunikat** <p> _CustomInternalBody_|Puste <p> `$null`|Puste <p> `$null`|Puste <p> `$null`||
|**Dostosowywanie powiadomień dotyczących komunikatów od nadawców zewnętrznych**||||Te ustawienia są używane tylko wtedy, gdy zostanie wybrane **powiadomienie administratora o niedostarczonych komunikatach od nadawców zewnętrznych** .|
|**Temat** <p> _CustomExternalSubject_|Puste <p> `$null`|Puste <p> `$null`|Puste <p> `$null`||
|**Komunikat** <p> _CustomExternalBody_|Puste <p> `$null`|Puste <p> `$null`|Puste <p> `$null`||

### <a name="eop-anti-phishing-policy-settings"></a>Ustawienia zasad ochrony przed wyłudzaniem informacji w usłudze EOP

Aby uzyskać więcej informacji na temat tych ustawień, zobacz [Spoof settings (Fałszowanie ustawień](set-up-anti-phishing-policies.md#spoof-settings)). Aby skonfigurować te ustawienia, zobacz [Konfigurowanie zasad ochrony przed wyłudzaniem informacji w ramach EOP](configure-anti-phishing-policies-eop.md).

Ustawienia fałszowania są ze sobą powiązane, ale ustawienie **Pokaż pierwszą poradę bezpieczeństwa kontaktu** nie jest zależne od ustawień fałszowania.

|Nazwa funkcji zabezpieczeń|Domyślne|Standard|Ścisłe|Komentowanie|
|---|:---:|:---:|:---:|---|
|**Ochrona & progu wyłudzania informacji**|||||
|**Włączanie analizy fałszowania** <p> _EnableSpoofIntelligence_|Wybrane <p> `$true`|Wybrane <p> `$true`|Wybrane <p> `$true`||
|**Działania**|||||
|**Jeśli komunikat zostanie wykryty jako sfałszowany** <p> _AuthenticationFailAction_|**Przenoszenie wiadomości do folderów wiadomości-śmieci adresatów** <p> `MoveToJmf`|**Przenoszenie wiadomości do folderów wiadomości-śmieci adresatów** <p> `MoveToJmf`|**Kwarantanna komunikatu** <p> `Quarantine`|To ustawienie dotyczy sfałszowanych nadawców, którzy zostali automatycznie zablokowani, jak pokazano w szczegółowych [informacjach dotyczących fałszowania analizy](learn-about-spoof-intelligence.md) lub ręcznie zablokowanych na [liście dozwolonych/zablokowanych dzierżaw](tenant-allow-block-list.md). <p> Jeśli **wybierzesz pozycję Kwarantanna komunikatu**, pole **Zastosuj zasady kwarantanny** jest dostępne, aby wybrać zasady kwarantanny, które definiują, co użytkownicy mogą robić dla komunikatów, które są poddane kwarantannie jako fałszowanie. Podczas tworzenia nowych zasad ochrony przed wyłudzaniem informacji pusta wartość oznacza, że domyślne zasady kwarantanny są używane do definiowania historycznych możliwości komunikatów, które zostały poddane kwarantannie jako fałszowanie (DefaultFullAccessPolicy bez powiadomień kwarantanny). <p> Standardowe i ścisłe wstępnie ustawione zasady zabezpieczeń używają domyślnych zasad kwarantanny (DefaultFullAccessPolicy bez powiadomień o kwarantannie) zgodnie z opisem w tabeli [tutaj](quarantine-policies.md#step-2-assign-a-quarantine-policy-to-supported-features). <p> Administratorzy mogą tworzyć i wybierać niestandardowe zasady kwarantanny, które definiują bardziej restrykcyjne lub mniej restrykcyjne możliwości dla użytkowników w domyślnych lub niestandardowych zasadach ochrony przed wyłudzaniem informacji. Aby uzyskać więcej informacji, zobacz [Zasady kwarantanny](quarantine-policies.md).|
|**Pokaż pierwszą poradę bezpieczeństwa kontaktu** <p> _EnableFirstContactSafetyTips_|Nie zaznaczono <p> `$false`|Nie zaznaczono <p> `$false`|Nie zaznaczono <p> `$false`|Aby uzyskać więcej informacji, zobacz [Porada dotycząca bezpieczeństwa pierwszego kontaktu](set-up-anti-phishing-policies.md#first-contact-safety-tip).|
|**Pokaż (?) dla nieuwierzytelnionych nadawców na potrzeby fałszowania** <p> _EnableUnauthenticatedSender_|Wybrane <p> `$true`|Wybrane <p> `$true`|Wybrane <p> `$true`|Dodaje znak zapytania (?) do zdjęcia nadawcy w programie Outlook dla niezidentyfikowanych sfałszowanych nadawców. Aby uzyskać więcej informacji, zobacz [Nieuwierzytelnione wskaźniki nadawcy](set-up-anti-phishing-policies.md#unauthenticated-sender-indicators).|
|**Pokaż tag "via"** <p> _EnableViaTag_|Wybrane <p> `$true`|Wybrane <p> `$true`|Wybrane <p> `$true`|Dodaje tag via (chris@contoso.com za pośrednictwem fabrikam.com) do adresu Od, jeśli różni się on od domeny w podpisie DKIM lub **adresIE MAIL FROM** . <p> Aby uzyskać więcej informacji, zobacz [Nieuwierzytelnione wskaźniki nadawcy](set-up-anti-phishing-policies.md#unauthenticated-sender-indicators).|

## <a name="microsoft-defender-for-office-365-security"></a>zabezpieczenia Ochrona usługi Office 365 w usłudze Microsoft Defender

Dodatkowe korzyści związane z zabezpieczeniami są dostępne w ramach subskrypcji Ochrona usługi Office 365 w usłudze Microsoft Defender. Najnowsze wiadomości i informacje można znaleźć w temacie [Co nowego w Ochrona usługi Office 365 w usłudze Defender](whats-new-in-defender-for-office-365.md).

> [!IMPORTANT]
>
> - Domyślne zasady ochrony przed wyłudzaniem informacji w Ochrona usługi Office 365 w usłudze Microsoft Defender zapewniają [ochronę przed fałszowaniem](set-up-anti-phishing-policies.md#spoof-settings) i analizę skrzynek pocztowych dla wszystkich adresatów. Jednak inne dostępne funkcje [ochrony przed personifikacją](#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365) i [ustawienia zaawansowane](#advanced-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365) nie są skonfigurowane ani włączone w zasadach domyślnych. Aby włączyć wszystkie funkcje ochrony, zmodyfikuj domyślne zasady ochrony przed wyłudzaniem informacji lub utwórz dodatkowe zasady ochrony przed wyłudzaniem informacji.
>
> - Mimo że nie ma domyślnych zasad bezpiecznych załączników ani zasad bezpiecznych łączy, wstępnie skonfigurowane zasady zabezpieczeń **wbudowanej ochrony** zapewniają ochronę bezpiecznych załączników i bezpieczne linki adresatom, którzy nie są jeszcze uwzględniane w niestandardowych zasadach bezpiecznych załączników lub zasadach bezpiecznych łączy. Aby uzyskać więcej informacji, zobacz [Preset security policies in EOP and Ochrona usługi Office 365 w usłudze Microsoft Defender (Ustawienia wstępne zasad zabezpieczeń w usłudze EOP i Ochrona usługi Office 365 w usłudze Microsoft Defender](preset-security-policies.md)).
>
> - [Bezpieczne załączniki do ochrony programu SharePoint, usługi OneDrive i usługi Microsoft Teams](mdo-for-spo-odb-and-teams.md) oraz ochrony [bezpiecznych dokumentów](safe-docs.md) nie są zależne od zasad bezpiecznych łączy.

Jeśli Twoja subskrypcja obejmuje Ochrona usługi Office 365 w usłudze Microsoft Defender lub jeśli zakupiono Ochrona usługi Office 365 w usłudze Defender jako dodatek, ustaw następujące konfiguracje standardowe lub ścisłe.

### <a name="anti-phishing-policy-settings-in-microsoft-defender-for-office-365"></a>Ustawienia zasad ochrony przed wyłudzaniem informacji w Ochrona usługi Office 365 w usłudze Microsoft Defender

Klienci EOP uzyskują podstawową ochronę przed wyłudzaniem informacji zgodnie z wcześniejszym opisem, ale Ochrona usługi Office 365 w usłudze Defender zawiera więcej funkcji i kontroli, aby pomóc w zapobieganiu atakom, wykrywaniu i korygowaniu ich. Aby utworzyć i skonfigurować te zasady, zobacz [Konfigurowanie zasad ochrony przed wyłudzaniem informacji w Ochrona usługi Office 365 w usłudze Defender](configure-mdo-anti-phishing-policies.md).

#### <a name="advanced-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365"></a>Zaawansowane ustawienia zasad ochrony przed wyłudzaniem informacji w Ochrona usługi Office 365 w usłudze Microsoft Defender

Aby uzyskać więcej informacji na temat tego ustawienia, zobacz [Zaawansowane progi wyłudzania informacji w zasadach ochrony przed wyłudzaniem informacji w Ochrona usługi Office 365 w usłudze Microsoft Defender](set-up-anti-phishing-policies.md#advanced-phishing-thresholds-in-anti-phishing-policies-in-microsoft-defender-for-office-365). Aby skonfigurować to ustawienie, zobacz [Konfigurowanie zasad ochrony przed wyłudzaniem informacji w Ochrona usługi Office 365 w usłudze Defender](configure-mdo-anti-phishing-policies.md).

|Nazwa funkcji zabezpieczeń|Domyślne|Standard|Ścisłe|Komentowanie|
|---|:---:|:---:|:---:|---|
|**Próg wiadomości e-mail wyłud** <p> _PhishThresholdLevel_|**1 — Standardowa** <p> `1`|**2 — Agresywne** <p> `2`|**3 — Bardziej agresywne** <p> `3`||

#### <a name="impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365"></a>Ustawienia personifikacji w zasadach ochrony przed wyłudzaniem informacji w Ochrona usługi Office 365 w usłudze Microsoft Defender

Aby uzyskać więcej informacji na temat tych ustawień, zobacz [Temat Impersonation settings in anti-phishing policies in Ochrona usługi Office 365 w usłudze Microsoft Defender (Ustawienia personifikacji w zasadach ochrony przed wyłudzaniem informacji w Ochrona usługi Office 365 w usłudze Microsoft Defender](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)). Aby skonfigurować te ustawienia, zobacz [Konfigurowanie zasad ochrony przed wyłudzaniem informacji w Ochrona usługi Office 365 w usłudze Defender](configure-mdo-anti-phishing-policies.md).

|Nazwa funkcji zabezpieczeń|Domyślne|Standard|Ścisłe|Komentowanie|
|---|:---:|:---:|:---:|---|
|**Ochrona & progu wyłudzania informacji**|||||
|**Umożliwianie użytkownikom ochrony** (ochrona użytkowników personifikowanych) <p> _EnableTargetedUserProtection_ <p> _TargetedUsersToProtect_|Nie zaznaczono <p> `$false` <p> brak|Wybrane <p> `$true` <p> \<list of users\>|Wybrane <p> `$true` <p> \<list of users\>|Zalecamy dodanie użytkowników (nadawców komunikatów) do kluczowych ról. Wewnętrznie chronionymi nadawcami mogą być Dyrektor Generalny, Dyrektor Finansowy i inni starsi liderzy. Zewnętrznie chronieni nadawcy mogą obejmować członków rady lub zarząd.|
|**Włączanie ochrony domen** (personifikowana ochrona domeny)|Nie zaznaczono|Wybrane|Wybrane||
|**Uwzględnij domeny, których jestem właścicielem** <p> _EnableOrganizationDomainsProtection_|Wył. <p> `$false`|Wybrane <p> `$true`|Wybrane <p> `$true`||
|**Dołączanie domen niestandardowych** <p> _EnableTargetedDomainsProtection_ <p> _TargetedDomainsToProtect_|Wył. <p> `$false` <p> brak|Wybrane <p> `$true` <p> \<list of domains\>|Wybrane <p> `$true` <p> \<list of domains\>|Zalecamy dodanie domen (domen nadawcy), których nie jesteś właścicielem, ale często wchodzisz w interakcje.|
|**Dodawanie zaufanych nadawców i domen** <p> _Wykluczeni nadawcy_ <p> _Wykluczonedomeny_|Brak|Brak|Brak|W zależności od organizacji zalecamy dodanie nadawców lub domen, które są niepoprawnie identyfikowane jako próby personifikacji.|
|**Włączanie analizy skrzynki pocztowej** <p> _EnableMailboxIntelligence_|Wybrane <p> `$true`|Wybrane <p> `$true`|Wybrane <p> `$true`||
|**Włączanie analizy w celu ochrony przed personifikacją** <p> _EnableMailboxIntelligenceProtection_|Wył. <p> `$false`|Wybrane <p> `$true`|Wybrane <p> `$true`|To ustawienie umożliwia określoną akcję wykrywania personifikacji za pomocą analizy skrzynki pocztowej.|
|**Działania**||||Wszędzie tam, gdzie **wybierzesz pozycję Kwarantanna komunikatu**, dostępne jest pole **Wyboru zasad kwarantanny** . Zasady kwarantanny definiują, co użytkownicy mogą robić w przypadku komunikatów poddanych kwarantannie. <p> Standardowe i ścisłe wstępnie ustawione zasady zabezpieczeń używają domyślnych zasad kwarantanny (DefaultFullAccessPolicy bez powiadomień o kwarantannie) zgodnie z opisem w tabeli [tutaj](quarantine-policies.md#step-2-assign-a-quarantine-policy-to-supported-features). <p> Podczas tworzenia nowych zasad ochrony przed wyłudzaniem informacji pusta wartość oznacza, że domyślne zasady kwarantanny są używane do definiowania historycznych możliwości komunikatów, które zostały poddane kwarantannie przez ten werdykt (DefaultFullAccessPolicy dla wszystkich typów wykrywania personifikacji). <p> Administratorzy mogą tworzyć i wybierać niestandardowe zasady kwarantanny, które definiują mniej restrykcyjne lub bardziej restrykcyjne możliwości dla użytkowników w domyślnych lub niestandardowych zasadach ochrony przed wyłudzaniem informacji. Aby uzyskać więcej informacji, zobacz [Zasady kwarantanny](quarantine-policies.md).|
|**Jeśli komunikat zostanie wykryty jako personifikowany użytkownik** <p> _TargetedUserProtectionAction_|**Nie stosuj żadnej akcji** <p> `NoAction`|**Kwarantanna komunikatu** <p> `Quarantine`|**Kwarantanna komunikatu** <p> `Quarantine`||
|**Jeśli komunikat zostanie wykryty jako domena personifikowana** <p> _TargetedDomainProtectionAction_|**Nie stosuj żadnej akcji** <p> `NoAction`|**Kwarantanna komunikatu** <p> `Quarantine`|**Kwarantanna komunikatu** <p> `Quarantine`||
|**Jeśli analiza skrzynki pocztowej wykryje i personifikuje użytkownika** <p> _Skrzynka pocztowaIntelligenceProtectionAction_|**Nie stosuj żadnej akcji** <p> `NoAction`|**Przenoszenie wiadomości do folderów wiadomości-śmieci adresatów** <p> `MoveToJmf`|**Kwarantanna komunikatu** <p> `Quarantine`||
|**Pokaż poradę dotyczącą bezpieczeństwa personifikacji użytkownika** <p> _EnableSimilarUsersSafetyTips_|Wył. <p> `$false`|Wybrane <p> `$true`|Wybrane <p> `$true`||
|**Pokaż poradę dotyczącą bezpieczeństwa personifikacji domeny** <p> _EnableSimilarDomainsSafetyTips_|Wył. <p> `$false`|Wybrane <p> `$true`|Wybrane <p> `$true`||
|**Pokaż wskazówki bezpieczeństwa dotyczące personifikacji nietypowych znaków przez użytkownika** <p> _EnableUnusualCharactersSafetyTips_|Wył. <p> `$false`|Wybrane <p> `$true`|Wybrane <p> `$true`||

#### <a name="eop-anti-phishing-policy-settings-in-microsoft-defender-for-office-365"></a>Ustawienia zasad ochrony przed wyłudzaniem informacji na platformie EOP w Ochrona usługi Office 365 w usłudze Microsoft Defender

Są to te same ustawienia, które są dostępne w [ustawieniach zasad ochrony przed spamem w ramach EOP](#eop-anti-spam-policy-settings).

### <a name="safe-attachments-settings"></a>Ustawienia bezpiecznych załączników

Bezpieczne załączniki w Ochrona usługi Office 365 w usłudze Microsoft Defender obejmują ustawienia globalne, które nie mają relacji z zasadami bezpiecznych załączników, oraz ustawienia specyficzne dla poszczególnych zasad bezpiecznych łączy. Aby uzyskać więcej informacji, zobacz [Bezpieczne załączniki w Ochrona usługi Office 365 w usłudze Defender](safe-attachments.md).

Mimo że nie ma domyślnych zasad bezpiecznych załączników, wstępnie skonfigurowane zasady zabezpieczeń **wbudowanej ochrony** zapewniają ochronę bezpiecznych załączników wszystkim adresatom, którzy nie są jeszcze uwzględnieni w niestandardowych zasadach bezpiecznych załączników. Aby uzyskać więcej informacji, zobacz [Preset security policies in EOP and Ochrona usługi Office 365 w usłudze Microsoft Defender (Ustawienia wstępne zasad zabezpieczeń w usłudze EOP i Ochrona usługi Office 365 w usłudze Microsoft Defender](preset-security-policies.md)).

#### <a name="global-settings-for-safe-attachments"></a>Ustawienia globalne bezpiecznych załączników

> [!NOTE]
> Ustawienia globalne bezpiecznych załączników są ustawiane przez wstępnie ustawione zasady zabezpieczeń **wbudowanej ochrony** , ale nie przez **standardowe lub** **ścisłe** zasady zabezpieczeń. Tak czy inaczej, administratorzy mogą modyfikować te globalne ustawienia bezpiecznych załączników w dowolnym momencie.
>
> Kolumna **Domyślne** zawiera wartości przed istnieniem **zasad zabezpieczeń wstępnie ustawionych wbudowanej ochrony** . Kolumna **Wbudowana ochrona** pokazuje wartości, które są ustawiane przez **wbudowane** zasady zabezpieczeń wstępnie ustawione, które są również naszymi zalecanymi wartościami.

Aby skonfigurować te ustawienia, zobacz [Włączanie bezpiecznych załączników dla programów SharePoint, OneDrive i Microsoft Teams](turn-on-mdo-for-spo-odb-and-teams.md) oraz [Bezpieczne dokumenty w Microsoft 365 E5](safe-docs.md).

W programie PowerShell używasz polecenia cmdlet [Set-AtpPolicyForO365](/powershell/module/exchange/set-atppolicyforo365) dla tych ustawień.

|Nazwa funkcji zabezpieczeń|Domyślne|Wbudowana ochrona|Komentowanie|
|---|:---:|:---:|---|
|**Włączanie Ochrona usługi Office 365 w usłudze Defender dla programów SharePoint, OneDrive i Microsoft Teams** <p> _EnableATPForSPOTeamsODB_|Wył. <p> `$false`|Na <p> `$true`|Aby uniemożliwić użytkownikom pobieranie złośliwych plików, zobacz [Używanie programu PowerShell usługi SharePoint Online, aby uniemożliwić użytkownikom pobieranie złośliwych plików](turn-on-mdo-for-spo-odb-and-teams.md#step-2-recommended-use-sharepoint-online-powershell-to-prevent-users-from-downloading-malicious-files).|
|**Włączanie bezpiecznych dokumentów dla klientów pakietu Office** <p> _EnableSafeDocs_|Wył. <p> `$false`|Na <p> `$true`|Ta funkcja jest dostępna i zrozumiała tylko w przypadku licencji, które nie są uwzględnione w Ochrona usługi Office 365 w usłudze Defender (na przykład Microsoft 365 E5 lub Zabezpieczenia platformy Microsoft 365 E5). Aby uzyskać więcej informacji, zobacz [Safe Documents in Microsoft 365 E5 (Bezpieczne dokumenty w Microsoft 365 E5](safe-docs.md)).|
|**Zezwalaj użytkownikom na klikanie widoku chronionego, nawet jeśli bezpieczne dokumenty zidentyfikowały plik jako złośliwy** <p> _AllowSafeDocsOpen_|Wył. <p> `$false`|Wył. <p> `$false`|To ustawienie jest związane z bezpiecznymi dokumentami.|

#### <a name="safe-attachments-policy-settings"></a>Ustawienia zasad bezpiecznych załączników

Aby skonfigurować te ustawienia, zobacz [Konfigurowanie zasad bezpiecznych załączników w Ochrona usługi Office 365 w usłudze Defender](set-up-safe-attachments-policies.md).

W programie PowerShell dla tych ustawień są używane polecenia cmdlet [New-SafeAttachmentPolicy](/powershell/module/exchange/new-safeattachmentpolicy) i [Set-SafeAttachmentPolicy](/powershell/module/exchange/set-safelinkspolicy) .

> [!NOTE]
> Zgodnie z wcześniejszym opisem nie ma domyślnych zasad bezpiecznych załączników, ale ochrona bezpiecznych załączników jest przypisywana do wszystkich adresatów przez [wstępnie ustawione zasady zabezpieczeń **wbudowanej ochrony**](preset-security-policies.md).
>
> **Kolumna Domyślne w kolumnie niestandardowej** odwołuje się do wartości domyślnych utworzonych w nowych zasadach bezpiecznych załączników. Pozostałe kolumny wskazują (o ile nie zaznaczono inaczej) wartości skonfigurowane w odpowiednich wstępnie ustawionych zasadach zabezpieczeń.

|Nazwa funkcji zabezpieczeń|Wartość domyślna w obszarze niestandardowym|Wbudowana ochrona|Standard|Ścisłe|Komentowanie|
|---|:---:|:---:|:---:|:---:|---|
|**Odpowiedź na nieznane złośliwe oprogramowanie dotyczące bezpiecznych załączników** <p> _Włączanie_ i _działanie_|**Wył.** <p> `-Enable $false` I `-Action Block`|**Blokuj** <p> `-Enable $true` I `-Action Block`|**Blokuj** <p> `-Enable $true` I `-Action Block`|**Blokuj** <p> `-Enable $true` I `-Action Block`|Gdy parametr _Enable_ jest $false, wartość parametru _Action_ nie ma znaczenia.|
|**Zasady kwarantanny** (_QuarantineTag_)|AdminOnlyAccessPolicy|AdminOnlyAccessPolicy|AdminOnlyAccessPolicy|AdminOnlyAccessPolicy| <p> Standardowe i ścisłe wstępnie ustawione zasady zabezpieczeń używają domyślnych zasad kwarantanny (AdminOnlyAccessPolicy bez powiadomień o kwarantannie) zgodnie z opisem w tabeli [tutaj](quarantine-policies.md#step-2-assign-a-quarantine-policy-to-supported-features). <p> Podczas tworzenia nowych zasad bezpiecznych załączników pusta wartość oznacza, że domyślne zasady kwarantanny są używane do definiowania historycznych możliwości komunikatów, które zostały poddane kwarantannie przez bezpieczne załączniki (AdminOnlyAccessPolicy bez powiadomień kwarantanny). <p> Administratorzy mogą tworzyć i wybierać niestandardowe zasady kwarantanny, które definiują więcej możliwości dla użytkowników. Aby uzyskać więcej informacji, zobacz [Zasady kwarantanny](quarantine-policies.md).|
|**Przekierowanie załącznika z wykrytymi załącznikami** : **Włącz przekierowanie** <p> _Przekierowanie_ <p> _RedirectAddress_|Nie wybrano i nie określono adresu e-mail. <p> `-Redirect $false` <p> _RedirectAddress_ jest pusty (`$null`)|Nie wybrano i nie określono adresu e-mail. <p> `-Redirect $false` <p> _RedirectAddress_ jest pusty (`$null`)|Wybrano i określ adres e-mail. <p> `$true` <p> adres e-mail|Wybrano i określ adres e-mail. <p> `$true` <p> adres e-mail|Przekieruj komunikaty do administratora zabezpieczeń w celu sprawdzenia. <p> **Uwaga**: to ustawienie nie jest skonfigurowane w zasadach zabezpieczeń wstępnie ustawionych w **warstwie Standardowa**, **Ścisła** ani **Wbudowana ochrona** . Wartości **Standardowe** i **Ścisłe** wskazują **zalecane** wartości w nowych zasadach bezpiecznych załączników, które tworzysz.|
|**Zastosuj odpowiedź wykrywania bezpiecznych załączników, jeśli skanowanie nie może zakończyć się (przekroczenie limitu czasu lub błędy)** <p> _ActionOnError_|Wybrane <p> `$true`|Wybrane <p> `$true`|Wybrane <p> `$true`|Wybrane <p> `$true`||

### <a name="safe-links-settings"></a>Ustawienia bezpiecznych łączy

Bezpieczne linki w Ochrona usługi Office 365 w usłudze Defender obejmują ustawienia globalne, które mają zastosowanie do wszystkich użytkowników, którzy są uwzględniane w aktywnych zasadach bezpiecznych łączy, oraz ustawienia specyficzne dla poszczególnych zasad bezpiecznych łączy. Aby uzyskać więcej informacji, zobacz [Bezpieczne linki w Ochrona usługi Office 365 w usłudze Defender](safe-links.md).

Chociaż nie ma domyślnych zasad bezpiecznych łączy, wstępnie ustawione zasady zabezpieczeń **wbudowanej ochrony** zapewniają ochronę bezpiecznych łączy wszystkim adresatom (użytkownikom, którzy nie są zdefiniowani w niestandardowych zasadach bezpiecznych łączy). Aby uzyskać więcej informacji, zobacz [Preset security policies in EOP and Ochrona usługi Office 365 w usłudze Microsoft Defender (Ustawienia wstępne zasad zabezpieczeń w usłudze EOP i Ochrona usługi Office 365 w usłudze Microsoft Defender](preset-security-policies.md)).

#### <a name="global-settings-for-safe-links"></a>Ustawienia globalne bezpiecznych linków

> [!NOTE]
> Ustawienia globalne bezpiecznych linków są ustawiane przez wstępnie ustawione zasady zabezpieczeń **wbudowanej ochrony** , ale nie przez **standardowe lub** **ścisłe** zasady zabezpieczeń. Tak czy inaczej, administratorzy mogą modyfikować te globalne ustawienia bezpiecznych łączy w dowolnym momencie.
>
> Kolumna **Domyślne** zawiera wartości przed istnieniem **zasad zabezpieczeń wstępnie ustawionych wbudowanej ochrony** . Kolumna **Wbudowana ochrona** pokazuje wartości, które są ustawiane przez **wbudowane** zasady zabezpieczeń wstępnie ustawione, które są również naszymi zalecanymi wartościami.

Aby skonfigurować te ustawienia, zobacz [Konfigurowanie ustawień globalnych bezpiecznych łączy w Ochrona usługi Office 365 w usłudze Defender](configure-global-settings-for-safe-links.md).

W programie PowerShell używasz polecenia cmdlet [Set-AtpPolicyForO365](/powershell/module/exchange/set-atppolicyforo365) dla tych ustawień.

|Nazwa funkcji zabezpieczeń|Domyślne|Wbudowana ochrona|Komentowanie|
|---|:---:|:---:|---|
|**Blokuj następujące adresy URL** <p> _ExcludedUrls_|Puste <p> `$null`|Puste <p> `$null`|Nie mamy żadnych konkretnych zaleceń dotyczących tego ustawienia. <p> Aby uzyskać więcej informacji, zobacz ["Blokuj następujące adresy URL" listy bezpiecznych linków](safe-links.md#block-the-following-urls-list-for-safe-links). <p> **Uwaga**: możesz teraz zarządzać wpisami adresu URL bloku na [liście dozwolonych/zablokowanych dzierżaw](allow-block-urls.md#create-block-url-entries-in-the-tenant-allowblock-list). Lista "Blokuj następujące adresy URL" jest w trakcie wycofywania. Spróbujemy przeprowadzić migrację istniejących wpisów z listy "Blokuj następujące adresy URL", aby zablokować wpisy adresów URL na liście dozwolonych/zablokowanych dzierżaw. Komunikaty zawierające zablokowany adres URL zostaną poddane kwarantannie.|
|**Używanie bezpiecznych linków w aplikacjach Office 365** <p> _EnableSafeLinksForO365Clients_|Na <p> `$true`|Na <p> `$true`|Używaj bezpiecznych linków w obsługiwanych aplikacjach Office 365 klasycznych i mobilnych (iOS i Android). Aby uzyskać więcej informacji, zobacz [Ustawienia bezpiecznych linków dla aplikacji Office 365](safe-links.md#safe-links-settings-for-office-365-apps).|
|**Nie śledź, gdy użytkownicy klikają linki chronione w aplikacjach Office 365** <p> _TrackClicks_|Na <p> `$false`|Wył. <p> `$true`|Wyłączenie tego ustawienia (ustawienie _pozycji TrackClicks_ na `$true`) śledzi kliknięcia użytkowników w obsługiwanych aplikacjach Office 365.|
|**Nie zezwalaj użytkownikom na klikanie oryginalnego adresu URL w aplikacjach Office 365** <p> _AllowClickThrough_|Na <p> `$false`|Na <p> `$false`|Włączenie tego ustawienia (ustawienie _allowClickThrough_ `$false`na ) uniemożliwia kliknięcie oryginalnego adresu URL w obsługiwanych aplikacjach Office 365.|

#### <a name="safe-links-policy-settings"></a>Ustawienia zasad bezpiecznych łączy

Aby skonfigurować te ustawienia, zobacz [Konfigurowanie zasad bezpiecznych łączy w Ochrona usługi Office 365 w usłudze Microsoft Defender](set-up-safe-links-policies.md).

W programie PowerShell dla tych ustawień są używane polecenia cmdlet [New-SafeLinksPolicy](/powershell/module/exchange/new-safelinkspolicy) i [Set-SafeLinksPolicy](/powershell/module/exchange/set-safelinkspolicy) .

> [!NOTE]
> Zgodnie z wcześniejszym opisem nie ma domyślnych zasad bezpiecznych łączy, ale ochrona bezpiecznych łączy jest przypisywana do wszystkich adresatów za pomocą [**wbudowanych zasad zabezpieczeń wstępnie** ustawionych zabezpieczeń](preset-security-policies.md) ochrony.
>
> **Kolumna Domyślne w kolumnie niestandardowej** odwołuje się do wartości domyślnych w nowych zasadach bezpiecznych łączy, które tworzysz. Pozostałe kolumny wskazują (o ile nie zaznaczono inaczej) wartości skonfigurowane w odpowiednich wstępnie ustawionych zasadach zabezpieczeń.

|Nazwa funkcji zabezpieczeń|Wartość domyślna w obszarze niestandardowym|Wbudowana ochrona|Standard|Ścisłe|Komentowanie|
|---|:---:|:---:|:---:|:---:|---|
|**Adres URL & kliknij ustawienia ochrony**||||||
|**Akcja dotycząca potencjalnie złośliwych adresów URL w wiadomościach e-mail**||||||
|**Włączone: Bezpieczne linki sprawdzają listę znanych, złośliwych linków, gdy użytkownicy klikają linki w wiadomości e-mail** <p> _EnableSafeLinksForEmail_|Nie zaznaczono <p> `$false`|Wybrane <p> `$true`|Wybrane <p> `$true`|Wybrane <p> `$true`||
|**Stosowanie bezpiecznych linków do wiadomości e-mail wysyłanych w organizacji** <p> _EnableForInternalSenders_|Nie zaznaczono <p> `$false`|Wybrane <p> `$true`|Wybrane <p> `$true`|Wybrane <p> `$true`||
|**Stosowanie skanowania adresów URL w czasie rzeczywistym w poszukiwaniu podejrzanych linków i linków wskazujących pliki** <p> _ScanUrls_|Nie zaznaczono <p> `$false`|Wybrane <p> `$true`|Wybrane <p> `$true`|Wybrane <p> `$true`||
|**Przed dostarczeniem komunikatu poczekaj na ukończenie skanowania adresu URL** <p> _DeliverMessageAfterScan_|Nie zaznaczono <p> `$false`|Wybrane <p> `$true`|Wybrane <p> `$true`|Wybrane <p> `$true`||
|**Nie należy ponownie pisać adresów URL, sprawdzaj tylko za pośrednictwem interfejsu API bezpiecznych linków** <p> _DisableURLRewrite_|Nie zaznaczono <p> `$false`|Wybrane <p> `$true`|Nie zaznaczono <p> `$false`|Nie zaznaczono <p> `$false`||
|**Nie należy ponownie pisać następujących adresów URL w wiadomości e-mail** <p> _DoNotRewriteUrls_|Nie zaznaczono <p> Puste|Nie zaznaczono <p> Puste|Nie zaznaczono <p> Puste|Nie zaznaczono <p> Puste|Nie mamy żadnych konkretnych zaleceń dotyczących tego ustawienia. <p> **Uwaga**: Celem listy "Nie przepisuj ponownie następujących adresów URL" jest pominięcie zawijania bezpiecznych łączy określonych adresów URL. Zamiast korzystać z tej listy, można teraz [tworzyć wpisy dozwolonych adresów URL na liście dozwolonych/zablokowanych dzierżaw](allow-block-urls.md#create-allow-url-entries).|
|**Akcja dla potencjalnie złośliwych adresów URL w usłudze Microsoft Teams**||||||
|**On: Safe Links checks a list of known, malicious links when users click links in Microsoft Teams** <p> _EnableSafeLinksForTeams_|Nie zaznaczono <p> `$false`|Wybrane <p> `$true`|Wybrane <p> `$true`|Wybrane <p> `$true`||
|**Kliknij ustawienia ochrony**||||||
|**Śledzenie kliknięć użytkowników** <p> _TrackUserClicks_|Wybrane <p> `$true`|Wybrane <p> `$true`|Wybrane <p> `$true`|Wybrane <p> `$true`||
|**Zezwalaj użytkownikom na klikanie oryginalnego adresu URL** <p> _AllowClickThrough_|Wybrane <p> `$true`|Wybrane <p> `$true`|Nie zaznaczono <p> `$false`|Nie zaznaczono <p> `$false`|Wyłączenie tego ustawienia (ustawienie _opcji AllowClickThrough_ `$false`na ) uniemożliwia przejście do oryginalnego adresu URL.|
|**Wyświetlanie znakowania organizacji na stronach powiadomień i ostrzeżeń** <p> _EnableOrganizationBranding_|Nie zaznaczono <p> `$false`|Nie zaznaczono <p> `$false`|Nie zaznaczono <p> `$false`|Nie zaznaczono <p> `$false`|Nie mamy żadnych konkretnych zaleceń dotyczących tego ustawienia. <p> Przed włączeniem tego ustawienia należy postępować zgodnie z instrukcjami w [temacie Dostosowywanie motywu platformy Microsoft 365 dla organizacji](../../admin/setup/customize-your-organization-theme.md) , aby przekazać logo firmy.|
|**Powiadomienie**||||||
|**Jak chcesz powiadomić użytkowników?**|**Użyj domyślnego tekstu powiadomienia**|**Użyj domyślnego tekstu powiadomienia**|**Użyj domyślnego tekstu powiadomienia**|**Użyj domyślnego tekstu powiadomienia**|Nie mamy żadnych konkretnych zaleceń dotyczących tego ustawienia. <p> Możesz wybrać pozycję **Użyj niestandardowego tekstu powiadomień** (_CustomNotificationText_), aby wprowadzić dostosowany tekst powiadomienia do użycia. Możesz również wybrać pozycję **Użyj usługi Microsoft Translator do automatycznej lokalizacji** (_UseTranslatedNotificationText_), aby przetłumaczyć niestandardowy tekst powiadomienia na język użytkownika.

## <a name="related-articles"></a>Powiązane artykuły:

- Szukasz najlepszych rozwiązań dotyczących **reguł przepływu poczty programu Exchange (nazywanych również regułami transportu**)? Zobacz [Najlepsze rozwiązania dotyczące konfigurowania reguł przepływu poczty w Exchange Online](/exchange/security-and-compliance/mail-flow-rules/configuration-best-practices).

- Administratorzy i użytkownicy mogą przesyłać do firmy Microsoft wyniki fałszywie dodatnie (dobra wiadomość e-mail oznaczona jako zła) i fałszywie ujemne (niedozwolona wiadomość e-mail). Aby uzyskać więcej informacji, zobacz [Zgłaszanie komunikatów i plików do firmy Microsoft](report-junk-email-messages-to-microsoft.md).

- Skorzystaj z tych linków, aby uzyskać informacje na temat **konfigurowania** [usługi EOP](/exchange/standalone-eop/set-up-your-eop-service) i **konfigurowania** [Ochrona usługi Office 365 w usłudze Microsoft Defender](defender-for-office-365.md). Nie zapomnij o pomocnych kierunkach w [temacie "Ochrona przed zagrożeniami w Office 365](protect-against-threats.md)".

- **Punkty odniesienia zabezpieczeń dla systemu Windows** można znaleźć tutaj: [Gdzie można uzyskać punkty odniesienia zabezpieczeń?](/windows/security/threat-protection/windows-security-baselines#where-can-i-get-the-security-baselines) w przypadku opcji obiektu zasad grupy/lokalnego i [Użyj punktów odniesienia zabezpieczeń, aby skonfigurować urządzenia z systemem Windows w Intune](/intune/protect/security-baselines) na potrzeby zabezpieczeń opartych na Intune. Na koniec porównanie punktów odniesienia zabezpieczeń Ochrona punktu końcowego w usłudze Microsoft Defender i Microsoft Intune jest dostępne w artykule [Porównanie Ochrona punktu końcowego w usłudze Microsoft Defender i Intune punktów odniesienia zabezpieczeń systemu Windows](/windows/security/threat-protection/microsoft-defender-atp/configure-machines-security-baseline#compare-the-microsoft-defender-atp-and-the-windows-intune-security-baselines).
