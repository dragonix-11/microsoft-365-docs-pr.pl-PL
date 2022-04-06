---
title: Konfigurowanie laboratorium próbnego Microsoft 365 Defender lub środowiska pilotażowego
description: Uzyskaj dostęp do portalu Microsoft 365 Defender, a następnie skonfiguruj środowisko laboratorium Microsoft 365 Defender próbnego
keywords: Microsoft 365 Defender konfiguracja wersji próbnej, Microsoft 365 Defender konfiguracja pilotażowa, spróbuj Microsoft 365 Defender, Microsoft 365 Defender konfigurację laboratorium ewaluacyjnego
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: lovina-saldanha
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-scenario
- m365solution-evalutatemtp
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: 5d516a7062d8c6f617cee2a260f27ee896689f2c
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2022
ms.locfileid: "64667345"
---
# <a name="set-up-your-microsoft-365-defender-trial-in-a-lab-environment"></a>Konfigurowanie wersji próbnej Microsoft 365 Defender w środowisku laboratoryjnym 

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Dotyczy:**
- Microsoft 365 Defender 

W tym temacie opisano konfigurowanie dedykowanego środowiska laboratoryjnego. Aby uzyskać informacje na temat konfigurowania wersji próbnej w środowisku produkcyjnym, zobacz nowy przewodnik [Evaluate and pilot Microsoft 365 Defender (Ocena i pilotaż Microsoft 365 Defender](eval-overview.md)). 

## <a name="create-an-office-365-e5-trial-tenant"></a>Tworzenie dzierżawy wersji próbnej Office 365 E5
>[!NOTE]
>Jeśli masz już istniejącą subskrypcję Office 365 lub Azure Active Directory, możesz pominąć kroki tworzenia dzierżawy Office 365 E5 wersji próbnej.

