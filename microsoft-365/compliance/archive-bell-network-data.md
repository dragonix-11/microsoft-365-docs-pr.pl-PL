---
title: Konfigurowanie łącznika w celu archiwizowania danych sieci sms/MMS programu Bell
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
description: Administratorzy mogą skonfigurować łącznik TeleMessage do importowania i archiwizowania danych PROGRAMU SMS i MMS z sieci Bell. Dzięki temu można archiwizować dane ze źródeł danych innych firm w usłudze Microsoft 365, aby można było zarządzać danymi innych firm za pomocą funkcji zgodności, takich jak archiwizowanie prawne, wyszukiwanie zawartości i zasady przechowywania.
ms.openlocfilehash: 82e86acaef19192d1cace5c5e2713a6b2fb39bf0
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66621606"
---
# <a name="set-up-a-connector-to-archive-bell-network-data"></a>Konfigurowanie łącznika do archiwizowania danych usługi Bell Network

Użyj łącznika TeleMessage w portal zgodności Microsoft Purview, aby zaimportować i zarchiwizować komunikaty usługi Short Messaging Service (SMS) i mms (Multimedia Messaging Service) z sieci Dzwonek. Po skonfigurowaniu i skonfigurowaniu łącznika łączy się on z siecią Bell Network organizacji raz dziennie i importuje wiadomości SMS i MMS do skrzynek pocztowych na platformie Microsoft 365.

Po zapisaniu wiadomości SMS i MMS w skrzynkach pocztowych użytkowników można zastosować funkcje usługi Microsoft Purview, takie jak blokada postępowania sądowego, wyszukiwanie zawartości i zasady przechowywania usługi Microsoft 365 do danych usługi Bell Network. Możesz na przykład wyszukać adres SMS/MMS usługi Bell Network przy użyciu wyszukiwania zawartości lub skojarzyć skrzynkę pocztową zawierającą dane łącznika bell network z opiekunem w przypadku zbierania elektronicznych materiałów dowodowych (Premium). Importowanie i archiwizowanie danych w usłudze Microsoft 365 przy użyciu łącznika bell network może pomóc twojej organizacji zachować zgodność z zasadami rządowymi i regulacyjnymi.

## <a name="overview-of-archiving-bell-network-data"></a>Omówienie archiwizacji danych sieci bell

W poniższym omówieniu wyjaśniono proces używania łącznika do archiwizowania danych usługi Bell Network na platformie Microsoft 365.

![Przepływ pracy archiwizacji usługi Bell Network.](../media/BellNetworkConnectorWorkflow.png)

