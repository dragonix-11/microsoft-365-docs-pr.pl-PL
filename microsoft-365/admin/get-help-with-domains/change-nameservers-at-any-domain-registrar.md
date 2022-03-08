---
title: Zmienianie serwerów nazw w celu skonfigurowania Microsoft 365 rejestratora domen
f1.keywords:
- CSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
- Adm_O365_Setup
ms.custom:
- okr_smb
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
- GEU150
- GEA150
ms.assetid: a8b487a9-2a45-4581-9dc4-5d28a47010a2
description: Dowiedz się, jak dodać i skonfigurować domenę w Microsoft 365 tak, aby w Twoich usługach, takich jak poczta e-mail i Skype dla firm Online, korzystać z Twojej nazwy domeny.
ms.openlocfilehash: 2d591429d74e03eec883b524b8fa36d082cfab93
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63316971"
---
# <a name="change-nameservers-to-set-up-microsoft-365-with-any-domain-registrar"></a>Zmienianie serwerów nazw w celu skonfigurowania Microsoft 365 rejestratora domen

 **[Zajrzyj do często zadawanych pytań dotyczących domen](../setup/domains-faq.yml)**, jeśli nie możesz znaleźć szukanych informacji.

Wykonaj poniższe instrukcje, aby dodać i skonfigurować domenę w Microsoft 365 tak, aby Twoje usługi, takie jak poczta e-mail Teams, były używać Twojej nazwy domeny. W tym celu zweryfikuj domenę, a następnie zmień serwery nazw domeny na Microsoft 365 tak, aby można było skonfigurować poprawne rekordy DNS. Wykonaj poniższe czynności, jeśli następujące stwierdzenia opisują Twoją sytuację:

- Masz własną domenę i chcesz skonfigurować ją do współpracy z Microsoft 365.

- Chcesz, Microsoft 365 samodzielnie zarządzać rekordami DNS. (Jeśli wolisz, możesz wybrać [zarządzanie własnymi rekordami DNS](../setup/add-domain.md)).

## <a name="add-a-txt-or-mx-record-for-verification"></a>Dodawanie rekordu TXT lub MX w celu weryfikacji

> [!NOTE]
> Utworzysz tylko jeden z tych rekordów. Preferowanym typem rekordu jest TXT, ale niektórzy dostawcy hostingu DNS nie obsługują go. W takim wypadku możesz zamiast niego utworzyć rekord MX.

Zanim będziesz używać własnej domeny z Microsoft 365, musimy się upewnić, że jesteś jej właścicielem. Możliwość zalogowania się do swojego konta w witrynie rejestratora domen i utworzenia rekordu DNS udowadnia, Microsoft 365, że jesteś właścicielem domeny.

> [!NOTE]
> Ten rekord jest używany tylko do weryfikowania, że jesteś właścicielem domeny, i nie wywiera wpływu na nic innego. Jeśli chcesz, możesz go później usunąć.

### <a name="find-the-area-on-your-dns-hosting-providers-website-where-you-can-create-a-new-record"></a>Znajdowanie obszaru w witrynie sieci Web dostawcy hostingu DNS w sieci Web, w którym można utworzyć nowy rekord

1. Zaloguj się do witryny internetowej dostawcy hostingu DNS.

2. Wybierz domenę.

3. Znajdź stronę, na której można edytować rekordy DNS dla domeny.

### <a name="create-the-record"></a>Tworzenie rekordu

W zależności od tego, czy tworzysz rekord TXT, czy rekord MX, wykonaj jedną z następujących czynności:

**Jeśli tworzysz rekord TXT, użyj tych wartości:**

<br>

****

|Typ rekordu|Alias lub nazwa hosta|Value|Czas wygaśnięcia|
|---|---|---|---|
|TXT|Wykonaj jedną z następujących czynności: Wpisz znak **@** lub pozostaw to pole puste albo wpisz nazwę domeny.  <p> **Uwaga**: Różne hosty DNS mają różne wymagania dotyczące tego pola.|MS=ms *XXXXXXXX* <p> **Uwaga:** To jest przykład. Użyj tutaj swojej **konkretnej** wartości Miejsce docelowe lub punkt na adres z tabeli w Microsoft 365. [Jak to znaleźć?](../get-help-with-domains/information-for-dns-records.md)|Ustaw ten parametr na wartość **1 godzina** lub na równowartość w minutach ( **60** ), sekundach ( **3600** ) itp.|
|||||

**Jeśli tworzysz rekord MX, użyj tych wartości:**

<br>

****

