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
description: Administratorzy mogą skonfigurować łącznik TeleMessage w celu importowania i archiwizowania danych komunikacji sygnałowej w Microsoft 365. Dzięki temu można archiwizować dane ze źródeł danych innych firm w programie Microsoft 365, aby zarządzać danymi innych firm przy użyciu funkcji zgodności, takich jak archiwizacja ze względu na przepisy prawne, wyszukiwanie zawartości i zasady przechowywania.
ms.openlocfilehash: 57c8fc5a6c3de5f6c8d376f8dfddd360f2627395
ms.sourcegitcommit: 36a19d80fe3f053df0fec398a7ff2dfc777f9730
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/30/2021
ms.locfileid: "63020783"
---
# <a name="set-up-a-connector-to-archive-signal-communications-data"></a>Konfigurowanie łącznika do archiwizowania danych komunikacji sygnałowej

Użyj łącznika TeleMessage w aplikacji Centrum zgodności platformy Microsoft 365 do importowania i archiwizowania czatów sygnałowych, załączników, plików oraz usuniętych wiadomości i połączeń. Po skonfigurowaniu i skonfigurowaniu łącznika połączy się on z kontem teleMessage Twojej organizacji i zaim importuje komunikację mobilną pracowników za pomocą funkcji Archiwum sygnału TeleMessage do skrzynek pocztowych w Microsoft 365.

Po zapisaniu danych łącznika programu Signal Archiver w skrzynkach pocztowych użytkowników możesz zastosować funkcje zgodności usługi Microsoft 365, takie jak archiwizacja w związku z postępowaniem sądowym, przeszukiwanie zawartości i zasady przechowywania Microsoft 365, aby zasygnalizować dane komunikacji. Na przykład możesz przeszukać komunikację sygnałową przy użyciu wyszukiwania zawartości lub skojarzyć skrzynkę pocztową zawierającą dane łącznika archiwizy sygnału ze współpracownikiem w Advanced eDiscovery przypadku. Importowanie i archiwizowanie danych w programie Microsoft 365 za pomocą łącznika archiwum sygnału może ułatwić organizacji pozostawanie w zrównaniu z przepisami dotyczącymi ładu korporacyjnego i zasadami prawnymi.

## <a name="overview-of-archiving-signal-communications-data"></a>Omówienie archiwizowania danych komunikacji sygnałowej

W poniższym o omówieniem wyjaśniono proces używania łącznika do archiwizowania danych komunikacji sygnałowej w Microsoft 365.

![Przepływ pracy archiwizacji komunikacji sygnałowej.](../media/SignalConnectorWorkflow.png)

