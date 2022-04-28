---
title: Konfigurowanie łącznika do archiwizowania danych mobilnych systemu Android
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
description: Administratorzy mogą skonfigurować łącznik TeleMessage do importowania i archiwizowania wiadomości SMS, MMS i połączeń głosowych z telefonów komórkowych z systemem Android. Umożliwia to archiwizowanie danych ze źródeł danych innych firm w Microsoft 365 dzięki czemu można używać funkcji zgodności, takich jak blokada prawna, wyszukiwanie zawartości i zasady przechowywania, aby zarządzać danymi innych firm w organizacji.
ms.openlocfilehash: b250d87ca84360f62467d2e0853384e4fbb1eaef
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65087002"
---
# <a name="set-up-a-connector-to-archive-android-mobile-data"></a>Konfigurowanie łącznika do archiwizowania danych mobilnych systemu Android

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Użyj łącznika TeleMessage w portalu zgodności usługi Microsoft Purview, aby importować i archiwizować wiadomości SMS, MMS, połączenia głosowe i dzienniki połączeń z telefonów komórkowych z systemem Android. Po skonfigurowaniu i skonfigurowaniu łącznika łączy się on z kontem TeleMessage organizacji raz dziennie i importuje komunikację mobilną pracowników przy użyciu archiwum systemu Android TeleMessage do skrzynek pocztowych w Microsoft 365.

Po zapisaniu danych z telefonów komórkowych z systemem Android w skrzynkach pocztowych użytkowników można zastosować funkcje usługi Microsoft Purview, takie jak blokada postępowania sądowego, wyszukiwanie zawartości i zasady przechowywania Microsoft 365 do danych archiwum systemu Android. Na przykład możesz przeszukiwać komunikację mobilną z systemem Android Archiver przy użyciu wyszukiwania zawartości lub skojarzyć skrzynkę pocztową zawierającą dane łącznika Archiwum systemu Android z opiekunem w przypadku zbierania elektronicznych materiałów dowodowych (Premium). Importowanie i archiwizowanie danych w Microsoft 365 przy użyciu łącznika Archiwum systemu Android może pomóc twojej organizacji zachować zgodność z zasadami rządowymi i regulacyjnymi.

## <a name="overview-of-archiving-android-mobile-data"></a>Omówienie archiwizacji danych mobilnych systemu Android

W poniższym omówieniu wyjaśniono proces używania łącznika do archiwizowania danych mobilnych systemu Android w Microsoft 365.

![Przepływ pracy łącznika Archiwum systemu Android.](../media/AndroidArchiverConnectorWorkflow.png)

