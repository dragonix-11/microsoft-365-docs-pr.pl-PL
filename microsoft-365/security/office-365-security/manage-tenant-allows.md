---
title: Zarządzaj swoimi zezwalaniami na liście zezwalania/blokowania dzierżawy
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: how-to
ms.localizationpriority: medium
search.appverid:
- MET150manage-tenant-allows.md
ms.collection:
- M365-security-compliance
description: Administratorzy mogą dowiedzieć się, jak skonfigurować zezwalają na to w portalu zabezpieczeń na liście zezwalania/blokowania dzierżawy.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 3823290e9f239b14e4bf97fe1ae8ef7020561697
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63314116"
---
# <a name="add-allows-in-the-tenant-allowblock-list"></a>Opcja Dodaj na liście zezwalania/blokowania dzierżawy

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender dla Office 365 plan 1 i plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Administratorzy nie mogą dodawać zezwalają bezpośrednio na listę zezwalania/blokowania dzierżawy. Zamiast tego możesz użyć procesu przesyłania administratora w celu przesłania wiadomości, która została zablokowana, dzięki czemu odpowiedni adres URL, plik i/lub nadawcy zostaną dodani do listy zezwalania/blokowania dzierżawy. Jeśli blok pliku, adresu URL lub nadawcy nie został zablokowany, nie zostanie utworzony zezwalanie. W większości przypadków, gdy wiadomość została określona jako fałszywie dodatnia, która została niepoprawnie zablokowana, zezwala się na to tak długo, jak jest to konieczne, aby zapewnić czas systemowy umożliwiający im naturalne zezwalanie.

> [!IMPORTANT]
> Firma Microsoft zarządza zezwalaniem na to, aby Ty, nadawca, adres URL lub plik zezwalał na to, że to, co nie jest potrzebne, lub uznane za złe, zostanie usunięte. Ma to na celu ochronę środowiska i zapobieganie błędnej konfiguracji zezwalania. W przypadkach, w których możesz się nie zgodzić, być może potrzebujesz spraw pomocy technicznej, aby ustalić, dlaczego wiadomość jest nadal uznawana za złą.

## <a name="add-sender-allows-using-the-submissions-portal"></a>Opcja Dodaj nadawcę umożliwia korzystanie z portalu Materiały 

Zezwalaj nadawcom (lub domenom) na stronie **Przesyłanie** w Microsoft 365 Defender. 

1. W portalu Microsoft 365 Defender podpowiem <https://security.microsoft.com>przejdź do **akcji i & przesyłania**\>. Aby przejść bezpośrednio do strony **Materiały**, użyj .<https://security.microsoft.com/reportsubmission>

2. Na stronie **Materiały sprawdź**, czy jest zaznaczona  karta Wiadomości e-mail, a następnie kliknij ikonę ![Prześlij do firmy Microsoft do analizy.](../../media/m365-cc-sc-create-icon.png) **Prześlij do firmy Microsoft w celu analizy**.

3. Aby **przejrzeć wysuwną wiadomość,** użyj wysuwu Prześlij do firmy Microsoft, aby przesłać wiadomość przez dodanie identyfikatora wiadomości sieciowej lub przekazanie pliku wiadomości e-mail. 

4. W sekcji **Wybierz przyczynę przesyłania do firmy Microsoft** wybierz pozycję Nie **powinno być blokowane (wynik fałszywie dodatni)**. 

5. Włącz opcję **Zezwalaj na wiadomości podobne do tej** . 

6. Z **listy rozwijanej** Usuń po określ, jak długo ma działać opcja zezwalania.

7. Po zakończeniu kliknij przycisk **Prześlij** .

> [!div class="mx-imgBorder"]
> ![Prześlij złośliwe oprogramowanie do firmy Microsoft na przykład do analizy.](../../media/admin-submission-allow-messages.png)

## <a name="add-url-allows-using-the-submissions-portal"></a>Dodawanie adresu URL umożliwia korzystanie z portalu Materiały

Zezwalaj na adresy URL na **stronie Przesyłanie** w Microsoft 365 Defender.

1. W portalu Microsoft 365 Defender podpowiem <https://security.microsoft.com>przejdź do **akcji i & przesyłania**\>. Aby przejść bezpośrednio do strony **Materiały**, użyj .<https://security.microsoft.com/reportsubmission>

2. Na stronie **Przesyłanie** wybierz kartę Adresy **URL** , a następnie kliknij ikonę ![Prześlij do firmy Microsoft do analizy.](../../media/m365-cc-sc-create-icon.png) **Prześlij do firmy Microsoft w celu analizy**.

3. Aby **wysłać wiadomość,** dodaj adres URL, korzystając z wysuwanych informacji Prześlij do firmy Microsoft w celu przejrzenia.

4. W sekcji **Wybierz przyczynę przesyłania do firmy Microsoft** wybierz pozycję Nie **powinno być blokowane (wynik fałszywie dodatni)**.

5. Włącz tę **opcję Zezwalaj na adresy URL** .

6. Z **listy rozwijanej** Usuń po określ, przez jaki czas ma działać opcja zezwalania.

7. Po zakończeniu kliknij przycisk **Prześlij** .

