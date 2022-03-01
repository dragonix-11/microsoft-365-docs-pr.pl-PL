---
title: Importowanie i archiwizowanie danych innych firm w programie Microsoft 365
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: overview
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
- m365initiative-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: 0ce338d5-3666-4a18-86ab-c6910ff408cc
ms.custom:
- seo-marvel-apr2020
description: Dowiedz się, jak importować i archiwizować dane innych firm z platform mediów społecznościowych, platform do obsługi wiadomości błyskawicznych i platform współpracy nad dokumentami Microsoft 365 skrzynkach pocztowych.
ms.openlocfilehash: 06833acd3ea29e30d8789fbb05e0a081309c7f2b
ms.sourcegitcommit: dbce0b6e74ae2efec42fe2b3b82c8e8cabe0ddbe
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/15/2022
ms.locfileid: "63015804"
---
# <a name="learn-about-connectors-for-third-party-data"></a>Informacje o łącznikach dla danych innych firm

Microsoft 365 umożliwia administratorom używanie łączników danych do importowania i archiwizowania danych innych firm niż firma Microsoft z platform mediów społecznościowych, platform wiadomości błyskawicznych i platform współpracy nad dokumentami do skrzynek pocztowych Microsoft 365 organizacji. Jedną z głównych zalet korzystania z łączników danych w celu importowania i archiwizowania danych innych firm w programie Microsoft 365 Microsoft 365 jest możliwość stosowania różnych rozwiązań zgodności z przepisami do danych po ich zaimportowaniu. Pomaga to zapewnić zgodność danych organizacji innych niż firmy Microsoft z przepisami i standardami, które mają wpływ na organizację.

Obejrzyj ten interakcyjny przewodnik, w który pokazano, jak tworzyć łączniki danych do importowania i archiwizowania danych innych firm, oraz przykłady stosowania rozwiązań zgodności do danych po ich zaimportowaniu do usługi Microsoft 365.

