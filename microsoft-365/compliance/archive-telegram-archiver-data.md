---
title: Konfigurowanie łącznika do archiwizowania danych komunikacji telegramu w programie Microsoft 365
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
description: Administratorzy mogą skonfigurować łącznik TeleMessage w celu importowania i archiwizowania danych komunikacji telegramu w Microsoft 365. Dzięki temu można archiwizować dane ze źródeł danych innych firm w programie Microsoft 365, aby zarządzać danymi innych firm przy użyciu funkcji zgodności, takich jak archiwizacja ze względu na przepisy prawne, wyszukiwanie zawartości i zasady przechowywania.
ms.openlocfilehash: 2fbe0a97572d13b6d2ba6e26ac02fd5ee8817b8a
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63312295"
---
# <a name="set-up-a-connector-to-archive-telegram-communications-data"></a>Konfigurowanie łącznika do archiwizowania danych komunikacji telegramu

Użyj łącznika TeleMessage w aplikacji Centrum zgodności platformy Microsoft 365 do importowania i archiwizowania czatów telegramu, załączników, plików oraz usuniętych wiadomości i połączeń. Po skonfigurowaniu i skonfigurowaniu łącznika połączy się on z kontem teleMessage Twojej organizacji i zaim importuje wiadomości mobilne pracowników za pomocą archiwum telegramu do skrzynek pocztowych w usłudze Microsoft 365.

Po zapisaniu danych łącznika programu Telegram Archiver w skrzynkach pocztowych użytkowników możesz zastosować funkcje zgodności usługi Microsoft 365, takie jak archiwizacja w związku z postępowaniem sądowym, przeszukiwanie zawartości i zasady przechowywania Microsoft 365 do danych komunikacji telegramu. Możesz na przykład przeszukać komunikację za pomocą telegramu przy użyciu funkcji przeszukiwania zawartości lub skojarzyć ze skrzynką pocztową zawierającą dane łącznika archiwum telegramu ze współpracownikiem w Advanced eDiscovery przypadku. Importowanie i archiwizowanie danych w programie Microsoft 365 za pomocą łącznika archiwum telegramu może ułatwić organizacji zgodność z przepisami dotyczącymi ładu korporacyjnego i przepisami prawnymi.

## <a name="overview-of-archiving-telegram-communications-data"></a>Omówienie archiwizowania danych komunikacji telegramu

W poniższym przeglądzie wyjaśniono proces używania łącznika do archiwizowania danych komunikacji telegramu w programie Microsoft 365.

![Przepływ pracy archiwizacji komunikacji telegramu.](../media/TelegramConnectorWorkflow.png)

