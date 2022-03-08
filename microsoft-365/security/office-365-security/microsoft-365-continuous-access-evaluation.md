---
title: Oceny dostępu ciągłego dla Microsoft 365 — Microsoft 365 dla przedsiębiorstw
description: W tym artykule opisano sposób Microsoft 365 dostępu warunkowego w usłudze Azure AD proaktywnie kończy aktywne sesje użytkowników i wymusza zmiany zasad dzierżawy w czasie rzeczywistym.
ms.author: dansimp
author: dansimp
manager: dansimp
ms.prod: m365-security
ms.topic: article
audience: Admin
f1.keywords:
- NOCSH
ms.custom:
- it-pro
- goldenconfig
ms.collection:
- M365-identity-device-management
- M365-security-compliance
- m365solution-identitydevice
- m365solution-scenario
ms.technology: mdo
ms.openlocfilehash: 255618508559e989a356ab404429bc4d87bfe2c6
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63324539"
---
# <a name="continuous-access-evaluation-for-microsoft-365"></a>Ocena dostępu ciągłego dla programu Microsoft 365

Nowoczesne usługi w chmurze, które używają protokołu OAuth 2.0 do uwierzytelniania, zazwyczaj korzystają z wygasania tokenu dostępu, aby odwołać dostęp do konta użytkownika. W praktyce oznacza to, że nawet jeśli administrator odwoła dostęp do konta użytkownika, ten użytkownik nadal będzie miał dostęp do momentu wygaśnięcia tokenu dostępu, który dla programu Microsoft 365 domyślnie był używany do godziny po początkowym zdarzeniu o odwołanie.

Analiza warunkowa dostępu dla usług Microsoft 365 i Azure Active Directory (Azure AD) aktywnie kończy aktywne sesje użytkowników i wymusza zmiany zasad dzierżawy w niedalekiej czasie rzeczywistym, zamiast polegać na wygaśnięciu tokenu dostępu. W usłudze Azure AD są powiadamiane usługi Microsoft 365 z włączonym oceny dostępu ciągłego (takie jak SharePoint, Teams i Exchange), gdy konto użytkownika lub dzierżawa uległy zmianie w sposób wymagający ponownego oceny stanu uwierzytelniania konta użytkownika.

Gdy klient oceny dostępu ciągłego, taki jak Outlook, próbuje uzyskać dostęp do usługi Exchange za pomocą istniejącego tokenu dostępu, token jest odrzucany przez usługę i jest monitowany o nowe uwierzytelnianie usługi Azure AD. Efektem jest niemal wymuszanie zmian w zasadach i konta użytkownika w czasie rzeczywistym.

Oto kilka dodatkowych korzyści:

- W przypadku złośliwego niejawnego programu testów, który kopiuje i eksportuje prawidłowy token dostępu poza organizację, ciągłe oceny dostępu zapobiegają użyciu tego tokenu za pośrednictwem zasad lokalizacji adresu IP usługi Azure AD. W przypadku ciągłego uwierzytelniania dostępu usługa Azure AD synchronizuje zasady w dół do obsługiwanych usług Microsoft 365, więc gdy token dostępu próbuje uzyskać dostęp do usługi spoza zakresu adresów IP zasad, usługa odrzuca token.

- Ciągłe oceny dostępu zwiększają odporność dzięki mniejszej częstotliwości odświeżania tokenów. Ponieważ usługi pomocy technicznej otrzymują proaktywne powiadomienia o konieczności ponownego uwierzytelniania, usługa Azure AD może wydawać tokeny, które są dłużej aktywne, na przykład dłużej niż godzina. W przypadku tokenów, w których czas pracy jest dłuższy, klienci nie muszą tak często żądać odświeżania tokenu w usłudze Azure AD, więc środowisko użytkownika jest bardziej odporne.

Oto kilka przykładów sytuacji, w których ciągłe ocenianie dostępu zwiększa bezpieczeństwo kontroli dostępu użytkownika:

- Hasło użytkownika zostało naruszone, więc administrator unieważni wszystkie istniejące sesje i zresetował je z centrum administracyjne platformy Microsoft 365. W czasie rzeczywistym wszystkie istniejące sesje użytkowników z Microsoft 365 zostaną unieważnione.

- Użytkownik pracujący nad dokumentem w programie Word przenosi tablet do publicznej kawiarni, która nie znajduje się w zdefiniowanym przez administratora i zatwierdzonym zakresie adresów IP. W kawiarni dostęp użytkownika do dokumentu jest natychmiast zablokowany.

