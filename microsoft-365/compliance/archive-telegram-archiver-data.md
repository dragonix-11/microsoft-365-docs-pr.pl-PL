---
title: Konfigurowanie łącznika do archiwizowania danych komunikacyjnych telegramu w Microsoft 365
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
description: Administratorzy mogą skonfigurować łącznik TeleMessage do importowania i archiwizowania danych komunikacyjnych telegramu w Microsoft 365. Umożliwia to archiwizowanie danych ze źródeł danych innych firm w Microsoft 365 dzięki czemu można używać funkcji zgodności, takich jak blokada prawna, wyszukiwanie zawartości i zasady przechowywania, aby zarządzać danymi innych firm w organizacji.
ms.openlocfilehash: b18d05fa697f3d23e57444d5757d14dff7acfc23
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2022
ms.locfileid: "64947126"
---
# <a name="set-up-a-connector-to-archive-telegram-communications-data"></a>Konfigurowanie łącznika do archiwizowania danych komunikacyjnych telegramu

Użyj łącznika TeleMessage w portalu zgodności usługi Microsoft Purview, aby zaimportować i zarchiwizować czaty telegramu, załączniki, pliki oraz usunięte komunikaty i wywołania. Po skonfigurowaniu i skonfigurowaniu łącznika łączy się on z kontem TeleMessage organizacji i importuje komunikację mobilną pracowników przy użyciu archiwum Telegram do skrzynek pocztowych w Microsoft 365.

Po zapisaniu danych łącznika usługi Telegram Archiver w skrzynkach pocztowych użytkowników można zastosować funkcje usługi Microsoft Purview, takie jak blokada postępowania sądowego, wyszukiwanie zawartości i zasady przechowywania Microsoft 365 do danych komunikacyjnych usługi Telegram. Na przykład możesz wyszukać komunikację telegramową przy użyciu wyszukiwania zawartości lub skojarzyć skrzynkę pocztową zawierającą dane łącznika Telegram Archiver z opiekunem w przypadku zbierania elektronicznych materiałów dowodowych (Premium). Importowanie i archiwizowanie danych w Microsoft 365 przy użyciu łącznika Archiwum Telegram może pomóc twojej organizacji zachować zgodność z przepisami dotyczącymi ładu korporacyjnego i zasadami prawnymi.

## <a name="overview-of-archiving-telegram-communications-data"></a>Omówienie archiwizacji danych komunikacyjnych telegramu

W poniższym omówieniu wyjaśniono proces używania łącznika do archiwizowania danych komunikacyjnych telegramu w Microsoft 365.

![Przepływ pracy archiwizacji komunikacji telegramu.](../media/TelegramConnectorWorkflow.png)

