---
title: Konfigurowanie łącznika do archiwizowania danych sieci Verizon Network w Microsoft 365
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
description: Administratorzy mogą skonfigurować łącznik TeleMessage w celu importowania i archiwizowania danych SMS i MMS z sieci Verizon Network w Microsoft 365. Dzięki temu można archiwizować dane ze źródeł danych innych firm w programie Microsoft 365, aby zarządzać danymi innych firm przy użyciu funkcji zgodności, takich jak archiwizacja ze względu na przepisy prawne, wyszukiwanie zawartości i zasady przechowywania.
ms.openlocfilehash: 3f9ae6d64a1cd89da580f84fa03add0ef0f54183
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63324833"
---
# <a name="set-up-a-connector-to-archive-verizon-network-data"></a>Konfigurowanie łącznika do archiwizowania danych sieci Verizon

Za pomocą łącznika TeleMessage w aplikacji Centrum zgodności platformy Microsoft 365 importować i archiwizować dane usług SMS i MMS (Short Messaging Service) i MMS z sieci Verizon Network. Po skonfigurowaniu i skonfigurowaniu łącznika łączy się on z siecią Verizon Network organizacji raz dziennie i importuje dane wiadomości SMS i MMS do skrzynek pocztowych w Microsoft 365.

Gdy dane łącznika sieci Verizon Network będą przechowywane w skrzynkach pocztowych użytkowników, do danych firmy Verizon możesz zastosować funkcje zgodności, Microsoft 365, takie jak zawieszenie w związku z postępowaniem sądowym, przeszukiwanie zawartości i Microsoft 365 przechowywania. Można na przykład wyszukiwać wiadomości Verizon SMS i MMS przy użyciu usługi Content Search lub skojarzyć skrzynkę pocztową zawierającą dane sieci Verizon z opiekunem w Advanced eDiscovery przypadku. Importowanie i archiwizowanie danych w sieci Microsoft 365 za pomocą łącznika sieci Verizon Network może pomóc Twojej organizacji zachować zgodność z zasadami rządowymi i przepisami regulacyjną.

## <a name="overview-of-archiving-verizon-network-data"></a>Omówienie archiwizowania danych sieci Verizon

W poniższym o omówieniem wyjaśniono proces używania łącznika do archiwizowania danych sieci Verizon Network w Microsoft 365.

![Przepływ pracy archiwizacji sieci Verizon.](../media/VerizonNetworkConnectorWorkflow.png)

