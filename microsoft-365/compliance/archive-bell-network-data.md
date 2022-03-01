---
title: Konfigurowanie łącznika do archiwizowania danych sieciowych SMS-MMS w programie Bell SMS/MMS
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
description: Administratorzy mogą skonfigurować łącznik TeleMessage w celu importowania i archiwizowania danych SMS-ów i MMS z sieci dzwonka. Dzięki temu można archiwizować dane ze źródeł danych innych firm w programie Microsoft 365, aby zarządzać danymi innych firm przy użyciu funkcji zgodności, takich jak archiwizacja ze względu na przepisy prawne, wyszukiwanie zawartości i zasady przechowywania.
ms.openlocfilehash: fd2c986d31e148d209734f0aa65c7b12f950e2eb
ms.sourcegitcommit: 36a19d80fe3f053df0fec398a7ff2dfc777f9730
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/30/2021
ms.locfileid: "63020750"
---
# <a name="set-up-a-connector-to-archive-bell-network-data"></a>Konfigurowanie łącznika do archiwizowania danych z sieci Bell Network

Użyj łącznika TeleMessage w programie Centrum zgodności platformy Microsoft 365 do importowania i archiwizowania wiadomości SMS (Short Messaging Service) i MMS z sieci dzwonowej. Po skonfigurowaniu i skonfigurowaniu łącznika połączy się on z siecią dzwonową organizacji raz dziennie i zaim importuje wiadomości SMS i MMS do skrzynek pocztowych w Microsoft 365.

Po zapisaniu wiadomości SMS i MMS w skrzynkach pocztowych użytkowników możesz zastosować funkcje zgodności usługi Microsoft 365, takie jak Zastosowanie w związku z postępowaniem sądowym, Wyszukiwanie zawartości i zasady przechowywania Microsoft 365 do danych w sieci Bell. Można na przykład przeszukać wiadomości SMS/MMS w sieci bellej przy użyciu funkcji przeszukiwania zawartości lub skojarzyć skrzynkę pocztową zawierającą dane łącznika sieci dzwonowej ze współpracownikiem w Advanced eDiscovery przypadku. Importowanie i archiwizowanie danych w aplikacji Microsoft 365 za pomocą łącznika sieci dzwonowej może ułatwić organizacji zachowania zgodności z zasadami rządowymi i przepisami regulacyjną.

## <a name="overview-of-archiving-bell-network-data"></a>Omówienie archiwizowania danych w sieci dzwonowej

W poniższym o omówieniem wyjaśniono proces używania łącznika do archiwizowania danych sieci dzwonka w Microsoft 365.

![Przepływ pracy archiwizacji sieci dzwonka.](../media/BellNetworkConnectorWorkflow.png)

