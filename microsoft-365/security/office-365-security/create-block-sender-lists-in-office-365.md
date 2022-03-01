---
title: Tworzenie list zablokowanych nadawców
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: how-to
ms.localizationpriority: medium
search.appverid:
- MET150s
description: Administratorzy mogą dowiedzieć się więcej o dostępnych i preferowanych opcjach blokowania wiadomości przychodzących w u Exchange Online Protection (EOP).
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 71f6312f160a445c184a52f96493360af8b9a360
ms.sourcegitcommit: 9f0e84835121ce6228fdc69182c24be7ad1cb20e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/18/2022
ms.locfileid: "63014883"
---
# <a name="create-blocked-sender-lists-in-eop"></a>Tworzenie list zablokowanych nadawców w uciekinie eop

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender dla Office 365 plan 1 i plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

W Microsoft 365 z skrzynkami pocztowymi w organizacjach Exchange Online lub autonomicznych organizacjach usługi Exchange Online Protection (EOP) bez skrzynek pocztowych usługi Exchange Online program EOP oferuje wiele sposobów blokowania wiadomości e-mail od niechcianych nadawców. Te opcje to Outlook zablokowani nadawcy, listy zablokowanych nadawców lub listy zablokowanych domen w zasadach ochrony przed spamem, reguły przepływu poczty Exchange (nazywane także regułami transportu) oraz lista zablokowanych adresów IP (filtrowanie połączeń). Te opcje można określić zbiorczo jako listy _zablokowanych nadawców_.

Najlepszą metodą blokowania nadawców jest zakres wpływu. W przypadku jednego użytkownika odpowiednim rozwiązaniem może być zablokowani Outlook nadawcy. W przypadku wielu użytkowników odpowiednia będzie jedna z pozostałych opcji. Poniższe opcje są klasyfikowane według zakresu i szerokości stron. Lista może mieć od wąskiego do szerokiego, ale zawiera _szczegółowe informacje,_ aby uzyskać pełne zalecenia.

1. Outlook zablokowanych nadawców (lista zablokowanych nadawców przechowywana w każdej skrzynce pocztowej)

2. Listy zablokowanych nadawców lub zablokowanych domen (zasady ochrony przed spamem)

3. Reguły przepływu poczty e-mail

4. Lista zablokowanych adresów IP (filtrowanie połączeń)

> [!NOTE]
> Ustawienia blokowania dla całej organizacji mogą dotyczyć wyników fałszywie ujemnych (nieodebranych spamu), ale należy również przesłać te wiadomości do firmy Microsoft w celu analizy. Zarządzanie wartościami fałszywie ujemnym za pomocą list zablokowanych znacznie zwiększa obciążenie administracyjne. Jeśli używasz list zablokowanych do wykrywania nieodebranych spamu, pamiętaj, aby zachować gotowy temat Zgłaszanie wiadomości i plików do firmy [Microsoft](report-junk-email-messages-to-microsoft.md) .

Z kolei w przypadku korzystania z list bezpiecznych nadawców jest dostępnych kilka opcji, które pozwalają zawsze zezwalać na wiadomości _e-mail_ z określonych źródeł. Aby uzyskać więcej informacji, zobacz [Tworzenie bezpiecznych list nadawców](create-safe-sender-lists-in-office-365.md).

## <a name="email-message-basics"></a>Podstawowe informacje o wiadomościach e-mail

Standardowa wiadomość e-mail SMTP składa się z _koperty_ wiadomości i jej zawartości. Koperta wiadomości zawiera informacje wymagane do przekazywania i dostarczania wiadomości między serwerami SMTP. Zawartość wiadomości zawiera pola nagłówka wiadomości (zbiorczo _nazywane nagłówkiem_ wiadomości) i treść wiadomości. Koperta wiadomości jest opisana w dokumencie RFC 5321, a nagłówek wiadomości jest opisany w dokumencie RFC 5322. Adresaci nigdy nie widzą rzeczywistej koperty wiadomości, ponieważ jest generowana przez proces transmisji wiadomości i w rzeczywistości nie jest ona częścią wiadomości.

- Adres `5321.MailFrom` (znany także jako adres **MAIL FROM** , nadawca P1 lub nadawca koperty) to adres e-mail używany w transmisji SMTP wiadomości. Ten adres e-mail jest zwykle rejestrowany w polu nagłówka **return-ścieżka** w nagłówku wiadomości (chociaż nadawca może wyznaczyć inny adres **e-mail** ze ścieżką zwrotną). Jeśli nie można dostarczyć wiadomości, jest ona adresatem raportu o niedostarczeniu (nazywanego również wiadomością o niedostarczeniu lub wiadomością odsuń).

