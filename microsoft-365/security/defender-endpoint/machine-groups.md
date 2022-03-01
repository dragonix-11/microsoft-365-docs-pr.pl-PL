---
title: Tworzenie grup urządzeń i zarządzanie nimi w programie Microsoft Defender dla punktu końcowego
description: Tworzenie grup urządzeń i ustawianie na nich zautomatyzowanych poziomów rozwiązywania problemów przez potwierdzanie reguł obowiązujących w grupie
keywords: grupy urządzeń, grupy, działania naprawcze, poziom, reguły, grupa aad, rola, przypisywanie, pozycja
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
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 951e49ddb7cb9ed0154fa70f66d54944a8aae066
ms.sourcegitcommit: 986ea76ecaceb5fe6b9616e553003e3c5b0df2e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2022
ms.locfileid: "63010450"
---
# <a name="create-and-manage-device-groups"></a>Tworzenie grup urządzeń i zarządzanie nimi

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- Azure Active Directory
- Usługa Office 365
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

> Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

W scenariuszu dla przedsiębiorstwa do zespołów operacji zabezpieczeń jest zazwyczaj przypisany zestaw urządzeń. Te urządzenia są grupowane według zestawu atrybutów, takich jak domeny, nazwy komputerów lub wyznaczone tagi.

W programie Microsoft Defender for Endpoint możesz tworzyć grupy urządzeń i używać ich do:

- Ograniczanie dostępu do powiązanych alertów i danych do określonych grup użytkowników usługi Azure AD z [przypisanymi rolami RBAC](rbac.md)
- Konfigurowanie różnych ustawień automatycznego korygowania dla różnych zestawów urządzeń
- Przypisywanie określonych poziomów rozwiązywania problemów, które mają być stosowane podczas automatycznego badania
- W przypadku badania przefiltruj listę **Urządzenia** , aby wyświetlić konkretne grupy urządzeń, używając **filtru Grupuj** .

Grupy urządzeń można tworzyć w kontekście dostępu opartego na rolach (RBAC, role based access), aby kontrolować, kto może podjąć określone działanie lub wyświetlić informacje, przypisując grupy urządzeń do grupy użytkowników. Aby uzyskać więcej informacji, zobacz [Zarządzanie dostępem do portalu za pomocą kontroli dostępu opartej na rolach](rbac.md).

