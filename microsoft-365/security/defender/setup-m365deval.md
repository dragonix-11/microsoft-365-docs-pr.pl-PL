---
title: Konfigurowanie laboratorium Microsoft 365 Defender próbnego lub środowiska pilotażowego
description: Program Access Microsoft 365 Defender następnie skonfiguruj środowisko laboratorium Microsoft 365 Defender próbnego
keywords: Microsoft 365 Defender konfiguracji wersji próbnej, Microsoft 365 Defender pilotażowej, Microsoft 365 Defender, Microsoft 365 Defender laboratorium oceny
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
ms.openlocfilehash: 681d9798c6f16f5829bdb4e5272abc3eac719a59
ms.sourcegitcommit: 3b8e009ea1ce928505b8fc3b8926021fb91155f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/28/2022
ms.locfileid: "64500986"
---
# <a name="set-up-your-microsoft-365-defender-trial-in-a-lab-environment"></a>Konfigurowanie wersji próbnej Microsoft 365 Defender w środowisku laboratoryjnym 

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Dotyczy:**
- Microsoft 365 Defender 

Ten temat zawiera wskazówki dotyczące skonfigurowania dedykowanego środowiska laboratoryjnych. Aby uzyskać informacje na temat konfigurowania wersji próbnej w środowisku produkcyjnym, zobacz nowy przewodnik dotyczący oceny i [Microsoft 365 Defender](eval-overview.md) pilotażowego. 

## <a name="create-an-office-365-e5-trial-tenant"></a>Tworzenie dzierżawy Office 365 E5 próbnej
>[!NOTE]
>Jeśli masz już istniejącą subskrypcję usługi Office 365 lub Azure Active Directory, możesz pominąć procedurę tworzenia Office 365 E5 wersji próbnej.

