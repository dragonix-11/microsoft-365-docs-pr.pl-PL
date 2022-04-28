---
title: Wyświetlanie lub edytowanie zasad ochrony urządzeń
description: Wyświetlanie, edytowanie, tworzenie i usuwanie zasad ochrony urządzeń w Microsoft 365 Business Premium
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 03/14/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: high
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: 816b425fbbd511b68d2c21f313b497bbd4b77f8a
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65087052"
---
# <a name="view-and-edit-your-device-protection-policies"></a>Wyświetlanie i edytowanie zasad ochrony urządzeń

W Microsoft 365 Business Premium ustawienia zabezpieczeń dla urządzeń zarządzanych są konfigurowane za pomocą zasad ochrony urządzeń. Aby uprościć konfigurację i środowisko konfiguracji, masz wstępnie skonfigurowane zasady, które ułatwiają ochronę urządzeń organizacji zaraz po ich dołączeniu. Użyj zasad domyślnych, edytuj istniejące zasady lub utwórz własne zasady.

**W tych wskazówkach opisano, jak** wykonać następujące czynności:

- Zapoznaj się z omówieniem domyślnych zasad
- Wyświetlanie istniejących zasad
- Edytowanie istniejących zasad
- Tworzenie nowych zasad

## <a name="default-device-protection-policies"></a>Domyślne zasady ochrony urządzeń

Microsoft 365 Business Premium obejmuje dwa główne typy zasad ochrony urządzeń organizacji:

- **Zasady ochrony nowej generacji**, które określają sposób konfigurowania Program antywirusowy Microsoft Defender i innych funkcji ochrony przed zagrożeniami

- **Zasady zapory** określające, jaki ruch sieciowy może przepływać do i z urządzeń organizacji

Te zasady są częścią Microsoft Defender dla Firm, która jest uwzględniona w subskrypcji Microsoft 365 Business Premium.

## <a name="view-your-existing-device-protection-policies"></a>Wyświetlanie istniejących zasad ochrony urządzeń

1. Przejdź do portalu Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) i zaloguj się. 

2. W okienku nawigacji wybierz pozycję **Konfiguracja urządzenia**. Zasady są zorganizowane według systemu operacyjnego (na przykład **klienta Windows**) i typu zasad (na przykład **ochrony następnej generacji** i **zapory**). 

    :::image type="content" source="../media/mdb-deviceconfiguration.png" lightbox="../media/mdb-deviceconfiguration.png" alt-text="Strona Konfiguracja urządzenia.":::

3. Wybierz kartę systemu operacyjnego (na przykład **Windows klientów**), a następnie przejrzyj listę zasad w kategoriach **Ochrona następnej generacji** i **Zapora**. 

4. Aby wyświetlić więcej szczegółów dotyczących zasad, wybierz jej nazwę. Zostanie otwarte okienko boczne, które zawiera więcej informacji o tych zasadach, takich jak urządzenia chronione przez te zasady.

   :::image type="content" source="../media/mdb-deviceconfig-selectedpolicy.png" lightbox="../media/mdb-deviceconfig-selectedpolicy.png" alt-text="Zrzut ekranu przedstawiający zasady wybrane na stronie Konfiguracja urządzenia.":::

## <a name="edit-an-existing-device-protection-policy"></a>Edytowanie istniejących zasad ochrony urządzeń

1. Przejdź do portalu Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) i zaloguj się. 

2. W okienku nawigacji wybierz pozycję **Konfiguracja urządzenia**. Zasady są zorganizowane według systemu operacyjnego (na przykład **klienta Windows**) i typu zasad (na przykład **ochrony następnej generacji** i **zapory**). 

3. Wybierz kartę systemu operacyjnego (na przykład **Windows klientów**), a następnie przejrzyj listę zasad w kategoriach **Ochrona następnej generacji** i **Zapora**. 

4. Aby edytować zasady, wybierz jej nazwę, a następnie wybierz pozycję **Edytuj**.

5. Na karcie **Informacje ogólne** przejrzyj informacje. W razie potrzeby możesz edytować opis. Następnie wybierz pozycję **Dalej**.

6. Na karcie **Grupy urządzeń** określ, które grupy urządzeń powinny otrzymywać te zasady.  

   - Aby zachować wybraną grupę urządzeń w następującym stanie, wybierz pozycję **Dalej**.
   - Aby usunąć grupę urządzeń z zasad, wybierz pozycję **Usuń**.
   - Aby skonfigurować nową grupę urządzeń, wybierz pozycję **Utwórz nową grupę**, a następnie skonfiguruj grupę urządzeń. (Aby uzyskać pomoc dotyczącą tego zadania, zobacz [Grupy urządzeń w Microsoft 365 Business Premium](m365bp-device-groups-mdb.md)).
   - Aby zastosować zasady do innej grupy urządzeń, wybierz pozycję **Użyj istniejącej grupy**.

   Po określeniu, które grupy urządzeń powinny otrzymywać zasady, wybierz pozycję **Dalej**.

