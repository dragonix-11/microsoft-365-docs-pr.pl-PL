---
title: Wyświetlanie lub edytowanie zasad ochrony urządzeń
description: Wyświetlanie, edytowanie, tworzenie i usuwanie zasad ochrony urządzeń w Microsoft 365 Business Premium
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 05/20/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: high
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: 5a01c2f045ea797aa61f3028f2a0a4ef4e260fe6
ms.sourcegitcommit: 349f0f54b0397cdd7d8fbb9ef07f1b6654a32d6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2022
ms.locfileid: "65623190"
---
# <a name="view-and-edit-device-protection-policies"></a>Wyświetlanie i edytowanie zasad ochrony urządzeń

W Microsoft 365 Business Premium ustawienia zabezpieczeń dla urządzeń zarządzanych są konfigurowane za pomocą zasad ochrony urządzeń w centrum zabezpieczeń usługi Microsoft Defender lub w centrum administracyjnym. Aby uprościć konfigurację i konfigurację, istnieją wstępnie skonfigurowane zasady, które ułatwiają ochronę urządzeń organizacji natychmiast po ich dołączeniu. Możesz użyć zasad domyślnych, edytować istniejące zasady lub tworzyć własne zasady.

**W tych wskazówkach opisano, jak** wykonać następujące czynności:

- Zapoznaj się z omówieniem domyślnych zasad
- Praca z zasadami urządzeń w centrum zabezpieczeń usługi Defender, centrum administracyjnym i Intune.

## <a name="about-the-default-device-protection-policies"></a>Informacje o domyślnych zasadach ochrony urządzeń

Microsoft 365 Business Premium obejmuje dwa główne typy zasad ochrony urządzeń organizacji:

- **Zasady ochrony nowej generacji**, które określają sposób konfigurowania Program antywirusowy Microsoft Defender i innych funkcji ochrony przed zagrożeniami.

- **Zasady zapory**, które określają, jaki ruch sieciowy może przepływać do i z urządzeń organizacji.

Te zasady są częścią Microsoft Defender dla Firm uwzględnionych w subskrypcji Microsoft 365 Business Premium. Informacje są udostępniane do pracy z zasadami w centrum zabezpieczeń usługi Microsoft Defender, a także sposobu pracy z zasadami w centrum administracyjnym i Intune.

## <a name="working-with-device-polices-in-the-microsoft-defender-security-center"></a>Praca z zasadami urządzeń w centrum zabezpieczeń usługi Microsoft Defender

Poniższe szczegóły dotyczą pracy z zasadami w centrum zabezpieczeń.

### <a name="view-existing-device-protection-policies"></a>Wyświetlanie istniejących zasad ochrony urządzeń

Aby wyświetlić istniejące zasady ochrony urządzeń w centrum zabezpieczeń:

1. Przejdź do portalu Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) i zaloguj się.

1. W okienku nawigacji wybierz pozycję **Konfiguracja urządzenia**. Zasady są zorganizowane według systemu operacyjnego (na przykład **klienta Windows**) i typu zasad (na przykład **ochrony następnej generacji** i **zapory**).

    :::image type="content" source="../media/mdb-deviceconfiguration.png" lightbox="../media/mdb-deviceconfiguration.png" alt-text="Strona Konfiguracja urządzenia.":::

1. Wybierz kartę systemu operacyjnego (na przykład **Windows klientów**), a następnie przejrzyj listę zasad w kategoriach **Ochrona następnej generacji** i **Zapora**.

1. Aby wyświetlić więcej szczegółów dotyczących zasad, wybierz jej nazwę. Zostanie otwarte okienko boczne, które zawiera więcej informacji o tych zasadach, takich jak urządzenia chronione przez te zasady.

   :::image type="content" source="../media/mdb-deviceconfig-selectedpolicy.png" lightbox="../media/mdb-deviceconfig-selectedpolicy.png" alt-text="Zrzut ekranu przedstawiający zasady wybrane na stronie Konfiguracja urządzenia.":::

### <a name="edit-an-existing-device-protection-policy"></a>Edytowanie istniejących zasad ochrony urządzeń

Aby edytować zasady urządzenia:

1. Przejdź do portalu Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) i zaloguj się.