|Typ rekordu|Alias lub nazwa hosta|Value|Priority (Priorytet)|TTL (Czas wygaśnięcia)|
|---|---|---|---|---|
|MX|Wpisz znak **@** lub nazwę domeny. |Ms=ms *XXXXXXXX* **Uwaga:** to jest przykład. Użyj tutaj swojej **konkretnej** wartości Miejsce docelowe lub punkt na adres z tabeli w Microsoft 365. [Jak to znaleźć?](../get-help-with-domains/information-for-dns-records.md)|W **przypadku rekordu Priority** (Priorytet) w celu uniknięcia konfliktów z rekordem MX używanym na poziomie przepływu poczty e-mail użyj priorytetu niższego niż priorytet dla wszystkich istniejących rekordów MX. Aby uzyskać więcej informacji o priorytetach, zobacz [Co to jest priorytet rekordu MX?](../setup/domains-faq.yml)|Ustaw ten parametr na wartość **1 godzina** lub na równowartość w minutach ( **60** ), sekundach ( **3600** ) itp.|
||||||

### <a name="save-the-record"></a>Zapisywanie rekordu

Po dodaniu rekordu w witrynie rejestratora domen wrócisz do usługi Microsoft 365 i zażądasz, aby Microsoft 365 go szukać.

Po Microsoft 365 poprawnego rekordu TXT domena zostanie zweryfikowana.

1. W Centrum administracyjnym przejdź do strony **Ustawienia** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">Domeny</a>.

2. Na **stronie Domeny** wybierz weryfikowaną domenę.

3. Na stronie **Konfiguracja** wybierz pozycję **Rozpocznij konfigurowanie**.

4. Na stronie **Weryfikowanie domeny** wybierz pozycję **Weryfikuj**.

> [!NOTE]
> Wprowadzenie zmian w systemie DNS trwa zwykle około 15 minut. Jednak czasem aktualizacja internetowego systemu DNS może potrwać dłużej. Jeśli po dodaniu rekordów DNS występują problemy z przepływem poczty e-mail lub inne, zobacz [Rozwiązywanie problemów po zmianie nazwy domeny lub rekordów DNS](../get-help-with-domains/find-and-fix-issues.md).

## <a name="change-your-domains-nameserver-ns-records"></a>Zmienianie rekordów serwerów nazw domeny (SN)

W ostatnim kroku kreatora konfiguracji domen w programie Microsoft 365 pozostaje jedno zadanie do wykonania. Aby skonfigurować domenę przy użyciu usług Microsoft 365, takich jak poczta e-mail, zmień rekordy serwera nazw (NS) domeny u rejestratora domen, tak aby wskazują podstawowe i pomocnicze serwery nazw usługi Microsoft 365. Następnie, ponieważ Microsoft 365 hostuje Twój system DNS, wymagane rekordy DNS dla Twoich usług są automatycznie ustawiane. Rekordy serwera nazw można zaktualizować samodzielnie, wykonując kroki podawane przez rejestratora domen w zawartości pomocy w jego witrynie sieci Web. Jeśli nie masz wiedzy na temat systemu DNS, skontaktuj się z zespołem pomocy technicznej u rejestratora domen.

::: moniker range="o365-worldwide"

Aby samodzielnie zmienić serwery nazw domeny w witrynie internetowej rejestratora domen, wykonaj następujące kroki:

1. Znajdź obszar w witrynie internetowej rejestratora domen, w którym możesz zmienić serwery nazw domeny lub obszar, w którym można używać niestandardowych serwerów nazw.

2. Utwórz rekordy serwera nazw lub edytuj istniejące rekordy serwera nazw, aby dopasować je do następujących wartości:

    - Pierwszy serwer nazw: ns1.bdm.microsoftonline.com
    - Drugi serwer nazw: ns2.bdm.microsoftonline.com
    - Trzeci serwer nazw: ns3.bdm.microsoftonline.com
    - Czwarty serwer nazw: ns4.bdm.microsoftonline.com

   > [!TIP]
   > Najlepiej dodać wszystkie cztery rekordy, ale jeśli rejestrator obsługuje tylko dwa rekordy, dodaj rekordy **ns1.bdm.microsoftonline.com i** **ns2.bdm.microsoftonline.com**.

3. Zapisz zmiany.

> [!CAUTION]
> Zmiana rekordów serwera nazw domeny na takie, które wskazują Microsoft 365 nazw, wpływa na wszystkie usługi obecnie skojarzone z Twoją domeną. Jeśli pominięto jakiekolwiek kroki kreatora, na przykład dodawanie adresów e-mail, lub domena jest używana do obsługi blogów, koszyków albo innych usług, wymagane jest wykonanie dodatkowych czynności. W przeciwnym razie ta zmiana może spowodować przerwy w świadczeniu usług, na przykład utratę dostępu do poczty e-mail lub niedostępność bieżącej witryny internetowej.

::: moniker-end

::: moniker range="o365-21vianet"

1. Znajdź obszar w witrynie internetowej rejestratora domen, w którym można edytować serwery nazw dla Twojej domeny.

