---
title: Praca z grupami urządzeń w aplikacji Microsoft 365 Business Premium
description: Informacje o grupach urządzeń w aplikacji Microsoft 365 Business Premium
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: how-to
ms.date: 03/08/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: 2cc874580dad24e1b3d5349d6075956a9e518704
ms.sourcegitcommit: adea59259a5900cad5de29ddf46d1ca9e9e1c82f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/04/2022
ms.locfileid: "64634652"
---
# <a name="device-groups-in-microsoft-365-business-premium"></a>Grupy urządzeń w aplikacji Microsoft 365 Business Premium

Microsoft 365 Business Premium obejmuje ochronę punktu końcowego za pośrednictwem Microsoft Defender dla Firm. Zasady ochrony urządzeń są stosowane do urządzeń za pośrednictwem określonych kolekcji nazywanych grupami urządzeń. 

**W tym artykule opisano**:  

- [Jakie grupy urządzeń to](#whats-a-device-group)
- [Jak utworzyć nową grupę urządzeń](#how-do-i-create-a-new-device-group)

## <a name="whats-a-device-group"></a>Co to jest grupa urządzeń?

Grupa urządzeń to zbiór urządzeń zgrupowanych ze względu na określone kryteria, takie jak wersja systemu operacyjnego. Urządzenia spełniające te kryteria są uwzględniane w tej grupie urządzeń, o ile nie zostaną wykluczone. 

W ramach subskrypcji masz domyślne grupy urządzeń, których możesz używać. Domyślne grupy urządzeń obejmują wszystkie urządzenia, które są włączone do usługi Defender dla firm. Możesz jednak również tworzyć nowe grupy urządzeń, aby przypisać zasady ochrony urządzeń z określonymi ustawieniami do określonych urządzeń. 

Wszystkie grupy urządzeń, w tym domyślne grupy urządzeń i wszystkie niestandardowe grupy urządzeń, które [zdefiniowasz, są przechowywane w usłudze Azure Active Directory](/azure/active-directory/fundamentals/active-directory-whatis) (Azure AD).

## <a name="how-do-i-create-a-new-device-group"></a>Jak mogę utworzyć nową grupę urządzeń?

Podczas tworzenia lub edytowania zasad ochrony urządzeń możesz utworzyć nową grupę urządzeń. 

1. Przejdź do Microsoft 365 Defender konta ([https://security.microsoft.com](https://security.microsoft.com)) i zaloguj się.

2. W okienku nawigacji wybierz pozycję **Konfiguracja urządzenia**. 

3. Aby to zrobić, zrób tak:

    1. Wybierz istniejące zasady, a następnie wybierz pozycję **Edytuj**.
    
    2. Wybierz **pozycję + Dodaj** , aby utworzyć nowe zasady.

    > [!TIP]
    > Aby uzyskać pomoc w tworzeniu lub edytowaniu zasad, zobacz [Wyświetlanie i edytowanie zasad w programie Microsoft Defender dla Firm](m365bp-view-edit-create-mdb-policies.md).

4. W kroku **Informacje ogólne** przejrzyj informacje, w razie potrzeby przeedytuj je, a następnie wybierz przycisk **Dalej**.

5. Wybierz **pozycję + Utwórz nową grupę**. 

6. Określ nazwę i opis grupy urządzeń, a następnie wybierz przycisk **Dalej**.

7. Wybierz urządzenia, które chcesz dołączyć do grupy, a następnie wybierz pozycję **Utwórz grupę**.

8. W kroku **Grupy** urządzeń przejrzyj listę grup urządzeń dla zasad. W razie potrzeby usuń grupę z listy. Następnie wybierz przycisk **Dalej**.

9. Na stronie **Ustawienia konfiguracji** przejrzyj i edytuj ustawienia zgodnie z potrzebami, a następnie wybierz pozycję **Dalej**. Aby uzyskać więcej informacji o tych ustawieniach, zobacz Opis ustawień konfiguracji następnej [generacji w programie Microsoft Defender dla Firm](../security/defender-business/mdb-next-gen-configuration-settings.md).

10. W kroku **Przejrzyj zasady** przejrzyj wszystkie ustawienia, wprowadzić wszelkie potrzebne zmiany, a następnie wybierz pozycję **Utwórz zasady** lub **Aktualizuj zasady**.