1. W okienku nawigacji wybierz pozycję **Konfiguracja urządzenia**. Zasady są zorganizowane według systemu operacyjnego (na przykład **klienta Windows**) i typu zasad (na przykład **ochrony następnej generacji** i **zapory**).

1. Wybierz kartę systemu operacyjnego (na przykład **Windows klientów**), a następnie przejrzyj listę zasad w kategoriach **Ochrona następnej generacji** i **Zapora**.

1. Aby edytować zasady, wybierz jej nazwę, a następnie wybierz pozycję **Edytuj**.

1. Na karcie **Informacje ogólne** przejrzyj informacje. W razie potrzeby możesz edytować opis. Następnie wybierz pozycję **Dalej**.

1. Na karcie **Grupy urządzeń** określ, które grupy urządzeń powinny otrzymywać te zasady.  

   - Aby zachować wybraną grupę urządzeń w następującym stanie, wybierz pozycję **Dalej**.
   - Aby usunąć grupę urządzeń z zasad, wybierz pozycję **Usuń**.
   - Aby skonfigurować nową grupę urządzeń, wybierz pozycję **Utwórz nową grupę**, a następnie skonfiguruj grupę urządzeń. (Aby uzyskać pomoc dotyczącą tego zadania, zobacz [Grupy urządzeń w Microsoft 365 Business Premium](m365bp-device-groups-mdb.md)).
   - Aby zastosować zasady do innej grupy urządzeń, wybierz pozycję **Użyj istniejącej grupy**.

   Po określeniu, które grupy urządzeń powinny otrzymywać zasady, wybierz pozycję **Dalej**.

1. Na karcie **Ustawienia konfiguracji** przejrzyj ustawienia. W razie potrzeby można edytować ustawienia zasad. Aby uzyskać pomoc dotyczącą tego zadania, zobacz następujące artykuły: 

   - [Omówienie ustawień konfiguracji następnej generacji](../security/defender-business/mdb-next-gen-configuration-settings.md)   
   - [Ustawienia zapory](../security/defender-business/mdb-firewall.md)

   Po określeniu ustawień ochrony nowej generacji wybierz pozycję **Dalej**.

1. Na karcie **Przeglądanie zasad** zapoznaj się z ogólnymi informacjami, urządzeniami docelowymi i ustawieniami konfiguracji.

   - Wprowadź wszelkie wymagane zmiany, wybierając pozycję **Edytuj**.
   - Gdy wszystko będzie gotowe do kontynuowania, wybierz pozycję **Aktualizuj zasady**.

### <a name="create-a-new-device-protection-policy"></a>Tworzenie nowych zasad ochrony urządzeń

Aby utworzyć nowe zasady ochrony urządzeń:

1. Przejdź do portalu Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) i zaloguj się.

1. W okienku nawigacji wybierz pozycję **Konfiguracja urządzenia**. Zasady są zorganizowane według systemu operacyjnego (na przykład **klienta Windows**) i typu zasad (na przykład **ochrony następnej generacji** i **zapory**).

1. Wybierz kartę systemu operacyjnego (na przykład **Windows klientów**), a następnie przejrzyj listę zasad **ochrony następnej generacji**.

1. W obszarze **Ochrona następnej generacji** lub **Zapora** wybierz pozycję **+ Dodaj**.

1. Na karcie **Informacje ogólne** wykonaj następujące kroki:

   1. Określ nazwę i opis. Te informacje pomogą Tobie i Twojej drużynie zidentyfikować zasady później.
   2. Przejrzyj kolejność zasad i w razie potrzeby edytuj ją. (Aby uzyskać więcej informacji, zobacz [Kolejność zasad](../security/defender-business/mdb-policy-order.md)).
   3. Wybierz przycisk **Dalej**.

1. Na karcie **Grupy urządzeń** utwórz nową grupę urządzeń lub użyj istniejącej grupy. Zasady są przypisywane do urządzeń za pośrednictwem grup urządzeń. Oto kilka kwestii, o których należy pamiętać:

   - Początkowo możesz mieć tylko domyślną grupę urządzeń, która obejmuje urządzenia używane przez osoby w organizacji do uzyskiwania dostępu do danych organizacji i poczty e-mail. Możesz zachować domyślną grupę urządzeń i korzystać z niej.
   - Utwórz nową grupę urządzeń, aby zastosować zasady z określonymi ustawieniami, które różnią się od zasad domyślnych.
   - Podczas konfigurowania grupy urządzeń należy określić pewne kryteria, takie jak wersja systemu operacyjnego. Urządzenia spełniające kryteria są uwzględniane w tej grupie urządzeń, chyba że zostaną wykluczone.
   - Wszystkie grupy urządzeń, w tym zdefiniowane domyślne i niestandardowe grupy urządzeń, są przechowywane w Azure Active Directory (Azure AD).

   Aby dowiedzieć się więcej o grupach urządzeń, zobacz [Temat Grupy urządzeń w Microsoft Defender dla Firm](../security/defender-business/mdb-create-edit-device-groups.md).

