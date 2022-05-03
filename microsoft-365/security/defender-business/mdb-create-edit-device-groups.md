---
title: Grupy urządzeń w Microsoft Defender dla Firm
description: Zasady zabezpieczeń są stosowane do urządzeń za pośrednictwem grup urządzeń w usłudze Defender dla Firm.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: how-to
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: abb1c694f98ace7595f1389e3270ca3479d0c745
ms.sourcegitcommit: f30616b90b382409f53a056b7a6c8be078e6866f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2022
ms.locfileid: "65172218"
---
# <a name="device-groups-in-microsoft-defender-for-business"></a>Grupy urządzeń w Microsoft Defender dla Firm

W Microsoft Defender dla Firm zasady są stosowane do urządzeń za pośrednictwem niektórych kolekcji nazywanych grupami urządzeń. 

**W tym artykule opisano**:  

- [Jakie są grupy urządzeń](#what-is-a-device-group)   
- [Jak tworzyć grupy urządzeń w usłudze Defender dla Firm](#create-a-new-device-group)
- [Jak wyświetlić istniejącą grupę urządzeń](#view-an-existing-device-group)
- [Co robi opcja Dodaj wszystkie urządzenia](#what-does-the-add-all-devices-option-do)

>
> **Masz minutę?**
> Weź udział w <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">krótkiej ankiecie dotyczącej bezpieczeństwa</a>. Chcielibyśmy usłyszeć od Ciebie!
>

## <a name="what-is-a-device-group"></a>Co to jest grupa urządzeń?

Grupa urządzeń to kolekcja urządzeń, które są pogrupowane ze względu na określone kryteria, takie jak wersja systemu operacyjnego. Urządzenia spełniające kryteria są uwzględniane w tej grupie urządzeń, chyba że zostaną wykluczone. W Microsoft Defender dla Firm zasady są stosowane do urządzeń przy użyciu grup urządzeń.

Usługa Defender dla firm obejmuje domyślne grupy urządzeń, których można użyć. Domyślne grupy urządzeń obejmują wszystkie urządzenia dołączone do usługi Defender dla Firm. Na przykład istnieje domyślna grupa urządzeń dla urządzeń Windows. Za każdym razem, gdy dołączasz Windows urządzenia, są one automatycznie dodawane do domyślnej grupy urządzeń.

Możesz również utworzyć nowe grupy urządzeń, aby przypisywać zasady z określonymi ustawieniami do niektórych urządzeń. Na przykład do jednego zestawu urządzeń Windows mogą być przypisane zasady zapory i inne zasady zapory przypisane do innego zestawu urządzeń Windows. Można zdefiniować określone grupy urządzeń do użycia z zasadami.

> [!NOTE]
> Podczas tworzenia zasad w usłudze Defender dla Firm jest przypisywana kolejność priorytetów. Jeśli zastosujesz wiele zasad do danego zestawu urządzeń, te urządzenia otrzymają tylko pierwsze zastosowane zasady. Aby uzyskać więcej informacji, zobacz [Omówienie kolejności zasad w Microsoft Defender dla Firm](mdb-policy-order.md).

Wszystkie grupy urządzeń, w tym domyślne grupy urządzeń i wszystkie zdefiniowane niestandardowe grupy urządzeń, są przechowywane w [Azure Active Directory](/azure/active-directory/fundamentals/active-directory-whatis) (Azure AD).

## <a name="create-a-new-device-group"></a>Tworzenie nowej grupy urządzeń

Obecnie w usłudze Defender dla firm można utworzyć nową grupę urządzeń podczas tworzenia lub edytowania zasad, zgodnie z opisem w poniższej procedurze: 

1. Przejdź do portalu Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) i zaloguj się.

2. W okienku nawigacji wybierz pozycję **Konfiguracja urządzenia**. 

3. Wykonaj jedną z następujących akcji:

    1. Wybierz istniejące zasady, a następnie wybierz pozycję **Edytuj**.
    2. Wybierz **pozycję + Dodaj** , aby utworzyć nowe zasady.

    > [!TIP]
    > Aby uzyskać pomoc dotyczącą tworzenia lub edytowania zasad, zobacz [Wyświetlanie lub edytowanie zasad w Microsoft Defender dla Firm](mdb-view-edit-policies.md).

4. W kroku **Informacje ogólne** przejrzyj informacje, w razie potrzeby edytuj, a następnie wybierz pozycję **Dalej**.

5. Wybierz **pozycję + Utwórz nową grupę**. 

6. Określ nazwę i opis grupy urządzeń, a następnie wybierz pozycję **Dalej**.

7. Wybierz urządzenia do uwzględnienia w grupie, a następnie wybierz pozycję **Utwórz grupę**.

8. W kroku **Grupy urządzeń** przejrzyj listę grup urządzeń dla zasad. W razie potrzeby usuń grupę z listy. Następnie wybierz pozycję **Dalej**.

9. Na stronie **Ustawienia konfiguracji** przejrzyj i edytuj ustawienia zgodnie z potrzebami, a następnie wybierz pozycję **Dalej**. Aby uzyskać więcej informacji na temat tych ustawień, zobacz [Ustawienia konfiguracji](mdb-next-gen-configuration-settings.md).

10. W kroku **Przeglądanie zasad przejrzyj** wszystkie ustawienia, wprowadź wymagane zmiany, a następnie wybierz pozycję **Utwórz zasady** lub **Zaktualizuj zasady**.

## <a name="view-an-existing-device-group"></a>Wyświetlanie istniejącej grupy urządzeń

Obecnie w usłudze Defender dla firm możesz wyświetlać istniejące grupy urządzeń podczas tworzenia lub edytowania zasad, zgodnie z opisem w poniższej procedurze: 

1. Przejdź do portalu Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) i zaloguj się.

2. W okienku nawigacji wybierz pozycję **Konfiguracja urządzenia**. 

3. Wykonaj jedną z następujących akcji:

    1. Wybierz istniejące zasady, a następnie wybierz pozycję **Edytuj**.
    2. Wybierz **pozycję + Dodaj** , aby utworzyć nowe zasady.

    > [!TIP]
    > Aby uzyskać pomoc dotyczącą tworzenia lub edytowania zasad, zobacz [Wyświetlanie lub edytowanie zasad w Microsoft Defender dla Firm](mdb-view-edit-policies.md).

4. W kroku **Informacje ogólne** przejrzyj informacje, w razie potrzeby edytuj, a następnie wybierz pozycję **Dalej**.

5. Wybierz pozycję **Użyj istniejącej grupy**. Zostanie otwarte okno wysuwane i zostaną wyświetlone grupy urządzeń. Jeśli nie masz jeszcze żadnych grup urządzeń, zostanie wyświetlony monit o utworzenie nowej grupy urządzeń.

## <a name="what-does-the-add-all-devices-option-do"></a>Do czego służy opcja Dodaj wszystkie urządzenia?

Podczas tworzenia lub edytowania zasad może zostać wyświetlona opcja **Dodaj wszystkie urządzenia** .

:::image type="content" source="media/add-all-devices-option.png" alt-text="Zrzut ekranu przedstawiający opcję Dodaj wszystkie urządzenia.":::

Jeśli wybierzesz tę opcję, wszystkie urządzenia zarejestrowane w Microsoft Intune otrzymają domyślnie tworzone lub edytowane zasady. 

## <a name="next-steps"></a>Następne kroki

Wybierz co najmniej jedno z następujących zadań:

- [Wyświetlanie lub edytowanie zasad](mdb-view-edit-policies.md)
- [Tworzenie nowych zasad](mdb-create-new-policy.md)
- [Wyświetlanie zdarzeń i zarządzanie nimi w Microsoft Defender dla Firm](mdb-view-manage-incidents.md)
- [Reagowanie na zagrożenia w Microsoft Defender dla Firm i eliminowanie ich](mdb-respond-mitigate-threats.md)
- [Przeglądanie akcji korygowania w centrum akcji](mdb-review-remediation-actions.md)