---
title: Konfigurowanie łącznika do archiwizowania danych WeChat na platformie Microsoft 365
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
description: Skonfiguruj i użyj łącznika w portal zgodności Microsoft Purview, aby zaimportować i zarchiwizować dane WeChat na platformie Microsoft 365.
ms.openlocfilehash: 1cc5ce3f15f8e40f5515dbac046fce8370a4252c
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66630604"
---
# <a name="set-up-a-connector-to-archive-wechat-data"></a>Konfigurowanie łącznika do archiwizowania danych WeChat

Użyj łącznika TeleMessage w portal zgodności Microsoft Purview, aby zaimportować i zarchiwizować wywołania WeChat i WeCom, czaty, załączniki, pliki i odwołane komunikaty. Po skonfigurowaniu i skonfigurowaniu łącznika łączy się on z kontem TeleMessage organizacji i importuje komunikację mobilną pracowników przy użyciu archiwum TeleMessage WeChat do skrzynek pocztowych na platformie Microsoft 365.

Po przechowywaniu danych łącznika archiwum WeChat w skrzynkach pocztowych użytkowników można zastosować takie funkcje usługi Microsoft Purview, jak blokada postępowania sądowego, zbieranie elektronicznych materiałów dowodowych, archiwizowanie In-Place, inspekcja, zgodność z komunikacją i zasady przechowywania usługi Microsoft 365 do danych komunikacyjnych platformy WeChat. Możesz na przykład wyszukać komunikację WeChat przy użyciu funkcji wyszukiwania zawartości lub skojarzyć skrzynkę pocztową zawierającą dane łącznika Archiwum WeChat z opiekunem w przypadku zbierania elektronicznych materiałów dowodowych (Premium). Importowanie i archiwizowanie danych w usłudze Microsoft 365 przy użyciu łącznika Archiwum WeChat może pomóc twojej organizacji zachować zgodność z przepisami dotyczącymi ładu korporacyjnego i zasadami prawnymi.

## <a name="overview-of-archiving-wechat-communication-data"></a>Omówienie archiwizacji danych komunikacyjnych WeChat

W poniższym omówieniu wyjaśniono proces używania łącznika do archiwizowania danych komunikacyjnych WeChat na platformie Microsoft 365.

![Przepływ pracy archiwizacji danych Archiwum WeChat.](../media/WeChatConnectorWorkflow.png)

1. Twoja organizacja współpracuje z usługą TeleMessage w celu skonfigurowania łącznika Archiwum WeChat.

2. W czasie rzeczywistym dane WeChat organizacji są kopiowane do witryny TeleMessage.

3. Łącznik Archiwum WeChat tworzony w portalu zgodności codziennie łączy się z witryną TeleMessage i przesyła wiadomości e-mail z poprzednich 24 godzin do bezpiecznego obszaru usługi Azure Storage w chmurze firmy Microsoft.

4. Łącznik importuje elementy komunikacji mobilnej do skrzynki pocztowej określonego użytkownika. Nowy folder o nazwie WeChat Archiver zostanie utworzony w skrzynce pocztowej określonego użytkownika, a elementy zostaną do niego zaimportowane. Łącznik wykonuje mapowanie przy użyciu wartości właściwości *Adres e-mail użytkownika* . Każda wiadomość e-mail zawiera tę właściwość, która jest wypełniana adresem e-mail każdego uczestnika wiadomości e-mail. Oprócz automatycznego mapowania użytkownika przy użyciu wartości właściwości *Adres e-mail użytkownika* można również zdefiniować mapowanie niestandardowe, przekazując plik mapowania CSV. Ten plik mapowania powinien zawierać numer telefonu komórkowego użytkownika i odpowiedni adres skrzynki pocztowej platformy Microsoft 365 dla każdego użytkownika. Jeśli włączysz automatyczne mapowanie użytkownika i udostępnisz mapowanie niestandardowe, dla każdego elementu wiadomości e-mail łącznik najpierw przyjrzy się niestandardowemu plikowi mapowania. Jeśli nie znajdzie prawidłowego użytkownika platformy Microsoft 365, który odpowiada numerowi telefonu komórkowego użytkownika, łącznik użyje właściwości adres e-mail użytkownika elementu poczty e-mail. Jeśli łącznik nie znajdzie prawidłowego użytkownika platformy Microsoft 365 w niestandardowym pliku mapowania lub we właściwości *adresu e-mail użytkownika* elementu poczty e-mail, element nie zostanie zaimportowany.

## <a name="before-you-set-up-a-connector"></a>Przed skonfigurowaniem łącznika

