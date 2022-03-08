---
title: Konfigurowanie łącznika do archiwizowania danych sieciowych O2 w Microsoft 365
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
description: Administratorzy mogą skonfigurować łącznik TeleMessage do importowania i archiwizowania danych SMS i MMS z sieci komórkowej O2 w Microsoft 365. Dzięki temu można archiwizować dane ze źródeł danych innych firm w programie Microsoft 365, aby zarządzać danymi innych firm przy użyciu funkcji zgodności, takich jak archiwizacja ze względu na przepisy prawne, wyszukiwanie zawartości i zasady przechowywania.
ms.openlocfilehash: cf3e7f42f8497b2bbba06ccda4e84956b731ede2
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63313261"
---
# <a name="set-up-a-connector-to-archive-o2-network-data"></a>Konfigurowanie łącznika do archiwizowania danych sieciowych O2

Za pomocą łącznika TeleMessage w Centrum zgodności platformy Microsoft 365 importować i archiwizować wiadomości SMS i połączenia głosowe z sieci komórkowej O2. Po skonfigurowaniu i skonfigurowaniu łącznika połączy się on z siecią O2 Twojej organizacji raz dziennie i zaim importuje wiadomości SMS i połączenia głosowe do skrzynek pocztowych w Microsoft 365.

Po przechowywaniu wiadomości SMS i połączeń głosowych w skrzynkach pocztowych użytkowników można stosować do danych sieciowych usługi Microsoft 365 funkcje zgodności, takie jak postępowanie w związku z postępowaniem sądowym, wyszukiwanie zawartości Microsoft 365 i zasady przechowywania zawartości. Można na przykład wyszukiwać w sieciowych wiadomościACH SMS i połączenia głosowe za pomocą funkcji przeszukiwania zawartości lub skojarzyć skrzynkę pocztową zawierającą dane sieci O2 ze współpracownikiem w Advanced eDiscovery przypadku. Importowanie i archiwizowanie danych w programie Microsoft 365 za pomocą łącznika sieci O2 może ułatwić organizacji zachowania zgodności z zasadami rządowymi i przepisami regulacyjną.

## <a name="overview-of-archiving-o2-network-data"></a>Omówienie archiwizowania danych sieciowych O2

W poniższym o omówieniem wyjaśniono proces używania łącznika do archiwizowania danych sieciowych usługi O2 w Microsoft 365.

![O2 Przepływ pracy archiwizacji sieci.](../media/O2NetworkConnectorWorkflow.png)

