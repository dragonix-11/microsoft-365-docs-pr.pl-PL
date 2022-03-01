---
title: Informacje dotyczące ustawień konfigurowalnych dla Microsoft Managed Desktop
description: Ustawianie kategorii dla ustawień konfigurowalnych w programie Microsoft Managed Desktop
keywords: Microsoft Managed Desktop, Microsoft 365, usługa, dokumentacja
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
ms.openlocfilehash: 07220c7a1b5e44eecdae247387a95ea6dfd445f1
ms.sourcegitcommit: 2c3b737e71038f843ef9e9ff4d5b99d6110b8ec5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2022
ms.locfileid: "63009670"
---
# <a name="configurable-settings-reference---microsoft-managed-desktop"></a>Informacje dotyczące ustawień konfigurowalnych — Microsoft Managed Desktop

Ten artykuł zawiera listę kategorii ustawień, które klienci mogą konfigurować za pomocą Microsoft Managed Desktop. Każda kategoria ustawień zawiera informacje na temat wymagań, najlepszych rozwiązań i sposobu dostosowywania kategorii ustawień.

## <a name="desktop-background-picture"></a>Obraz tła pulpitu

Możesz dostosować obraz tła pulpitu dla Microsoft Managed Desktop urządzeniach w organizacji. Obraz tła pulpitu umożliwia zastosowanie marki firmy lub materiałów marketingowych.

### <a name="requirements"></a>Wymagania

Obraz tła pulpitu musi spełniać następujące wymagania:

- Format pliku obrazu: .jpg, jpeg lub .png
- Lokalizacja pliku: Hostuj w zaufanej bezpiecznej lokalizacji http (https).
- Niedozwolone: Lokalizacje Http i lokalizacje udziału plików (unc) nie są obsługiwane.

### <a name="customize-and-deploy-desktop-background-picture"></a>Dostosowywanie i wdrażanie obrazu tła pulpitu

**Aby dodać niestandardowy obraz tła pulpitu:**