1. Twoja organizacja współpracuje z funkcjami TeleMessage i Bell w celu skonfigurowania łącznika bell Network. Aby uzyskać więcej informacji, zobacz [Bell Network Archiver (Bell Network Archiver](https://www.telemessage.com/office365-activation-for-bell-network-archiver)).

2. W czasie rzeczywistym wiadomości SMS i MMS z sieci dzwonowej organizacji są kopiowane do witryny TeleMessage.

3. Łącznik Bell Network, który tworzysz w usłudze Centrum zgodności platformy Microsoft 365, łączy się z witryną TeleMessage codziennie i przenosi wiadomości SMS i MMS z poprzednich 24 godzin do bezpiecznej lokalizacji usługi Azure Storage w chmurze firmy Microsoft. Łącznik konwertuje także treść wiadomości SMS i MMS na format wiadomości e-mail.

4. Łącznik zaim importuje elementy komunikacji mobilnej do skrzynki pocztowej określonych użytkowników. W skrzynce pocztowej określonego użytkownika jest tworzony nowy folder o nazwie Bell **SMS/MMS Network Archiver** , a elementy są do niego importowane. Łącznik obsługuje to mapowanie przy użyciu wartości *właściwości Adres e-mail* użytkownika. Każda wiadomość SMS i MMS zawiera tę właściwość, która jest wypełniana adresem e-mail każdego uczestnika wiadomości.

   Oprócz automatycznego mapowania użytkowników przy użyciu wartości właściwości Adres e-mail użytkownika możesz również zdefiniować mapowanie niestandardowe, przesyłając plik mapowania plików CSV. Ten plik mapowania zawiera numer telefonu komórkowego i Microsoft 365 e-mail dla użytkowników w organizacji. Jeśli włączysz zarówno automatyczne mapowanie użytkowników, jak i mapowanie niestandardowe, dla każdego elementu sieci bella łącznik najpierw przejdę do pliku mapowania niestandardowego. Jeśli nie znajdzie prawidłowego użytkownika Microsoft 365 odpowiadającego numerowi telefonu komórkowego użytkownika, łącznik użyje wartości z właściwości adresu e-mail elementu, który próbuje zaimportować. Jeśli łącznik nie znajdzie prawidłowego użytkownika Microsoft 365 w pliku mapowania niestandardowego lub we właściwości adresu e-mail elementu Bell Network, element nie zostanie zaimportowany.

## <a name="before-you-set-up-a-connector"></a>Przed skonfigurowaniem łącznika

Niektóre kroki implementacji wymagane do archiwizowania danych z sieci Bell Network są zewnętrzne Microsoft 365 i muszą zostać ukończone, aby można było utworzyć łącznik w centrum zgodności.

- Zamów [usługę Bell Network Archiver w serwisie TeleMessage](https://www.telemessage.com/mobile-archiver/order-mobile-archiver-for-o365/) i uzyskaj prawidłowe konto administracyjne dla swojej organizacji. Podczas tworzenia łącznika w centrum zgodności musisz zalogować się do tego konta.

- Uzyskaj konto Bell Network i dane kontaktowe do rozliczeń, aby móc wypełnić formularze dołączania aplikacji TeleMessage i zamówić usługę archiwizowania wiadomości od dzwonka.

- Zarejestruj wszystkich użytkowników, którzy wymagają archiwizacji w sieci Bell SMS/MMS, na koncie TeleMessage. Podczas rejestrowania użytkowników pamiętaj, aby używać tego samego adresu e-mail, który jest używany na ich Microsoft 365 kontach.

- Pracownicy muszą posiadać firmowe i firmowe telefony komórkowe w sieci komórkowej Bell. Archiwizowanie wiadomości w Microsoft 365 jest niedostępne w przypadku urządzeń należących do pracownika lub "Przynieź własne urządzenia (BYOD).

- Użytkownik, który tworzy łącznik sieci dzwonowej, musi mieć przypisaną rolę importowania i eksportowania skrzynek pocztowych w programie Exchange Online. Jest to wymagane do dodawania łączników na **stronie Łączniki** danych w Centrum zgodności platformy Microsoft 365. Domyślnie ta rola nie jest przypisana do żadnej grupy ról w Exchange Online. Rolę importowania i eksportowania skrzynek pocztowych możesz dodać do grupy ról Zarządzanie organizacją w programie Exchange Online. Możesz też utworzyć grupę ról, przypisać rolę importowania i eksportowania skrzynek pocztowych, a następnie dodać odpowiednich użytkowników jako członków. Aby uzyskać więcej informacji, zobacz sekcje [Tworzenie grup ról](/Exchange/permissions-exo/role-groups#create-role-groups) [lub](/Exchange/permissions-exo/role-groups#modify-role-groups) Modyfikowanie grup ról w artykule "Zarządzanie grupami ról w aplikacji Exchange Online".

- Ten łącznik danych TeleMessage jest dostępny w GCC w chmurze dla instytucji rządowych Microsoft 365 USA. Aplikacje i usługi innych firm mogą obejmować przechowywanie, przekazywanie i przetwarzanie danych klienta Organizacji w systemach innych firm, które znajdują się poza infrastrukturą firmy Microsoft 365 i dlatego nie są objęte zobowiązaniami firmy Microsoft 365 w zakresie zgodności z przepisami i ochrony danych. Firma Microsoft nie zapewnia, że używanie tego produktu do łączenia się z aplikacjami innych firm oznacza, że te aplikacje innych firm są zgodne z fedRAMP.

## <a name="create-a-bell-network-connector"></a>Tworzenie łącznika sieci dzwonowej

Ostatnim krokiem jest utworzenie łącznika bell Network w Centrum zgodności platformy Microsoft 365. Łącznik używa podanej informacji do nawiązania połączenia z witryną TeleMessage i przesłania wiadomości SMS/MMS do odpowiednich skrzynek pocztowych użytkowników w Microsoft 365.

1. Przejdź do i [https://compliance.microsoft.com](https://compliance.microsoft.com) kliknij pozycję **Łączniki danychSzybki** >  **SMS/MMS Network Archiver**.

2. Na stronie **Opis produktu Bell Network** kliknij pozycję **Dodaj łącznik**

3. Na stronie **Warunki użytkowania usługi** kliknij pozycję **Zaakceptuj**.

4. Na stronie **Login to TeleMessage** (Logowanie do telemessage) w obszarze Krok 3 wprowadź wymagane informacje w następujących polach, a następnie kliknij przycisk **Dalej**.

   - **Nazwa użytkownika:** Twoja nazwa użytkownika aplikacji TeleMessage.

   - **Hasło:** Hasło aplikacji TeleMessage.

5. Po utworzeniu łącznika możesz zamknąć okno podręczne i przejść do następnej strony.

6. Na stronie **Mapowanie użytkowników** włącz automatyczne mapowanie użytkowników. Aby włączyć mapowanie niestandardowe, przekaż plik CSV zawierający informacje o mapowaniu użytkowników, a następnie kliknij przycisk **Dalej**.

7. Przejrzyj ustawienia, a następnie kliknij przycisk **Zakończ,** aby utworzyć łącznik.

8. Przejdź do karty **Łączniki** na stronie **Łączniki** danych w centrum zgodności, aby wyświetlić postęp procesu importowania nowego łącznika.

## <a name="known-issues"></a>Znane problemy

- Obecnie importowanie załączników ani elementów większych niż 10 MB nie jest obsługuje. Obsługa większych elementów będzie dostępna w późniejszym terminie.