1. Na **karcie Ustawienia konfiguracji** określ ustawienia zasad, a następnie wybierz pozycję **Dalej**. Aby uzyskać więcej informacji na temat poszczególnych ustawień, zobacz [Omówienie ustawień konfiguracji nowej generacji w Microsoft Defender dla Firm](../security/defender-business/mdb-next-gen-configuration-settings.md).

1. Na karcie **Przeglądanie zasad** zapoznaj się z ogólnymi informacjami, urządzeniami docelowymi i ustawieniami konfiguracji.

   - Wprowadź wszelkie wymagane zmiany, wybierając pozycję **Edytuj**.
   - Gdy wszystko będzie gotowe do kontynuowania, wybierz pozycję **Utwórz zasady**.

## <a name="using-device-policies-in-the-admin-center"></a>Korzystanie z zasad urządzeń w Centrum administracyjnym

Poniższe informacje opisują wyświetlanie zasad i zarządzanie nimi w centrum administracyjnym usługi Microsoft Business Premium.

### <a name="working-with-device-policies"></a>Praca z zasadami urządzeń

Aby pracować z zasadami w Centrum administracyjnym:

1.  Przejdź do centrum administracyjnego w witrynie <a href="https://go.microsoft.com/fwlink/p/?linkid=837890" target="_blank">https://admin.microsoft.com</a>.

1. Na lewym pasku nawigacyjnym wybierz pozycję **Zasady urządzeń**\>.

    Na tej stronie można tworzyć, edytować, zmieniać grupę docelową lub usuwać zasady.

    ![Zrzut ekranu przedstawiający stronę Zasady.](../media/devicepolicies.png)
  
### <a name="view-and-manage-devices"></a>Wyświetlanie urządzeń i zarządzanie nimi

Aby wyświetlić zasady i zarządzać nimi:

1. Na lewym pasku nawigacyjnym wybierz pozycję **Zarządzaj urządzeniami**\>.

    Na tej stronie możesz wybrać co najmniej jedno urządzenie i usunąć dane firmowe. W przypadku urządzeń Windows 10, dla których ustawiono ustawienia ochrony urządzeń, możesz również zresetować urządzenie do ustawień fabrycznych.
  
   ![Strona Zarządzanie urządzeniami.](../media/devicesmanage.png)

## <a name="working-with-device-policies-in-intune"></a>Praca z zasadami urządzeń w Intune

Poniższe informacje umożliwiają tworzenie zasad urządzeń i zarządzanie nimi w Intune, które są wykonywane za pośrednictwem zabezpieczeń punktu końcowego w centrum administracyjnym Microsoft Endpoint Manager.

### <a name="create-duplicate-and-edit-policies"></a>Tworzenie, duplikowanie i edytowanie zasad

Aby utworzyć zasady w Intune

1. Zaloguj się do centrum administracyjnego programu Microsoft Endpoint Manager.

1. Wybierz pozycję **Zabezpieczenia punktu końcowego** i typ zasad, które chcesz skonfigurować, a następnie wybierz pozycję **Utwórz zasady**.

1. Wybierz spośród następujących typów zasad:

    - Antivirus
    - Szyfrowanie dysków
    - Zapory
    - Wykrywanie i reagowanie dotyczące punktów końcowych
    - Zmniejszanie obszaru podatnego na ataki
    - Ochrona konta
    - Wprowadź następujące właściwości:

1. Platforma: wybierz platformę, dla której tworzysz zasady. Dostępne opcje zależą od wybranego typu zasad.

1. Profil: wybierz spośród dostępnych profilów wybranej platformy. Aby uzyskać informacje o profilach, zobacz dedykowaną sekcję w tym artykule dotyczącą wybranego typu zasad.

