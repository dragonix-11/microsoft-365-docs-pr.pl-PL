---
title: Używanie zaufanych nadawców usługi ARC na potrzeby legalnych urządzeń i usług między nadawcą a odbiorcą
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
manager: dansimp
audience: ITPro
ms.topic: article
ms.localizationpriority: high
search.appverid:
- MET150
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
ms.custom:
- seo-marvel-apr2020
description: Uwierzytelniony łańcuch odebranych wiadomości e-mail (ARC) to uwierzytelnianie poczty e-mail, które próbuje zachować wyniki uwierzytelniania na różnych urządzeniach i w przypadku wszelkich pośrednich przepływów poczty przesyłanych między nadawcą a odbiorcą. Poniżej przedstawiono sposób tworzenia wyjątków dla zaufanych nadawców usługi ARC.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 625dd27ff59fca6a0e156bd65296e407e22005a6
ms.sourcegitcommit: 612ce4d15d8a2fdbf7795393b50af477d81b6139
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2022
ms.locfileid: "65663915"
---
# <a name="make-a-list-of-trusted-arc-senders-to-trust-legitimate-indirect-mailflows"></a>Tworzenie listy zaufanych nadawców usługi ARC w celu zaufania *legalnym* pośrednim przepływom poczty

**Dotyczy**

- Exchange Online Protection
- Usługi Microsoft Defender dla usługi Office 365 (plan 1 i plan 2)
- Microsoft 365 Defender

Mechanizmy uwierzytelniania poczty e-mail, takie jak [SPF](set-up-spf-in-office-365-to-help-prevent-spoofing.md), [DKIM](use-dkim-to-validate-outbound-email.md), [DMARC](use-dmarc-to-validate-email.md) , służą do weryfikowania nadawców wiadomości e-mail pod kątem *bezpieczeństwa* adresatów wiadomości e-mail, ale niektóre uzasadnione usługi mogą wprowadzać zmiany w wiadomości e-mail między nadawcą a odbiorcą. **W Microsoft 365 Defender usługa ARC pomoże ograniczyć błędy dostarczania SPF, DKIM i DMARC, które występują z powodu *legalnych* pośrednich przepływów poczty.**

## <a name="authenticated-received-chain-arc-for-legitimate-indirect-mailflows-in-microsoft-365-defender-for-office"></a>Uwierzytelniony łańcuch odebranych wiadomości (ARC) dla *legalnych* pośrednich przepływów poczty w Microsoft 365 Defender dla Office

Listy wysyłkowe i usługi, które filtrują lub przekazują wiadomości e-mail, są dobrze znaną i normalną funkcją przepływu poczty w organizacji. Jednak fowarding wiadomości e-mail narusza SPF. Usługi mogą również naruszać uwierzytelnianie poczty e-mail DKIM, zmieniając nagłówki wiadomości e-mail, dodając takie rzeczy jak informacje o skanowaniu wirusów lub usuwając załączniki. Niepowodzenie jednej z tych metod uwierzytelniania poczty e-mail może spowodować niepowodzenie przekazania DMARC.

Planowane interwencje przepływów pocztowych z legalnych usług są często *nazywane pośrednim przepływem poczty* i mogą *przypadkowo* powodować niepowodzenie uwierzytelniania poczty e-mail, gdy przechodzą przez (przeskok do) następnego urządzenia lub usługi w drodze do odbiorcy.

**Zaufane uszczelnienia ARC umożliwiają administratorom dodawanie listy *zaufanych* pośredników do portalu Microsoft 365 Defender.** Zaufane uszczelniacze ARC umożliwiają firmie Microsoft honorowanie podpisów ARC od zaufanych pośredników, uniemożliwiając tym legalnym komunikatom niepowodzenie łańcucha uwierzytelniania.

> [!NOTE]
> ***Zaufane uszczelniacze ARC to lista utworzona przez administratora dla każdej domeny, której procesy powodują pośredni przepływ poczty i które zaimplementowano uszczelnianie arc.*** Gdy wiadomość e-mail jest kierowana do Office 365 za pośrednictwem usługi ARC i zardzewiałego pośrednika dzierżawy Office 365, firma Microsoft weryfikuje podpis ARC i na podstawie wyników usługi ARC może uwzględniać podane szczegóły uwierzytelniania.

## <a name="when-to-use-trusted-arc-sealers"></a>Kiedy używać zaufanych uszczelniaczy ARC?

Lista zaufanych uszczelniaczy ARC jest wymagana tylko wtedy, gdy urządzenia i serwery interweniują w przepływie poczty e-mail organizacji i:

