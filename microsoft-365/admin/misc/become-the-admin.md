---
title: Wykonywanie wewnętrznego przejęcia przez administratora
f1.keywords:
- CSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_NonTOC
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: b9707ec8-2247-4e25-9bad-f11ddbc686e4
description: Dowiedz się, jak zweryfikować własność poczty e-mail i domeny w celu przejęcia niezarządzanego konta utworzonego przez samoobsługową rejestrację użytkownika w usłudze Microsoft 365.
ms.openlocfilehash: b930e9d4774dc9271d4bcbd93ffb9e5ced577dab
ms.sourcegitcommit: 8a0de6240facfe26ee391a14076b7fe534ee6598
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/07/2022
ms.locfileid: "65922136"
---
# <a name="internal-admin-takeover"></a>Przejęcie przez administratora wewnętrznego

 **[Zajrzyj do często zadawanych pytań dotyczących domen](../setup/domains-faq.yml)**, jeśli nie możesz znaleźć szukanych informacji.

Jeśli jesteś administratorem i chcesz przejąć niezarządzane konto utworzone przez samoobsługową rejestrację użytkownika, możesz wykonać przejęcie przez administratora wewnętrznego, wykonując kroki opisane w tym artykule.

> [!NOTE]
> Samoobsługowa rejestracja w dowolnej usłudze w chmurze, która korzysta z usługi Azure AD, dodaje użytkownika do katalogu usługi Azure AD niezarządzanego lub "w tle" i tworzy konto niezarządzane. Konto niezarządzane to katalog bez administratora globalnego. Aby określić, czy konto jest zarządzane, czy niezarządzane, zobacz [Określanie typu dzierżawy](/power-platform/admin/powerapps-gdpr-dsr-guide-systemlogs#determining-tenant-type). 
  
## <a name="before-you-begin"></a>Przed rozpoczęciem

Gdy użytkownik zarejestruje się w usługach Platformy Microsoft 365 przy użyciu adresu e-mail, automatycznie zostanie dla niego utworzone konto. Jeśli administrator chce zarządzać użytkownikami na koncie lub kupić dodatkowe usługi platformy Microsoft 365, musi zostać administratorem konta, wykonując następujące kroki, aby przeprowadzić przejęcie przez administratora.

## <a name="step-1-verify-your-email-address"></a>Krok 1. Weryfikowanie adresu e-mail

> [!NOTE]
> Jeśli na Twoim koncie włączono samoobsługę, użytkownicy mogą samodzielnie subskrybować bezpłatne usługi, takie jak Power BI. Te usługi są przeznaczone do użytku w przypadkach, gdy subskrypcja użytkownika samoobsługi utworzyła niezarządzane konto, które chcesz przejąć jako administrator. W kroku 1 utworzysz konto użytkownika dla domeny, którą chcesz usunąć za pomocą usługi Power BI, aby uruchomić kreatora przejęcia administratora, aby można było zostać administratorem niezarządzanego konta domeny.

1. Aby zarejestrować się w usłudze Power BI, przejdź do [witryny usługi Power BI](https://powerbi.com) i wybierz pozycję **Rozpocznij bezpłatną** > **wersję próbną (** w polu Udostępnij w usłudze Power BI Pro). 

2. Utwórz konto użytkownika, które używa nazwy domeny organizacji (na przykład `powerbiadmin@contoso.com`). Jeśli Twoje konto jest już używane, zaloguj się przy użyciu bieżącego hasła.

3. Sprawdź swój adres e-mail pod kątem **kodu weryfikacyjnego** i wprowadź kod, aby zweryfikować swój adres e-mail.

## <a name="step-2-create-a-new-account-for-admin-access"></a>Krok 2. Tworzenie nowego konta na potrzeby dostępu administratora

1. Po wprowadzeniu kodu weryfikacyjnego nastąpi przejście do strony, na której można utworzyć nowe konto.

2. Wypełnij pola nazwy użytkownika i hasła kontem, którego chcesz użyć, a następnie wykonaj kroki tworzenia konta.

## <a name="step-3-verify-domain-ownership-and-become-the-admin"></a>Krok 3. Weryfikowanie własności domeny i zostać administratorem

1. Po ukończeniu kroku 2 wybierz ikonę centrum administracyjnego w okienku nawigacji po lewej stronie (alternatywnie przejdź do przeglądarki i wpisz `https://admin.microsoft.com`ciąg ).

    Nastąpi przekierowanie do kreatora przejęcia administratora.

2. Wybierz pozycję **Dalej** i sprawdź, czy jesteś właścicielem domeny, którą chcesz przejąć, dodając rekord TXT do rejestratora domen.

    Kreator udostępni ci rekord TXT do dodania, a także udostępni link do witryny internetowej rejestratora oraz link do instrukcji krok po kroku.

3. Na stronie **Jesteś teraz administratorem** wybierz pozycję **Przejdź do centrum administracyjnego**.

    Masz uprawnienia administratora wymagane do zarządzania kontem w centrum administracyjnym. Możesz na przykład zarządzać użytkownikami i grupami kont, kupować nowe subskrypcje i przypisyać użytkowników oraz zarządzać domenami kont.

    Jeśli chcesz usunąć domenę z tego konta, aby można było dodać ją do innego konta, zobacz [Usuwanie domeny z innego konta](remove-a-domain-from-another-account.md).
  
## <a name="related-content"></a>Zawartość pokrewna

YouTube: [Trzy kroki do przejęcia przez administratora IT usługi Power BI i platformy Microsoft 365](https://www.youtube.com/watch?v=xt5EsrQBZZk) (wideo)\
[Przejęcie przez administratora w usłudze Azure AD](/azure/active-directory/users-groups-roles/domains-admin-takeover) (artykuł)\
[Korzystanie z samoobsługowej rejestracji w organizacji](self-service-sign-up.md) (artykuł)\
[Omówienie roli administratora usługi Power BI](/power-bi/service-admin-role) (artykuł)