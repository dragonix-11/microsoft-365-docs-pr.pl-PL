---
title: Konfigurowanie łącznika do archiwizowania danych aplikacji WhatsApp w Microsoft 365
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
description: Administratorzy mogą skonfigurować łącznik TeleMessage w celu importowania i archiwizowania danych aplikacji WhatsApp w Microsoft 365. Dzięki temu można archiwizować dane ze źródeł danych innych firm w programie Microsoft 365, aby zarządzać danymi innych firm przy użyciu funkcji zgodności, takich jak archiwizacja ze względu na przepisy prawne, wyszukiwanie zawartości i zasady przechowywania.
ms.openlocfilehash: b94d22b787e88de241bee404774caaabf5ac02ca
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63313233"
---
# <a name="set-up-a-connector-to-archive-whatsapp-data"></a>Konfigurowanie łącznika do archiwizowania danych aplikacji WhatsApp

Użyj łącznika TeleMessage w aplikacji Centrum zgodności platformy Microsoft 365 do importowania i archiwizowania połączeń WhatsApp, czatów, załączników, plików i usuniętych wiadomości. Po skonfigurowaniu i skonfigurowaniu łącznika połączy się on z kontem teleMessage Twojej organizacji raz dziennie i zaim importuje wiadomości mobilne pracowników za pomocą archiwum aplikacji TeleMessage Telefon Archiver lub TeleMessage WhatsApp Cloud Archiver do skrzynek pocztowych w usłudze Microsoft 365.

Po zapisaniu danych aplikacji WhatsApp w skrzynkach pocztowych użytkowników możesz zastosować funkcje zgodności usługi Microsoft 365, takie jak zawieszenie w związku z postępowaniem sądowym, przeszukiwanie zawartości i zasady przechowywania Microsoft 365 do danych aplikacji WhatsApp. Możesz na przykład wyszukiwać wiadomości w aplikacji WhatsApp przy użyciu funkcji Wyszukiwanie zawartości lub skojarzyć skrzynkę pocztową zawierającą wiadomości aplikacji WhatsApp ze współpracownikiem w Advanced eDiscovery przypadku. Importowanie i archiwizowanie danych w programie Microsoft 365 za pomocą łącznika aplikacji WhatsApp może ułatwić organizacji zachowania zgodności z zasadami rządowymi i przepisami regulacyjną.

## <a name="overview-of-archiving-whatsapp-data"></a>Omówienie archiwizowania danych aplikacji WhatsApp

Poniższe omówienie przedstawia proces używania łącznika do archiwizowania danych aplikacji WhatsApp w Microsoft 365.

![CoApp archiwizowanie przepływu pracy.](../media/WhatsAppConnectorWorkflow.png)

