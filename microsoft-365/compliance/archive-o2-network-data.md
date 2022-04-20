---
title: Konfigurowanie łącznika do archiwizowania danych sieci O2 w Microsoft 365
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: 04/06/2022
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
description: Administratorzy mogą skonfigurować łącznik TeleMessage do importowania i archiwizowania danych programu SMS i MMS z sieci komórkowej O2 w Microsoft 365. Umożliwia to archiwizowanie danych ze źródeł danych innych firm w Microsoft 365 dzięki czemu można używać funkcji zgodności, takich jak blokada prawna, wyszukiwanie zawartości i zasady przechowywania, aby zarządzać danymi innych firm w organizacji.
ms.openlocfilehash: 5e802aab643fc795191344f22512f073bd1785fc
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2022
ms.locfileid: "64944090"
---
# <a name="set-up-a-connector-to-archive-o2-network-data"></a>Konfigurowanie łącznika do archiwizowania danych sieci O2

Użyj łącznika TeleMessage w portalu zgodności usługi Microsoft Purview, aby zaimportować i zarchiwizować wiadomości sms oraz połączenia głosowe z sieci komórkowej usługi O2. Po skonfigurowaniu i skonfigurowaniu łącznika łączy się on z siecią O2 w organizacji raz dziennie i importuje wiadomości SMS i połączenia głosowe do skrzynek pocztowych w Microsoft 365.

Po zapisaniu wiadomości SMS i połączeń głosowych w skrzynkach pocztowych użytkowników można zastosować funkcje usługi Microsoft Purview, takie jak blokada postępowania sądowego, wyszukiwanie zawartości i zasady przechowywania Microsoft 365 do danych sieci O2. Na przykład możesz wyszukiwać wiadomości SMS i połączenia głosowe sieci O2 przy użyciu wyszukiwania zawartości lub skojarzyć skrzynkę pocztową zawierającą dane sieci O2 z opiekunem w przypadku zbierania elektronicznych materiałów dowodowych (Premium). Importowanie i archiwizowanie danych w Microsoft 365 przy użyciu łącznika sieci O2 może pomóc twojej organizacji zachować zgodność z zasadami rządowymi i regulacyjnymi.

## <a name="overview-of-archiving-o2-network-data"></a>Omówienie archiwizacji danych sieci O2

W poniższym omówieniu wyjaśniono proces korzystania z łącznika do archiwizowania danych sieci O2 w Microsoft 365.

![Przepływ pracy archiwizacji sieci O2.](../media/O2NetworkConnectorWorkflow.png)

