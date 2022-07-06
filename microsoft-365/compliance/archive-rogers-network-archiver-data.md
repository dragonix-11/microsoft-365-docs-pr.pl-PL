---
title: Konfigurowanie łącznika w celu archiwizowania danych usługi Rogers Network na platformie Microsoft 365
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
description: Administratorzy mogą skonfigurować łącznik TeleMessage do importowania i archiwizowania danych sieci Rogers Na platformie Microsoft 365. Dzięki temu można archiwizować dane ze źródeł danych innych firm w usłudze Microsoft 365, aby można było zarządzać danymi innych firm za pomocą funkcji zgodności, takich jak archiwizowanie prawne, wyszukiwanie zawartości i zasady przechowywania.
ms.openlocfilehash: 62cdfa6c920451c73ff2941841cffd220ce427a8
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66623324"
---
# <a name="set-up-a-connector-to-archive-rogers-network-data"></a>Konfigurowanie łącznika do archiwizowania danych sieci Rogers

Użyj łącznika TeleMessage w portal zgodności Microsoft Purview, aby zaimportować i zarchiwizować dane programu SMS i MMS z sieci komórkowej Rogers. Po skonfigurowaniu i skonfigurowaniu [łącznika Rogers Network Archiver](https://www.telemessage.com/mobile-archiver/network-archiver/rogers/) łączy się on z siecią komórkową Rogers w organizacji i importuje dane SMS i MMS do skrzynek pocztowych na platformie Microsoft 365.

Po zapisaniu danych z sieci komórkowej Rogers w skrzynkach pocztowych użytkowników można zastosować do danych funkcje usługi Microsoft Purview, takie jak blokada postępowania sądowego, wyszukiwanie zawartości i zasady przechowywania platformy Microsoft 365. Na przykład możesz wyszukiwać wiadomości SMS i MMS z sieci komórkowej Rogers przy użyciu wyszukiwania zawartości lub wyszukiwania skojarzonego z przypadkiem Zbieranie elektronicznych materiałów dowodowych w Microsoft Purview (Standardowa). Importowanie i archiwizowanie danych w usłudze Microsoft 365 przy użyciu łącznika Rogers Network Archiver może pomóc twojej organizacji zachować zgodność z przepisami dotyczącymi ładu korporacyjnego i zasadami regulacyjnymi.

## <a name="overview-of-archiving-rogers-mobile-network-data"></a>Omówienie archiwizacji danych sieci komórkowej Rogers

W poniższym omówieniu wyjaśniono proces używania łącznika do archiwizowania danych programu Rogers SMS i MMS na platformie Microsoft 365.

![Przepływ pracy archiwizacji usługi Rogers Network.](../media/RogersNetworkConnectorWorkflow.png)

1. Twoja organizacja współpracuje z usługą TeleMessage w celu skonfigurowania łącznika Rogers Network Archiver. Aby uzyskać więcej informacji, zobacz [Aktywowanie archiwum sieciowego TeleMessage Rogers dla platformy Microsoft 365](https://www.telemessage.com/microsoft-365-activation-for-the-rogers-network-archiver/).

2. W czasie rzeczywistym dane sieci komórkowej Rogers organizacji są kopiowane do witryny TeleMessage.

3. Łącznik Rogers Network Archiver tworzony w portalu zgodności codziennie łączy się z witryną TeleMessage i przesyła wiadomości e-mail z poprzednich 24 godzin do bezpiecznego obszaru usługi Azure Storage w chmurze firmy Microsoft.

4. Łącznik importuje elementy komunikacji mobilnej do skrzynki pocztowej określonego użytkownika. Nowy folder o nazwie Rogers SMS/MMS Network Archiver zostanie utworzony w skrzynce pocztowej określonego użytkownika, a elementy zostaną do niego zaimportowane. Łącznik wykonuje mapowanie przy użyciu wartości właściwości *Adres e-mail użytkownika* . Każda wiadomość e-mail zawiera tę właściwość, która jest wypełniana adresem e-mail każdego uczestnika wiadomości e-mail.

   Oprócz automatycznego mapowania użytkownika przy użyciu wartości właściwości *Adres e-mail użytkownika* można również zdefiniować mapowanie niestandardowe, przekazując plik mapowania CSV. Ten plik mapowania powinien zawierać numer telefonu komórkowego użytkownika i odpowiedni adres skrzynki pocztowej platformy Microsoft 365 dla każdego użytkownika. Jeśli włączysz automatyczne mapowanie użytkownika i udostępnisz mapowanie niestandardowe, dla każdego elementu wiadomości e-mail łącznik najpierw przyjrzy się niestandardowemu plikowi mapowania. Jeśli nie znajdzie prawidłowego użytkownika usługi Microsoft 365, który odpowiada numerowi telefonu komórkowego użytkownika, łącznik użyje właściwości adresu e-mail użytkownika elementu wiadomości e-mail. Jeśli łącznik nie znajdzie prawidłowego użytkownika platformy Microsoft 365 w niestandardowym pliku mapowania lub we właściwości *adresu e-mail użytkownika* elementu poczty e-mail, element nie zostanie zaimportowany.

## <a name="before-you-set-up-a-connector"></a>Przed skonfigurowaniem łącznika

- [Zamów usługę Rogers Network Archiver z usługi TeleMessage i uzyskaj prawidłowe](https://www.telemessage.com/mobile-archiver/order-mobile-archiver-for-o365/) konto administracyjne dla swojej organizacji. Musisz zalogować się do tego konta podczas tworzenia łącznika w Centrum zgodności.

- Zarejestruj wszystkich użytkowników, którzy wymagają archiwizacji usługi Rogers Network na koncie TeleMessage. Podczas rejestrowania użytkowników należy użyć tego samego adresu e-mail, który jest używany dla ich konta platformy Microsoft 365.

- Pracownicy muszą mieć firmowe i firmowe telefony komórkowe w sieci komórkowej O2. Archiwizowanie komunikatów na platformie Microsoft 365 nie jest dostępne dla urządzeń należących do pracowników lub "Przynieś własne urządzenia (BYOD).

- Uzyskaj dane kontaktowe konta Rogers i rozliczeń dla swojej organizacji, aby można było wypełnić formularze dołączania i zamówić usługę archiwizacji wiadomości od firmy Rogers.

- Użytkownik, który tworzy łącznik Rogers Network Archiver w kroku 3, musi mieć przypisaną rolę Administracja łącznika danych. Ta rola jest wymagana do dodawania łączników na stronie **Łączniki danych** w portalu zgodności. Ta rola jest domyślnie dodawana do wielu grup ról. Aby uzyskać listę tych grup ról, zobacz sekcję "Role w centrach zabezpieczeń i zgodności" w obszarze [Uprawnienia w Centrum zgodności & zabezpieczeń](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternatywnie administrator w organizacji może utworzyć niestandardową grupę ról, przypisać rolę Administracja łącznika danych, a następnie dodać odpowiednich użytkowników jako członków. Aby uzyskać instrukcje, zobacz sekcję "Tworzenie niestandardowej grupy ról" w obszarze [Uprawnienia w portal zgodności Microsoft Purview](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Ten łącznik danych telemessage jest dostępny w środowiskach GCC w chmurze microsoft 365 us government. Aplikacje i usługi innych firm mogą obejmować przechowywanie, przesyłanie i przetwarzanie danych klientów organizacji w systemach innych firm, które znajdują się poza infrastrukturą platformy Microsoft 365 i w związku z tym nie są objęte zobowiązaniami microsoft purview i ochrony danych. Firma Microsoft nie przedstawia żadnej reprezentacji, że użycie tego produktu do łączenia się z aplikacjami innych firm oznacza, że te aplikacje innych firm są zgodne z fedrampem.

## <a name="create-a-rogers-network-archiver-connector"></a>Tworzenie łącznika Rogers Network Archiver

Po ukończeniu wymagań wstępnych opisanych w poprzedniej sekcji możesz utworzyć łącznik Rogers Network Archiver w portalu zgodności. Łącznik używa podanych informacji, aby nawiązać połączenie z witryną TeleMessage i przenieść dane rogers SMS/MMS do odpowiednich skrzynek pocztowych użytkownika w usłudze Microsoft 365.

1. Przejdź do, <https://compliance.microsoft.com> a następnie kliknij pozycję **Łączniki** >  danych **Rogers Network Archiver**.

2. Na stronie opisu produktu **Rogers Network Archiver** kliknij pozycję **Dodaj łącznik**.

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
