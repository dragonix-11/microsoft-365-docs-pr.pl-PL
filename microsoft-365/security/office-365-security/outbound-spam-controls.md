---
title: Ochrona przed spamem ruchu wychodzącego
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: Admin
ms.topic: overview
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: 6a601501-a6a8-4559-b2e7-56b59c96a586
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Administratorzy mogą dowiedzieć się więcej o kontrolkach spamu wychodzącego w u Exchange Online Protection (EOP) i co należy zrobić, jeśli musisz wysyłać wysyłki masowe.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 26be514584a8fb2f8c024c0f4db208018d951868
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988005"
---
# <a name="outbound-spam-protection-in-eop"></a>Ochrona przed spamem ruchu wychodzącego w uceniu EOP

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender dla Office 365 plan 1 i plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

W Microsoft 365 z skrzynkami pocztowymi w organizacjach Exchange Online lub autonomicznych organizacjach typu Exchange Online Protection (EOP) bez skrzynek pocztowych usługi Exchange Online poważne zarządzanie spamem wychodzącym. Nawet jeśli jeden z klientów celowo lub nieumyślnie wysyła spam ze swojej organizacji, to działanie to może pogorszyć reputację całej usługi i może mieć wpływ na dostarczanie wiadomości e-mail do innych klientów.

W tym artykule opisano kontrolki i powiadomienia, które mają pomóc w zapobieganiu spamowi wychodzącemu, oraz co możesz zrobić, jeśli musisz wysyłać masową korespondencję pocztową.

## <a name="what-admins-can-do-to-control-outbound-spam"></a>Co administratorzy mogą zrobić, aby kontrolować spam wychodzący

