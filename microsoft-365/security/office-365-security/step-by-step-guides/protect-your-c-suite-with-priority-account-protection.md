---
title: Ochrona pakietu c przy użyciu priorytetowej ochrony konta w planie Ochrona usługi Office 365 w usłudze Microsoft Defender 2
description: Kroki ochrony pakietu C z priorytetową ochroną konta. Tagowanie konta jako konta priorytetowego umożliwi dodatkową ochronę dostosowaną do wzorców przepływu poczty skierowanych do kierownictwa firmy, a także dodatkowy wgląd w raporty, alerty i badania.
search.product: ''
search.appverid: ''
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-guidance-templates
ms.topic: how-to
ms.technology: mdo
ms.openlocfilehash: 99bfcd9003d55ced96364f033080992fa4447188
ms.sourcegitcommit: a7c1acfb3d2cbba913e32493b16ebd8cbfeee456
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/13/2022
ms.locfileid: "66042932"
---
# <a name="protect-your-c-suite-with-priority-account-protection"></a>Ochrona pakietu C z priorytetową ochroną konta

Priorytetowa ochrona konta pomaga zespołom IT i zespołom ds. zabezpieczeń zapewnić wysoką jakość usług i ochronę krytycznych osób w organizacji. Tagowanie konta jako konta priorytetowego umożliwi dodatkową ochronę dostosowaną do wzorców przepływu poczty skierowanych do kierownictwa firmy, a także dodatkowy wgląd w raporty, alerty i badania.

## <a name="what-youll-need"></a>Co będzie potrzebne
- Ochrona usługi Office 365 w usłudze Microsoft Defender plan 2 (uwzględniony w planach E5)
- Wystarczające uprawnienia (rola administratora zabezpieczeń)
- 5 minut na wykonanie poniższych kroków.

## <a name="tag-priority-users"></a>Tagowanie użytkowników o priorytecie
1. Zidentyfikuj użytkowników, grupy lub domeny, które chcesz oznaczyć jako konta priorytetowe.
1. Zaloguj się do [witryny Microsoft Security Portal](https://security.microsoft.com/) i przejdź do Ustawienia na lewym pasku nawigacyjnym.
1. Wybierz pozycję Poczta e-mail & współpracy na załadowanej stronie, a następnie kliknij pozycję Tagi użytkownika
1. Na stronie Tagi użytkownika wybierz tag Konto priorytetowe i naciśnij pozycję Edytuj tag
1. Na wyświetlonym wysuwie wybierz pozycję Dodaj członków
1. Wyszukaj użytkowników, którzy chcesz oznaczyć tagiem, wybierz co najmniej jednego użytkownika i naciśnij przycisk Dodaj
1. Przejrzyj wybrane elementy członkowskie i naciśnij przycisk Dalej
1. Naciśnij pozycję Prześlij, aby potwierdzić zmiany

Aby dowiedzieć się, jakie są priorytetowe tagi kont, zobacz [Zarządzanie kontami priorytetów i monitorowanie ich — Microsoft 365 administratora | Microsoft Docs](../../../admin/setup/priority-accounts.md).

## <a name="next-steps"></a>Następne kroki
[Przejrzyj zróżnicowaną ochronę użytkowników oznaczonych jako konta priorytetowe](../../office-365-security/configure-review-priority-account.md).

## <a name="powershell-configuration"></a>Konfiguracja programu PowerShell
Jeśli chcesz wykonać te kroki za pośrednictwem programu [PowerShell](/powershell/exchange/connect-to-exchange-online-powershell), możesz to zrobić przy użyciu następujących poleceń cmdlet:
1. Wyświetl listę kont priorytetów: **Get-User -IsVIP | wybierz pozycję Tożsamość**
1. Dodawanie użytkownika do listy kont priorytetów: **Set-User -VIP:$true -Identity \<Identity\>**
1. Usuwanie użytkownika z listy kont priorytetów: **Set-User -VIP:$false -Identity \<Identity\>**
