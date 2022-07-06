---
title: Konfigurowanie łącznika do archiwizowania danych z archiwum numerów przedsiębiorstwa usługi TeleMessage
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
description: Administratorzy mogą skonfigurować łącznik do importowania i archiwizowania danych PROGRAMU SMS i MMS z archiwizatora numerów przedsiębiorstwa usługi TeleMessage. Dzięki temu można archiwizować dane ze źródeł danych innych firm w usłudze Microsoft Purview, aby można było zarządzać danymi innych firm za pomocą funkcji zgodności, takich jak archiwizowanie prawne, wyszukiwanie zawartości i zasady przechowywania.
ms.openlocfilehash: 8adefbe03a2202dd88b8114dbfbcf033b4bf3844
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66631464"
---
# <a name="set-up-a-connector-to-archive-enterprise-number-data"></a>Konfigurowanie łącznika do archiwizowania danych numerów przedsiębiorstwa

Użyj łącznika TeleMessage w portal zgodności Microsoft Purview, aby zaimportować i zarchiwizować komunikaty usługi Short Messaging Service (SMS) i mms (Multimedia Messaging Service), wiadomości czatu, nagrania połączeń głosowych i dzienniki połączeń głosowych z archiwum numerów przedsiębiorstwa. Po skonfigurowaniu i skonfigurowaniu łącznika łączy się on z kontem telemessage organizacji raz dziennie i importuje dane komunikacji mobilnej pracowników przy użyciu archiwum numerów przedsiębiorstwa telemessage do skrzynek pocztowych na platformie Microsoft 365.

Po zapisaniu danych łącznika TeleMessage Enterprise Number Archiver w skrzynkach pocztowych użytkowników można zastosować funkcje usługi Microsoft Purview, takie jak blokada postępowania sądowego, wyszukiwanie zawartości, archiwizowanie In-Place, inspekcja, zgodność z komunikacją i zasady przechowywania usługi Microsoft 365 do danych archiwizatora numerów przedsiębiorstwa. Możesz na przykład wyszukać adres SMS, MMS i połączenie głosowe usługi TeleMessage Enterprise Number Archiver przy użyciu funkcji wyszukiwania zawartości lub skojarzyć skrzynkę pocztową zawierającą dane łącznika Archiwum numerów przedsiębiorstwa z opiekunem w przypadku zbierania elektronicznych materiałów dowodowych (Premium). Importowanie i archiwizowanie danych w usłudze Microsoft 365 przy użyciu łącznika Archiwum numerów przedsiębiorstwa może pomóc organizacji zachować zgodność z zasadami rządowymi i regulacyjnymi.

## <a name="overview-of-archiving-enterprise-number-data"></a>Omówienie archiwizacji danych numerów przedsiębiorstwa

W poniższym omówieniu wyjaśniono proces używania łącznika do archiwizowania danych usługi Enterprise Network na platformie Microsoft 365.

![Przepływ pracy archiwizacji numerów przedsiębiorstwa.](../media/EnterpriseNumberConnectorWorkflow.png)

