---
title: Konfigurowanie łącznika do archiwizowania danych komunikacji sygnałowej w Microsoft 365
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
description: Administratorzy mogą skonfigurować łącznik TeleMessage do importowania i archiwizowania danych komunikacji sygnałowej w Microsoft 365. Umożliwia to archiwizowanie danych ze źródeł danych innych firm w Microsoft 365 dzięki czemu można używać funkcji zgodności, takich jak blokada prawna, wyszukiwanie zawartości i zasady przechowywania, aby zarządzać danymi innych firm w organizacji.
ms.openlocfilehash: f29d100a622bbe7d3d73e3e629a22b4768095a32
ms.sourcegitcommit: 9ba00298cfa9ae293e4a57650965fdb3e8ffe07b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/11/2022
ms.locfileid: "64760014"
---
# <a name="set-up-a-connector-to-archive-signal-communications-data"></a>Konfigurowanie łącznika do archiwizowania danych komunikacji sygnałowej

Użyj łącznika TeleMessage w Centrum zgodności platformy Microsoft 365, aby zaimportować i zarchiwizować czaty, załączniki, pliki oraz usunięte komunikaty i wywołania. Po skonfigurowaniu i skonfigurowaniu łącznika łączy się on z kontem telemessage organizacji i importuje komunikację mobilną pracowników przy użyciu archiwum sygnałów telemessage do skrzynek pocztowych w Microsoft 365.

Po zapisaniu danych łącznika usługi Signal Archiver w skrzynkach pocztowych użytkowników można zastosować Microsoft 365 funkcje zgodności, takie jak blokada postępowania sądowego, wyszukiwanie zawartości i zasady przechowywania Microsoft 365 do danych komunikacji sygnału. Możesz na przykład wyszukać komunikację sygnałową przy użyciu wyszukiwania zawartości lub skojarzyć skrzynkę pocztową zawierającą dane łącznika Usługi Signal Archiver z opiekunem w Advanced eDiscovery przypadku. Importowanie i archiwizowanie danych w Microsoft 365 przy użyciu łącznika usługi Signal Archiver może pomóc organizacji zachować zgodność z przepisami dotyczącymi ładu korporacyjnego i zasadami prawnymi.

## <a name="overview-of-archiving-signal-communications-data"></a>Omówienie archiwizacji danych komunikacji sygnału

W poniższym omówieniu wyjaśniono proces używania łącznika do archiwizowania danych komunikacji sygnału w Microsoft 365.

![Przepływ pracy archiwizacji komunikacji sygnału.](../media/SignalConnectorWorkflow.png)