7. Na karcie **Ustawienia konfiguracji** przejrzyj ustawienia. W razie potrzeby można edytować ustawienia zasad. Aby uzyskać pomoc dotyczącą tego zadania, zobacz następujące artykuły: 

   - [Omówienie ustawień konfiguracji następnej generacji](../security/defender-business/mdb-next-gen-configuration-settings.md)   
   - [Ustawienia zapory](../security/defender-business/mdb-firewall.md)

   Po określeniu ustawień ochrony nowej generacji wybierz pozycję **Dalej**.

8. Na karcie **Przeglądanie zasad** zapoznaj się z ogólnymi informacjami, urządzeniami docelowymi i ustawieniami konfiguracji. 

   - Wprowadź wszelkie wymagane zmiany, wybierając pozycję **Edytuj**.
   - Gdy wszystko będzie gotowe do kontynuowania, wybierz pozycję **Aktualizuj zasady**.

## <a name="create-a-new-device-protection-policy"></a>Tworzenie nowych zasad ochrony urządzeń

1. Przejdź do portalu Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) i zaloguj się. 

2. W okienku nawigacji wybierz pozycję **Konfiguracja urządzenia**. Zasady są zorganizowane według systemu operacyjnego (na przykład **klienta Windows**) i typu zasad (na przykład **ochrony następnej generacji** i **zapory**). 

3. Wybierz kartę systemu operacyjnego (na przykład **Windows klientów**), a następnie przejrzyj listę zasad **ochrony następnej generacji**. 

4. W obszarze **Ochrona następnej generacji** lub **Zapora** wybierz pozycję **+ Dodaj**.

5. Na karcie **Informacje ogólne** wykonaj następujące kroki:

   1. Określ nazwę i opis. Te informacje pomogą Tobie i Twojej drużynie zidentyfikować zasady później.
   2. Przejrzyj kolejność zasad i w razie potrzeby edytuj ją. (Aby uzyskać więcej informacji, zobacz [Kolejność zasad](../security/defender-business/mdb-policy-order.md)).
   3. Wybierz przycisk **Dalej**. 

7. Na karcie **Grupy urządzeń** utwórz nową grupę urządzeń lub użyj istniejącej grupy. Zasady są przypisywane do urządzeń za pośrednictwem grup urządzeń. Oto kilka kwestii, o których należy pamiętać:

   - Początkowo możesz mieć tylko domyślną grupę urządzeń, która obejmuje urządzenia używane przez osoby w organizacji do uzyskiwania dostępu do danych organizacji i poczty e-mail. Możesz zachować domyślną grupę urządzeń i korzystać z niej.
   - Utwórz nową grupę urządzeń, aby zastosować zasady z określonymi ustawieniami, które różnią się od zasad domyślnych. 
   - Podczas konfigurowania grupy urządzeń należy określić pewne kryteria, takie jak wersja systemu operacyjnego. Urządzenia spełniające kryteria są uwzględniane w tej grupie urządzeń, chyba że zostaną wykluczone. 
   - Wszystkie grupy urządzeń, w tym zdefiniowane domyślne i niestandardowe grupy urządzeń, są przechowywane w Azure Active Directory (Azure AD).

   Aby dowiedzieć się więcej o grupach urządzeń, zobacz [Temat Grupy urządzeń w Microsoft Defender dla Firm](../security/defender-business/mdb-create-edit-device-groups.md).

8. Na **karcie Ustawienia konfiguracji** określ ustawienia zasad, a następnie wybierz pozycję **Dalej**. Aby uzyskać więcej informacji na temat poszczególnych ustawień, zobacz [Omówienie ustawień konfiguracji nowej generacji w Microsoft Defender dla Firm](../security/defender-business/mdb-next-gen-configuration-settings.md).

9. Na karcie **Przeglądanie zasad** zapoznaj się z ogólnymi informacjami, urządzeniami docelowymi i ustawieniami konfiguracji. 

   - Wprowadź wszelkie wymagane zmiany, wybierając pozycję **Edytuj**.
   - Gdy wszystko będzie gotowe do kontynuowania, wybierz pozycję **Utwórz zasady**.

## <a name="next-objective"></a>Następny cel

Konfigurowanie [grup urządzeń](m365bp-device-groups-mdb.md) i zarządzanie nimi.

