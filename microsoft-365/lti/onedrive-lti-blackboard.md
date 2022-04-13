---
title: Integracja Microsoft OneDrive LTI z aplikacją Blackboard
ms.author: danismith
author: DaniEASmith
manager: serdars
ms.reviewer: amitman
audience: admin
ms.topic: article
ms.service: o365-administration
f1.keywords:
- CSH
ms.collection: M365-modern-desktop
ms.localizationpriority: medium
ROBOTS: NOINDEX, NOFOLLOW
description: Twórz i oceniaj przypisania, twórz i kuratoruj zawartość kursu oraz współpracuj nad plikami w czasie rzeczywistym przy użyciu nowej współdziałania narzędzi Microsoft OneDrive Edukacja Tools for Blackboard.
ms.openlocfilehash: 7e43ff51a069db55be06236fb0318aa4453d8feb
ms.sourcegitcommit: 195e4734d9a6e8e72bd355ee9f8bca1f18577615
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/13/2022
ms.locfileid: "64824657"
---
# <a name="integrate-microsoft-onedrive-lti-with-blackboard"></a>Integracja Microsoft OneDrive LTI z aplikacją Blackboard

Integracja Microsoft OneDrive LTI z aplikacją Blackboard jest procesem dwuetapowym. Pierwszy krok udostępnia Microsoft OneDrive LTI w ramach kursów Blackboard, a drugi krok włącza Microsoft OneDrive dla blackboardu.

> [!IMPORTANT]
> Osoba wykonująca tę integrację powinna być administratorem aplikacji Blackboard i administratorem dzierżawy Microsoft 365.

## <a name="recommended-browser-settings"></a>Zalecane ustawienia przeglądarki

- Pliki cookie powinny być dozwolone dla Microsoft OneDrive.
- Wyskakujące okienka nie powinny być blokowane dla Microsoft OneDrive.

> [!NOTE]
>
> - Pliki cookie nie są domyślnie dozwolone w trybie incognito przeglądarki Chrome i muszą być dozwolone.
> - Microsoft OneDrive LTI działa w trybie prywatnym w przeglądarce Microsoft Edge. Upewnij się, że nie zablokowano plików cookie (które są domyślnie dozwolone).

## <a name="register-the-onedrive-lti-13-tool-in-blackboard"></a>Rejestrowanie narzędzia OneDrive LTI 1.3 w aplikacji Blackboard

1. W panelu administratora blackboardu wybierz pozycję **Dostawcy narzędzi LTI**.
2. Wybierz pozycję **Zarejestruj narzędzie LTI 1.3**.
3. W polu Identyfikator klienta wpisz lub skopiuj i wklej ten identyfikator: ``78cd1b1c-ccbd-4318-9f90-22241f63b1f5``

   > [!NOTE]
   > Dodanie tego identyfikatora klienta spowoduje skonfigurowanie dwóch różnych umiejscowień w blackboardzie: jednego, który umożliwia dostęp do narzędzia z rynku zawartości, książek i narzędzi oraz edytora tekstu sformatowany, a drugi, który umożliwia dostęp do narzędzia z menu Dodaj zawartość w kursie online dla kursów Ultra.

4. Wybierz pozycję **Prześlij**.
5. Przejrzyj wszystkie wstępnie wypełnione ustawienia w widoku **Stan narzędzia** i upewnij się, że wybrany przycisk **Okrągły stan narzędzia** ma wartość **Zatwierdzone**.
6. W **obszarze Zasady instytucji** zaznacz pole wyboru **Rola w kursie** i **Pole wyboru Nazwa** w polach użytkownika do wysłania. Wszystkie inne pola użytkownika są opcjonalne, ale zaleca się pozostawienie ich na potrzeby przyszłego sprawdzania instalacji OneDrive.
7. **Zezwalaj na dostęp do usługi klasy** i **Zezwalaj na dostęp do usługi członkostwa** są w tej chwili opcjonalne, ale mogą być wymagane w przypadku przyszłych aktualizacji narzędzia LTI.
8. Skopiuj **identyfikator wdrożenia**. Będzie on potrzebny do skonfigurowania narzędzia Microsoft LTI Tool.
9. Wybierz przycisk **Prześlij** , aby zakończyć.

## <a name="configure-the-microsoft-lti-tool-to-work-with-blackboard"></a>Konfigurowanie narzędzia MICROSOFT LTI do pracy z aplikacją Blackboard

1. Zaloguj się do [portalu rejestracji Microsoft OneDrive LTI](https://onedrivelti.microsoft.com/admin).
2. Wybierz przycisk **Zgoda administratora** i zaakceptuj uprawnienia.

> [!CAUTION]
> Jeśli ten krok nie zostanie wykonany, poniższy krok spowoduje wyświetlenie błędu i nie będzie można wykonać tego kroku przez godzinę po wystąpieniu błędu.

3. Wybierz przycisk **Utwórz nową dzierżawę LTI** .
4. Na stronie Rejestracja LTI wybierz pozycję **Blackboard** z listy rozwijanej LTI Consumer Platform, a następnie wybierz przycisk **Dalej** .
5. Wklej **skopiowany identyfikator wdrożenia** podczas rejestrowania narzędzia w aplikacji Blackboard i wybierz pozycję **Dalej**.
6. Przejrzyj i zapisz zmiany. Po pomyślnej rejestracji zostanie wyświetlony komunikat.
7. Szczegóły rejestracji można również przejrzeć, wybierając przycisk **Wyświetl dzierżawy LTI** na stronie głównej.

Po wykonaniu tych kroków instruktorzy będą mogli otwierać dokumenty z OneDrive, gdy korzystają z menu "plus" na stronie Zawartość kursu.

## <a name="recommended-content"></a>Zalecana zawartość

[Integracje firmy Microsoft dla aplikacji Blackboard](https://help.blackboard.com/Learn/Administrator/SaaS/Integrations/Microsoft)

[integracja klas Microsoft Teams](https://help.blackboard.com/Learn/Administrator/SaaS/Integrations/Microsoft_Classes)
