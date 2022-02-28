---
title: Limity czasu sesji dla Microsoft 365
ms.author: tracyp
author: MSFTTracyP
manager: scotv
ms.date: 6/29/2018
audience: Admin
ms.topic: reference
ms.service: o365-administration
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- BCS160
ms.assetid: 37a5c116-5b07-4f70-8333-5b86fd2c3c40
ms.collection:
- M365-security-compliance
description: Dowiedz się, jak limity czasu sesji są używane do równoważenia zabezpieczeń i ułatwień dostępu w Microsoft 365 klienckich.
ms.openlocfilehash: f5b7c87cabfd6f80061c2795568cd53955caa10f
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988441"
---
# <a name="session-timeouts-for-microsoft-365"></a>Limity czasu sesji dla Microsoft 365

Okresy istnienia sesji są ważną częścią uwierzytelniania Microsoft 365 i są ważnym elementem w równoważeniu zabezpieczeń oraz liczbie monitów użytkowników o poświadczenia.

## <a name="session-times-for-microsoft-365-services"></a>Czasy sesji dla Microsoft 365 internetowych

Gdy użytkownicy uwierzytelniają się w dowolnej z Microsoft 365 sieci Web lub aplikacji mobilnych, jest ustanowiona sesja. W trakcie trwania sesji użytkownicy nie muszą ponownie uwierzytelniać się. Sesje mogą wygasać, gdy użytkownicy są nieaktywni, zamykają przeglądarkę lub kartę albo wygasają ich tokeny z innych powodów, na przykład po zresetowaniu hasła. Różne Microsoft 365 mają różne limity czasu sesji odpowiadające typowym poszczególnych usługom.

W poniższej tabeli wymieniono okresy istnienia sesji dla Microsoft 365 internetowych:

| Microsoft 365 usługi | Limit czasu sesji |
|:-----|:-----|
|Centrum administracyjne platformy Microsoft 365  <br/> |Co 8 godzin jest wymagane podanie poświadczeń dla centrum administracyjnego.  <br/> |
|SharePoint Online  <br/> |5 dni braku aktywności, jeśli użytkownik wybierze opcję Nie **wyebraj mnie**. Jeśli użytkownik ponownie SharePoint dostęp do usługi Online po upływie co najmniej 24 godzin od poprzedniego logowania, wartość limitu czasu jest resetowana do 5 dni.  <br/> |
|Outlook Web App  <br/> |6 godzin.  <br/> Możesz zmienić tę wartość, używając  _parametru ActivityBasedAuthenticationTimeoutInterval_ w cmdlet [Set-OrganizationConfig](/powershell/module/exchange/set-organizationconfig) .  <br/> |
|Azure Active Directory  <br/> (Używane przez aplikacje Office i Microsoft 365 w Windows klientów z włączonym nowoczesnym uwierzytelnianiem)  <br/> | Nowoczesne uwierzytelnianie używa tokenów dostępu i tokenów odświeżania w celu udzielania użytkownikom dostępu Microsoft 365 zasobów przy użyciu Azure Active Directory. Token dostępu to token sieci Web JSON dostarczony po pomyślnym uwierzytelnieniu i ważny przez godzinę. Token odświeżania ma dłuższy czas istnienia. Gdy token dostępu wygasa, klienci Office używają prawidłowego tokenu odświeżania w celu uzyskania nowego tokenu dostępu. Ta wymiana zakończy się powodzeniem, jeśli początkowe uwierzytelnianie użytkownika jest nadal prawidłowe.  <br/>  Tokeny odświeżania są ważne 90 dni i w przypadku stałego użytkowania mogą być ważne do czasu ich odwołania.  <br/>  Tokeny odświeżania mogą zostać unieważnione przez kilka zdarzeń, takich jak:  <br/>  Hasło użytkownika zostało zmienione od momentu wystawienia tokenu odświeżania.  <br/>  Administrator może zastosować zasady dostępu warunkowego ograniczające dostęp do zasobu, do których użytkownik próbuje uzyskać dostęp.  <br/> |
|SharePoint i OneDrive dla systemów Android, iOS i Windows 10  <br/> |Domyślny czas istnienia tokenu dostępu to 1 godzina. Domyślny maksymalny czas braku aktywności tokenu odświeżania to 90 dni.  <br/> [Dowiedz się więcej o tokenach i  how to configure token lifetimes](/azure/active-directory/active-directory-configurable-token-lifetimes) <br/> Aby odwołać token odświeżania, możesz zresetować hasło Microsoft 365 użytkownika  <br/> |
|Yammer z Microsoft 365 Sign-In  <br/> |Okres istnienia okna przeglądarki. Jeśli użytkownicy zamkną przeglądarkę i uzyskają Yammer w nowej przeglądarce, Yammer zostaną ponownie uwierzytelnieni w Microsoft 365. Jeśli użytkownicy korzystają z przeglądarek innych firm, które buforują pliki cookie, ponowne uwierzytelnianie po ponownym otwarciu przeglądarki może nie być konieczne.  <br/> > [!NOTE]> Obowiązuje to tylko w przypadku sieci korzystających Microsoft 365 Sign-In sieci Yammer.           |