1. Twoja organizacja współpracuje z usługą TeleMessage w celu skonfigurowania łącznika Archiwum numerów przedsiębiorstwa. Aby uzyskać więcej informacji, zobacz [tutaj](https://www.telemessage.com/office365-activation-for-enterprise-number-archiver/).

2. Łącznik Archiwum numerów przedsiębiorstwa tworzony w portalu zgodności codziennie łączy się z witryną TeleMessage i przesyła wiadomości e-mail z poprzednich 24 godzin do bezpiecznego obszaru usługi Azure Storage w chmurze firmy Microsoft.

3. Łącznik importuje elementy komunikacji mobilnej do skrzynki pocztowej określonego użytkownika. Nowy folder o nazwie Enterprise Number Archiver zostanie utworzony w skrzynce pocztowej określonego użytkownika i elementy zostaną do niego zaimportowane. Łącznik wykonuje mapowanie przy użyciu wartości właściwości *Adres e-mail użytkownika* . Każda wiadomość e-mail zawiera tę właściwość, która jest wypełniana adresem e-mail każdego uczestnika wiadomości e-mail. Oprócz automatycznego mapowania użytkownika przy użyciu wartości właściwości *Adres e-mail użytkownika* można również zdefiniować mapowanie niestandardowe, przekazując plik mapowania CSV. Ten plik mapowania powinien zawierać numer telefonu komórkowego użytkownika i odpowiedni adres skrzynki pocztowej platformy Microsoft 365 dla każdego użytkownika. Jeśli włączysz automatyczne mapowanie użytkownika i udostępnisz mapowanie niestandardowe, dla każdego elementu wiadomości e-mail łącznik najpierw przyjrzy się niestandardowemu plikowi mapowania. Jeśli nie znajdzie prawidłowego użytkownika platformy Microsoft 365, który odpowiada numerowi telefonu komórkowego użytkownika, łącznik użyje właściwości adres e-mail użytkownika elementu poczty e-mail. Jeśli łącznik nie znajdzie prawidłowego użytkownika platformy Microsoft 365 w niestandardowym pliku mapowania lub we właściwości *adresu e-mail użytkownika* elementu poczty e-mail, element nie zostanie zaimportowany.

## <a name="before-you-set-up-a-connector"></a>Przed skonfigurowaniem łącznika

Niektóre kroki implementacji wymagane do zarchiwizowania danych archiwum numerów przedsiębiorstwa są zewnętrzne dla platformy Microsoft 365 i muszą zostać ukończone przed utworzeniem łącznika w Centrum zgodności.

- [Zamów usługę Enterprise Number Archiver z usługi TeleMessage i uzyskaj prawidłowe](https://www.telemessage.com/mobile-archiver/order-mobile-archiver-for-o365) konto administracyjne dla swojej organizacji. Musisz zalogować się do tego konta podczas tworzenia łącznika w Centrum zgodności.

- Zarejestruj wszystkich użytkowników, którzy wymagają archiwizacji sieci SMS/MMS numerów przedsiębiorstwa na koncie telemessage. Podczas rejestrowania użytkowników należy użyć tego samego adresu e-mail, który jest używany dla ich konta platformy Microsoft 365.

- Zainstaluj i aktywuj aplikację TeleMessage Enterprise Number Archiver na telefonach komórkowych pracowników.

- Użytkownikowi tworzącemu łącznik archiwum numerów przedsiębiorstwa musi zostać przypisana rola Administracja łącznika danych. Ta rola jest wymagana do dodawania łączników na stronie **Łączniki danych** w portalu zgodności. Ta rola jest domyślnie dodawana do wielu grup ról. Aby uzyskać listę tych grup ról, zobacz sekcję "Role w centrach zabezpieczeń i zgodności" w obszarze [Uprawnienia w Centrum zgodności & zabezpieczeń](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternatywnie administrator w organizacji może utworzyć niestandardową grupę ról, przypisać rolę Administracja łącznika danych, a następnie dodać odpowiednich użytkowników jako członków. Aby uzyskać instrukcje, zobacz sekcję "Tworzenie niestandardowej grupy ról" w obszarze [Uprawnienia w portal zgodności Microsoft Purview](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Ten łącznik danych telemessage jest dostępny w środowiskach GCC w chmurze microsoft 365 us government. Aplikacje i usługi innych firm mogą obejmować przechowywanie, przesyłanie i przetwarzanie danych klientów organizacji w systemach innych firm, które znajdują się poza infrastrukturą platformy Microsoft 365 i w związku z tym nie są objęte zobowiązaniami microsoft purview i ochrony danych. Firma Microsoft nie przedstawia żadnej reprezentacji, że użycie tego produktu do łączenia się z aplikacjami innych firm oznacza, że te aplikacje innych firm są zgodne z fedrampem.

## <a name="create-an-enterprise-number-archiver-connector"></a>Tworzenie łącznika archiwizatora numerów przedsiębiorstwa

Po ukończeniu wymagań wstępnych opisanych w poprzedniej sekcji możesz utworzyć łącznik Archiwum numerów przedsiębiorstwa w portalu zgodności. Łącznik używa podanych informacji w celu nawiązania połączenia z witryną TeleMessage i przeniesienia wiadomości SMS, MMS i połączeń głosowych do odpowiednich skrzynek pocztowych użytkownika w usłudze Microsoft 365.

1. Przejdź do obszaru [https://compliance.microsoft.com](https://compliance.microsoft.com/) , a następnie kliknij pozycję **Łączniki danych** **— archiwizator numerów**\> przedsiębiorstwa.

2. Na stronie Opis produktu **Enterprise Number Archiver** kliknij pozycję **Dodaj łącznik**

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