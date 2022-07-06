---
title: Konfigurowanie łącznika do archiwizowania danych komunikacji sygnałowej na platformie Microsoft 365
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
description: Administratorzy mogą skonfigurować łącznik TeleMessage do importowania i archiwizowania danych komunikacji sygnału na platformie Microsoft 365. Dzięki temu można archiwizować dane ze źródeł danych innych firm w usłudze Microsoft 365, aby można było zarządzać danymi innych firm za pomocą funkcji zgodności, takich jak archiwizowanie prawne, wyszukiwanie zawartości i zasady przechowywania.
ms.openlocfilehash: 8c72549e561bf138add47365d3920e2af068703f
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66625660"
---
# <a name="set-up-a-connector-to-archive-signal-communications-data"></a>Konfigurowanie łącznika do archiwizowania danych komunikacji sygnałowej

Użyj łącznika TeleMessage w portal zgodności Microsoft Purview, aby zaimportować i zarchiwizować czaty, załączniki, pliki oraz usunięte komunikaty i wywołania. Po skonfigurowaniu i skonfigurowaniu łącznika nawiązuje on połączenie z kontem telemessage organizacji i importuje komunikację mobilną pracowników przy użyciu archiwum sygnałów telemessage do skrzynek pocztowych na platformie Microsoft 365.

Po zapisaniu danych łącznika usługi Signal Archiver w skrzynkach pocztowych użytkowników można zastosować funkcje usługi Microsoft Purview, takie jak blokada postępowania sądowego, wyszukiwanie zawartości i zasady przechowywania usługi Microsoft 365, do danych komunikacji sygnału. Możesz na przykład wyszukać komunikację sygnałową przy użyciu wyszukiwania zawartości lub skojarzyć skrzynkę pocztową zawierającą dane łącznika Usługi Signal Archiver z opiekunem w przypadku zbierania elektronicznych materiałów dowodowych (Premium). Importowanie i archiwizowanie danych na platformie Microsoft 365 przy użyciu łącznika Usługi Signal Archiver może pomóc organizacji zachować zgodność z przepisami dotyczącymi ładu korporacyjnego i zasadami regulacyjnymi.

## <a name="overview-of-archiving-signal-communications-data"></a>Omówienie archiwizacji danych komunikacji sygnału

W poniższym omówieniu wyjaśniono proces używania łącznika do archiwizowania danych komunikacji sygnału na platformie Microsoft 365.

![Przepływ pracy archiwizacji komunikacji sygnału.](../media/SignalConnectorWorkflow.png)