- Współpracuj z aplikacją TeleMessage, aby skonfigurować łącznik archiwum WeChat. Aby uzyskać więcej informacji, zobacz [Aktywowanie archiwum WeChat TeleMessage dla platformy Microsoft 365](https://www.telemessage.com/microsoft-365-activation-for-wechat-archiver/).

- Skonfiguruj łącznik TeleMessage dla platformy Microsoft 365 i uzyskaj prawidłowe konto administracyjne firmy. Aby uzyskać więcej informacji, zobacz [Order Microsoft 365 Mobile Archiving (Zamawianie archiwizacji urządzeń przenośnych platformy Microsoft 365).](https://www.telemessage.com/mobile-archiver/order-mobile-archiver-for-microsoft-365/)

- Zarejestruj wszystkich użytkowników, którzy wymagają archiwizacji weChat na koncie telemessage przy użyciu tego samego adresu e-mail, który jest używany dla konta microsoft 365 użytkownika.

- Musisz zainstalować aplikację Tencent WeCom na telefonach komórkowych użytkowników w organizacji i aktywować ją. Aplikacja WeCom umożliwia użytkownikom komunikowanie się i czatowanie z innymi użytkownikami WeChat i WeCom.

- Użytkownikowi, który tworzy łącznik Archiwum WeChat w portalu zgodności, należy przypisać rolę Administracja łącznika danych. Ta rola jest wymagana do dodawania łączników na stronie **Łączniki danych** w portalu zgodności. Ta rola jest domyślnie dodawana do wielu grup ról. Aby uzyskać listę tych grup ról, zobacz sekcję "Role w centrach zabezpieczeń i zgodności" w obszarze [Uprawnienia w Centrum zgodności & zabezpieczeń](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternatywnie administrator w organizacji może utworzyć niestandardową grupę ról, przypisać rolę Administracja łącznika danych, a następnie dodać odpowiednich użytkowników jako członków. Aby uzyskać instrukcje, zobacz sekcję "Tworzenie niestandardowej grupy ról" w obszarze [Uprawnienia w portal zgodności Microsoft Purview](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Ten łącznik danych telemessage jest dostępny w środowiskach GCC w chmurze microsoft 365 us government. Aplikacje i usługi innych firm mogą obejmować przechowywanie, przesyłanie i przetwarzanie danych klientów organizacji w systemach innych firm, które znajdują się poza infrastrukturą platformy Microsoft 365 i w związku z tym nie są objęte zobowiązaniami microsoft purview i ochrony danych. Firma Microsoft nie przedstawia żadnej reprezentacji, że użycie tego produktu do łączenia się z aplikacjami innych firm oznacza, że te aplikacje innych firm są zgodne z fedrampem.

## <a name="create-a-wechat-archiver-connector"></a>Tworzenie łącznika archiwum WeChat

Wykonaj kroki opisane w tej sekcji, aby utworzyć łącznik Archiwum WeChat w portalu zgodności. Łącznik korzysta z podanych informacji, aby nawiązać połączenie z witryną telemessage i przenieść dane komunikacji WeChat do odpowiednich skrzynek pocztowych użytkowników w usłudze Microsoft 365.

1. Przejdź do obszaru <https://compliance.microsoft.com> , a następnie kliknij pozycję **Łączniki** >  danych **WeChat Archiver**.

2. Na stronie Opis produktu **WeChat Archiver** kliknij pozycję **Dodaj łącznik**

3. Na stronie **Warunki korzystania z usługi** kliknij pozycję **Akceptuj**.

4. Na stronie **Logowanie do usługi TeleMessage** w obszarze Krok 3 wprowadź wymagane informacje w poniższych polach, a następnie kliknij przycisk **Dalej**.

    - **Nazwa użytkownika**: Nazwa użytkownika telemessage.

    - **Hasło**: Twoje hasło telemessage.

5. Po utworzeniu łącznika możesz zamknąć okno podręczne i przejść do następnej strony.

6. Na stronie **Mapowanie użytkownika** włącz automatyczne mapowanie użytkowników. Możesz również przekazać niestandardowy plik CSV mapowania użytkownika.

7. Kliknij **przycisk Dalej**, przejrzyj ustawienia, a następnie kliknij przycisk **Zakończ** , aby utworzyć łącznik.

8. Przejdź do karty **Łączniki** na stronie **Łączniki danych** , aby zobaczyć postęp procesu importowania nowego łącznika.

## <a name="known-issues"></a>Znane problemy

- Obecnie nie obsługujemy importowania załączników ani elementów o rozmiarze większym niż 10 MB. Obsługa większych elementów będzie dostępna w późniejszym terminie.
