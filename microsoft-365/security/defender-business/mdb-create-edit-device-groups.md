---
title: Grupy urządzeń w programie Microsoft Defender dla firm
description: Informacje o grupach urządzeń w programie Microsoft Defender dla firm
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: how-to
ms.date: 02/07/2022
ms.prod: m365-security
ms.technology: mdb
localization_priority: Normal
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: 469bf6e2c5a25ef96175caf951972de26420620c
ms.sourcegitcommit: 2697938d2d4fec523b501c5e7b0b8ec8f34e59b0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2022
ms.locfileid: "63449146"
---
# <a name="device-groups-in-microsoft-defender-for-business"></a>Grupy urządzeń w programie Microsoft Defender dla firm

> [!IMPORTANT]
> Program Microsoft Defender dla firm jest wprowadzany [dla Microsoft 365 Business Premium](../../business-premium/index.md) klientów od 1 marca 2022 r. Autonomiczna subskrypcja usługi Defender dla firm jest w wersji Preview i będzie stopniowo wprowadzana u klientów i partnerów IT, [](https://aka.ms/mdb-preview) którzy zarejestrują się tutaj, aby poprosić o to. Wersja Preview zawiera [początkowy zestaw scenariuszy](mdb-tutorials.md#try-these-preview-scenarios), a my będziemy regularnie dodawać funkcje.
> 
> Niektóre informacje w tym artykule dotyczą wstępnie dzierżawionych produktów/usług, które mogą zostać znacząco zmodyfikowane przed ich komercyjną premierą. Firma Microsoft nie udziela żadnych gwarancji, jawnych ani domniemanych, dotyczących podanych tutaj informacji. 

W programie Microsoft Defender for Business zasady są stosowane do urządzeń za pośrednictwem niektórych kolekcji nazywanych grupami urządzeń. 

**W tym artykule opisano**:  

- [Jakie grupy urządzeń to](#what-is-a-device-group)   
- [Jak tworzyć grupy urządzeń w programie Defender dla firm](#create-a-new-device-group)

>
> **Masz minutę?**
> Prosimy o <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">krótką ankietę na temat programu Microsoft Defender dla firm</a>. Chcemy ją usłyszeć!
>

## <a name="what-is-a-device-group"></a>Co to jest grupa urządzeń?

Grupa urządzeń to zbiór urządzeń zgrupowanych ze względu na określone kryteria, takie jak wersja systemu operacyjnego. Urządzenia spełniające te kryteria są uwzględniane w tej grupie urządzeń, o ile nie zostaną wykluczone. W programie Microsoft Defender dla firm zasady są stosowane do urządzeń za pomocą grup urządzeń. 

Program Defender dla firm zawiera domyślne grupy urządzeń, z których możesz korzystać. Domyślne grupy urządzeń obejmują wszystkie urządzenia, które są włączone do usługi Defender dla firm. Możesz jednak również tworzyć nowe grupy urządzeń, aby przypisać zasady z określonymi ustawieniami do określonych urządzeń. 

Wszystkie grupy urządzeń, w tym domyślne grupy urządzeń i wszystkie niestandardowe grupy urządzeń, które [zdefiniowasz, są przechowywane w usłudze Azure Active Directory](/azure/active-directory/fundamentals/active-directory-whatis) (Azure AD).

## <a name="create-a-new-device-group"></a>Tworzenie nowej grupy urządzeń

Obecnie w u programie Defender dla firm można podczas tworzenia lub edytowania zasad utworzyć nową grupę urządzeń, zgodnie z opisem w poniższej procedurze: 

1. Przejdź do Microsoft 365 Defender konta ([https://security.microsoft.com](https://security.microsoft.com)) i zaloguj się.

2. W okienku nawigacji wybierz pozycję **Konfiguracja urządzenia**. 

3. Aby to zrobić, zrób tak:

    1. Wybierz istniejące zasady, a następnie wybierz pozycję **Edytuj**.
    2. Wybierz **pozycję + Dodaj** , aby utworzyć nowe zasady.

    > [!TIP]
    > Aby uzyskać pomoc w tworzeniu lub edytowaniu zasad, zobacz [Wyświetlanie i edytowanie zasad w u programie Microsoft Defender dla firm](mdb-view-edit-policies.md).

4. W kroku **Informacje ogólne** przejrzyj informacje, w razie potrzeby przeedytuj je, a następnie wybierz przycisk **Dalej**.

5. Wybierz **pozycję + Utwórz nową grupę**. 

6. Określ nazwę i opis grupy urządzeń, a następnie wybierz przycisk **Dalej**.

7. Wybierz urządzenia, które chcesz dołączyć do grupy, a następnie wybierz pozycję **Utwórz grupę**.

8. W kroku **Grupy** urządzeń przejrzyj listę grup urządzeń dla zasad. W razie potrzeby usuń grupę z listy. Następnie wybierz przycisk **Dalej**.

9. Na stronie **Ustawienia konfiguracji** przejrzyj i edytuj ustawienia zgodnie z potrzebami, a następnie wybierz pozycję **Dalej**. Aby uzyskać więcej informacji o tych ustawieniach, zobacz [Ustawienia konfiguracji](mdb-next-gen-configuration-settings.md).

10. W kroku **Przejrzyj zasady** przejrzyj wszystkie ustawienia, wprowadzić wszelkie potrzebne zmiany, a następnie wybierz pozycję **Utwórz zasady** lub **Aktualizuj zasady**.

## <a name="next-steps"></a>Następne kroki

Wybierz co najmniej jedno z następujących zadań:

- [Wyświetlanie i edytowanie zasad](mdb-view-edit-policies.md)

- [Tworzenie nowych zasad](mdb-create-new-policy.md)

- [Wyświetlanie zdarzeń i zarządzanie nimi w programie Microsoft Defender dla firm](mdb-view-manage-incidents.md)

- [Reagowanie na zagrożenia i ograniczanie ich w programie Microsoft Defender dla firm](mdb-respond-mitigate-threats.md)

- [Przeglądanie działań naprawczych w Centrum akcji](mdb-review-remediation-actions.md)