> [!TIP]
> Aby uzyskać pełny opis aplikacji RBAC, przeczytaj: Czy twój [soc działa płasko z RBAC](https://techcommunity.microsoft.com/t5/Windows-Defender-ATP/Is-your-SOC-running-flat-with-limited-RBAC/ba-p/320015).

W ramach procesu tworzenia grupy urządzeń:

- Ustawianie automatycznego poziomu rozwiązywania problemów dla tej grupy. Aby uzyskać więcej informacji na temat poziomów rozwiązywania problemów, zobacz [Używanie automatycznego badania w celu zbadania i rozwiązania problemów związanych z zagrożeniami](automated-investigations.md).
- Określ regułę dopasowywania, która określa, która grupa urządzeń należy do grupy, na podstawie nazwy urządzenia, domeny, tagów i platformy systemu operacyjnego. Jeśli urządzenie jest także dopasowane do innych grup, jest dodawane tylko do grupy urządzeń, która jest najwyżej w rankingu.
- Wybierz grupę użytkowników usługi Azure AD, którzy powinni mieć dostęp do grupy urządzeń.
- Po utworzeniu grupy urządzeń należy ją do innych grup.

> [!NOTE]
> Grupa urządzeń jest dostępna dla wszystkich użytkowników, jeśli nie przypiszesz do tej grupy usługi Azure AD żadnych grup.

## <a name="create-a-device-group"></a>Tworzenie grupy urządzeń

1. W okienku nawigacji **wybierz pozycję Ustawienia** \> **grupy Urządzenia z** \> **uprawnieniami** \> **punktów końcowych**.

2. Kliknij **pozycję Dodaj grupę urządzeń**.

3. Wprowadź nazwę grupy oraz ustawienia automatyzacji i określ regułę dopasowywania określającą, które urządzenia należą do grupy. Zobacz [Jak rozpoczyna się automatyczne badanie](automated-investigations.md#how-the-automated-investigation-starts).

    > [!TIP]
    > Jeśli chcesz używać tagów do grupowania urządzeń, zobacz [Tworzenie tagów urządzeń i zarządzanie nimi](machine-tags.md).

4. Wyświetl podgląd kilku urządzeń, które będą zgodne z tą regułą. Jeśli ta reguła ci się podoba, kliknij **kartę Dostęp** użytkownika.

5. Przypisz grupy użytkowników, które mają dostęp do utworzonej grupy urządzeń.

    > [!NOTE]
    > Możesz udzielić dostępu tylko tym grupom użytkowników usługi Azure AD, które zostały przypisane do ról RBAC.

6. Kliknij przycisk **Zamknij**. Zmiany konfiguracji zostaną zastosowane.

## <a name="manage-device-groups"></a>Zarządzanie grupami urządzeń

Można podwyższyć lub obniżyć pozycję grupy urządzeń, aby podczas dopasowywania była ona o wyższym lub niższym priorytecie. Gdy urządzenie zostanie dopasowane do więcej niż jednej grupy, jest ono dodawane tylko do grupy sklasyfikowanych jako pierwsze. Możesz również edytować i usuwać grupy.

> [!WARNING]
> Usunięcie grupy urządzeń może mieć wpływ na reguły powiadomień e-mail. Jeśli grupa urządzeń została skonfigurowana w ramach reguły powiadomień e-mail, zostanie ona usunięta z tej reguły. Jeśli grupa urządzeń jest jedyną grupą skonfigurowaną do powiadamiania e-mail, ta reguła powiadomień e-mail zostanie usunięta wraz z grupą urządzeń.

Domyślnie grupy urządzeń są dostępne dla wszystkich użytkowników z dostępem do portalu. Możesz zmienić domyślne zachowanie, przypisując grupy użytkowników usługi Azure AD do grupy urządzeń.

Urządzenia, które nie są zgodne z żadnymi grupami, są dodawane do grupy Urządzenia rozgrupowane (domyślne). Nie można zmienić pozycji tej grupy ani jej usunąć. Można jednak zmienić poziom rozwiązywania problemów dla tej grupy i zdefiniować grupy użytkowników usługi Azure AD, które mogą mieć dostęp do tej grupy.

> [!NOTE]
> Zastosowanie zmian w konfiguracji grupy urządzeń może potrwać kilka minut.

### <a name="add-device-group-definitions"></a>Dodawanie definicji grup urządzeń

Definicje grup urządzeń mogą także zawierać wiele wartości dla każdego warunku. Możesz ustawić wiele tagów, nazw urządzeń i domen na definicję jednej grupy urządzeń.

1. Utwórz nową grupę urządzeń, a następnie wybierz **kartę** Urządzenia.
2. Dodaj pierwszą wartość dla jednego z warunków.
3. Zaznacz `+` , aby dodać więcej wierszy tego samego typu właściwości.

> [!TIP]
> Użyj operatora "LUB" między wierszami o tym samym typie warunku, co pozwala na stosowanie wielu wartości na właściwość.
> Możesz dodać maksymalnie 10 wierszy (wartości) dla każdego typu właściwości — tag, nazwa urządzenia, domena.

Aby uzyskać więcej informacji na temat łączenia się z definicjami grup urządzeń, zobacz [Grupy urządzeń — Microsoft 365 zabezpieczeń](https://sip.security.microsoft.com/homepage).

## <a name="related-topics"></a>Tematy pokrewne

- [Zarządzanie dostępem do portalu przy użyciu kontroli dostępu opartej na rolach](rbac.md)
- [Tworzenie tagów urządzeń i zarządzanie nimi](machine-tags.md)
- [Uzyskiwanie listy grup urządzeń dzierżawcy przy użyciu interfejsu API Graph API](/graph/api/device-list-memberof)
