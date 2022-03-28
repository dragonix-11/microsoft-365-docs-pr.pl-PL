---
title: Ograniczanie możliwości zapraszania gości
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.collection:
- SPO_Content
- M365-collaboration
- m365solution-securecollab
- m365solution-scenario
- m365initiative-externalcollab
ms.localizationpriority: medium
f1.keywords: NOCSH
recommendations: false
description: Dowiedz się, jak ograniczyć liczbę osób, które mogą zapraszać gości do organizacji.
ms.openlocfilehash: d8eb9452abb76916940d10fa042dae479358568a
ms.sourcegitcommit: 46456ca009c9d50622e57e24269be74986184654
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2022
ms.locfileid: "63717318"
---
# <a name="limit-who-can-invite-guests"></a>Ograniczanie możliwości zapraszania gości

Możesz ograniczyć liczbę osób w organizacji, które mogą zapraszać gości. Konta gości mogą być używane do udostępniania zespołów, SharePoint witryn, plików i folderów osobom spoza organizacji.

Jeśli w Twoich procesach biznesowych wymagane jest ograniczenie liczby osób, które mogą udostępniać gościom, lub jeśli chcesz, aby użytkownicy ukończyli szkolenia zanim będą mogli udostępniać gościom, możesz ograniczyć liczbę osób, które mogą udostępniać, używając roli zapraszania gościa w programie Azure Active Directory.

## <a name="create-a-security-group-for-people-allowed-to-invite-guests"></a>Tworzenie grupy zabezpieczeń dla osób, które mogą zapraszać gości

Pierwszym krokiem jest utworzenie grupy zabezpieczeń dla użytkowników, którzy będą mogli zapraszać gości. Pamiętaj, aby skonfigurować tę grupę, aby zezwolić na rolę usługi Azure AD, a następnie przypisać jej rolę Zapraszanie gościa.

Aby utworzyć grupę zabezpieczeń dla osób zapraszanych gości
1. Zaloguj się, [Azure Active Directory](https://aad.portal.azure.com) administratora globalnego lub konta administratora zabezpieczeń.
1. Na stronie **Usługi Active Directory** wybierz pozycję **Grupy** , a następnie wybierz pozycję **Nowa grupa**.
1. Wybierz **pozycję** Zabezpieczenia dla **typu grupy**.
1. Wpisz **nazwę grupy.** 
1. Opcjonalnie dodaj opis grupy.
1. W **przypadku przypisywania ról usługi Azure AD do grupy** wybierz pozycję **Tak**.
1. Dodaj właścicieli i członków grupy.
1. W **obszarze Role** wybierz pozycję **Brak zaznaczonych ról**.
1. Wyszukaj i wybierz rolę **zapraszania gościa** , a następnie wybierz pozycję **Wybierz**.
1. Wybierz **pozycję** Utwórz i potwierdź, że chcesz, aby grupa, do której można przypisywać role. Twoja grupa zostanie utworzona i będzie gotowa do dodawania członków.

## <a name="configure-external-collaboration-settings"></a>Konfigurowanie ustawień współpracy zewnętrznej

Po utworzeniu grupy zabezpieczeń i dodaniu użytkowników, którzy mają mieć możliwość zapraszania gości, następnym krokiem jest skonfigurowanie ustawień współpracy zewnętrznej usługi Azure AD w celu umożliwienia zapraszania gości tylko użytkownikom z rolą zapraszania gości.

Uwaga: niezależnie od tego ustawienia administratorzy globalni mogą zawsze zapraszać gości.

> [!NOTE]
> Zmiany ustawień dostępu między dzierżawami mogą potrwać dwie godziny.

Aby skonfigurować usługę Azure AD w celu ograniczenia zaproszeń gości do roli zapraszania gościa
1. W [Azure Active Directory](https://aad.portal.azure.com/) wybierz pozycję **Tożsamości zewnętrzne**.
1. Wybierz **pozycję Ustawienia współpracy zewnętrznej**.
1. W **obszarze Ustawienia zapraszania gości** wybierz pozycję **Tylko użytkownicy przypisani do określonych ról administratora mogą zapraszać gości**.
1. Wybierz **Zapisz**.

## <a name="related-topics"></a>Tematy pokrewne

[Zezwalaj tylko użytkownikom z określonych grup zabezpieczeń na zewnętrzne udostępnianie w SharePoint i OneDrive](/sharepoint/manage-security-groups)

[Włącz współpracę zewnętrzną B2B i zarządzaj tym, kto może zapraszać gości](/azure/active-directory/external-identities/delegate-invitations)