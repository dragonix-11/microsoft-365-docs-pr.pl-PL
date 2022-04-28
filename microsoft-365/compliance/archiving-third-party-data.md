---
title: Importowanie i archiwizowanie danych innych firm w Microsoft 365 przy użyciu łączników danych
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
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
description: Dowiedz się, jak importować i archiwizować dane innych firm z platform mediów społecznościowych, platform wiadomości błyskawicznych i platform współpracy dokumentów w celu Microsoft 365 skrzynek pocztowych.
ms.openlocfilehash: 75a1136c38c0b893babd1cd349dbe34aa9bbf8cd
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65093575"
---
# <a name="learn-about-connectors-for-third-party-data"></a>Dowiedz się więcej o łącznikach dla danych innych firm

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Microsoft 365 umożliwia administratorom używanie łączników danych do importowania i archiwizowania danych innych firm z platform mediów społecznościowych, platform wiadomości błyskawicznych i platform współpracy dokumentów do skrzynek pocztowych w organizacji Microsoft 365. Jedną z głównych zalet importowania i archiwizowania danych innych firm w Microsoft 365 jest zastosowanie różnych rozwiązań usługi Microsoft Purview do danych po ich zaimportowaniu. Dzięki temu możesz upewnić się, że dane organizacji spoza firmy Microsoft są zgodne z przepisami i standardami, które mają wpływ na organizację.

Obejrzyj ten interaktywny przewodnik pokazujący sposób tworzenia łączników danych do importowania i archiwizowania danych innych firm oraz przykłady stosowania rozwiązań zgodności do danych po ich zaimportowaniu do Microsoft 365.