2. Utwórz dwa rekordy serwera nazw lub edytuj istniejące rekordy serwera nazw, aby odpowiadały następującym wartościom:

   - Pierwszy serwer nazw: ns1.dns.partner.microsoftonline.cn
   - Drugi serwer nazw: ns2.dns.partner.microsoftonline.cn

   > [!TIP]
   > Należy użyć co najmniej dwóch rekordów serwera nazw. Jeśli na liście znajdują się jakiekolwiek inne serwery nazw, możesz je usunąć lub zmienić na **ns3.dns.partner.microsoftonline.cn** i **ns4.dns.partner.microsoftonline.cn**.

3. Zapisz zmiany.

> [!CAUTION]
> Zmiana rekordów serwera nazw domeny na takie, które wskazują serwer Office 365 obsługiwany przez serwery nazw firmy 21Vianet, wpływa na wszystkie usługi obecnie skojarzone z Twoją domeną. Jeśli pominięto jakiekolwiek kroki kreatora, na przykład dodawanie adresów e-mail, lub domena jest używana do obsługi blogów, koszyków albo innych usług, wymagane jest wykonanie dodatkowych czynności. W przeciwnym razie ta zmiana może spowodować przerwy w świadczeniu usług, na przykład utratę dostępu do poczty e-mail lub niedostępność bieżącej witryny internetowej.

::: moniker-end

Oto niektóre dodatkowe kroki, które mogą być wymagane na przykład dla hostingu poczty e-mail i witryny internetowej:

- Przenieś wszystkie adresy e-mail, w których jest Microsoft 365, zanim zmienisz rekordy systemu nazw.

- Chcesz dodać domenę, która jest obecnie używana z adresem witryny internetowej, na przykład `https://www.fourthcoffee.com`? Podczas dodawania domeny możesz wykonać poniższe czynności, aby zachować swoją witrynę internetową w miejscu jej hostować teraz, dzięki czemu po zmianie rekordów serwera nazw domeny na takie, które wskazują adres Microsoft 365.

1. W Centrum administracyjnym przejdź do strony **Ustawienia** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">Domeny</a>.

2. Na stronie **Domeny** wybierz domenę.

3. Na stronie szczegółów domeny wybierz **kartę Rekordy DNS** .

4. Wybierz **pozycję Add record (Dodaj rekord**).

5. W **okienku Dodaj niestandardowy rekord DNS** z listy rozwijanej **Typ** wybierz pozycję **A (Adres)**.

6. W **polu Nazwa hosta lub Alias** wpisz **@**.

7. W polu **Adres IP** wpisz statyczny adres IP witryny internetowej, w której jest obecnie hostowana. Na przykład 172.16.140.1.

   > [!IMPORTANT]
   > Musi to być _statyczny_ adres IP witryny internetowej, a nie _dynamiczny_ adres IP. Aby upewnić się, że możesz uzyskać statyczny adres IP swojej publicznej witryny sieci Web, skontaktuj się z witryną host która hostuje Twoją witrynę sieci Web.

8. Jeśli chcesz zmienić ustawienie czasu wygaśnięcia dla rekordu, wybierz nowy czas z listy rozwijanej **TTL** (Czas wygaśnięcia). W przeciwnym razie przejdź do kroku 9.

9. Wybierz pozycję **Zapisz**.

Możesz też utworzyć rekord CNAME, aby ułatwić klientom odnalezienie Twojej witryny sieci Web.

1. Wybierz **pozycję Add record (Dodaj rekord**).
2. W **okienku Add a custom DNS record pane** (Dodawanie niestandardowego rekordu DNS) z listy rozwijanej **Type** (Typ) wybierz pozycję **CNAME (Alias).**
3. W **polu Nazwa hosta lub Alias** wpisz **www**.
4. W **polu Points to address (** Wskazuje adres) wpisz w pełni kwalifikowaną nazwę domeny (FQDN) witryny sieci Web. Na przykład **contoso.5om**.
5. Jeśli chcesz zmienić ustawienie czasu wygaśnięcia dla rekordu, wybierz nowy czas z listy rozwijanej **TTL** (Czas wygaśnięcia). W przeciwnym razie przejdź do kroku 6.
6. Wybierz **Zapisz**.

Po zaktualizowaniu rekordów serwera nazw, tak aby wskazują firmę Microsoft, konfiguracja domeny została ukończona. Poczta e-mail jest przekierowyowana do firmy Microsoft, a ruch na adres witryny sieci Web jest nadal przenoszony do bieżącego hosta witryny internetowej".

> [!NOTE]
> Aktualizowanie rekordu serwera nazw w internetowym systemie DNS może potrwać nawet kilka godzin. Wtedy poczta e-mail Firmy Microsoft i inne usługi będą ustawione do współpracy z Twoją domeną.

## <a name="related-content"></a>Zawartość pokrewna

[Dodawanie rekordów DNS w celu połączenia domeny](create-dns-records-at-any-dns-hosting-provider.md) (artykuł)\
[Znajdowanie i rozwiązywanie problemów po dodaniu domeny lub rekordów DNS](find-and-fix-issues.md) (artykuł)\
[Zarządzanie domenami](/admin) (strona linku)
