---
title: Konfigurowanie łącznika do archiwizowania danych sieci TELUS na platformie Microsoft 365
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
description: Administratorzy mogą skonfigurować łącznik TeleMessage do importowania i archiwizowania danych programu SMS z sieci TELUS na platformie Microsoft 365. Dzięki temu można archiwizować dane ze źródeł danych innych firm w usłudze Microsoft 365, aby można było zarządzać danymi innych firm za pomocą funkcji zgodności, takich jak archiwizowanie prawne, wyszukiwanie zawartości i zasady przechowywania.
ms.openlocfilehash: 215f185aa655f031151799f77889976bca799766
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66628952"
---
# <a name="set-up-a-connector-to-archive-telus-network-data"></a>Konfigurowanie łącznika do archiwizowania danych sieci TELUS

Użyj łącznika TeleMessage w portal zgodności Microsoft Purview, aby zaimportować i zarchiwizować dane usługi Short Messaging Service (SMS) z sieci TELUS w organizacji. Po skonfigurowaniu i skonfigurowaniu łącznika łączy się on z siecią TELUS w organizacji raz dziennie i importuje dane sms do skrzynek pocztowych na platformie Microsoft 365.

Po zapisaniu wiadomości SMS w skrzynkach pocztowych użytkowników można zastosować do danych TELUS funkcje usługi Microsoft Purview, takie jak blokada sporów sądowych, wyszukiwanie zawartości i zasady przechowywania platformy Microsoft 365. Na przykład można wyszukiwać wiadomości SMS TELUS przy użyciu wyszukiwania zawartości lub skojarzyć skrzynkę pocztową zawierającą dane TELUS z opiekunem w przypadku zbierania elektronicznych materiałów dowodowych (Premium). Importowanie i archiwizowanie danych na platformie Microsoft 365 przy użyciu łącznika sieci TELUS może pomóc twojej organizacji zachować zgodność z zasadami rządowymi i regulacyjnymi.

## <a name="overview-of-archiving-telus-network-data"></a>Omówienie archiwizacji danych sieci TELUS

W poniższym omówieniu wyjaśniono proces używania łącznika do archiwizowania danych sieci TELUS na platformie Microsoft 365.

![Przepływ pracy archiwizacji sieci TELUS.](../media/TelusNetworkConnectorWorkflow.png)