> [!VIDEO https://mslearn.cloudguides.com/guides/Archive%20data%20from%20non-Microsoft%20sources%20in%20Microsoft%20365]

## <a name="third-party-data-connectors"></a>Łączniki danych innych firm

Witryna Centrum zgodności platformy Microsoft 365 udostępnia natywne łączniki danych innych firm od firmy Microsoft do importowania danych z różnych źródeł danych, takich jak serwis LinkedIn, Błyskawiczna rozkwitberga i Twitter, oraz łączniki danych, które obsługują rozwiązanie do zarządzania ryzykiem w niejawnym programie testów. Oprócz tych łączników danych firma Microsoft współpracuje z następującymi partnerami, aby udostępnić o wiele więcej łączników danych większej liczby części danych w p Centrum zgodności platformy Microsoft 365. Twoja organizacja współpracuje z tymi partnerami w celu skonfigurowania usługi archiwizacji przed utworzeniem odpowiedniego łącznika danych w Centrum zgodności platformy Microsoft 365.

- [Veritas](#veritas-data-connectors)

- [TeleMessage](#telemessage-data-connectors)

- [17a-4 LLC.](#17a-4-data-connectors)

- [CellTrust](#celltrust-data-connectors)

Dane innych firm wymienione w następnych sekcjach (z wyjątkiem danych kadrowych i danych fizycznych stosowanych do rozwiązania do zarządzania ryzykiem w niejawnym programie testów programu Microsoft 365) są importowane do skrzynek pocztowych użytkowników. Rozwiązania Microsoft 365, które obsługują dane innych firm, są stosowane do skrzynki pocztowej użytkownika, w której te dane są przechowywane.

### <a name="microsoft-data-connectors"></a>Łączniki danych firmy Microsoft

W poniższej tabeli wymieniono natywne łączniki danych innych firm dostępne w Centrum zgodności platformy Microsoft 365. W tabeli podsumowano również rozwiązania dotyczące zgodności, które można stosować po zaimportowaniu i zarchiwizować dane innych firm w Microsoft 365. Zobacz Omówienie [rozwiązań zgodności, które](#overview-of-compliance-solutions-that-support-third-party-data) obsługują dane innych firm, aby uzyskać bardziej szczegółowy opis poszczególnych rozwiązań do zgodności i informacje o tym, jak obsługuje ono dane innych firm.

Kliknij link w kolumnie **Dane** innych firm, aby przejść do instrukcji krok po kroku dotyczących tworzenia łącznika dla tego typu danych.

|Dane innych firm  |Zawieszenie w  postępowaniem sądowym|zbierania elektronicznych materiałów dowodowych  |Ustawienia przechowywania  |Zarządzanie rekordami  |Zgodność komunikacji  |Zarządzanie ryzykiem w niejawnym programie testów  |
|:---------|:---------|:---------|:---------|:---------|:---------|:---------|
|[Wiadomość bloomberga](archive-bloomberg-message-data.md)     |![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru.](../media/checkmark.png)||
|[Hero EHR healthcare](import-epic-data.md) ||||||![Znacznik wyboru](../media/checkmark.png)|
|[Facebook](archive-facebook-data-with-sample-connector.md)     |![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|||
|[Ogólna ochrona zdrowia w zakresie EHR](import-healthcare-data.md) ||||||![Znacznik wyboru](../media/checkmark.png)|
|[Kadry](import-hr-data.md) ||||||![Znacznik wyboru](../media/checkmark.png)|
|[ICE Chat](archive-icechat-data.md)     |![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)||
|[Instant Bloomberg](archive-instant-bloomberg-data.md)|![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)||
|[LinkedIn](archive-linkedin-data.md)   |![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|||
|[Badging fizyczny](import-physical-badging-data.md) ||||||![Znacznik wyboru](../media/checkmark.png)|
|[Slack eDiscovery](archive-slack-data-microsoft.md)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)||
|[Twitter](archive-twitter-data-with-sample-connector.md)     |![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|||
||||||||

### <a name="veritas-data-connectors"></a>Łączniki danych veritas

W tabeli w tej sekcji wymieniono łączniki danych innych firm dostępne we współpracy z firmą Veritas. W tabeli podsumowano również rozwiązania zgodności, które można zastosować do danych innych firm po zaimportowaniu i zarchiwizować je w Microsoft 365. Zobacz Omówienie [rozwiązań zgodności, które](#overview-of-compliance-solutions-that-support-third-party-data) obsługują dane innych firm, aby uzyskać bardziej szczegółowy opis poszczególnych rozwiązań do zgodności i informacje o tym, jak obsługuje ono dane innych firm.

Zanim będzie można zarchiwizować dane innych firm w Microsoft 365, musisz we współpracy z serwisem Veritas skonfigurować ich usługę archiwizacji (o nazwie *Merge1*) dla Twojej organizacji. Aby uzyskać więcej informacji, kliknij link w kolumnie  Dane innej firmy, aby przejść do instrukcji krok po kroku dotyczących tworzenia łącznika dla tego typu danych.

|Dane innych firm  |Zawieszenie w  postępowaniem sądowym|zbierania elektronicznych materiałów dowodowych  |Ustawienia przechowywania  |Zarządzanie rekordami  |Zgodność komunikacji  |Zarządzanie ryzykiem w niejawnym programie testów  |
|:---------|:---------|:---------|:---------|:---------|:---------|:---------|
|[CellTrust](archive-celltrust-data.md)|![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)||
|[Cisco Jabber na SQL](archive-ciscojabberonmssql-data.md)|![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)||
|[Cisco Jabber w oracle](archive-ciscojabberonoracle-data.md)|![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)||
|[Cisco Jabber on PostgreSQL](archive-ciscojabberonpostgresql-data.md)|![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)||
|[EML](archive-eml-data.md)|![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|||
|[FX Połączenie](archive-fxconnect-data.md)|![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)||
|[Jive](archive-jive-data.md)|![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)||
|[MS SQL Database](archive-mssqldatabaseimporter-data.md)|![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|||
|[Pivot](archive-pivot-data.md)|![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)||
|[Redtail Speak](archive-redtailspeak-data.md)|![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)||
|[Reuters Dealing](archive-reutersdealing-data.md)|![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)||
|[Reuters Eikon](archive-reuterseikon-data.md)|![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)||
|[Reuters FX](archive-reutersfx-data.md)|![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)||
|[RingCentral](archive-ringcentral-data.md)|![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)||
|[Czat usługi Salesforce](archive-salesforcechatter-data.md)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|||
|[ServiceNow](archive-servicenow-data.md)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|||
|[Skype dla firm](archive-skypeforbusiness-data.md)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)||
|[Slack eDiscovery](archive-slack-data.md)|![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)||
|[Nago](archive-symphony-data.md)|![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)||
|[Rozdzielany tekstem](archive-text-delimited-data.md)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|||
|[Twitter](archive-veritas-twitter-data.md)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|||
|[Webex Teams](archive-webexteams-data.md)|![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)||
|[Strony internetowe](archive-webpagecapture-data.md)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|||
|[Miejsce pracy z serwisu Facebook](archive-workplacefromfacebook-data.md)|![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)||
|[XIP](archive-xip-data.md)|![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)||
|[XSLT/XML](archive-xslt-xml-data.md)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|||
|[Yieldbroker](archive-yieldbroker-data.md)|![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)||
|[YouTube](archive-youtube-data.md)|![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|||
|[Powiększanie spotkań](archive-zoommeetings-data.md)     |![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)||
||||||||

### <a name="telemessage-data-connectors"></a>Łączniki danych TeleMessage

W tabeli w tej sekcji wymieniono łączniki danych innych firm dostępne w ramach współpracy z TeleMessage. W tabeli podsumowano również rozwiązania zgodności, które można zastosować do danych innych firm po zaimportowaniu i zarchiwizować je w Microsoft 365. Zobacz Omówienie [rozwiązań zgodności, które](#overview-of-compliance-solutions-that-support-third-party-data) obsługują dane innych firm, aby uzyskać bardziej szczegółowy opis poszczególnych rozwiązań do zgodności i informacje o tym, jak obsługuje ono dane innych firm.

Zanim będzie można zarchiwizować dane innych firm w usłudze Microsoft 365 musisz za pomocą telemessage skonfigurować ich usługę archiwizacji dla Twojej organizacji. Aby uzyskać więcej informacji, kliknij link w kolumnie  Dane innej firmy, aby przejść do instrukcji krok po kroku dotyczących tworzenia łącznika dla tego typu danych.

Łączniki danych TeleMessage są również dostępne w GCC środowiskach biznesowych w chmurze dla instytucji rządowych Microsoft 365 USA. Aby uzyskać więcej informacji, zobacz sekcję Łączniki [danych w sekcji dotyczącej](#data-connectors-in-the-us-government-cloud) chmury dla instytucji rządowych Stanów Zjednoczonych w tym artykule.

|Dane innych firm  |Zawieszenie w  postępowaniem sądowym|zbierania elektronicznych materiałów dowodowych  |Ustawienia przechowywania  |Zarządzanie rekordami  |Zgodność komunikacji  |Zarządzanie ryzykiem w niejawnym programie testów  |
|:---------|:---------|:---------|:---------|:---------|:---------|:---------|
|[Android](archive-android-archiver-data.md)     |![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)||
|[AT&T Network](archive-att-network-archiver-data.md)     |![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)||
|[Bell Network](archive-bell-network-data.md)     |![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)||
|[Enterprise numer telefonu](archive-enterprise-number-data.md)     |![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)||
|[O2 Network](archive-o2-network-data.md)     |![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)||
|[Grzegorzs Network](archive-rogers-network-archiver-data.md)|![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)||
|[Sygnał](archive-signal-archiver-data.md)|![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)||
|[Telegram](archive-telegram-archiver-data.md)|![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)||
|[TELUS Network](archive-telus-network-data.md)    |![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)||
|[Verizon Network](archive-verizon-network-data.md)     |![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)||
|[WeChat](archive-wechat-data.md)|![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)||
|[WhatsApp](archive-whatsapp-data.md)     |![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)||
||||||||

### <a name="17a-4-data-connectors"></a>Łączniki danych 17a-4

W tabeli w tej sekcji wymieniono łączniki danych innych firm dostępne w ramach współpracy z firmą 17a-4 LLC. W tabeli podsumowano również rozwiązania zgodności, które można zastosować do danych innych firm po zaimportowaniu i zarchiwizować je w Microsoft 365. Zobacz Omówienie [rozwiązań zgodności, które](#overview-of-compliance-solutions-that-support-third-party-data) obsługują dane innych firm, aby uzyskać bardziej szczegółowy opis poszczególnych rozwiązań do zgodności i informacje o tym, jak obsługuje ono dane innych firm.

Zanim będzie można zarchiwizować dane innych firm w usłudze Microsoft 365, musisz współpracować z 17a-4 LLC, aby skonfigurować ich usługę archiwizacji (o nazwie *DataParser*) dla Twojej organizacji. Aby uzyskać więcej informacji, kliknij link w kolumnie  Dane innej firmy, aby przejść do instrukcji krok po kroku dotyczących tworzenia łącznika dla tego typu danych.

Łączniki danych 17a–4 są również dostępne w GCC w chmurze dla instytucji rządowych Microsoft 365 Usa. Aby uzyskać więcej informacji, zobacz sekcję Łączniki [danych w sekcji dotyczącej](#data-connectors-in-the-us-government-cloud) chmury dla instytucji rządowych Stanów Zjednoczonych w tym artykule.

|Dane innych firm  |Zawieszenie w  postępowaniem sądowym|zbierania elektronicznych materiałów dowodowych  |Ustawienia przechowywania  |Zarządzanie rekordami  |Zgodność komunikacji  |Zarządzanie ryzykiem w niejawnym programie testów  |
|:---------|:---------|:---------|:---------|:---------|:---------|:---------|
|[BlackBerry](archive-17a-4-blackberry-data.md)     |![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)||
|[Bloomberg](archive-17a-4-bloomberg-data.md)     |![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)||
|[Cisco Jabber](archive-17a-4-cisco-jabber-data.md)   |![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)||
|[Cisco Webex](archive-17a-4-webex-teams-data.md)   |![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)||
|[FactSet](archive-17a-4-factset-data.md)    |![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)||
|[Fuze](archive-17a-4-fuze-data.md)    |![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)||
|[FX Połączenie](archive-17a-4-fxconnect-data.md)    |![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)||
|[ICE Chat](archive-17a-4-ice-im-data.md)    |![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)||
|[InvestEdge](archive-17a-4-investedge-data.md)    |![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)||
|[Chmura konwersacji LivePerson](archive-17a-4-liveperson-data.md)    |![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)||
|[Quip](archive-17a-4-quip-data.md)    |![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)||
|[Refinitiv Eikon Messenger](archive-17a-4-refinitiv-messenger-data.md)    |![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)||
|[ServiceNow](archive-17a-4-servicenow-data.md)    |![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)||
[Skype dla firm Server](archive-17a-4-skype-for-business-server-data.md)    |![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)||
|[Zapas czasu](archive-17a-4-slack-data.md)    |![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)||
|[SQL](archive-17a-4-sql-database-data.md)    |![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)||
|[Nago](archive-17a-4-symphony-data.md)    |![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)||
|[Powiększenie](archive-17a-4-zoom-data.md)    |![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)||
||||||||

### <a name="celltrust-data-connectors"></a>Łączniki danych cellTrust

W tabeli w tej sekcji wymieniono łącznik danych innej firmy dostępny w ramach współpracy z firmą CellTrust. W tabeli podsumowano również rozwiązania zgodności, które można zastosować do danych innych firm po zaimportowaniu i zarchiwizować je w Microsoft 365. Zobacz Omówienie [rozwiązań zgodności, które](#overview-of-compliance-solutions-that-support-third-party-data) obsługują dane innych firm, aby uzyskać bardziej szczegółowy opis poszczególnych rozwiązań do zgodności i informacje o tym, jak obsługuje ono dane innych firm.

Zanim będzie można zarchiwizować dane innych firm w programie Microsoft 365, musisz współpracować z cellTrust, aby skonfigurować ich usługę archiwizacji (*o nazwie CellTrust SL2*) dla twojej organizacji. Aby uzyskać więcej informacji, kliknij link w kolumnie  Dane innej firmy, aby przejść do instrukcji krok po kroku dotyczących tworzenia łącznika CellTrust SL2.

|Dane innych firm  |Zawieszenie w  postępowaniem sądowym|zbierania elektronicznych materiałów dowodowych  |Ustawienia przechowywania  |Zarządzanie rekordami  |Zgodność komunikacji  |Zarządzanie ryzykiem w niejawnym programie testów  |
|:---------|:---------|:---------|:---------|:---------|:---------|:---------|
|[CellTrust SL2](archive-data-from-celltrustsl2.md)     |![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)||
||||||||

Łącznik danych CellTrust SL2 jest również dostępny w GCC danych w chmurze firmy Microsoft Microsoft 365 Rząd Stanów Zjednoczonych. Aby uzyskać więcej informacji, zobacz sekcję Łączniki [danych w sekcji dotyczącej](#data-connectors-in-the-us-government-cloud) chmury dla instytucji rządowych Stanów Zjednoczonych w tym artykule.

## <a name="overview-of-compliance-solutions-that-support-third-party-data"></a>Omówienie rozwiązań zgodności, które obsługują dane innych firm

W poniższych sekcjach opisano niektóre rozwiązania zgodności Microsoft 365, które mogą ułatwić zarządzanie danymi innych firm wymienionymi w poprzedniej tabeli.

### <a name="litigation-hold"></a>Zawieszenie w  postępowaniem sądowym

Aby zachować dane [innych](create-a-litigation-hold.md) firm, należy umieścić w skrzynce pocztowej użytkownika postępowaniem sądowym. Podczas tworzenia blokowania można określić czas trwania blokowania (nazywany także holdm opartym na czasie), aby usunięte i zmodyfikowane dane innych firm zostały zachowane przez określony czas *, a następnie* trwale usunięte ze skrzynki pocztowej. Możesz też po prostu przechowywać zawartość przez czas nieograniczony ( *nazywany nieskończonym* zawieszeniem) lub do czasu usunięcia postępowania sądowego.

### <a name="ediscovery"></a>zbierania elektronicznych materiałów dowodowych

Trzy podstawowe narzędzia zbierania elektronicznych materiałów dowodowych w programie Microsoft 365 to Przeszukiwanie zawartości, Podstawowe zbierania elektronicznych materiałów dowodowych i Advanced eDiscovery.

- **[Wyszukiwanie zawartości](content-search.md).** Za pomocą narzędzia do przeszukiwania zawartości możesz wyszukiwać w skrzynkach pocztowych dane zaimportowanych przez inne firmy. Możesz zawęzić wyniki wyszukiwania i wyeksportować wyniki wyszukiwania za pomocą zapytań i warunków wyszukiwania.

- **[Podstawowe funkcje zbierania elektronicznych materiałów dowodowych](get-started-core-ediscovery.md).** To narzędzie bazuje na podstawowych funkcjach wyszukiwania i eksportu, umożliwiając tworzenie spraw, które pozwalają kontrolować, kto może uzyskać dostęp do danych sprawy, umieszczać w zawartości skrzynek pocztowych użytkowników lub skrzynki pocztowej, które spełniają kryteria wyszukiwania. Oznacza to, że możesz umieścić wstrzymanie zbierania elektronicznych materiałów dowodowych na danych innych firm, które zaimportowano do skrzynek pocztowych użytkowników.

- **[Advanced eDiscovery](overview-ediscovery-20.md).** To zaawansowane narzędzie rozszerza funkcjonalność funkcji zbierania elektronicznych materiałów dowodowych na sprawy, umożliwiając dodawanie osób do sprawy i umieszczanie danych osoby- opiekunów w stanie przechowywania, a następnie załadowanie danych innych osób do recenzji w celu dalszej analizy, takiej jak motywy czy wykrywanie duplikatów. Po załadowaniu danych innych firm do zestawu recenzji możesz utworzyć zapytanie i odfiltrować je do wąskiego zestawu wyników.

   Zarówno core eDiscovery, jak i Advanced eDiscovery umożliwiają zarządzanie danymi innych firm, które mogą być istotne dla dochodzenia prawnego lub wewnętrznego organizacji.

### <a name="retention-settings"></a>Ustawienia przechowywania

Zasady przechowywania można stosować [do](retention.md) skrzynek pocztowych użytkowników w celu przechowywania, a następnie usuwania danych innych firm (i innej zawartości skrzynek pocztowych) po wygaśnięciu okresu przechowywania. Przy użyciu zasad przechowywania można również usuwać dane innych firm określonego wieku lub uruchamiać recenzję usuwania po wygaśnięciu okresu przechowywania danych innych firm za pomocą etykiet przechowywania.[](disposition.md)

### <a name="records-management"></a>Zarządzanie rekordami

Funkcja [zarządzania rekordami](records-management.md) w Microsoft 365 umożliwia deklarowanie danych innych firm jako rekordu. Mogą to robić użytkownicy, którzy stosują etykietę przechowywania, która oznacza w swoich skrzynkach pocztowych dane innych firm jako rekord. Etykiety przechowywania można też stosować automatycznie, identyfikując informacje poufne, słowa kluczowe lub typy zawartości w danych innych firm.

### <a name="communication-compliance"></a>Zgodność komunikacji

Za pomocą funkcji [zgodności komunikacji](communication-compliance.md) możesz zbadać dane innych firm, aby upewnić się, że są zgodne ze standardami danych Twojej organizacji. Możesz to zrobić przez wykrywanie, przechwytywanie i podejmowanie działań naprawczych dla nieodpowiednich wiadomości w organizacji. Można na przykład monitorować importowane dane innych firm pod celu zapewnienia obraźliwego języka, informacji poufnych i zgodności z przepisami.

### <a name="insider-risk-management"></a>Zarządzanie ryzykiem w niejawnym programie testów

Sygnały z danych innych firm, takie jak selektywne dane HR, mogą być używane przez rozwiązanie [](insider-risk-management.md) do zarządzania ryzykiem w ramach niejawnego programu testów w celu zminimalizowania ryzyka wewnętrznego, pozwalając na wykrywanie, badanie i działanie na ryzykowne działania w organizacji. Dane zaimportowane za pomocą łącznika danych hr są na przykład używane jako wskaźniki ryzyka w celu wykrywania kradzieży danych pracowników.

## <a name="using-ediscovery-tools-to-search-for-third-party-data"></a>Korzystanie z narzędzi zbierania elektronicznych materiałów dowodowych do wyszukiwania danych innych firm

Po zaimportowaniu i zarchiwizowania danych innych firm w skrzynkach pocztowych użytkowników za pomocą łączników danych można wyszukiwać dane innych firm za pomocą narzędzi zbierania elektronicznych materiałów dowodowych w programie Microsoft 365. Możesz również korzystać z narzędzi zbierania elektronicznych materiałów dowodowych w celu tworzenia opartych na zapytaniach zbierania elektronicznych materiałów dowodowych i zbierania elektronicznych materiałów dowodowych Advanced eDiscovery w celu zachowania danych innych firm. Aby uzyskać więcej informacji na temat narzędzi zbierania elektronicznych materiałów dowodowych, zobacz [Rozwiązania zbierania elektronicznych materiałów dowodowych w programie Microsoft 365](ediscovery.md).

Aby wyszukać (lub przytrzymać) dowolny typ danych innych firm zaimportowanych do skrzynek pocztowych użytkowników za pomocą łącznika danych, możesz użyć następującego zapytania wyszukiwania. Pamiętaj, aby zawęcić zakres wyszukiwania do skrzynek pocztowych użytkowników.

```powershell
kind:externaldata
```

Tego zapytania można użyć w polu Słowa  kluczowe w celu przeszukiwania zawartości, wyszukiwania skojarzonego z podstawową sprawą zbierania elektronicznych materiałów dowodowych lub kolekcji w Advanced eDiscovery.

![Zapytanie wyszukuje dane innych firm.](..\media\SearchThirdPartyData1.png)

Zawęzić `kind:externaldata` zakres wyszukiwania do danych innych firm możesz również użyć pary property:value. Aby na przykład wyszukać elementy zaimportowane z dowolnego źródła danych innej firmy, które zawierają wyraz *contoso* we właściwości **Temat** importowanego elementu, użyj następującego zapytania w polu Słowa **kluczowe** :

```powershell
subject:contoso AND kind:externaldata
```

Możesz również użyć warunku **typu wiadomości,** aby skonfigurować to samo zapytanie.

![Użyj warunku typu wiadomości, aby zawęzić wyszukiwania do danych innych firm.](..\media\SearchThirdPartyData2.png)

Aby wyszukać określony typ zarchiwizowane dane innych firm, użyj właściwości **skrzynki** pocztowej klasy elementów w zapytaniu wyszukiwania. Użyj następującej właściwości:format wartości:

```powershell
itemclass:ipm.externaldata.<third-party data type>
```

Każdy element zaimportowany przez łącznik danych innej firmy zawiera właściwość **itemclass** (Klasyfikacja elementów) z wartością odpowiadającą typowi danych innej firmy. Aby na przykład wyszukać dane serwisu Facebook zawierające wyraz *contoso*, we właściwości **Temat** importowanego elementu użyj następującego zapytania:

```powershell
subject:contoso AND itemclass:ipm.externaldata.facebook*
```

Oto kilka przykładów wartości **klasy elementów** dla różnych typów danych innych firm.

| **Typ danych innej firmy** | **Wartość właściwości itemclass**   |
|---------------------------|-------------------------------------|
| Wiadomość bloomberga         | ipm.externaldata.bloombergmessage* |
| CellTrust                 | ipm.externaldata.celltrust*        |
| Pivot                     | ipm.externaldata.pivot*            |
| WhatsApp Archiver         | ipm.externaldata.whatsapparchiver* |
|||

W wartościach *właściwości itemclass* nie jest wielkość liter. Ogólnie należy użyć nazwy typu danych innej firmy (bez spacji), po której następuje symbol wieloznaczny ( * ).

Aby uzyskać więcej informacji na temat tworzenia zapytań wyszukiwania zbierania elektronicznych materiałów dowodowych, zobacz Zapytania słów kluczowych i warunki wyszukiwania [dotyczące zbierania elektronicznych materiałów dowodowych](keyword-queries-and-search-conditions.md).

## <a name="data-connectors-in-the-us-government-cloud"></a>Łączniki danych w chmurze dla instytucji rządowych Stanów Zjednoczonych

Niektóre łączniki danych są dostępne w chmurze dla instytucji rządowych Stanów Zjednoczonych. Poniższe sekcje wskazują konkretne środowiska rządowe, które obsługują łączniki danych innych firm. Aby uzyskać więcej informacji na temat chmur dla instytucji rządowych Stanów Zjednoczonych, [zobacz Microsoft 365 rząd Stanów Zjednoczonych](/office365/servicedescriptions/office-365-platform-service-description/office-365-us-government/microsoft-365-government-how-to-buy).

### <a name="veritas-data-connectors-in-the-us-government-cloud-preview"></a>Łączniki danych usługi Veritas w chmurze dla instytucji rządowych Stanów Zjednoczonych (wersja zapoznawcza)

|Łącznik danych  |GCC  |GCC wysoki  |DoD  |
|:---------|:---------|:---------|:---------|
|CellTrust| Tak | Nie | Nie |
|Cisco Jabber na SQL| Tak | Nie | Nie |
|Cisco Jabber w oracle| Tak | Nie | Nie |
|Cisco Jabber on PostgreSQL| Tak | Nie | Nie |
|EML| Tak | Nie | Nie |
|FX Połączenie| Tak | Nie | Nie |
|Jive| Tak | Nie | Nie |
|MS SQL Database| Tak | Nie | Nie |
|Pivot| Tak | Nie | Nie |
|Redtail Speak| Tak | Nie | Nie |
|Reuters Dealing| Tak | Nie | Nie |
|Reuters Eikon| Tak | Nie | Nie |
|Reuters FX| Tak | Nie | Nie |
|RingCentral| Tak | Nie | Nie |
|Czat usługi Salesforce| Tak | Nie | Nie |
|ServiceNow| Tak | Nie | Nie |
|Skype dla firm| Tak | Nie | Nie |
|Slack eDiscovery| Tak | Nie | Nie |
|Nago| Tak | Nie | Nie |
|Rozdzielany tekstem| Tak | Nie | Nie |
|Twitter| Tak | Nie | Nie |
|Webex Teams| Tak | Nie | Nie |
|Strony internetowe| Tak | Nie | Nie |
|Miejsce pracy z serwisu Facebook| Tak | Nie | Nie |
|XIP| Tak | Nie | Nie |
|XSLT/XML| Tak | Nie | Nie |
|Yieldbroker| Tak | Nie | Nie |
|YouTube| Nie | Nie | Nie |
|Powiększanie spotkań| Tak | Nie | Nie |
|||||

### <a name="telemessage-data-connectors-in-the-us-government-cloud"></a>Łączniki danych teleMessage w chmurze dla instytucji rządowych Stanów Zjednoczonych

|Łącznik danych  |GCC  |GCC wysoki  |DoD  |
|:---------|:---------|:---------|:---------|
|Archiwum systemu Android | Tak | Nie | Nie |
|AT&WIADOMOŚCI SMS/MMS Network Archiver | Tak | Nie | Nie |
|Bell SMS/MMS Network Archiver | Tak | Nie | Nie |
|Enterprise archiwum liczb | Tak | Nie | Nie |
|O2 SMS and Voice Network Archiver | Tak         | Nie | Nie |
|Grzegorzs Network Archiver | Tak         | Nie | Nie |
|Archiver sygnału | Tak | Nie | Nie |
|Archiwum telegramu | Tak | Nie | Nie |
|TELUS SMS Network Archiver | Tak | Nie | Nie |
|Verizon SMS/MMS Network Archiver | Tak | Nie | Nie |
|WeChat Archiver | Tak | Nie | Nie |
|WhatsApp Archiver | Tak | Nie | Nie |
|||||

### <a name="17a-4-data-connectors-in-the-us-government-cloud"></a>Łączniki danych 17a-4 w chmurze dla instytucji rządowych Stanów Zjednoczonych

|Łącznik danych  |GCC  |GCC wysoki  |DoD  |
|:---------|:---------|:---------|:---------|
|BlackBerry DataParser | Tak | Nie | Nie |
|Bloomberg DataParser  | Tak | Nie | Nie |
|Cisco Jabber DataParser  | Tak | Nie | Nie |
|Cisco Webex DataParser  | Tak | Nie | Nie |
|FactSet DataParser  | Tak | Nie | Nie |
|Fuze DataParser  | Tak | Nie | Nie |
|FX Połączenie DataParser  | Tak | Nie | Nie |
|ICE DataParser  | Tak | Nie | Nie |
|InvestEdge DataParser  | Tak | Nie | Nie |
|LivePerson Conversational Cloud DataParser  | Tak | Nie | Nie |
|Quip DataParser  | Tak | Nie | Nie |
|Refinitiv Eikon Messenger DataParser  | Tak | Nie | Nie |
|ServiceNow DataParser  | Tak | Nie | Nie |
|Skype dla firm Server DataParser | Tak | Nie | Nie |
|Slack DataParser | Tak | Nie | Nie |
|SQL DataParser  | Tak | Nie | Nie |
|Namysłowy DataParser | Tak | Nie | Nie |
|Zoom DataParser | Tak | Nie | Nie |
|||||

### <a name="celltrust-data-connectors-in-the-us-government-cloud"></a>Łączniki danych firmy CellTrust w chmurze dla instytucji rządowych Stanów Zjednoczonych

|Łącznik danych  |GCC  |GCC wysoki  |DoD  |
|:---------|:---------|:---------|:---------|
|CellTrust SL2 | Tak | Nie | Nie |
|||||

## <a name="working-with-a-microsoft-partner-to-archive-third-party-data"></a>Współpraca z partnerem firmy Microsoft w celu archiwizowania danych innych firm

Inną opcją importowania i archiwizowania danych innych firm jest współpraca organizacji z partnerem firmy Microsoft. Jeśli łączniki danych innych firm nie są obsługiwane przez łączniki danych dostępne w Centrum zgodności firmy Microsoft, możesz współpracować z partnerem, który może udostępnić łącznik niestandardowy, który będzie konfigurowany w celu regularnego wyodrębniania elementów ze źródła danych innej firmy, a następnie łączenia się z chmurą firmy Microsoft przy użyciu interfejsu API innej firmy i importowania tych elementów do usługi Microsoft 365. Łącznik partnera konwertuje również zawartość elementu ze źródła danych innej firmy na wiadomość e-mail, a następnie importuje go do skrzynki pocztowej w u Microsoft 365.

Aby uzyskać listę partnerów, z których możesz współpracować, oraz proces krok po kroku dla tej metody, zobacz Współpraca z partnerem w celu archiwizowania danych innych [firm w programie Microsoft 365](work-with-partner-to-archive-third-party-data.md).
