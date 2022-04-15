---
title: Konfigurowanie powiadomień e-mail dla zespołu ds. zabezpieczeń
description: Konfigurowanie powiadomień e-mail w celu poinformowania użytkowników o alertach i lukach w zabezpieczeniach przy użyciu Microsoft Defender dla Firm
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 04/12/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection: M365-security-compliance
ms.openlocfilehash: a65634a5827e60d710cec56ca10835c73053cb10
ms.sourcegitcommit: e3bc6563037bd2cce2abf108b3d1bcc2ccf538f6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/15/2022
ms.locfileid: "64862857"
---
# <a name="set-up-email-notifications"></a>Konfigurowanie powiadomień e-mail

> [!NOTE]
> Microsoft Defender dla Firm jest teraz uwzględniony w [Microsoft 365 Business Premium](../../business-premium/index.md). 

Możesz skonfigurować powiadomienia e-mail dla zespołu ds. zabezpieczeń. Następnie po wygenerowaniu alertów lub wykryciu nowych luk w zabezpieczeniach osoby z zespołu ds. zabezpieczeń będą automatycznie powiadamiane. 

## <a name="what-to-do"></a>Co robić

1. [Dowiedz się więcej o typach powiadomień e-mail](#types-of-email-notifications).

2. [Wyświetlanie i edytowanie ustawień powiadomień e-mail](#view-and-edit-email-notifications).

3. [Przejdź do kolejnych kroków](#next-steps).


>
> **Masz minutę?**
> Weź udział w <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">krótkiej ankiecie dotyczącej bezpieczeństwa</a>. Chcielibyśmy usłyszeć od Ciebie!
>

## <a name="types-of-email-notifications"></a>Typy powiadomień e-mail

Podczas konfigurowania powiadomień e-mail można wybrać jeden z dwóch typów, zgodnie z opisem w poniższej tabeli:

| Typ powiadomienia  | Opis  |
|---------|---------|
| Luki  | Za każdym razem, gdy zostaną wykryte nowe luki w zabezpieczeniach lub luki w zabezpieczeniach, adresaci otrzymają wiadomość e-mail. |
| Alerty & luk w zabezpieczeniach  | Po wygenerowaniu alertów z powodu wykrycia zagrożeń na urządzeniach lub wykryciu nowych luk w zabezpieczeniach adresaci otrzymują wiadomość e-mail. |

> [!TIP]
> **Powiadomienia e-mail nie są jedynym sposobem, w jaki zespół ds. zabezpieczeń może dowiedzieć się o nowych alertach lub lukach w zabezpieczeniach**.
> 
> Powiadomienia e-mail są wygodnym sposobem na informowanie zespołu ds. zabezpieczeń w czasie rzeczywistym. Ale są też inne! Na przykład za każdym razem, gdy zespół ds. zabezpieczeń loguje się do portalu Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)), będą widoczne karty wyróżniające nowe zagrożenia, alerty i luki w zabezpieczeniach. Usługa Defender dla Firm została zaprojektowana w celu wyróżnienia ważnych informacji, na które dba twój zespół ds. zabezpieczeń zaraz po zalogowaniu się.
> 
> Twój zespół ds. zabezpieczeń może również wybrać pozycję **Incydenty** w okienku nawigacji, aby wyświetlić informacje. Aby dowiedzieć się więcej, zobacz [Wyświetlanie zdarzeń i zarządzanie nimi w Microsoft Defender dla Firm](mdb-view-manage-incidents.md).

## <a name="view-and-edit-email-notifications"></a>Wyświetlanie i edytowanie powiadomień e-mail

Aby wyświetlić lub edytować ustawienia powiadomień e-mail dla firmy, wykonaj następujące kroki:

1. Przejdź do portalu Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) i zaloguj się.

2. W okienku nawigacji wybierz pozycję **Ustawienia**, a następnie wybierz pozycję **Punkty końcowe**. Następnie w obszarze **Ogólne** wybierz pozycję **Powiadomienia e-mail**. 

3. Przejrzyj informacje na **kartach Alerty** i **luki w zabezpieczeniach** .

   - Jeśli nie widzisz żadnych elementów wymienionych na **karcie Alerty** , możesz utworzyć regułę powiadamiania użytkowników podczas generowania alertów. Aby uzyskać pomoc dotyczącą tego zadania, zobacz [Tworzenie reguł dla powiadomień o alertach](../defender-endpoint/configure-email-notifications.md).

   - Jeśli nie widzisz żadnych elementów wymienionych na karcie **Luki w zabezpieczeniach** , możesz utworzyć regułę powiadamiania użytkowników za każdym razem, gdy zostanie wykryte nowe luki w zabezpieczeniach. Aby uzyskać pomoc dotyczącą tego zadania, zobacz [Tworzenie reguł dla zdarzeń luk w zabezpieczeniach](../defender-endpoint/configure-vulnerability-email-notifications.md).

   - Jeśli masz utworzone reguły, wybierz regułę, aby ją edytować. Można również usunąć regułę. 

## <a name="next-steps"></a>Następne kroki

Przejdź do:

- [Krok 4. Dołączanie urządzeń do Microsoft Defender dla Firm](mdb-onboard-devices.md)