Na Microsoft 365 program oceny dostępu ciągłego jest obecnie obsługiwany przez:

- Exchange, SharePoint i Teams usługi.
- Outlook, Teams, Office i OneDrive w przeglądarce internetowej oraz dla klientów systemów Win32, iOS, Android i Mac.

Firma Microsoft pracuje nad dodatkowymi Microsoft 365 usługami i klientami w celu obsługi oceny ciągłego dostępu.

Ocena dostępu ciągłego zostanie uwzględniona we wszystkich wersjach programu Office 365 i Microsoft 365. Konfigurowanie zasad dostępu warunkowego wymaga Azure AD — wersja Premium P1, która jest zawarta we wszystkich Microsoft 365 wersjach.

> [!NOTE]
> Zobacz [ten artykuł,](/azure/active-directory/conditional-access/concept-continuous-access-evaluation#limitations) aby uzyskać informacje na temat ograniczeń oceny dostępu ciągłego.

## <a name="scenarios-supported-by-microsoft-365"></a>Scenariusze obsługiwane przez Microsoft 365

Ocena dostępu ciągłego obsługuje dwa typy zdarzeń:

- Zdarzenia krytyczne to te, w których użytkownik powinien utracić dostęp.
- Ocena zasad dostępu warunkowego występuje, gdy użytkownik powinien utracić dostęp do zasobu na podstawie zasad zdefiniowanych przez administratora.

Zdarzenia krytyczne to między innymi:

- Konto użytkownika jest wyłączone
- Zmieniono hasło
- Sesje użytkowników zostały odwołane
- Uwierzytelnianie wieloskładnikowe jest włączone dla użytkownika
- Ryzyko związane z kontem zwiększa się na podstawie oceny dostępu z usługi [Azure AD Identity Protection](/azure/active-directory/identity-protection/overview-identity-protection)

Ocena zasad dostępu warunkowego jest wtedy, gdy konto użytkownika nie łączy się już z zaufaną siecią.

Poniższe Microsoft 365 obecnie obsługują ocenę dostępu ciągłego, nasłuchiwanie zdarzeń z usługi Azure AD.

<br>

****

|Typ wymuszania|Exchange|SharePoint|Teams|
|---|---|---|---|
|**Zdarzenia krytyczne:**||||
|Odwołania użytkowników|Obsługiwane|Obsługiwane|Obsługiwane|
|Ryzyko użytkownika|Obsługiwane|Nieobsługiwane|Nieobsługiwane|
|**Ocena zasad dostępu warunkowego:**||||
|Zasady lokalizacji adresów IP|Obsługiwane|Obsługiwane\*|Obsługiwane|
|

\*SharePoint Office dostęp do przeglądarki sieci Web obsługuje błyskawiczne wymuszanie zasad ip przez włączenie trybu ścisłego. Bez trybu ścisłego okres istnienia tokenu dostępu wynosi jedną godzinę.

Aby uzyskać więcej informacji na temat sposobu skonfigurowania zasad dostępu warunkowego, [zobacz ten artykuł](/azure/active-directory/conditional-access/overview).

## <a name="microsoft-365-clients-supporting-continuous-access-evaluation"></a>Microsoft 365 klientów obsługujący ocenę dostępu ciągłego

Klienci programu Microsoft 365 z włączoną oceną dostępu ciągłego obsługują wyzwanie żądania, które polega na przekierowaniu sesji użytkownika do usługi Azure AD w celu ponownego uwierzytelnienia, gdy token użytkownika w pamięci podręcznej zostanie odrzucony przez usługę sieci Microsoft 365 z włączoną oceny dostępu ciągłego.

Następujący klienci obsługują ocenę ciągłego dostępu w sieci Web, systemach Win32, iOS, Android i Mac:

- Outlook
- Teams
- Pakiet Office\*
- SharePoint
- OneDrive

\*Żądanie wyzwania nie jest obsługiwane w Office sieci Web.

W przypadku klientów, którzy nie obsługują uwierzytelniania dostępu ciągłego, okres istnienia tokenu dostępu do Microsoft 365 jest domyślnie jedną godziną.

## <a name="see-also"></a>Zobacz też

- [Ocena dostępu ciągłego](/azure/active-directory/conditional-access/concept-continuous-access-evaluation)
- [Dokumentacja programu Access warunkowa](/azure/active-directory/conditional-access/overview)
- [Dokumentacja usługi Azure AD Identity Protection](/azure/active-directory/identity-protection/overview-identity-protection)