1. Może modyfikować nagłówek wiadomości e-mail lub inną zawartość wiadomości e-mail.
2. Może to spowodować niepowodzenie uwierzytelniania z innych powodów (na przykład przez usunięcie załączników).
 
Dodając zaufany uszczelniacz ARC, Office 365 będzie weryfikować i ufać wynikom uwierzytelniania dostarczanym przez uszczelniacz podczas dostarczania poczty do dzierżawy w Office 365.

**Administratorzy powinni dodawać *tylko uzasadnione usługi* jako zaufane uszczelniacze ARC.** Dodanie tylko usług, których organizacja wyraźnie używa i wie, pomoże komunikatom, które muszą najpierw przejść przez usługę, aby przekazać testy uwierzytelniania poczty e-mail i zapobiec wysyłaniu legalnych wiadomości do *wiadomości-śmieci* z powodu błędów uwierzytelniania.

## <a name="steps-to-add-a-trusted-arc-sealer-to-microsoft-365-defender"></a>Kroki dodawania zaufanego uszczelniacza ARC do Microsoft 365 Defender

Zaufane uszczelniacze ARC w portalu Microsoft 365 Defender wyświetlają wszystkie uszczelniacze ARC potwierdzone i dodane do dzierżawy.

**Aby dodać nowy uszczelniacz Trusted ARC w portalu administracyjnym:**