1. Twoja organizacja współpracuje z usługą TeleMessage w celu skonfigurowania łącznika usługi Signal Archiver. Aby uzyskać więcej informacji, zobacz [Aktywowanie archiwizacji sygnałów telemessage dla platformy Microsoft 365](https://www.telemessage.com/microsoft-365-activation-for-signal-archiver/).

2. W czasie rzeczywistym dane sygnału organizacji są kopiowane do witryny TeleMessage.

3. Łącznik Usługi Signal Archiver tworzony w portalu zgodności codziennie łączy się z witryną TeleMessage i przesyła wiadomości e-mail z poprzednich 24 godzin do bezpiecznego obszaru usługi Azure Storage w chmurze firmy Microsoft.

4. Łącznik importuje elementy komunikacji mobilnej do skrzynki pocztowej określonego użytkownika. Nowy folder o nazwie Signal Archiver zostanie utworzony w skrzynce pocztowej określonego użytkownika, a elementy zostaną do niego zaimportowane. Łącznik wykonuje mapowanie przy użyciu wartości właściwości *Adres e-mail użytkownika* . Każda wiadomość e-mail zawiera tę właściwość, która jest wypełniana adresem e-mail każdego uczestnika wiadomości e-mail.

   Oprócz automatycznego mapowania użytkownika przy użyciu wartości właściwości *Adres e-mail użytkownika* można również zdefiniować mapowanie niestandardowe, przekazując plik mapowania CSV. Ten plik mapowania powinien zawierać numer telefonu komórkowego użytkownika i odpowiedni adres skrzynki pocztowej platformy Microsoft 365 dla każdego użytkownika. Jeśli włączysz automatyczne mapowanie użytkownika i udostępnisz mapowanie niestandardowe, dla każdego elementu wiadomości e-mail łącznik najpierw przyjrzy się niestandardowemu plikowi mapowania. Jeśli nie znajdzie prawidłowego użytkownika platformy Microsoft 365, który odpowiada numerowi telefonu komórkowego użytkownika, łącznik użyje właściwości adres e-mail użytkownika elementu poczty e-mail. Jeśli łącznik nie znajdzie prawidłowego użytkownika platformy Microsoft 365 w niestandardowym pliku mapowania lub we właściwości *adresu e-mail użytkownika* elementu poczty e-mail, element nie zostanie zaimportowany.

## <a name="before-you-set-up-a-connector"></a>Przed skonfigurowaniem łącznika

- [Zamów usługę Signal Archiver z usługi TeleMessage i uzyskaj prawidłowe](https://www.telemessage.com/mobile-archiver/order-mobile-archiver-for-o365/) konto administracyjne dla swojej organizacji. Musisz zalogować się do tego konta podczas tworzenia łącznika w Centrum zgodności.

- Zarejestruj wszystkich użytkowników, którzy wymagają archiwizacji sygnału na koncie TeleMessage. Podczas rejestrowania użytkowników należy użyć tego samego adresu e-mail, który jest używany dla ich konta platformy Microsoft 365.

- Zainstaluj aplikację Signal Archiver na telefonach komórkowych pracowników i aktywuj ją. Aplikacja Signal Archiver umożliwia im komunikowanie się i czatowanie z innymi użytkownikami usługi Signal.

- Użytkownikowi, który tworzy łącznik usługi Signal Archiver w kroku 3, należy przypisać rolę Administracja łącznika danych. Ta rola jest wymagana do dodawania łączników na stronie **Łączniki danych** w portalu zgodności. Ta rola jest domyślnie dodawana do wielu grup ról. Aby uzyskać listę tych grup ról, zobacz sekcję "Role w centrach zabezpieczeń i zgodności" w obszarze [Uprawnienia w Centrum zgodności & zabezpieczeń](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternatywnie administrator w organizacji może utworzyć niestandardową grupę ról, przypisać rolę Administracja łącznika danych, a następnie dodać odpowiednich użytkowników jako członków. Aby uzyskać instrukcje, zobacz sekcję "Tworzenie niestandardowej grupy ról" w obszarze [Uprawnienia w portal zgodności Microsoft Purview](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Ten łącznik danych telemessage jest dostępny w środowiskach GCC w chmurze microsoft 365 us government. Aplikacje i usługi innych firm mogą obejmować przechowywanie, przesyłanie i przetwarzanie danych klientów organizacji w systemach innych firm, które znajdują się poza infrastrukturą platformy Microsoft 365 i w związku z tym nie są objęte zobowiązaniami microsoft purview i ochrony danych. Firma Microsoft nie przedstawia żadnej reprezentacji, że użycie tego produktu do łączenia się z aplikacjami innych firm oznacza, że te aplikacje innych firm są zgodne z fedrampem.

## <a name="create-a-signal-archiver-connector"></a>Tworzenie łącznika usługi Signal Archiver

Po ukończeniu wymagań wstępnych opisanych w poprzedniej sekcji możesz utworzyć łącznik Usługi Signal Archiver w portalu zgodności. Łącznik używa podanych informacji, aby nawiązać połączenie z witryną TeleMessage i przesyła dane komunikacji sygnału do odpowiednich skrzynek pocztowych użytkownika na platformie Microsoft 365.

1. Przejdź do obszaru <https://compliance.microsoft.com> , a następnie kliknij pozycję **Łączniki** >  danych **Signal Archiver**.

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