1. Zaloguj się [w Microsoft Endpoint Manager](https://endpoint.microsoft.com/) i przejdź do menu **Urządzenia**.
2. W sekcji Microsoft Managed Desktop wybierz pozycję **Ustawienia**.
3. W obszarze **Ustawienia** wybierz pozycję **Obraz tła pulpitu**.
4. Wprowadź lokalizację obrazu, którego chcesz użyć.
5. Wybierz **pozycję Wdrożenie etapowe** , aby zapisać zmiany i wdrożyć je w grupie Test.

## <a name="browser-start-pages"></a>Strony startowe przeglądarki

Strony startowe przeglądarki są otwierane na poszczególnych kartach, gdy użytkownicy Microsoft Edge. Jeśli chcesz ułatwić użytkownikom otwieranie zestawu witryn, z których często korzystają, dodaj stronę startową przeglądarki dla każdej witryny.

### <a name="requirements"></a>Wymagania

Dla stron startowych przeglądarki należy podać w pełni kwalifikowaną nazwę domeny (FQDN) dla intranetowych lub internetowych witryn internetowych. Jeśli skonfigurowano witryny wewnętrzne, informuje użytkowników, że dostęp do nich jest dozwolony tylko w przypadku połączenia z siecią wewnętrzną lub połączenia przez sieć VPN.

### <a name="customize-and-deploy-browser-start-pages"></a>Dostosowywanie i wdrażanie stron startowych przeglądarki

**Aby dodać stronę startową przeglądarki:**

1. Zaloguj się [w Microsoft Endpoint Manager](https://endpoint.microsoft.com/) i przejdź do menu **Urządzenia**.
2. W sekcji Microsoft Managed Desktop wybierz pozycję **Ustawienia**.
3. W obszarze **Ustawienia** wybierz pozycję **Strony startowe przeglądarki**.
4. Wybierz **pozycję Dodaj stronę startową**.
5. Na **stronie startowej dodawania** przeglądarki wprowadź adres URL witryny, której chcesz użyć, a następnie wybierz pozycję **Dodaj stronę startową**.
6. Powtórz kroki od 1 do 5 dla, aby dodać więcej stron startowych przeglądarki.
7. Wybierz **pozycję Wdrożenie etapowe** , aby zapisać zmiany i wdrożyć je w grupie Test.

## <a name="enterprise-mode-site-list-location"></a>Enterprise lokalizacji listy witryn w trybie online

Jeśli masz określone witryny internetowe i aplikacje, które mają problemy ze zgodnością z programem Microsoft Edge, możesz użyć listy witryn w trybie Enterprise, aby automatycznie otwierać witryny internetowe w programie Internet Explorer 11. Ponadto, jeśli wiesz, że witryny intranetowe nie działają poprawnie Microsoft Edge, możesz skonfigurować automatyczne otwieranie wszystkich witryn intranetowych w programie Internet Explorer 11.

Korzystanie Enterprise oznacza, że nadal możesz używać programu Microsoft Edge jako domyślnej przeglądarki, a jednocześnie zagwarantować, że aplikacje będą nadal działać w programie Internet Explorer 11. Aby uzyskać więcej informacji na temat list witryn w trybie przedsiębiorstwa, zobacz Enterprise [Tryb Enterprise list witryn w trybie przedsiębiorstwa](/internet-explorer/ie11-deploy-guide/what-is-enterprise-mode).

Możesz określić lokalizację `https://` lub lokalizację udziału wewnętrznego, w którym hostowana jest lista witryn w trybie przedsiębiorstwa.

### <a name="requirements"></a>Wymagania

Plik listy witryn w trybie przedsiębiorstwa musi spełniać następujące wymagania:

- Format pliku: plik XML spełniający [wymagania dotyczące pliku](/internet-explorer/ie11-deploy-guide/what-is-enterprise-mode#site-list-xml-file).
- Lokalizacja pliku: Plik hosta w wewnętrznej lokalizacji HTTPS.
- Niedozwolone: Hosting we wewnętrznym udziału plików, na `//sharename`przykład , nie jest dozwolony.

### <a name="best-practices"></a>Najważniejsze wskazówki

Te najlepsze rozwiązania są oferowane, aby ułatwić klientom podejmowanie decyzji dotyczących unowocześnień swojej infrastruktury IT:

| Ćwiczenia | Opis |
| ------ | ------ |
| Wybieranie ograniczonej liczby witryn | Microsoft Managed Desktop używa Microsoft Edge jako preferowanej przeglądarki w celu zwiększenia ogólnego bezpieczeństwa organizacji i użyteczności dla użytkowników. Większość witryn na tej liście dotyczy starszych aplikacji sieci Web, które wymagają starszej wersji przeglądarki, która nie będzie zawierać tylu funkcji zabezpieczeń. |
| Rozważenie alternatywy | Rozważ inną witrynę lub aplikację sieci Web, która nie wymaga starszej przeglądarki. Rozważ też zaktualizowanie witryny, aby korzystać z nowych przeglądarek. Nowsze przeglądarki korzystają z najnowszych technologii i pomagają zwiększyć bezpieczeństwo. |

### <a name="customize-and-deploy-enterprise-site-mode-list-location"></a>Dostosowywanie i wdrażanie Enterprise lokalizacji listy w trybie witryny

**Aby dodać lokalizację listy w trybie witryny przedsiębiorstwa:**

1. Zaloguj się [w Microsoft Endpoint Manager](https://endpoint.microsoft.com/) i przejdź do menu **Urządzenia**.
2. W sekcji Microsoft Managed Desktop wybierz pozycję **Ustawienia**.
3. W obszarze **Ustawienia** wybierz **lokalizację Enterprise witryny w trybie online**.
4. Wprowadź lokalizację https dla listy witryn.
5. Wybierz **pozycję Wdrożenie etapowe** , aby zapisać zmiany i wdrożyć je w grupie Test.

## <a name="trusted-sites"></a>Zaufane witryny

Zaufane witryny umożliwiają dostosowywanie stref zabezpieczeń lub miejsc, w których można używać witryny dla różnych witryn. Strefy zabezpieczeń obejmują:

- Strefa 1: Strefa Lokalny intranet
- Strefa 2: Strefa Zaufane witryny
- Strefa 3: strefa internetowa
- Strefa 4. Strefa Witryny z ograniczeniami

### <a name="requirements"></a>Wymagania

Podaj w pełni kwalifikowaną nazwę domeny (FQDN) dla witryn intranetowych lub internetowych dla każdej zaufanej witryny.

### <a name="customize-and-deploy-trusted-sites"></a>Dostosowywanie i wdrażanie zaufanych witryn

**Aby dodać zaufaną witrynę:**

1. Zaloguj się [w Microsoft Endpoint Manager](https://endpoint.microsoft.com/) i przejdź do menu **Urządzenia**.
2. W sekcji Microsoft Managed Desktop wybierz pozycję **Ustawienia**.
3. W obszarze **Ustawienia** wybierz pozycję **Zaufane witryny**, a następnie wybierz pozycję **Dodaj zaufaną witrynę**.
4. W **polu Dodaj zaufaną** witrynę wprowadź adres URL, wybierz strefę zabezpieczeń, a następnie wybierz pozycję **Dodaj zaufaną witrynę**.
5. Powtórz kroki od 1 do 4 dla każdej zaufanej witryny, którą chcesz dodać.
6. Wybierz **pozycję Wdrożenie etapowe** , aby zapisać zmiany i wdrożyć je w grupie Test.

**Aby usunąć zaufaną witrynę:**

1. Zaloguj się [w Microsoft Endpoint Manager](https://endpoint.microsoft.com/) i przejdź do menu **Urządzenia**.
2. W sekcji Microsoft Managed Desktop wybierz pozycję **Ustawienia**.
3. W **Ustawienia** obszaru roboczego wybierz pozycję **Zaufane witryny**.
4. Wybierz witrynę, którą chcesz usunąć, a następnie wybierz pozycję **Usuń**.
5. Powtórz kroki od 1 do 4 dla każdej zaufanej witryny, którą chcesz usunąć.
6. Wybierz **pozycję Wdrożenie etapowe** , aby zapisać zmiany i wdrożyć je w grupie Test.

## <a name="proxy"></a>Serwer proxy

Możesz zarządzać ustawieniami sieciowego serwera proxy dla swojej organizacji. Dodaj serwer proxy i numer portu, a następnie dodaj wyjątki witryny serwera proxy.

Microsoft Managed Desktop zawiera zestaw domyślnych wyjątków serwera proxy wymaganych do obsługi usługi. Domyślna lista wykluczeń może zostać zmodyfikowana tylko przez Microsoft Managed Desktop usługi. Aby uzyskać więcej informacji, [zobacz Konfiguracja sieci dla Microsoft Managed Desktop](../get-ready/network.md).

Wyjątki witryny serwera proxy dodane w portalu Microsoft Managed Desktop są dodawane do domyślnych wyjątków serwera proxy uwzględnionych w Microsoft Managed Desktop serwera proxy.

> [!NOTE]
> W przypadku aktualizacji domyślnej listy wyjątków serwera proxy priorytetyzuje się w porównaniu z wdrożeniami klientów. Oznacza to, że wdrożenie etapowe zostanie wstrzymane, jeśli istnieje wdrożenie domyślnej listy wyjątków serwera proxy.  

### <a name="requirements"></a>Wymagania

W przypadku wyjątków dla serwera proxy i witryny proxy muszą być spełnione następujące wymagania:

- Musi to być prawidłowy adres serwera i numer portu.
- Adresy URL muszą być prawidłową witryną http.

### <a name="customize-and-deploy-proxies"></a>Dostosowywanie i wdrażanie serwerów proxy

**Aby dodać wyjątek indywidualnej witryny proxy:**

1. Zaloguj się [w Microsoft Endpoint Manager](https://endpoint.microsoft.com/) i przejdź do menu **Urządzenia**.
2. W sekcji Microsoft Managed Desktop wybierz pozycję **Ustawienia**.
3. W obszarze **Ustawienia** wybierz pozycję **Serwer proxy**.
4. Wprowadź adres **i** **numer portu serwera** proxy, a następnie wybierz pozycję **Dodaj wyjątek serwera proxy**.
5. Wprowadź adres URL prawidłowej witryny http, a następnie wybierz pozycję **Dodaj wyjątek serwera proxy**.
6. Powtórz kroki od 1 do 5 dla każdej zaufanej witryny, którą chcesz dodać.
7. Wybierz **pozycję Wdrożenie etapowe** , aby zapisać zmiany i wdrożyć je w grupie Test.

## <a name="additional-resources"></a>Dodatkowe materiały

- [Omówienie ustawień konfigurowalnych](config-setting-overview.md)
- [Wdrażanie ustawień konfigurowalnych](config-setting-deploy.md)
