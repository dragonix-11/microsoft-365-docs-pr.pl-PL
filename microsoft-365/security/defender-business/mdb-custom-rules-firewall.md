---
title: Zarządzanie regułami niestandardowymi dla zasad zapory w programie Microsoft Defender dla firm
description: Reguły niestandardowe zapewniają wyjątki od zasad zapory. Za pomocą reguł niestandardowych można blokować określone połączenia lub zezwalać na nie w programie Microsoft Defender dla Firm.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 02/24/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: 161ce8a20500bdea7d2ccd2dd9cc8a387345de1c
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2022
ms.locfileid: "63525878"
---
# <a name="manage-your-custom-rules-for-firewall-policies-in-microsoft-defender-for-business"></a>Zarządzanie niestandardowymi regułami zasad zapory w programie Microsoft Defender dla firm

> [!IMPORTANT]
> Program Microsoft Defender dla firm jest wprowadzany [dla Microsoft 365 Business Premium](../../business-premium/index.md) klientów od 1 marca 2022 r. Autonomiczna subskrypcja usługi Defender dla firm jest w wersji Preview i będzie stopniowo wprowadzana u klientów i partnerów IT, [](https://aka.ms/mdb-preview) którzy zarejestrują się tutaj, aby poprosić o to. Wersja Preview zawiera [początkowy zestaw scenariuszy](mdb-tutorials.md#try-these-preview-scenarios), a my będziemy regularnie dodawać funkcje.
> 
> Niektóre informacje w tym artykule dotyczą wstępnie dzierżawionych produktów/usług, które mogą zostać znacząco zmodyfikowane przed ich komercyjną premierą. Firma Microsoft nie udziela żadnych gwarancji, jawnych ani domniemanych, dotyczących podanych tutaj informacji. 


Usługa Microsoft Defender dla firm zawiera zasady zapory, które pomagają chronić urządzenia przed niechcianym ruchem sieciowym. Reguły niestandardowe mogą umożliwiać definiowanie wyjątków dla zasad zapory. Oznacza to, że za pomocą reguł niestandardowych można blokować określone połączenia lub zezwalać na nie.

Aby dowiedzieć się więcej o zasadach i ustawieniach zapory, zobacz [Zapora w programie Microsoft Defender dla firm](mdb-firewall.md).

**W tym artykule opisano, jak to zrobić**:

- [Tworzenie reguły niestandardowej dla zasad zapory](#create-a-custom-rule-for-a-firewall-policy)
- [Edytowanie reguły niestandardowej zasad zapory](#edit-a-custom-rule-for-a-firewall-policy)
- [Usuwanie reguły niestandardowej](#delete-a-custom-rule)

>
> **Masz minutę?**
> Prosimy o <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">krótką ankietę na temat programu Microsoft Defender dla firm</a>. Chcemy ją usłyszeć!
>

## <a name="create-a-custom-rule-for-a-firewall-policy"></a>Tworzenie reguły niestandardowej dla zasad zapory

1. Przejdź do Microsoft 365 Defender konta ([https://security.microsoft.com](https://security.microsoft.com)) i zaloguj się.

2. Przejdź do **endpointsDevice** >  configuration i przejrzyj listę zasad.

3. W sekcji **Zapora** wybierz istniejące zasady lub dodaj nowe zasady.

4. W **kroku Ustawienia konfiguracji** przejrzyj ustawienia. W razie potrzeby należy wprowadzić zmiany **w sieci domeny**, **sieci publicznej** i **sieci prywatnej**.

5. Aby utworzyć regułę niestandardową, wykonaj następujące czynności: 

   1. W **obszarze Reguły niestandardowe** wybierz **pozycję + Dodaj regułę**. (Możesz mieć maksymalnie 150 reguł niestandardowych).
   2. W **wysuwanych polach Utwórz** nową regułę podaj nazwę i opis reguły.
   3. Wybierz profil. (Dostępne opcje to **Sieć domenowa**, **Sieć publiczna** lub **Sieć prywatna**).
   4. Na liście **Remote address type (Typ adresu zdalnego**) wybierz **ścieżkę IP** **lub Application file path (Ścieżka pliku aplikacji).**
   5. W **polu Wartość** określ odpowiednią wartość. W zależności od opcji wybranej w kroku 6d możesz określić adres IP, zakres adresów IP lub ścieżkę pliku aplikacji. (Zobacz [Ustawienia zapory](mdb-firewall.md)).
   6. Na **wysuwanych przyciskach Utwórz nową** regułę wybierz **pozycję Utwórz regułę**. 

6. Na **ekranie Ustawienia konfiguracji** wybierz pozycję **Dalej**.

7. Na **ekranie Przeglądanie zasad** przejrzyj zmiany wprowadzone w ustawieniach zasad zapory. Wprowadzić wszelkie potrzebne zmiany, a następnie wybierz **pozycję Utwórz zasady**.

## <a name="edit-a-custom-rule-for-a-firewall-policy"></a>Edytowanie reguły niestandardowej zasad zapory

1. Przejdź do Microsoft 365 Defender konta ([https://security.microsoft.com](https://security.microsoft.com)) i zaloguj się.

2. Przejdź do **endpointsDevice** >  configuration i przejrzyj listę zasad.

3. W sekcji **Zapora** wybierz istniejące zasady lub dodaj nowe zasady.

4. W **obszarze Reguły** niestandardowe przejrzyj listę reguł.

5. Zaznacz regułę, a następnie wybierz pozycję **Edytuj**. Zostanie otwarte wysunięcie tego menu.

6. Aby edytować regułę niestandardową, wykonaj następujące czynności:

   1. Na **wysuwanych** oknie edytowanie reguły przejrzyj i edytuj nazwę i opis reguły.
   2. Przejrzyj i w razie potrzeby edytuj profil reguły. (Dostępne opcje to **Sieć domenowa**, **Sieć publiczna** lub **Sieć prywatna**).
   3. Na liście **Remote address type (Typ adresu zdalnego**) wybierz **ścieżkę IP** **lub Application file path (Ścieżka pliku aplikacji).**
   4. W **polu Wartość** określ odpowiednią wartość. W zależności od opcji wybranej w kroku 6c możesz określić adres IP, zakres adresów IP lub ścieżkę do pliku aplikacji. (Zobacz [Ustawienia zapory](mdb-firewall.md)).
   5. Ustaw **dla ustawienia Włącz** **regułę wartość Wł** ., aby uaktywnić regułę. Aby wyłączyć regułę, ustaw dla ustawienia przełącznika wartość **Wyłączone**.
   6. W **wysuwanych oknie edytowanie** reguły wybierz **pozycję Aktualizuj regułę**. 

7. Na **ekranie Ustawienia konfiguracji** wybierz pozycję **Dalej**.

8. Na **ekranie Przeglądanie zasad** przejrzyj zmiany wprowadzone w ustawieniach zasad zapory. Wprowadzić wszelkie potrzebne zmiany, a następnie wybierz **pozycję Utwórz zasady**.

## <a name="delete-a-custom-rule"></a>Usuwanie reguły niestandardowej

1. Przejdź do Microsoft 365 Defender konta ([https://security.microsoft.com](https://security.microsoft.com)) i zaloguj się.

2. Przejdź do **endpointsDevice** >  configuration i przejrzyj listę zasad.

3. W sekcji **Zapora** wybierz istniejące zasady lub dodaj nowe zasady.

4. W **obszarze Reguły** niestandardowe przejrzyj listę reguł.

5. Zaznacz regułę, a następnie wybierz pozycję **Usuń**. Zostanie otwarte wysunięcie tego menu.

6. Na ekranie potwierdzenia wybierz pozycję **Usuń**. 

## <a name="next-steps"></a>Następne kroki

- [Wyświetlanie zdarzeń i zarządzanie nimi w programie Microsoft Defender dla firm](mdb-view-manage-incidents.md)

- [Reagowanie na zagrożenia i ograniczanie ich w programie Microsoft Defender dla firm](mdb-respond-mitigate-threats.md)

- [Przeglądanie działań naprawczych w Centrum akcji](mdb-review-remediation-actions.md)