- Korzystanie z wbudowanych powiadomień: Jeśli użytkownik przekracza limity wysyłania usługi lub [](configure-the-outbound-spam-policy.md) zasad spamu wychodzącego i nie może wysyłać wiadomości **e-mail**,  domyślne zasady alertów o nazwie Użytkownik z ograniczeniem wysyłania wiadomości e-mail wysyła powiadomienia e-mail do członków grupy **TenantAdmins** **(** administratorzy globalni).[](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#sending-limits-across-office-365-options) Aby skonfigurować inne osoby, które otrzymają te powiadomienia, zobacz [Weryfikowanie ustawień alertów dla użytkowników z ograniczeniami](removing-user-from-restricted-users-portal-after-spam.md#verify-the-alert-settings-for-restricted-users). Ponadto domyślne zasady alertów o nazwie  Przekroczono limit wysyłania wiadomości  e-mail i Wykryto podejrzane wzorce wysyłania wiadomości e-mail, które wysyłają powiadomienia e-mail do członków grupy **Administratorzy** **dzierżawcy (** administratorzy globalni). Aby uzyskać więcej informacji na temat zasad alertów, zobacz [Zasady alertów w programie Microsoft 365](../../compliance/alert-policies.md).

- Przejrzyj skargi dotyczące spamu od dostawców poczty e-mail innych firm: Wiele usług poczty e-mail, takich jak Outlook.com, Yahoo i AOL, zapewnia pętlę opinii, w której jeśli jakiś użytkownik w swojej usłudze oznacza wiadomość **e-mail** od firmy Microsoft 365 jako spam, jest spakowana i wysyłana do nas w celu sprawdzenia. Aby dowiedzieć się więcej na temat obsługi nadawców w Outlook.com, przejdź do <https://sendersupport.olc.protection.outlook.com/pm/services.aspx>.

## <a name="how-eop-controls-outbound-spam"></a>Jak eOP steruje spamem wychodzącym

- **Podział wychodzącego ruchu poczty e-mail**: Każda wiadomość wychodząca wysyłana za pośrednictwem usługi jest skanowana w celu wykrywania spamu. Jeśli wiadomość zostanie określona jako spam, jest dostarczana z pomocniczej, mniej godnej zaufania puli adresów IP o nazwie pula dostarczania _wysokiego ryzyka_. Aby uzyskać więcej informacji, zobacz [Pula dostarczania wiadomości o wysokim poziomie ryzyka dla wiadomości wychodzących](high-risk-delivery-pool-for-outbound-messages.md).

- **Monitorowanie naszej reputacji źródłowego adresu IP**: Microsoft 365 różne listy zablokowanych adresów IP innych firm. Jeśli na tych listach pojawi się dowolny z adresów IP, których używamy do wychodzących wiadomości e-mail, zostanie wygenerowany alert. Monitorowanie to pozwala nam szybko reagować, gdy spam spowodował obniżenie reputacji firmy. Po wygenerowaniu alertu mamy wewnętrzną dokumentację, która opisuje sposób usuwania adresów IP (wykreślanych) z list zablokowanych.

- Wyłącz konta, które wysyłają zbyt wiele **spamu**<sup>\*</sup>: Nawet jeśli rozdzielimy spam wychodzący na pulę dostarczania wiadomości wysokiego ryzyka, nie możemy zezwolić kontu (często na naruszone konto) na wysyłanie spamu w nieskończoność. Monitorujemy konta, które wysyłają spam, i w przypadku przekroczenia limitu nieujawnianych wiadomości e-mail takie konto ma zablokowaną możliwość wysyłania wiadomości e-mail. Istnieją różne progi dla poszczególnych użytkowników i całej dzierżawy.

- <sup>\*</sup>Wyłączanie kont, które zbyt szybko wysyłają zbyt wiele wiadomości e-mail: oprócz limitów wyszukiwania wiadomości oznaczonych jako spam istnieją również ograniczenia blokowania kont po osiągnięciu ogólnego limitu wiadomości wychodzących, niezależnie od werdyktu filtrowania spamu dla wiadomości wychodzących. Naruszone konto może wysyłać spam bezpowrzewowy (nierozpoznany wcześniej) i nieodebrany przez filtr spamu. Ponieważ zidentyfikowanie legalnych kampanii wysyłkowych masowych i kampanii spamowych może być trudne, limity te pomagają zminimalizować potencjalne szkody.

<sup>\*</sup> Nie ogłaszamy dokładnych limitów, aby spamerzy nie grali w system, więc możemy zwiększyć lub zmniejszyć te limity w razie potrzeby. Limity są na tyle duże, aby zapobiec przekroczeniu ich przez przeciętnego użytkownika biznesowego, a także są na tyle niskie, aby pomóc w powstawaniu szkód spowodowanych przez spamer.

## <a name="recommendations-for-customers-who-want-to-send-mass-mailings-through-eop"></a>Rekomendacje dla klientów, którzy chcą wysyłać wysyłki masowe za pośrednictwem usługi EOP

Trudno jest przechylić równowagę między klientami, którzy chcą wysyłać dużą ilość poczty e-mail, a chronić usługę przed naruszonymi kontami i masową pocztą e-mail nadawców, którzy mają złe praktyki pozyskiwania adresatów. Koszt wiadomości e-Microsoft 365 e-mail do listy zablokowanych adresów IP innej firmy jest większy niż blokowanie użytkownika, który wysyła zbyt dużo wiadomości e-mail.

Jak [opisano](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits) w opisie usługi Exchange Online, używanie usługi EOP do wysyłania zbiorczych wiadomości e-mail nie jest obsługiwanym korzystaniem z usługi i jest dozwolone tylko dla "najlepszych starań, ale bez nakładu pracy". Klientom, którzy chcą wysyłać masową pocztę e-mail, zalecamy następujące rozwiązania:

- **Wysyłaj masową pocztę e-mail** za pośrednictwem lokalnych serwerów poczty e-mail: Klienci utrzymują własną infrastrukturę poczty e-mail do wysyłki masowej.

- **Użyj zbiorczego dostawcy poczty e-mail** od innej firmy: Istnieje kilku dostawców rozwiązań do zbiorczej poczty e-mail, których można używać do wysyłania wysyłek masowych wiadomości e-mail. Te firmy mają duże zainteresowanie współpracę z klientami w celu zapewnienia dobrych praktyk w zakresie wysyłania wiadomości e-mail.

Grupa robocza ds. wiadomości( Messaging, Mobile, Malware Anti-Abuse Working Group, MAAWG) publikuje wykaz członków w <https://www.maawg.org/about/roster>. Kilku zbiorczo dostępnych dostawców poczty e-mail jest odpowiedzialnych za połączenia internetowe.
