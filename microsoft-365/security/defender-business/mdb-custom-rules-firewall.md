---
title: Zarządzanie regułami niestandardowymi zasad zapory w Microsoft Defender dla Firm
description: Reguły niestandardowe zapewniają wyjątki od zasad zapory. Reguły niestandardowe umożliwiają blokowanie lub zezwalanie na określone połączenia w usłudze Defender dla firm.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: acc183abcbae89cd952011cfc637161bb409a95f
ms.sourcegitcommit: f30616b90b382409f53a056b7a6c8be078e6866f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2022
ms.locfileid: "65174513"
---
# <a name="manage-your-custom-rules-for-firewall-policies-in-microsoft-defender-for-business"></a>Zarządzanie niestandardowymi regułami zasad zapory w Microsoft Defender dla Firm

Microsoft Defender dla Firm obejmuje zasady zapory, które pomagają chronić urządzenia przed niepożądanym ruchem sieciowym. Reguły niestandardowe umożliwiają definiowanie wyjątków dla zasad zapory. Oznacza to, że można użyć reguł niestandardowych do blokowania lub zezwalania na określone połączenia.

Aby dowiedzieć się więcej na temat zasad i ustawień zapory, zobacz [Zapora w Microsoft Defender dla Firm](mdb-firewall.md).

**W tym artykule opisano sposób wykonywania następujących czynności**:

- [Tworzenie reguły niestandardowej dla zasad zapory](#create-a-custom-rule-for-a-firewall-policy)
- [Edytowanie reguły niestandardowej dla zasad zapory](#edit-a-custom-rule-for-a-firewall-policy)
- [Usuwanie reguły niestandardowej](#delete-a-custom-rule)

>
> **Masz minutę?**
> Weź udział w <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">krótkiej ankiecie dotyczącej bezpieczeństwa</a>. Chcielibyśmy usłyszeć od Ciebie!
>

## <a name="create-a-custom-rule-for-a-firewall-policy"></a>Tworzenie reguły niestandardowej dla zasad zapory

1. Przejdź do portalu Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) i zaloguj się.

2. Przejdź do **pozycji Punkty końcoweKonfiguracja** >  **urządzenia** i przejrzyj listę zasad.

3. W sekcji **Zapora** wybierz istniejące zasady lub dodaj nowe zasady.

4. W kroku **Ustawienia konfiguracji** przejrzyj ustawienia. Wprowadź wszelkie wymagane zmiany w **sieci domeny**, **sieci publicznej** i **sieci prywatnej**.

5. Aby utworzyć regułę niestandardową, wykonaj następujące kroki: 

   1. W obszarze **Reguły niestandardowe** wybierz pozycję **+ Dodaj regułę**. (Możesz mieć maksymalnie 150 reguł niestandardowych).
   2. W menu wysuwnym **Tworzenie nowej reguły** określ nazwę i opis reguły.
   3. Wybierz profil. (Dostępne opcje obejmują **sieć domeny**, **sieć publiczna** lub **sieć prywatna**).
   4. Na liście **Typ adresu zdalnego** wybierz **ścieżkę pliku** **ip** lub aplikacji.
   5. W polu **Wartość** określ odpowiednią wartość. W zależności od tego, co wybrano w kroku 6d, możesz określić adres IP, zakres adresów IP lub ścieżkę pliku aplikacji. (Zobacz [Ustawienia zapory](mdb-firewall.md)).
   6. W menu wysuwowym **Tworzenie nowej reguły** wybierz pozycję **Utwórz regułę**. 

6. Na ekranie **Ustawienia konfiguracji** wybierz pozycję **Dalej**.

7. Na ekranie **Przeglądanie zasad przejrzyj** zmiany wprowadzone w ustawieniach zasad zapory. Wprowadź wszelkie wymagane zmiany, a następnie wybierz pozycję **Utwórz zasady**.

## <a name="edit-a-custom-rule-for-a-firewall-policy"></a>Edytowanie reguły niestandardowej dla zasad zapory

1. Przejdź do portalu Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) i zaloguj się.

2. Przejdź do **pozycji Punkty końcoweKonfiguracja** >  **urządzenia** i przejrzyj listę zasad.

3. W sekcji **Zapora** wybierz istniejące zasady lub dodaj nowe zasady.

4. W obszarze **Reguły niestandardowe** przejrzyj listę reguł.

5. Wybierz regułę, a następnie wybierz pozycję **Edytuj**. Zostanie otwarte okno wysuwane.

6. Aby edytować regułę niestandardową, wykonaj następujące kroki:

   1. Na wysuwanej **edytuj regułę** przejrzyj i edytuj nazwę i opis reguły.
   2. Przejrzyj i w razie potrzeby edytuj profil reguły. (Dostępne opcje obejmują **sieć domeny**, **sieć publiczna** lub **sieć prywatna**).
   3. Na liście **Typ adresu zdalnego** wybierz **ścieżkę pliku** **ip** lub aplikacji.
   4. W polu **Wartość** określ odpowiednią wartość. W zależności od wybranego kroku 6c możesz określić adres IP, zakres adresów IP lub ścieżkę pliku aplikacji. (Zobacz [Ustawienia zapory](mdb-firewall.md)).
   5. Ustaw **opcję Włącz regułę** **na Włączone** , aby uaktywnić regułę. Lub, aby wyłączyć regułę, ustaw przełącznik na **Wył**.
   6. W wysuwanej **edytuj regułę** wybierz pozycję **Aktualizuj regułę**. 

7. Na ekranie **Ustawienia konfiguracji** wybierz pozycję **Dalej**.

8. Na ekranie **Przeglądanie zasad przejrzyj** zmiany wprowadzone w ustawieniach zasad zapory. Wprowadź wszelkie wymagane zmiany, a następnie wybierz pozycję **Utwórz zasady**.

## <a name="delete-a-custom-rule"></a>Usuwanie reguły niestandardowej

1. Przejdź do portalu Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) i zaloguj się.

2. Przejdź do **pozycji Punkty końcoweKonfiguracja** >  **urządzenia** i przejrzyj listę zasad.

3. W sekcji **Zapora** wybierz istniejące zasady lub dodaj nowe zasady.

4. W obszarze **Reguły niestandardowe** przejrzyj listę reguł.

5. Wybierz regułę, a następnie wybierz pozycję **Usuń**. Zostanie otwarte okno wysuwane.

6. Na ekranie potwierdzenia wybierz pozycję **Usuń**. 

## <a name="next-steps"></a>Następne kroki

- [Wyświetlanie zdarzeń i zarządzanie nimi w Microsoft Defender dla Firm](mdb-view-manage-incidents.md)
- [Reagowanie na zagrożenia w Microsoft Defender dla Firm i eliminowanie ich](mdb-respond-mitigate-threats.md)
- [Przeglądanie akcji korygowania w centrum akcji](mdb-review-remediation-actions.md)