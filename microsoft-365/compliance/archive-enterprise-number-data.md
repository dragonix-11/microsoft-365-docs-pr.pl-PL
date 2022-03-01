---
title: Konfigurowanie łącznika do archiwizowania danych z archiwum liczb Enterprise TeleMessage
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
description: Administratorzy mogą skonfigurować łącznik do importowania i archiwizowania danych SMS-ów i MMS z Enterprise archiwum liczb telemessage. Dzięki temu można archiwizować dane ze źródeł danych innych firm w programie Microsoft 365, aby zarządzać danymi innych firm przy użyciu funkcji zgodności, takich jak archiwizacja ze względu na przepisy prawne, wyszukiwanie zawartości i zasady przechowywania.
ms.openlocfilehash: 01c72b630c61ff0fda764971872b2a776617c3d2
ms.sourcegitcommit: 36a19d80fe3f053df0fec398a7ff2dfc777f9730
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/30/2021
ms.locfileid: "63020789"
---
# <a name="set-up-a-connector-to-archive-enterprise-number-data"></a>Konfigurowanie łącznika do archiwizowania Enterprise danych liczbowych

Za pomocą łącznika TeleMessage w programie Centrum zgodności platformy Microsoft 365 można importować i archiwizować wiadomości SMS i MMS (Short Messaging Service), wiadomości czatu, nagrania połączeń głosowych i dzienniki połączeń głosowych z archiwum numeru Enterprise. Po skonfigurowaniu i skonfigurowaniu łącznika połączy się on z kontem TeleMessage Twojej organizacji raz dziennie i zaim importuje dane komunikacji mobilnej pracowników za pomocą archiwum liczb TeleMessage Enterprise do skrzynek pocztowych w usłudze Microsoft 365.

Po zapisaniu danych łącznika funkcji TeleMessage Enterprise Number Archiver w skrzynkach pocztowych użytkowników możesz zastosować funkcje zgodności usługi Microsoft 365, takie jak archiwizacja w związku z postępowaniem sądowym, wyszukiwanie zawartości In-Place, archiwizowanie, inspekcja, zgodność z komunikacją i zasady przechowywania usługi Microsoft 365 do danych archiwum liczb usługi Enterprise. Możesz na przykład przeszukać wiadomości TELEMessage Enterprise Number Archiver SMS, MMS i Voice Call przy użyciu wyszukiwania zawartości lub skojarzyć skrzynkę pocztową zawierającą dane łącznika archiwum liczb Enterprise z folderem folderowym w Advanced eDiscovery przypadku. Importowanie Enterprise archiwizowanie danych w programie Microsoft 365 za pomocą łącznika archiwum liczb w programie Microsoft 365 może ułatwić organizacji zachowania zgodności z zasadami rządowymi i przepisami regulowymi.

## <a name="overview-of-archiving-enterprise-number-data"></a>Omówienie archiwizowania Enterprise danych liczbowych

W poniższym o omówieniem wyjaśniono proces używania łącznika do Enterprise danych sieciowych w Microsoft 365.

![Enterprise zarchiwizowanie liczb.](../media/EnterpriseNumberConnectorWorkflow.png)