1. Przejdź do strony [ustawień uwierzytelniania poczty e-mail](https://security.microsoft.com/authentication?viewid=ARC) .

2. Jeśli po raz pierwszy dodano zaufany uszczelniacz ARC, kliknij przycisk Dodaj.
3. Dodaj zaufane uszczelnienia ARC w wyświetlonym polu tekstowym.
    1. Zwróć uwagę, że dodajesz domeny (na przykład fabrikam.com).
    1. Wprowadzona tutaj nazwa domeny *musi* być zgodna z domeną wyświetlaną w tagu domeny "d" w nagłówkach ARC-Seal i ARC-Message-Signature (w nagłówkach wiadomości e-mail wiadomości).
    1. Można je wyświetlić we właściwościach komunikatu w Outlook.

## <a name="steps-to-validate-your-trusted-arc-sealer"></a>Kroki sprawdzania poprawności zaufanego uszczelniacza ARC

Jeśli przed dotarciem wiadomości do Microsoft 365 Defender istnieje pieczęć ARC od innej firmy, **sprawdź nagłówki po odebraniu wiadomości e-mail i wyświetl najnowsze nagłówki usługi ARC**.

W ostatnim **nagłówku *ARC-Authentication-Results** _sprawdź, czy walidacja usługi ARC jest wyświetlana jako _*pass**.

Nagłówek ARC z listą "oda" 1 wskazuje, że poprzednia funkcja ARC została *zweryfikowana*, poprzedni uszczelniacz ARC jest *zaufany*, a poprzedni *wynik przebiegu* może służyć do zastąpienia bieżącego błędu DMARC.

**Nagłówek przekazywania ARC przedstawiający oda=1**

Zobacz metody uwierzytelniania poczty e-mail na końcu tego bloku nagłówka, aby uzyskać wynik oda.

``
ARC-Authentication-Results: i=2; mx.microsoft.com 1; spf=pass (sender ip is
40.107.65.78) smtp.rcpttodomain=microsoft.com
smtp.mailfrom=o365e5test083.onmicrosoft.com; dmarc=bestguesspass action=none
header.from=o365e5test083.onmicrosoft.com; dkim=none (message not signed);
arc=pass (0 oda=1 ltdi=1
spf=[1,1,smtp.mailfrom=o365e5test083.onmicrosoft.com]
dkim=[1,1,header.d=o365e5test083.onmicrosoft.com]
dmarc=[1,1,header.from=o365e5test083.onmicrosoft.com])
``

Aby sprawdzić, czy wynik ARC został użyty do zastąpienia błędu DMARC, poszukaj *wyniku kompauth* i *przyczyny kodu (130)* w nagłówku.

Zobacz ostatni wpis w tym bloku nagłówka, aby znaleźć *kompauth* i *przyczynę*.

``
Authentication-Results: spf=fail (sender IP is 51.163.158.241)
smtp.mailfrom=contoso.com; dkim=fail (body hash did not verify)
header.d=contoso.com;dmarc=fail action=none
header.from=contoso.com;compauth=pass reason=130
``

## <a name="powershell-steps-to-add-or-remove-a-trusted-arc-sealer"></a>Kroki programu PowerShell dotyczące dodawania lub usuwania zaufanego uszczelniacza ARC

**Administratorzy mogą również skonfigurować konfiguracje usługi ARC przy użyciu Exchange Online programu PowerShell.**

1. Połączenie Exchange w trybie online programu PowerShell.
2. Połączenie-ExchangeOnline.
3. Aby dodać lub zaktualizować domenę do zaufanego uszczelniacza ARC:
</br>
``
Set-ArcConfig -Identity default -ArcTrustedSealers {a list of arc signing domains split by comma}
``
</br>lub</br>
``
Set-ArcConfig -Identity {tenant name/tenanid}\default -ArcTrustedSealers {a list of arc signing domains split by comma}
``
</br>Podczas uruchamiania polecenia *Set-ArcConfig* należy podać parametr tożsamości *-Identity*. Zaufane uszczelniacze powinny być dopasowane do wartości tagu "d" w *nagłówku ARC-Seal*.

4. Wyświetl zaufane uszczelniacze ARC:
</br>
``
Get-ArcConfig
`` Lub ``
Get-ArcConfig - Organization {tenant name}
``

## <a name="trusted-arc-sealer-mailflow-graphics"></a>Zaufana grafika przepływu poczty uszczelniacza ARC

Te diagramy kontrastują operacje przepływu poczty z zaufanym uszczelniaczem ARC i bez niego podczas korzystania z uwierzytelniania poczty e-mail SPF, DKIM i DMARC. W obu grafikach istnieją uzasadnione usługi używane przez firmę, które muszą interweniować w przepływie poczty, czasami naruszając standardy uwierzytelniania poczty e-mail, zmieniając wysyłanie adresów IP i pisząc do nagłówka wiadomości e-mail. **W pierwszym przypadku pośredni ruch przepływów poczty pokazuje wynik *, zanim* administratorzy dodają zaufany uszczelniacz ARC.**

:::image type="content" source="../../media/m365d-indirect-traffic-flow-without-trusted-arc-sealer.PNG" alt-text="Na tej ilustracji firma Contoso publikuje SPF, DKIM i DMARC w ramach standardowych zabezpieczeń poczty e-mail. Nadawca korzystający z protokołu SPF wysyła wiadomość e-mail z wewnątrz contoso.com do fabrikam.com, a ta wiadomość jest przekazywana przez usługę innej firmy, którą firma Contoso zatrudniła, a ta usługa modyfikuje adres IP wysyłania w nagłówku wiadomości e-mail. Poczta kończy się niepowodzeniem SPF z powodu zmienionego adresu IP i DKIM, ponieważ zawartość została zmodyfikowana przez inną firmę podczas sprawdzania dns w EOP. DMARC kończy się niepowodzeniem z powodu błędów SPF i DKIM. Wiadomość jest wysyłana do wiadomości-śmieci, kwarantanny lub odrzuconej.":::

W tym miejscu zobaczysz tę samą **organizację po wykorzystaniu możliwości utworzenia zaufanego uszczelniacza ARC.**

:::image type="content" source="../../media/m365d-indirect-traffic-flow-with-trusted-arc-sealer.PNG" alt-text="W drugiej ilustracji firma Contoso utworzyła listę zaufanych uszczelniaczy ARC. Ten sam użytkownik wysyła drugą wiadomość e-mail z contoso.com do fabrikam.com. Usługa innej firmy zatrudniona przez firmę Contoso modyfikuje adres IP nadawcy w nagłówku wiadomości e-mail. Ale tym razem usługa zaimplementowała uszczelnianie arc, a ponieważ administrator dzierżawy dodał już domenę innej firmy do zaufanych uszczelniaczy ARC, modyfikacja jest akceptowana. SPF kończy się niepowodzeniem dla nowego adresu IP; DKIM kończy się niepowodzeniem z powodu modyfikacji zawartości; DMARC kończy się niepowodzeniem z powodu wcześniejszych awarii; ale usługa ARC rozpoznaje modyfikacje, wystawia przepustkę i akceptuje zmiany. Fałsz również otrzymuje przepustkę. Wiadomość jest wysyłana do skrzynki odbiorczej.":::

## <a name="next-steps-after-you-set-up-arc-for-microsoft-365-defender-for-office"></a>Następne kroki: Po skonfigurowaniu usługi ARC dla Microsoft 365 Defender dla Office

Po skonfigurowaniu sprawdź nagłówki USŁUGI ARC za pomocą [analizatora nagłówków komunikatów](/connectivity-analyzer/message-header-analyzer).

Przejrzyj kroki konfiguracji [SPF](set-up-spf-in-office-365-to-help-prevent-spoofing.md), [DKIM](use-dkim-to-validate-outbound-email.md), [DMARC](use-dmarc-to-validate-email.md).