1. Twoja organizacja współpracuje z usługą TeleMessage w celu skonfigurowania łącznika Archiwum Telegram. Aby uzyskać więcej informacji, zobacz [Aktywowanie archiwum TeleMessage Telegram na potrzeby Microsoft 365](https://www.telemessage.com/microsoft-365-activation-for-telegram-archiver/).

2. W czasie rzeczywistym dane telegramu organizacji są kopiowane do witryny TeleMessage.

3. Łącznik Archiwum Telegram tworzony w portalu zgodności codziennie łączy się z witryną TeleMessage i przesyła wiadomości e-mail z poprzednich 24 godzin do bezpiecznego obszaru usługi Azure Storage w chmurze firmy Microsoft.

4. Łącznik importuje elementy komunikacji mobilnej do skrzynki pocztowej określonego użytkownika. Nowy folder o nazwie Telegram Archiver zostanie utworzony w skrzynce pocztowej określonego użytkownika, a elementy zostaną do niego zaimportowane. Łącznik wykonuje to mapowanie przy użyciu wartości właściwości *Adres e-mail użytkownika* . Każda wiadomość e-mail zawiera tę właściwość, która jest wypełniana adresem e-mail każdego uczestnika wiadomości e-mail.

> Oprócz automatycznego mapowania użytkownika przy użyciu wartości właściwości *Adres e-mail użytkownika* można również zdefiniować mapowanie niestandardowe, przekazując plik mapowania CSV. Ten plik mapowania powinien zawierać numer telefonu komórkowego użytkownika i odpowiedni adres skrzynki pocztowej Microsoft 365 dla każdego użytkownika. Jeśli włączysz automatyczne mapowanie użytkownika i udostępnisz mapowanie niestandardowe, dla każdego elementu wiadomości e-mail łącznik najpierw przyjrzy się niestandardowemu plikowi mapowania. Jeśli nie znajdzie prawidłowego Microsoft 365 użytkownika odpowiadającego numerowi telefonu komórkowego użytkownika, łącznik użyje właściwości adres e-mail użytkownika elementu wiadomości e-mail. Jeśli łącznik nie znajdzie prawidłowego Microsoft 365 użytkownika w niestandardowym pliku mapowania lub we właściwości *adresu e-mail użytkownika* elementu wiadomości e-mail, element nie zostanie zaimportowany.

## <a name="before-you-set-up-a-connector"></a>Przed skonfigurowaniem łącznika

- [Zamów usługę archiwizacji telegramu z usługi TeleMessage i uzyskaj prawidłowe](https://www.telemessage.com/mobile-archiver/order-mobile-archiver-for-o365/) konto administracyjne dla swojej organizacji. Musisz zalogować się do tego konta podczas tworzenia łącznika w Centrum zgodności.

- Zarejestruj wszystkich użytkowników, którzy wymagają archiwizacji telegramu na koncie TeleMessage. Podczas rejestrowania użytkowników należy użyć tego samego adresu e-mail, który jest używany dla ich konta Microsoft 365.

- Zainstaluj aplikację Telegram Archiver na telefonach komórkowych pracowników i aktywuj ją. Aplikacja Telegram Archiver pozwala im komunikować się i rozmawiać z innymi użytkownikami telegramu.

- Użytkownikowi tworzącemu łącznik Archiwum telegramu w kroku 3 musi zostać przypisana rola administratora łącznika danych. Ta rola jest wymagana do dodawania łączników na stronie **Łączniki danych** w portalu zgodności. Ta rola jest domyślnie dodawana do wielu grup ról. Aby uzyskać listę tych grup ról, zobacz sekcję "Role w centrach zabezpieczeń i zgodności" w obszarze [Uprawnienia w Centrum zgodności & zabezpieczeń](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternatywnie administrator w organizacji może utworzyć niestandardową grupę ról, przypisać rolę administratora łącznika danych, a następnie dodać odpowiednich użytkowników jako członków. Aby uzyskać instrukcje, zobacz sekcję "Tworzenie niestandardowej grupy ról" w obszarze [Uprawnienia w portalu zgodności usługi Microsoft Purview](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Ten łącznik danych TeleMessage jest dostępny w środowiskach GCC w chmurze Microsoft 365 US Government. Aplikacje i usługi innych firm mogą obejmować przechowywanie, przesyłanie i przetwarzanie danych klientów organizacji w systemach innych firm, które znajdują się poza infrastrukturą Microsoft 365 i dlatego nie są objęte zobowiązaniami dotyczącymi usługi Microsoft Purview i ochrony danych. Firma Microsoft nie przedstawia żadnej reprezentacji, że użycie tego produktu do łączenia się z aplikacjami innych firm oznacza, że te aplikacje innych firm są zgodne z fedrampem.

## <a name="create-a-telegram-archiver-connector"></a>Tworzenie łącznika usługi Telegram Archiver

Po ukończeniu wymagań wstępnych opisanych w poprzedniej sekcji możesz utworzyć łącznik Telegram Archiver w portalu zgodności. Łącznik używa podanych informacji w celu nawiązania połączenia z witryną TeleMessage i przesyłania danych komunikacji telegramu do odpowiednich skrzynek pocztowych użytkownika w Microsoft 365.

1. Przejdź do obszaru <https://compliance.microsoft.com> , a następnie kliknij pozycję **Łączniki danych** > **archiwum Telegram**.

2. Na stronie Opis produktu **Telegram Archiver** kliknij pozycję **Dodaj łącznik**.

3. Na stronie **Warunki korzystania z usługi** kliknij pozycję **Akceptuj**.

4. Na stronie **Logowanie do usługi TeleMessage** w obszarze Krok 3 wprowadź wymagane informacje w poniższych polach, a następnie kliknij przycisk **Dalej**.

    - **Nazwę użytkownika:** Nazwa użytkownika usługi TeleMessage.

    - **Hasło:** Twoje hasło telemessage.

5. Po utworzeniu łącznika możesz zamknąć okno podręczne i przejść do następnej strony.

6. Na stronie **Mapowanie użytkownika** włącz automatyczne mapowanie użytkowników. Aby włączyć mapowanie niestandardowe, przekaż plik CSV zawierający informacje o mapowaniu użytkownika, a następnie kliknij przycisk **Dalej**.

7. Przejrzyj ustawienia, a następnie kliknij przycisk **Zakończ** , aby utworzyć łącznik.

8. Przejdź do karty Łączniki na stronie **Łączniki danych** , aby zobaczyć postęp procesu importowania nowego łącznika.

## <a name="known-issues"></a>Znane problemy

- Obecnie nie obsługujemy importowania załączników ani elementów o rozmiarze większym niż 10 MB. Obsługa większych elementów będzie dostępna w późniejszym terminie.
