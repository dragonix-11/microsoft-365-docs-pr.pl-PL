---
title: Konfigurowanie łącznika do archiwizowania danych sieciowych AT&T SMS/MMS
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
description: Administratorzy mogą skonfigurować łącznik TeleMessage w celu importowania i archiwizowania danych SMS-ów i MMS z sieci AT&T Mobile. Dzięki temu można archiwizować dane ze źródeł danych innych firm w programie Microsoft 365, aby zarządzać danymi innych firm przy użyciu funkcji zgodności, takich jak archiwizacja ze względu na przepisy prawne, wyszukiwanie zawartości i zasady przechowywania.
ms.openlocfilehash: 5725350502bf47f41ccac1d519599daecafe0d0d
ms.sourcegitcommit: 36a19d80fe3f053df0fec398a7ff2dfc777f9730
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/30/2021
ms.locfileid: "63020807"
---
# <a name="set-up-a-connector-to-archive-att-smsmms-data"></a>Konfigurowanie łącznika do archiwizowania danych AT&T SMS/MMS

Użyj łącznika TeleMessage w aplikacji Centrum zgodności platformy Microsoft 365 i archiwizuj dane SMS-ów i MMS z usługi AT&T Mobile Network. Po skonfigurowaniu i skonfigurowaniu łącznika połączy się on z siecią AT&T Network organizacji raz dziennie i zaim importuje dane wiadomości SMS i MMS do skrzynek pocztowych w Microsoft 365.

Po przechowywaniu wiadomości SMS i MMS w skrzynkach pocztowych użytkowników możesz zastosować funkcje zgodności usługi Microsoft 365, takie jak zastosowanie stosowania sporów sądowych, przeszukiwanie zawartości i zasady przechowywania Microsoft 365 do danych sieciowych AT&T. Można na przykład wyszukać dane z sieci AT&T przy użyciu funkcji przeszukiwania zawartości lub skojarzyć skrzynkę pocztową zawierającą dane łącznika sieci AT&T ze współpracownikiem w Advanced eDiscovery przypadku. Importowanie i archiwizowanie danych w programie Microsoft 365 za pomocą łącznika sieci AT&T Network może ułatwić organizacji zachowania zgodności z zasadami rządowymi i przepisami prawa.

## <a name="overview-of-archiving-att-network-data"></a>Omówienie archiwizowania danych w&T Network

W poniższym o omówieniem wyjaśniono proces używania łącznika do archiwizowania danych sieciowych at&T w programie Microsoft 365.

![Przepływ pracy ATT Network archiwum.](../media/ATTNetworkConnectorWorkflow.png)

