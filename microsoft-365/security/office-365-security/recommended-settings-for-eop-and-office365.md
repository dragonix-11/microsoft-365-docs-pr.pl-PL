---
title: Zalecenia firmy Microsoft dotyczące usług EOP i Defender w Office 365 zabezpieczeń
keywords: Office 365 zalecenia dotyczące zabezpieczeń, struktury zasad dotyczących nadawców, raportowania i zgodności wiadomości opartych na domenie, zidentyfikowanej poczty DomainKeys, kroków, sposobu działania, planu bazowego zabezpieczeń, planu bazowego usługi EOP, linii bazowych programu Defender dla usługi Office 365, konfigurowania usługi Defender dla usługi Office 365, konfigurowania usługi EOP, konfigurowania usługi Defender dla usługi Office 365 , skonfiguruj usługę EOP, konfigurację zabezpieczeń
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
description: Jakie są najlepsze rozwiązania dotyczące usługi Exchange Online Protection (EOP) i programu Defender w zakresie Office 365 zabezpieczeń? Jakie są bieżące zalecenia dotyczące ochrony standardowej? Czego należy używać, aby być bardziej rygorystycznym? Jakie dodatkowe dodatki otrzymasz, jeśli korzystasz również z programu Defender dla Office 365?
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 66d221b422236c6818ebb146babc0cc90eab1206
ms.sourcegitcommit: f563b4229760fa099703296d1ad2c1f0264f1647
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/14/2022
ms.locfileid: "63015759"
---
# <a name="recommended-settings-for-eop-and-microsoft-defender-for-office-365-security"></a>Zalecane ustawienia usług EOP i Microsoft Defender w Office 365 zabezpieczeń

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender dla Office 365 plan 1 i plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

**Exchange Online Protection (EOP)** to podstawowa ochrona subskrypcji usługi Microsoft 365 i pomaga zapobiegać dotarciu złośliwych wiadomości e-mail do skrzynek pocztowych pracowników. W związku z tym, że każdego dnia pojawiają się nowe, bardziej zaawansowane ataki, często jest wymagana ulepszona ochrona. **Usługa Microsoft Defender Office 365** Plan 1 lub Plan 2 zawiera dodatkowe funkcje, które zapewniają administratorom więcej warstw zabezpieczeń, kontroli i badania.

Chociaż umożliwiamy administratorom zabezpieczeń dostosowywanie ich ustawień zabezpieczeń, zaleca się stosowanie dwóch poziomów zabezpieczeń w usługach EOP i Microsoft Defender Office 365: **Standardowy** i **Ścisłe**. Mimo że środowiska i potrzeby klientów różnią się, te poziomy filtrowania pomagają zapobiec dotarciu niechcianej poczty do skrzynki odbiorczej pracowników w większości przypadków.

Aby automatycznie zastosować ustawienia Standardowe lub Ścisłe do użytkowników, zobacz Wstępnie ustawione zasady zabezpieczeń w usługach [EOP i Microsoft Defender for Office 365](preset-security-policies.md).

W tym artykule opisano ustawienia domyślne, a także zalecane ustawienia standardowe i ścisłe w celu ochrony użytkowników. Tabele zawierają ustawienia w portalu programu Microsoft 365 Defender i programie PowerShell (Exchange Online Power Exchange Online Protection Shell lub autonomicznym programie PowerShell dla organizacji bez Exchange Online pocztowych).

> [!TIP]
> Zalecanych ustawień standardowych i ścisłych nie można zmienić w portalu Microsoft 365 Defender sieci. Aby zmienić zalecane wartości, takie **jak Włączanie ochrony** użytkownikom, należy użyć programu [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).
>
> Moduł Office 365 orCA (Advanced Threat Protection Recommended Configuration Analyzer) dla programu PowerShell może ułatwić Ci (administratorom) znalezienie bieżących wartości tych ustawień. Polecenie **cmdlet Get-ORCAReport** generuje w szczególności ocenę ustawień ochrony przed spamem, ochrony przed wyłudzaniem informacji i innymi ustawieniami ustawień wiadomości. Możesz pobrać moduł ORCA na stronie <https://www.powershellgallery.com/packages/ORCA/>.

## <a name="anti-spam-anti-malware-and-anti-phishing-protection-in-eop"></a>Ochrona przed spamem, złośliwym oprogramowaniem oraz ochrona przed wyłudzaniem informacji w uchcie EOP

Funkcje ochrony przed spamem, ochrony przed złośliwym oprogramowaniem i przed wyłudzaniem informacji to funkcje usługi EOP, które mogą być konfigurowane przez administratorów. Zalecamy następujące konfiguracje standardowe lub ścisłe.

### <a name="eop-anti-spam-policy-settings"></a>Ustawienia zasad ochrony przed spamem w utermie EOP

Aby utworzyć i skonfigurować zasady ochrony przed spamem, zobacz Konfigurowanie zasad ochrony [przed spamem w u usługi EOP](configure-your-spam-filter-policies.md).

<br>

****

