---
title: Integracja Microsoft OneDrive LTI z blackboardem
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
description: Tworzenie i ocena zadań, tworzenie i nauczanie zawartości kursu oraz współpraca nad plikami w czasie rzeczywistym przy użyciu nowego współdziałania narzędzi programu Microsoft OneDrive Edukacja dla aplikacji Blackboard.
ms.openlocfilehash: 94e77181244bbf02115bd706e86751a9382b906b
ms.sourcegitcommit: a9266e4e7470e8c1e8afd31fef8d266f7849d781
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2022
ms.locfileid: "63705300"
---
# <a name="integrate-microsoft-onedrive-lti-with-blackboard"></a>Integracja Microsoft OneDrive LTI z blackboardem

Integracja Microsoft OneDrive LTI z blackboard to proces dwuetapowy. Pierwszy krok sprawia, że Microsoft OneDrive LTI jest dostępny w ramach kursów blackboard, a drugi krok włącza Microsoft OneDrive dla czarnego tablicy.

> [!IMPORTANT]
> Osoba, która wykonuje tę integrację, powinna być administratorem blackboard i administratorem Microsoft 365 dzierżawy.

## <a name="recommended-browser-settings"></a>Zalecane ustawienia przeglądarki

- Pliki cookie powinny być dozwolone dla Microsoft OneDrive.
- Wyskakujące okienka nie powinny być blokowane przez Microsoft OneDrive.

> [!NOTE]
>
> - Pliki cookie nie są domyślnie dozwolone w trybie incognito przeglądarki Chrome i muszą być dozwolone.
> - Microsoft OneDrive lti działa w trybie prywatnym w Microsoft Edge przeglądarce. Upewnij się, że pliki cookie nie zostały zablokowane (które są domyślnie dozwolone).

## <a name="register-the-onedrive-lti-13-tool-in-blackboard"></a>Zarejestruj narzędzie OneDrive LTI 1.3 w blackboard

1. W panelu administratora aplikacji Blackboard wybierz pozycję  **Dostawcy narzędziLTI**.
2.  **Wybierzregister LTI 1.3 Tool**.
3. W polu Identyfikator klienta wpisz lub skopiuj i wklej ten identyfikator: ``78cd1b1c-ccbd-4318-9f90-22241f63b1f5``

  > [!NOTE]
  > Dodanie tego identyfikatora klienta spowoduje skonfigurowanie dwóch różnych miejsc na tablicy: jednego, które umożliwia dostęp do narzędzia z rynku zawartości, książek i narzędzi, edytora tekstów sformatowanych, oraz innego, które umożliwia dostęp do narzędzia z menu Dodaj zawartość w kursie online dotyczącym kursów Ultra.

4. Wybierz **pozycję Prześlij**.
5. Przejrzyj wszystkie wstępnie wypełnione ustawienia w widoku  **Stan**  narzędzia i upewnij się, że zaznaczono przycisk  Stan narzędzia  **zaokrąglony ma stanApprzędne**.
6.  **InInin przeszły**, **select the Role in course** and **the Name checkboxes** in the user fields to send. Wszystkie pozostałe pola użytkowników są opcjonalne, ale zaleca się pozostawienie ich w przyszłości w celu weryfikacji OneDrive instalacji.
7. **Zezwalaj na dostęp do usługi oceny**   **orazZgodnianie dostępu do** usługi członkostwa jest obecnie również opcjonalne, ale może być wymagane w przyszłości w celu aktualizacji narzędzia LTI.
8. Skopiuj **identyfikator wdrożenia**. Będzie ona potrzebna do skonfigurowania narzędzia Microsoft LTI Tool.
9. Wybierz przycisk **Prześlij** , aby zakończyć.

## <a name="configure-the-microsoft-lti-tool-to-work-with-blackboard"></a>Konfigurowanie narzędzia Microsoft LTI Tool do pracy z tablicą Blackboard

1. Zaloguj się do [Microsoft OneDrive LTI Registration Portal](https://onedrivelti.microsoft.com/admin).
2. Wybierz przycisk **Zgoda administratora** i zaakceptuj te uprawnienia.

> [!CAUTION]
> Jeśli ten krok nie zostanie wykonany, poniższy krok spowoduje błąd i nie będzie można go wykonać przez godzinę, gdy błąd wystąpi.

3. Wybierz przycisk **Create new LTI Tenant (Utwórz nową dzierżawę LTI** ).
4. Na stronie LTI Registration (Rejestracja LTI) wybierz pozycję **Blackboard** z listy rozwijanej LTI Consumer Platform (Platforma konsumencka LTI), a następnie wybierz **przycisk Next (** Dalej).
5. Wklej identyfikator **wdrożenia skopiowany** podczas rejestrowania narzędzia w aplikacji Blackboard i wybierz pozycję **Dalej**.
6. Przejrzyj i zapisz zmiany. Po pomyślnej rejestracji zostanie wyświetlony komunikat.
7. Szczegóły rejestracji można również przejrzeć, wybierając przycisk Wyświetl dzierżawy **LTI** na stronie głównej.

Po zakończeniu tych czynności instruktorzy będą mogli otwierać dokumenty z programu OneDrive, gdy użyją menu "plus" na stronie Zawartość kursu.

## <a name="recommended-content"></a>Zalecana zawartość

[Integracje firmy Microsoft dla tablicy Blackboard](https://help.blackboard.com/Learn/Administrator/SaaS/Integrations/Microsoft)

[Integracja Microsoft Teams zajęć](https://help.blackboard.com/Learn/Administrator/SaaS/Integrations/Microsoft_Classes)
