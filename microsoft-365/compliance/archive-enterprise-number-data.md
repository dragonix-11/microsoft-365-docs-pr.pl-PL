---
title: Konfigurowanie łącznika do archiwizowania danych z archiwizatora Enterprise numerów telemessage
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
description: Administratorzy mogą skonfigurować łącznik do importowania i archiwizowania danych programu SMS i MMS z usługi TeleMessage Enterprise Number Archiver. Dzięki temu można archiwizować dane ze źródeł danych innych firm w usłudze Microsoft Purview, aby można było zarządzać danymi innych firm za pomocą funkcji zgodności, takich jak archiwizowanie prawne, wyszukiwanie zawartości i zasady przechowywania.
ms.openlocfilehash: b3f429af6caa4d650688b27f5157a212e348ffe8
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2022
ms.locfileid: "64995057"
---
# <a name="set-up-a-connector-to-archive-enterprise-number-data"></a>Konfigurowanie łącznika do archiwizowania danych Enterprise Number

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Łącznik TeleMessage w portalu zgodności usługi Microsoft Purview umożliwia importowanie i archiwizowanie wiadomości SMS i wiadomości MMS (Multimedia Messaging Service), wiadomości czatu, nagrań połączeń głosowych i dzienników połączeń głosowych z archiwum numerów Enterprise. Po skonfigurowaniu i skonfigurowaniu łącznika łączy się on z kontem telemessage organizacji raz dziennie i importuje dane komunikacji mobilnej pracowników przy użyciu archiwum telemessage Enterprise number do skrzynek pocztowych w Microsoft 365.

Po zapisaniu danych łącznika TeleMessage Enterprise Number Archiver w skrzynkach pocztowych użytkowników można zastosować funkcje usługi Microsoft Purview, takie jak blokada postępowania sądowego, wyszukiwanie zawartości, archiwizowanie In-Place, inspekcja, zgodność z komunikacją i zasady przechowywania Microsoft 365 w celu Enterprise danych archiwizatora numerów. Możesz na przykład wyszukać Enterprise TeleMessage Number Archiver SMS, MMS i Voice Call przy użyciu wyszukiwania zawartości lub skojarzyć skrzynkę pocztową zawierającą dane łącznika Enterprise Number Archiver z opiekunem w przypadku zbierania elektronicznych materiałów dowodowych (Premium). Użycie łącznika Enterprise Number Archiver do importowania i archiwizowania danych w Microsoft 365 może pomóc twojej organizacji zachować zgodność z zasadami rządowymi i regulacyjnymi.

## <a name="overview-of-archiving-enterprise-number-data"></a>Omówienie archiwizacji danych Enterprise Number

W poniższym omówieniu wyjaśniono proces korzystania z łącznika do archiwizowania danych sieci Enterprise w Microsoft 365.

![Enterprise przepływu pracy archiwizacji numerów.](../media/EnterpriseNumberConnectorWorkflow.png)