1. Twoja organizacja współpracuje z firmami TeleMessage i Verizon w celu skonfigurowania łącznika sieci Verizon Network. Aby uzyskać więcej informacji, zobacz [Verizon Network Archiver](https://www.telemessage.com/office365-activation-for-verizon-network-archiver/).

2. Wiadomości SMS i MMS z sieci Verizon Twojej organizacji są kopiowane do witryny TeleMessage co 24 godziny.

3. Łącznik sieci Verizon Network, który tworzysz w sieci Centrum zgodności platformy Microsoft 365, łączy się z witryną TeleMessage codziennie i przenosi wiadomości SMS i MMS z poprzednich 24 godzin do bezpiecznej lokalizacji usługi Azure Storage w chmurze firmy Microsoft. Łącznik konwertuje także treść wiadomości SMS i MMS na format wiadomości e-mail.

4. Łącznik importuje elementy komunikacji mobilnej do skrzynki pocztowej określonego użytkownika. W skrzynce pocztowej określonego użytkownika jest tworzony nowy folder o nazwie **Verizon SMS/MMS Network Archiver** , a elementy są do niego importowane. Łącznik obsługuje to mapowanie przy użyciu wartości *właściwości Adres e-mail* użytkownika. Każda wiadomość SMS i MMS zawiera tę właściwość, która jest wypełniana adresem e-mail każdego uczestnika wiadomości.

   Oprócz automatycznego mapowania użytkowników przy użyciu wartości właściwości Adres e-mail użytkownika możesz także zaimplementować mapowanie niestandardowe, przesyłając plik mapowania CSV. Ten plik mapowania zawiera numer telefonu komórkowego i Microsoft 365 e-mail dla użytkowników w organizacji. Jeśli włączysz zarówno automatyczne mapowanie użytkowników, jak i mapowanie niestandardowe, dla każdego elementu Verizon łącznik najpierw przejmie plik mapowania niestandardowego. Jeśli nie znajdzie prawidłowego użytkownika Microsoft 365 odpowiadającego numerowi telefonu komórkowego użytkownika, łącznik użyje wartości z właściwości adresu e-mail elementu, który próbuje zaimportować. Jeśli łącznik nie znajdzie prawidłowego użytkownika Microsoft 365 w pliku mapowania niestandardowego lub we właściwości adresu e-mail elementu Verizon, element nie zostanie zaimportowany.

## <a name="before-you-set-up-a-connector"></a>Przed skonfigurowaniem łącznika

Niektóre kroki implementacji wymagane do archiwizacji danych sieci Verizon są zewnętrzne Microsoft 365 i muszą zostać ukończone, zanim będzie można utworzyć łącznik w centrum zgodności.

- Zamów [usługę Verizon Network Archiver w serwisie TeleMessage](https://www.telemessage.com/mobile-archiver/order-mobile-archiver-for-o365) i uzyskaj prawidłowe konto administracyjne dla swojej organizacji. Podczas tworzenia łącznika w centrum zgodności musisz zalogować się do tego konta.

- Uzyskaj konto Verizon Network i dane kontaktowe do rozliczeń, aby móc wypełnić formularze dołączania telemessage i zamówić usługę archiwizacji wiadomości od firmy Verizon.

- Zarejestruj wszystkich użytkowników, którzy wymagają archiwizacji w sieci Verizon SMS i MMS, na koncie TeleMessage. Podczas rejestrowania użytkowników pamiętaj, aby używać tego samego adresu e-mail, który jest używany na ich Microsoft 365 kontach.

- Pracownicy muszą posiadać firmowe i firmowe telefony komórkowe w sieci komórkowej Verizon. Archiwizowanie wiadomości w Microsoft 365 nie jest dostępne w przypadku urządzeń należących do pracownika ani urządzeń Bring Your Own Devices (BYOD).

- Użytkownik, który tworzy łącznik sieci Verizon, musi mieć przypisaną rolę administratora łącznika danych. Ta rola jest wymagana do dodawania łączników na **stronie Łączniki** danych w Centrum zgodności platformy Microsoft 365. Ta rola jest domyślnie dodawana do wielu grup ról. Aby uzyskać listę tych grup ról, zobacz sekcję "Role w centrach zabezpieczeń i zgodności" w sekcji Uprawnienia w Centrum zabezpieczeń & [zgodności](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Administrator w organizacji może również utworzyć niestandardową grupę ról, przypisać rolę administrator łącznika danych, a następnie dodać odpowiednich użytkowników jako członków. Aby uzyskać instrukcje, zobacz sekcję "Tworzenie niestandardowej grupy ról" w sekcji Uprawnienia [w Centrum zgodności platformy Microsoft 365](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Ten łącznik danych TeleMessage jest dostępny w GCC w chmurze dla instytucji rządowych Microsoft 365 USA. Aplikacje i usługi innych firm mogą obejmować przechowywanie, przekazywanie i przetwarzanie danych klienta Organizacji w systemach innych firm, które znajdują się poza infrastrukturą firmy Microsoft 365 i dlatego nie są objęte zobowiązaniami firmy Microsoft 365 w zakresie zgodności z przepisami i ochrony danych. Firma Microsoft nie zapewnia, że używanie tego produktu do łączenia się z aplikacjami innych firm oznacza, że te aplikacje innych firm są zgodne z fedRAMP.

## <a name="create-a-verizon-network-connector"></a>Tworzenie łącznika sieci Verizon

Po wylieniu wymagań wstępnych opisanych w poprzedniej sekcji możesz utworzyć łącznik sieci Verizon Network w Centrum zgodności platformy Microsoft 365. Łącznik używa podanej informacji do nawiązania połączenia z witryną TeleMessage i przesłania wiadomości SMS i MMS do odpowiednich skrzynek pocztowych użytkowników w Microsoft 365.

1. Przejdź do, [https://compliance.microsoft.com](https://compliance.microsoft.com) a następnie kliknij pozycję **Łączniki danychSiećVerizon** >  Network.

2. Na stronie **opis produktu Verizon Network** kliknij pozycję **Dodaj łącznik**.

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