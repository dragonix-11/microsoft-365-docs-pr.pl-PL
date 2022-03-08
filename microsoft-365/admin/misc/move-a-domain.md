---
title: Przenoszenie domeny zweryfikowane na koncie niezawiązyanym
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
description: Dowiedz się, jak dołączyć do konta niezamanektowego w celu usunięcia domeny z konta i dodania tej domeny do swojego konta.
ms.openlocfilehash: 7b7befdae4279b4b08ff076b88ed552b2bc411c3
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63326346"
---
# <a name="move-a-domain-verified-in-an-unmanaged-account"></a>Przenoszenie domeny zweryfikowane na koncie niezawiązyanym

 **[Zajrzyj do często zadawanych pytań dotyczących domen](../setup/domains-faq.yml)**, jeśli nie możesz znaleźć szukanych informacji.

Jeśli jesteś administratorem i próbujesz dodać domenę do konta platformy Microsoft 365, ale domena została zablokowana, ponieważ domena została zweryfikowana dla konta niezawiązywana, możesz zostać administratorem na koncie niezawiązyanym, aby usunąć domenę i dodać ją do swojego konta.

> [!NOTE]
> Samodzielne tworzenie konta w dowolnej usłudze w chmurze, która korzysta z usługi Azure AD, powoduje dodanie użytkownika do niezazadowonianego lub "cienia" katalogu Azure AD i utworzenie konta niezazadowońnego. Niezamanektowane konto to katalog bez administratora globalnego. Aby określić, czy konto jest zarządzane, czy nieza zarządzaniem, zobacz [Określanie typu dzierżawy](/power-platform/admin/powerapps-gdpr-dsr-guide-systemlogs#determining-tenant-type).
  
## <a name="before-you-begin"></a>Przed rozpoczęciem

Czasami nie można dodać domeny do konta organizacji, ponieważ inna osoba już załozyła konto na platformie Microsoft 365 przy użyciu adresu e-mail skojarzonego z tą nazwą domeny. Możesz jednak usunąć domenę z innego konta w stanie wykonania i dodać ją do konta organizacji.

Najpierw musisz dołączyć do konta niezamówinego i zostać administratorem tego konta (kroki 1–3). Następnie możesz usunąć domenę z konta (krok 4), zalogować się ponownie do konta organizacji i dodać domenę do swojego konta (krok 5).

## <a name="step-1-get-an-invitation-to-join-the-unmanaged-account"></a>Krok 1. Uzyskiwanie zaproszenia do dołączenia do konta niezamanektowego

Po próbie dodania domeny do konta może zostać wyświetlony komunikat informujący, że ktoś już zalogował się na platformie Microsoft 365 za pomocą adresu e-mail. Krok 1 to żądanie zaproszenia do dołączenia do drugiego konta i rozpoczęcie procesu przejęcia roli administratora.

1. Przejdź do centrum administracyjnego platformy Microsoft 365 i > **SettingsDomains** >  > **+ Dodaj** domenę i dodaj nazwę domeny.

1. Jeśli zobaczysz komunikat informujący, że nie możesz dodać domeny, ponieważ inne osoby już je załozyły przy użyciu adresu e-mail dla tej domeny, wprowadź nazwę użytkownika konta, a następnie wybierz pozycję Wyślij mi **zaproszenie**.

1. Wyloguj się z bieżącego konta, aby zalogować się na niezamówione konto.

    Sprawdź w wiadomości e-mail zaproszenie, które pomoże Ci dołączyć do konta niezakieregotowego, i wybierz link podany w wiadomości e-mail.

    Wprowadź kod **weryfikacyjny z wiadomości** e-mail, aby zweryfikować swój adres e-mail.

## <a name="step-2-complete-signup-with-email-instructions"></a>Krok 2. Ukończ rejestracja przy użyciu instrukcji poczty e-mail

1. Po wprowadzeniu kodu weryfikacyjnego zostaniesz przekierowyny do strony, na której możesz utworzyć nowe konto.

2. Wypełnij pola nazwy użytkownika i hasła konta, którego chcesz użyć, a następnie wykonaj kroki tworzenia konta.

## <a name="step-3-verify-domain-ownership-and-become-the-admin"></a>Krok 3. Zweryfikuj własność domeny i zostań administratorem

1. Po zakończeniu kroku 2 wybierz ikonę centrum administracyjnego w lewym okienku nawigacji (ewentualnie przejdź do przeglądarki i wpisz ).`https://admin.microsoft.com`

    Nastąpi przekierowanie do kreatora przejęcia roli administratora.

1. Wybierz **pozycję Dalej** i sprawdź, czy jesteś właścicielem domeny, którą chcesz przejąć, dodając rekord TXT u rejestratora domen.

    Kreator udostępni rekord TXT do dodania, a także link do witryny internetowej twojego rejestratora oraz link do instrukcji krok po kroku.

1. Na **stronie Jesteś teraz administratorem** wybierz pozycję **Przejdź do centrum administracyjnego**.

    Masz teraz uprawnienia administratora wymagane do usunięcia domeny z wcześniej niezaimkówtowego konta.

## <a name="step-4-remove-a-domain-from-the-unmanaged-account"></a>Krok 4. Usuwanie domeny z konta niezawiązywana

1. Przejdź do **strony** **UżytkownicyAktywowanie** >  użytkowników dla konta, do którego dołączyć w kroku 2, a następnie wybierz nazwę wyświetlaną dla nazwy użytkownika, przy użyciu którego się zalogowano.

1. W **obszarze Nazwa** użytkownika wybierz pozycję **Zarządzaj** nazwą użytkownika i przenieś użytkownika do domeny onmicrosoft, wybierając onmicrosoft.com z listy rozwijanej.

1. Wyloguj się z konta i zaloguj się ponownie przy użyciu nowego `username@account.onmicrosoft.com`konta .

1. Wybierz **pozycję** **SettingsDomains** >  ,zlokalizuj domenę, którą chcesz dodać do innego konta, a następnie wybierz pozycję **Usuń domenę**.

    Jeśli zostaniesz poproszony o wybranie innej domeny jako domyślnej, wybierz domenę onmicrosoft.com domenę.

    Jeśli inni użytkownicy korzystają z tej domeny, należy je usunąć. Wybierz jedną z opcji: **Automatycznie** usuń, ręcznie przenieś użytkowników do domeny lub całkowicie usuń użytkowników.

   > [!NOTE]
   > Sprawdź ponownie, ponieważ usunięcie domeny z konta może trochę potrwać. Usuwanie zostanie ukończone, gdy domena zniknie z konta.

1. Wyloguj się z konta.

## <a name="step-5-add-the-domain-to-your-account"></a>Krok 5. Dodawanie domeny do konta

1. Zaloguj się do konta, do którego chcesz dodać domenę.

1. Wybierz **pozycję** **SettingsDomains** >  > **+ Dodaj** domenę, a następnie wprowadź nazwę domeny, aby kontynuować kroki kreatora w celu zweryfikowania własności domeny na tym koncie i ukończenia dodawania domeny do swojego konta.
  
## <a name="related-content"></a>Zawartość pokrewna

[Przeprowadzanie przejęcia administratora wewnętrznego](become-the-admin.md) (artykuł)