1. Twoja organizacja współpracuje z telemessage i O2 w celu skonfigurowania łącznika sieci O2. Aby uzyskać więcej informacji, zobacz [O2 Network Archiver (Archiwator sieci O2](https://www.telemessage.com/office365-activation-for-o2-network-archiver)).

2. Wiadomości SMS i połączenia głosowe z sieci O2 Twojej organizacji są kopiowane do witryny TeleMessage co 24 godziny.

3. Łącznik sieciowy O2, który tworzysz w usłudze Centrum zgodności platformy Microsoft 365, łączy się z witryną TeleMessage każdego dnia i przesyła wiadomości SMS i połączenia głosowe z poprzednich 24 godzin do bezpiecznej lokalizacji usługi Azure Storage w chmurze firmy Microsoft. Łącznik konwertuje także treść sms-ów i połączeń głosowych na format wiadomości e-mail.

4. Łącznik zaim importuje elementy komunikacji mobilnej do skrzynki pocztowej określonych użytkowników. W skrzynce pocztowej określonego użytkownika jest tworzony nowy folder o nazwie **O2 SMS and Voice Network Archiver** , do którym są importowane elementy. Łącznik obsługuje to mapowanie przy użyciu wartości *właściwości Adres e-mail* użytkownika. Każda wiadomość SMS i każda połączenie głosowe zawiera tę właściwość, która jest wypełniana adresem e-mail każdego uczestnika wiadomości.

   Oprócz automatycznego mapowania użytkowników przy użyciu wartości właściwości Adres e-mail użytkownika możesz również zdefiniować mapowanie niestandardowe, przesyłając plik mapowania plików CSV. Ten plik mapowania zawiera numer telefonu komórkowego i Microsoft 365 e-mail dla użytkowników w organizacji. Jeśli włączysz zarówno automatyczne mapowanie użytkowników, jak i mapowanie niestandardowe, dla każdego elementu O2 łącznik najpierw przejdę do pliku mapowania niestandardowego. Jeśli nie znajdzie prawidłowego użytkownika Microsoft 365 odpowiadającego numerowi telefonu komórkowego użytkownika, łącznik użyje wartości z właściwości adresu e-mail elementu, który próbuje zaimportować. Jeśli łącznik nie znajdzie prawidłowego użytkownika Microsoft 365 w pliku mapowania niestandardowego lub we właściwości adresu e-mail elementu O2, element nie zostanie zaimportowany.

## <a name="before-you-set-up-a-connector"></a>Przed skonfigurowaniem łącznika

Niektóre kroki implementacji wymagane do archiwizowania danych sieciowych O2 są zewnętrzne Microsoft 365 i muszą zostać ukończone, zanim będzie można utworzyć łącznik w centrum zgodności.

- Zamów [usługę O2 Network Archiver w serwisie TeleMessage](https://www.telemessage.com/mobile-archiver/order-mobile-archiver-for-o365/) i uzyskaj prawidłowe konto administracyjne dla swojej organizacji. Podczas tworzenia łącznika w centrum zgodności musisz zalogować się do tego konta.

- Uzyskaj konto usługi O2 Network i dane kontaktowe do rozliczeń, aby móc wypełnić formularze dołączania aplikacji TeleMessage i zamówić usługę archiwizowania wiadomości w O2.

- Zarejestruj wszystkich użytkowników wymagających archiwizacji W2 SMS i Voice Network na koncie TeleMessage. Podczas rejestrowania użytkowników pamiętaj, aby używać tego samego adresu e-mail, który jest używany na ich Microsoft 365 kontach.

- Pracownicy muszą posiadać firmowe i firmowe telefony komórkowe w sieci komórkowej O2. Archiwizowanie wiadomości w Microsoft 365 jest niedostępne w przypadku urządzeń należących do pracownika lub "Przynieź własne urządzenia (BYOD).

- Użytkownik, który tworzy łącznik sieciowy o2, musi mieć przypisaną rolę Administratora łącznika danych. Ta rola jest wymagana do dodawania łączników na **stronie Łączniki** danych w Centrum zgodności platformy Microsoft 365. Ta rola jest domyślnie dodawana do wielu grup ról. Aby uzyskać listę tych grup ról, zobacz sekcję "Role w centrach zabezpieczeń i zgodności" w sekcji Uprawnienia w Centrum zabezpieczeń & [zgodności](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Administrator w organizacji może również utworzyć niestandardową grupę ról, przypisać rolę administrator łącznika danych, a następnie dodać odpowiednich użytkowników jako członków. Aby uzyskać instrukcje, zobacz sekcję "Tworzenie niestandardowej grupy ról" w sekcji Uprawnienia [w Centrum zgodności platformy Microsoft 365](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Ten łącznik danych TeleMessage jest dostępny w GCC w chmurze dla instytucji rządowych Microsoft 365 USA. Aplikacje i usługi innych firm mogą obejmować przechowywanie, przekazywanie i przetwarzanie danych klienta Organizacji w systemach innych firm, które znajdują się poza infrastrukturą firmy Microsoft 365 i dlatego nie są objęte zobowiązaniami firmy Microsoft 365 w zakresie zgodności z przepisami i ochrony danych. Firma Microsoft nie zapewnia, że używanie tego produktu do łączenia się z aplikacjami innych firm oznacza, że te aplikacje innych firm są zgodne z fedRAMP.

## <a name="create-an-o2-network-connector"></a>Tworzenie łącznika sieciowego O2

Po zakończeniu wymagań wstępnych opisanych w poprzedniej sekcji możesz utworzyć łącznik sieci O2 w Centrum zgodności platformy Microsoft 365. Łącznik używa informacji, które po podaję, do łączenia się z witryną TeleMessage i przesyłania SMS-ów i połączeń głosowych do odpowiednich skrzynek pocztowych użytkowników w Microsoft 365.

1. Przejdź do, [https://compliance.microsoft.com](https://compliance.microsoft.com/) a następnie kliknij pozycję **Łączniki danych** \> **O2 Network**.

2. Na stronie **Opis produktu sieciowego O2** kliknij pozycję **Dodaj łącznik**

3. Na stronie **Warunki użytkowania usługi** kliknij pozycję **Zaakceptuj**.

4. Na stronie **Login to TeleMessage** (Logowanie do telemessage) w obszarze Krok 3 wprowadź wymagane informacje w następujących polach, a następnie kliknij przycisk **Dalej**.

   - **Nazwa użytkownika:** Twoja nazwa użytkownika aplikacji TeleMessage.

   - **Hasło:** Hasło aplikacji TeleMessage.

5. Po utworzeniu łącznika możesz zamknąć okno podręczne i przejść do następnej strony.

6. Na stronie **Mapowanie użytkowników** włącz automatyczne mapowanie użytkowników i kliknij przycisk **Dalej**. Jeśli potrzebujesz mapowania niestandardowego, przekaż plik CSV i kliknij przycisk **Dalej**.

7. Przejrzyj ustawienia, a następnie kliknij przycisk **Zakończ,** aby utworzyć łącznik.

8. Przejdź do karty Łączniki na **stronie Łączniki** danych, aby wyświetlić postęp procesu importowania nowego łącznika.

## <a name="known-issues"></a>Znane problemy

- Obecnie importowanie załączników ani elementów większych niż 10 MB nie jest obsługuje. Obsługa większych elementów będzie dostępna w późniejszym terminie.