1. Przejdź do portalu [Office 365 E5 produktu i](https://www.microsoft.com/microsoft-365/business/office-365-enterprise-e5-business-software?activetab=pivot%3aoverviewtab) wybierz pozycję **Bezpłatna wersja próbna**.

   :::image type="content" source="../../media/mtp-eval-9.png" alt-text="Strona Office 365 E5 wersji próbnej" lightbox="../../media/mtp-eval-9.png":::
  
2. Ukończ rejestrację w wersji próbnej, wprowadzając swój adres e-mail (osobisty lub firmowy). Kliknij **pozycję Skonfiguruj konto**.

   :::image type="content" source="../../media/mtp-eval-10.png" alt-text="Strona konfiguracji Office 365 E5 rejestracji wersji próbnej" lightbox="../../media/mtp-eval-10.png":::

3. Wprowadź swoje imię, nazwisko, służbowy numer telefonu, nazwę firmy, rozmiar firmy oraz kraj lub region.  

   :::image type="content" source="../../media/mtp-eval-11.png" alt-text="Strona konfiguracji Office 365 E5 próbnej z prośbą o imię i nazwisko, telefon i szczegóły firmy" lightbox="../../media/mtp-eval-11.png":::
   
   > [!NOTE]
   > Kraj lub region ustawiony tutaj określa region centrum danych, Office 365 będzie hostowany.
  
4. Wybierz preferencje weryfikacji: za pośrednictwem wiadomości SMS lub połączenia. Kliknij **pozycję Wyślij kod weryfikacyjny**. 

   :::image type="content" source="../../media/mtp-eval-12.png" alt-text="Strona konfiguracji Office 365 E5 wersji próbnej z pytaniem o preferencje weryfikacji" lightbox="../../media/mtp-eval-12.png":::

5. Ustaw niestandardową nazwę domeny dla dzierżawy, a następnie kliknij przycisk **Dalej**.

   :::image type="content" source="../../media/mtp-eval-13.png" alt-text="Strona konfiguracji Office 365 E5 rejestracji wersji próbnej, na której można skonfigurować niestandardową nazwę domeny" lightbox="../../media/mtp-eval-13.png":::
 
6. Skonfiguruj pierwszą tożsamość, która będzie administratorem globalnym dzierżawy. Wypełnij pola **Nazwa** i **hasło**. Kliknij **pozycję Zarejestruj się**.

   :::image type="content" source="../../media/mtp-eval-14.png" alt-text="Strona Office 365 E5 rejestracji wersji próbnej, na której można ustawić tożsamość biznesową" lightbox="../../media/mtp-eval-14.png":::

7. Kliknij **pozycję Przejdź do instalatora**, aby ukończyć inicjowanie obsługi Office 365 E5 próbnej dzierżawy.

   :::image type="content" source="../../media/mtp-eval-15.png" alt-text="Strona Office 365 E5 rejestracji wersji próbnej z monitem o kliknięcie przycisku Przejdź do konfiguracji" lightbox="../../media/mtp-eval-15.png":::

8. Połączenie firmowej do dzierżawy Office 365 dzierżawy. [Opcjonalnie] Wybierz **Połączenie nazwę domeny, która już należy do** Ciebie, i wpisz nazwę domeny. Kliknij **Dalej**.

   :::image type="content" source="../../media/mtp-eval-16.png" alt-text="Strona Office 365 E5, na której należy spersonalizować logowanie i adres e-mail" lightbox="../../media/mtp-eval-16.png":::
 
9. Dodaj rekord TXT lub MX, aby sprawdzić poprawność własności domeny. Po dodaniu rekordu TXT lub MX do domeny wybierz pozycję **Weryfikuj**.

   :::image type="content" source="../../media/mtp-eval-17.png" alt-text="Strona Office 365 E5 konfiguracyjna, na której należy dodać rekord TXT rekordu MX w celu zweryfikowania domeny" lightbox="../../media/mtp-eval-17.png":::
 
10. [Opcjonalnie] Utwórz więcej kont użytkowników dla swojej dzierżawy. Możesz pominąć ten krok, klikając przycisk **Dalej**.

    :::image type="content" source="../../media/mtp-eval-18.png" alt-text="Strona Office 365 E5 konfiguracyjna, na której można dodać więcej użytkowników" lightbox="../../media/mtp-eval-18.png":::
 
11. [Opcjonalnie] Pobierz Office aplikacji. Kliknij **przycisk Dalej** , aby pominąć ten krok. 

    :::image type="content" source="../../media/mtp-eval-19.png" alt-text="Strona Office 365 E5, na której można zainstalować aplikacje pakietu Office firm" lightbox="../../media/mtp-eval-19.png":::

12. [Opcjonalnie] Migrowanie wiadomości e-mail. Ponownie możesz pominąć ten krok.

    :::image type="content" source="../../media/mtp-eval-20.png" alt-text="Informacje Office 365 E5, gdzie można określić, czy wiadomości e-mail mają być migrowane, czy nie" lightbox="../../media/mtp-eval-20.png":::
 
13. Wybierz Usługi online. Wybierz **Exchange** i kliknij przycisk **Dalej**. 

    :::image type="content" source="../../media/mtp-eval-21.png" alt-text="Miejsce Office 365 E5, w którym można wybrać Usługi online" lightbox="../../media/mtp-eval-21.png":::

14. Dodaj rekordy MX, CNAME i TXT do swojej domeny. Po zakończeniu wybierz pozycję **Weryfikuj**.

    :::image type="content" source="../../media/mtp-eval-22.png" alt-text="W Office 365 E5 można dodać rekordy DNS" lightbox="../../media/mtp-eval-22.png":::
 
15. Gratulacje! Zakończono inicjowanie obsługi Office 365 dzierżawy.

    :::image type="content" source="../../media/mtp-eval-23.png" alt-text="Strona Office 365 E5 potwierdzenia ukończenia konfiguracji" lightbox="../../media/mtp-eval-23.png":::
    

## <a name="enable-microsoft-365-trial-subscription"></a>Włączanie Microsoft 365 próbnej

>[!NOTE]
>Zarejestrowanie się w celu korzystania z wersji próbnej daje Ci 25 licencji użytkowników, których możesz używać przez miesiąc. Zobacz [Wypróbowanie lub zakup Microsoft 365,](../../commerce/try-or-buy-microsoft-365.md) aby uzyskać szczegółowe informacje.

1. W [Administracja Microsoft 365 usługi kliknij](https://admin.microsoft.com/) **pozycję Rozliczenia**, a następnie przejdź do **strony Zakup usług**.

2. Wybierz **Microsoft 365 E5** i kliknij pozycję **Rozpocznij bezpłatny okres próbny**. 

   :::image type="content" source="../../media/mtp-eval-24.png" alt-text="Strona Microsoft 365 E5 Rozpoczynanie bezpłatnej wersji próbnej" lightbox="../../media/mtp-eval-24.png":::

3. Wybierz preferencje weryfikacji: za pośrednictwem wiadomości SMS lub połączenia. Po wybraniu tej opcji wprowadź numer telefonu, wybierz pozycję Tekst do **mnie** **lub Zadzwoń** do mnie w zależności od wybranej opcji.

   :::image type="content" source="../../media/mtp-eval-25.png" alt-text="Strona Microsoft 365 E5 Rozpocznij bezpłatny okres próbny z prośbą o dane kontaktowe w celu wysłania kodu w celu udowodnienia, że nie jesteś robotem" lightbox="../../media/mtp-eval-25.png":::
 
4. Wprowadź kod weryfikacyjny i kliknij pozycję **Rozpocznij bezpłatny okres próbny**.

   :::image type="content" source="../../media/mtp-eval-26.png" alt-text="Strona Microsoft 365 E5 Rozpocznij bezpłatny okres próbny, na której możesz wypełnić kod weryfikacyjny wysłany przez system, aby potwierdzić, że nie jesteś robotem" lightbox="../../media/mtp-eval-26.png":::

5. Kliknij **pozycję Wypróbuj teraz**, aby potwierdzić Microsoft 365 E5 próbną.

   :::image type="content" source="../../media/mtp-eval-27.png" alt-text="The Microsoft 365 E5 Start free trial page where you should clock the Try now button to start" lightbox="../../media/mtp-eval-27.png":::
 
6. Przejdź do centrum **Administracja Microsoft 365** >  **UsersActivsActive** >  **użytkowników**. Wybierz swoje konto użytkownika, wybierz **pozycję Zarządzaj licencjami produktów**, a następnie zamień licencję z aplikacji Office 365 E5 do **Microsoft 365 E5**. Kliknij **Zapisz**.

   :::image type="content" source="../../media/mtp-eval-28.png" alt-text="Strona Administracja Microsoft 365 Centrum danych, na której można wybrać Microsoft 365 E5 licencji" lightbox="../../media/mtp-eval-28.png":::
 
7. Ponownie wybierz konto administratora globalnego, a następnie kliknij pozycję **Zarządzaj nazwą użytkownika**.

   :::image type="content" source="../../media/mtp-eval-29.png" alt-text="Strona Centrum Administracja Microsoft 365, gdzie można wybrać pozycję Konto i Zarządzanie nazwą użytkownika" lightbox="../../media/mtp-eval-29.png":::

8. [Opcjonalnie] Zmień domenę *z onmicrosoft.com* na własną domenę w zależności od tego, co wybrano w poprzednich krokach. Kliknij przycisk **Zapisz zmiany**.

   :::image type="content" source="../../media/mtp-eval-30.png" alt-text="Strona Administracja Microsoft 365 Center, na której można zmienić preferencje domeny" lightbox="../../media/mtp-eval-30.png":::

## <a name="next-step"></a>Następny krok
|[Etap 3. Konfigurowanie & wsadu](config-m365d-eval.md) | Skonfiguruj każdy Microsoft 365 Defender w celu Microsoft 365 Defender laboratorium próbnego lub środowiska pilotażowego i wsaduj punkty końcowe.
|:-------|:-----|
