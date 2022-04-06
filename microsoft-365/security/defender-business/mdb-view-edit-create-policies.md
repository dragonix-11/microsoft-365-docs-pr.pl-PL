---
title: Wyświetlanie lub edytowanie zasad w Microsoft Defender dla Firm
description: Dowiedz się, jak wyświetlać, edytować, tworzyć i usuwać zasady ochrony nowej generacji w Microsoft Defender dla Firm
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
ms.openlocfilehash: 6f8ad1bd1f77bd3e53a1686674984155a7dc8525
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2022
ms.locfileid: "64665101"
---
# <a name="view-or-edit-policies-in-microsoft-defender-for-business"></a>Wyświetlanie lub edytowanie zasad w Microsoft Defender dla Firm

> [!IMPORTANT]
> Microsoft Defender dla Firm jest wdrażana dla [klientów Microsoft 365 Business Premium](../../business-premium/index.md) od 1 marca 2022 r. Usługa Defender dla Firm jako subskrypcja autonomiczna jest dostępna w wersji zapoznawczej i będzie stopniowo wdrażana dla klientów i partnerów IT, którzy [zarejestrują się tutaj](https://aka.ms/mdb-preview) , aby zażądać tej subskrypcji. Wersja zapoznawcza zawiera [początkowy zestaw scenariuszy](mdb-tutorials.md#try-these-preview-scenarios), a my będziemy regularnie dodawać możliwości.
> 
> Niektóre informacje zawarte w tym artykule odnoszą się do wstępnie wydanych produktów/usług, które mogą zostać znacząco zmodyfikowane przed ich komercyjnym wydaniem. Firma Microsoft nie udziela żadnych gwarancji, wyraźnych ani dorozumianych, dotyczących informacji podanych tutaj. 

W Microsoft Defender dla Firm ustawienia zabezpieczeń są konfigurowane za pomocą zasad stosowanych do urządzeń. Aby uprościć konfigurację i środowisko konfiguracji, usługa Defender dla firm zawiera wstępnie skonfigurowane zasady ułatwiające ochronę urządzeń firmy natychmiast po ich dołączeniu. Możesz użyć zasad domyślnych, edytować zasady lub tworzyć własne zasady.

**W tym artykule opisano sposób wykonywania następujących czynności**:

- [Zapoznaj się z omówieniem domyślnych zasad](#default-policies-in-defender-for-business)

- [Wyświetlanie istniejących zasad](#view-your-existing-policies)

- [Edytowanie istniejących zasad](#edit-an-existing-policy)

- [Tworzenie nowych zasad](#create-a-new-policy)

>
> **Masz minutę?**
> Weźmy <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">krótką ankietę dotyczącą Microsoft Defender dla Firm</a>. Chcielibyśmy usłyszeć od Ciebie!
>

## <a name="default-policies-in-defender-for-business"></a>Zasady domyślne w usłudze Defender dla Firm

W usłudze Defender dla firm istnieją dwa główne typy zasad ochrony urządzeń firmy:

- **Zasady ochrony nowej generacji**, które określają sposób konfigurowania Program antywirusowy Microsoft Defender i innych funkcji ochrony przed zagrożeniami

- **Zasady zapory**, które określają, jaki ruch sieciowy może przepływać do i z urządzeń firmy


## <a name="view-your-existing-policies"></a>Wyświetlanie istniejących zasad

1. Przejdź do portalu Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) i zaloguj się. 

2. W okienku nawigacji wybierz pozycję **Konfiguracja urządzenia**. Zasady są zorganizowane według systemu operacyjnego (na przykład **klienta Windows**) i typu zasad (na przykład **ochrony następnej generacji** i **zapory**). 

3. Wybierz kartę systemu operacyjnego (na przykład **Windows klientów**), a następnie przejrzyj listę zasad w kategoriach **Ochrona następnej generacji** i **Zapora**. 

4. Aby wyświetlić więcej szczegółów dotyczących zasad, wybierz jej nazwę. Zostanie otwarte okienko boczne, które zawiera więcej informacji o tych zasadach, takich jak urządzenia chronione przez te zasady.

## <a name="edit-an-existing-policy"></a>Edytowanie istniejących zasad

1. Przejdź do portalu Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) i zaloguj się. 

2. W okienku nawigacji wybierz pozycję **Konfiguracja urządzenia**. Zasady są zorganizowane według systemu operacyjnego (na przykład **klienta Windows**) i typu zasad (na przykład **ochrony następnej generacji** i **zapory**). 

3. Wybierz kartę systemu operacyjnego (na przykład **Windows klientów**), a następnie przejrzyj listę zasad w kategoriach **Ochrona następnej generacji** i **Zapora**. 

4. Aby edytować zasady, wybierz jej nazwę, a następnie wybierz pozycję **Edytuj**.

5. Na karcie **Informacje ogólne** przejrzyj informacje. W razie potrzeby możesz edytować opis. Następnie wybierz pozycję **Dalej**.

6. Na karcie **Grupy urządzeń** określ, które grupy urządzeń powinny otrzymywać te zasady.  

   - Aby zachować wybraną grupę urządzeń w następującym stanie, wybierz pozycję **Dalej**.
   - Aby usunąć grupę urządzeń z zasad, wybierz pozycję **Usuń**.
   - Aby skonfigurować nową grupę urządzeń, wybierz pozycję **Utwórz nową grupę**, a następnie skonfiguruj grupę urządzeń. (Aby uzyskać pomoc dotyczącą tego zadania, zobacz [Grupy urządzeń w Microsoft Defender dla Firm](mdb-create-edit-device-groups.md)).
   - Aby zastosować zasady do innej grupy urządzeń, wybierz pozycję **Użyj istniejącej grupy**.

   Po określeniu, które grupy urządzeń powinny otrzymywać zasady, wybierz pozycję **Dalej**.

7. Na karcie **Ustawienia konfiguracji** przejrzyj ustawienia. W razie potrzeby można edytować ustawienia zasad. Aby uzyskać pomoc dotyczącą tego zadania, zobacz następujące artykuły: 

   - [Omówienie ustawień konfiguracji następnej generacji](mdb-next-gen-configuration-settings.md)   
   - [Ustawienia zapory](mdb-firewall.md)

   Po określeniu ustawień ochrony nowej generacji wybierz pozycję **Dalej**.

8. Na karcie **Przeglądanie zasad** zapoznaj się z ogólnymi informacjami, urządzeniami docelowymi i ustawieniami konfiguracji. 

   - Wprowadź wszelkie wymagane zmiany, wybierając pozycję **Edytuj**.
   - Gdy wszystko będzie gotowe do kontynuowania, wybierz pozycję **Aktualizuj zasady**.

## <a name="create-a-new-policy"></a>Tworzenie nowych zasad

1. Przejdź do portalu Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) i zaloguj się. 

2. W okienku nawigacji wybierz pozycję **Konfiguracja urządzenia**. Zasady są zorganizowane według systemu operacyjnego (na przykład **klienta Windows**) i typu zasad (na przykład **ochrony następnej generacji** i **zapory**). 

3. Wybierz kartę systemu operacyjnego (na przykład **Windows klientów**), a następnie przejrzyj listę zasad **ochrony następnej generacji**. 

4. W obszarze **Ochrona następnej generacji** lub **Zapora** wybierz pozycję **+ Dodaj**.

5. Na karcie **Informacje ogólne** wykonaj następujące kroki:

   1. Określ nazwę i opis. Te informacje pomogą Tobie i Twojej drużynie zidentyfikować zasady później.
   2. Przejrzyj kolejność zasad i w razie potrzeby edytuj ją. (Aby uzyskać więcej informacji, zobacz [Kolejność zasad](mdb-policy-order.md)).
   3. Wybierz przycisk **Dalej**. 

7. Na karcie **Grupy urządzeń** utwórz nową grupę urządzeń lub użyj istniejącej grupy. Zasady są przypisywane do urządzeń za pośrednictwem grup urządzeń. Oto kilka kwestii, o których należy pamiętać:

   - Początkowo możesz mieć tylko domyślną grupę urządzeń, która obejmuje urządzenia używane przez osoby w firmie do uzyskiwania dostępu do danych firmowych i poczty e-mail. Możesz zachować domyślną grupę urządzeń i korzystać z niej.
   - Utwórz nową grupę urządzeń, aby zastosować zasady z określonymi ustawieniami, które różnią się od zasad domyślnych. 
   - Podczas konfigurowania grupy urządzeń należy określić pewne kryteria, takie jak wersja systemu operacyjnego. Urządzenia spełniające kryteria są uwzględniane w tej grupie urządzeń, chyba że zostaną wykluczone. 
   - Wszystkie grupy urządzeń, w tym zdefiniowane domyślne i niestandardowe grupy urządzeń, są przechowywane w Azure Active Directory (Azure AD).

   Aby dowiedzieć się więcej o grupach urządzeń, zobacz [Grupy urządzeń w usłudze Defender dla Firm](mdb-create-edit-device-groups.md).

8. Na **karcie Ustawienia konfiguracji** określ ustawienia zasad, a następnie wybierz pozycję **Dalej**. Aby uzyskać więcej informacji na temat poszczególnych ustawień, zobacz [Ustawienia konfiguracji dla Microsoft Defender dla Firm](mdb-next-gen-configuration-settings.md).

9. Na karcie **Przeglądanie zasad** zapoznaj się z ogólnymi informacjami, urządzeniami docelowymi i ustawieniami konfiguracji. 

   - Wprowadź wszelkie wymagane zmiany, wybierając pozycję **Edytuj**.
   - Gdy wszystko będzie gotowe do kontynuowania, wybierz pozycję **Utwórz zasady**.


## <a name="next-steps"></a>Następne kroki

Wybierz co najmniej jedno z następujących zadań:

- [Zarządzanie urządzeniami](mdb-manage-devices.md)

- [Tworzenie nowych zasad w Microsoft Defender dla Firm](mdb-create-new-policy.md)

- [Wyświetlanie zdarzeń i zarządzanie nimi w Microsoft Defender dla Firm](mdb-view-manage-incidents.md)

- [Reagowanie na zagrożenia w Microsoft Defender dla Firm i eliminowanie ich](mdb-respond-mitigate-threats.md)

- [Przeglądanie akcji korygowania w centrum akcji](mdb-review-remediation-actions.md)