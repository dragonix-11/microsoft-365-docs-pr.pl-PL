---
title: Korzystanie z kreatora konfiguracji w Microsoft Defender dla Firm
description: Usługa Defender dla firm obejmuje proces konfiguracji i konfiguracji podobny do kreatora. Użyj kreatora, aby zaoszczędzić czas i nakład pracy.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: article
ms.date: 04/15/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.custom: intro-get-started
ms.openlocfilehash: 697dfc567eb2719a6e81a7b57df321ba2af40911
ms.sourcegitcommit: 23e186b46b27a6a4863f507a52a11105afae9726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/15/2022
ms.locfileid: "64882313"
---
# <a name="use-the-setup-wizard-in-microsoft-defender-for-business"></a>Korzystanie z kreatora konfiguracji w Microsoft Defender dla Firm

> [!NOTE]
> Microsoft Defender dla Firm jest teraz uwzględniony w [Microsoft 365 Business Premium](../../business-premium/index.md). 

Microsoft Defender dla Firm została zaprojektowana w celu zaoszczędzenia czasu i wysiłku małych i średnich firm. Na przykład można wykonać początkową konfigurację i konfigurację za pomocą kreatora konfiguracji. Kreator konfiguracji przeprowadzi Cię przez udzielanie dostępu zespołowi ds. zabezpieczeń, konfigurowanie powiadomień e-mail dla zespołu ds. zabezpieczeń i dołączanie urządzeń Windows firmy.

>
> **Masz minutę?**
> Weź udział w <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">krótkiej ankiecie dotyczącej bezpieczeństwa</a>. Chcielibyśmy usłyszeć od Ciebie!
>

> [!TIP]
> Korzystanie z kreatora konfiguracji jest opcjonalne. Możesz ręcznie przejść przez proces konfiguracji i konfiguracji. Aby dowiedzieć się więcej, zobacz:
> - [Co się stanie, jeśli nie będę używać kreatora?](#what-happens-if-i-dont-use-the-wizard)
> - [Jak skonfigurować i skonfigurować Microsoft Defender dla Firm](mdb-setup-configuration.md)

## <a name="how-to-start-the-setup-wizard"></a>Jak uruchomić kreatora instalacji

Kreator instalacji jest przeznaczony do uruchamiania po raz pierwszy, gdy ktoś w firmie loguje się do portalu Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)). 

Jeśli Twoja firma korzysta z Microsoft 365 Business Premium, kreator konfiguracji usługi Defender dla Firm uruchomi polecenie po raz pierwszy, gdy ktoś przejdzie do **spisu punktów** **końcowychUrządzenia** > . 

Ekran uruchamiania kreatora instalacji wygląda następująco:

:::image type="content" source="media/mdb-wizard-start.png" alt-text="Zrzut ekranu przedstawiający ekran główny kreatora umożliwiający skonfigurowanie usługi Defender dla Firm.":::

## <a name="the-setup-wizard-flow"></a>Przepływ kreatora instalacji

> [!IMPORTANT]
> Aby uruchomić kreatora instalacji, musisz być administratorem globalnym. Osoba, która utworzyła firmę w celu Microsoft 365 lub Microsoft Defender dla Firm, jest domyślnie administratorem globalnym.

Kreator konfiguracji został zaprojektowany, aby ułatwić szybkie i wydajne konfigurowanie usługi Defender for Business. Kreator przeprowadzi Cię przez następujące kroki:

1. **Przypisz uprawnienia użytkownika**. W tym kroku udzielisz zespołowi ds. zabezpieczeń dostępu do portalu Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)). W tym portalu ty i Twój zespół ds. zabezpieczeń będziecie zarządzać twoimi możliwościami zabezpieczeń, wyświetlać alerty i podejmować wszelkie wymagane akcje dotyczące wykrytych zagrożeń. Dostęp do portalu jest udzielany za pośrednictwem ról, które implikują określone uprawnienia.

   W usłudze Defender dla firm członkom zespołu ds. zabezpieczeń można przypisać jedną z następujących trzech ról:<br/>
   
   - **Administrator globalny**: administrator globalny może wyświetlać i edytować wszystkie ustawienia w dzierżawie Microsoft 365. Administrator globalny przeprowadza początkową konfigurację subskrypcji Microsoft 365 firmy. 
   - **Administrator zabezpieczeń**: administrator zabezpieczeń może wyświetlać i edytować ustawienia zabezpieczeń oraz podejmować działania w przypadku wykrycia zagrożeń.
   - **Czytelnik zabezpieczeń**: czytelnik zabezpieczeń może wyświetlać informacje w raportach, ale nie może zmieniać żadnych ustawień zabezpieczeń. 

   [Dowiedz się więcej o rolach i uprawnieniach](mdb-roles-permissions.md). 

2. **Konfigurowanie powiadomień e-mail**. W tym kroku możesz skonfigurować powiadomienia e-mail dla zespołu ds. zabezpieczeń. Następnie po wygenerowaniu alertu lub wykryciu nowej luki w zabezpieczeniach twój zespół ds. zabezpieczeń nie będzie o nim korzystać, nawet jeśli znajduje się z dala od biurka. [Dowiedz się więcej o powiadomieniach e-mail](mdb-email-notifications.md). 