1. Twoja organizacja współpracuje z usługą TeleMessage w celu skonfigurowania łącznika signal Archiver. Aby uzyskać więcej informacji, zobacz [Aktywowanie archiwum sygnału telemessage dla Microsoft 365](https://www.telemessage.com/microsoft-365-activation-for-signal-archiver/).

2. W czasie rzeczywistym dane sygnału organizacji są kopiowane do witryny TeleMessage.

3. Łącznik Signal Archiver (Archiwator sygnału) tworzyć w aplikacji Centrum zgodności platformy Microsoft 365 łączy się z witryną TeleMessage codziennie i przenosi wiadomości e-mail z poprzednich 24 godzin do bezpiecznego obszaru usługi Azure Storage w chmurze firmy Microsoft.

4. Łącznik importuje elementy komunikacji mobilnej do skrzynki pocztowej określonego użytkownika. W skrzynce pocztowej określonego użytkownika zostanie utworzony nowy folder o nazwie Signal Archiver, a elementy zostaną do niego zaimportowane. Łącznik obsługuje mapowanie przy użyciu wartości właściwości *Adres e-mail* użytkownika. Każda wiadomość e-mail zawiera tę właściwość, która jest wypełniana adresem e-mail każdego uczestnika wiadomości e-mail.

   Oprócz automatycznego mapowania użytkowników przy użyciu wartości właściwości Adres e-mail użytkownika możesz również zdefiniować mapowanie niestandardowe, przesyłając plik mapowania plików CSV. Ten plik mapowania powinien zawierać numer telefonu komórkowego użytkownika i odpowiadający mu adres Microsoft 365 pocztowej dla każdego użytkownika. Jeśli włączysz automatyczne mapowanie użytkowników i udostępnisz mapowanie niestandardowe, dla każdego elementu poczty e-mail łącznik najpierw przyjrzy się plikowi mapowania niestandardowego. Jeśli użytkownik nie znajdzie prawidłowego Microsoft 365 odpowiadającego numerowi telefonu komórkowego użytkownika, łącznik użyje właściwości adres e-mail użytkownika elementu poczty e-mail. Jeśli łącznik nie znajdzie prawidłowego użytkownika Microsoft 365 w pliku mapowania niestandardowego lub właściwości adresu e-mail użytkownika elementu poczty  e-mail, element nie zostanie zaimportowany.

## <a name="before-you-set-up-a-connector"></a>Przed skonfigurowaniem łącznika

- [Zamów usługę Signal Archiver w serwisie TeleMessage](https://www.telemessage.com/mobile-archiver/order-mobile-archiver-for-o365/) i uzyskaj prawidłowe konto administracyjne dla twojej organizacji. Podczas tworzenia łącznika w centrum zgodności musisz zalogować się do tego konta.

- Zarejestruj wszystkich użytkowników wymagających archiwizacji sygnału na koncie telemessage. Podczas rejestrowania użytkowników pamiętaj, aby używać tego samego adresu e-mail, który jest używany na ich Microsoft 365 kontach.

- Zainstaluj aplikację Signal Archiver na telefonach komórkowych pracowników i aktywuj ją. Aplikacja Signal Archiver umożliwia im komunikowanie się i rozmawianie na czacie z innymi użytkownikami sygnału.

- Użytkownik, który tworzy łącznik archiwatora sygnału w kroku 3, musi mieć przypisaną rolę importowania i eksportowania skrzynek pocztowych w programie Exchange Online. Jest to wymagane do dodawania łączników na **stronie Łączniki** danych w Centrum zgodności platformy Microsoft 365. Domyślnie ta rola nie jest przypisana do żadnej grupy ról w Exchange Online. Rolę importowania i eksportowania skrzynek pocztowych możesz dodać do grupy ról Zarządzanie organizacją w programie Exchange Online. Możesz też utworzyć grupę ról, przypisać rolę importowania i eksportowania skrzynek pocztowych, a następnie dodać odpowiednich użytkowników jako członków. Aby uzyskać więcej informacji, zobacz sekcje [Tworzenie grup ról](/Exchange/permissions-exo/role-groups#create-role-groups) [lub](/Exchange/permissions-exo/role-groups#modify-role-groups) Modyfikowanie grup ról w artykule "Zarządzanie grupami ról w aplikacji Exchange Online".

- Ten łącznik danych TeleMessage jest dostępny w GCC w chmurze dla instytucji rządowych Microsoft 365 USA. Aplikacje i usługi innych firm mogą obejmować przechowywanie, przekazywanie i przetwarzanie danych klienta Organizacji w systemach innych firm, które znajdują się poza infrastrukturą firmy Microsoft 365 i dlatego nie są objęte zobowiązaniami firmy Microsoft 365 w zakresie zgodności z przepisami i ochrony danych. Firma Microsoft nie zapewnia, że używanie tego produktu do łączenia się z aplikacjami innych firm oznacza, że te aplikacje innych firm są zgodne z fedRAMP.

## <a name="create-a-signal-archiver-connector"></a>Tworzenie łącznika archiwum sygnału

Po zakończeniu wymagań wstępnych opisanych w poprzedniej sekcji możesz utworzyć łącznik Signal Archiver w Centrum zgodności platformy Microsoft 365. Łącznik używa podanej informacji do nawiązania połączenia z witryną TeleMessage i przesyła dane komunikacji sygnałowej do odpowiednich skrzynek pocztowych użytkowników w Microsoft 365.

1. Przejdź do, <https://compliance.microsoft.com> a następnie kliknij pozycję **Łączniki** **danychArchiwizatorsignalny** > .

2. Na stronie **Opis produktu Archiwizuj** sygnał kliknij pozycję **Dodaj łącznik.**

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
