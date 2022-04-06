---
title: Wyświetlanie i edytowanie zasad ochrony urządzeń
description: Wyświetlanie, edytowanie, tworzenie i usuwanie zasad ochrony urządzeń w aplikacji Microsoft 365 Business Premium
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
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
ms.openlocfilehash: ba322493b3900c099ab5525f052604604ef0ac23
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2022
ms.locfileid: "63705480"
---
# <a name="view-and-edit-your-device-protection-policies"></a>Wyświetlanie i edytowanie zasad ochrony urządzeń

W Microsoft 365 Business Premium zabezpieczeń dla urządzeń zarządzanych są konfigurowane za pomocą zasad ochrony urządzeń. Aby uprościć proces konfiguracji i konfiguracji, dostępne są wstępnie skonfigurowane zasady, które mogą pomóc chronić urządzenia organizacji zaraz po ich dojechach. Możesz używać zasad domyślnych, edytować zasady lub tworzyć własne zasady.

**W tym artykule opisano, jak to zrobić**:

- Omówienie zasad domyślnych
- Wyświetlanie istniejących zasad
- Edytowanie istniejących zasad
- Tworzenie nowych zasad

## <a name="default-device-protection-policies"></a>Domyślne zasady ochrony urządzeń

Microsoft 365 Business Premium zawiera dwa główne typy zasad ochrony urządzeń organizacji:

- **Zasady ochrony następnej generacji**, które określają sposób Program antywirusowy Microsoft Defender i innych funkcji ochrony przed zagrożeniami

- **Zasady zapory**, które określają, jaki ruch sieciowy może przepływać do i z urządzeń organizacji

Te zasady są częścią usługi Microsoft Defender dla firm, która jest zawarta w Twojej Microsoft 365 Business Premium subskrypcji usługi.

## <a name="view-your-existing-device-protection-policies"></a>Wyświetlanie istniejących zasad ochrony urządzeń

