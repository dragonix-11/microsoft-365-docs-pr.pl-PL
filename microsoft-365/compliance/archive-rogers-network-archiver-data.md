---
title: Konfigurowanie łącznika do archiwizowania danych sieciowych w programie Microsoft 365
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
description: Administratorzy mogą skonfigurować łącznik TeleMessage w celu importowania i archiwizowania danych sieciowych Aplikacji Microsoft 365. Dzięki temu można archiwizować dane ze źródeł danych innych firm w programie Microsoft 365, aby zarządzać danymi innych firm przy użyciu funkcji zgodności, takich jak archiwizacja ze względu na przepisy prawne, wyszukiwanie zawartości i zasady przechowywania.
ms.openlocfilehash: 7ff260640606a2870cefca0de5e8b833018760cc
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63328263"
---
# <a name="set-up-a-connector-to-archive-rogers-network-data"></a>Konfigurowanie łącznika do archiwizowania danych sieciowych Przez Użytkownika

Użyj łącznika TeleMessage w p Centrum zgodności platformy Microsoft 365 i zarchiwizuj dane SMS-ów i MMS z sieci komórkowej Wi-Fi. Po skonfigurowaniu łącznika archiwum sieciowej [Firmy Grzegorzs](https://www.telemessage.com/mobile-archiver/network-archiver/rogers/) łączy się z siecią komórkową organizacji i importuje dane wiadomości SMS i MMS do skrzynek pocztowych w programie Microsoft 365.

Po zapisaniu danych z sieci komórkowej Grzegorzs w skrzynkach pocztowych użytkowników możesz zastosować do danych funkcje zgodności usługi Microsoft 365, takie jak Zawieszenie w związku z postępowaniem sądowym, Wyszukiwanie zawartości i Microsoft 365 przechowywania. Można na przykład wyszukiwać wiadomości SMS i MMS z sieci komórkowej Grzegorz przy użyciu wyszukiwania zawartości lub wyszukiwania skojarzonego ze sprawą Core eDiscovery. Importowanie i archiwizowanie danych w programie Microsoft 365 za pomocą łącznika archiwum sieci firmy Grzegorze może ułatwić organizacji zgodność z przepisami prawa dotyczącymi ładu korporacyjnego i przepisami prawnymi.

## <a name="overview-of-archiving-rogers-mobile-network-data"></a>Omówienie archiwizowania danych sieci komórkowej aplikacji Federowanie

Poniższe omówienie przedstawia proces używania łącznika do archiwizowania danych SMS-ów i MMS w Microsoft 365.

![Przepływ pracy archiwizowania sieci.](../media/RogersNetworkConnectorWorkflow.png)

1. Twoja organizacja korzysta z programu TeleMessage w celu skonfigurowania łącznika archiwum sieciowego w firmie Apple. Aby uzyskać więcej informacji, zobacz [Aktywowanie archiwum sieciowego TeleMessage dla Microsoft 365](https://www.telemessage.com/microsoft-365-activation-for-the-rogers-network-archiver/).

2. W czasie rzeczywistym dane z sieci komórkowej firmy Apple są kopiowane do witryny TeleMessage.

3. Łącznik archiver sieci Grzegorzs, który tworzysz w usłudze Centrum zgodności platformy Microsoft 365, łączy się z witryną TeleMessage każdego dnia i przesyła wiadomości e-mail z poprzednich 24 godzin do bezpiecznego obszaru usługi Azure Storage w chmurze firmy Microsoft.

4. Łącznik importuje elementy komunikacji mobilnej do skrzynki pocztowej określonego użytkownika. W skrzynce pocztowej określonego użytkownika zostanie utworzony nowy folder o nazwie Grzegorz SMS/MMS Network Archiver, a elementy zostaną do niego zaimportowane. Łącznik obsługuje mapowanie przy użyciu wartości właściwości *Adres e-mail* użytkownika. Każda wiadomość e-mail zawiera tę właściwość, która jest wypełniana adresem e-mail każdego uczestnika wiadomości e-mail.

   Oprócz automatycznego mapowania użytkowników przy użyciu wartości właściwości Adres e-mail użytkownika możesz również zdefiniować mapowanie niestandardowe, przesyłając plik mapowania plików CSV. Ten plik mapowania powinien zawierać numer telefonu komórkowego użytkownika i odpowiadający mu adres Microsoft 365 pocztowej dla każdego użytkownika. Jeśli włączysz automatyczne mapowanie użytkowników i udostępnisz mapowanie niestandardowe, dla każdego elementu poczty e-mail łącznik najpierw przyjrzy się plikowi mapowania niestandardowego. Jeśli użytkownik nie znajdzie prawidłowego Microsoft 365 odpowiadającego numerowi telefonu komórkowego użytkownika, łącznik użyje właściwości adresu e-mail użytkownika elementu poczty e-mail. Jeśli łącznik nie znajdzie prawidłowego użytkownika Microsoft 365 w pliku mapowania niestandardowego lub właściwości adresu e-mail użytkownika elementu poczty  e-mail, element nie zostanie zaimportowany.

## <a name="before-you-set-up-a-connector"></a>Przed skonfigurowaniem łącznika

- [Zamów usługę Archiver sieci w aplikacji TeleMessage](https://www.telemessage.com/mobile-archiver/order-mobile-archiver-for-o365/) i uzyskaj prawidłowe konto administracyjne dla twojej organizacji. Podczas tworzenia łącznika w centrum zgodności musisz zalogować się do tego konta.

- Zarejestruj wszystkich użytkowników wymagających archiwizacji w sieci firmy Apple na koncie usługi TeleMessage. Podczas rejestrowania użytkowników pamiętaj, aby używać tego samego adresu e-mail, który jest używany na ich Microsoft 365 kontach.

- Pracownicy muszą posiadać firmowe i firmowe telefony komórkowe w sieci komórkowej O2. Archiwizowanie wiadomości w Microsoft 365 jest niedostępne w przypadku urządzeń należących do pracownika lub "Przynieź własne urządzenia (BYOD).

- Uzyskaj dane konta i kontaktu rozliczeniowego dla organizacji, aby móc wypełnić formularze dołączania i zamówić usługę archiwizacji wiadomości od Użytkownika.

- Użytkownik, który tworzy łącznik archiwum sieci w kroku 3, musi mieć przypisaną rolę administratora łącznika danych. Ta rola jest wymagana do dodawania łączników na **stronie Łączniki** danych w Centrum zgodności platformy Microsoft 365. Ta rola jest domyślnie dodawana do wielu grup ról. Aby uzyskać listę tych grup ról, zobacz sekcję "Role w centrach zabezpieczeń i zgodności" w sekcji Uprawnienia w Centrum zabezpieczeń & [zgodności](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Administrator w organizacji może również utworzyć niestandardową grupę ról, przypisać rolę administrator łącznika danych, a następnie dodać odpowiednich użytkowników jako członków. Aby uzyskać instrukcje, zobacz sekcję "Tworzenie niestandardowej grupy ról" w sekcji Uprawnienia [w Centrum zgodności platformy Microsoft 365](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Ten łącznik danych TeleMessage jest dostępny w GCC w chmurze dla instytucji rządowych Microsoft 365 USA. Aplikacje i usługi innych firm mogą obejmować przechowywanie, przekazywanie i przetwarzanie danych klienta Organizacji w systemach innych firm, które znajdują się poza infrastrukturą firmy Microsoft 365 i dlatego nie są objęte zobowiązaniami firmy Microsoft 365 w zakresie zgodności z przepisami i ochrony danych. Firma Microsoft nie zapewnia, że używanie tego produktu do łączenia się z aplikacjami innych firm oznacza, że te aplikacje innych firm są zgodne z fedRAMP.

## <a name="create-a-rogers-network-archiver-connector"></a>Tworzenie łącznika archiwum sieciowego Dla firmy Federator

Po wyliczaniu wymagań wstępnych opisanych w poprzedniej sekcji można utworzyć łącznik Archiwum sieci firmy Grzegorze w Centrum zgodności platformy Microsoft 365. Łącznik używa podanej informacji w celu nawiązania połączenia z witryną TeleMessage i przeniesienia danych Aplikacji Sms/MMS do odpowiednich skrzynek pocztowych użytkowników w Microsoft 365.

1. Przejdź do, <https://compliance.microsoft.com> a następnie kliknij pozycję **Łączniki** **danychArchiwizator** >  sieciowy.

2. Na stronie **opisowej produktu Archiwum sieci Firmy Federer** kliknij pozycję **Dodaj łącznik**.

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
