---
title: Korzystanie z kreatora konfiguracji w Microsoft Defender dla Firm
description: Usługa Defender dla firm obejmuje proces konfiguracji i konfiguracji podobny do kreatora. Użyj kreatora, aby zaoszczędzić czas i nakład pracy.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: article
ms.date: 04/08/2022
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
ms.openlocfilehash: ad070273567d350973037f1ac5a0192036d22187
ms.sourcegitcommit: dd5fc139affb4cba4089cbdb2c478968b680699a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2022
ms.locfileid: "64746650"
---
# <a name="use-the-setup-wizard-in-microsoft-defender-for-business"></a>Korzystanie z kreatora konfiguracji w Microsoft Defender dla Firm

> [!IMPORTANT]
> Microsoft Defender dla Firm jest wdrażana dla [klientów Microsoft 365 Business Premium](../../business-premium/index.md) od 1 marca 2022 r. Usługa Defender dla Firm jako subskrypcja autonomiczna jest dostępna w wersji zapoznawczej i będzie stopniowo wdrażana dla klientów i partnerów IT, którzy [zarejestrują się tutaj](https://aka.ms/mdb-preview) , aby zażądać tej subskrypcji. Wersja zapoznawcza zawiera [początkowy zestaw scenariuszy](mdb-tutorials.md#try-these-preview-scenarios), a my będziemy regularnie dodawać możliwości.
> 
> Niektóre informacje zawarte w tym artykule odnoszą się do wstępnie wydanych produktów/usług, które mogą zostać znacząco zmodyfikowane przed ich komercyjnym wydaniem. Firma Microsoft nie udziela żadnych gwarancji, wyraźnych ani dorozumianych, dotyczących informacji podanych tutaj. 

Microsoft Defender dla Firm została zaprojektowana w celu zaoszczędzenia czasu i wysiłku małych i średnich firm przy użyciu kreatora środowiska początkowej konfiguracji i konfiguracji. Kreator konfiguracji przeprowadzi Cię przez udzielanie dostępu zespołowi ds. zabezpieczeń, konfigurowanie powiadomień e-mail dla zespołu ds. zabezpieczeń i dołączanie urządzeń Windows firmy.

:::image type="content" source="media/mdb-wizard-start.png" alt-text="Zrzut ekranu przedstawiający ekran główny kreatora umożliwiający skonfigurowanie usługi Defender dla Firm.":::

>
> **Masz minutę?**
> Weźmy <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">krótką ankietę dotyczącą Microsoft Defender dla Firm</a>. Chcielibyśmy usłyszeć od Ciebie!
>

## <a name="overview-of-the-setup-wizard"></a>Omówienie kreatora konfiguracji

> [!IMPORTANT]
> Przed rozpoczęciem upewnij się, że do twojej subskrypcji Microsoft 365 dodano już użytkowników. Aby uzyskać pomoc dotyczącą tego zadania, zobacz [Dodawanie użytkowników i przypisywanie licencji w tym samym czasie](../../admin/add-users/add-users.md).

Kreator został zaprojektowany, aby ułatwić szybkie i wydajne konfigurowanie usługi Defender for Business. Kreator przeprowadzi Cię przez następujące kroki:

1. **Przypisz uprawnienia użytkownika**. W tym kroku udzielisz zespołowi ds. zabezpieczeń dostępu do portalu Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)). W tym portalu ty i Twój zespół ds. zabezpieczeń będziecie zarządzać twoimi możliwościami zabezpieczeń, wyświetlać alerty i podejmować wszelkie wymagane akcje dotyczące wykrytych zagrożeń. Dostęp do portalu jest udzielany za pośrednictwem ról, które implikują określone uprawnienia.

   W usłudze Defender dla Firm członkom zespołu ds. zabezpieczeń można przypisać jedną z trzech ról:<br/>
   
      - **Administrator globalny**: administrator globalny może wyświetlać i edytować wszystkie ustawienia w dzierżawie Microsoft 365. Administrator globalny przeprowadza początkową konfigurację subskrypcji Microsoft 365 firmy. 
      - **Administrator zabezpieczeń**: administrator zabezpieczeń może wyświetlać i edytować ustawienia zabezpieczeń oraz podejmować działania w przypadku wykrycia zagrożeń.
      - **Czytelnik zabezpieczeń**: czytelnik zabezpieczeń może wyświetlać informacje w raportach, ale nie może zmieniać żadnych ustawień zabezpieczeń. 
      
      [Dowiedz się więcej o rolach i uprawnieniach](mdb-roles-permissions.md). 