|Nazwa funkcji zabezpieczeń|Domyślne|Standard|Ścisłe|Komentowanie|
|---|:---:|:---:|:---:|---|
|**Próg masowej poczty e-mail & właściwości spamu**|||||
|**Próg masowej poczty e-mail** <p> _BulkThreshold_|7|6|4|Aby uzyskać szczegółowe informacje, [zobacz Zbiorczy poziom skarg (BCL, Bulk complaint level) w UOP](bulk-complaint-level-values.md).|
|_MarkAsSpamBulkMail_|`On`|`On`|`On`|To ustawienie jest dostępne tylko w programie PowerShell.|
|**Zwiększanie ustawień wyników spamu**|Wyłączone|Wyłączone|Wyłączone|Wszystkie te ustawienia są częścią zaawansowanego filtru spamu (ASF). Aby uzyskać więcej informacji, zobacz sekcję Ustawienia [ochrony przed spamem](#asf-settings-in-anti-spam-policies) w sekcji dotyczącej zasad ochrony przed spamem w tym artykule.|
|**Ustawienia oznaczania jako spamu**|Wyłączone|Wyłączone|Wyłączone|Większość tych ustawień jest częścią asf. Aby uzyskać więcej informacji, zobacz sekcję Ustawienia [ochrony przed spamem](#asf-settings-in-anti-spam-policies) w sekcji dotyczącej zasad ochrony przed spamem w tym artykule.|
|**Zawiera określone języki** <p> _EnableLanguageBlockList_ <p> _LanguageBlockList_|**Wyłączone** <p> `$false` <p> Puste|**Wyłączone** <p> `$false` <p> Puste|**Wyłączone** <p> `$false` <p> Puste|Nie mamy konkretnych zaleceń dla tego ustawienia. Wiadomości można blokować w określonych językach w zależności od potrzeb biznesowych.|
|**Z tych krajów** <p> _EnableRegionBlockList_ <p> _Lista RegionBlockList_|**Wyłączone** <p> `$false` <p> Puste|**Wyłączone** <p> `$false` <p> Puste|**Wyłączone** <p> `$false` <p> Puste|Nie mamy konkretnych zaleceń dla tego ustawienia. Możesz blokować wiadomości z określonych krajów w zależności od potrzeb biznesowych.|
|**Tryb testowy** (_TestModeAction_)|**Brak**|**Brak**|**Brak**|To ustawienie jest częścią asf. Aby uzyskać więcej informacji, zobacz sekcję Ustawienia [ochrony przed spamem](#asf-settings-in-anti-spam-policies) w sekcji dotyczącej zasad ochrony przed spamem w tym artykule.|
|**Akcje**||||Gdziekolwiek wybierzesz pozycję **Poddaj wiadomość kwarantannie**, dostępne jest **pole Wybierz zasady kwarantanny** . Zasady kwarantanny określają, co użytkownicy mogą robić w przypadku wiadomości poddanych kwarantannie. <p> Gdy tworzysz nowe zasady ochrony przed spamem, wartość pusta oznacza, że domyślne zasady kwarantanny są używane do definiowania funkcji historycznych dla wiadomości poddanych kwarantannie przez ten określony werdykt (AdminOnlyAccessPolicy for **High confidence** phishing; DefaultFullAccessPolicy dla wszystkich innych). <p> Administratorzy mogą tworzyć i wybierać niestandardowe zasady kwarantanny definiujące bardziej restrykcyjne lub mniej restrykcyjne funkcje dla użytkowników. Aby uzyskać więcej informacji, zobacz [Zasady kwarantanny](quarantine-policies.md).|
|**Akcja wykrywania spamu** <p> _SpamAction_|**Przenoszenie wiadomości do folderu Wiadomości-śmieci** <p> `MoveToJmf`|**Przenoszenie wiadomości do folderu Wiadomości-śmieci** <p> `MoveToJmf`|**Poddaj wiadomość kwarantannie** <p> `Quarantine`||
|**Akcja wykrywania spamu o dużej** pewności <p> _HighConfidenceSpamAction_|**Poddaj wiadomość kwarantannie** <p> `MoveToJmf`|**Poddaj wiadomość kwarantannie** <p> `Quarantine`|**Poddaj wiadomość kwarantannie** <p> `Quarantine`||
|**Akcja wykrywania** wyłudzania informacji <p> _PhishSpamAction_|**Poddaj wiadomość kwarantannie** <p> `MoveToJmf`|**Poddaj wiadomość kwarantannie** <p> `Quarantine`|**Poddaj wiadomość kwarantannie** <p> `Quarantine`||
|**Akcja wykrywania wyłudzania informacji o wysokiej** pewności <p> _HighConfidencePhishAction_|**Poddaj wiadomość kwarantannie** <p> `Quarantine`|**Poddaj wiadomość kwarantannie** <p> `Quarantine`|**Poddaj wiadomość kwarantannie** <p> `Quarantine`||
|**Akcja wykrywania** zbiorczego <p> _BulkSpamAction_|**Przenoszenie wiadomości do folderu Wiadomości-śmieci** <p> `MoveToJmf`|**Przenoszenie wiadomości do folderu Wiadomości-śmieci** <p> `MoveToJmf`|**Poddaj wiadomość kwarantannie** <p> `Quarantine`||
|**Zachowywanie spamu w kwarantannie przez tę wiele dni** <p> _QuarantineRetentionPeriod_|15 dni<sup>\*</sup>|30 dni|30 dni|<sup>\*</sup> Wartość domyślna domyślnych zasad ochrony przed spamem oraz nowych zasad ochrony przed spamem tworzyć w programie PowerShell wynosi 15 dni. Wartość domyślna nowych zasad ochrony przed spamem tworzyć w portalu ochrony przed Microsoft 365 Defender spamem wynosi 30 dni. <p> Ta wartość wpływa również na wiadomości poddane kwarantannie przez zasady ochrony przed wyłudzaniem informacji. Aby uzyskać więcej informacji, zobacz [Poddaj wiadomościom w kwarantannie usługi EOP](quarantine-email-messages.md).|
|**Włączanie porad dotyczących bezpieczeństwa przed spamem** <p> _InlineSafetyTipsEnabled_|Zaznaczone <p> `$true`|Zaznaczone <p> `$true`|Zaznaczone <p> `$true`||
|Włączanie automatycznego przeczyszczania (ZAP) bez godzin dla wiadomości wyłudzających informacje <p> _PhishZapEnabled_|Zaznaczone <p> `$true`|Zaznaczone <p> `$true`|Zaznaczone <p> `$true`||
|Włączanie zap dla wiadomości-śmieci <p> _SpamZapEnabled_|Zaznaczone <p> `$true`|Zaznaczone <p> `$true`|Zaznaczone <p> `$true`||
|**Zezwalaj & listy zablokowanych**|||||
|Z dozwolonymi nadawcami <p> _AllowedSenders_|Brak|Brak|Brak||
|Dozwolone domeny nadawców <p> _AllowedSenderDomains_|Brak|Brak|Brak|Dodawanie domen do listy dozwolonych nadawców to bardzo zły pomysł. Atakujący będą mogli wysyłać Ci wiadomości e-mail, które w przeciwnym razie zostaną odfiltrowane. <p> Użyj szczegółowych [](learn-about-spoof-intelligence.md) informacji o analizie fałszowania i listy zablokowanych[/](tenant-allow-block-list.md)zezwalających na dostęp do dzierżawy, aby przejrzeć wszystkich nadawców, którzy podszywają się pod adresy e-mail nadawców w domenach poczty e-mail Twojej organizacji lub podszywają się pod adresy e-mail nadawców w domenach zewnętrznych.|
|Zablokowani nadawcy <p> _BlockedSenders_|Brak|Brak|Brak||
|Zablokowane domeny nadawcy <p> _BlockedSenderDomains_|Brak|Brak|Brak||
|

#### <a name="asf-settings-in-anti-spam-policies"></a>Ustawienia asf w zasadach ochrony przed spamem

W tabeli w tej sekcji opisano ustawienia zaawansowanego filtru spamu (ASF, Advanced Spam Filter) dostępne w zasadach ochrony przed spamem. Wszystkie te ustawienia są Wyłączone **zarówno dla** poziomów **standardowych,** **jak i ścisłych** . Aby uzyskać więcej informacji o ustawieniach asf, zobacz Zaawansowane ustawienia filtru [spamu (ASF) w uciekaniu poczty e-mail](advanced-spam-filtering-asf-options.md).

<br>

****

|Nazwa funkcji zabezpieczeń|Komentowanie|
|---|---|
|**Obraz linków do witryn zdalnych** (_IncreaseScoreWithImageLinks_)||
|**Numeric IP address in URL** (_IncreaseScoreWithNumericIps_)||
|**Przekierowanie adresu URL do innego portu** (_IncreaseScoreWithRedirectToOtherPort_)||
|**Linki do witryn internetowych .biz lub .info** (_IncreaseScoreWithBizOrInfoUrls_)||
|**Puste wiadomości** (_MarkAsSpamEmptyMessages_)||
|**Osadzanie tagów w języku HTML** (_MarkAsSpamEmbedTagsInHtml_)||
|**JavaScript lub VBScript w języku HTML** (_MarkAsSpamJavaScriptInHtml_)||
|**Tagi formularza w języku HTML** (_MarkAsSpamFormTagsInHtml_)||
|**Tagi ramki lub elementu iframe w języku HTML** (_MarkAsSpamFramesInHtml_)||
|**Usterki sieci Web w języku HTML** (_MarkAsSpamWebBugsInHtml_)||
|**Tagi obiektów w języku HTML** (_MarkAsSpamObjectTagsInHtml_)||
|**Wyrazy poufne** (_MarkAsSpamSensitiveWordList_)||
|**Rekord SPF: trudno nie powieść** (_MarkAsSpamSpfRecordFail_)||
|**Trudno nie można przefiltrować identyfikatora** nadawcy (_MarkAsSpamFromAddressAuthFail_)||
|**Backscatter** (_MarkAsSpamNdrBackscatter_)||
|**Tryb testowy** (_TestModeAction_)|W przypadku ustawień asf,  które obsługują akcję Testuj, możesz skonfigurować akcję trybu testowania na wartość **Brak, Dodaj** domyślny tekst **nagłówka X** lub Wyślij wiadomość **UDW** (`None`, `AddXHeader`lub ).`BccMessage` Aby uzyskać więcej informacji, zobacz [Włączanie, wyłączanie i testowanie ustawień asf](advanced-spam-filtering-asf-options.md#enable-disable-or-test-asf-settings).|
|

#### <a name="eop-outbound-spam-policy-settings"></a>Ustawienia zasad spamu ruchu wychodzącego eOP

Aby utworzyć i skonfigurować zasady spamu ruchu wychodzącego, zobacz Konfigurowanie filtrowania [spamu ruchu wychodzącego w u usługi EOP](configure-the-outbound-spam-policy.md).

Aby uzyskać więcej informacji o domyślnych limitach wysyłania w usłudze, zobacz [Limity wysyłania](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#sending-limits-1).

> [!NOTE]
> Zasady spamu wychodzącego nie są częścią standardowych ani ściśle wstępnie ustawionych zasad zabezpieczeń. Wartości **Standardowe** i **Ścisłe** wskazują nasze **wartości zalecane** w domyślnych zasadach spamu wychodzącego lub niestandardowych niestandardowych zasadach, które tworzysz.

<br>

****

|Nazwa funkcji zabezpieczeń|Domyślne|Standard|Ścisłe|Komentowanie|
|---|:---:|:---:|:---:|---|
|**Ustawianie limitu wiadomości zewnętrznych** <p> _RecipientLimitExternalPerHour_|0|500|400|Wartość domyślna 0 oznacza używanie wartości domyślnych usługi.|
|**Ustawianie wewnętrznego limitu wiadomości** <p> _RecipientLimitInternalPerHour_|0|1000|800|Wartość domyślna 0 oznacza używanie wartości domyślnych usługi.|
|**Ustawianie dziennego limitu wiadomości** <p> _RecipientLimitPerDay_|0|1000|800|Wartość domyślna 0 oznacza używanie wartości domyślnych usługi.|
|**Ograniczenie dotyczące użytkowników, którzy osiągają limit wiadomości** <p> _ActionWhenThresholdReached_|**Ograniczanie możliwości wysyłania poczty przez użytkownika do następnego dnia** <p> `BlockUserForToday`|**Ograniczanie możliwości wysyłania poczty przez użytkownika** <p> `BlockUser`|**Ograniczanie możliwości wysyłania poczty przez użytkownika** <p> `BlockUser`||
|**Reguły automatycznego przesyłania dalej** <p> _AutoForwardingMode_|**Automatyczne — sterowane przez system** <p> `Automatic`|**Automatyczne — sterowane przez system** <p> `Automatic`|**Automatyczne — sterowane przez system** <p> `Automatic`|
|**Wysyłanie kopii wiadomości wychodzących, które przekraczają te limity, do tych użytkowników i grup** <p> _BccSuspi dpiOutboundMail_ <p> _UDWSuspipitrwałaOutboundAdditionalRecipients_|Nie wybrano <p> `$false` <p> Puste|Nie wybrano <p> `$false` <p> Puste|Nie wybrano <p> `$false` <p> Puste|Nie mamy konkretnych zaleceń dla tego ustawienia. <p> To ustawienie działa tylko w domyślnych zasadach spamu wychodzącego. Nie działa on w niestandardowych, niestandardowych zasadach spamu wychodzących, które tworzysz.|
|**Powiadamianie tych użytkowników i grup w przypadku zablokowania nadawcy z powodu wysyłania spamu wychodzącego** <p> _NotifyOutboundSpam_ <p> _NotifyOutboundSpamRecipients_|Nie wybrano <p> `$false` <p> Puste|Nie wybrano <p> `$false` <p> Puste|Nie wybrano <p> `$false` <p> Puste|Domyślne zasady [alertów](../../compliance/alert-policies.md) o  nazwie Użytkownik z ograniczonymi możliwościami wysyłania wiadomości e-mail już wysyłają powiadomienia e-mail do członków grupy **TenantAdmins** **(** administratorzy globalni), gdy użytkownicy zostaną zablokowani ze względu na przekroczenie limitów określonych w zasadach. **Zdecydowanie zalecamy korzystanie z zasad alertów** zamiast tego ustawienia w zasadach spamu ruchu wychodzącego do powiadamiania administratorów i innych użytkowników. Aby uzyskać instrukcje, [zobacz Weryfikowanie ustawień alertów dla użytkowników z ograniczeniami](removing-user-from-restricted-users-portal-after-spam.md#verify-the-alert-settings-for-restricted-users).|
|

### <a name="eop-anti-malware-policy-settings"></a>Ustawienia zasad ochrony przed złośliwym oprogramowaniem firmy EOP

Aby tworzyć i konfigurować zasady ochrony przed złośliwym oprogramowaniem, zobacz [Konfigurowanie zasad ochrony przed złośliwym oprogramowaniem w uciek usługi EOP](configure-anti-malware-policies.md).

<br>

****

|Nazwa funkcji zabezpieczeń|Domyślne|Standard|Ścisłe|Komentowanie|
|---|:---:|:---:|:---:|---|
|**Ustawienia ochrony**|||||
|**Włączanie filtru typowych załączników** <p> _EnableFileFilter_|Nie wybrano <p> `$false`|Zaznaczone <p> `$true`|Zaznaczone <p> `$true`|To ustawienie umożliwia kwarantannę wiadomości zawierających wykonywalne załączniki na podstawie typu pliku, niezależnie od ich zawartości.|
|**Włączanie automatycznego przeczyszczania w godzinach pracy w poszukiwaniu złośliwego oprogramowania** <p> _ZapEnabled_|Zaznaczone <p> `$true`|Zaznaczone <p> `$true`|Zaznaczone <p> `$true`||
|**Zasady kwarantanny**|AdminOnlyAccessPolicy|AdminOnlyAccessPolicy|AdminOnlyAccessPolicy|Po utworzeniu nowych zasad ochrony przed złośliwym oprogramowaniem pusta wartość oznacza, że do zdefiniowania funkcji historycznych wiadomości poddanych kwarantannie jako złośliwe oprogramowanie są używane domyślne zasady kwarantanny (AdminOnlyAccessPolicy). <p> Administratorzy mogą tworzyć i wybierać niestandardowe zasady kwarantanny definiujące więcej możliwości dla użytkowników. Aby uzyskać więcej informacji, zobacz [Zasady kwarantanny](quarantine-policies.md).|
|**Powiadomienia adresata**|||||
|**Powiadamianie adresatów, gdy wiadomości są poddane kwarantannie jako złośliwe oprogramowanie** <p> _Akcja_|Nie wybrano <p> _DeleteMessage_|Nie wybrano <p> _DeleteMessage_|Nie wybrano <p> _DeleteMessage_|W przypadku wykrycia złośliwego oprogramowania w załączniku wiadomości e-mail wiadomość jest poddana kwarantannie i może zostać opublikowana tylko przez administratora.|
|**Powiadomienia nadawcy**|||||
|**Powiadamianie nadawców wewnętrznych, gdy wiadomości są poddane kwarantannie jako złośliwe oprogramowanie** <p> _EnableInternalSenderNotifications_|Nie wybrano <p> `$false`|Nie wybrano <p> `$false`|Nie wybrano <p> `$false`||
|**Powiadamianie nadawców zewnętrznych, gdy wiadomości są poddane kwarantannie jako złośliwe oprogramowanie** <p> _EnableExternalSenderNotifications_|Nie wybrano <p> `$false`|Nie wybrano <p> `$false`|Nie wybrano <p> `$false`||
|**Powiadomienia administratora**|||||
|**Powiadamianie administratora o niedostarczanych wiadomościach od nadawców wewnętrznych** <p> _EnableInternalSenderAdminNotifications_ <p> _InternalSenderAdminAddress_|Nie wybrano <p> `$false`|Nie wybrano <p> `$false`|Nie wybrano <p> `$false`|Nie mamy konkretnych zaleceń dla tego ustawienia.|
|**Powiadamianie administratora o niedostarczanych wiadomościach od nadawców zewnętrznych** <p> _EnableExternalSenderAdminNotifications_ <p> _ExternalSenderAdminAddress_|Nie wybrano <p> `$false`|Nie wybrano <p> `$false`|Nie wybrano <p> `$false`|Nie mamy konkretnych zaleceń dla tego ustawienia.|
|**Dostosowywanie powiadomień**||||Nie mamy konkretnych zaleceń dotyczących tych ustawień.|
|**Stosowanie niestandardowego tekstu powiadomień** <p> _CustomNotifications_|Nie wybrano <p> `$false`|Nie wybrano <p> `$false`|Nie wybrano <p> `$false`||
|**Od nazwy** <p> _CustomFromName_|Puste <p> `$null`|Puste <p> `$null`|Puste <p> `$null`||
|**Od adresu** <p> _CustomFromAddress_|Puste <p> `$null`|Puste <p> `$null`|Puste <p> `$null`||
|**Dostosowywanie powiadomień dotyczących wiadomości od nadawców wewnętrznych**||||Te ustawienia są używane tylko w przypadku, gdy zaznaczono opcję Powiadamiaj nadawców wewnętrznych,  gdy wiadomości są poddane kwarantannie jako złośliwe **oprogramowanie lub** Powiadom administratora o niedostarczanych wiadomościach od nadawców wewnętrznych.|
|**Temat** <p> _CustomInternalSubject_|Puste <p> `$null`|Puste <p> `$null`|Puste <p> `$null`||
|**Komunikat** <p> _CustomInternalBody_|Puste <p> `$null`|Puste <p> `$null`|Puste <p> `$null`||
|**Dostosowywanie powiadomień dotyczących wiadomości od nadawców zewnętrznych**||||Te ustawienia są używane tylko wtedy, gdy jest zaznaczona opcja Powiadamiaj nadawców zewnętrznych,  gdy wiadomości są poddane kwarantannie jako złośliwe **oprogramowanie lub** Powiadom administratora o niedostarczanych wiadomościach od nadawców zewnętrznych.|
|**Temat** <p> _CustomExternalSubject_|Puste <p> `$null`|Puste <p> `$null`|Puste <p> `$null`||
|**Komunikat** <p> _CustomExternalBody_|Puste <p> `$null`|Puste <p> `$null`|Puste <p> `$null`||
|

### <a name="eop-anti-phishing-policy-settings"></a>Ustawienia zasad ochrony przed wyłudzaniem informacji w uchcie EOP

Aby uzyskać więcej informacji o tych ustawieniach, zobacz [Fałsz ustawienia](set-up-anti-phishing-policies.md#spoof-settings). Aby skonfigurować te ustawienia, zobacz [Konfigurowanie zasad ochrony przed wyłudzaniem informacji w u usługi EOP](configure-anti-phishing-policies-eop.md).

<br>

****

|Nazwa funkcji zabezpieczeń|Domyślne|Standard|Ścisłe|Komentowanie|
|---|:---:|:---:|:---:|---|
|**Próg wyłudzania & informacji**|||||
|**Włączanie analizy fałszowania** <p> _EnableSpoofIntelligence_|Zaznaczone <p> `$true`|Zaznaczone <p> `$true`|Zaznaczone <p> `$true`||
|**Akcje**|||||
|**Jeśli wiadomość zostanie wykryta jako fałszywa** <p> _UwierzytelnianieFailAction_|**Przenoszenie wiadomości do folderów wiadomości-śmieci adresatów** <p> `MoveToJmf`|**Przenoszenie wiadomości do folderów wiadomości-śmieci adresatów** <p> `MoveToJmf`|**Poddaj wiadomość kwarantannie** <p> `Quarantine`|To ustawienie dotyczy fałszywych nadawców, którzy zostali automatycznie zablokowani, jak pokazano w szczegółowych [](learn-about-spoof-intelligence.md) informacjach o analizie fałszerzy lub ręcznie zablokowanych na liście zezwalania[/blokowania dzierżawy](tenant-allow-block-list.md). <p> Jeśli **wybierzesz pozycję** Poddaj  wiadomość kwarantannie, dostępne jest pole Zastosuj zasady kwarantanny w celu wybrania zasad kwarantanny definiujących, co użytkownicy mogą robić w przypadku wiadomości poddanych kwarantannie jako fałszowanie. Podczas tworzenia nowych zasad ochrony przed wyłudzaniem informacji pusta wartość oznacza, że do zdefiniowania funkcji historycznych dla wiadomości poddanych kwarantannie jako spoofing (DefaultFullAccessPolicy) są używane domyślne zasady kwarantanny. <p> Administratorzy mogą tworzyć i wybierać niestandardowe zasady kwarantanny definiujące bardziej restrykcyjne lub mniej restrykcyjne funkcje dla użytkowników. Aby uzyskać więcej informacji, zobacz [Zasady kwarantanny](quarantine-policies.md).|
|**Pokazywanie pierwszego kontaktu porada dotycząca bezpieczeństwa** <p> _EnableFirstContactSafetyTips_|Nie wybrano <p> `$false`|Nie wybrano <p> `$false`|Nie wybrano <p> `$false`|Aby uzyskać więcej informacji, zobacz [Pierwszy kontakt porada dotycząca bezpieczeństwa](set-up-anti-phishing-policies.md#first-contact-safety-tip).|
|**Pokaż (?) dla nieuwierzytanych nadawców w celu fałszowania** <p> _EnableUnauthenticatedSender_|Zaznaczone <p> `$true`|Zaznaczone <p> `$true`|Zaznaczone <p> `$true`|Dodaje znak zapytania (?) do zdjęcia nadawcy w programie Outlook niezidentyfikowanych nadawców. Aby uzyskać więcej informacji, zobacz [Nieuwierzyta nadawca](set-up-anti-phishing-policies.md#unauthenticated-sender).|
|**Pokaż tag "za pośrednictwem"** <p> _EnableViaTag_|Zaznaczone <p> `$true`|Zaznaczone <p> `$true`|Zaznaczone <p> `$true`|Dodaje tag za pośrednictwem (chris@contoso.com przez fabrikam.com) do adresu Od, jeśli różni się on od domeny w podpisie DKIM lub adresu **MAIL FROM** . <p> Aby uzyskać więcej informacji, zobacz [Nieuwierzyta nadawca](set-up-anti-phishing-policies.md#unauthenticated-sender).|
|

## <a name="microsoft-defender-for-office-365-security"></a>Program Microsoft Defender dla Office 365 zabezpieczeń

Dodatkowe korzyści związane z zabezpieczeniami są dostępne w programie Microsoft Defender dla Office 365 subskrypcji. Aby uzyskać najnowsze informacje, zobacz Co nowego w [programie Defender dla Office 365](whats-new-in-defender-for-office-365.md).

> [!IMPORTANT]
>
> - Domyślne zasady ochrony przed wyłudzaniem informacji w programie Microsoft Defender dla Office 365 zapewniają ochronę przed [fałszerami](set-up-anti-phishing-policies.md#spoof-settings) i analizą skrzynek pocztowych dla wszystkich adresatów. Jednak inne dostępne funkcje ochrony [personifikacji](#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365) i ustawienia [zaawansowane](#advanced-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365) nie są konfigurowane ani włączone w zasadach domyślnych. Aby włączyć wszystkie funkcje ochrony, zmodyfikuj domyślne zasady ochrony przed wyłudzaniem informacji lub utwórz dodatkowe zasady ochrony przed wyłudzaniem informacji.
>
> - Chociaż nie istnieją żadne domyślne zasady załączników ani linki programu Sejf Sejf Sejf, wstępnie ustawione zasady zabezpieczeń wbudowanej  ochrony zapewniają ochronę załączników i Sejf Ochronę załączników oraz ochronę linków dla wszystkich adresatów (użytkowników, którzy nie są zdefiniowani w niestandardowych zasadach załączników programu Sejf lub zasadach linków programu Sejf). Aby uzyskać więcej informacji, zobacz [Wstępnie ustawione zasady zabezpieczeń w usługach EOP i Microsoft Defender for Office 365](preset-security-policies.md).
>
> - Sejf załączników do [SharePoint, wiadomości OneDrive](mdo-for-spo-odb-and-teams.md) i dokumentów oraz Microsoft Teams [dokumenty](safe-docs.md) Sejf nie mają zależności od zasad Sejf linków.

Jeśli Twoja subskrypcja obejmuje program Microsoft Defender dla systemu Office 365 lub jeśli zakupiono usługę Defender dla systemu Office 365 jako dodatek, ustaw następujące konfiguracje standardowe lub ścisłe.

### <a name="anti-phishing-policy-settings-in-microsoft-defender-for-office-365"></a>Ustawienia zasad ochrony przed wyłudzaniem informacji w programie Microsoft Defender dla Office 365

Klienci usługi EOP mogą uzyskać podstawowe funkcje ochrony przed wyłudzaniem informacji w sposób opisany wcześniej, ale program Defender for Office 365 oferuje więcej funkcji i kontroli, które pomagają zapobiegać atakom, wykrywać i rekultywować je. Aby utworzyć i skonfigurować te zasady, zobacz Konfigurowanie zasad ochrony przed wyłudzaniem informacji w [programie Defender dla Office 365](configure-mdo-anti-phishing-policies.md).

#### <a name="advanced-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365"></a>Ustawienia zaawansowane w zasadach ochrony przed wyłudzaniem informacji w programie Microsoft Defender dla Office 365

Aby uzyskać więcej informacji na temat tego ustawienia, zobacz Zaawansowane progi wyłudzania informacji w zasadach ochrony przed wyłudzaniem informacji w [programie Microsoft Defender for Office 365](set-up-anti-phishing-policies.md#advanced-phishing-thresholds-in-anti-phishing-policies-in-microsoft-defender-for-office-365). Aby skonfigurować to ustawienie, zobacz [Konfigurowanie zasad ochrony przed wyłudzaniem informacji w programie Defender dla Office 365](configure-mdo-anti-phishing-policies.md).

<br>

****

|Nazwa funkcji zabezpieczeń|Domyślne|Standard|Ścisłe|Komentowanie|
|---|:---:|:---:|:---:|---|
|**Próg wyłudzania informacji e-mail** <p> _PhishThresholdLevel_|**1 — Standardowy** <p> `1`|**2. Agresywne** <p> `2`|**3 . Bardziej agresywne** <p> `3`||
|

#### <a name="impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365"></a>Ustawienia personifikacji w zasadach ochrony przed wyłudzaniem informacji w programie Microsoft Defender dla Office 365

Aby uzyskać więcej informacji na temat tych ustawień, zobacz Ustawienia personifikacji w zasadach ochrony przed wyłudzaniem informacji w [programie Microsoft Defender for Office 365](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365). Aby skonfigurować te ustawienia, zobacz [Konfigurowanie zasad ochrony przed wyłudzaniem informacji w programie Defender dla Office 365](configure-mdo-anti-phishing-policies.md).

<br>

****

|Nazwa funkcji zabezpieczeń|Domyślne|Standard|Ścisłe|Komentowanie|
|---|:---:|:---:|:---:|---|
|**Próg wyłudzania & informacji**|||||
|**Umożliwianie użytkownikom ochrony** (personifikacja ochrony użytkownika) <p> _EnableTargetedUserProtection_ <p> _TargetedUsersToProtect_|Nie wybrano <p> `$false` <p> brak|Zaznaczone <p> `$true` <p> \<list of users\>|Zaznaczone <p> `$true` <p> \<list of users\>|Zalecamy dodawanie użytkowników (nadawców wiadomości) do kluczowych ról. Wewnętrznie chronionymi nadawcami może być dyrektor generalny, dyrektor ds. dyrektora finansowego i inni kierownictwo wyższego szczebla. Zewnętrznie chronieni nadawcy mogą obejmować członków zarządu lub członków zarządu. <p> W wstępnie ustawionych zasadach zabezpieczeń nie można określić użytkowników, którzy będą chronić. Należy wyłączyć wstępnie ustawione zasady zabezpieczeń i użyć niestandardowych zasad ochrony przed wyłudzaniem informacji, aby dodać użytkowników do kluczowych ról zgodnie z sugestiami.|
|**Włączanie ochrony domen** (spersonifikowana ochrona domeny)|Nie wybrano|Zaznaczone|Zaznaczone||
|**Uwzględnij domeny, których jestem właścicielem** <p> _EnableOrganizationDomainsProtection_|Wyłączone <p> `$false`|Zaznaczone <p> `$true`|Zaznaczone <p> `$true`||
|**Uwzględnianie domen niestandardowych** <p> _EnableTargetedDomainsProtection_ <p> _TargetedDomainsToProtect_|Wyłączone <p> `$false` <p> brak|Zaznaczone <p> `$true` <p> \<list of domains\>|Zaznaczone <p> `$true` <p> \<list of domains\>|Zalecamy dodanie domen (domen nadawcy), które nie są Dla Ciebie właścicielami, ale często wchodzisz w interakcje. <p> W wstępnie ustawionych zasadach zabezpieczeń nie można określić domen custm w celu ochrony. Aby dodać domeny niestandardowe do ochrony zgodnie z sugestiami, należy wyłączyć wstępnie ustawione zasady zabezpieczeń i użyć niestandardowych zasad ochrony przed wyłudzaniem informacji.|
|**Dodawanie zaufanych nadawców i domen** <p> _ExcludedSenders_ <p> _ExcludedDomains_|Brak|Brak|Brak|W zależności od organizacji zalecamy dodawanie nadawców lub domen, które są niepoprawnie zidentyfikowane jako próby personifikacji.|
|**Włączanie analizy skrzynek pocztowych** <p> _EnableMailboxIntelligence_|Zaznaczone <p> `$true`|Zaznaczone <p> `$true`|Zaznaczone <p> `$true`||
|**Włączanie analizy dla ochrony personifikacji** <p> _EnableMailboxIntelligenceProtection_|Wyłączone <p> `$false`|Zaznaczone <p> `$true`|Zaznaczone <p> `$true`|To ustawienie umożliwia określoną akcję wykrywania personifikacji przez analizę skrzynki pocztowej.|
|**Akcje**||||Niezależnie od tego, gdzie wybierzesz pozycję Poddaj wiadomość kwarantannie, dostępne **jest pole Wybierz zasady** kwarantanny. Zasady kwarantanny określają, co użytkownicy mogą robić w przypadku wiadomości poddanych kwarantannie. <p> Podczas tworzenia nowych zasad ochrony przed wyłudzaniem informacji pusta wartość oznacza, że do definiowania funkcji historycznych dla wiadomości poddanych kwarantannie w tym werdyktzie są używane domyślne zasady kwarantanny (DefaultFullAccessPolicy dla wszystkich typów wykrywania personifikacji). <p> Administratorzy mogą tworzyć i wybierać niestandardowe zasady kwarantanny definiujące mniej restrykcyjne lub bardziej restrykcyjne funkcje dla użytkowników. Aby uzyskać więcej informacji, zobacz [Zasady kwarantanny](quarantine-policies.md).|
|**Jeśli wiadomość zostanie wykryta jako personifikowany użytkownik** <p> _TargetedUserProtectionAction_|**Nie zastosuj żadnej akcji** <p> `NoAction`|**Poddaj wiadomość kwarantannie** <p> `Quarantine`|**Poddaj wiadomość kwarantannie** <p> `Quarantine`|Pamiętaj, że wstępnie ustawione zasady zabezpieczeń nie pozwalają na określenie użytkowników do ochrony, więc to ustawienie nie powoduje żadnych działań w wstępnie ustawionych zasadach zabezpieczeń.|
|**Jeśli wiadomość zostanie wykryta jako spersonifikowana domena** <p> _TargetedDomainProtectionAction_|**Nie zastosuj żadnej akcji** <p> `NoAction`|**Poddaj wiadomość kwarantannie** <p> `Quarantine`|**Poddaj wiadomość kwarantannie** <p> `Quarantine`|Pamiętaj, że wstępnie ustawione zasady zabezpieczeń nie umożliwiają określenia domen niestandardowych do ochrony, więc to ustawienie dotyczy tylko tych domen, których jesteś właścicielem, a nie domen niestandardowych.|
|**Jeśli inteligencja skrzynki pocztowej wykryje i personifikuje użytkownika** <p> _MailboxIntelligenceProtectionAction_|**Nie zastosuj żadnej akcji** <p> `NoAction`|**Przenoszenie wiadomości do folderów wiadomości-śmieci adresatów** <p> `MoveToJmf`|**Poddaj wiadomość kwarantannie** <p> `Quarantine`||
|**Pokaż identyfikator personifikacji porada dotycząca bezpieczeństwa** <p> _EnableSimilarUsersSafetyTips_|Wyłączone <p> `$false`|Zaznaczone <p> `$true`|Zaznaczone <p> `$true`||
|**Pokaż domenę personifikacji porada dotycząca bezpieczeństwa** <p> _EnableSimilarDomainsSafetyTips_|Wyłączone <p> `$false`|Zaznaczone <p> `$true`|Zaznaczone <p> `$true`||
|**Pokaż nietypowe znaki personifikacji porada dotycząca bezpieczeństwa** <p> _EnableUnusualCharactersSafetyTips_|Wyłączone <p> `$false`|Zaznaczone <p> `$true`|Zaznaczone <p> `$true`||
|

#### <a name="eop-anti-phishing-policy-settings-in-microsoft-defender-for-office-365"></a>Ustawienia zasad ochrony przed wyłudzaniem informacji usługi EOP w programie Microsoft Defender dla Office 365

Są to te same ustawienia, które są dostępne w ustawieniach zasad ochrony [przed spamem w u programie EOP](#eop-anti-spam-policy-settings).

Ustawienia fałsz są powiązane ze sobą, ale ustawienie Pokaż pierwszy kontakt **porada dotycząca bezpieczeństwa** nie ma zależności od ustawień fałszowania.

<br>

****

|Nazwa funkcji zabezpieczeń|Domyślne|Standard|Ścisłe|Komentowanie|
|---|:---:|:---:|:---:|---|
|**Próg wyłudzania & informacji**|||||
|**Włączanie analizy fałszowania** <p> _EnableSpoofIntelligence_|Zaznaczone <p> `$true`|Zaznaczone <p> `$true`|Zaznaczone <p> `$true`||
|**Akcje**|||||
|**Jeśli wiadomość zostanie wykryta jako fałszywa** <p> _UwierzytelnianieFailAction_|**Przenoszenie wiadomości do folderów wiadomości-śmieci adresatów** <p> `MoveToJmf`|**Przenoszenie wiadomości do folderów wiadomości-śmieci adresatów** <p> `MoveToJmf`|**Poddaj wiadomość kwarantannie** <p> `Quarantine`|To ustawienie dotyczy fałszywych nadawców, którzy zostali automatycznie zablokowani, jak pokazano w szczegółowych [](learn-about-spoof-intelligence.md) informacjach o analizie fałszerzy lub ręcznie zablokowanych na liście zezwalania[/blokowania dzierżawy](tenant-allow-block-list.md). <p> Jeśli wybierzesz pozycję **Poddaj** wiadomość kwarantannie, dostępne jest pole Zastosuj zasady kwarantanny w celu wybrania zasad kwarantanny definiujących, co użytkownicy mogą robić w kwarantannie wiadomości. Podczas tworzenia nowych zasad ochrony przed wyłudzaniem informacji pusta wartość oznacza, że do definiowania funkcji historycznych pod kwarantanną są używane domyślne zasady kwarantanny (DefaultFullAccessPolicy). <p> Administratorzy mogą utworzyć i wybrać niestandardowe zasady kwarantanny, które określają, co adresaci mogą robić w kwarantannie. Aby uzyskać więcej informacji, zobacz [Zasady kwarantanny](quarantine-policies.md).|
|**Pokazywanie pierwszego kontaktu porada dotycząca bezpieczeństwa** <p> _EnableFirstContactSafetyTips_|Nie wybrano <p> `$false`|Zaznaczone <p> `$true`|Zaznaczone <p> `$true`|Aby uzyskać więcej informacji, zobacz [Pierwszy kontakt porada dotycząca bezpieczeństwa](set-up-anti-phishing-policies.md#first-contact-safety-tip).|
|**Pokaż (?) dla nieuwierzytanych nadawców w celu fałszowania** <p> _EnableUnauthenticatedSender_|Zaznaczone <p> `$true`|Zaznaczone <p> `$true`|Zaznaczone <p> `$true`|Dodaje znak zapytania (?) do zdjęcia nadawcy w programie Outlook niezidentyfikowanych nadawców. Aby uzyskać więcej informacji, zobacz [Nieuwierzyta nadawca](set-up-anti-phishing-policies.md#unauthenticated-sender).|
|**Pokaż tag "za pośrednictwem"** <p> _EnableViaTag_|Zaznaczone <p> `$true`|Zaznaczone <p> `$true`|Zaznaczone <p> `$true`|Dodaje tag za pośrednictwem (chris@contoso.com przez fabrikam.com) do adresu Od, jeśli różni się on od domeny w podpisie DKIM lub adresu **MAIL FROM** . <p> Aby uzyskać więcej informacji, zobacz [Nieuwierzyta nadawca](set-up-anti-phishing-policies.md#unauthenticated-sender).|
|

### <a name="safe-attachments-settings"></a>Sejf ustawienia załączników

Sejf w programie Microsoft Defender dla programu Office 365 zawiera ustawienia globalne, które nie mają relacji z zasadami załączników programu Sejf, oraz ustawieniami specyficznmi dla poszczególnych zasad usługi Sejf Links. Aby uzyskać więcej informacji, [zobacz załączniki Sejf w programie Defender dla Office 365](safe-attachments.md).

Chociaż nie istnieją domyślne zasady załączników załączników programu Sejf, wstępnie ustawione  zasady zabezpieczeń wbudowanej ochrony zapewniają ochronę załączników programu Sejf wszystkim adresatom (użytkownikom, którzy nie są zdefiniowani w niestandardowych zasadach załączników Sejf). Aby uzyskać więcej informacji, zobacz [Wstępnie ustawione zasady zabezpieczeń w usługach EOP i Microsoft Defender for Office 365](preset-security-policies.md).

#### <a name="global-settings-for-safe-attachments"></a>Ustawienia globalne załączników Sejf

> [!NOTE]
> Ustawienia globalne załączników Sejf są ustawiane przez wstępnie ustawione zasady  zabezpieczeń Wbudowane ustawienia ochrony, ale nie są określone przez standardowe lub  **ścisłe** wstępnie ustawione zasady zabezpieczeń. W każdym z tych sposobów administratorzy mogą w dowolnym momencie Sejf ustawienia załączników globalnych.
>
> W **kolumnie** Domyślne są wartości, które istnieją przed ustawieniem wstępnie ustawionych zasad zabezpieczeń **Wbudowany** ochrona. W **kolumnie Ochrona wbudowana są** wartości ustawione przez wstępnie ustawione zasady zabezpieczeń Wbudowane ustawienia  ochrony, które są również wartościami zalecanymi.

Aby skonfigurować te ustawienia, zobacz Włączanie załączników wiadomości [Sejf dla SharePoint, OneDrive,](turn-on-mdo-for-spo-odb-and-teams.md) Microsoft Teams i Sejf [Dokumenty w](safe-docs.md) Microsoft 365 E5.

W programie PowerShell możesz użyć polecenia cmdlet [Set-AtpPolicyForO365](/powershell/module/exchange/set-atppolicyforo365) dla tych ustawień.

<br>

****

|Nazwa funkcji zabezpieczeń|Domyślne|Wbudowana ochrona|Komentowanie|
|---|:---:|:---:|---|
|**Włącz defender for Office 365 for SharePoint, OneDrive, and Microsoft Teams** <p> _EnableATPForSPOTeamsODB_|Wyłączone <p> `$false`|Wł. <p> `$true`|Aby uniemożliwić użytkownikom pobieranie złośliwych plików, zobacz Używanie programu SharePoint Online PowerShell w celu uniemożliwienie użytkownikom [pobierania złośliwych plików](turn-on-mdo-for-spo-odb-and-teams.md#step-2-recommended-use-sharepoint-online-powershell-to-prevent-users-from-downloading-malicious-files).|
|**Włączanie dokumentów Sejf dla Office klientów** <p> _EnableSafeDocs_|Wyłączone <p> `$false`|Wł. <p> `$true`|Ta funkcja jest dostępna i znacząca tylko w przypadku licencji, które nie są zawarte w programie Defender Office 365 (na przykład dla Microsoft 365 E5 lub Zabezpieczenia platformy Microsoft 365 E5). Aby uzyskać więcej informacji, [zobacz Sejf Dokumenty w programie Microsoft 365 E5](safe-docs.md).|
|**Zezwalaj użytkownikom na klikanie w widoku chronionym, Sejf plik został oznaczony jako złośliwy** <p> _AllowSafeDocsOpen_|Wyłączone <p> `$false`|Wyłączone <p> `$false`|To ustawienie jest powiązane z Sejf dokumentów.|
|

#### <a name="safe-attachments-policy-settings"></a>Sejf zasad Załączniki

Aby skonfigurować te ustawienia, zobacz [Konfigurowanie Sejf załączników w programie Defender for Office 365](set-up-safe-attachments-policies.md).

W programie PowerShell do tych ustawień są służące polecenia cmdlet [New-SafeAttachmentPolicy](/powershell/module/exchange/new-safeattachmentpolicy) i [Set-SafeAttachmentPolicy](/powershell/module/exchange/set-safelinkspolicy) .

> [!NOTE]
> Zgodnie z wcześniejszym opisem nie ma żadnych domyślnych Sejf załączników, ale Sejf Ochronę załączników można przypisać do wszystkich adresatów za pomocą wstępnie ustawionych zasad zabezpieczeń Wbudowane [ ustawienia ochrony](preset-security-policies.md).
>
> Wartość **Domyślna w kolumnie** niestandardowej odwołuje się do wartości domyślnych w nowych Sejf tworzyć załączniki. Pozostałe kolumny wskazują (chyba że zaznaczono inaczej) wartości skonfigurowane w odpowiednich wstępnie ustawionych zasadach zabezpieczeń.

<br>

****

|Nazwa funkcji zabezpieczeń|Domyślne w niestandardowym|Wbudowana ochrona|Standard|Ścisłe|Komentowanie|
|---|:---:|:---:|:---:|:---:|---|
|**Sejf załączników odpowiedź z nieznanym złośliwym oprogramowaniem** <p> _Włączanie_ i _działanie_|**Wyłączone** <p> `-Enable $false` i `-Action Block`|**Blokuj** <p> `-Enable $true` i `-Action Block`|**Blokuj** <p> `-Enable $true` i `-Action Block`|**Blokuj** <p> `-Enable $true` i `-Action Block`|Gdy parametr _Enable_ $false, wartość parametru _Action_ nie ma znaczenia.|
|**Zasady kwarantanny** (_tag kwarantanny_)|AdminOnlyAccessPolicy|AdminOnlyAccessPolicy|AdminOnlyAccessPolicy|AdminOnlyAccessPolicy|Gdy tworzysz nowe zasady załączników Sejf, wartość pusta oznacza, że do definiowania funkcji historycznych dla wiadomości poddanych kwarantannie przez program Sejf Attachments (AdminOnlyAccessPolicy) są używane domyślne zasady kwarantanny. <p> Administratorzy mogą tworzyć i wybierać niestandardowe zasady kwarantanny definiujące więcej możliwości dla użytkowników. Aby uzyskać więcej informacji, zobacz [Zasady kwarantanny](quarantine-policies.md).|
|**Przekierowywanie załącznika z wykrytymi załącznikami** : **Włącz przekierowywanie** <p> _Przekierowywanie_ <p> _RedirectAddress (Przekierowywanie)_|Nie wybrano i nie podano żadnego adresu e-mail. <p> `-Redirect $false` <p> _RedirectAddress jest_ pusta (`$null`)|Nie wybrano i nie podano żadnego adresu e-mail. <p> `-Redirect $false` <p> _RedirectAddress jest_ pusta (`$null`)|Zaznaczono i określono adres e-mail. <p> `$true` <p> adres e-mail|Zaznaczono i określono adres e-mail. <p> `$true` <p> adres e-mail|Przekieruj wiadomości do administratora zabezpieczeń w celu ich przejrzenia. <p> **Uwaga**: To ustawienie nie jest skonfigurowane w zasadach zabezpieczeń **Standardowa****, Ścisła** ani Wbudowana ochrona. Wartości **Standardowe** i **Ścisłe** **wskazują nasze zalecane** wartości w nowych Sejf tworzyć załączniki.|
|**Stosowanie odpowiedzi Sejf wykrywania załączników, jeśli skanowanie nie jest ukończone (limit czasu lub błędy)** <p> _ActionOnError_|Zaznaczone <p> `$true`|Zaznaczone <p> `$true`|Zaznaczone <p> `$true`|Zaznaczone <p> `$true`||
|

### <a name="safe-links-settings"></a>Sejf ustawienia linków

Sejf Linki w programie Defender dla usługi Office 365 obejmują ustawienia globalne, które dotyczą wszystkich użytkowników uwzględnionych w aktywnych zasadach linków do usługi Sejf oraz ustawień specyficznych dla poszczególnych zasad usługi Sejf Links. Aby uzyskać więcej informacji, [zobacz Sejf w programie Defender dla Office 365](safe-links.md).

Mimo że nie istnieją domyślne zasady Sejf, wstępnie ustawione zasady zabezpieczeń wbudowanej  ochrony zapewniają ochronę linków programu Sejf wszystkim adresatom (użytkownikom, którzy nie są zdefiniowani w niestandardowych zasadach Sejf Linków). Aby uzyskać więcej informacji, zobacz [Wstępnie ustawione zasady zabezpieczeń w usługach EOP i Microsoft Defender for Office 365](preset-security-policies.md).

#### <a name="global-settings-for-safe-links"></a>Ustawienia globalne linków Sejf użytkownika

> [!NOTE]
> Ustawienia globalne linków Sejf są określone przez wstępnie ustawione zasady zabezpieczeń Wbudowane ustawienia  ochrony, ale nie są określone przez standardowe lub **ścisłe** wstępnie ustawione  zasady zabezpieczeń. W każdym z tych sposobów administratorzy mogą w dowolnym momencie Sejf ustawienia linków do stron internetowych.
>
> W **kolumnie** Domyślne są wartości, które istnieją przed ustawieniem wstępnie ustawionych zasad zabezpieczeń **Wbudowany** ochrona. W **kolumnie Ochrona wbudowana są** wartości ustawione przez wstępnie ustawione zasady zabezpieczeń Wbudowane ustawienia  ochrony, które są również wartościami zalecanymi.

Aby skonfigurować te ustawienia, zobacz [Konfigurowanie ustawień globalnych pod Sejf Linków w programie Defender Office 365](configure-global-settings-for-safe-links.md).

W programie PowerShell możesz użyć polecenia cmdlet [Set-AtpPolicyForO365](/powershell/module/exchange/set-atppolicyforo365) dla tych ustawień.

<br>

****

|Nazwa funkcji zabezpieczeń|Domyślne|Wbudowana ochrona|Komentowanie|
|---|:---:|:---:|---|
|**Blokowanie następujących adresów URL** <p> _ExcludedUrls_|Puste <p> `$null`|Puste <p> `$null`|Nie mamy konkretnych zaleceń dla tego ustawienia. <p> Aby uzyskać więcej informacji, zobacz ["Blokowanie następujących adresów URL" w celu Sejf url](safe-links.md#block-the-following-urls-list-for-safe-links).
|**Używanie Sejf w Office 365 aplikacji** <p> _EnableSafeLinksForO365Clients_|Wł. <p> `$true`|Wł. <p> `$true`|Używaj Sejf w obsługiwanych aplikacjach Office 365 i mobilnych (dla systemów iOS i Android). Aby uzyskać więcej informacji, [zobacz Sejf Ustawienia linków dla Office 365 aplikacji](safe-links.md#safe-links-settings-for-office-365-apps).|
|**Nie śledź, gdy użytkownicy klikną chronione linki w Office 365 aplikacji** <p> _TrackClicks_|Wł. <p> `$false`|Wyłączone <p> `$true`|Wyłączenie tego ustawienia (ustawienie _śledzenia kliknięć_ `$true`na ) umożliwia śledzenie kliknięć użytkowników w obsługiwanych Office 365 aplikacjach.|
|**Nie pozwól użytkownikom na kliknięcie w oryginalnym adresie URL w Office 365 aplikacjach** <p> _AllowClickThrough_|Wł. <p> `$false`|Wł. <p> `$false`|Włączenie tego ustawienia (ustawienie _opcji AllowClickThrough_ to `$false`) zapobiega kliknięciu pierwotnego adresu URL w obsługiwanych Office 365 aplikacjach.|
|

#### <a name="safe-links-policy-settings"></a>Sejf zasad Linków

Aby skonfigurować te ustawienia, zobacz [Konfigurowanie zasad Sejf Linków w programie Microsoft Defender dla Office 365](set-up-safe-links-policies.md).

W programie PowerShell do tych ustawień są służące polecenia cmdlet [New-SafeLinksPolicy](/powershell/module/exchange/new-safelinkspolicy) i [Set-SafeLinksPolicy](/powershell/module/exchange/set-safelinkspolicy) .

> [!NOTE]
> Zgodnie z wcześniejszym opisem nie istnieją żadne domyślne zasady Sejf, ale wstępnie ustawione zasady zabezpieczeń dla Sejf Linki są przypisywane do wszystkich [ adresatów](preset-security-policies.md).
>
> Kolumna **Domyślna w kolumnie** niestandardowej odwołuje się do wartości domyślnych w nowych Sejf tworzyć linki. Pozostałe kolumny wskazują (chyba że zaznaczono inaczej) wartości skonfigurowane w odpowiednich wstępnie ustawionych zasadach zabezpieczeń.

<br>

****

|Nazwa funkcji zabezpieczeń|Domyślne w niestandardowym|Wbudowana ochrona|Standard|Ścisłe|Komentowanie|
|---|:---:|:---:|:---:|:---:|---|
|**Ustawienia ochrony**||||||
|**Wybierz akcję dla nieznanych, potencjalnie złośliwych adresów URL w wiadomościach** <p> _IsEnabled_|**Wyłączone** <p> `$false`|**Wł.** <p> `$true`|**Wł.** <p> `$true`|**Wł.** <p> `$true`||
|**Wybierz akcję dla nieznanych lub potencjalnie złośliwych adresów URL w Microsoft Teams** <p> _EnableSafeLinksForTeams_|**Wyłączone** <p> `$false`|**Wł.** <p> `$true`|**Wł.** <p> `$true`|**Wł.** <p> `$true`||
|**Stosowanie skanowania w czasie rzeczywistym adresów URL w celu wykrycia podejrzanych linków i linków, które wskazują pliki** <p> _ScanUrls_|Nie wybrano <p> `$false`|Zaznaczone <p> `$true`|Zaznaczone <p> `$true`|Zaznaczone <p> `$true`||
|**Przed dostarczeniem wiadomości poczekaj na ukończenie skanowania adresów URL** <p> _DeliverMessageAfterKan_|Nie wybrano <p> `$false`|Zaznaczone <p> `$true`|Zaznaczone <p> `$true`|Zaznaczone <p> `$true`||
|**Stosowanie Sejf do wiadomości e-mail wysyłanych w organizacji** <p> _EnableForInternalSenders_|Nie wybrano <p> `$false`|Zaznaczone <p> `$true`|Zaznaczone <p> `$true`|Zaznaczone <p> `$true`||
|**Nie śledź kliknięć użytkownika** <p> _DoNotTrackUserClicks_|Nie wybrano <p> `$false`|Nie wybrano <p> `$false`|Nie wybrano <p> `$false`|Nie wybrano <p> `$false`|Wyłączenie tego ustawienia (ustawienie opcji _DoNotTrackUserClicks_ to `$false`) umożliwia śledzenie kliknięć użytkowników.|
|**Nie pozwól użytkownikom na klikanie w celu oryginalnego adresu URL** <p> _DoNotAllowClickThrough_|Nie wybrano <p> `$false`|Nie wybrano <p> `$false`|Zaznaczone <p> `$true`|Zaznaczone <p> `$true`|Włączenie tego ustawienia (ustawienie opcji _DoNotAllowClickThrough_ ) `$true`zapobiega kliknięciu pierwotnego adresu URL.|
|**Wyświetlanie  brandingu organizacji na stronach powiadomień i ostrzeżeń** <p> _EnableOrganizationBranding_|Nie wybrano <p> `$false`|Nie wybrano <p> `$false`|Nie wybrano <p> `$false`|Nie wybrano <p> `$false`|Nie mamy konkretnych zaleceń dla tego ustawienia. <p> Przed włączeniem tego ustawienia należy postępować zgodnie z instrukcjami w temacie [Dostosowywanie](../../admin/setup/customize-your-organization-theme.md) motywu Microsoft 365 organizacji w celu przekazania logo firmy.|
|**Nie przepisuj adresów URL, sprawdzaj tylko za Sejf API łączy** <p> _DisableURLRewrite_|Nie wybrano <p> `$false`|Zaznaczone <p> `$true`|Nie wybrano <p> `$false`|Nie wybrano <p> `$false`||
|**Nie omów następujących adresów URL** <p> _DoNotRewriteUrls_|Nie wybrano <p> puste|Nie wybrano <p> puste|Nie wybrano <p> puste|Nie wybrano <p> puste|Nie mamy konkretnych zaleceń dla tego ustawienia. Aby uzyskać więcej informacji, zobacz [listy "Nie](safe-links.md#do-not-rewrite-the-following-urls-lists-in-safe-links-policies) robisz ponownie następujących adresów URL" w zasadach dotyczących Sejf URL.|
|**Powiadomienie**||||||
|**Jak chcesz powiadomić użytkowników?**|**Używanie domyślnego tekstu powiadomień**|**Używanie domyślnego tekstu powiadomień**|**Używanie domyślnego tekstu powiadomień**|**Używanie domyślnego tekstu powiadomień**|Nie mamy konkretnych zaleceń dla tego ustawienia. <p> Możesz wybrać pozycję **Użyj niestandardowego tekstu powiadomień** (_Tekst Powiadomienia_ niestandardowego), aby wprowadzić niestandardowy tekst powiadomienia. Możesz również zaznaczyć **pole wyboru Użyj Microsoft Translator** do automatycznej lokalizacji (_użyj tekstuTranslatedNotificationText_), aby przetłumaczyć niestandardowy tekst powiadomienia na język użytkownika.
|

## <a name="related-articles"></a>Artykuły pokrewne

- Szukasz najlepszych rozwiązań dotyczących reguł przepływu poczty e Exchange (nazywanych również **regułami transportu**)? Zobacz [Najlepsze rozwiązania dotyczące konfigurowania reguł przepływu poczty e-mail w programie Exchange Online](/exchange/security-and-compliance/mail-flow-rules/configuration-best-practices).

- Administratorzy i użytkownicy mogą przesyłać do firmy Microsoft wartości fałszywie dodatnie (oznaczane jako złe) i wartości fałszywie ujemne (oznaczane jako złe wiadomości e-mail). Aby uzyskać więcej informacji, zobacz [Zgłaszanie wiadomości i plików do firmy Microsoft](report-junk-email-messages-to-microsoft.md).

- Skorzystaj z tych linków, aby uzyskać informacje **na temat** konfigurowania usługi [EOP](/exchange/standalone-eop/set-up-your-eop-service) i  konfigurowania programu [Microsoft Defender na](defender-for-office-365.md) Office 365. Nie zapomnij o pomocnych wskazówkach w [tece "Ochrona przed zagrożeniami w](protect-against-threats.md) Office 365".

- Informacje o planach bazowych zabezpieczeń dla usługi **Windows** można znaleźć tutaj: Gdzie mogę uzyskać plan bazowy zabezpieczeń [?](/windows/security/threat-protection/windows-security-baselines#where-can-i-get-the-security-baselines) dla opcji lokalnych/zasad grupy i Użyj planu bazowego zabezpieczeń, aby skonfigurować Windows urządzenia w usłudze Intune pod względem zabezpieczeń opartych na usłudze [Intune](/intune/protect/security-baselines). Porównanie między programem Microsoft Defender dla punktu końcowego i bazami bazowymi zabezpieczeń usługi Microsoft Intune jest dostępne w tesłudze [Compare the Microsoft Defender for Endpoint and the Windows baselines zabezpieczeń Intune](/windows/security/threat-protection/microsoft-defender-atp/configure-machines-security-baseline#compare-the-microsoft-defender-atp-and-the-windows-intune-security-baselines).