1. Przejdź do [portalu produktu Office 365 E5](https://www.microsoft.com/microsoft-365/business/office-365-enterprise-e5-business-software?activetab=pivot%3aoverviewtab) i wybierz pozycję **Bezpłatna wersja próbna**.

   :::image type="content" source="../../media/mtp-eval-9.png" alt-text="Strona bezpłatnej wersji próbnej Office 365 E5" lightbox="../../media/mtp-eval-9.png":::
  
2. Zakończ rejestrację próbną, wprowadzając swój adres e-mail (osobisty lub firmowy). Kliknij **pozycję Skonfiguruj konto**.

   :::image type="content" source="../../media/mtp-eval-10.png" alt-text="Strona konfiguracji rejestracji wersji próbnej Office 365 E5" lightbox="../../media/mtp-eval-10.png":::

3. Podaj imię, nazwisko, numer telefonu służbowego, nazwę firmy, rozmiar firmy oraz kraj lub region.  

   :::image type="content" source="../../media/mtp-eval-11.png" alt-text="Strona konfiguracji rejestracji wersji próbnej Office 365 E5 z prośbą o podanie nazwy, telefonu i szczegółów firmy" lightbox="../../media/mtp-eval-11.png":::
   
   > [!NOTE]
   > Kraj lub region, który został tutaj ustawiony, określa region centrum danych, w Office 365 będzie hostowany.
  
4. Wybierz preferencję weryfikacji: za pośrednictwem wiadomości SMS lub połączenia. Kliknij **pozycję Wyślij kod weryfikacyjny**. 

   :::image type="content" source="../../media/mtp-eval-12.png" alt-text="Strona konfiguracji rejestracji wersji próbnej Office 365 E5 z prośbą o preferencję weryfikacji" lightbox="../../media/mtp-eval-12.png":::

5. Ustaw niestandardową nazwę domeny dla dzierżawy, a następnie kliknij przycisk **Dalej**.

   :::image type="content" source="../../media/mtp-eval-13.png" alt-text="Strona konfiguracji rejestracji wersji próbnej Office 365 E5, na której można skonfigurować niestandardową nazwę domeny" lightbox="../../media/mtp-eval-13.png":::
 
6. Skonfiguruj pierwszą tożsamość, która będzie administratorem globalnym dzierżawy. Wypełnij **pola Nazwa** i **Hasło**. Kliknij **pozycję Zarejestruj się**.

   :::image type="content" source="../../media/mtp-eval-14.png" alt-text="Strona konfiguracji rejestracji wersji próbnej Office 365 E5, na której można ustawić tożsamość biznesową" lightbox="../../media/mtp-eval-14.png":::

7. Kliknij **pozycję Przejdź do instalatora**, aby ukończyć aprowizację dzierżawy Office 365 E5 wersji próbnej.

   :::image type="content" source="../../media/mtp-eval-15.png" alt-text="Strona konfiguracji rejestracji wersji próbnej Office 365 E5 monitująca o kliknięcie przycisku Przejdź do instalatora" lightbox="../../media/mtp-eval-15.png":::

8. Połączenie domenę firmową do dzierżawy Office 365. [Opcjonalnie] Wybierz **Połączenie domenę, którą już posiadasz**, i wpisz nazwę domeny. Kliknij **Dalej**.

   :::image type="content" source="../../media/mtp-eval-16.png" alt-text="Strona konfiguracji Office 365 E5, na której należy spersonalizować logowanie i wiadomość e-mail" lightbox="../../media/mtp-eval-16.png":::
 
9. Dodaj rekord TXT lub MX, aby zweryfikować własność domeny. Po dodaniu rekordu TXT lub MX do domeny wybierz pozycję **Sprawdź**.

   :::image type="content" source="../../media/mtp-eval-17.png" alt-text="Strona konfiguracji Office 365 E5, na której należy dodać rekord TXT MX, aby zweryfikować domenę" lightbox="../../media/mtp-eval-17.png":::
 
10. [Opcjonalnie] Utwórz więcej kont użytkowników dla dzierżawy. Możesz pominąć ten krok, klikając przycisk **Dalej**.

    :::image type="content" source="../../media/mtp-eval-18.png" alt-text="Strona konfiguracji Office 365 E5, na której można dodać więcej użytkowników" lightbox="../../media/mtp-eval-18.png":::
 
11. [Opcjonalnie] Pobierz aplikacje Office. Kliknij przycisk **Dalej** , aby pominąć ten krok. 

    :::image type="content" source="../../media/mtp-eval-19.png" alt-text="Strona Office 365 E5, na której można instalować aplikacje Office" lightbox="../../media/mtp-eval-19.png":::

12. [Opcjonalnie] Migrowanie wiadomości e-mail. Ponownie możesz pominąć ten krok.

    :::image type="content" source="../../media/mtp-eval-20.png" alt-text="Office 365 E5, w którym można określić, czy chcesz migrować wiadomości e-mail, czy nie" lightbox="../../media/mtp-eval-20.png":::
 
13. Wybierz pozycję Usługi online. Wybierz **pozycję Exchange** i kliknij przycisk **Dalej**. 

    :::image type="content" source="../../media/mtp-eval-21.png" alt-text="Office 365 E5, w którym można wybrać Usługi online" lightbox="../../media/mtp-eval-21.png":::

14. Dodaj rekordy MX, CNAME i TXT do domeny. Po zakończeniu wybierz pozycję **Sprawdź**.

    :::image type="content" source="../../media/mtp-eval-22.png" alt-text="W tym miejscu Office 365 E5 można dodać rekordy DNS" lightbox="../../media/mtp-eval-22.png":::
 
15. Gratulacje, zakończono aprowizację dzierżawy Office 365.

    :::image type="content" source="../../media/mtp-eval-23.png" alt-text="Strona potwierdzenia ukończenia konfiguracji Office 365 E5" lightbox="../../media/mtp-eval-23.png":::
    

## <a name="enable-microsoft-365-trial-subscription"></a>Włączanie subskrypcji wersji próbnej Microsoft 365

>[!NOTE]
>Rejestracja w wersji próbnej daje 25 licencji użytkowników do użycia przez miesiąc. Aby uzyskać szczegółowe informacje[, zobacz Try or buy a Microsoft 365 subscription (Wypróbuj lub kup subskrypcję Microsoft 365](../../commerce/try-or-buy-microsoft-365.md)).

1. W [centrum Administracja Microsoft 365](https://admin.microsoft.com/) kliknij pozycję **Rozliczenia**, a następnie przejdź do pozycji **Kup usługi**.

2. Wybierz **pozycję Microsoft 365 E5** i kliknij pozycję **Rozpocznij bezpłatną wersję próbną**. 

   :::image type="content" source="../../media/mtp-eval-24.png" alt-text="Strona Microsoft 365 E5 Rozpocznij bezpłatną wersję próbną" lightbox="../../media/mtp-eval-24.png":::

3. Wybierz preferencję weryfikacji: za pośrednictwem wiadomości SMS lub połączenia. Po podjęciu decyzji wprowadź numer telefonu, wybierz pozycję **Wyślij wiadomość SMS** lub **Zadzwoń do mnie** w zależności od wybranego wyboru.

   :::image type="content" source="../../media/mtp-eval-25.png" alt-text="Strona Microsoft 365 E5 Rozpocznij bezpłatną wersję próbną z prośbą o podanie danych kontaktowych w celu wysłania kodu, aby udowodnić, że nie jesteś robotem" lightbox="../../media/mtp-eval-25.png":::
 
4. Wprowadź kod weryfikacyjny i kliknij pozycję **Rozpocznij bezpłatną wersję próbną**.

   :::image type="content" source="../../media/mtp-eval-26.png" alt-text="Strona Microsoft 365 E5 Rozpocznij bezpłatną wersję próbną, na której można wypełnić kod weryfikacyjny wysłany przez system, aby udowodnić, że nie jesteś robotem" lightbox="../../media/mtp-eval-26.png":::

5. Kliknij **pozycję Wypróbuj teraz**, aby potwierdzić Microsoft 365 E5 wersji próbnej.

   :::image type="content" source="../../media/mtp-eval-27.png" alt-text="Strona Microsoft 365 E5 Rozpocznij bezpłatną wersję próbną, na której należy uruchomić przycisk Wypróbuj teraz" lightbox="../../media/mtp-eval-27.png":::
 
6. Przejdź do **obszaru Administracja Microsoft 365** CenterUsersActive users ( Centrum  >  Administracja Microsoft 365 **UżytkownicyAktywni** >  **użytkownicy**). Wybierz konto użytkownika, wybierz pozycję **Zarządzaj licencjami produktów**, a następnie zamień licencję z Office 365 E5 na **Microsoft 365 E5**. Kliknij **Zapisz**.

   :::image type="content" source="../../media/mtp-eval-28.png" alt-text="Strona centrum Administracja Microsoft 365, na której można wybrać licencję Microsoft 365 E5" lightbox="../../media/mtp-eval-28.png":::
 
7. Ponownie wybierz konto administratora globalnego, a następnie kliknij pozycję **Zarządzaj nazwą użytkownika**.

   :::image type="content" source="../../media/mtp-eval-29.png" alt-text="Strona centrum Administracja Microsoft 365, na której można wybrać pozycję Konto i zarządzać nazwą użytkownika" lightbox="../../media/mtp-eval-29.png":::

8. [Opcjonalnie] Zmień domenę z *onmicrosoft.com* na własną domenę — w zależności od tego, co wybrano w poprzednich krokach. Kliknij przycisk **Zapisz zmiany**.

   :::image type="content" source="../../media/mtp-eval-30.png" alt-text="Strona centrum Administracja Microsoft 365, na której można zmienić preferencje domeny" lightbox="../../media/mtp-eval-30.png":::

## <a name="next-step"></a>Następny krok
|[Faza 3. Konfigurowanie dołączania &](config-m365d-eval.md) | Skonfiguruj każdy filar Microsoft 365 Defender dla laboratorium próbnego Microsoft 365 Defender lub środowiska pilotażowego i dołącz punkty końcowe.
|:-------|:-----|