1. Przejdź do Microsoft 365 Defender portalu internetowego ([https://security.microsoft.com](https://security.microsoft.com)) i zaloguj się. 

2. W okienku nawigacji wybierz pozycję **Konfiguracja urządzenia**. Zasady są uporządkowane według systemu operacyjnego (na przykład **Windows klienta)** i typu zasad (na przykład ochrony następnej generacji **i** **zapory**). 

3. Wybierz kartę systemu operacyjnego (na Windows **klientów**), a następnie przejrzyj listę zasad w kategoriach Ochrona następnej generacji i Zapora.  

4. Aby wyświetlić więcej szczegółów dotyczących zasad, wybierz jej nazwę. Zostanie otwarte okienko boczne z większej liczby informacji o tych zasadach, na przykład o urządzeniach chronionych przez te zasady.

## <a name="edit-an-existing-device-protection-policy"></a>Edytowanie istniejących zasad ochrony urządzeń

1. Przejdź do Microsoft 365 Defender portalu internetowego ([https://security.microsoft.com](https://security.microsoft.com)) i zaloguj się. 

2. W okienku nawigacji wybierz pozycję **Konfiguracja urządzenia**. Zasady są uporządkowane według systemu operacyjnego (na przykład **Windows klienta)** i typu zasad (na przykład ochrony następnej generacji **i** **zapory**). 

3. Wybierz kartę systemu operacyjnego (na Windows **klientów**), a następnie przejrzyj listę zasad w kategoriach Ochrona następnej generacji i Zapora.  

4. Aby edytować zasady, zaznacz ich nazwę, a następnie wybierz pozycję **Edytuj**.

5. Przejrzyj **informacje na** karcie Informacje ogólne. W razie potrzeby możesz edytować opis. Następnie wybierz przycisk **Dalej**.

6. Na karcie **Grupy urządzeń** określ, które grupy urządzeń powinny otrzymywać te zasady.  

   - Aby zachować wybraną grupę urządzeń w stanie, w tym celu wybierz przycisk **Dalej**.
   - Aby usunąć grupę urządzeń z zasad, wybierz pozycję **Usuń**.
   - Aby skonfigurować nową grupę urządzeń, wybierz pozycję **Utwórz nową** grupę, a następnie skonfiguruj grupę urządzeń. (Aby uzyskać pomoc na temat tego zadania, zobacz [Grupy urządzeń Microsoft 365 Business Premium](m365bp-device-groups-mdb.md)).
   - Aby zastosować zasady do innej grupy urządzeń, wybierz **pozycję Użyj istniejącej grupy**.

   Po wybraniu grup urządzeń, które mają otrzymywać zasady, wybierz pozycję **Dalej**.

7. Na **karcie Ustawienia konfiguracji** przejrzyj ustawienia. W razie potrzeby możesz edytować ustawienia zasad. Aby uzyskać pomoc na temat tego zadania, zobacz następujące artykuły: 

   - [Opis ustawień konfiguracji następnej generacji](../security/defender-business/mdb-next-gen-configuration-settings.md)   
   - [Ustawienia zapory](../security/defender-business/mdb-firewall.md)

   Po wybraniu ustawień ochrony następnej generacji wybierz pozycję **Dalej**.

8. Na **karcie Przejrzyj zasady** przejrzyj ogólne informacje, urządzenia docelowe i ustawienia konfiguracji. 

   - W razie potrzeby zmień, wybierając pozycję **Edytuj**.
   - Gdy wszystko będzie gotowe do kontynuowania, wybierz **pozycję Aktualizuj zasady**.

## <a name="create-a-new-device-protection-policy"></a>Tworzenie nowych zasad ochrony urządzeń

1. Przejdź do Microsoft 365 Defender portalu internetowego ([https://security.microsoft.com](https://security.microsoft.com)) i zaloguj się. 

2. W okienku nawigacji wybierz pozycję **Konfiguracja urządzenia**. Zasady są uporządkowane według systemu operacyjnego (na przykład **Windows klienta)** i typu zasad (na przykład ochrony następnej generacji **i** **zapory**). 

3. Wybierz kartę systemu operacyjnego (na przykład Windows **klientów**), a następnie przejrzyj listę zasad **ochrony następnej** generacji. 

4. W **obszarze Ochrona następnej generacji** lub **Zapora** wybierz pozycję **+ Dodaj**.

5. Na **karcie Informacje ogólne** zrób tak:

   1. Określ nazwę i opis. Te informacje pomogą Zespołowi w zidentyfikowaniu zasad w późniejszym czasie.
   2. Przejrzyj kolejność zasad i w razie potrzeby ją edytuj. (Aby uzyskać więcej informacji, zobacz [Kolejność zasad](../security/defender-business/mdb-policy-order.md)).
   3. Wybierz przycisk **Dalej**. 

7. Na karcie **Grupy** urządzeń utwórz nową grupę urządzeń lub użyj istniejącej grupy. Zasady są przypisywane do urządzeń za pośrednictwem grup urządzeń. Oto kilka rzeczy, o których należy pamiętać:

   - Początkowo może być dostępna tylko domyślna grupa urządzeń, która zawiera urządzenia, których osoby w Twojej organizacji używa do uzyskiwania dostępu do danych organizacji i poczty e-mail. Możesz zachować domyślną grupę urządzeń i korzystać z jej.
   - Utwórz nową grupę urządzeń, aby zastosować zasady z określonymi ustawieniami, które różnią się od zasad domyślnych. 
   - Podczas instalacji grupy urządzeń należy określić pewne kryteria, na przykład wersję systemu operacyjnego. Urządzenia spełniające te kryteria są uwzględniane w tej grupie urządzeń, o ile nie zostaną wykluczone. 
   - Wszystkie grupy urządzeń, w tym domyślne i niestandardowe grupy urządzeń, które definiujesz, są przechowywane w usłudze Azure Active Directory (Azure AD).

   Aby dowiedzieć się więcej o grupach urządzeń, zobacz [Grupy urządzeń w programie Microsoft Defender dla firm](../security/defender-business/mdb-create-edit-device-groups.md).

8. Na karcie **Ustawienia konfiguracji** określ ustawienia zasad, a następnie wybierz przycisk **Dalej**. Aby uzyskać więcej informacji na temat poszczególnych ustawień, zobacz [Opis ustawień konfiguracji następnej generacji w programie Microsoft Defender dla firm](../security/defender-business/mdb-next-gen-configuration-settings.md).

9. Na **karcie Przejrzyj zasady** przejrzyj ogólne informacje, urządzenia docelowe i ustawienia konfiguracji. 

   - W razie potrzeby zmień, wybierając pozycję **Edytuj**.
   - Gdy wszystko będzie gotowe do kontynuowania, wybierz **pozycję Utwórz zasady**.


## <a name="next-steps"></a>Następne kroki

[Grupy urządzeń w aplikacji Microsoft 365 Business Premium](m365bp-device-groups-mdb.md)