1. Wybierz pozycję **Utwórz**.

1. Na stronie Podstawowe wprowadź nazwę i opis dla profilu, a następnie wybierz pozycję **Dalej**.

1. Na stronie Ustawienia konfiguracji rozwiń każdą grupę ustawień i skonfiguruj ustawienia, które chcesz zarządzać przy użyciu tego profilu.

1. Po zakończeniu konfigurowania ustawień wybierz pozycję **Dalej**.

1. Na stronie Tagi zakresu wybierz **pozycję Wybierz tagi zakresu** , aby otworzyć okienko **Wybierz tagi** , aby przypisać tagi zakresu do profilu.

1. Wybierz przycisk **Dalej**, aby kontynuować.

1. Na stronie **Przypisania** wybierz grupy, które otrzymają ten profil. Aby uzyskać więcej informacji na temat przypisywania profilów, zobacz Przypisywanie profilów użytkowników i urządzeń.

1. Wybierz pozycję **Dalej**.

1. Na stronie Przeglądanie + tworzenie po zakończeniu wybierz pozycję **Utwórz**. Nowy profil zostanie wyświetlony na liście po wybraniu typu zasad dla utworzonego profilu.

Aby zduplikować zasady w Intune:

1. Zaloguj się do centrum administracyjnego programu Microsoft Endpoint Manager.

1. Wybierz zasady, które chcesz skopiować. Następnie wybierz pozycję **Duplikuj** lub wybierz wielokropek **(...)** po prawej stronie zasad i wybierz pozycję **Duplikuj**.
1. Podaj nową nazwę zasad, a następnie wybierz pozycję **Zapisz**.

Aby edytować zasady:

1. Wybierz nowe zasady, a następnie wybierz pozycję **Właściwości**.

1. Wybierz **pozycję Ustawienia**, aby rozwinąć listę ustawień konfiguracji w zasadach. Nie można zmodyfikować ustawień z tego widoku, ale możesz sprawdzić, jak są skonfigurowane.

1. Aby zmodyfikować zasady, wybierz pozycję **Edytuj** dla każdej kategorii, w której chcesz wprowadzić zmianę:

    - Podstawy
    - Przypisania
    - Tagi zakresu
    - Ustawienia konfiguracji

1. Po wprowadzeniu zmian wybierz pozycję **Zapisz** , aby zapisać zmiany. Przed wprowadzeniem zmian do dowolnych dodatkowych kategorii należy zapisać zmiany w jednej kategorii.

## <a name="manage-conflicts"></a>Zarządzanie konfliktami

Wiele ustawień urządzeń, które można zarządzać za pomocą zasad zabezpieczeń punktu końcowego, jest również dostępnych za pośrednictwem innych typów zasad w Intune. Te inne typy zasad obejmują zasady konfiguracji urządzeń i punkty odniesienia zabezpieczeń. Ponieważ ustawienia mogą być zarządzane za pomocą kilku różnych typów zasad lub wielu wystąpień tego samego typu zasad, należy przygotować się do identyfikowania i rozwiązywania konfliktów zasad dla urządzeń, które nie są zgodne z oczekiwanymi konfiguracjami.

Punkty odniesienia zabezpieczeń mogą ustawić wartość inną niż domyślna dla ustawienia, aby było zgodne z zalecaną konfiguracją adresów odniesienia.

Inne typy zasad, w tym zasady zabezpieczeń punktu końcowego, domyślnie ustawiają wartość Nieskonfigurowane. Te inne typy zasad wymagają jawnej konfiguracji ustawień w zasadach.

Niezależnie od metody zasad zarządzanie tym samym ustawieniem na tym samym urządzeniu za pomocą wielu typów zasad lub za pośrednictwem wielu wystąpień tego samego typu zasad może powodować konflikty, których należy unikać.

## <a name="see-also"></a>Zobacz też

[Zarządzanie zabezpieczeniami punktu końcowego w Microsoft Intune](/mem/Intune/protect/endpoint-security)

[Najlepsze rozwiązania dotyczące zabezpieczania Microsoft 365 dla planów biznesowych](../admin/security-and-compliance/secure-your-business-data.md)

## <a name="next-objective"></a>Następny cel

[Konfigurowanie grup urządzeń i zarządzanie nimi](m365bp-device-groups-mdb.md).