1. Twoja organizacja współpracuje z usługą TeleMessage w celu skonfigurowania łącznika AT&T Network. Aby uzyskać informacje, [zobacz AT&T Network Archiver](https://www.telemessage.com/office365-activation-for-atnt-network-archiver/).

2. W czasie rzeczywistym wiadomości SMS i MMS z sieci AT&T Są kopiowane do witryny TeleMessage.

3. Łącznik AT&T Network, który tworzysz w usłudze Centrum zgodności platformy Microsoft 365, łączy się z witryną TeleMessage każdego dnia i przesyła wiadomości SMS i MMS z poprzednich 24 godzin do bezpiecznej lokalizacji usługi Azure Storage w chmurze firmy Microsoft. Łącznik konwertuje także treść wiadomości SMS i MMS na format wiadomości e-mail.

4. Łącznik zaim importuje elementy komunikacji mobilnej do skrzynki pocztowej określonych użytkowników. W skrzynce pocztowej użytkownika jest tworzony nowy folder o **nazwie AT&T SMS/MMS Network Archiver** , a elementy są do niego importowane. Łącznik obsługuje to mapowanie przy użyciu wartości *właściwości Adres e-mail* użytkownika. Każda wiadomość SMS i MMS zawiera tę właściwość, która jest wypełniana adresem e-mail każdego uczestnika wiadomości.
 
   Oprócz automatycznego mapowania użytkowników przy użyciu wartości właściwości Adres e-mail użytkownika możesz również zdefiniować mapowanie niestandardowe, przesyłając plik mapowania plików CSV. Ten plik mapowania zawiera numer telefonu komórkowego i Microsoft 365 e-mail dla użytkowników w organizacji. Jeśli włączysz zarówno automatyczne mapowanie użytkowników, jak i mapowanie niestandardowe, dla każdego elementu poczty e-mail łącznik najpierw przejmie plik mapowania niestandardowego. Jeśli użytkownik nie znajdzie prawidłowego Microsoft 365 odpowiadającego numerowi telefonu komórkowego, łącznik użyje wartości z właściwości adresu e-mail elementu, który próbuje zaimportować. Jeśli łącznik nie znajdzie prawidłowego użytkownika Microsoft 365 w pliku mapowania niestandardowego lub we właściwości adresu e-mail elementu poczty e-mail, element nie zostanie zaimportowany.

## <a name="before-you-begin"></a>Przed rozpoczęciem

Niektóre kroki implementacji wymagane do archiwizowania danych sieci AT&T są zewnętrzne Microsoft 365 i muszą zostać ukończone, aby można było utworzyć łącznik w centrum zgodności.

- [Zamów usługę archiwum mobilnego w usłudze TeleMessage](https://www.telemessage.com/mobile-archiver/order-mobile-archiver-for-o365/) i uzyskaj prawidłowe konto administracyjne dla swojej organizacji. Podczas tworzenia łącznika w centrum zgodności musisz zalogować się do tego konta.

- Uzyskaj swoje konto AT&T i dane kontaktowe do rozliczeń, aby móc wypełnić formularze dołączania telemessage i zamówić usługę archiwizowania wiadomości w usłudze AT&T.

- Zarejestruj wszystkich użytkowników wymagających archiwizacji w usłudze AT&SMS/MMS Network na koncie telemessage. Podczas rejestrowania użytkowników pamiętaj, aby używać tego samego adresu e-mail, który jest używany na ich Microsoft 365 kontach.

- Pracownicy muszą posiadać firmowe i firmowe telefony komórkowe w sieci komórkowej AT&T. Archiwizowanie wiadomości w Microsoft 365 jest niedostępne w przypadku urządzeń należących do pracownika lub "Przynieź własne urządzenia (BYOD).

- Użytkownik, który tworzy łącznik sieci AT&T, musi mieć przypisaną rolę importowania i eksportowania skrzynek pocztowych w programie Exchange Online. Jest to wymagane do dodawania łączników na **stronie Łączniki** danych w Centrum zgodności platformy Microsoft 365. Domyślnie ta rola nie jest przypisana do żadnej grupy ról w Exchange Online. Rolę importowania i eksportowania skrzynek pocztowych możesz dodać do grupy ról Zarządzanie organizacją w programie Exchange Online. Możesz też utworzyć grupę ról, przypisać rolę importowania i eksportowania skrzynek pocztowych, a następnie dodać odpowiednich użytkowników jako członków. Aby uzyskać więcej informacji, zobacz sekcje [Tworzenie grup ról](/Exchange/permissions-exo/role-groups#create-role-groups) [lub](/Exchange/permissions-exo/role-groups#modify-role-groups) Modyfikowanie grup ról w artykule "Zarządzanie grupami ról w aplikacji Exchange Online".

- Ten łącznik danych TeleMessage jest dostępny w GCC w chmurze dla instytucji rządowych Microsoft 365 USA. Aplikacje i usługi innych firm mogą obejmować przechowywanie, przekazywanie i przetwarzanie danych klienta Organizacji w systemach innych firm, które znajdują się poza infrastrukturą firmy Microsoft 365 i dlatego nie są objęte zobowiązaniami firmy Microsoft 365 w zakresie zgodności z przepisami i ochrony danych. Firma Microsoft nie zapewnia, że używanie tego produktu do łączenia się z aplikacjami innych firm oznacza, że te aplikacje innych firm są zgodne z fedRAMP.

## <a name="create-a-att-network-connector"></a>Tworzenie łącznika AT&T Network

Po zakończeniu wymagań wstępnych opisanych w poprzedniej sekcji możesz utworzyć łącznik AT&T Network w Centrum zgodności platformy Microsoft 365. Łącznik używa podanej informacji do nawiązania połączenia z witryną TeleMessage i przesłania wiadomości SMS i MMS do odpowiednich skrzynek pocztowych użytkowników w Microsoft 365.

1. Przejdź do, [https://compliance.microsoft.com](https://compliance.microsoft.com/) a następnie kliknij pozycję **Łączniki danychAT** \  **&T Network**.

2. Na stronie **AT&T Network product** description (Opis produktu sieci AT&) kliknij **pozycję Add connector (Dodaj łącznik)**

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
