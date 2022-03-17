---
title: Wyświetlanie i edytowanie zasad w programie Microsoft Defender dla firm
description: Dowiedz się, jak wyświetlać, edytować, tworzyć i usuwać zasady ochrony następnej generacji w programie Microsoft Defender dla firm
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 03/15/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: cb79804985ee888faf1aa70029014a77ac9cae78
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2022
ms.locfileid: "63526776"
---
# <a name="view-or-edit-policies-in-microsoft-defender-for-business"></a>Wyświetlanie i edytowanie zasad w programie Microsoft Defender dla firm

> [!IMPORTANT]
> Program Microsoft Defender dla firm jest wprowadzany [dla Microsoft 365 Business Premium](../../business-premium/index.md) klientów od 1 marca 2022 r. Autonomiczna subskrypcja usługi Defender dla firm jest w wersji Preview i będzie stopniowo wprowadzana u klientów i partnerów IT, [](https://aka.ms/mdb-preview) którzy zarejestrują się tutaj, aby poprosić o to. Wersja Preview zawiera [początkowy zestaw scenariuszy](mdb-tutorials.md#try-these-preview-scenarios), a my będziemy regularnie dodawać funkcje.
> 
> Niektóre informacje w tym artykule dotyczą wstępnie dzierżawionych produktów/usług, które mogą zostać znacząco zmodyfikowane przed ich komercyjną premierą. Firma Microsoft nie udziela żadnych gwarancji, jawnych ani domniemanych, dotyczących podanych tutaj informacji. 

W programie Microsoft Defender for Business ustawienia zabezpieczeń są konfigurowane za pomocą zasad stosowanych do urządzeń. Aby uprościć proces konfiguracji i konfiguracji, program Defender dla firm zawiera wstępnie skonfigurowane zasady ułatwiające ochronę urządzeń firmowych zaraz po ich dojechu. Możesz używać zasad domyślnych, edytować zasady lub tworzyć własne zasady.

**W tym artykule opisano, jak to zrobić**:

- [Omówienie zasad domyślnych](#default-policies-in-defender-for-business)

- [Wyświetlanie istniejących zasad](#view-your-existing-policies)

- [Edytowanie istniejących zasad](#edit-an-existing-policy)

- [Tworzenie nowych zasad](#create-a-new-policy)

>
> **Masz minutę?**
> Prosimy o <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">krótką ankietę na temat programu Microsoft Defender dla firm</a>. Chcemy ją usłyszeć!
>

## <a name="default-policies-in-defender-for-business"></a>Zasady domyślne w uchcie programu Defender dla firm

W programie Defender dla firm istnieją dwa główne typy zasad ochrony urządzeń firmowych:

- **Zasady ochrony następnej generacji**, które określają sposób Program antywirusowy Microsoft Defender i innych funkcji ochrony przed zagrożeniami

- **Zasady zapory**, które określają, jaki ruch sieciowy może przepływać do i z urządzeń firmy


## <a name="view-your-existing-policies"></a>Wyświetlanie istniejących zasad

1. Przejdź do Microsoft 365 Defender portalu internetowego ([https://security.microsoft.com](https://security.microsoft.com)) i zaloguj się. 

2. W okienku nawigacji wybierz pozycję **Konfiguracja urządzenia**. Zasady są uporządkowane według systemu operacyjnego (na przykład **Windows klienta)** i typu zasad (na przykład ochrony następnej generacji **i** **zapory**). 

3. Wybierz kartę systemu operacyjnego (na Windows **klientów**), a następnie przejrzyj listę zasad w kategoriach Ochrona następnej generacji i Zapora.  

4. Aby wyświetlić więcej szczegółów dotyczących zasad, wybierz jej nazwę. Zostanie otwarte okienko boczne z większej liczby informacji o tych zasadach, na przykład o urządzeniach chronionych przez te zasady.

## <a name="edit-an-existing-policy"></a>Edytowanie istniejących zasad

1. Przejdź do Microsoft 365 Defender portalu internetowego ([https://security.microsoft.com](https://security.microsoft.com)) i zaloguj się. 

2. W okienku nawigacji wybierz pozycję **Konfiguracja urządzenia**. Zasady są uporządkowane według systemu operacyjnego (na przykład **Windows klienta)** i typu zasad (na przykład ochrony następnej generacji **i** **zapory**). 

3. Wybierz kartę systemu operacyjnego (na Windows **klientów**), a następnie przejrzyj listę zasad w kategoriach Ochrona następnej generacji i Zapora.  

4. Aby edytować zasady, zaznacz ich nazwę, a następnie wybierz pozycję **Edytuj**.

5. Przejrzyj **informacje na** karcie Informacje ogólne. W razie potrzeby możesz edytować opis. Następnie wybierz przycisk **Dalej**.

6. Na karcie **Grupy urządzeń** określ, które grupy urządzeń powinny otrzymywać te zasady.  

   - Aby zachować wybraną grupę urządzeń w stanie, w tym celu wybierz przycisk **Dalej**.
   - Aby usunąć grupę urządzeń z zasad, wybierz pozycję **Usuń**.
   - Aby skonfigurować nową grupę urządzeń, wybierz pozycję **Utwórz nową** grupę, a następnie skonfiguruj grupę urządzeń. (Aby uzyskać pomoc w tym zadaniu, zobacz [Grupy urządzeń w programie Microsoft Defender dla firm](mdb-create-edit-device-groups.md)).
   - Aby zastosować zasady do innej grupy urządzeń, wybierz **pozycję Użyj istniejącej grupy**.

   Po wybraniu grup urządzeń, które mają otrzymywać zasady, wybierz pozycję **Dalej**.

7. Na **karcie Ustawienia konfiguracji** przejrzyj ustawienia. W razie potrzeby możesz edytować ustawienia zasad. Aby uzyskać pomoc na temat tego zadania, zobacz następujące artykuły: 

   - [Opis ustawień konfiguracji następnej generacji](mdb-next-gen-configuration-settings.md)   
   - [Ustawienia zapory](mdb-firewall.md)

   Po wybraniu ustawień ochrony następnej generacji wybierz pozycję **Dalej**.

8. Na **karcie Przejrzyj zasady** przejrzyj ogólne informacje, urządzenia docelowe i ustawienia konfiguracji. 

   - W razie potrzeby zmień, wybierając pozycję **Edytuj**.
   - Gdy wszystko będzie gotowe do kontynuowania, wybierz **pozycję Aktualizuj zasady**.

## <a name="create-a-new-policy"></a>Tworzenie nowych zasad

1. Przejdź do Microsoft 365 Defender portalu internetowego ([https://security.microsoft.com](https://security.microsoft.com)) i zaloguj się. 

2. W okienku nawigacji wybierz pozycję **Konfiguracja urządzenia**. Zasady są uporządkowane według systemu operacyjnego (na przykład **Windows klienta)** i typu zasad (na przykład ochrony następnej generacji **i** **zapory**). 

3. Wybierz kartę systemu operacyjnego (na przykład Windows **klientów**), a następnie przejrzyj listę zasad **ochrony następnej** generacji. 

4. W **obszarze Ochrona następnej generacji** lub **Zapora** wybierz pozycję **+ Dodaj**.

5. Na **karcie Informacje ogólne** zrób tak:

   1. Określ nazwę i opis. Te informacje pomogą Zespołowi w zidentyfikowaniu zasad w późniejszym czasie.
   2. Przejrzyj kolejność zasad i w razie potrzeby ją edytuj. (Aby uzyskać więcej informacji, zobacz [Kolejność zasad](mdb-policy-order.md)).
   3. Wybierz przycisk **Dalej**. 

7. Na karcie **Grupy** urządzeń utwórz nową grupę urządzeń lub użyj istniejącej grupy. Zasady są przypisywane do urządzeń za pośrednictwem grup urządzeń. Oto kilka rzeczy, o których należy pamiętać:

   - Początkowo może być dostępna tylko domyślna grupa urządzeń, która zawiera urządzenia, za pomocą których osoby w Twojej firmie mają dostęp do danych firmowych i poczty e-mail. Możesz zachować domyślną grupę urządzeń i korzystać z jej.
   - Utwórz nową grupę urządzeń, aby zastosować zasady z określonymi ustawieniami, które różnią się od zasad domyślnych. 
   - Podczas instalacji grupy urządzeń należy określić pewne kryteria, na przykład wersję systemu operacyjnego. Urządzenia spełniające te kryteria są uwzględniane w tej grupie urządzeń, o ile nie zostaną wykluczone. 
   - Wszystkie grupy urządzeń, w tym domyślne i niestandardowe grupy urządzeń, które definiujesz, są przechowywane w usłudze Azure Active Directory (Azure AD).

   Aby dowiedzieć się więcej o grupach urządzeń, zobacz [Grupy urządzeń w programie Defender dla firm](mdb-create-edit-device-groups.md).

8. Na karcie **Ustawienia konfiguracji** określ ustawienia zasad, a następnie wybierz przycisk **Dalej**. Aby uzyskać więcej informacji na temat poszczególnych ustawień, zobacz [Ustawienia konfiguracji programu Microsoft Defender dla firm](mdb-next-gen-configuration-settings.md).

9. Na **karcie Przejrzyj zasady** przejrzyj ogólne informacje, urządzenia docelowe i ustawienia konfiguracji. 

   - W razie potrzeby zmień, wybierając pozycję **Edytuj**.
   - Gdy wszystko będzie gotowe do kontynuowania, wybierz **pozycję Utwórz zasady**.


## <a name="next-steps"></a>Następne kroki

Wybierz co najmniej jedno z następujących zadań:

- [Zarządzanie urządzeniami](mdb-manage-devices.md)

- [Tworzenie nowych zasad w programie Microsoft Defender dla firm](mdb-create-new-policy.md)

- [Wyświetlanie zdarzeń i zarządzanie nimi w programie Microsoft Defender dla firm](mdb-view-manage-incidents.md)

- [Reagowanie na zagrożenia i ograniczanie ich w programie Microsoft Defender dla firm](mdb-respond-mitigate-threats.md)

- [Przeglądanie działań naprawczych w Centrum akcji](mdb-review-remediation-actions.md)