1. Twoja organizacja współpracuje z usługami TeleMessage i Bell w celu skonfigurowania łącznika bell network. Aby uzyskać więcej informacji, zobacz [Bell Network Archiver](https://www.telemessage.com/office365-activation-for-bell-network-archiver).

2. W czasie rzeczywistym wiadomości SMS i MMS z sieci Dzwonek organizacji są kopiowane do witryny TeleMessage.

3. Łącznik bell network tworzony w portalu zgodności codziennie łączy się z witryną TeleMessage i przesyła wiadomości SMS i MMS z poprzednich 24 godzin do bezpiecznej lokalizacji usługi Azure Storage w chmurze firmy Microsoft. Łącznik konwertuje również zawartość wiadomości SMS i MMS na format wiadomości e-mail.

4. Łącznik importuje elementy komunikacji mobilnej do skrzynki pocztowej określonych użytkowników. Nowy folder o nazwie **Bell SMS/MMS Network Archiver** zostanie utworzony w skrzynce pocztowej określonego użytkownika i elementy zostaną do niego zaimportowane. Łącznik wykonuje to mapowanie przy użyciu wartości właściwości *Adres e-mail użytkownika* . Każda wiadomość SMS i MMS zawiera tę właściwość, która jest wypełniana adresem e-mail każdego uczestnika wiadomości.

   Oprócz automatycznego mapowania użytkownika przy użyciu wartości właściwości *Adres e-mail użytkownika* można również zdefiniować mapowanie niestandardowe, przekazując plik mapowania CSV. Ten plik mapowania zawiera numer telefonu komórkowego i odpowiedni adres e-mail platformy Microsoft 365 dla użytkowników w organizacji. Jeśli włączysz automatyczne mapowanie użytkowników i mapowanie niestandardowe, dla każdego elementu sieci Dzwonek łącznik najpierw przyjrzy się niestandardowemu plikowi mapowania. Jeśli nie znajdzie prawidłowego użytkownika platformy Microsoft 365, który odpowiada numerowi telefonu komórkowego użytkownika, łącznik użyje wartości we właściwości adresu e-mail elementu, który próbuje zaimportować. Jeśli łącznik nie znajdzie prawidłowego użytkownika platformy Microsoft 365 w niestandardowym pliku mapowania lub we właściwości adresu e-mail elementu Bell Network, element nie zostanie zaimportowany.

## <a name="before-you-set-up-a-connector"></a>Przed skonfigurowaniem łącznika

Niektóre kroki implementacji wymagane do archiwizacji danych usługi Bell Network są zewnętrzne dla platformy Microsoft 365 i muszą zostać ukończone przed utworzeniem łącznika w Centrum zgodności.

- [Zamów usługę Bell Network Archiver z usługi TeleMessage i uzyskaj prawidłowe](https://www.telemessage.com/mobile-archiver/order-mobile-archiver-for-o365/) konto administracyjne dla swojej organizacji. Musisz zalogować się do tego konta podczas tworzenia łącznika w Centrum zgodności.

- Uzyskaj konto usługi Bell Network i dane kontaktowe dotyczące rozliczeń, aby można było wypełnić formularze dołączania usługi TeleMessage i zamówić usługę archiwizacji komunikatów w aplikacji Bell.

- Zarejestruj wszystkich użytkowników, którzy wymagają archiwizacji sieci Bell SMS/MMS na koncie TeleMessage. Podczas rejestrowania użytkowników należy użyć tego samego adresu e-mail, który jest używany dla ich konta platformy Microsoft 365.

- Pracownicy muszą mieć firmowe i firmowe telefony komórkowe w sieci komórkowej Bell. Archiwizowanie komunikatów na platformie Microsoft 365 nie jest dostępne dla urządzeń należących do pracowników lub "Przynieś własne urządzenia (BYOD).

- Użytkownikowi, który tworzy łącznik sieci bell, musi zostać przypisana rola Administracja łącznika danych. Ta rola jest wymagana do dodawania łączników na stronie **Łączniki danych** w portalu zgodności. Ta rola jest domyślnie dodawana do wielu grup ról. Aby uzyskać listę tych grup ról, zobacz sekcję "Role w centrach zabezpieczeń i zgodności" w obszarze [Uprawnienia w Centrum zgodności & zabezpieczeń](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternatywnie administrator w organizacji może utworzyć niestandardową grupę ról, przypisać rolę Administracja łącznika danych, a następnie dodać odpowiednich użytkowników jako członków. Aby uzyskać instrukcje, zobacz sekcję "Tworzenie niestandardowej grupy ról" w obszarze [Uprawnienia w portal zgodności Microsoft Purview](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Ten łącznik danych telemessage jest dostępny w środowiskach GCC w chmurze microsoft 365 us government. Aplikacje i usługi innych firm mogą obejmować przechowywanie, przesyłanie i przetwarzanie danych klientów organizacji w systemach innych firm, które znajdują się poza infrastrukturą platformy Microsoft 365 i w związku z tym nie są objęte zobowiązaniami microsoft purview i ochrony danych. Firma Microsoft nie przedstawia żadnej reprezentacji, że użycie tego produktu do łączenia się z aplikacjami innych firm oznacza, że te aplikacje innych firm są zgodne z fedrampem.

## <a name="create-a-bell-network-connector"></a>Tworzenie łącznika sieci dzwonka

Ostatnim krokiem jest utworzenie łącznika bell network w portalu zgodności. Łącznik używa podanych informacji, aby nawiązać połączenie z witryną TeleMessage i przenieść wiadomości SMS/MMS do odpowiednich skrzynek pocztowych użytkownika na platformie Microsoft 365.

1. Przejdź do, [https://compliance.microsoft.com](https://compliance.microsoft.com) a następnie kliknij pozycję **Łączniki** >  danych **Bell SMS/MMS Network Archiver**.

2. Na stronie Opis produktu **Bell Network** kliknij pozycję **Dodaj łącznik**

3. Na stronie **Warunki korzystania z usługi** kliknij pozycję **Akceptuj**.

4. Na stronie **Logowanie do usługi TeleMessage** w obszarze Krok 3 wprowadź wymagane informacje w poniższych polach, a następnie kliknij przycisk **Dalej**.

   - **Nazwę użytkownika:** Nazwa użytkownika usługi TeleMessage.

   - **Hasło:** Twoje hasło telemessage.

5. Po utworzeniu łącznika możesz zamknąć okno podręczne i przejść do następnej strony.

6. Na stronie **Mapowanie użytkownika** włącz automatyczne mapowanie użytkowników. Aby włączyć mapowanie niestandardowe, przekaż plik CSV zawierający informacje o mapowaniu użytkownika, a następnie kliknij przycisk **Dalej**.

7. Przejrzyj ustawienia, a następnie kliknij przycisk **Zakończ** , aby utworzyć łącznik.

8. Przejdź do karty **Łączniki** na stronie **Łączniki danych** w centrum zgodności, aby zobaczyć postęp procesu importowania nowego łącznika.

## <a name="known-issues"></a>Znane problemy

- Obecnie nie obsługujemy importowania załączników ani elementów o rozmiarze większym niż 10 MB. Obsługa większych elementów będzie dostępna w późniejszym terminie.