> [!div class="mx-imgBorder"]
> ![Prześlij adres URL do analizy.](../../media/submit-url-for-analysis.png)

## <a name="add-file-allows-using-the-submissions-portal"></a>Opcja Dodaj plik umożliwia korzystanie z portalu Materiały

Zezwalaj na pliki **na stronie Przesyłanie** w Microsoft 365 Defender.

W portalu Microsoft 365 Defender podpowiem <https://security.microsoft.com>przejdź do **akcji i & przesyłania**\>. Aby przejść bezpośrednio do strony **Materiały**, użyj .<https://security.microsoft.com/reportsubmission>

2. Na stronie **Przesyłanie wybierz** kartę Załączniki wiadomości **e-mail** , a następnie kliknij ikonę ![Prześlij do firmy Microsoft do analizy.](../../media/m365-cc-sc-create-icon.png) **Prześlij do firmy Microsoft w celu analizy**.

3. Aby **przesłać wiadomość, użyj** wysuwanych informacji Prześlij do firmy Microsoft w celu przejrzenia, aby przesłać wiadomość przez dodanie plików.

4. W sekcji **Wybierz przyczynę przesyłania do firmy Microsoft** wybierz pozycję Nie **powinno być blokowane (wynik fałszywie dodatni)**.

5. Włącz opcję **Zezwalaj na pliki podobne do tej** .

6. Z **listy rozwijanej** Usuń po określ, przez jaki czas ma działać opcja zezwalania.

7. Po zakończeniu kliknij przycisk **Prześlij** .

> [!div class="mx-imgBorder"]
> ![Prześlij wiadomość e-mail do analizy.](../../media/submit-email-for-analysis.png)


## <a name="create-spoofed-sender-allow-entries-using-microsoft-365-defender"></a>Tworzenie fałszywych nadawców zezwala na wpisy przy użyciu Microsoft 365 Defender

> [!NOTE]
> 
> - _Fałszowanie_ jest dozwolone lub blokowane  tylko przez połączenie sfałszowanej infrastruktury nadawczej i użytkownika zdefiniowanego w parach domen.
> - Po skonfigurowaniu wpisu zezwalania lub blokowania dla pary domen wiadomości z tej pary domen nie będą już wyświetlane w szczegółowych informacjach o analizie fałszowania.
> - Wpisy sfałszowanych nadawców nigdy nie wygasają.
> - Fałsz obsługuje zarówno zezwalanie, jak i blokowanie. Adres URL obsługuje tylko zezwalanie.

1. W portalu Microsoft 365 Defender <https://security.microsoft.com>pod adresem przejdź  \>  \>  \> do sekcji & e-mail i zasad & zasady zagrożeń dla **dzierżawy zezwalają** **na** listy/listy zablokowanych. Aby przejść bezpośrednio do strony Listy **zezwalań/** zablokowanych dzierżaw, użyj .<https://security.microsoft.com/tenantAllowBlockList>

2. Na stronie **Lista zezwalania/blokowania dzierżawy** wybierz kartę **Fałszowanie** , a następnie kliknij pozycję ![Dodaj.](../../media/m365-cc-sc-create-icon.png) **Dodaj**.

3. W **wyświetlonym wysuwam menu Add new domain pairs** (Dodaj nowe pary domen) skonfiguruj następujące ustawienia:
   - **Dodaj nowe pary domen z symbolami wieloznacznymi**: Wprowadź jedną parę domen w wierszu (maksymalnie 20). Aby uzyskać szczegółowe informacje na temat składni fałszywych wpisów nadawców, zobacz [Zarządzanie listą zezwalania/blokowania dzierżawy](tenant-allow-block-list.md).
   - **Fałsz typ**: Wybierz jedną z następujących wartości:
     - **Wewnętrzny**: sfałszowany nadawca należy do Twojej organizacji ( [zaakceptowana domena](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains)).
     - **Zewnętrzne**: sfałszowany nadawca znajduje się w domenie zewnętrznej.
   - **Akcja**: Wybierz pozycję **Zezwalaj** lub **Zablokuj**.

4. Po zakończeniu kliknij przycisk **Dodaj**.

## <a name="add-spoofed-sender-allow-entries-using-powershell"></a>Dodawanie fałszywych nadawców zezwala na wpisy przy użyciu programu PowerShell

Aby dodać sfałszowane wpisy nadawców na liście zezwalania/blokowania dzierżawy w [programie Exchange Online PowerShell](/exchange/connect-to-exchange-online-powershell), użyj następującej składni:

```powershell
New-TenantAllowBlockListSpoofItems -SpoofedUser <Domain | EmailAddress | *> -SendingInfrastructure <Domain | IPAddress/24> -SpoofType <External | Internal> -Action <Allow | Block>
```

Aby uzyskać szczegółowe informacje o składni i parametrach, [zobacz New-TenantAllowBlockListSpoofItems](/powershell/module/exchange/new-tenantallowblocklistspoofitems).

## <a name="related-articles"></a>Artykuły pokrewne

- [Zgłoszenia administratora](admin-submission.md)
- [Zgłaszanie wyników fałszywie dodatnich i ujemnych](report-false-positives-and-false-negatives.md)