- Nadawca `5322.From` (nazywany również nadawcą Od lub P2) jest adresem e-mail w polu  nagłówka Od i jest adresem e-mail nadawcy wyświetlanym w klientach poczty e-mail.

Adresy i często są `5321.MailFrom` `5322.From` takie same (komunikacja między osobami). Jednak gdy wiadomości e-mail są wysyłane w imieniu innej osoby, adresy mogą być inne.

Na listach zablokowanych nadawców i w domenach zablokowanych w zasadach ochrony przed spamem usługi EOP sprawdź zarówno adresy, jak `5321.MailFrom` i `5322.From` adresy. Outlook zablokowani nadawcy mają tylko ten `5322.From` adres.

## <a name="use-outlook-blocked-senders"></a>Używanie Outlook zablokowanych nadawców

Jeśli tylko niewielka liczba użytkowników otrzymała niechciane wiadomości e-mail, użytkownicy lub administratorzy mogą dodać adresy e-mail tych nadawców do listy zablokowanych nadawców w skrzynce pocztowej. Aby uzyskać instrukcje, [zobacz Konfigurowanie ustawień wiadomości-śmieci Exchange Online pocztowych](configure-junk-email-settings-on-exo-mailboxes.md).

Gdy wiadomości zostaną pomyślnie zablokowane z powodu listy zablokowanych nadawców użytkownika, pole nagłówka **X-Forefront-Antispam-Report** będzie zawierać wartość `SFV:BLK`.

> [!NOTE]
> Jeśli niechciane wiadomości to biuletyny z wiarygodnego i rozpoznawalnego źródła, niewysubskrybowanie wiadomości e-mail to kolejna opcja zatrzymania odbierania wiadomości przez użytkownika.

## <a name="use-blocked-sender-lists-or-blocked-domain-lists"></a>Używanie list zablokowanych nadawców lub zablokowanych domen

Jeśli problem dotyczy wielu użytkowników, ten zakres jest szerszy, więc następną najlepszą opcją jest zablokowanie list nadawców lub zablokowanych list domen w zasadach ochrony przed spamem. Wiadomości od nadawców z tych list są oznaczane jako **spam** (nie spam o dużej **pewności), a** wiadomość jest akcję skonfigurowaną dla werdyktu filtru spamu. Aby uzyskać więcej informacji, [zobacz Konfigurowanie zasad ochrony przed spamem](configure-your-spam-filter-policies.md).

Maksymalny limit dla tych list to około 1000 wpisów.

## <a name="use-mail-flow-rules"></a>Używanie reguł przepływu poczty e-mail

Jeśli chcesz zablokować wiadomości wysyłane do określonych użytkowników lub do całej organizacji, możesz użyć reguł przepływu poczty e-mail. Reguły przepływu poczty e-mail są bardziej elastyczne niż listy zablokowanych nadawców lub listy domen zablokowanych nadawców, ponieważ mogą również wyszukiwać słowa kluczowe lub inne właściwości w niechcianych wiadomościach.

Niezależnie od warunków lub wyjątków, przy użyciu których identyfikujesz wiadomości, skonfigurujesz akcję w celu ustawienia poziomu ufności filtru spamu (SCL) wiadomości na 9, co oznacza wiadomość jako spam o dużej **pewności.** Aby uzyskać więcej informacji, zobacz Ustawianie listy SCL w wiadomościach przy użyciu [reguł przepływu poczty](/exchange/security-and-compliance/mail-flow-rules/use-rules-to-set-scl).

> [!IMPORTANT]
> Tworzenie zbyt agresywnych reguł jest łatwe, dlatego  ważne jest, aby identyfikować tylko wiadomości, które mają zostać zablokowane, przy użyciu bardzo konkretnych kryteriów. Pamiętaj też, aby włączyć inspekcję tej reguły i przetestować jej wyniki, aby upewnić się, że wszystko działa zgodnie z oczekiwaniami.

## <a name="use-the-ip-block-list"></a>Korzystanie z listy zablokowanych adresów IP

Jeśli zablokowanie nadawcy przy użyciu jednej z pozostałych opcji nie jest _możliwe, tylko_ należy użyć listy zablokowanych adresów IP w zasadach filtru połączenia. Aby uzyskać więcej informacji, [zobacz Konfigurowanie zasad filtru połączenia](configure-the-connection-filter-policy.md). Należy utrzymać minimalną liczbę zablokowanych adresów IP, dlatego nie zaleca się blokowania całych zakresów _adresów IP_ .

Należy zwłaszcza  unikać dodawania zakresów adresów IP należących do usług dla klientów (na przykład outlook.com) lub infrastruktury udostępnionej, a także sprawdzać listę zablokowanych adresów IP w ramach regularnej konserwacji.