1. Twoja organizacja współpracuje z usługą TeleMessage w celu skonfigurowania łącznika Enterprise Archiwum liczb. Aby uzyskać więcej informacji, zobacz [tutaj](https://www.telemessage.com/office365-activation-for-enterprise-number-archiver/).

2. Łącznik archiwum liczb Enterprise, który tworzysz w usłudze Centrum zgodności platformy Microsoft 365, łączy się z witryną TeleMessage każdego dnia i przenosi wiadomości e-mail z poprzednich 24 godzin do bezpiecznego obszaru usługi Azure Storage w chmurze firmy Microsoft.

3. Łącznik importuje elementy komunikacji mobilnej do skrzynki pocztowej określonego użytkownika. W skrzynce pocztowej określonego Enterprise jest tworzony nowy folder o nazwie Archiwum liczb, do których elementy są importowane. Łącznik mapuje dane przy użyciu wartości *właściwości Adres e-mail* użytkownika. Każda wiadomość e-mail zawiera tę właściwość, która jest wypełniana adresem e-mail każdego uczestnika wiadomości e-mail. Oprócz automatycznego mapowania użytkowników przy użyciu wartości właściwości Adres e-mail użytkownika możesz również zdefiniować mapowanie niestandardowe, przesyłając plik mapowania plików CSV. Ten plik mapowania powinien zawierać numer telefonu komórkowego użytkownika i odpowiadający mu adres Microsoft 365 pocztowej dla każdego użytkownika. Jeśli włączysz automatyczne mapowanie użytkowników i udostępnisz mapowanie niestandardowe, dla każdego elementu poczty e-mail łącznik najpierw przyjrzy się plikowi mapowania niestandardowego. Jeśli użytkownik nie znajdzie prawidłowego Microsoft 365 odpowiadającego numerowi telefonu komórkowego użytkownika, łącznik użyje właściwości adres e-mail użytkownika elementu poczty e-mail. Jeśli łącznik nie znajdzie prawidłowego użytkownika Microsoft 365 w pliku mapowania niestandardowego lub właściwości adresu e-mail użytkownika elementu poczty  e-mail, element nie zostanie zaimportowany.

## <a name="before-you-set-up-a-connector"></a>Przed skonfigurowaniem łącznika

Niektóre kroki implementacji wymagane do zarchiwizować Enterprise archiwum liczb są zewnętrzne Microsoft 365 i muszą zostać ukończone, zanim będzie można utworzyć łącznik w centrum zgodności.

- [Zamów Enterprise Archiwum liczb w TeleMessage](https://www.telemessage.com/mobile-archiver/order-mobile-archiver-for-o365) i uzyskaj prawidłowe konto administracyjne dla twojej organizacji. Podczas tworzenia łącznika w centrum zgodności musisz zalogować się do tego konta.

- Zarejestruj wszystkich użytkowników wymagających archiwizacji Enterprise wiadomości SMS/MMS w sieci TeleMessage. Podczas rejestrowania użytkowników pamiętaj, aby używać tego samego adresu e-mail, który jest używany na ich Microsoft 365 kontach.

- Zainstaluj i aktywuj aplikację TeleMessage Enterprise Number Archiver na telefonach komórkowych pracowników.

- Użytkownik, który tworzy łącznik Enterprise archiwum liczb, musi mieć przypisaną rolę importowania i eksportowania skrzynek pocztowych w programie Exchange Online. Jest to wymagane do dodawania łączników na **stronie Łączniki** danych w Centrum zgodności platformy Microsoft 365. Domyślnie ta rola nie jest przypisana do żadnej grupy ról w Exchange Online. Rolę importowania i eksportowania skrzynek pocztowych możesz dodać do grupy ról Zarządzanie organizacją w programie Exchange Online. Możesz też utworzyć grupę ról, przypisać rolę importowania i eksportowania skrzynek pocztowych, a następnie dodać odpowiednich użytkowników jako członków. Aby uzyskać więcej informacji, zobacz sekcje [Tworzenie grup ról](/Exchange/permissions-exo/role-groups#create-role-groups) [lub](/Exchange/permissions-exo/role-groups#modify-role-groups) Modyfikowanie grup ról w artykule "Zarządzanie grupami ról w aplikacji Exchange Online".

- Ten łącznik danych TeleMessage jest dostępny w GCC w chmurze dla instytucji rządowych Microsoft 365 USA. Aplikacje i usługi innych firm mogą obejmować przechowywanie, przekazywanie i przetwarzanie danych klienta Organizacji w systemach innych firm, które znajdują się poza infrastrukturą firmy Microsoft 365 i dlatego nie są objęte zobowiązaniami firmy Microsoft 365 w zakresie zgodności z przepisami i ochrony danych. Firma Microsoft nie zapewnia, że używanie tego produktu do łączenia się z aplikacjami innych firm oznacza, że te aplikacje innych firm są zgodne z fedRAMP.

## <a name="create-an-enterprise-number-archiver-connector"></a>Tworzenie łącznika Enterprise archiwum liczb

Po zakończeniu wymagań wstępnych opisanych w poprzedniej sekcji możesz utworzyć łącznik Enterprise archiwum liczb w Centrum zgodności platformy Microsoft 365. Łącznik używa podanej informacji do nawiązania połączenia z witryną TeleMessage i przesłania wiadomości SMS, MMS oraz wiadomości połączeń głosowych do odpowiednich skrzynek pocztowych użytkowników w Microsoft 365.

1. Przejdź do łączników [https://compliance.microsoft.com](https://compliance.microsoft.com/) danych, a **następnie** \> **Enterprise archiwum liczb**.

2. Na stronie **Enterprise opis produktu Archiwum** liczb kliknij pozycję **Dodaj łącznik**

3. Na stronie **Warunki użytkowania usługi** kliknij pozycję **Zaakceptuj**.

4. Na stronie **Login to TeleMessage** (Logowanie do telemessage) w obszarze Krok 3 wprowadź wymagane informacje w następujących polach, a następnie kliknij przycisk **Dalej**.

   - **Nazwa użytkownika:** Twoja nazwa użytkownika aplikacji TeleMessage.

   - **Hasło:** Hasło aplikacji TeleMessage.

5. Po utworzeniu łącznika możesz zamknąć okno podręczne i przejść do następnej strony.

6. Na stronie **Mapowanie użytkowników** włącz automatyczne mapowanie użytkowników. Aby włączyć mapowanie niestandardowe, przekaż plik CSV zawierający informacje o mapowaniu użytkowników, a następnie kliknij przycisk **Dalej**.

7. Przejrzyj ustawienia, a następnie kliknij przycisk **Zakończ,** aby utworzyć łącznik.

8. Przejdź do karty Łączniki na **stronie Łączniki** danych, aby wyświetlić postęp procesu importowania nowego łącznika.

## <a name="known-issues"></a>Znane problemy

- Obecnie importowanie załączników ani elementów większych niż 10 MB nie jest obsługuje. Obsługa większych elementów będzie dostępna w późniejszym terminie.