1. Twoja organizacja współpracuje z usługą TeleMessage w celu skonfigurowania łącznika archiwum telegramu. Aby uzyskać więcej informacji, zobacz [Aktywowanie archiwum telegramu TeleMessage dla Microsoft 365](https://www.telemessage.com/microsoft-365-activation-for-telegram-archiver/).

2. W czasie rzeczywistym dane telegramu Organizacji są kopiowane do witryny TeleMessage.

3. Łącznik Archiwum telegramu, który tworzysz w aplikacji Centrum zgodności platformy Microsoft 365, łączy się z witryną TeleMessage każdego dnia i przesyła wiadomości e-mail z poprzednich 24 godzin do bezpiecznego obszaru usługi Azure Storage w chmurze firmy Microsoft.

4. Łącznik importuje elementy komunikacji mobilnej do skrzynki pocztowej określonego użytkownika. W skrzynce pocztowej określonego użytkownika zostanie utworzony nowy folder o nazwie Archiwum telegramów, do których elementy zostaną zaimportowane. Łącznik obsługuje to mapowanie przy użyciu wartości *właściwości Adres e-mail* użytkownika. Każda wiadomość e-mail zawiera tę właściwość, która jest wypełniana adresem e-mail każdego uczestnika wiadomości e-mail.

> Oprócz automatycznego mapowania użytkowników przy użyciu wartości właściwości Adres e-mail użytkownika możesz również zdefiniować mapowanie niestandardowe, przesyłając plik mapowania plików CSV. Ten plik mapowania powinien zawierać numer telefonu komórkowego użytkownika i odpowiadający mu adres Microsoft 365 pocztowej dla każdego użytkownika. Jeśli włączysz automatyczne mapowanie użytkowników i udostępnisz mapowanie niestandardowe, dla każdego elementu poczty e-mail łącznik najpierw przyjrzy się plikowi mapowania niestandardowego. Jeśli użytkownik nie znajdzie prawidłowego Microsoft 365 odpowiadającego numerowi telefonu komórkowego użytkownika, łącznik użyje właściwości adres e-mail użytkownika elementu poczty e-mail. Jeśli łącznik nie znajdzie prawidłowego użytkownika Microsoft 365 w pliku mapowania niestandardowego lub właściwości adresu e-mail użytkownika elementu poczty  e-mail, element nie zostanie zaimportowany.

## <a name="before-you-set-up-a-connector"></a>Przed skonfigurowaniem łącznika

- Zamów [usługę archiwizacji telegramu w usłudze TeleMessage](https://www.telemessage.com/mobile-archiver/order-mobile-archiver-for-o365/) i uzyskaj prawidłowe konto administracyjne dla twojej organizacji. Podczas tworzenia łącznika w centrum zgodności musisz zalogować się do tego konta.

- Zarejestruj wszystkich użytkowników wymagających archiwizacji telegramu na koncie usługi TeleMessage. Podczas rejestrowania użytkowników pamiętaj, aby używać tego samego adresu e-mail, który jest używany na ich Microsoft 365 kontach.

- Zainstaluj aplikację Archiwum telegramów na telefonach komórkowych pracowników i aktywuj ją. Aplikacja Archiwum telegramów umożliwia im komunikowanie się i rozmawianie na czacie z innymi użytkownikami telegramu.

- Użytkownik, który tworzy łącznik archiwum telegramu w kroku 3, musi mieć przypisaną rolę Administratora łącznika danych. Ta rola jest wymagana do dodawania łączników na **stronie Łączniki** danych w Centrum zgodności platformy Microsoft 365. Ta rola jest domyślnie dodawana do wielu grup ról. Aby uzyskać listę tych grup ról, zobacz sekcję "Role w centrach zabezpieczeń i zgodności" w sekcji Uprawnienia w Centrum zabezpieczeń & [zgodności](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Administrator w organizacji może również utworzyć niestandardową grupę ról, przypisać rolę administrator łącznika danych, a następnie dodać odpowiednich użytkowników jako członków. Aby uzyskać instrukcje, zobacz sekcję "Tworzenie niestandardowej grupy ról" w sekcji Uprawnienia [w Centrum zgodności platformy Microsoft 365](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Ten łącznik danych TeleMessage jest dostępny w GCC w chmurze dla instytucji rządowych Microsoft 365 USA. Aplikacje i usługi innych firm mogą obejmować przechowywanie, przekazywanie i przetwarzanie danych klienta Organizacji w systemach innych firm, które znajdują się poza infrastrukturą firmy Microsoft 365 i dlatego nie są objęte zobowiązaniami firmy Microsoft 365 w zakresie zgodności z przepisami i ochrony danych. Firma Microsoft nie zapewnia, że używanie tego produktu do łączenia się z aplikacjami innych firm oznacza, że te aplikacje innych firm są zgodne z fedRAMP.

## <a name="create-a-telegram-archiver-connector"></a>Tworzenie łącznika archiwum telegramu

Po wyliczaniu wymagań wstępnych opisanych w poprzedniej sekcji można utworzyć łącznik programu Telegram Archiver w Centrum zgodności platformy Microsoft 365. Łącznik używa podanej informacji do nawiązania połączenia z witryną TeleMessage i przesyła dane komunikacji telegramu do odpowiednich skrzynek pocztowych użytkowników w Microsoft 365.

1. Przejdź do łączników <https://compliance.microsoft.com> **danych i kliknij** > **archiwum Telegram**.

2. Na stronie **Opis produktu Archiwum telegramów** kliknij pozycję **Dodaj łącznik**.

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