1. Twoja organizacja współpracuje z teleMessage, aby skonfigurować łącznik archiwum aplikacji WhatsApp. Aby uzyskać więcej informacji, zobacz [WhatsApp Archiver](https://www.telemessage.com/office365-activation-for-whatsapp-archiver).

2. W czasie rzeczywistym dane organizacji w aplikacji WhatsApp są kopiowane do witryny TeleMessage.

3. Łącznik aplikacji WhatsApp tworzyć w Centrum zgodności platformy Microsoft 365 łączy się z witryną TeleMessage codziennie i przesyła dane aplikacji WhatsApp z poprzednich 24 godzin do bezpiecznej lokalizacji usługi Azure Storage w chmurze firmy Microsoft. Łącznik konwertuje również dane zawartości aplikacji WhatsApp na format wiadomości e-mail.

4. Łącznik zaim importuje dane aplikacji WhatsApp do skrzynki pocztowej określonego użytkownika. W skrzynce pocztowej określonego użytkownika zostanie utworzony nowy folder o nazwie **WhatsApp Archiver** , a elementy zostaną do niego zaimportowane. Łącznik obsługuje to mapowanie przy użyciu wartości *właściwości Adres e-mail* użytkownika. Każda wiadomość aplikacji WhatsApp zawiera tę właściwość, która jest wypełniana adresem e-mail każdego uczestnika wiadomości.

   Oprócz automatycznego mapowania użytkowników przy użyciu wartości właściwości Adres e-mail użytkownika możesz także zaimplementować mapowanie niestandardowe, przesyłając plik mapowania CSV. Ten plik mapowania zawiera numer telefonu komórkowego i Microsoft 365 e-mail dla użytkowników w organizacji. Jeśli włączysz zarówno automatyczne mapowanie użytkowników, jak i mapowanie niestandardowe, dla każdego elementu aplikacji WhatsApp łącznik najpierw przejdę do pliku mapowania niestandardowego. Jeśli nie znajdzie prawidłowego użytkownika Microsoft 365 odpowiadającego numerowi telefonu komórkowego użytkownika, łącznik użyje wartości z właściwości adresu e-mail elementu, który próbuje zaimportować. Jeśli łącznik nie znajdzie prawidłowego użytkownika Microsoft 365 w pliku mapowania niestandardowego lub we właściwości adresu e-mail elementu WhatsApp, element nie zostanie zaimportowany.

## <a name="before-you-set-up-a-connector"></a>Przed skonfigurowaniem łącznika

Niektóre kroki implementacji wymagane do archiwizowania danych komunikacji aplikacji WhatsApp są zewnętrzne Microsoft 365 i muszą zostać ukończone, zanim będzie można utworzyć łącznik w centrum zgodności.

- Zamów [usługę WhatsApp Archiver w serwisie TeleMessage](https://www.telemessage.com/mobile-archiver/order-mobile-archiver-for-o365) i uzyskaj prawidłowe konto administracyjne dla twojej organizacji. Podczas tworzenia łącznika w centrum zgodności musisz zalogować się do tego konta.

- Zarejestruj wszystkich użytkowników wymagających archiwizacji CoApp na koncie TeleMessage. Podczas rejestrowania użytkowników pamiętaj, aby używać tego samego adresu e-mail, który jest używany na ich Microsoft 365 kontach.

- Zainstaluj aplikację TeleMessage [WhatsApp Telefon Archiver](https://www.telemessage.com/mobile-archiver/whatsapp-phone-archiver-2/) na telefonach komórkowych pracowników i aktywuj ją. Ewentualnie możesz zainstalować zwykłe aplikacje WhatsApp lub WhatsApp Business na telefonach komórkowych swoich pracowników i aktywować usługę WhatsApp Cloud Archiver, skanując kod QR w witrynie internetowej TeleMessage. Aby uzyskać więcej informacji, zobacz [WhatsApp Cloud Archiver](https://www.telemessage.com/mobile-archiver/whatsapp-archiver/whatsapp-cloud-archiver/).

- Użytkownik, który tworzy łącznik sieci Verizon, musi mieć przypisaną rolę administratora łącznika danych. Ta rola jest wymagana do dodawania łączników na **stronie Łączniki** danych w Centrum zgodności platformy Microsoft 365. Ta rola jest domyślnie dodawana do wielu grup ról. Aby uzyskać listę tych grup ról, zobacz sekcję "Role w centrach zabezpieczeń i zgodności" w sekcji Uprawnienia w Centrum zabezpieczeń & [zgodności](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Administrator w organizacji może również utworzyć niestandardową grupę ról, przypisać rolę administrator łącznika danych, a następnie dodać odpowiednich użytkowników jako członków. Aby uzyskać instrukcje, zobacz sekcję "Tworzenie niestandardowej grupy ról" w sekcji Uprawnienia [w Centrum zgodności platformy Microsoft 365](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Ten łącznik danych TeleMessage jest dostępny w GCC w chmurze dla instytucji rządowych Microsoft 365 USA. Aplikacje i usługi innych firm mogą obejmować przechowywanie, przekazywanie i przetwarzanie danych klienta Organizacji w systemach innych firm, które znajdują się poza infrastrukturą firmy Microsoft 365 i dlatego nie są objęte zobowiązaniami firmy Microsoft 365 w zakresie zgodności z przepisami i ochrony danych. Firma Microsoft nie zapewnia, że używanie tego produktu do łączenia się z aplikacjami innych firm oznacza, że te aplikacje innych firm są zgodne z fedRAMP.

## <a name="create-a-whatsapp-archiver-connector"></a>Tworzenie łącznika archiwum aplikacji WhatsApp

Po zakończeniu wymagań wstępnych opisanych w poprzedniej sekcji możesz utworzyć łącznik WhatsApp w Centrum zgodności platformy Microsoft 365. Łącznik używa podanej informacji do nawiązania połączenia z witryną TeleMessage i przeniesienia danych aplikacji WhatsApp do odpowiednich skrzynek pocztowych użytkowników w Microsoft 365.

1. Przejdź do, [https://compliance.microsoft.com](https://compliance.microsoft.com/) a następnie kliknij pozycję **Łączniki** **danychCosApp** >  Archiver.

2. Na stronie **coapp Archiver** product description (Opis produktu archiwum aplikacji WhatsApp) kliknij pozycję **Add connector (Dodaj łącznik)**

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
