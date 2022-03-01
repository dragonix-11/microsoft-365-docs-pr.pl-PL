---
title: Tworzenie ról dla kontroli dostępu opartej na rolach i zarządzanie nimi
description: Tworzenie ról i definiowanie uprawnień przypisanych do roli w ramach implementacji kontroli dostępu opartej na rolach w p Microsoft 365 Defender
keywords: role użytkowników, role, rbac dostępu
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.custom: admindeeplinkDEFENDER
ms.topic: article
ms.technology: mde
ms.openlocfilehash: a959edf1eaefcb25fd3fb8279e7e03d317c4f12e
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/24/2021
ms.locfileid: "62997367"
---
# <a name="create-and-manage-roles-for-role-based-access-control"></a>Tworzenie ról dla kontroli dostępu opartej na rolach i zarządzanie nimi

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**

- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-roles-abovefoldlink)

[!include[Prerelease information](../../includes/prerelease.md)]

## <a name="create-roles-and-assign-the-role-to-an-azure-active-directory-group"></a>Tworzenie ról i przypisywanie roli do grupy Azure Active Directory grupy

Poniższe instrukcje krok po kroku to, jak tworzyć role w Microsoft 365 Defender. Przyjęto w nim założenie, że już utworzono Azure Active Directory użytkowników.

1. Zaloguj się, <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a> przy użyciu konta z przypisaną rolą administratora zabezpieczeń lub administratora globalnego.

2. W okienku nawigacji **wybierz pozycję Ustawienia** \> **punktów końcowych** \> (w obszarze **Uprawnienia**).

3. Wybierz **pozycję Dodaj element**.

4. Wprowadź nazwę, opis i uprawnienia roli, które chcesz przypisać do roli.

5. Wybierz **pozycję Dalej** , aby przypisać rolę do grupy zabezpieczeń usługi Azure AD.

6. Użyj filtru, aby wybrać grupę usługi Azure AD, do których chcesz dodać tę rolę.

7. **Zapisz i zamknij**.

8. Zastosuj ustawienia konfiguracji.

> [!IMPORTANT]
> Po utworzeniu ról musisz utworzyć grupę urządzeń i zapewnić dostęp do grupy urządzeń przez przypisanie jej do właśnie utworzonej roli.

### <a name="permission-options"></a>Opcje uprawnień

- **Wyświetlanie danych**
  - **Operacje zabezpieczeń** — wyświetlanie wszystkich danych operacji zabezpieczeń w portalu
  - **Zagrożenia i zarządzanie lukami w zabezpieczeniach** — wyświetlanie Zarządzanie zagrożeniami i lukami danych w portalu

- **Aktywne działania naprawcze**
  - **Operacje zabezpieczeń** — działanie w odpowiedzi, zatwierdzanie lub odrzucanie oczekujących działań naprawczych, zarządzanie listami dozwolonymi/zablokowanymi w celu automatyzacji i wskaźników
  - **Zagrożenia i zarządzanie lukami w zabezpieczeniach — Obsługa wyjątków** — Tworzenie nowych wyjątków i zarządzanie aktywnymi wyjątkami
  - **Zagrożenia i zarządzanie lukami w zabezpieczeniach —** Obsługa działań naprawczych — przesyłanie nowych żądań rozwiązywania problemów, tworzenie biletów i zarządzanie istniejącymi działaniami naprawczymi

- **Badanie alertów** — zarządzanie alertami, inicjowanie zautomatyzowanych badań, uruchamianie skanów, zbieranie pakietów badania, zarządzanie tagami urządzeń i pobieranie tylko przenośnych plików wykonywalnych (PE)

- **Zarządzanie ustawieniami systemu portalu** — konfigurowanie ustawień pamięci, usług SIEM i zagrożeń w interfejsie API firmy Intel (ma zastosowanie globalnie), zaawansowane ustawienia, automatyczne przekazywanie plików, role i grupy urządzeń

    > [!NOTE]
    > To ustawienie jest dostępne tylko w roli administratora programu Microsoft Defender dla punktu końcowego (domyślnej).

- **Zarządzanie ustawieniami zabezpieczeń w usłudze Defender dla** chmury — konfigurowanie ustawień alertów i wykluczeń folderów w celu automatyzacji, urządzenia wynoszeń i wynoszeń oraz zarządzanie powiadomieniami e-mail, zarządzanie laboratorium oceny

- **Funkcje reagowania na żywo**
  - **Podstawowe** polecenia:
    - Rozpoczynanie sesji odpowiedzi na żywo
    - Wykonywanie poleceń odpowiedzi na żywo tylko do odczytu na urządzeniu zdalnym (z wyjątkiem kopiowania i wykonywania pliku)
    - Pobieranie pliku z urządzenia zdalnego za pośrednictwem funkcji odpowiedzi na żywo
  - **Polecenia** zaawansowane:
    - Pobieranie plików PE i innych niż PE ze strony pliku
    - Upload pliku na urządzenie zdalne
    - Wyświetlanie skryptu z biblioteki plików
    - Wykonywanie skryptu na urządzeniu zdalnym z biblioteki plików

Aby uzyskać więcej informacji na temat dostępnych poleceń, zobacz [Badanie urządzeń za pomocą funkcji odpowiedzi na żywo](live-response.md).

## <a name="edit-roles"></a>Edytuj role

1. Zaloguj się, <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a> przy użyciu konta z przypisaną rolą administratora zabezpieczeń lub administratora globalnego.

2. W okienku nawigacji **wybierz pozycję Ustawienia** \> **punktów końcowych** \> (w obszarze **Uprawnienia**).

3. Wybierz rolę, która chcesz edytować.

4. Kliknij pozycję **Edytuj**.

5. Zmodyfikuj szczegóły lub grupy przypisane do roli.

6. Kliknij **przycisk Zapisz i zamknij**.

## <a name="delete-roles"></a>Usuwanie ról

1. Zaloguj się, <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a> przy użyciu konta z przypisaną rolą administratora zabezpieczeń lub administratora globalnego.

2. W okienku nawigacji **wybierz pozycję Ustawienia** \> **punktów końcowych** \> (w obszarze **Uprawnienia**).

3. Wybierz rolę, która chcesz usunąć.

4. Kliknij przycisk listy rozwijanej i wybierz pozycję **Usuń rolę**.

## <a name="related-topic"></a>Temat pokrewny

- [Podstawowe uprawnienia użytkownika do uzyskiwania dostępu do portalu](basic-permissions.md)
- [Tworzenie grup urządzeń i zarządzanie nimi](machine-groups.md)
