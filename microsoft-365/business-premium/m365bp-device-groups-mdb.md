---
title: Praca z grupami urządzeń w Microsoft 365 Business Premium
description: Dowiedz się więcej o grupach urządzeń w Microsoft 365 Business Premium
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: how-to
ms.date: 03/16/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: high
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: 2c218cd2b0f04201f46155a72a916cc7676aaddb
ms.sourcegitcommit: 7dc7e9fd76adf848f941919f86ca25eecc704015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/11/2022
ms.locfileid: "65320823"
---
# <a name="device-groups-in-microsoft-365-business-premium"></a>Grupy urządzeń w Microsoft 365 Business Premium

Microsoft 365 Business Premium obejmuje ochronę punktów końcowych za pośrednictwem Microsoft Defender dla Firm. Zasady ochrony urządzeń są stosowane do urządzeń za pośrednictwem niektórych kolekcji nazywanych grupami urządzeń. 

**W tych wskazówkach opisano**:  

- [Jakie są grupy urządzeń](#whats-a-device-group)
- [Jak utworzyć nową grupę urządzeń](#how-do-i-create-a-new-device-group)

## <a name="whats-a-device-group"></a>Co to jest grupa urządzeń?

Grupa urządzeń to kolekcja urządzeń, które są pogrupowane ze względu na określone kryteria, takie jak wersja systemu operacyjnego. Urządzenia spełniające kryteria są uwzględniane w tej grupie urządzeń, chyba że zostaną wykluczone. 

W ramach subskrypcji masz domyślne grupy urządzeń, których możesz użyć. Domyślne grupy urządzeń obejmują wszystkie urządzenia dołączone do usługi Defender dla Firm. Można jednak również utworzyć nowe grupy urządzeń w celu przypisania zasad ochrony urządzeń z określonymi ustawieniami do niektórych urządzeń. 

Wszystkie grupy urządzeń, w tym domyślne grupy urządzeń i wszystkie zdefiniowane niestandardowe grupy urządzeń, są przechowywane w [Azure Active Directory](/azure/active-directory/fundamentals/active-directory-whatis) (Azure AD).

## <a name="how-do-i-create-a-new-device-group"></a>Jak mogę utworzyć nową grupę urządzeń?

Podczas tworzenia lub edytowania zasad ochrony urządzeń można utworzyć nową grupę urządzeń. 

1. Przejdź do portalu Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) i zaloguj się.

2. W okienku nawigacji wybierz pozycję **Konfiguracja urządzenia**. 

3. Wykonaj jedną z następujących akcji:

    1. Wybierz istniejące zasady, a następnie wybierz pozycję **Edytuj**.
    
    2. Wybierz **pozycję + Dodaj** , aby utworzyć nowe zasady.

    > [!TIP]
    > Aby uzyskać pomoc dotyczącą tworzenia lub edytowania zasad, zobacz [Wyświetlanie lub edytowanie zasad w Microsoft Defender dla Firm](m365bp-view-edit-create-mdb-policies.md).

4. W kroku **Informacje ogólne** przejrzyj informacje, w razie potrzeby edytuj, a następnie wybierz pozycję **Dalej**.

5. Wybierz **pozycję + Utwórz nową grupę**. 

6. Określ nazwę i opis grupy urządzeń, a następnie wybierz pozycję **Dalej**.

7. Wybierz urządzenia do uwzględnienia w grupie, a następnie wybierz pozycję **Utwórz grupę**.

8. W kroku **Grupy urządzeń** przejrzyj listę grup urządzeń dla zasad. W razie potrzeby usuń grupę z listy. Następnie wybierz pozycję **Dalej**.

9. Na stronie **Ustawienia konfiguracji** przejrzyj i edytuj ustawienia zgodnie z potrzebami, a następnie wybierz pozycję **Dalej**. Aby uzyskać więcej informacji na temat tych ustawień, zobacz [Omówienie ustawień konfiguracji nowej generacji w Microsoft Defender dla Firm](../security/defender-business/mdb-next-gen-configuration-settings.md).

10. W kroku **Przeglądanie zasad przejrzyj** wszystkie ustawienia, wprowadź wymagane zmiany, a następnie wybierz pozycję **Utwórz zasady** lub **Zaktualizuj zasady**.

## <a name="next-steps"></a>Następne kroki

Po ukończeniu podstawowych misji skonfiguruj [zespoły reagowania](m365bp-security-incident-management.md) i [zachowaj środowisko](m365bp-maintain-environment.md).