2. **Konfigurowanie powiadomień e-mail**. W tym kroku możesz skonfigurować powiadomienia e-mail dla zespołu ds. zabezpieczeń. Następnie po wygenerowaniu alertu lub wykryciu nowej luki w zabezpieczeniach twój zespół ds. zabezpieczeń nie będzie o nim korzystać, nawet jeśli nie znajdzie się w biurze. 

   [Dowiedz się więcej o powiadomieniach e-mail](mdb-email-notifications.md). 

3. **Dołączanie i konfigurowanie urządzeń Windows**. W tym kroku możesz szybko dołączyć urządzenia Windows firmy do usługi Defender dla Firm. Od razu dołączanie urządzeń pomaga chronić te urządzenia od pierwszego dnia. 

   - **Jeśli używasz już Microsoft Endpoint Manager** (w tym Microsoft Intune), a twoja firma ma urządzenia zarejestrowane w Endpoint Manager, zostanie wyświetlone pytanie, czy chcesz używać [automatycznego dołączania](mdb-onboard-devices.md#automatic-onboarding-for-windows-devices-enrolled-in-microsoft-endpoint-manager) do niektórych lub wszystkich zarejestrowanych urządzeń Windows. Automatyczne dołączanie konfiguruje połączenie między Endpoint Manager i usługą Defender dla Firm, a następnie bezproblemowo dołącza urządzenia Windows do usługi Defender dla Firm. 
   - **Jeśli nie używasz jeszcze Endpoint Manager**, możesz [dołączyć urządzenia do usługi Defender dla Firm przy użyciu skryptu lokalnego](mdb-onboard-devices.md#local-script-in-defender-for-business). 
   
   Zobacz [Dowiedz się więcej o dołączaniu urządzeń do Microsoft Defender dla Firm](mdb-onboard-devices.md).
   
4. **Skonfiguruj zasady zabezpieczeń**. Usługa Defender dla firm zawiera domyślne zasady zabezpieczeń dla ochrony następnej generacji i ochrony zapory, które mogą być stosowane do urządzeń firmy. Te domyślne zasady używają zalecanych ustawień i zostały zaprojektowane tak, aby zapewnić silną ochronę urządzeń. Możesz również utworzyć własne zasady zabezpieczeń. A jeśli już używasz Endpoint Manager, możesz nadal używać ich do zarządzania zasadami zabezpieczeń.

   Aby dowiedzieć się więcej, zobacz [Wyświetlanie i edytowanie zasad i ustawień zabezpieczeń](mdb-configure-security-settings.md). |

## <a name="what-happens-if-i-dont-use-the-wizard"></a>Co się stanie, jeśli nie będę używać kreatora?

Korzystanie z kreatora konfiguracji jest opcjonalne. Jeśli nie chcesz korzystać z kreatora lub kreator zostanie zamknięty przed zakończeniem procesu konfiguracji, możesz samodzielnie ukończyć proces konfiguracji i konfiguracji. Zobacz [Konfigurowanie i konfigurowanie Microsoft Defender dla Firm](mdb-setup-configuration.md), aby wykonać następujące kroki:

1. **[Przypisz role i uprawnienia](mdb-roles-permissions.md)**, aby zespół ds. zabezpieczeń mógł uzyskiwać dostęp do portalu Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) i korzystać z niego.

2. **[Skonfiguruj powiadomienia e-mail dla zespołu ds. zabezpieczeń](mdb-email-notifications.md)** , aby były w pętli dotyczące nowych alertów lub luk w zabezpieczeniach.

3. **[Dołącz urządzenia](mdb-onboard-devices.md)** , aby były chronione przez usługę Defender dla Firm.

4. **[Zarządzaj zasadami zabezpieczeń](mdb-configure-security-settings.md)**, które obejmują ochronę następnej generacji, ochronę zapory i filtrowanie zawartości internetowej.

## <a name="next-steps"></a>Następne kroki

- [Konfigurowanie powiadomień e-mail dla zespołu ds. zabezpieczeń](mdb-email-notifications.md)

- [Wprowadzenie przy użyciu portalu Microsoft 365 Defender](mdb-get-started.md)

- [Korzystanie z pulpitu nawigacyjnego zarządzania lukami w zabezpieczeniach & zagrożeń](mdb-view-tvm-dashboard.md)