3. **Dołączanie i konfigurowanie urządzeń Windows**. W tym kroku możesz szybko dołączyć urządzenia Windows firmy do usługi Defender dla Firm. Od razu dołączanie urządzeń pomaga chronić te urządzenia od pierwszego dnia. 

   - **Jeśli używasz już Microsoft Endpoint Manager** (w tym Microsoft Intune), a twoja firma ma urządzenia zarejestrowane w Endpoint Manager, zostanie wyświetlone pytanie, czy chcesz używać [automatycznego dołączania](#what-is-automatic-onboarding) do niektórych lub wszystkich zarejestrowanych urządzeń Windows. Automatyczne dołączanie konfiguruje połączenie między Endpoint Manager i usługą Defender dla Firm, a następnie bezproblemowo dołącza urządzenia Windows do usługi Defender dla Firm. 
   - **Jeśli nie używasz jeszcze Endpoint Manager**, możesz [dołączyć urządzenia do usługi Defender dla Firm](mdb-onboard-devices.md). 
   
   [Dowiedz się więcej o dołączaniu urządzeń do Microsoft Defender dla Firm](mdb-onboard-devices.md).
   
4. **Skonfiguruj zasady zabezpieczeń**. Usługa Defender dla firm zawiera domyślne zasady zabezpieczeń dla ochrony następnej generacji i ochrony zapory, które mogą być stosowane do urządzeń firmy. Te domyślne zasady używają zalecanych ustawień i zostały zaprojektowane tak, aby zapewnić silną ochronę urządzeń. Możesz również utworzyć własne zasady zabezpieczeń. A jeśli już używasz Endpoint Manager, możesz nadal używać ich do zarządzania zasadami zabezpieczeń.

   [Wyświetlanie i edytowanie zasad zabezpieczeń i ustawień](mdb-configure-security-settings.md).

## <a name="what-is-automatic-onboarding"></a>Co to jest automatyczne dołączanie?

Automatyczne dołączanie to uproszczony sposób dołączania urządzeń Windows do usługi Defender for Business. Automatyczne dołączanie jest dostępne tylko dla urządzeń Windows, które są już zarejestrowane w Microsoft Endpoint Manager (lub Microsoft Intune). 

Podczas korzystania z kreatora instalacji system wykryje, czy urządzenia Windows są już zarejestrowane w Endpoint Manager. Zostanie wyświetlone pytanie, czy chcesz używać automatycznego dołączania dla wszystkich lub niektórych z tych urządzeń. Możesz dołączyć wszystkie urządzenia Windows jednocześnie lub wybrać określone urządzenia do rozpoczęcia, a następnie dodać więcej urządzeń później. 

Aby dołączyć inne urządzenia, zobacz [Dołączanie urządzeń do Microsoft Defender dla Firm](mdb-onboard-devices.md).

> [!TIP]
> - Zalecamy wybranie opcji "wszystkie zarejestrowane urządzenia". Dzięki temu, gdy Windows urządzenia zostaną zarejestrowane w Endpoint Manager później, zostaną automatycznie dołączone do usługi Defender for Business. 
> - Jeśli zarządzasz zasadami i ustawieniami zabezpieczeń w Endpoint Manager, zalecamy przejście do portalu Microsoft 365 Defender w celu zarządzania urządzeniami, zasadami i ustawieniami. Aby dowiedzieć się więcej, zobacz [Wybieranie miejsca zarządzania zasadami zabezpieczeń i urządzeniami](mdb-configure-security-settings.md#choose-where-to-manage-security-policies-and-devices).

## <a name="what-happens-if-i-dont-use-the-wizard"></a>Co się stanie, jeśli nie będę używać kreatora?

Korzystanie z kreatora konfiguracji jest opcjonalne. Jeśli nie chcesz korzystać z kreatora lub kreator zostanie zamknięty przed zakończeniem procesu konfiguracji, możesz samodzielnie ukończyć proces konfiguracji i konfiguracji. 

Zobacz [Konfigurowanie i konfigurowanie Microsoft Defender dla Firm](mdb-setup-configuration.md), aby wykonać następujące kroki:

1. **[Przypisz role i uprawnienia](mdb-roles-permissions.md)**, aby zespół ds. zabezpieczeń mógł uzyskiwać dostęp do portalu Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) i korzystać z niego.

2. **[Skonfiguruj powiadomienia e-mail dla zespołu ds. zabezpieczeń](mdb-email-notifications.md)** , aby były w pętli dotyczące nowych alertów lub luk w zabezpieczeniach.

3. **[Dołącz urządzenia](mdb-onboard-devices.md)** , aby były chronione przez usługę Defender dla Firm.

4. **[Zarządzaj zasadami zabezpieczeń](mdb-configure-security-settings.md)**, które obejmują ochronę następnej generacji, ochronę zapory i filtrowanie zawartości internetowej.

## <a name="next-steps"></a>Następne kroki

- [Dołączanie większej liczby urządzeń do Microsoft Defender dla Firm](mdb-onboard-devices.md)
- [Wyświetlanie i edytowanie zasad zabezpieczeń i ustawień w Microsoft Defender dla Firm](mdb-configure-security-settings.md)