> [!VIDEO https://mslearn.cloudguides.com/guides/Archive%20data%20from%20non-Microsoft%20sources%20in%20Microsoft%20365]

## <a name="third-party-data-connectors"></a>Łączniki danych innych firm

Portal zgodności usługi Microsoft Purview udostępnia natywne łączniki danych innych firm od firmy Microsoft do importowania danych z różnych źródeł danych, takich jak LinkedIn, Instant Bloomberg i Twitter oraz łączniki danych, które obsługują rozwiązanie do zarządzania ryzykiem wewnętrznym. Oprócz tych łączników danych firma Microsoft współpracuje z następującymi partnerami, aby udostępnić o wiele więcej łączników danych trzeciej części w portalu zgodności. Twoja organizacja współpracuje z tymi partnerami w celu skonfigurowania usługi archiwizacji przed utworzeniem odpowiedniego łącznika danych w portalu zgodności.

- [Veritas](#veritas-data-connectors)

- [TeleMessage](#telemessage-data-connectors)

- [17a-4 LLC](#17a-4-data-connectors)

- [CellTrust](#celltrust-data-connectors)

Dane innych firm wymienione w następnych sekcjach (z wyjątkiem danych hr i fizycznych danych nieprawidłowych zabezpieczeń używanych w rozwiązaniu do zarządzania ryzykiem Microsoft 365 niejawnych testerów) są importowane do skrzynek pocztowych użytkowników. Rozwiązania usługi Microsoft Purview obsługujące dane innych firm są stosowane do skrzynki pocztowej użytkownika, w której są przechowywane dane.

### <a name="microsoft-data-connectors"></a>Łączniki danych firmy Microsoft

Poniższa tabela zawiera listę natywnych łączników danych innych firm dostępnych w portalu zgodności. Tabela zawiera również podsumowanie rozwiązań zgodności, które można zastosować po zaimportowaniu i zarchiwizowaniu danych innych firm w Microsoft 365. Zobacz [sekcję Omówienie rozwiązań zgodności, które obsługują dane innych firm](#overview-of-compliance-solutions-that-support-third-party-data) , aby uzyskać bardziej szczegółowy opis każdego rozwiązania zgodności i sposobu obsługi danych innych firm.

Kliknij link w kolumnie **Dane innych firm** , aby przejść do instrukcji krok po kroku dotyczących tworzenia łącznika dla tego typu danych.

|Dane innych firm  |Wstrzymanie postępowania sądowego|Zbierania elektronicznych materiałów dowodowych  |Ustawienia przechowywania  |Zarządzanie rekordami  |Zgodność w komunikacji  |Zarządzanie ryzykiem wewnętrznym  |
|:---------|:---------|:---------|:---------|:---------|:---------|:---------|
|[Wiadomość serwisu Bloomberg](archive-bloomberg-message-data.md)     |![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru.](../media/checkmark.png)||
|[Epic EHR healthcare](import-epic-data.md) ||||||![Znacznik wyboru](../media/checkmark.png)|
|[Facebook](archive-facebook-data-with-sample-connector.md)     |![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|||
|[Ogólna opieka zdrowotna EHR](import-healthcare-data.md) ||||||![Znacznik wyboru](../media/checkmark.png)|
|[Kadry (HR)](import-hr-data.md) ||||||![Znacznik wyboru](../media/checkmark.png)|
|[Czat ICE](archive-icechat-data.md)     |![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)||
|[Instant Bloomberg](archive-instant-bloomberg-data.md)|![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)||
|[LinkedIn](archive-linkedin-data.md)   |![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|||
|[Fizyczne badging](import-physical-badging-data.md) ||||||![Znacznik wyboru](../media/checkmark.png)|
|[Slack eDiscovery](archive-slack-data-microsoft.md)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)||
|[Twitter](archive-twitter-data-with-sample-connector.md)     |![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|||
||||||||

### <a name="veritas-data-connectors"></a>Łączniki danych Veritas

Tabela w tej sekcji zawiera listę łączników danych innych firm dostępnych we współpracy z platformą Veritas. Tabela zawiera również podsumowanie rozwiązań zgodności, które można zastosować do danych innych firm po zaimportowaniu i zarchiwizowaniu ich w Microsoft 365. Zobacz [sekcję Omówienie rozwiązań zgodności, które obsługują dane innych firm](#overview-of-compliance-solutions-that-support-third-party-data) , aby uzyskać bardziej szczegółowy opis każdego rozwiązania zgodności i sposobu obsługi danych innych firm.

Zanim będzie można archiwizować dane innych firm w Microsoft 365, musisz współpracować z usługą Veritas, aby skonfigurować ich usługę archiwizacji (o nazwie *Merge1*) dla swojej organizacji. Aby uzyskać więcej informacji, kliknij link w kolumnie **Danych innych firm** , aby przejść do instrukcji krok po kroku dotyczących tworzenia łącznika dla tego typu danych.

|Dane innych firm  |Wstrzymanie postępowania sądowego|Zbierania elektronicznych materiałów dowodowych  |Ustawienia przechowywania  |Zarządzanie rekordami  |Zgodność w komunikacji  |Zarządzanie ryzykiem wewnętrznym  |
|:---------|:---------|:---------|:---------|:---------|:---------|:---------|
|[CellTrust](archive-celltrust-data.md)|![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)||
|[Cisco Jabber w witrynie MS SQL](archive-ciscojabberonmssql-data.md)|![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)||
|[Cisco Jabber w systemie Oracle](archive-ciscojabberonoracle-data.md)|![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)||
|[Cisco Jabber w usłudze PostgreSQL](archive-ciscojabberonpostgresql-data.md)|![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)||
|[EML](archive-eml-data.md)|![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|||
|[FX Connect](archive-fxconnect-data.md)|![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)||
|[Jive](archive-jive-data.md)|![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)||
|[Baza danych MS SQL](archive-mssqldatabaseimporter-data.md)|![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|||
|[Dokument bazowy](archive-pivot-data.md)|![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)||
|[Redtail Speak](archive-redtailspeak-data.md)|![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)||
|[Reuters Dealing](archive-reutersdealing-data.md)|![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)||
|[Reuters Eikon](archive-reuterseikon-data.md)|![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)||
|[Reuters FX](archive-reutersfx-data.md)|![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)||
|[RingCentral](archive-ringcentral-data.md)|![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)||
|[Czat w usłudze Salesforce](archive-salesforcechatter-data.md)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|||
|[ServiceNow](archive-servicenow-data.md)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|||
|[Skype dla firm](archive-skypeforbusiness-data.md)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)||
|[Slack eDiscovery](archive-slack-data.md)|![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)||
|[Symphony](archive-symphony-data.md)|![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)||
|[Rozdzielany tekstem](archive-text-delimited-data.md)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|||
|[Twitter](archive-veritas-twitter-data.md)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|||
|[Webex Teams](archive-webexteams-data.md)|![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)||
|[Strony internetowe](archive-webpagecapture-data.md)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|||
|[Miejsce pracy z serwisu Facebook](archive-workplacefromfacebook-data.md)|![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)||
|[XIP](archive-xip-data.md)|![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)||
|[XSLT/XML](archive-xslt-xml-data.md)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|||
|[Yieldbroker](archive-yieldbroker-data.md)|![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)||
|[YouTube](archive-youtube-data.md)|![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|||
|[Spotkania w usłudze Zoom](archive-zoommeetings-data.md)     |![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)||
||||||||

### <a name="telemessage-data-connectors"></a>Łączniki danych TeleMessage

Tabela w tej sekcji zawiera listę łączników danych innych firm dostępnych we współpracy z usługą TeleMessage. Tabela zawiera również podsumowanie rozwiązań zgodności, które można zastosować do danych innych firm po zaimportowaniu i zarchiwizowaniu ich w Microsoft 365. Zobacz [sekcję Omówienie rozwiązań zgodności, które obsługują dane innych firm](#overview-of-compliance-solutions-that-support-third-party-data) , aby uzyskać bardziej szczegółowy opis każdego rozwiązania zgodności i sposobu obsługi danych innych firm.

Aby można było zarchiwizować dane innych firm w Microsoft 365, musisz współpracować z usługą TeleMessage, aby skonfigurować ich usługę archiwizacji dla organizacji. Aby uzyskać więcej informacji, kliknij link w kolumnie **Danych innych firm** , aby przejść do instrukcji krok po kroku dotyczących tworzenia łącznika dla tego typu danych.

Łączniki danych telemessage są również dostępne w środowiskach GCC w chmurze Microsoft 365 US Government. Aby uzyskać więcej informacji, zobacz sekcję [Łączniki danych w chmurze dla instytucji rządowych USA](#data-connectors-in-the-us-government-cloud) w tym artykule.

|Dane innych firm  |Wstrzymanie postępowania sądowego|Zbierania elektronicznych materiałów dowodowych  |Ustawienia przechowywania  |Zarządzanie rekordami  |Zgodność w komunikacji  |Zarządzanie ryzykiem wewnętrznym  |
|:---------|:---------|:---------|:---------|:---------|:---------|:---------|
|[Android](archive-android-archiver-data.md)     |![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)||
|[AT&T Network](archive-att-network-archiver-data.md)     |![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)||
|[Sieć dzwonów](archive-bell-network-data.md)     |![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)||
|[numer Enterprise](archive-enterprise-number-data.md)     |![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)||
|[Sieć O2](archive-o2-network-data.md)     |![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)||
|[Rogers Network](archive-rogers-network-archiver-data.md)|![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)||
|[Sygnału](archive-signal-archiver-data.md)|![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)||
|[Telegram](archive-telegram-archiver-data.md)|![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)||
|[Sieć TELUS](archive-telus-network-data.md)    |![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)||
|[Sieć Verizon](archive-verizon-network-data.md)     |![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)||
|[Wechat](archive-wechat-data.md)|![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)||
|[Whatsapp](archive-whatsapp-data.md)     |![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)||
||||||||

### <a name="17a-4-data-connectors"></a>Łączniki danych 17a-4

Tabela w tej sekcji zawiera listę łączników danych innych firm dostępnych we współpracy z firmą 17a-4 LLC. Tabela zawiera również podsumowanie rozwiązań zgodności, które można zastosować do danych innych firm po zaimportowaniu i zarchiwizowaniu ich w Microsoft 365. Zobacz [sekcję Omówienie rozwiązań zgodności, które obsługują dane innych firm](#overview-of-compliance-solutions-that-support-third-party-data) , aby uzyskać bardziej szczegółowy opis każdego rozwiązania zgodności i sposobu obsługi danych innych firm.

Zanim będzie można archiwizować dane innych firm w Microsoft 365, musisz współpracować z firmą 17a-4 LLC, aby skonfigurować ich usługę archiwizacji (o nazwie *DataParser*) dla swojej organizacji. Aby uzyskać więcej informacji, kliknij link w kolumnie **Danych innych firm** , aby przejść do instrukcji krok po kroku dotyczących tworzenia łącznika dla tego typu danych.

Łączniki danych 17a-4 są również dostępne w środowiskach GCC w chmurze Microsoft 365 US Government. Aby uzyskać więcej informacji, zobacz sekcję [Łączniki danych w chmurze dla instytucji rządowych USA](#data-connectors-in-the-us-government-cloud) w tym artykule.

|Dane innych firm  |Wstrzymanie postępowania sądowego|Zbierania elektronicznych materiałów dowodowych  |Ustawienia przechowywania  |Zarządzanie rekordami  |Zgodność w komunikacji  |Zarządzanie ryzykiem wewnętrznym  |
|:---------|:---------|:---------|:---------|:---------|:---------|:---------|
|[Blackberry](archive-17a-4-blackberry-data.md)     |![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)||
|[Bloomberg](archive-17a-4-bloomberg-data.md)     |![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)||
|[Cisco Jabber](archive-17a-4-cisco-jabber-data.md)   |![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)||
|[Cisco Webex](archive-17a-4-webex-teams-data.md)   |![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)||
|[FactSet](archive-17a-4-factset-data.md)    |![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)||
|[Fuze](archive-17a-4-fuze-data.md)    |![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)||
|[FX Connect](archive-17a-4-fxconnect-data.md)    |![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)||
|[Czat ICE](archive-17a-4-ice-im-data.md)    |![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)||
|[InvestEdge](archive-17a-4-investedge-data.md)    |![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)||
|[Chmura konwersacyjna LivePerson](archive-17a-4-liveperson-data.md)    |![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)||
|[Quip](archive-17a-4-quip-data.md)    |![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)||
|[Komunikator Refinitiv Eikon](archive-17a-4-refinitiv-messenger-data.md)    |![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)||
|[ServiceNow](archive-17a-4-servicenow-data.md)    |![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)||
[Skype dla firm Server](archive-17a-4-skype-for-business-server-data.md)    |![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)||
|[Luzu](archive-17a-4-slack-data.md)    |![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)||
|[SQL](archive-17a-4-sql-database-data.md)    |![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)||
|[Symphony](archive-17a-4-symphony-data.md)    |![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)||
|[Powiększenia](archive-17a-4-zoom-data.md)    |![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)||
||||||||

### <a name="celltrust-data-connectors"></a>Łączniki danych CellTrust

Tabela w tej sekcji zawiera listę łącznika danych innej firmy dostępnego we współpracy z usługą CellTrust. Tabela zawiera również podsumowanie rozwiązań zgodności, które można zastosować do danych innych firm po zaimportowaniu i zarchiwizowaniu ich w Microsoft 365. Zobacz [sekcję Omówienie rozwiązań zgodności, które obsługują dane innych firm](#overview-of-compliance-solutions-that-support-third-party-data) , aby uzyskać bardziej szczegółowy opis każdego rozwiązania zgodności i sposobu obsługi danych innych firm.

Przed zarchiwizowaniem danych innych firm w Microsoft 365 musisz współpracować z aplikacją CellTrust, aby skonfigurować ich usługę archiwizacji (o nazwie *CellTrust SL2*) dla swojej organizacji. Aby uzyskać więcej informacji, kliknij link w kolumnie **Danych innych firm** , aby przejść do instrukcji krok po kroku dotyczących tworzenia łącznika CellTrust SL2.

|Dane innych firm  |Wstrzymanie postępowania sądowego|Zbierania elektronicznych materiałów dowodowych  |Ustawienia przechowywania  |Zarządzanie rekordami  |Zgodność w komunikacji  |Zarządzanie ryzykiem wewnętrznym  |
|:---------|:---------|:---------|:---------|:---------|:---------|:---------|
|[CellTrust SL2](archive-data-from-celltrustsl2.md)     |![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)||
||||||||

Łącznik danych CellTrust SL2 jest również dostępny w środowiskach GCC w chmurze Microsoft 365 US Government. Aby uzyskać więcej informacji, zobacz sekcję [Łączniki danych w chmurze dla instytucji rządowych USA](#data-connectors-in-the-us-government-cloud) w tym artykule.

## <a name="overview-of-compliance-solutions-that-support-third-party-data"></a>Omówienie rozwiązań zgodności, które obsługują dane innych firm

W poniższych sekcjach opisano niektóre z elementów, które rozwiązania Microsoft Purview mogą pomóc w zarządzaniu danymi innych firm wymienionymi w poprzedniej tabeli.

### <a name="litigation-hold"></a>Wstrzymanie postępowania sądowego

Aby zachować dane innych firm, należy [wstrzymać postępowanie sądowe](create-a-litigation-hold.md) w skrzynce pocztowej użytkownika. Podczas tworzenia blokady można określić czas przechowywania (nazywany również *blokadą czasową*), aby usunięte i zmodyfikowane dane innych firm były przechowywane przez określony okres, a następnie trwale usuwane ze skrzynki pocztowej. Możesz też zachować zawartość przez czas nieokreślony (nazywaną *nieskończoną blokadą*) lub do momentu usunięcia blokady postępowania sądowego.

### <a name="ediscovery"></a>Zbierania elektronicznych materiałów dowodowych

Trzy podstawowe narzędzia zbierania elektronicznych elektronicznych materiałów dowodowych w Microsoft 365 to wyszukiwanie zawartości, microsoft Purview eDiscovery (Standard) i microsoft Purview eDiscovery (Premium).

- **[Wyszukiwanie zawartości](content-search.md).** Za pomocą narzędzia do wyszukiwania zawartości można wyszukiwać skrzynki pocztowe w poszukiwaniu zaimportowanych danych innych firm. Możesz użyć zapytań wyszukiwania i warunków, aby zawęzić wyniki wyszukiwania i wyeksportować wyniki wyszukiwania.

- **[eDiscovery (Standard)](get-started-core-ediscovery.md).** To narzędzie bazuje na podstawowych funkcjach wyszukiwania i eksportowania, umożliwiając tworzenie przypadków, które umożliwiają kontrolowanie, kto może uzyskiwać dostęp do danych przypadków, umieszczać blokady w skrzynkach pocztowych użytkowników lub zawartości skrzynki pocztowej zgodnej z kryteriami wyszukiwania. Oznacza to, że możesz wstrzymać zbieranie elektronicznych materiałów dowodowych na danych innych firm, które zostały zaimportowane do skrzynek pocztowych użytkowników.

- **[eDiscovery (Premium)](overview-ediscovery-20.md).** To zaawansowane narzędzie rozszerza funkcjonalność przypadków zbierania elektronicznych materiałów dowodowych (Standard), umożliwiając dodawanie opiekunów do sprawy, umieszczanie danych opiekuna w zawieszeniu, a następnie ładowanie danych innych firm opiekuna do przeglądu w celu dalszej analizy, takiej jak motywy i wykrywanie duplikatów. Po załadowaniu danych innych firm do zestawu przeglądów można wykonywać zapytania i filtrować je do wąskiego zestawu wyników.

   Zarówno eDiscovery (Standard) jak i eDiscovery (Premium) umożliwiają zarządzanie danymi innych firm, które mogą być istotne dla dochodzeń prawnych lub wewnętrznych twojej organizacji.

### <a name="retention-settings"></a>Ustawienia przechowywania

Zasady [przechowywania](retention.md) można zastosować do skrzynek pocztowych użytkowników, aby zachować, a następnie usunąć dane innych firm (i inną zawartość skrzynki pocztowej) po upływie okresu przechowywania. Możesz również użyć zasad przechowywania, aby usunąć dane innych firm w określonym wieku lub [użyć etykiet przechowywania, aby wyzwolić przegląd dyspozycji](disposition.md) po upływie okresu przechowywania danych innych firm.

### <a name="records-management"></a>Zarządzanie rekordami

Funkcja [zarządzania rekordami](records-management.md) w Microsoft 365 umożliwia deklarowanie danych innych firm jako rekordu. Można to zrobić ręcznie przez użytkowników, którzy stosują etykietę przechowywania, która oznacza dane innych firm w skrzynce pocztowej jako rekord. Możesz też automatycznie stosować etykiety przechowywania, identyfikując poufne informacje, słowa kluczowe lub typy zawartości w danych innych firm.

### <a name="communication-compliance"></a>Zgodność w komunikacji

Aby sprawdzić dane innych firm, możesz użyć [zgodności z komunikacją](communication-compliance.md) , aby upewnić się, że są zgodne ze standardami danych organizacji. Możesz to zrobić, wykrywając, przechwytując i podejmując akcje korygowania nieodpowiednich komunikatów w organizacji. Można na przykład monitorować importowane dane innych firm pod kątem obraźliwego języka, informacji poufnych i zgodności z przepisami.

### <a name="insider-risk-management"></a>Zarządzanie ryzykiem wewnętrznym

Sygnały z danych innych firm, takie jak selektywne dane kadrowe, mogą być używane przez rozwiązanie do [zarządzania ryzykiem wewnętrznym](insider-risk-management.md) , aby zminimalizować ryzyko wewnętrzne, umożliwiając wykrywanie, badanie i działanie na ryzykownych działaniach w organizacji. Na przykład dane zaimportowane przez łącznik danych HR są używane jako wskaźniki ryzyka ułatwiające wykrywanie kradzieży danych odchodzących pracowników.

## <a name="using-ediscovery-tools-to-search-for-third-party-data"></a>Wyszukiwanie danych innych firm przy użyciu narzędzi zbierania elektronicznych materiałów dowodowych

Po użyciu łączników danych do importowania i archiwizowania danych innych firm w skrzynkach pocztowych użytkowników można wyszukiwać dane innych firm za pomocą narzędzi Microsoft 365 do zbierania elektronicznych materiałów dowodowych. Narzędzia zbierania elektronicznych materiałów dowodowych umożliwiają również tworzenie blokad opartych na zapytaniach skojarzonych z przypadkami zbierania elektronicznych materiałów dowodowych (Standard) i eDiscovery (Premium) w celu zachowania danych innych firm. Aby uzyskać więcej informacji na temat narzędzi zbierania elektronicznych materiałów dowodowych, zobacz rozwiązania zbierania [elektronicznych materiałów dowodowych w Microsoft 365](ediscovery.md).

Aby wyszukać (lub wstrzymać) dowolny typ danych innych firm zaimportowanych do skrzynek pocztowych użytkownika przy użyciu łącznika danych, możesz użyć następującego zapytania wyszukiwania. Pamiętaj, aby zakres wyszukiwania do skrzynek pocztowych użytkownika.

```powershell
kind:externaldata
```

Tego zapytania można użyć w polu **Słowa kluczowe** dla wyszukiwania zawartości, wyszukiwania skojarzonego ze sprawą zbierania elektronicznych materiałów dowodowych (Standardowa) lub kolekcji zbierania elektronicznych materiałów dowodowych (Premium).

![Zapytanie w celu wyszukania danych innych firm.](..\media\SearchThirdPartyData1.png)

Możesz również użyć `kind:externaldata` pary property:value, aby zawęzić zakres wyszukiwań do danych innych firm. Aby na przykład wyszukać elementy zaimportowane z dowolnego źródła danych innej firmy, które zawierają słowo *contoso* we właściwości **Podmiot** zaimportowanego elementu, użyj następującego zapytania w polu **Słowa kluczowe** :

```powershell
subject:contoso AND kind:externaldata
```

Alternatywnie możesz użyć warunku **Rodzaju komunikatu** , aby skonfigurować to samo zapytanie.

![Użyj warunku rodzaju komunikatu, aby zawęzić wyszukiwania do danych innych firm.](..\media\SearchThirdPartyData2.png)

Aby wyszukać określony typ zarchiwizowanego danych innej firmy, użyj właściwości skrzynki pocztowej **klasy itemclass** w zapytaniu wyszukiwania. Użyj następującego formatu property:value:

```powershell
itemclass:ipm.externaldata.<third-party data type>
```

Każdy element zaimportowany przez łącznik danych innej firmy zawiera właściwość **itemclass** z wartością odpowiadającą typowi danych innej firmy. Aby na przykład wyszukać dane serwisu Facebook zawierające słowo *contoso*, we właściwości **Podmiot** zaimportowanego elementu użyj następującego zapytania:

```powershell
subject:contoso AND itemclass:ipm.externaldata.facebook*
```

Oto kilka przykładów wartości **klasy itemclass** dla różnych typów danych innych firm.

| **Typ danych innych firm** | **Wartość właściwości itemclass**   |
|---------------------------|-------------------------------------|
| Wiadomość serwisu Bloomberg         | ipm.externaldata.bloombergmessage* |
| CellTrust                 | ipm.externaldata.celltrust*        |
| Dokument bazowy                     | ipm.externaldata.pivot*            |
| Archiwizator usługi WhatsApp         | ipm.externaldata.whatsapparchiver* |
|||

Wartości właściwości *itemclass* nie uwzględniają wielkości liter. Ogólnie rzecz biorąc, użyj nazwy typu danych innej firmy (bez spacji), a następnie symbolu wieloznacznego ( * ).

Aby uzyskać więcej informacji na temat tworzenia zapytań wyszukiwania zbierania elektronicznych materiałów dowodowych, zobacz [Zapytania słów kluczowych i warunki wyszukiwania dla zbierania elektronicznych materiałów dowodowych](keyword-queries-and-search-conditions.md).

## <a name="data-connectors-in-the-us-government-cloud"></a>Łączniki danych w chmurze dla instytucji rządowych USA

Niektóre łączniki danych są dostępne w chmurze dla instytucji rządowych USA. Poniższe sekcje wskazują konkretne środowiska rządowe, które obsługują łączniki danych innych firm. Aby uzyskać więcej informacji na temat chmur dla instytucji rządowych USA, zobacz [Microsoft 365 US Government](/office365/servicedescriptions/office-365-platform-service-description/office-365-us-government/microsoft-365-government-how-to-buy).

### <a name="veritas-data-connectors-in-the-us-government-cloud-preview"></a>Łączniki danych Veritas w chmurze dla instytucji rządowych USA (wersja zapoznawcza)

|Łącznik danych  |GCC  |GCC wysoki  |DoD  |
|:---------|:---------|:---------|:---------|
|CellTrust| Tak | Nie | Nie |
|Cisco Jabber w witrynie MS SQL| Tak | Nie | Nie |
|Cisco Jabber w systemie Oracle| Tak | Nie | Nie |
|Cisco Jabber w usłudze PostgreSQL| Tak | Nie | Nie |
|EML| Tak | Nie | Nie |
|FX Connect| Tak | Nie | Nie |
|Jive| Tak | Nie | Nie |
|Baza danych MS SQL| Tak | Nie | Nie |
|Dokument bazowy| Tak | Nie | Nie |
|Redtail Speak| Tak | Nie | Nie |
|Reuters Dealing| Tak | Nie | Nie |
|Reuters Eikon| Tak | Nie | Nie |
|Reuters FX| Tak | Nie | Nie |
|RingCentral| Tak | Nie | Nie |
|Czat w usłudze Salesforce| Tak | Nie | Nie |
|ServiceNow| Tak | Nie | Nie |
|Skype dla firm| Tak | Nie | Nie |
|Slack eDiscovery| Tak | Nie | Nie |
|Symphony| Tak | Nie | Nie |
|Rozdzielany tekstem| Tak | Nie | Nie |
|Twitter| Tak | Nie | Nie |
|Webex Teams| Tak | Nie | Nie |
|Strony internetowe| Tak | Nie | Nie |
|Miejsce pracy z serwisu Facebook| Tak | Nie | Nie |
|XIP| Tak | Nie | Nie |
|XSLT/XML| Tak | Nie | Nie |
|Yieldbroker| Tak | Nie | Nie |
|YouTube| Nie | Nie | Nie |
|Spotkania w usłudze Zoom| Tak | Nie | Nie |
|||||

### <a name="telemessage-data-connectors-in-the-us-government-cloud"></a>Łączniki danych telemessage w chmurze dla instytucji rządowych USA

|Łącznik danych  |GCC  |GCC wysoki  |DoD  |
|:---------|:---------|:---------|:---------|
|Archiwizator systemu Android | Tak | Nie | Nie |
|Archiwizator sieci AT&T SMS/MMS | Tak | Nie | Nie |
|Archiwizator sieci Bell SMS/MMS | Tak | Nie | Nie |
|Archiwizator numerów przedsiębiorstwa | Tak | Nie | Nie |
|O2 SMS i Voice Network Archiver | Tak         | Nie | Nie |
|Archiwizator sieci Rogers | Tak         | Nie | Nie |
|Archiwizator sygnału | Tak | Nie | Nie |
|Archiwizator usługi Telegram | Tak | Nie | Nie |
|TELUS SMS Network Archiver | Tak | Nie | Nie |
|Archiwizator sieci Verizon SMS/MMS | Tak | Nie | Nie |
|Archiwizator usługi WeChat | Tak | Nie | Nie |
|Archiwizator usługi WhatsApp | Tak | Nie | Nie |
|||||

### <a name="17a-4-data-connectors-in-the-us-government-cloud"></a>Łączniki danych 17a-4 w chmurze dla instytucji rządowych USA

|Łącznik danych  |GCC  |GCC wysoki  |DoD  |
|:---------|:---------|:---------|:---------|
|BlackBerry DataParser | Tak | Nie | Nie |
|Bloomberg DataParser  | Tak | Nie | Nie |
|Cisco Jabber DataParser  | Tak | Nie | Nie |
|Cisco Webex DataParser  | Tak | Nie | Nie |
|FactSet DataParser  | Tak | Nie | Nie |
|Fuze DataParser  | Tak | Nie | Nie |
|FX Connect DataParser  | Tak | Nie | Nie |
|ICE DataParser  | Tak | Nie | Nie |
|InvestEdge DataParser  | Tak | Nie | Nie |
|LivePerson Conversational Cloud DataParser  | Tak | Nie | Nie |
|Quip DataParser  | Tak | Nie | Nie |
|Refinitiv Eikon Messenger DataParser  | Tak | Nie | Nie |
|ServiceNow DataParser  | Tak | Nie | Nie |
|Skype dla firm Server DataParser | Tak | Nie | Nie |
|Slack DataParser | Tak | Nie | Nie |
|SQL DataParser  | Tak | Nie | Nie |
|Symphony DataParser | Tak | Nie | Nie |
|Zoom DataParser | Tak | Nie | Nie |
|||||

### <a name="celltrust-data-connectors-in-the-us-government-cloud"></a>Łączniki danych CellTrust w chmurze dla instytucji rządowych USA

|Łącznik danych  |GCC  |GCC wysoki  |DoD  |
|:---------|:---------|:---------|:---------|
|CellTrust SL2 | Tak | Nie | Nie |
|||||

## <a name="working-with-a-microsoft-partner-to-archive-third-party-data"></a>Praca z partnerem firmy Microsoft w celu archiwizacji danych innych firm

Inną opcją importowania i archiwizowania danych innych firm jest współpraca organizacji z partnerem firmy Microsoft. Jeśli typ danych innej firmy nie jest obsługiwany przez łączniki danych dostępne w Centrum zgodności firmy Microsoft, możesz współpracować z partnerem, który może udostępnić łącznik niestandardowy, który będzie regularnie konfigurowany do wyodrębniania elementów ze źródła danych innej firmy, a następnie łączyć się z chmurą firmy Microsoft za pomocą interfejsu API innej firmy i importować te elementy do Microsoft 365. Łącznik partnera konwertuje również zawartość elementu ze źródła danych innej firmy na wiadomość e-mail, a następnie importuje ją do skrzynki pocztowej w Microsoft 365.

Aby uzyskać listę partnerów, z którą możesz pracować, oraz proces krok po kroku dla tej metody, zobacz [Praca z partnerem w celu archiwizacji danych innych firm w Microsoft 365](work-with-partner-to-archive-third-party-data.md).