1. Twoja organizacja współpracuje z usługą TeleMessage w celu skonfigurowania łącznika usługi Signal Archiver. Aby uzyskać więcej informacji, zobacz [Aktywowanie archiwizacji sygnałów telemessage dla Microsoft 365](https://www.telemessage.com/microsoft-365-activation-for-signal-archiver/).

2. W czasie rzeczywistym dane sygnału organizacji są kopiowane do witryny TeleMessage.

3. Łącznik Usługi Signal Archiver utworzony w Centrum zgodności platformy Microsoft 365 codziennie łączy się z witryną TeleMessage i przesyła wiadomości e-mail z poprzednich 24 godzin do bezpiecznego obszaru usługi Azure Storage w chmurze firmy Microsoft.

4. Łącznik importuje elementy komunikacji mobilnej do skrzynki pocztowej określonego użytkownika. Nowy folder o nazwie Signal Archiver zostanie utworzony w skrzynce pocztowej określonego użytkownika, a elementy zostaną do niego zaimportowane. Łącznik wykonuje mapowanie przy użyciu wartości właściwości *Adres e-mail użytkownika* . Każda wiadomość e-mail zawiera tę właściwość, która jest wypełniana adresem e-mail każdego uczestnika wiadomości e-mail.

   Oprócz automatycznego mapowania użytkownika przy użyciu wartości właściwości *Adres e-mail użytkownika* można również zdefiniować mapowanie niestandardowe, przekazując plik mapowania CSV. Ten plik mapowania powinien zawierać numer telefonu komórkowego użytkownika i odpowiedni adres skrzynki pocztowej Microsoft 365 dla każdego użytkownika. Jeśli włączysz automatyczne mapowanie użytkownika i udostępnisz mapowanie niestandardowe, dla każdego elementu wiadomości e-mail łącznik najpierw przyjrzy się niestandardowemu plikowi mapowania. Jeśli nie znajdzie prawidłowego Microsoft 365 użytkownika odpowiadającego numerowi telefonu komórkowego użytkownika, łącznik użyje właściwości adres e-mail użytkownika elementu wiadomości e-mail. Jeśli łącznik nie znajdzie prawidłowego Microsoft 365 użytkownika w niestandardowym pliku mapowania lub we właściwości *adresu e-mail użytkownika* elementu wiadomości e-mail, element nie zostanie zaimportowany.

## <a name="before-you-set-up-a-connector"></a>Przed skonfigurowaniem łącznika

- [Zamów usługę Signal Archiver z usługi TeleMessage i uzyskaj prawidłowe](https://www.telemessage.com/mobile-archiver/order-mobile-archiver-for-o365/) konto administracyjne dla swojej organizacji. Musisz zalogować się do tego konta podczas tworzenia łącznika w Centrum zgodności.

- Zarejestruj wszystkich użytkowników, którzy wymagają archiwizacji sygnału na koncie TeleMessage. Podczas rejestrowania użytkowników należy użyć tego samego adresu e-mail, który jest używany dla ich konta Microsoft 365.

- Zainstaluj aplikację Signal Archiver na telefonach komórkowych pracowników i aktywuj ją. Aplikacja Signal Archiver umożliwia im komunikowanie się i czatowanie z innymi użytkownikami usługi Signal.

- Użytkownikowi, który tworzy łącznik usługi Signal Archiver w kroku 3, należy przypisać rolę administratora łącznika danych. Ta rola jest wymagana do dodawania łączników na stronie **Łączniki danych** w Centrum zgodności platformy Microsoft 365. Ta rola jest domyślnie dodawana do wielu grup ról. Aby uzyskać listę tych grup ról, zobacz sekcję "Role w centrach zabezpieczeń i zgodności" w obszarze [Uprawnienia w Centrum zgodności & zabezpieczeń](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternatywnie administrator w organizacji może utworzyć niestandardową grupę ról, przypisać rolę administratora łącznika danych, a następnie dodać odpowiednich użytkowników jako członków. Aby uzyskać instrukcje, zobacz sekcję "Tworzenie niestandardowej grupy ról" w obszarze [Uprawnienia w Centrum zgodności platformy Microsoft 365](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Ten łącznik danych TeleMessage jest dostępny w środowiskach GCC w chmurze Microsoft 365 US Government. Aplikacje i usługi innych firm mogą obejmować przechowywanie, przesyłanie i przetwarzanie danych klientów organizacji w systemach innych firm, które znajdują się poza infrastrukturą Microsoft 365 i w związku z tym nie są objęte zobowiązaniami dotyczącymi zgodności Microsoft 365 i ochrony danych. Firma Microsoft nie przedstawia żadnej reprezentacji, że użycie tego produktu do łączenia się z aplikacjami innych firm oznacza, że te aplikacje innych firm są zgodne z fedrampem.

## <a name="create-a-signal-archiver-connector"></a>Tworzenie łącznika usługi Signal Archiver

Po ukończeniu wymagań wstępnych opisanych w poprzedniej sekcji możesz utworzyć łącznik Usługi Signal Archiver w Centrum zgodności platformy Microsoft 365. Łącznik używa podanych informacji w celu nawiązania połączenia z lokacją TeleMessage i przesyłania danych komunikacji sygnału do odpowiednich skrzynek pocztowych użytkownika w Microsoft 365.

1. Przejdź do obszaru <https://compliance.microsoft.com> , a następnie kliknij pozycję **Łączniki** >  **danychSignal Archiver**.

2. Na stronie Opis produktu **Signal Archiver** kliknij pozycję **Dodaj łącznik.**

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
