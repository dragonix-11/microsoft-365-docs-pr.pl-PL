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
ms.openlocfilehash: bd30be87a277d271fece74a9700a60992a562399
ms.sourcegitcommit: a7c1acfb3d2cbba913e32493b16ebd8cbfeee456
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/13/2022
ms.locfileid: "66043034"
---
# <a name="recommended-settings-for-eop-and-microsoft-defender-for-office-365-security"></a>Zalecane ustawienia zabezpieczeń EOP i Ochrona usługi Office 365 w usłudze Microsoft Defender

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Usługi Microsoft Defender dla usługi Office 365 (plan 1 i plan 2)](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

**Exchange Online Protection (EOP)** jest podstawą zabezpieczeń dla subskrypcji Microsoft 365 i pomaga zapobiegać docieraniu złośliwych wiadomości e-mail do skrzynek odbiorczych pracownika. Jednak w przypadku nowych, bardziej zaawansowanych ataków pojawiających się każdego dnia często wymagane są ulepszone zabezpieczenia. **Ochrona usługi Office 365 w usłudze Microsoft Defender** Plan 1 lub Plan 2 zawierają dodatkowe funkcje, które zapewniają administratorom więcej warstw zabezpieczeń, kontroli i badania.

Mimo że umożliwiamy administratorom zabezpieczeń dostosowywanie ich ustawień zabezpieczeń, zalecamy stosowanie dwóch poziomów zabezpieczeń w ramach EOP i Ochrona usługi Office 365 w usłudze Microsoft Defender: **Standardowa** i **Ścisła**. Mimo że środowiska i potrzeby klientów są różne, te poziomy filtrowania pomogą zapobiec docieraniu niechcianej poczty do skrzynki odbiorczej pracowników w większości sytuacji.

Aby automatycznie zastosować ustawienia standardowe lub ścisłe do użytkowników, zobacz [Wstępnie ustawione zasady zabezpieczeń w usłudze EOP i Ochrona usługi Office 365 w usłudze Microsoft Defender](preset-security-policies.md).

W tym artykule opisano ustawienia domyślne, a także zalecane ustawienia standardowe i ścisłe, które ułatwiają ochronę użytkowników. Tabele zawierają ustawienia w portalu Microsoft 365 Defender i programie PowerShell (Exchange Online programu PowerShell lub autonomicznej Exchange Online Protection programu PowerShell dla organizacji bez Exchange Online skrzynek pocztowych).

> [!NOTE]
> Moduł Office 365 Advanced Threat Protection Recommended Configuration Analyzer (ORCA) dla programu PowerShell może ułatwić (administratorom) znalezienie bieżących wartości tych ustawień. W szczególności polecenie cmdlet **Get-ORCAReport** generuje ocenę ochrony przed spamem, ochrony przed wyłudzaniem informacji i innych ustawień higieny wiadomości. Moduł ORCA można pobrać pod adresem <https://www.powershellgallery.com/packages/ORCA/>.
>
> W Microsoft 365 organizacjach zalecamy pozostawienie filtru wiadomości-śmieci w Outlook ustawić wartość **Brak automatycznego filtrowania**, aby zapobiec niepotrzebnym konfliktom (zarówno pozytywnym, jak i negatywnym) z werdyktami filtrowania spamu z EOP. Aby uzyskać więcej informacji, zapoznaj się z następującymi artykułami:
>
> - [Konfigurowanie ustawień wiadomości-śmieci w skrzynkach pocztowych Exchange Online](configure-junk-email-settings-on-exo-mailboxes.md)
> - [Informacje o ustawieniach wiadomości-śmieci w Outlook](configure-junk-email-settings-on-exo-mailboxes.md#about-junk-email-settings-in-outlook)
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
|**Próg zbiorczej poczty e-mail** <br/><br/> _BulkThreshold_|7|6|4|Aby uzyskać szczegółowe informacje, zobacz [Poziom skarg zbiorczych (BCL) w EOP](bulk-complaint-level-values.md).|
|_MarkAsSpamBulkMail_|`On`|`On`|`On`|To ustawienie jest dostępne tylko w programie PowerShell.|
|**Zwiększanie ustawień oceny spamu**|Wył.|Wył.|Wył.|Wszystkie te ustawienia są częścią zaawansowanego filtru spamu (ASF). Aby uzyskać więcej informacji, zobacz [sekcję Ustawienia asf w zasadach ochrony przed spamem](#asf-settings-in-anti-spam-policies) w tym artykule.|
|**Oznacz jako ustawienia spamu**|Wył.|Wył.|Wył.|Większość z tych ustawień jest częścią usługi ASF. Aby uzyskać więcej informacji, zobacz [sekcję Ustawienia asf w zasadach ochrony przed spamem](#asf-settings-in-anti-spam-policies) w tym artykule.|
|**Zawiera określone języki** <br/><br/> _EnableLanguageBlockList_ <br/><br/> _LanguageBlockList_|**Wył.** <br/><br/> `$false` <br/><br/> Puste|**Wył.** <br/><br/> `$false` <br/><br/> Puste|**Wył.** <br/><br/> `$false` <br/><br/> Puste|Nie mamy żadnych konkretnych zaleceń dotyczących tego ustawienia. Komunikaty można blokować w określonych językach w zależności od potrzeb biznesowych.|
|**Z tych krajów** <br/><br/> _EnableRegionBlockList_ <br/><br/> _RegionBlockList_|**Wył.** <br/><br/> `$false` <br/><br/> Puste|**Wył.** <br/><br/> `$false` <br/><br/> Puste|**Wył.** <br/><br/> `$false` <br/><br/> Puste|Nie mamy żadnych konkretnych zaleceń dotyczących tego ustawienia. Komunikaty z określonych krajów można blokować w zależności od potrzeb biznesowych.|
|**Tryb testu** (_TestModeAction_)|**Brak**|**Brak**|**Brak**|To ustawienie jest częścią usługi ASF. Aby uzyskać więcej informacji, zobacz [sekcję Ustawienia asf w zasadach ochrony przed spamem](#asf-settings-in-anti-spam-policies) w tym artykule.|
|**Działania**||||Wszędzie tam, gdzie **wybrano komunikat kwarantanny**, dostępne jest pole **Wyboru zasad kwarantanny** . Zasady kwarantanny definiują, co użytkownicy mogą robić w przypadku komunikatów poddanych kwarantannie. <br/><br/> Standardowe i ścisłe wstępnie ustawione zasady zabezpieczeń używają domyślnych zasad kwarantanny (AdminOnlyAccessPolicy lub DefaultFullAccessPolicy bez powiadomień kwarantanny) zgodnie z opisem w tabeli [tutaj](quarantine-policies.md#step-2-assign-a-quarantine-policy-to-supported-features). <br/><br/> Podczas tworzenia nowych zasad ochrony przed spamem pusta wartość oznacza, że domyślne zasady kwarantanny są używane do definiowania historycznych możliwości komunikatów, które zostały poddane kwarantannie przez ten konkretny werdykt (AdminOnlyAccessPolicy bez powiadomień kwarantanny dotyczących **wyłudzania informacji o wysokim poziomie zaufania**; DefaultFullAccessPolicy bez powiadomień o kwarantannie dla wszystkiego innego). <br/><br/> Administratorzy mogą tworzyć i wybierać niestandardowe zasady kwarantanny, które definiują bardziej restrykcyjne lub mniej restrykcyjne możliwości dla użytkowników w domyślnych lub niestandardowych zasadach ochrony przed spamem. Aby uzyskać więcej informacji, zobacz [Zasady kwarantanny](quarantine-policies.md).|
|Akcja wykrywania **spamu** <br/><br/> _SpamAction_|**Przenoszenie wiadomości do folderu Wiadomości-śmieci** <br/><br/> `MoveToJmf`|**Przenoszenie wiadomości do folderu Wiadomości-śmieci** <br/><br/> `MoveToJmf`|**Komunikat kwarantanny** <br/><br/> `Quarantine`||
|**Akcja wykrywania spamu o wysokim poziomie ufności** <br/><br/> _HighConfidenceSpamAction_|**Przenoszenie wiadomości do folderu Wiadomości-śmieci** <br/><br/> `MoveToJmf`|**Komunikat kwarantanny** <br/><br/> `Quarantine`|**Komunikat kwarantanny** <br/><br/> `Quarantine`||
|Akcja wykrywania **wyłudzania informacji** <br/><br/> _PhishSpamAction_|**Przenoszenie wiadomości do folderu Wiadomości-śmieci**<sup>\*</sup> <br/><br/> `MoveToJmf`|**Komunikat kwarantanny** <br/><br/> `Quarantine`|**Komunikat kwarantanny** <br/><br/> `Quarantine`|<sup>\*</sup> Wartość domyślna to **Przenieś wiadomość do folderu Wiadomości-śmieci** w domyślnych zasadach ochrony przed spamem oraz w nowych zasadach ochrony przed spamem utworzonych w programie PowerShell. Wartość domyślna to **Komunikat kwarantanny** w nowych zasadach ochrony przed spamem tworzonych w portalu Microsoft 365 Defender.|
|**Akcja wykrywania wyłudzania informacji o wysokim poziomie zaufania** <br/><br/> _HighConfidencePhishAction_|**Komunikat kwarantanny** <br/><br/> `Quarantine`|**Komunikat kwarantanny** <br/><br/> `Quarantine`|**Komunikat kwarantanny** <br/><br/> `Quarantine`||
|Akcja wykrywania **zbiorczego** <br/><br/> _BulkSpamAction_|**Przenoszenie wiadomości do folderu Wiadomości-śmieci** <br/><br/> `MoveToJmf`|**Przenoszenie wiadomości do folderu Wiadomości-śmieci** <br/><br/> `MoveToJmf`|**Komunikat kwarantanny** <br/><br/> `Quarantine`||
|**Przechowywanie spamu w kwarantannie przez tyle dni** <br/><br/> _KwarantannaRetentionPeriod_|15 dni<sup>\*</sup>|30 dni|30 dni|<sup>\*</sup> Wartość domyślna to 15 dni w domyślnych zasadach ochrony przed spamem i w nowych zasadach ochrony przed spamem utworzonych w programie PowerShell. Wartość domyślna to 30 dni w nowych zasadach ochrony przed spamem tworzonych w portalu Microsoft 365 Defender. <br/><br/> Ta wartość ma również wpływ na komunikaty poddane kwarantannie przez zasady ochrony przed wyłudzaniem informacji. Aby uzyskać więcej informacji, zobacz [Kwarantanna wiadomości e-mail w EOP](quarantine-email-messages.md).|
|**Włączanie wskazówek dotyczących bezpieczeństwa spamu** <br/><br/> _InlineSafetyTipsEnabled_|Wybrane <br/><br/> `$true`|Wybrane <br/><br/> `$true`|Wybrane <br/><br/> `$true`||
|Włączanie automatycznego przeczyszczania w godzinach zerowych (ZAP) na potrzeby wiadomości wyłudzających informacje <br/><br/> _PhishZapEnabled_|Wybrane <br/><br/> `$true`|Wybrane <br/><br/> `$true`|Wybrane <br/><br/> `$true`||
|Włączanie zap dla wiadomości niepożądanych <br/><br/> _SpamZapEnabled_|Wybrane <br/><br/> `$true`|Wybrane <br/><br/> `$true`|Wybrane <br/><br/> `$true`||
|**Zezwalaj na listę zablokowanych &**|||||
|Dozwoloni nadawcy <br/><br/> _AllowedSenders_|Brak|Brak|Brak||
|Dozwolone domeny nadawcy <br/><br/> _AllowedSenderDomains_|Brak|Brak|Brak|Dodawanie domen do listy dozwolonych nadawców jest bardzo złym pomysłem. Osoby atakujące będą mogły wysłać Ci wiadomość e-mail, która w przeciwnym razie zostałaby odfiltrowana. <br/><br/> Skorzystaj ze [szczegółowych informacji analitycznych na temat fałszowania](learn-about-spoof-intelligence.md) i [listy dozwolonych/zablokowanych dzierżaw](tenant-allow-block-list.md) , aby przejrzeć wszystkich nadawców, którzy podszywają się pod adresy e-mail nadawcy w domenach poczty e-mail w organizacji lub podszywają się pod adresy e-mail nadawcy w domenach zewnętrznych.|
|Zablokowani nadawcy <br/><br/> _BlockedSenders_|Brak|Brak|Brak||
|Zablokowane domeny nadawcy <br/><br/> _BlockedSenderDomains_|Brak|Brak|Brak||

#### <a name="asf-settings-in-anti-spam-policies"></a>Ustawienia usługi ASF w zasadach ochrony przed spamem

W tabeli w tej sekcji opisano ustawienia zaawansowanego filtru spamu (ASF), które są dostępne w zasadach ochrony przed spamem. Wszystkie te ustawienia są **wyłączone** dla poziomów **standardowych** i **ścisłych** . Aby uzyskać więcej informacji na temat ustawień asf, zobacz [Ustawienia zaawansowanego filtru spamu (ASF) w EOP](advanced-spam-filtering-asf-options.md).

|Nazwa funkcji zabezpieczeń|Komentowanie|
|---|---|
|**Linki obrazów do lokacji zdalnych** (_IncreaseScoreWithImageLinks_)||
|**Numeryczny adres IP w adresie URL** (_IncreaseScoreWithNumericIps_)||
|**Przekierowanie adresu URL do innego portu** (_IncreaseScoreWithRedirectToOtherPort_)||
|**Linki do witryn .biz lub .info** (_IncreaseScoreWithBizOrInfoUrls_)||
|**Puste komunikaty** (_MarkAsSpamEmptyMessages_)||
|**Osadzanie tagów w języku HTML** (_MarkAsSpamEmbedTagsInHtml_)||
|**JavaScript lub VBScript w języku HTML** (_MarkAsSpamJavaScriptInHtml_)||
|**Tagi formularzy w języku HTML** (_MarkAsSpamFormTagsInHtml_)||
|**Tagi ramek lub ramek w języku HTML** (_MarkAsSpamFramesInHtml_)||
|**Usterki internetowe w języku HTML** (_MarkAsSpamWebBugsInHtml_)||
|**Tagi obiektów w języku HTML** (_MarkAsSpamObjectTagsInHtml_)||
|**Wyrazy wrażliwe** (_MarkAsSpamSensitiveWordList_)||
|**Rekord SPF: twardy błąd** (_MarkAsSpamSpfRecordHardFail_)||
|**Filtrowanie identyfikatora nadawcy nie powiodło się** (_MarkAsSpamFromAddressAuthFail_)||
|**Backscatter** (_MarkAsSpamNdrBackscatter_)||
|**Tryb testu** (_TestModeAction_)|W przypadku ustawień asf, które obsługują akcję **Testuj** jako akcję, możesz skonfigurować akcję trybu **testowego na wartość Brak**, **Dodaj domyślny tekst X-Header** lub **Wyślij komunikat Bcc** (`None`, `AddXHeader`lub `BccMessage`). Aby uzyskać więcej informacji, zobacz [Włączanie, wyłączanie lub testowanie ustawień asf](advanced-spam-filtering-asf-options.md#enable-disable-or-test-asf-settings).|

#### <a name="eop-outbound-spam-policy-settings"></a>Ustawienia zasad wychodzących zasad dotyczących spamu w usłudze EOP

Aby utworzyć i skonfigurować zasady wychodzącego spamu, zobacz [Konfigurowanie filtrowania spamu wychodzącego w ramach EOP](configure-the-outbound-spam-policy.md).

Aby uzyskać więcej informacji na temat domyślnych limitów wysyłania w usłudze, zobacz [Wysyłanie limitów](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#sending-limits-1).

> [!NOTE]
> Zasady wychodzącego spamu nie są częścią standardowych ani rygorystycznych wstępnie ustawionych zasad zabezpieczeń. Wartości **Standardowe** i **Ścisłe** wskazują **zalecane** wartości w domyślnych zasadach spamu wychodzącego lub niestandardowych utworzonych przez Ciebie zasadach spamu wychodzącego.

|Nazwa funkcji zabezpieczeń|Domyślne|Zalecane<br/>Standard|Zalecane<br/>Ścisłe|Komentowanie|
|---|:---:|:---:|:---:|---|
|**Ustawianie limitu komunikatów zewnętrznych** <br/><br/> _AdresatLimitExternalPerHour_|0|500|400|Wartość domyślna 0 oznacza użycie wartości domyślnych usługi.|
|**Ustawianie wewnętrznego limitu komunikatów** <br/><br/> _AdresatLimitInternalPerHour_|0|1000|800|Wartość domyślna 0 oznacza użycie wartości domyślnych usługi.|
|**Ustawianie dziennego limitu komunikatów** <br/><br/> _AdresatLimitPerDay_|0|1000|800|Wartość domyślna 0 oznacza użycie wartości domyślnych usługi.|
|**Ograniczenie nałożone na użytkowników, którzy osiągną limit komunikatów** <br/><br/> _ActionWhenThresholdReached_|**Ogranicz użytkownikowi wysyłanie wiadomości e-mail do następnego dnia** <br/><br/> `BlockUserForToday`|**Ograniczanie użytkownikowi możliwości wysyłania wiadomości e-mail** <br/><br/> `BlockUser`|**Ograniczanie użytkownikowi możliwości wysyłania wiadomości e-mail** <br/><br/> `BlockUser`||
|**Reguły automatycznego przekazywania** <br/><br/> _AutoForwardingMode_|**Automatyczne — sterowane przez system** <br/><br/> `Automatic`|**Automatyczne — sterowane przez system** <br/><br/> `Automatic`|**Automatyczne — sterowane przez system** <br/><br/> `Automatic`|
|**Wysyłanie kopii komunikatów wychodzących przekraczających te limity do tych użytkowników i grup** <br/><br/> _BccSuspiciousOutboundMail_ <br/><br/> _BccSuspiciousOutboundAdditionalRecipients_|Nie zaznaczono <br/><br/> `$false` <br/><br/> Puste|Nie zaznaczono <br/><br/> `$false` <br/><br/> Puste|Nie zaznaczono <br/><br/> `$false` <br/><br/> Puste|Nie mamy żadnych konkretnych zaleceń dotyczących tego ustawienia. <br/><br/> To ustawienie działa tylko w domyślnych zasadach spamu wychodzącego. Nie działa to w ramach niestandardowych zasad spamu wychodzącego, które tworzysz.|
|**Powiadamiaj tych użytkowników i grupy, jeśli nadawca jest zablokowany z powodu wysyłania spamu wychodzącego** <br/><br/> _NotifyOutboundSpam_ <br/><br/> _NotifyOutboundSpamRecipients_|Nie zaznaczono <br/><br/> `$false` <br/><br/> Puste|Nie zaznaczono <br/><br/> `$false` <br/><br/> Puste|Nie zaznaczono <br/><br/> `$false` <br/><br/> Puste|Domyślne [zasady alertów](../../compliance/alert-policies.md) o nazwie **Użytkownik z ograniczeniami wysyłania wiadomości e-mail** wysyłają już powiadomienia e-mail do członków grupy **TenantAdmins** (**administratorzy globalni**), gdy użytkownicy są blokowani z powodu przekroczenia limitów w zasadach. **Zdecydowanie zalecamy używanie zasad alertów zamiast tego ustawienia w zasadach spamu wychodzącego w celu powiadamiania administratorów i innych użytkowników**. Aby uzyskać instrukcje, zobacz [Weryfikowanie ustawień alertów dla użytkowników z ograniczeniami](removing-user-from-restricted-users-portal-after-spam.md#verify-the-alert-settings-for-restricted-users).|

### <a name="eop-anti-malware-policy-settings"></a>Ustawienia zasad ochrony przed złośliwym oprogramowaniem EOP

Aby utworzyć i skonfigurować zasady ochrony przed złośliwym oprogramowaniem, zobacz [Konfigurowanie zasad ochrony przed złośliwym oprogramowaniem w ramach EOP](configure-anti-malware-policies.md).

|Nazwa funkcji zabezpieczeń|Domyślne|Standard|Ścisłe|Komentowanie|
|---|:---:|:---:|:---:|---|
|**Ustawienia ochrony**|||||
|**Włączanie wspólnego filtru załączników** <br/><br/> _EnableFileFilter_|Nie zaznaczono <br/><br/> `$false`|Wybrane <br/><br/> `$true`|Wybrane <br/><br/> `$true`|To ustawienie powoduje kwarantannę komunikatów zawierających załączniki wykonywalne na podstawie typu pliku, niezależnie od zawartości załącznika.|
|**Włączanie automatycznego przeczyszczania z zerową godziną w przypadku złośliwego oprogramowania** <br/><br/> _ZapEnabled_|Wybrane <br/><br/> `$true`|Wybrane <br/><br/> `$true`|Wybrane <br/><br/> `$true`||
|**Zasady kwarantanny**|AdminOnlyAccessPolicy|AdminOnlyAccessPolicy|AdminOnlyAccessPolicy|Podczas tworzenia nowych zasad ochrony przed złośliwym oprogramowaniem pusta wartość oznacza, że domyślne zasady kwarantanny są używane do definiowania historycznych możliwości komunikatów, które zostały poddane kwarantannie jako złośliwe oprogramowanie (AdminOnlyAccessPolicy bez powiadomień kwarantanny). <br/><br/> Standardowe i ścisłe wstępnie ustawione zasady zabezpieczeń używają domyślnych zasad kwarantanny (AdminOnlyAccessPolicy bez powiadomień o kwarantannie) zgodnie z opisem w tabeli [tutaj](quarantine-policies.md#step-2-assign-a-quarantine-policy-to-supported-features). <br/><br/> Administratorzy mogą tworzyć i wybierać niestandardowe zasady kwarantanny, które definiują więcej możliwości dla użytkowników w domyślnych lub niestandardowych zasadach ochrony przed złośliwym oprogramowaniem. Aby uzyskać więcej informacji, zobacz [Zasady kwarantanny](quarantine-policies.md).|
|**Powiadomienia adresatów**|||||
|**Powiadamianie adresatów o kwarantannie wiadomości jako złośliwe oprogramowanie** <br/><br/> _Akcja_|Nie zaznaczono <br/><br/> _DeleteMessage_|Nie zaznaczono <br/><br/> _DeleteMessage_|Nie zaznaczono <br/><br/> _DeleteMessage_|Jeśli złośliwe oprogramowanie zostanie wykryte w załączniku wiadomości e-mail, wiadomość zostanie poddana kwarantannie i może zostać wydana tylko przez administratora.|
|**Powiadomienia nadawcy**|||||
|**Powiadamianie wewnętrznych nadawców, gdy komunikaty są poddawane kwarantannie jako złośliwe oprogramowanie** <br/><br/> _EnableInternalSenderNotifications_|Nie zaznaczono <br/><br/> `$false`|Nie zaznaczono <br/><br/> `$false`|Nie zaznaczono <br/><br/> `$false`||
|**Powiadamianie nadawców zewnętrznych, gdy komunikaty są poddawane kwarantannie jako złośliwe oprogramowanie** <br/><br/> _EnableExternalSenderNotifications_|Nie zaznaczono <br/><br/> `$false`|Nie zaznaczono <br/><br/> `$false`|Nie zaznaczono <br/><br/> `$false`||
|**Powiadomienia administratora**|||||
|**Powiadamianie administratora o niedostarczonych komunikatach od nadawców wewnętrznych** <br/><br/> _EnableInternalSenderAdminNotifications_ <br/><br/> _InternalSenderAdminAddress_|Nie zaznaczono <br/><br/> `$false`|Nie zaznaczono <br/><br/> `$false`|Nie zaznaczono <br/><br/> `$false`|Nie mamy żadnych konkretnych zaleceń dotyczących tego ustawienia.|
|**Powiadamianie administratora o niedostarczonych komunikatach od nadawców zewnętrznych** <br/><br/> _EnableExternalSenderAdminNotifications_ <br/><br/> _ExternalSenderAdminAddress_|Nie zaznaczono <br/><br/> `$false`|Nie zaznaczono <br/><br/> `$false`|Nie zaznaczono <br/><br/> `$false`|Nie mamy żadnych konkretnych zaleceń dotyczących tego ustawienia.|
|**Dostosowywanie powiadomień**||||Nie mamy żadnych konkretnych zaleceń dotyczących tych ustawień.|
|**Korzystanie z dostosowanego tekstu powiadomień** <br/><br/> _CustomNotifications_|Nie zaznaczono <br/><br/> `$false`|Nie zaznaczono <br/><br/> `$false`|Nie zaznaczono <br/><br/> `$false`||
|**Z nazwy** <br/><br/> _CustomFromName_|Puste <br/><br/> `$null`|Puste <br/><br/> `$null`|Puste <br/><br/> `$null`||
|**Z adresu** <br/><br/> _CustomFromAddress_|Puste <br/><br/> `$null`|Puste <br/><br/> `$null`|Puste <br/><br/> `$null`||
|**Dostosowywanie powiadomień dotyczących komunikatów od nadawców wewnętrznych**||||Te ustawienia są używane tylko wtedy, **gdy powiadom wewnętrznych nadawców, gdy komunikaty zostaną poddane kwarantannie jako złośliwe oprogramowanie** lub zostanie wybrana opcja **Powiadom administratora o niedostarczonych komunikatach od nadawców wewnętrznych** .|
|**Temat** <br/><br/> _CustomInternalSubject_|Puste <br/><br/> `$null`|Puste <br/><br/> `$null`|Puste <br/><br/> `$null`||
|**Komunikat** <br/><br/> _CustomInternalBody_|Puste <br/><br/> `$null`|Puste <br/><br/> `$null`|Puste <br/><br/> `$null`||
|**Dostosowywanie powiadomień dotyczących komunikatów od nadawców zewnętrznych**||||Te ustawienia są używane tylko wtedy, **gdy powiadom zewnętrznych nadawców, gdy komunikaty są poddane kwarantannie jako złośliwe oprogramowanie** lub zostanie wybrana opcja **Powiadom administratora o niedostarczonych komunikatach od nadawców zewnętrznych** .|
|**Temat** <br/><br/> _CustomExternalSubject_|Puste <br/><br/> `$null`|Puste <br/><br/> `$null`|Puste <br/><br/> `$null`||
|**Komunikat** <br/><br/> _CustomExternalBody_|Puste <br/><br/> `$null`|Puste <br/><br/> `$null`|Puste <br/><br/> `$null`||

### <a name="eop-anti-phishing-policy-settings"></a>Ustawienia zasad ochrony przed wyłudzaniem informacji w usłudze EOP

Aby uzyskać więcej informacji na temat tych ustawień, zobacz [Spoof settings (Fałszowanie ustawień](set-up-anti-phishing-policies.md#spoof-settings)). Aby skonfigurować te ustawienia, zobacz [Konfigurowanie zasad ochrony przed wyłudzaniem informacji w ramach EOP](configure-anti-phishing-policies-eop.md).

Ustawienia fałszowania są ze sobą powiązane, ale ustawienie **Pokaż pierwszy kontakt porada dotycząca bezpieczeństwa** nie ma zależności od ustawień fałszowania.

|Nazwa funkcji zabezpieczeń|Domyślne|Standard|Ścisłe|Komentowanie|
|---|:---:|:---:|:---:|---|
|**Ochrona & progu wyłudzania informacji**|||||
|**Włączanie analizy fałszowania** <br/><br/> _EnableSpoofIntelligence_|Wybrane <br/><br/> `$true`|Wybrane <br/><br/> `$true`|Wybrane <br/><br/> `$true`||
|**Działania**|||||
|**Jeśli komunikat zostanie wykryty jako sfałszowany** <br/><br/> _AuthenticationFailAction_|**Przenoszenie wiadomości do folderów wiadomości-śmieci adresatów** <br/><br/> `MoveToJmf`|**Przenoszenie wiadomości do folderów wiadomości-śmieci adresatów** <br/><br/> `MoveToJmf`|**Kwarantanna komunikatu** <br/><br/> `Quarantine`|To ustawienie dotyczy sfałszowanych nadawców, którzy zostali automatycznie zablokowani, jak pokazano w szczegółowych [informacjach dotyczących fałszowania analizy](learn-about-spoof-intelligence.md) lub ręcznie zablokowanych na [liście dozwolonych/zablokowanych dzierżaw](tenant-allow-block-list.md). <br/><br/> Jeśli **wybierzesz pozycję Kwarantanna komunikatu**, pole **Zastosuj zasady kwarantanny** jest dostępne, aby wybrać zasady kwarantanny, które definiują, co użytkownicy mogą robić dla komunikatów, które są poddane kwarantannie jako fałszowanie. Podczas tworzenia nowych zasad ochrony przed wyłudzaniem informacji pusta wartość oznacza, że domyślne zasady kwarantanny są używane do definiowania historycznych możliwości komunikatów, które zostały poddane kwarantannie jako fałszowanie (DefaultFullAccessPolicy bez powiadomień kwarantanny). <br/><br/> Standardowe i ścisłe wstępnie ustawione zasady zabezpieczeń używają domyślnych zasad kwarantanny (DefaultFullAccessPolicy bez powiadomień o kwarantannie) zgodnie z opisem w tabeli [tutaj](quarantine-policies.md#step-2-assign-a-quarantine-policy-to-supported-features). <br/><br/> Administratorzy mogą tworzyć i wybierać niestandardowe zasady kwarantanny, które definiują bardziej restrykcyjne lub mniej restrykcyjne możliwości dla użytkowników w domyślnych lub niestandardowych zasadach ochrony przed wyłudzaniem informacji. Aby uzyskać więcej informacji, zobacz [Zasady kwarantanny](quarantine-policies.md).|
|**Pokaż pierwszy kontakt porada dotycząca bezpieczeństwa** <br/><br/> _EnableFirstContactSafetyTips_|Nie zaznaczono <br/><br/> `$false`|Nie zaznaczono <br/><br/> `$false`|Nie zaznaczono <br/><br/> `$false`|Aby uzyskać więcej informacji, zobacz [Pierwszy kontakt porada dotycząca bezpieczeństwa](set-up-anti-phishing-policies.md#first-contact-safety-tip).|
|**Pokaż (?) dla nieuwierzytelnionych nadawców na potrzeby fałszowania** <br/><br/> _EnableUnauthenticatedSender_|Wybrane <br/><br/> `$true`|Wybrane <br/><br/> `$true`|Wybrane <br/><br/> `$true`|Dodaje znak zapytania (?) do zdjęcia nadawcy w Outlook dla niezidentyfikowanych sfałszowanych nadawców. Aby uzyskać więcej informacji, zobacz [Nieuwierzytelnione wskaźniki nadawcy](set-up-anti-phishing-policies.md#unauthenticated-sender-indicators).|
|**Pokaż tag "via"** <br/><br/> _EnableViaTag_|Wybrane <br/><br/> `$true`|Wybrane <br/><br/> `$true`|Wybrane <br/><br/> `$true`|Dodaje tag via (chris@contoso.com za pośrednictwem fabrikam.com) do adresu Od, jeśli różni się on od domeny w podpisie DKIM lub **adresIE MAIL FROM** . <br/><br/> Aby uzyskać więcej informacji, zobacz [Nieuwierzytelnione wskaźniki nadawcy](set-up-anti-phishing-policies.md#unauthenticated-sender-indicators).|

## <a name="microsoft-defender-for-office-365-security"></a>zabezpieczenia Ochrona usługi Office 365 w usłudze Microsoft Defender

Dodatkowe korzyści związane z zabezpieczeniami są dostępne w ramach subskrypcji Ochrona usługi Office 365 w usłudze Microsoft Defender. Najnowsze wiadomości i informacje można znaleźć w temacie [Co nowego w Ochrona usługi Office 365 w usłudze Defender](whats-new-in-defender-for-office-365.md).

> [!IMPORTANT]
>
> - Domyślne zasady ochrony przed wyłudzaniem informacji w Ochrona usługi Office 365 w usłudze Microsoft Defender zapewniają [ochronę przed fałszowaniem](set-up-anti-phishing-policies.md#spoof-settings) i analizę skrzynek pocztowych dla wszystkich adresatów. Jednak inne dostępne funkcje [ochrony przed personifikacją](#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365) i [ustawienia zaawansowane](#advanced-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365) nie są skonfigurowane ani włączone w zasadach domyślnych. Aby włączyć wszystkie funkcje ochrony, zmodyfikuj domyślne zasady ochrony przed wyłudzaniem informacji lub utwórz dodatkowe zasady ochrony przed wyłudzaniem informacji.
>
> - Mimo że nie ma domyślnych zasad Sejf Załączniki ani Sejf Linki, **zasady zabezpieczeń wbudowanej ochrony** zapewniają ochronę Sejf Załączniki i Sejf Linki dla wszystkich adresatów (użytkowników, którzy nie są zdefiniowani w niestandardowych zasadach załączników Sejf lub zasadach łączy Sejf). Aby uzyskać więcej informacji, zobacz [Preset security policies in EOP and Ochrona usługi Office 365 w usłudze Microsoft Defender (Ustawienia wstępne zasad zabezpieczeń w usłudze EOP i Ochrona usługi Office 365 w usłudze Microsoft Defender](preset-security-policies.md)).
>
> - [Sejf Załączniki do ochrony SharePoint, OneDrive i](mdo-for-spo-odb-and-teams.md) Microsoft Teams oraz ochrony [dokumentów Sejf](safe-docs.md) nie mają zależności od zasad łączy Sejf.

Jeśli Twoja subskrypcja obejmuje Ochrona usługi Office 365 w usłudze Microsoft Defender lub jeśli zakupiono Ochrona usługi Office 365 w usłudze Defender jako dodatek, ustaw następujące konfiguracje standardowe lub ścisłe.

### <a name="anti-phishing-policy-settings-in-microsoft-defender-for-office-365"></a>Ustawienia zasad ochrony przed wyłudzaniem informacji w Ochrona usługi Office 365 w usłudze Microsoft Defender

Klienci EOP uzyskują podstawową ochronę przed wyłudzaniem informacji zgodnie z wcześniejszym opisem, ale Ochrona usługi Office 365 w usłudze Defender zawiera więcej funkcji i kontroli, aby pomóc w zapobieganiu atakom, wykrywaniu i korygowaniu ich. Aby utworzyć i skonfigurować te zasady, zobacz [Konfigurowanie zasad ochrony przed wyłudzaniem informacji w Ochrona usługi Office 365 w usłudze Defender](configure-mdo-anti-phishing-policies.md).

#### <a name="advanced-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365"></a>Zaawansowane ustawienia zasad ochrony przed wyłudzaniem informacji w Ochrona usługi Office 365 w usłudze Microsoft Defender

Aby uzyskać więcej informacji na temat tego ustawienia, zobacz [Zaawansowane progi wyłudzania informacji w zasadach ochrony przed wyłudzaniem informacji w Ochrona usługi Office 365 w usłudze Microsoft Defender](set-up-anti-phishing-policies.md#advanced-phishing-thresholds-in-anti-phishing-policies-in-microsoft-defender-for-office-365). Aby skonfigurować to ustawienie, zobacz [Konfigurowanie zasad ochrony przed wyłudzaniem informacji w Ochrona usługi Office 365 w usłudze Defender](configure-mdo-anti-phishing-policies.md).

|Nazwa funkcji zabezpieczeń|Domyślne|Standard|Ścisłe|Komentowanie|
|---|:---:|:---:|:---:|---|
|**Próg wiadomości e-mail wyłud** <br/><br/> _PhishThresholdLevel_|**1 — Standardowa** <br/><br/> `1`|**2 — Agresywne** <br/><br/> `2`|**3 — Bardziej agresywne** <br/><br/> `3`||

#### <a name="impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365"></a>Ustawienia personifikacji w zasadach ochrony przed wyłudzaniem informacji w Ochrona usługi Office 365 w usłudze Microsoft Defender

Aby uzyskać więcej informacji na temat tych ustawień, zobacz [Temat Impersonation settings in anti-phishing policies in Ochrona usługi Office 365 w usłudze Microsoft Defender (Ustawienia personifikacji w zasadach ochrony przed wyłudzaniem informacji w Ochrona usługi Office 365 w usłudze Microsoft Defender](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)). Aby skonfigurować te ustawienia, zobacz [Konfigurowanie zasad ochrony przed wyłudzaniem informacji w Ochrona usługi Office 365 w usłudze Defender](configure-mdo-anti-phishing-policies.md).

|Nazwa funkcji zabezpieczeń|Domyślne|Standard|Ścisłe|Komentowanie|
|---|:---:|:---:|:---:|---|
|**Ochrona & progu wyłudzania informacji**|||||
|**Umożliwianie użytkownikom ochrony** (ochrona użytkowników personifikowanych) <br/><br/> _EnableTargetedUserProtection_ <br/><br/> _TargetedUsersToProtect_|Nie zaznaczono <br/><br/> `$false` <br/><br/> brak|Wybrane <br/><br/> `$true` <br/><br/> \<list of users\>|Wybrane <br/><br/> `$true` <br/><br/> \<list of users\>|Zalecamy dodanie użytkowników (nadawców komunikatów) do kluczowych ról. Wewnętrznie chronionymi nadawcami mogą być Dyrektor Generalny, Dyrektor Finansowy i inni starsi liderzy. Zewnętrznie chronieni nadawcy mogą obejmować członków rady lub zarząd.|
|**Włączanie ochrony domen** (personifikowana ochrona domeny)|Nie zaznaczono|Wybrane|Wybrane||
|**Uwzględnij domeny, których jestem właścicielem** <br/><br/> _EnableOrganizationDomainsProtection_|Wył. <br/><br/> `$false`|Wybrane <br/><br/> `$true`|Wybrane <br/><br/> `$true`||
|**Dołączanie domen niestandardowych** <br/><br/> _EnableTargetedDomainsProtection_ <br/><br/> _TargetedDomainsToProtect_|Wył. <br/><br/> `$false` <br/><br/> brak|Wybrane <br/><br/> `$true` <br/><br/> \<list of domains\>|Wybrane <br/><br/> `$true` <br/><br/> \<list of domains\>|Zalecamy dodanie domen (domen nadawcy), których nie jesteś właścicielem, ale często wchodzisz w interakcje.|
|**Dodawanie zaufanych nadawców i domen** <br/><br/> _Wykluczeni nadawcy_ <br/><br/> _Wykluczonedomeny_|Brak|Brak|Brak|W zależności od organizacji zalecamy dodanie nadawców lub domen, które są niepoprawnie identyfikowane jako próby personifikacji.|
|**Włączanie analizy skrzynki pocztowej** <br/><br/> _EnableMailboxIntelligence_|Wybrane <br/><br/> `$true`|Wybrane <br/><br/> `$true`|Wybrane <br/><br/> `$true`||
|**Włączanie analizy w celu ochrony przed personifikacją** <br/><br/> _EnableMailboxIntelligenceProtection_|Wył. <br/><br/> `$false`|Wybrane <br/><br/> `$true`|Wybrane <br/><br/> `$true`|To ustawienie umożliwia określoną akcję wykrywania personifikacji za pomocą analizy skrzynki pocztowej.|
|**Działania**||||Wszędzie tam, gdzie **wybierzesz pozycję Kwarantanna komunikatu**, dostępne jest pole **Wyboru zasad kwarantanny** . Zasady kwarantanny definiują, co użytkownicy mogą robić w przypadku komunikatów poddanych kwarantannie. <br/><br/> Standardowe i ścisłe wstępnie ustawione zasady zabezpieczeń używają domyślnych zasad kwarantanny (DefaultFullAccessPolicy bez powiadomień o kwarantannie) zgodnie z opisem w tabeli [tutaj](quarantine-policies.md#step-2-assign-a-quarantine-policy-to-supported-features). <br/><br/> Podczas tworzenia nowych zasad ochrony przed wyłudzaniem informacji pusta wartość oznacza, że domyślne zasady kwarantanny są używane do definiowania historycznych możliwości komunikatów, które zostały poddane kwarantannie przez ten werdykt (DefaultFullAccessPolicy dla wszystkich typów wykrywania personifikacji). <br/><br/> Administratorzy mogą tworzyć i wybierać niestandardowe zasady kwarantanny, które definiują mniej restrykcyjne lub bardziej restrykcyjne możliwości dla użytkowników w domyślnych lub niestandardowych zasadach ochrony przed wyłudzaniem informacji. Aby uzyskać więcej informacji, zobacz [Zasady kwarantanny](quarantine-policies.md).|
|**Jeśli komunikat zostanie wykryty jako personifikowany użytkownik** <br/><br/> _TargetedUserProtectionAction_|**Nie stosuj żadnej akcji** <br/><br/> `NoAction`|**Kwarantanna komunikatu** <br/><br/> `Quarantine`|**Kwarantanna komunikatu** <br/><br/> `Quarantine`|Pamiętaj, że wstępnie ustawione zasady zabezpieczeń nie umożliwiają określania użytkowników do ochrony, dlatego to ustawienie nie działa w przypadku wstępnie ustawionych zasad zabezpieczeń.|
|**Jeśli komunikat zostanie wykryty jako domena personifikowana** <br/><br/> _TargetedDomainProtectionAction_|**Nie stosuj żadnej akcji** <br/><br/> `NoAction`|**Kwarantanna komunikatu** <br/><br/> `Quarantine`|**Kwarantanna komunikatu** <br/><br/> `Quarantine`|Pamiętaj, że wstępnie ustawione zasady zabezpieczeń nie umożliwiają określania domen niestandardowych do ochrony, więc to ustawienie ma wpływ tylko na domeny należące do Ciebie, a nie domeny niestandardowe.|
|**Jeśli analiza skrzynki pocztowej wykryje i personifikuje użytkownika** <br/><br/> _Skrzynka pocztowaIntelligenceProtectionAction_|**Nie stosuj żadnej akcji** <br/><br/> `NoAction`|**Przenoszenie wiadomości do folderów wiadomości-śmieci adresatów** <br/><br/> `MoveToJmf`|**Kwarantanna komunikatu** <br/><br/> `Quarantine`||
|**Pokaż porada dotycząca bezpieczeństwa personifikacji użytkownika** <br/><br/> _EnableSimilarUsersSafetyTips_|Wył. <br/><br/> `$false`|Wybrane <br/><br/> `$true`|Wybrane <br/><br/> `$true`||
|**Pokaż porada dotycząca bezpieczeństwa personifikacji domeny** <br/><br/> _EnableSimilarDomainsSafetyTips_|Wył. <br/><br/> `$false`|Wybrane <br/><br/> `$true`|Wybrane <br/><br/> `$true`||
|**Pokaż nietypowe znaki personifikacji użytkownika porada dotycząca bezpieczeństwa** <br/><br/> _EnableUnusualCharactersSafetyTips_|Wył. <br/><br/> `$false`|Wybrane <br/><br/> `$true`|Wybrane <br/><br/> `$true`||

#### <a name="eop-anti-phishing-policy-settings-in-microsoft-defender-for-office-365"></a>Ustawienia zasad ochrony przed wyłudzaniem informacji na platformie EOP w Ochrona usługi Office 365 w usłudze Microsoft Defender

Są to te same ustawienia, które są dostępne w [ustawieniach zasad ochrony przed spamem w ramach EOP](#eop-anti-spam-policy-settings).

### <a name="safe-attachments-settings"></a>ustawienia załączników Sejf

Sejf Załączniki w Ochrona usługi Office 365 w usłudze Microsoft Defender zawierają ustawienia globalne, które nie mają relacji z zasadami załączników Sejf, oraz ustawienia specyficzne dla poszczególnych zasad łączy Sejf. Aby uzyskać więcej informacji, zobacz [Sejf Załączniki w Ochrona usługi Office 365 w usłudze Defender](safe-attachments.md).

Mimo że nie ma domyślnych zasad Sejf Załączniki, wbudowane zasady zabezpieczeń **wstępnie ustawione ochrony** zapewniają ochronę Sejf załączników wszystkim adresatom (użytkownikom, którzy nie są zdefiniowani w niestandardowych zasadach załączników Sejf). Aby uzyskać więcej informacji, zobacz [Preset security policies in EOP and Ochrona usługi Office 365 w usłudze Microsoft Defender (Ustawienia wstępne zasad zabezpieczeń w usłudze EOP i Ochrona usługi Office 365 w usłudze Microsoft Defender](preset-security-policies.md)).

#### <a name="global-settings-for-safe-attachments"></a>Ustawienia globalne dla załączników Sejf

> [!NOTE]
> Ustawienia globalne dla załączników Sejf są ustawiane przez wstępnie ustawione zasady zabezpieczeń **wbudowanej ochrony**, ale nie przez **standardowe lub** **ścisłe** zasady zabezpieczeń. Tak czy inaczej, administratorzy mogą modyfikować te globalne ustawienia Sejf Załączniki w dowolnym momencie.
>
> Kolumna **Domyślne** zawiera wartości przed istnieniem **zasad zabezpieczeń wstępnie ustawionych wbudowanej ochrony** . Kolumna **Wbudowana ochrona** pokazuje wartości, które są ustawiane przez **wbudowane** zasady zabezpieczeń wstępnie ustawione, które są również naszymi zalecanymi wartościami.

Aby skonfigurować te ustawienia, zobacz [Włączanie załączników Sejf dla SharePoint, OneDrive oraz Microsoft Teams](turn-on-mdo-for-spo-odb-and-teams.md) i [Sejf Dokumenty w Microsoft 365 E5](safe-docs.md).

W programie PowerShell używasz polecenia cmdlet [Set-AtpPolicyForO365](/powershell/module/exchange/set-atppolicyforo365) dla tych ustawień.

|Nazwa funkcji zabezpieczeń|Domyślne|Wbudowana ochrona|Komentowanie|
|---|:---:|:---:|---|
|**Włącz Ochrona usługi Office 365 w usłudze Defender dla SharePoint, OneDrive i Microsoft Teams** <br/><br/> _EnableATPForSPOTeamsODB_|Wył. <br/><br/> `$false`|Na <br/><br/> `$true`|Aby uniemożliwić użytkownikom pobieranie złośliwych plików, zobacz [Używanie programu PowerShell SharePoint Online, aby uniemożliwić użytkownikom pobieranie złośliwych plików](turn-on-mdo-for-spo-odb-and-teams.md#step-2-recommended-use-sharepoint-online-powershell-to-prevent-users-from-downloading-malicious-files).|
|**Włączanie Sejf dokumentów dla klientów Office** <br/><br/> _EnableSafeDocs_|Wył. <br/><br/> `$false`|Na <br/><br/> `$true`|Ta funkcja jest dostępna i zrozumiała tylko w przypadku licencji, które nie są uwzględnione w Ochrona usługi Office 365 w usłudze Defender (na przykład Microsoft 365 E5 lub Zabezpieczenia platformy Microsoft 365 E5). Aby uzyskać więcej informacji, zobacz [Sejf Documents in Microsoft 365 E5 (Dokumenty Sejf w Microsoft 365 E5](safe-docs.md)).|
|**Zezwalaj użytkownikom na klikanie widoku chronionego, nawet jeśli Sejf Documents zidentyfikowało plik jako złośliwy** <br/><br/> _AllowSafeDocsOpen_|Wył. <br/><br/> `$false`|Wył. <br/><br/> `$false`|To ustawienie jest związane z dokumentami Sejf.|

#### <a name="safe-attachments-policy-settings"></a>ustawienia zasad załączników Sejf

Aby skonfigurować te ustawienia, zobacz [Konfigurowanie zasad załączników Sejf w Ochrona usługi Office 365 w usłudze Defender](set-up-safe-attachments-policies.md).

W programie PowerShell dla tych ustawień są używane polecenia cmdlet [New-SafeAttachmentPolicy](/powershell/module/exchange/new-safeattachmentpolicy) i [Set-SafeAttachmentPolicy](/powershell/module/exchange/set-safelinkspolicy) .

> [!NOTE]
> Zgodnie z wcześniejszym opisem nie ma domyślnych zasad Sejf Załączniki, ale Sejf ochrona załączników jest przypisywana do wszystkich adresatów przez [wstępnie ustawione zasady zabezpieczeń **wbudowanej ochrony**](preset-security-policies.md).
>
> **Kolumna Domyślna w kolumnie niestandardowej** odwołuje się do wartości domyślnych w nowych zasadach Sejf Załączniki, które tworzysz. Pozostałe kolumny wskazują (o ile nie zaznaczono inaczej) wartości skonfigurowane w odpowiednich wstępnie ustawionych zasadach zabezpieczeń.

|Nazwa funkcji zabezpieczeń|Wartość domyślna w obszarze niestandardowym|Wbudowana ochrona|Standard|Ścisłe|Komentowanie|
|---|:---:|:---:|:---:|:---:|---|
|**Sejf Załączniki — nieznana odpowiedź na złośliwe oprogramowanie** <br/><br/> _Włączanie_ i _działanie_|**Wył.** <br/><br/> `-Enable $false` I `-Action Block`|**Blokuj** <br/><br/> `-Enable $true` I `-Action Block`|**Blokuj** <br/><br/> `-Enable $true` I `-Action Block`|**Blokuj** <br/><br/> `-Enable $true` I `-Action Block`|Gdy parametr _Enable_ jest $false, wartość parametru _Action_ nie ma znaczenia.|
|**Zasady kwarantanny** (_QuarantineTag_)|AdminOnlyAccessPolicy|AdminOnlyAccessPolicy|AdminOnlyAccessPolicy|AdminOnlyAccessPolicy| <br/><br/> Standardowe i ścisłe wstępnie ustawione zasady zabezpieczeń używają domyślnych zasad kwarantanny (AdminOnlyAccessPolicy bez powiadomień o kwarantannie) zgodnie z opisem w tabeli [tutaj](quarantine-policies.md#step-2-assign-a-quarantine-policy-to-supported-features). <br/><br/> Podczas tworzenia nowych zasad Sejf Załączniki wartość pusta oznacza, że domyślne zasady kwarantanny są używane do definiowania historycznych możliwości komunikatów, które zostały poddane kwarantannie przez załączniki Sejf (AdminOnlyAccessPolicy bez powiadomień kwarantanny). <br/><br/> Administratorzy mogą tworzyć i wybierać niestandardowe zasady kwarantanny, które definiują więcej możliwości dla użytkowników. Aby uzyskać więcej informacji, zobacz [Zasady kwarantanny](quarantine-policies.md).|
|**Przekierowanie załącznika z wykrytymi załącznikami** : **Włącz przekierowanie** <br/><br/> _Przekierowanie_ <br/><br/> _RedirectAddress_|Nie wybrano i nie określono adresu e-mail. <br/><br/> `-Redirect $false` <br/><br/> _RedirectAddress_ jest pusty (`$null`)|Nie wybrano i nie określono adresu e-mail. <br/><br/> `-Redirect $false` <br/><br/> _RedirectAddress_ jest pusty (`$null`)|Wybrano i określ adres e-mail. <br/><br/> `$true` <br/><br/> adres e-mail|Wybrano i określ adres e-mail. <br/><br/> `$true` <br/><br/> adres e-mail|Przekieruj komunikaty do administratora zabezpieczeń w celu sprawdzenia. <br/><br/> **Uwaga**: to ustawienie nie jest skonfigurowane w zasadach zabezpieczeń wstępnie ustawionych w **warstwie Standardowa**, **Ścisła** ani **Wbudowana ochrona** . Wartości **Standardowe** i **Ścisłe** wskazują **zalecane** wartości w nowych zasadach Sejf Załączniki, które tworzysz.|
|**Zastosuj odpowiedź wykrywania załączników Sejf, jeśli skanowanie nie może zakończyć się (przekroczenie limitu czasu lub błędy)** <br/><br/> _ActionOnError_|Wybrane <br/><br/> `$true`|Wybrane <br/><br/> `$true`|Wybrane <br/><br/> `$true`|Wybrane <br/><br/> `$true`||

### <a name="safe-links-settings"></a>ustawienia linków Sejf

Sejf Linki w Ochrona usługi Office 365 w usłudze Defender zawierają ustawienia globalne, które mają zastosowanie do wszystkich użytkowników, którzy są uwzględniane w aktywnych zasadach Sejf Łącza, oraz ustawienia specyficzne dla poszczególnych zasad Sejf Łącza. Aby uzyskać więcej informacji, zobacz [linki Sejf w Ochrona usługi Office 365 w usłudze Defender](safe-links.md).

Mimo że nie ma domyślnych zasad Sejf Łącza, wstępnie ustawione zasady zabezpieczeń **wbudowanej ochrony** zapewniają ochronę Sejf Łącza wszystkim adresatom (użytkownikom, którzy nie są zdefiniowani w niestandardowych zasadach Sejf Łącza). Aby uzyskać więcej informacji, zobacz [Preset security policies in EOP and Ochrona usługi Office 365 w usłudze Microsoft Defender (Ustawienia wstępne zasad zabezpieczeń w usłudze EOP i Ochrona usługi Office 365 w usłudze Microsoft Defender](preset-security-policies.md)).

#### <a name="global-settings-for-safe-links"></a>Ustawienia globalne linków Sejf

> [!NOTE]
> Ustawienia globalne dla linków Sejf są ustawiane przez wstępnie ustawione zasady zabezpieczeń **wbudowanej ochrony**, ale nie przez **standardowe lub** **ścisłe** wstępnie ustawione zasady zabezpieczeń. Tak czy inaczej, administratorzy mogą modyfikować te globalne ustawienia linków Sejf w dowolnym momencie.
>
> Kolumna **Domyślne** zawiera wartości przed istnieniem **zasad zabezpieczeń wstępnie ustawionych wbudowanej ochrony** . Kolumna **Wbudowana ochrona** pokazuje wartości, które są ustawiane przez **wbudowane** zasady zabezpieczeń wstępnie ustawione, które są również naszymi zalecanymi wartościami.

Aby skonfigurować te ustawienia, zobacz [Konfigurowanie ustawień globalnych dla linków Sejf w Ochrona usługi Office 365 w usłudze Defender](configure-global-settings-for-safe-links.md).

W programie PowerShell używasz polecenia cmdlet [Set-AtpPolicyForO365](/powershell/module/exchange/set-atppolicyforo365) dla tych ustawień.

|Nazwa funkcji zabezpieczeń|Domyślne|Wbudowana ochrona|Komentowanie|
|---|:---:|:---:|---|
|**Blokuj następujące adresy URL** <br/><br/> _ExcludedUrls_|Puste <br/><br/> `$null`|Puste <br/><br/> `$null`|Nie mamy żadnych konkretnych zaleceń dotyczących tego ustawienia. <br/><br/> Aby uzyskać więcej informacji, zobacz [listę "Blokuj następujące adresy URL" dla linków Sejf](safe-links.md#block-the-following-urls-list-for-safe-links).
|**Używanie linków Sejf w aplikacjach Office 365** <br/><br/> _EnableSafeLinksForO365Clients_|Na <br/><br/> `$true`|Na <br/><br/> `$true`|Użyj linków Sejf w obsługiwanych aplikacjach Office 365 desktop i mobile (iOS i Android). Aby uzyskać więcej informacji, zobacz [ustawienia linków Sejf dla aplikacji Office 365](safe-links.md#safe-links-settings-for-office-365-apps).|
|**Nie śledź, gdy użytkownicy klikają linki chronione w aplikacjach Office 365** <br/><br/> _TrackClicks_|Na <br/><br/> `$false`|Wył. <br/><br/> `$true`|Wyłączenie tego ustawienia (ustawienie _pozycji TrackClicks_ na `$true`) śledzi kliknięcia użytkowników w obsługiwanych aplikacjach Office 365.|
|**Nie zezwalaj użytkownikom na klikanie oryginalnego adresu URL w aplikacjach Office 365** <br/><br/> _AllowClickThrough_|Na <br/><br/> `$false`|Na <br/><br/> `$false`|Włączenie tego ustawienia (ustawienie _allowClickThrough_ `$false`na ) uniemożliwia kliknięcie oryginalnego adresu URL w obsługiwanych aplikacjach Office 365.|

#### <a name="safe-links-policy-settings"></a>ustawienia zasad linków Sejf

Aby skonfigurować te ustawienia, zobacz [Konfigurowanie zasad linków Sejf w Ochrona usługi Office 365 w usłudze Microsoft Defender](set-up-safe-links-policies.md).

W programie PowerShell dla tych ustawień są używane polecenia cmdlet [New-SafeLinksPolicy](/powershell/module/exchange/new-safelinkspolicy) i [Set-SafeLinksPolicy](/powershell/module/exchange/set-safelinkspolicy) .

> [!NOTE]
> Zgodnie z wcześniejszym opisem nie ma domyślnych zasad Sejf Łącza, ale ochrona Sejf Łącza jest przypisywana do wszystkich adresatów przez [wstępnie ustawione zasady zabezpieczeń **wbudowanej ochrony**](preset-security-policies.md).
>
> **Kolumna Domyślne w kolumnie niestandardowej** odnosi się do wartości domyślnych w nowych zasadach Sejf Łącza, które tworzysz. Pozostałe kolumny wskazują (o ile nie zaznaczono inaczej) wartości skonfigurowane w odpowiednich wstępnie ustawionych zasadach zabezpieczeń.

|Nazwa funkcji zabezpieczeń|Wartość domyślna w obszarze niestandardowym|Wbudowana ochrona|Standard|Ścisłe|Komentowanie|
|---|:---:|:---:|:---:|:---:|---|
|**Adres URL & kliknij ustawienia ochrony**||||||
|**Akcja dotycząca potencjalnie złośliwych adresów URL w wiadomościach e-mail**||||||
|**Włączone: Sejf Linki sprawdzają listę znanych, złośliwych linków, gdy użytkownicy klikają linki w wiadomości e-mail** <br/><br/> _EnableSafeLinksForEmail_|Nie zaznaczono <br/><br/> `$false`|Wybrane <br/><br/> `$true`|Wybrane <br/><br/> `$true`|Wybrane <br/><br/> `$true`||
|**Stosowanie linków Sejf do wiadomości e-mail wysyłanych w organizacji** <br/><br/> _EnableForInternalSenders_|Nie zaznaczono <br/><br/> `$false`|Wybrane <br/><br/> `$true`|Wybrane <br/><br/> `$true`|Wybrane <br/><br/> `$true`||
|**Stosowanie skanowania adresów URL w czasie rzeczywistym w poszukiwaniu podejrzanych linków i linków wskazujących pliki** <br/><br/> _ScanUrls_|Nie zaznaczono <br/><br/> `$false`|Wybrane <br/><br/> `$true`|Wybrane <br/><br/> `$true`|Wybrane <br/><br/> `$true`||
|**Przed dostarczeniem komunikatu poczekaj na ukończenie skanowania adresu URL** <br/><br/> _DeliverMessageAfterScan_|Nie zaznaczono <br/><br/> `$false`|Wybrane <br/><br/> `$true`|Wybrane <br/><br/> `$true`|Wybrane <br/><br/> `$true`||
|**Nie przepisuj ponownie adresów URL, sprawdzaj tylko za pośrednictwem interfejsu API linków Sejf** <br/><br/> _DisableURLRewrite_|Nie zaznaczono <br/><br/> `$false`|Wybrane <br/><br/> `$true`|Nie zaznaczono <br/><br/> `$false`|Nie zaznaczono <br/><br/> `$false`||
|**Nie należy ponownie pisać następujących adresów URL w wiadomości e-mail** <br/><br/> _DoNotRewriteUrls_|Nie zaznaczono <br/><br/> Puste|Nie zaznaczono <br/><br/> Puste|Nie zaznaczono <br/><br/> Puste|Nie zaznaczono <br/><br/> Puste|Nie mamy żadnych konkretnych zaleceń dotyczących tego ustawienia. Aby uzyskać więcej informacji, zobacz [artykuł "Nie przepisuj ponownie następujących adresów URL" list w zasadach linków Sejf](safe-links.md#do-not-rewrite-the-following-urls-lists-in-safe-links-policies).|
|**Akcja dla potencjalnie złośliwych adresów URL w Microsoft Teams**||||||
|**On: Sejf Links checks a list of known, malicious links when users click links in Microsoft Teams** <br/><br/> _EnableSafeLinksForTeams_|Nie zaznaczono <br/><br/> `$false`|Wybrane <br/><br/> `$true`|Wybrane <br/><br/> `$true`|Wybrane <br/><br/> `$true`||
|**Kliknij ustawienia ochrony**||||||
|**Śledzenie kliknięć użytkowników** <br/><br/> _TrackUserClicks_|Wybrane <br/><br/> `$true`|Wybrane <br/><br/> `$true`|Wybrane <br/><br/> `$true`|Wybrane <br/><br/> `$true`||
|**Zezwalaj użytkownikom na klikanie oryginalnego adresu URL** <br/><br/> _AllowClickThrough_|Wybrane <br/><br/> `$true`|Wybrane <br/><br/> `$true`|Nie zaznaczono <br/><br/> `$false`|Nie zaznaczono <br/><br/> `$false`|Wyłączenie tego ustawienia (ustawienie _opcji AllowClickThrough_ `$false`na ) uniemożliwia przejście do oryginalnego adresu URL.|
|**Wyświetlanie znakowania organizacji na stronach powiadomień i ostrzeżeń** <br/><br/> _EnableOrganizationBranding_|Nie zaznaczono <br/><br/> `$false`|Nie zaznaczono <br/><br/> `$false`|Nie zaznaczono <br/><br/> `$false`|Nie zaznaczono <br/><br/> `$false`|Nie mamy żadnych konkretnych zaleceń dotyczących tego ustawienia. <br/><br/> Przed włączeniem tego ustawienia należy postępować zgodnie z instrukcjami w [temacie Dostosowywanie motywu Microsoft 365 dla organizacji](../../admin/setup/customize-your-organization-theme.md) w celu przekazania logo firmy.|
|**Powiadomienie**||||||
|**Jak chcesz powiadomić użytkowników?**|**Użyj domyślnego tekstu powiadomienia**|**Użyj domyślnego tekstu powiadomienia**|**Użyj domyślnego tekstu powiadomienia**|**Użyj domyślnego tekstu powiadomienia**|Nie mamy żadnych konkretnych zaleceń dotyczących tego ustawienia. <br/><br/> Możesz wybrać pozycję **Użyj niestandardowego tekstu powiadomień** (_CustomNotificationText_), aby wprowadzić dostosowany tekst powiadomienia do użycia. Możesz również wybrać pozycję **Użyj Microsoft Translator do automatycznej lokalizacji** (_UseTranslatedNotificationText_), aby przetłumaczyć niestandardowy tekst powiadomienia na język użytkownika.

## <a name="related-articles"></a>Powiązane artykuły:

- Czy szukasz najlepszych rozwiązań dotyczących **reguł przepływu poczty Exchange (nazywanych również regułami transportu**)? Zobacz [Najlepsze rozwiązania dotyczące konfigurowania reguł przepływu poczty w Exchange Online](/exchange/security-and-compliance/mail-flow-rules/configuration-best-practices).

- Administratorzy i użytkownicy mogą przesyłać do firmy Microsoft wyniki fałszywie dodatnie (dobra wiadomość e-mail oznaczona jako zła) i fałszywie ujemne (niedozwolona wiadomość e-mail). Aby uzyskać więcej informacji, zobacz [Zgłaszanie komunikatów i plików do firmy Microsoft](report-junk-email-messages-to-microsoft.md).

- Skorzystaj z tych linków, aby uzyskać informacje na temat **konfigurowania** [usługi EOP](/exchange/standalone-eop/set-up-your-eop-service) i **konfigurowania** [Ochrona usługi Office 365 w usłudze Microsoft Defender](defender-for-office-365.md). Nie zapomnij o pomocnych kierunkach w [temacie "Ochrona przed zagrożeniami w Office 365](protect-against-threats.md)".

- **Punkty odniesienia zabezpieczeń dla Windows** można znaleźć tutaj: [Gdzie mogę uzyskać punkty odniesienia zabezpieczeń?](/windows/security/threat-protection/windows-security-baselines#where-can-i-get-the-security-baselines) dla opcji obiektu zasad grupy/lokalnego i [Użyj punktów odniesienia zabezpieczeń, aby skonfigurować urządzenia Windows w Intune](/intune/protect/security-baselines) pod kątem zabezpieczeń opartych na Intune. Na koniec porównanie punktów odniesienia zabezpieczeń Ochrona punktu końcowego w usłudze Microsoft Defender i Microsoft Intune jest dostępne w artykule [Porównanie Ochrona punktu końcowego w usłudze Microsoft Defender i Windows Intune punktów odniesienia zabezpieczeń](/windows/security/threat-protection/microsoft-defender-atp/configure-machines-security-baseline#compare-the-microsoft-defender-atp-and-the-windows-intune-security-baselines).