1. Twoja organizacja współpracuje z usługą TeleMessage w celu skonfigurowania łącznika Archiwum systemu Android. Aby uzyskać więcej informacji, zobacz [Android Archiver](https://www.telemessage.com/office365-activation-for-android-archiver/).

2. W czasie rzeczywistym wiadomości SMS, MMS, połączenia głosowe i dzienniki połączeń z telefonów komórkowych z systemem Android organizacji są kopiowane do witryny TeleMessage.

3. Łącznik Archiwum systemu Android tworzony w portalu zgodności codziennie łączy się z witryną TeleMessage i przesyła dane systemu Android z poprzednich 24 godzin do bezpiecznej lokalizacji usługi Azure Storage w chmurze firmy Microsoft. Łącznik konwertuje również dane systemu Android na format wiadomości e-mail.

4. Łącznik importuje elementy komunikacji mobilnej do skrzynki pocztowej określonego użytkownika. W skrzynce pocztowej określonego użytkownika zostanie utworzony nowy folder o nazwie Android Archiver, a elementy zostaną do niego zaimportowane. Łącznik wykonuje mapowanie przy użyciu wartości właściwości *Adres e-mail użytkownika* . Każda wiadomość e-mail zawiera tę właściwość, która jest wypełniana adresem e-mail każdego uczestnika wiadomości e-mail. Oprócz automatycznego mapowania użytkownika przy użyciu wartości właściwości *Adres e-mail użytkownika* można również zdefiniować mapowanie niestandardowe, przekazując plik mapowania CSV. Ten plik mapowania powinien zawierać numer telefonu komórkowego i odpowiedni adres skrzynki pocztowej Microsoft 365 dla każdego użytkownika. Jeśli włączysz automatyczne mapowanie użytkownika i udostępnisz mapowanie niestandardowe, dla każdego elementu wiadomości e-mail łącznik najpierw przyjrzy się niestandardowemu plikowi mapowania. Jeśli nie znajdzie prawidłowego użytkownika Microsoft 365, który odpowiada numerowi telefonu komórkowego użytkownika, łącznik użyje właściwości adresu e-mail użytkownika elementu wiadomości e-mail. Jeśli łącznik nie znajdzie prawidłowego użytkownika Microsoft 365 w niestandardowym pliku mapowania lub we właściwości *adresu e-mail użytkownika* elementu wiadomości e-mail, element nie zostanie zaimportowany.

## <a name="before-you-set-up-a-connector"></a>Przed skonfigurowaniem łącznika

Niektóre kroki implementacji wymagane do archiwizacji danych komunikacyjnych systemu Android są zewnętrzne dla Microsoft 365 i muszą zostać ukończone przed utworzeniem łącznika w centrum zgodności.

- [Zamów usługę Archiwum systemu Android z usługi TeleMessage i uzyskaj prawidłowe](https://www.telemessage.com/mobile-archiver/order-mobile-archiver-for-o365) konto administracyjne dla swojej organizacji. Podczas tworzenia łącznika musisz zalogować się do tego konta.

- Zarejestruj wszystkich użytkowników, którzy wymagają usługi Archiwum systemu Android na koncie TeleMessage. Podczas rejestrowania użytkowników należy użyć tego samego adresu e-mail, który jest używany dla ich konta Microsoft 365.

- Zainstaluj i aktywuj aplikację TeleMessage Android Archiver na telefonach komórkowych pracowników.

- Użytkownikowi tworzącemu łącznik Archiwum systemu Android musi zostać przypisana rola administratora łącznika danych. Ta rola jest wymagana do dodawania łączników na stronie **Łączniki danych** w portalu zgodności. Ta rola jest domyślnie dodawana do wielu grup ról. Aby uzyskać listę tych grup ról, zobacz sekcję "Role w centrach zabezpieczeń i zgodności" w obszarze [Uprawnienia w Centrum zgodności & zabezpieczeń](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternatywnie administrator w organizacji może utworzyć niestandardową grupę ról, przypisać rolę administratora łącznika danych, a następnie dodać odpowiednich użytkowników jako członków. Aby uzyskać instrukcje, zobacz sekcję "Tworzenie niestandardowej grupy ról" w obszarze [Uprawnienia w portalu zgodności usługi Microsoft Purview](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Ten łącznik danych TeleMessage jest dostępny w środowiskach GCC w chmurze Microsoft 365 US Government. Aplikacje i usługi innych firm mogą obejmować przechowywanie, przesyłanie i przetwarzanie danych klientów organizacji w systemach innych firm, które znajdują się poza infrastrukturą Microsoft 365 i dlatego nie są objęte zobowiązaniami dotyczącymi usługi Microsoft Purview i ochrony danych. Firma Microsoft nie przedstawia żadnej reprezentacji, że użycie tego produktu do łączenia się z aplikacjami innych firm oznacza, że te aplikacje innych firm są zgodne z fedrampem.

## <a name="create-an-android-archiver-connector"></a>Tworzenie łącznika Archiwum systemu Android

Ostatnim krokiem jest utworzenie łącznika Archiwum systemu Android w portalu zgodności. Łącznik używa podanych informacji, aby nawiązać połączenie z witryną TeleMessage i przenieść komunikację systemu Android do odpowiednich skrzynek pocztowych użytkownika w Microsoft 365.

1. Przejdź do pozycji [https://compliance.microsoft.com](https://compliance.microsoft.com) i kliknij pozycję **Łączniki** >  **danychAndroid Archiver**.

2. Na stronie Opis produktu **Archiwum systemu Android** kliknij pozycję **Dodaj łącznik**.

3. Na stronie **Warunki korzystania z usługi** kliknij pozycję **Akceptuj**.

4. Na stronie **Logowanie do usługi TeleMessage** w obszarze Krok 3 wprowadź wymagane informacje w poniższych polach, a następnie kliknij przycisk **Dalej**.

   - **Nazwę użytkownika:** Nazwa użytkownika usługi TeleMessage.

   - **Hasło:** Twoje hasło telemessage.

5. Po utworzeniu łącznika zamknij okno podręczne i kliknij przycisk **Dalej**.

6. Na stronie **Mapowanie użytkownika** włącz automatyczne mapowanie użytkownika i kliknij przycisk **Dalej**. Jeśli potrzebujesz mapowania niestandardowego, przekaż plik CSV, a następnie kliknij przycisk **Dalej**.

7. Przejrzyj ustawienia, a następnie kliknij przycisk **Zakończ** , aby utworzyć łącznik.

8. Przejdź do karty Łączniki na stronie **Łączniki danych** , aby zobaczyć postęp procesu importowania nowego łącznika.

## <a name="known-issues"></a>Znane problemy

- Obecnie nie obsługujemy importowania załączników ani elementów o rozmiarze większym niż 10 MB. Obsługa większych elementów będzie dostępna w późniejszym terminie.