1. Twoja organizacja współpracuje z usługami TeleMessage i TELUS w celu skonfigurowania łącznika sieci TELUS. Aby uzyskać więcej informacji, zobacz [TELUS Network Archiver](https://www.telemessage.com/office365-activation-for-telus-network-archiver/).

2. W czasie rzeczywistym wiadomości SMS z sieci TELUS organizacji są kopiowane do witryny TeleMessage.

3. Łącznik sieci TELUS tworzony w portalu zgodności codziennie łączy się z witryną TeleMessage i przesyła wiadomości SMS z poprzednich 24 godzin do bezpiecznej lokalizacji usługi Azure Storage w chmurze firmy Microsoft. Łącznik konwertuje również zawartość wiadomości SMS na format wiadomości e-mail.

4. Łącznik importuje elementy komunikacji mobilnej do skrzynki pocztowej określonego użytkownika. Nowy folder o nazwie **TELUS SMS Network Archiver** jest tworzony w skrzynce pocztowej określonego użytkownika, a elementy są do niego importowane. Łącznik wykonuje mapowanie przy użyciu wartości właściwości *Adres e-mail użytkownika* . Każda wiadomość SMS zawiera tę właściwość, która jest wypełniana adresem e-mail każdego uczestnika wiadomości SMS.

   Oprócz automatycznego mapowania użytkownika przy użyciu wartości właściwości *Adres e-mail użytkownika* można również zaimplementować mapowanie niestandardowe, przekazując plik mapowania CSV. Ten plik mapowania zawiera numer telefonu komórkowego i odpowiedni adres e-mail platformy Microsoft 365 dla użytkowników w organizacji. Jeśli włączysz automatyczne mapowanie użytkowników i mapowanie niestandardowe, dla każdego elementu TELUS łącznik najpierw przyjrzy się niestandardowemu plikowi mapowania. Jeśli nie znajdzie prawidłowego użytkownika platformy Microsoft 365, który odpowiada numerowi telefonu komórkowego użytkownika, łącznik użyje wartości we właściwości adresu e-mail elementu, który próbuje zaimportować. Jeśli łącznik nie znajdzie prawidłowego użytkownika usługi Microsoft 365 w niestandardowym pliku mapowania lub we właściwości adresu e-mail elementu TELUS, element nie zostanie zaimportowany.

## <a name="before-you-set-up-a-connector"></a>Przed skonfigurowaniem łącznika

Niektóre kroki implementacji wymagane do archiwizacji danych sieci TELUS są zewnętrzne dla platformy Microsoft 365 i muszą zostać ukończone przed utworzeniem łącznika w Centrum zgodności.

- Zamów [usługę TELUS Network Archiver z usługi TeleMessage i uzyskaj prawidłowe](https://www.telemessage.com/mobile-archiver/order-mobile-archiver-for-o365) konto administracyjne dla swojej organizacji. Musisz zalogować się do tego konta podczas tworzenia łącznika w Centrum zgodności.

- Uzyskaj swoje konto sieciowe TELUS i dane kontaktowe dotyczące rozliczeń, aby można było wypełnić formularze dołączania usługi TeleMessage i zamówić usługę archiwizacji komunikatów z aplikacji TELUS.

- Zarejestruj wszystkich użytkowników, którzy wymagają archiwizacji sieci TELUS SMS na koncie TeleMessage. Podczas rejestrowania użytkowników należy użyć tego samego adresu e-mail, który jest używany dla ich konta platformy Microsoft 365.

- Pracownicy muszą mieć firmowe i firmowe telefony komórkowe w sieci komórkowejTELUS. Archiwizowanie komunikatów na platformie Microsoft 365 nie jest dostępne dla urządzeń należących do pracowników ani urządzeń BYOD (Bring Your Own Devices).

- Użytkownikowi, który tworzy łącznik sieci TELUS, należy przypisać rolę Administracja łącznika danych. Ta rola jest wymagana do dodawania łączników na stronie **Łączniki danych** w portalu zgodności. Ta rola jest domyślnie dodawana do wielu grup ról. Aby uzyskać listę tych grup ról, zobacz sekcję "Role w centrach zabezpieczeń i zgodności" w obszarze [Uprawnienia w Centrum zgodności & zabezpieczeń](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternatywnie administrator w organizacji może utworzyć niestandardową grupę ról, przypisać rolę Administracja łącznika danych, a następnie dodać odpowiednich użytkowników jako członków. Aby uzyskać instrukcje, zobacz sekcję "Tworzenie niestandardowej grupy ról" w obszarze [Uprawnienia w portal zgodności Microsoft Purview](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Ten łącznik danych telemessage jest dostępny w środowiskach GCC w chmurze microsoft 365 us government. Aplikacje i usługi innych firm mogą obejmować przechowywanie, przesyłanie i przetwarzanie danych klientów organizacji w systemach innych firm, które znajdują się poza infrastrukturą platformy Microsoft 365 i w związku z tym nie są objęte zobowiązaniami microsoft purview i ochrony danych. Firma Microsoft nie przedstawia żadnej reprezentacji, że użycie tego produktu do łączenia się z aplikacjami innych firm oznacza, że te aplikacje innych firm są zgodne z fedrampem.

## <a name="create-a-telus-network-connector"></a>Tworzenie łącznika sieci TELUS

Po ukończeniu wymagań wstępnych opisanych w poprzedniej sekcji możesz utworzyć łącznik sieci TELUS w portalu zgodności. Łącznik używa podanych informacji, aby nawiązać połączenie z witryną TeleMessage i przenieść wiadomości SMS do odpowiednich skrzynek pocztowych użytkownika w usłudze Microsoft 365.

1. Przejdź do obszaru [https://compliance.microsoft.com](https://compliance.microsoft.com/) , a następnie kliknij pozycję **Łączniki** >  danych **TELUS Network**.

2. Na stronie opisu produktu **telus network** kliknij pozycję **Dodaj łącznik**

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
