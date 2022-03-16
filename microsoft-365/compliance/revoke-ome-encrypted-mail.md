---
title: Odwoływanie wiadomości e-mail zaszyfrowanych za pomocą zaawansowanego szyfrowania wiadomości
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.date: 03/04/2022
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MET150
description: Jako administrator i nadawca wiadomości możesz odwołać określone wiadomości e-mail, które były szyfrowane przy użyciu Zaawansowane szyfrowanie wiadomości usługi Office 365.
ms.openlocfilehash: bf793dce23c91e8b45f96114e6c4a56c866adc32
ms.sourcegitcommit: a216617d6ff27fe7d3089a047fbeaac5d72fd25c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2022
ms.locfileid: "63512256"
---
# <a name="revoke-email-encrypted-by-advanced-message-encryption"></a>Odwoływanie wiadomości e-mail zaszyfrowanych za pomocą zaawansowanego szyfrowania wiadomości

Odwołania wiadomości e-mail są oferowane w ramach Zaawansowane szyfrowanie wiadomości usługi Office 365. Zaawansowane szyfrowanie wiadomości usługi Office 365 jest zawarta w usługach [Microsoft 365 Enterprise E5](https://www.microsoft.com/microsoft-365/enterprise/home), Office 365 E5 i Microsoft 365 E5 (Nonprofit Staff Pricing), Office 365 Enterprise E5 (Nonprofit Staff Pricing) i Office 365 Education A5. Jeśli Twoja organizacja ma subskrypcję, która nie zawiera subskrypcji usługi Zaawansowane szyfrowanie wiadomości usługi Office 365, możesz ją kupić za pomocą dodatku Zgodność platformy Microsoft 365 E5 SKU dla Microsoft 365 E3, Microsoft 365 E3 (Nonprofit Staff Pricing) lub dodatek jednostki SKU usługi Office 365 Advanced Compliance dla produktów Microsoft 365 E3, Microsoft 365 E3 (Nonprofit Staff Pricing) lub Office 365 jednostki SKU.

Ten artykuł jest częścią większego szeregu artykułów [na temat](ome.md) Szyfrowanie wiadomości usługi Office 365.

Jeśli wiadomość została zaszyfrowana przy Zaawansowane szyfrowanie wiadomości usługi Office 365 wiadomości i jesteś Microsoft 365 administratorem lub nadawcą wiadomości, możesz odwołać wiadomość w określonych warunkach. Administratorzy odwołają wiadomości przy użyciu programu PowerShell. Nadawca odwoła wiadomość wysłaną bezpośrednio z Outlook w sieci Web. W tym artykule opisano okoliczności, w których można odwołań, i przedstawiono, jak to zrobić.

> [!NOTE]
> Aby zagwarantować możliwość śledzenia i odwoływania wiadomości OME, należy dodać niestandardowy szablon śledzenia i oznaczania. Zobacz [Dodawanie marki organizacji do zaszyfrowanych wiadomości.](add-your-organization-brand-to-encrypted-messages.md)
  
## <a name="encrypted-emails-that-you-can-revoke"></a>Zaszyfrowane wiadomości e-mail, które można odwołać

Administratorzy i nadawcy wiadomości mogą odwołać zaszyfrowane wiadomości e-mail, jeśli adresat otrzymał zaszyfrowaną wiadomość e-mail opartą na linkach. Jeśli adresat otrzymał natywne środowisko wbudowane w obsługiwanym kliencie poczty Outlook, nie można odwołać wiadomości.

To, czy adresat otrzyma środowisko oparte na linku, czy wbudowane środowisko, zależy od typu tożsamości adresata: adresaci kont Office 365 i kont Microsoft (na przykład użytkownicy usługi outlook.com) otrzymują wbudowane środowisko w obsługiwanych Outlook klienckich. Wszystkie inne typy adresatów, takie jak adresaci usług Gmail i Yahoo, otrzymują środowisko oparte na linkach.

Administratorzy i nadawcy wiadomości mogą odwołać wiadomości, które są szyfrowane przy użyciu szyfrowania zastosowanego bezpośrednio Outlook w sieci Web. Na przykład wiadomości zaszyfrowane za pomocą opcji Szyfruj tylko.

:::image type="content" source="../media/adhocencryptionrevoke.png" alt-text="Zrzut ekranu przedstawiający opcję Tylko szyfrowanie w Outlook w sieci Web.":::

## <a name="recipient-experience-for-revoked-encrypted-emails"></a>Środowisko adresata dla odwołanych zaszyfrowanych wiadomości e-mail

Po odwołaniu wiadomości e-mail adresat otrzymuje komunikat o błędzie, gdy uzyskuje dostęp do zaszyfrowanej wiadomości e-mail za pośrednictwem portalu Szyfrowanie wiadomości usługi Office 365: "Wiadomość została odwołana przez nadawcę".

![Zrzut ekranu przedstawiający odwołaną zaszyfrowaną wiadomość e-mail.](../media/revoked-encrypted-email.png)

## <a name="how-to-revoke-an-encrypted-message-that-you-sent"></a>Jak odwołać wysłaną zaszyfrowaną wiadomość

Możesz odwołać wiadomość wysłaną do pojedynczego adresata, który korzysta z konta społecznościowego, takiego gmail.com lub yahoo.com. Innymi słowy, możesz odwołać wiadomość e-mail wysłaną do pojedynczego adresata, który otrzymał środowisko oparte na linku.

Nie można odwołać wiadomości wysłanej do adresata, który korzysta z konta służbowego w programie Office 365 lub Microsoft 365, bądź do użytkownika, który używa konta Microsoft, na przykład konta outlook.com. 

Aby odwołać wysłaną zaszyfrowaną wiadomość, wykonaj poniższe czynności.

1. W Outlook w sieci Web folder **Wysłane** przejdź do wiadomości, którą chcesz odwołać.

   Jeśli wiadomość zostanie odwołana, u góry wiadomości zobaczysz link "Usuń dostęp zewnętrzny".

    :::image type="content" source="../media/infoprotect-email-encryption/adhocencryptionrevokesentmsg.png" alt-text="Zrzut ekranu przedstawiający zaszyfrowaną pocztę, którą chcesz odwołać w Outlook w sieci Web.":::

2. Kliknij **pozycję Usuń dostęp zewnętrzny,** aby odwołać wiadomość.

   Komunikat pokazuje, że jego stan został odwołany.

   :::image type="content" source="../media/adhocencryptionrevokedmsg.png" alt-text="Zrzut ekranu przedstawiający odwołaną zaszyfrowaną wiadomość w Outlook w sieci Web.":::

## <a name="how-to-revoke-an-encrypted-message-as-an-administrator"></a>Jak odwołać zaszyfrowaną wiadomość jako administrator

Microsoft 365 e-mail, wykonaj następujące ogólne czynności, aby odwołać uprawnianą zaszyfrowaną wiadomość e-mail:

- Uzyskaj identyfikator wiadomości e-mail.
- Sprawdź, czy możesz odwołać wiadomość.
- Odwołaj wiadomość.

### <a name="step-1-obtain-the-message-id-of-the-email"></a>Krok nr 1. Uzyskiwanie identyfikatora wiadomości e-mail

Aby można było odwołać zaszyfrowaną wiadomość, zbierz identyfikator wiadomości. Zazwyczaj jest to format MessageId:

`<xxxxxxxxxxxxxxxxxxxxxxx@xxxxxx.xxxx.prod.outlook.com>`  

Istnieje wiele sposobów na znalezienie identyfikatora wiadomości e-mail, którą chcesz odwołać. W tej sekcji opisano kilka opcji, ale możesz użyć dowolnej metody, która udostępnia identyfikator.

#### <a name="to-identify-the-message-id-of-the-email-you-want-to-revoke-by-using-message-trace-in-the-security-amp-compliance-center"></a>Aby zidentyfikować identyfikator wiadomości e-mail, którą chcesz odwołać, przy użyciu funkcji śledzenia wiadomości w Centrum zgodności &amp; zabezpieczeń

1. Wyszukaj wiadomość e-mail według nadawcy lub adresata za pomocą [funkcji śledzenia nowych wiadomości w Centrum & zgodności](https://blogs.technet.microsoft.com/exchange/2018/05/02/new-message-trace-in-office-365-security-compliance-center/).

2. Po zlokalizowaniu wiadomości e-mail wybierz ją, aby w wyświetlonym **okienku Szczegóły śledzenia** wiadomości. **Rozwiń więcej informacji**, aby zlokalizować identyfikator wiadomości.

#### <a name="to-identify-the-message-id-of-the-email-you-want-to-revoke-by-using-office-message-encryption-reports-in-the-security-amp-compliance-center"></a>Aby zidentyfikować identyfikator wiadomości e-mail, którą chcesz odwołać, przy użyciu raportów szyfrowania Office wiadomości w Centrum &amp; zgodności zabezpieczeń

1. W Centrum zgodności &amp; zabezpieczeń przejdź do raportu Szyfrowanie **wiadomości**. Aby uzyskać informacje o tym raporcie, zobacz [Wyświetlanie raportów dotyczących zabezpieczeń poczty e-mail w Centrum zgodności &amp; zabezpieczeń](../security/office-365-security/view-email-security-reports.md).

2. Wybierz **tabelę Wyświetl szczegóły** i określ komunikat, który chcesz odwołać.

3. Kliknij dwukrotnie wiadomość, aby wyświetlić szczegóły z identyfikatorem wiadomości.

### <a name="step-2-verify-that-the-mail-is-revocable"></a>Krok nr 2. Sprawdzanie, czy wiadomość można odwołać

Aby sprawdzić, czy można odwołać wiadomość, sprawdź, czy pole Stan odwołania jest widoczne w raporcie szyfrowanie w tabeli Szczegóły  w Centrum &amp; zgodności zabezpieczeń.

Aby sprawdzić, czy możesz odwołać określoną wiadomość e-mail przy Windows PowerShell, wykonaj poniższe czynności.

1. Korzystając z konta służbowego z uprawnieniami administratora globalnego w Twojej organizacji, rozpocznij sesję Windows PowerShell i połącz się z Exchange Online. Aby uzyskać instrukcje, [Połączenie do Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Uruchom następujące Get-OMEMessageStatus cmdlet:

     ```powershell
     Get-OMEMessageStatus -MessageId "<message id>" | ft -a  Subject, IsRevocable
     ```

   To polecenie zwraca temat wiadomości i to, czy wiadomość można odwołać. Na przykład:

     ```console
     Subject        IsRevocable
     -------        -----------
     "Test message" True
     ```

### <a name="step-3-revoke-the-mail"></a>Krok nr 3. Odwoływanie wiadomości

Gdy znasz identyfikator wiadomości e-mail, którą chcesz odwołać, i po sprawdzeniu, że wiadomość można odwołać, &amp; możesz odwołać wiadomość e-mail za pomocą Centrum zgodności zabezpieczeń lub Windows PowerShell.

Aby odwołać wiadomość za pomocą Centrum &amp; zgodności zabezpieczeń

1. Używając konta służbowego z uprawnieniami administratora globalnego w organizacji, połącz się z Centrum zabezpieczeń & zgodności.

2. W **raporcie Szyfrowanie** w tabeli **Szczegóły** wiadomości wybierz pozycję **Odwołaj wiadomość**.

Aby odwołać wiadomość e-mail przy Windows PowerShell, użyj Set-OMEMessageRevocation cmdlet.

1. Używając konta służbowego z uprawnieniami administratora globalnego w twojej organizacji, możesz Połączenie program [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Uruchom następujące Set-OMEMessageRevocation cmdlet:

    ```powershell
    Set-OMEMessageRevocation -Revoke $true -MessageId "<messageId>"
    ```

3. Aby sprawdzić, czy wiadomość e-mail została odwołana, uruchom Get-OMEMessageStatus cmdlet w następujący sposób:

    ```powershell
    Get-OMEMessageStatus -MessageId "<messageId>" | ft -a  Subject, Revoked
    ```

    Jeśli odwołanie zakończyło się pomyślnie, polecenie cmdlet zwraca następujący wynik:  

     ```console
     Revoked: True
     ```

## <a name="more-information-about-office-365-advanced-message-encryption"></a>Więcej informacji na temat Zaawansowane szyfrowanie wiadomości usługi Office 365

- [Zaawansowane szyfrowanie wiadomości usługi Office 365](ome-advanced-message-encryption.md)

- [Zaawansowane szyfrowanie wiadomości usługi Office 365 — wygasanie wiadomości e-mail](ome-advanced-expiration.md)

- [Opis usługi zgodności i zasad dotyczących wiadomości](/office365/servicedescriptions/exchange-online-service-description/message-policy-and-compliance)