1. Twoja organizacja współpracuje z usługą TeleMessage w celu skonfigurowania łącznika Enterprise Number Archiver. Aby uzyskać więcej informacji, zobacz [tutaj](https://www.telemessage.com/office365-activation-for-enterprise-number-archiver/).

2. Łącznik Enterprise Number Archiver tworzony w portalu zgodności codziennie łączy się z witryną TeleMessage i przesyła wiadomości e-mail z poprzednich 24 godzin do bezpiecznego obszaru usługi Azure Storage w chmurze firmy Microsoft.

3. Łącznik importuje elementy komunikacji mobilnej do skrzynki pocztowej określonego użytkownika. Nowy folder o nazwie Enterprise Number Archiver jest tworzony w skrzynce pocztowej określonego użytkownika, a elementy są do niego importowane. Łącznik wykonuje mapowanie przy użyciu wartości właściwości *Adres e-mail użytkownika* . Każda wiadomość e-mail zawiera tę właściwość, która jest wypełniana adresem e-mail każdego uczestnika wiadomości e-mail. Oprócz automatycznego mapowania użytkownika przy użyciu wartości właściwości *Adres e-mail użytkownika* można również zdefiniować mapowanie niestandardowe, przekazując plik mapowania CSV. Ten plik mapowania powinien zawierać numer telefonu komórkowego użytkownika i odpowiedni adres skrzynki pocztowej Microsoft 365 dla każdego użytkownika. Jeśli włączysz automatyczne mapowanie użytkownika i udostępnisz mapowanie niestandardowe, dla każdego elementu wiadomości e-mail łącznik najpierw przyjrzy się niestandardowemu plikowi mapowania. Jeśli nie znajdzie prawidłowego Microsoft 365 użytkownika odpowiadającego numerowi telefonu komórkowego użytkownika, łącznik użyje właściwości adres e-mail użytkownika elementu wiadomości e-mail. Jeśli łącznik nie znajdzie prawidłowego Microsoft 365 użytkownika w niestandardowym pliku mapowania lub we właściwości *adresu e-mail użytkownika* elementu wiadomości e-mail, element nie zostanie zaimportowany.

## <a name="before-you-set-up-a-connector"></a>Przed skonfigurowaniem łącznika

Niektóre kroki implementacji wymagane do zarchiwizowania danych Enterprise Archiwum numerów są zewnętrzne dla Microsoft 365 i muszą zostać ukończone przed utworzeniem łącznika w centrum zgodności.

- [Zamów usługę Enterprise Number Archiver z usługi TeleMessage i uzyskaj prawidłowe](https://www.telemessage.com/mobile-archiver/order-mobile-archiver-for-o365) konto administracyjne dla swojej organizacji. Musisz zalogować się do tego konta podczas tworzenia łącznika w Centrum zgodności.

- Zarejestruj wszystkich użytkowników, którzy wymagają archiwizacji sieci Enterprise Numer SMS/MMS na koncie TeleMessage. Podczas rejestrowania użytkowników należy użyć tego samego adresu e-mail, który jest używany dla ich konta Microsoft 365.

- Zainstaluj i aktywuj aplikację TeleMessage Enterprise Number Archiver na telefonach komórkowych pracowników.

- Użytkownik, który tworzy łącznik Enterprise Number Archiver, musi mieć przypisaną rolę administratora łącznika danych. Ta rola jest wymagana do dodawania łączników na stronie **Łączniki danych** w portalu zgodności. Ta rola jest domyślnie dodawana do wielu grup ról. Aby uzyskać listę tych grup ról, zobacz sekcję "Role w centrach zabezpieczeń i zgodności" w obszarze [Uprawnienia w Centrum zgodności & zabezpieczeń](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternatywnie administrator w organizacji może utworzyć niestandardową grupę ról, przypisać rolę administratora łącznika danych, a następnie dodać odpowiednich użytkowników jako członków. Aby uzyskać instrukcje, zobacz sekcję "Tworzenie niestandardowej grupy ról" w obszarze [Uprawnienia w portalu zgodności usługi Microsoft Purview](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Ten łącznik danych TeleMessage jest dostępny w środowiskach GCC w chmurze Microsoft 365 US Government. Aplikacje i usługi innych firm mogą obejmować przechowywanie, przesyłanie i przetwarzanie danych klientów organizacji w systemach innych firm, które znajdują się poza infrastrukturą Microsoft 365 i dlatego nie są objęte zobowiązaniami dotyczącymi usługi Microsoft Purview i ochrony danych. Firma Microsoft nie przedstawia żadnej reprezentacji, że użycie tego produktu do łączenia się z aplikacjami innych firm oznacza, że te aplikacje innych firm są zgodne z fedrampem.

## <a name="create-an-enterprise-number-archiver-connector"></a>Tworzenie łącznika Enterprise Number Archiver

Po ukończeniu wymagań wstępnych opisanych w poprzedniej sekcji możesz utworzyć łącznik Enterprise Number Archiver w portalu zgodności. Łącznik używa podanych informacji w celu nawiązania połączenia z witryną TeleMessage i przeniesienia wiadomości SMS, MMS i połączeń głosowych do odpowiednich skrzynek pocztowych użytkownika w Microsoft 365.

1. Przejdź do obszaru [https://compliance.microsoft.com](https://compliance.microsoft.com/) , a następnie kliknij pozycję **Łączniki danych** **Enterprise Archiwum numerów**\>.

2. Na stronie **opisu produktu Enterprise Number Archiver** kliknij pozycję **Dodaj łącznik**

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