---
title: Zarządzanie zezwoleniami na liście dozwolonych/zablokowanych dzierżaw
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
description: Administratorzy mogą dowiedzieć się, jak skonfigurować zezwolenia na liście dozwolonych/zablokowanych dzierżaw w portalu zabezpieczeń.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: ad2a55d19f60bf310b62ac13dfbe2563709673d2
ms.sourcegitcommit: 45bc65972d4007b2aa7760d4457a0d2699f81926
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2022
ms.locfileid: "64970940"
---
# <a name="add-allows-in-the-tenant-allowblock-list"></a>Dodawanie zezwoleń na liście dozwolonych/zablokowanych dzierżaw

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Usługi Microsoft Defender dla usługi Office 365 (plan 1 i plan 2)](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Administratorzy nie mogą dodawać opcji zezwala bezpośrednio na listę dozwolonych/zablokowanych dzierżaw. Zamiast tego należy użyć procesu przesyłania przez administratora, aby przesłać zablokowany komunikat, aby odpowiedni adres URL, plik i/lub nadawcy zostali dodani do listy dozwolonych/zablokowanych dzierżaw. Jeśli blok pliku, adresu URL lub nadawcy nie został utworzony, zezwalanie nie zostanie utworzone. W większości przypadków, gdy komunikat został uznany za fałszywie dodatni, który został niepoprawnie zablokowany, zezwala są przechowywane tak długo, jak to konieczne, aby dać systemowi czas, aby umożliwić im naturalnie.

> [!IMPORTANT]
> Ponieważ firma Microsoft zarządza zezwala dla Ciebie, nadawca, adres URL lub plik zezwala, które nie są potrzebne lub uważane za złe zostaną usunięte. Ma to na celu ochronę środowiska i zapobieganie błędnej konfiguracji opcji zezwalania. W przypadkach, w których użytkownik może się nie zgadzać, może być potrzebna pomoc techniczna, aby ustalić, dlaczego komunikat jest nadal uważany za zły.

## <a name="add-sender-allows-using-the-submissions-portal"></a>Dodawanie nadawcy umożliwia korzystanie z portalu Przesyłania

Zezwalaj nadawcom (lub domenom) na stronie **Przesyłanie** w Microsoft 365 Defender.

1. W portalu Microsoft 365 Defender pod adresem <https://security.microsoft.com>przejdź do obszaru **Akcje & przesłania**\>. Aby przejść bezpośrednio do strony **Przesłane** , użyj polecenia <https://security.microsoft.com/reportsubmission>.

2. Na stronie **Przesłane** sprawdź, czy wybrano kartę **Wiadomości e-mail** , a następnie kliknij ikonę ![Prześlij do firmy Microsoft w celu analizy.](../../media/m365-cc-sc-create-icon.png) **Prześlij do firmy Microsoft w celu analizy**.

3. Użyj wysuwanego **okienka Prześlij do firmy Microsoft** , aby przejrzeć komunikat, dodając identyfikator komunikatu sieciowego lub przekazując plik e-mail.

4. W sekcji **Wybierz przyczynę przesłania do firmy Microsoft** wybierz pozycję **Nie powinno być blokowane (fałszywie dodatnie).**

5. Włącz opcję **Zezwalaj na komunikaty, takie jak ta** .

6. Z listy rozwijanej **Usuń po** określ, jak długo ma działać opcja zezwalania.

7. Po zakończeniu kliknij przycisk **Prześlij** .

> ![Prześlij złośliwe oprogramowanie do firmy Microsoft w celu analizy przykładu.](../../media/admin-submission-allow-messages.png)

## <a name="add-url-allows-using-the-submissions-portal"></a>Dodawanie adresu URL umożliwia korzystanie z portalu Przesyłania

Zezwalaj na adresy URL na stronie **Przesyłanie** w Microsoft 365 Defender.

1. W portalu Microsoft 365 Defender pod adresem <https://security.microsoft.com>przejdź do obszaru **Akcje & przesłania**\>. Aby przejść bezpośrednio do strony **Przesłane** , użyj polecenia <https://security.microsoft.com/reportsubmission>.

2. Na stronie **Przesyłanie** wybierz kartę **Adresy URL** , a następnie kliknij ikonę ![Prześlij do firmy Microsoft w celu analizy.](../../media/m365-cc-sc-create-icon.png) **Prześlij do firmy Microsoft w celu analizy**.

3. Użyj wysuwanego **okienka Prześlij do firmy Microsoft,** aby przejrzeć komunikat, dodając adres URL.

4. W sekcji **Wybierz przyczynę przesłania do firmy Microsoft** wybierz pozycję **Nie powinno być blokowane (fałszywie dodatnie).**

5. Włącz opcję **Zezwalaj na adresy URL podobne do tej** .

6. Z listy rozwijanej **Usuń po** określ, jak długo ma działać opcja zezwalania.

7. Po zakończeniu kliknij przycisk **Prześlij** .

> [!div class="mx-imgBorder"]
> ![Prześlij adres URL do analizy.](../../media/submit-url-for-analysis.png)

## <a name="add-file-allows-using-the-submissions-portal"></a>Opcja Dodaj plik umożliwia korzystanie z portalu Przesyłania

Zezwalaj na pliki na stronie **Przesyłanie** w Microsoft 365 Defender.

1. W portalu Microsoft 365 Defender pod adresem <https://security.microsoft.com>przejdź do obszaru **Akcje & przesłania**\>. Aby przejść bezpośrednio do strony **Przesłane** , użyj polecenia <https://security.microsoft.com/reportsubmission>.

2. Na stronie **Przesłane** wybierz kartę **Załączniki wiadomości e-mail** , a następnie kliknij ikonę ![Prześlij do firmy Microsoft w celu analizy.](../../media/m365-cc-sc-create-icon.png) **Prześlij do firmy Microsoft w celu analizy**.

3. Użyj wysuwanego **okienka Prześlij do firmy Microsoft** , aby przejrzeć komunikat, dodając plik lub pliki.

4. W sekcji **Wybierz przyczynę przesłania do firmy Microsoft** wybierz pozycję **Nie powinno być blokowane (fałszywie dodatnie).**

5. Włącz opcję **Zezwalaj na pliki podobne do tej** .

6. Z listy rozwijanej **Usuń po** określ, jak długo ma działać opcja zezwalania.

7. Po zakończeniu kliknij przycisk **Prześlij** .

> [!div class="mx-imgBorder"]
> ![Prześlij wiadomość e-mail do analizy.](../../media/submit-email-for-analysis.png)

## <a name="create-spoofed-sender-allow-entries-using-microsoft-365-defender"></a>Tworzenie sfałszowanego nadawcy zezwala na wpisy przy użyciu Microsoft 365 Defender

> [!NOTE]
>
> - Tylko _kombinacja_ sfałszowanego użytkownika _i_ infrastruktury wysyłania zdefiniowanej w parze domeny jest wyraźnie dozwolona lub zablokowana przed fałszowaniem.
> - Podczas konfigurowania wpisu zezwalania lub blokowania dla pary domeny komunikaty z tej pary domeny nie są już wyświetlane w szczegółowych informacjach analizy na temat fałszowania.
> - Wpisy dla sfałszowanych nadawców nigdy nie wygasają.
> - Spoof obsługuje zarówno zezwalanie, jak i blokowanie. Adres URL obsługuje tylko opcję zezwalania.

1. W portalu Microsoft 365 Defender pod adresem <https://security.microsoft.com>przejdź do obszaru Zasady **współpracy** \> & poczty e-mail **& reguły** \> **Zasad** \> zagrożeń **Zezwalaj/Blokuj listy** dzierżawy w sekcji **Reguły**. Możesz też przejść bezpośrednio do strony **Zezwalaj/blokuj listy dzierżawy** , użyj polecenia <https://security.microsoft.com/tenantAllowBlockList>.

2. Na stronie **Lista dozwolonych/blokowych dzierżawy** wybierz kartę **Fałszowanie** , a następnie kliknij pozycję Dodaj ikonę ![.](../../media/m365-cc-sc-create-icon.png) **Dodaj**.

3. W wyświetlonym menu wysuwowym **Dodawanie nowych par domeny** skonfiguruj następujące ustawienia:
   - **Dodaj nowe pary domen z symbolami wieloznacznymi**: wprowadź jedną parę domeny na wiersz, maksymalnie do 20. Aby uzyskać szczegółowe informacje na temat składni fałszywych wpisów nadawcy, zobacz [Zarządzanie listą dozwolonych/zablokowanych dzierżaw](tenant-allow-block-list.md).
   - **Typ fałszowania**: wybierz jedną z następujących wartości:
     - **Wewnętrzne**: sfałszowany nadawca znajduje się w domenie należącej do Organizacji ( [akceptowana domena](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains)).
     - **Zewnętrzne**: sfałszowany nadawca znajduje się w domenie zewnętrznej.
   - **Akcja**: wybierz pozycję **Zezwalaj** lub **Blokuj**.

4. Po zakończeniu kliknij przycisk **Dodaj**.

## <a name="add-spoofed-sender-allow-entries-using-powershell"></a>Dodawanie fałszywych wpisów zezwalania nadawcy przy użyciu programu PowerShell

Aby dodać sfałszowane wpisy nadawcy na liście dozwolonych/zablokowanych dzierżaw w [programie Exchange Online programu PowerShell](/exchange/connect-to-exchange-online-powershell), użyj następującej składni:

```powershell
New-TenantAllowBlockListSpoofItems -SpoofedUser <Domain | EmailAddress | *> -SendingInfrastructure <Domain | IPAddress/24> -SpoofType <External | Internal> -Action <Allow | Block>
```

Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz [New-TenantAllowBlockListSpoofItems](/powershell/module/exchange/new-tenantallowblocklistspoofitems).

## <a name="related-articles"></a>Artykuły pokrewne

- [Przesyłanie przez administratora](admin-submission.md)
- [Zgłaszanie wyników fałszywie dodatnich i fałszywie ujemnych](report-false-positives-and-false-negatives.md)