1. Twoja organizacja współpracuje z usługami TeleMessage i O2 w celu skonfigurowania łącznika sieci O2. Aby uzyskać więcej informacji, zobacz [Archiwum sieci O2](https://www.telemessage.com/office365-activation-for-o2-network-archiver).

2. Raz na 24 godziny wiadomości SMS i połączenia głosowe z sieci O2 organizacji są kopiowane do witryny TeleMessage.

3. Łącznik sieci O2 tworzony w portalu zgodności codziennie łączy się z witryną TeleMessage i przesyła wiadomości SMS i połączenia głosowe z poprzednich 24 godzin do bezpiecznej lokalizacji Storage platformy Azure w chmurze firmy Microsoft. Łącznik konwertuje również zawartość wiadomości SMS i połączeń głosowych na format wiadomości e-mail.

4. Łącznik importuje elementy komunikacji mobilnej do skrzynki pocztowej określonych użytkowników. Nowy folder o nazwie **O2 SMS i Voice Network Archiver** jest tworzony w skrzynce pocztowej określonego użytkownika, a elementy są do niego importowane. Łącznik wykonuje to mapowanie przy użyciu wartości właściwości *Adres e-mail użytkownika* . Każda wiadomość SMS i połączenie głosowe zawierają tę właściwość, która jest wypełniana adresem e-mail każdego uczestnika wiadomości.

   Oprócz automatycznego mapowania użytkownika przy użyciu wartości właściwości *Adres e-mail użytkownika* można również zdefiniować mapowanie niestandardowe, przekazując plik mapowania CSV. Ten plik mapowania zawiera numer telefonu komórkowego i odpowiadający Microsoft 365 adres e-mail dla użytkowników w organizacji. Jeśli włączysz automatyczne mapowanie użytkowników i mapowanie niestandardowe, dla każdego elementu O2 łącznik najpierw przyjrzy się niestandardowemu plikowi mapowania. Jeśli nie znajdzie prawidłowego użytkownika Microsoft 365, który odpowiada numerowi telefonu komórkowego użytkownika, łącznik użyje wartości we właściwości adresu e-mail elementu, który próbuje zaimportować. Jeśli łącznik nie znajdzie prawidłowego użytkownika Microsoft 365 w niestandardowym pliku mapowania lub we właściwości adresu e-mail elementu O2, element nie zostanie zaimportowany.

## <a name="before-you-set-up-a-connector"></a>Przed skonfigurowaniem łącznika

Niektóre kroki implementacji wymagane do zarchiwizowania danych sieci O2 są zewnętrzne dla Microsoft 365 i muszą zostać ukończone przed utworzeniem łącznika w centrum zgodności.

- [Zamów usługę Archiwum sieci O2 z usługi TeleMessage i uzyskaj prawidłowe](https://www.telemessage.com/mobile-archiver/order-mobile-archiver-for-o365/) konto administracyjne dla swojej organizacji. Musisz zalogować się do tego konta podczas tworzenia łącznika w Centrum zgodności.

- Uzyskaj swoje konto sieci O2 i dane kontaktowe dotyczące rozliczeń, aby można było wypełnić formularze dołączania usługi TeleMessage i zamówić usługę archiwizacji komunikatów w usłudze O2.

- Zarejestruj wszystkich użytkowników, którzy wymagają archiwizacji usługi O2 SMS i Voice Network na koncie TeleMessage. Podczas rejestrowania użytkowników należy użyć tego samego adresu e-mail, który jest używany dla ich konta Microsoft 365.

- Pracownicy muszą mieć firmowe i firmowe telefony komórkowe w sieci komórkowej O2. Archiwizowanie komunikatów w Microsoft 365 nie jest dostępne dla urządzeń należących do pracowników lub "Przynieś własne urządzenia (BYOD).

- Użytkownik, który tworzy łącznik sieci O2, musi mieć przypisaną rolę administratora łącznika danych. Ta rola jest wymagana do dodawania łączników na stronie **Łączniki danych** w portalu zgodności. Ta rola jest domyślnie dodawana do wielu grup ról. Aby uzyskać listę tych grup ról, zobacz sekcję "Role w centrach zabezpieczeń i zgodności" w obszarze [Uprawnienia w Centrum zgodności & zabezpieczeń](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternatywnie administrator w organizacji może utworzyć niestandardową grupę ról, przypisać rolę administratora łącznika danych, a następnie dodać odpowiednich użytkowników jako członków. Aby uzyskać instrukcje, zobacz sekcję "Tworzenie niestandardowej grupy ról" w obszarze [Uprawnienia w portalu zgodności usługi Microsoft Purview](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Ten łącznik danych TeleMessage jest dostępny w środowiskach GCC w chmurze Microsoft 365 US Government. Aplikacje i usługi innych firm mogą obejmować przechowywanie, przesyłanie i przetwarzanie danych klientów organizacji w systemach innych firm, które znajdują się poza infrastrukturą Microsoft 365 i dlatego nie są objęte zobowiązaniami dotyczącymi usługi Microsoft Purview i ochrony danych. Firma Microsoft nie przedstawia żadnej reprezentacji, że użycie tego produktu do łączenia się z aplikacjami innych firm oznacza, że te aplikacje innych firm są zgodne z fedrampem.

## <a name="create-an-o2-network-connector"></a>Tworzenie łącznika sieci O2

Po ukończeniu wymagań wstępnych opisanych w poprzedniej sekcji możesz utworzyć łącznik sieci O2 w portalu zgodności. Łącznik używa podanych informacji, aby nawiązać połączenie z witryną TeleMessage i przenieść wiadomości SMS i połączenia głosowe do odpowiednich skrzynek pocztowych użytkownika w Microsoft 365.

1. Przejdź do obszaru [https://compliance.microsoft.com](https://compliance.microsoft.com/) , a następnie kliknij pozycję **Łączniki** \> danych **O2 Network**.

2. Na stronie Opis produktu **sieci O2** kliknij pozycję **Dodaj łącznik**

3. Na stronie **Warunki korzystania z usługi** kliknij pozycję **Akceptuj**.

4. Na stronie **Logowanie do usługi TeleMessage** w obszarze Krok 3 wprowadź wymagane informacje w poniższych polach, a następnie kliknij przycisk **Dalej**.

   - **Nazwę użytkownika:** Nazwa użytkownika usługi TeleMessage.

   - **Hasło:** Twoje hasło telemessage.

5. Po utworzeniu łącznika możesz zamknąć okno podręczne i przejść do następnej strony.

6. Na stronie **Mapowanie użytkownika** włącz automatyczne mapowanie użytkownika i kliknij przycisk **Dalej**. Jeśli potrzebujesz mapowania niestandardowego, przekaż plik CSV, a następnie kliknij przycisk **Dalej**.

7. Przejrzyj ustawienia, a następnie kliknij przycisk **Zakończ** , aby utworzyć łącznik.

8. Przejdź do karty Łączniki na stronie **Łączniki danych** , aby zobaczyć postęp procesu importowania nowego łącznika.

## <a name="known-issues"></a>Znane problemy

- Obecnie nie obsługujemy importowania załączników ani elementów o rozmiarze większym niż 10 MB. Obsługa większych elementów będzie dostępna w późniejszym terminie.