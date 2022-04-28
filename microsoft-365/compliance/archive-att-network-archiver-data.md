---
title: Konfigurowanie łącznika do archiwizowania danych sieciowych usługi AT&T SMS/MMS
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
description: Administratorzy mogą skonfigurować łącznik TeleMessage w celu importowania i archiwizowania danych programu SMS i MMS z usługi AT&T Mobile Network. Dzięki temu można archiwizować dane ze źródeł danych innych firm w usłudze Microsoft Purview, aby można było zarządzać danymi innych firm za pomocą funkcji zgodności, takich jak archiwizowanie prawne, wyszukiwanie zawartości i zasady przechowywania.
ms.openlocfilehash: 7d73e6a5e5a5190609cd50bd055af8b7aec969b7
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65093180"
---
# <a name="set-up-a-connector-to-archive-att-smsmms-data"></a>Konfigurowanie łącznika do archiwizowania danych usługi AT&T SMS/MMS

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Użyj łącznika TeleMessage w portalu zgodności usługi Microsoft Purview, aby zaimportować i zarchiwizować dane programu SMS i MMS z usługi AT&T Mobile Network. Po skonfigurowaniu i skonfigurowaniu łącznika łączy się on z siecią AT&T w organizacji raz dziennie i importuje dane SMS i MMS do skrzynek pocztowych w usłudze Microsoft Purview.

Po zapisaniu wiadomości SMS i MMS w skrzynkach pocztowych użytkowników można zastosować Microsoft 365 funkcji usługi Purview, takich jak blokada postępowania sądowego, wyszukiwanie zawartości i zasady przechowywania Microsoft 365 do danych usługi AT&T Network. Możesz na przykład wyszukać dane usługi AT&T Network przy użyciu funkcji wyszukiwania zawartości lub skojarzyć skrzynkę pocztową zawierającą dane łącznika usługi AT&T Network z opiekunem w przypadku zbierania elektronicznych materiałów dowodowych (Premium). Importowanie i archiwizowanie danych w Microsoft 365 przy użyciu łącznika usługi AT&T Network może pomóc twojej organizacji zachować zgodność z zasadami rządowymi i regulacyjnymi.

## <a name="overview-of-archiving-att-network-data"></a>Omówienie archiwizacji danych usługi AT&T Network

W poniższym omówieniu wyjaśniono proces używania łącznika do archiwizowania danych usługi AT&T Network w Microsoft 365.

![Przepływ pracy archiwizacji sieci ATT.](../media/ATTNetworkConnectorWorkflow.png)

1. Twoja organizacja współpracuje z usługą TeleMessage w celu skonfigurowania łącznika usługi AT&T Network. Aby uzyskać informacje, zobacz [AT&T Network Archiver](https://www.telemessage.com/office365-activation-for-atnt-network-archiver/).

2. W czasie rzeczywistym wiadomości SMS i MMS z sieci AT&T Organizacji są kopiowane do witryny TeleMessage.

3. Łącznik usługi AT&T Network tworzony w portalu zgodności codziennie łączy się z witryną TeleMessage i przesyła wiadomości SMS i MMS z poprzednich 24 godzin do bezpiecznej lokalizacji usługi Azure Storage w chmurze firmy Microsoft. Łącznik konwertuje również zawartość wiadomości SMS i MMS na format wiadomości e-mail.

4. Łącznik importuje elementy komunikacji mobilnej do skrzynki pocztowej określonych użytkowników. W skrzynce pocztowej użytkownika zostanie utworzony nowy folder o nazwie **AT&T SMS/MMS Network Archiver** , a elementy zostaną do niego zaimportowane. Łącznik wykonuje to mapowanie przy użyciu wartości właściwości *Adres e-mail użytkownika* . Każda wiadomość SMS i MMS zawiera tę właściwość, która jest wypełniana adresem e-mail każdego uczestnika wiadomości.
 
   Oprócz automatycznego mapowania użytkownika przy użyciu wartości właściwości *Adres e-mail użytkownika* można również zdefiniować mapowanie niestandardowe, przekazując plik mapowania CSV. Ten plik mapowania zawiera numer telefonu komórkowego i odpowiadający Microsoft 365 adres e-mail dla użytkowników w organizacji. Jeśli włączysz automatyczne mapowanie użytkowników i mapowanie niestandardowe, dla każdego elementu wiadomości e-mail łącznik najpierw przyjrzy się niestandardowemu plikowi mapowania. Jeśli nie znajdzie prawidłowego użytkownika Microsoft 365, który odpowiada numerowi telefonu komórkowego, łącznik używa wartości we właściwości adresu e-mail elementu, który próbuje zaimportować. Jeśli łącznik nie znajdzie prawidłowego użytkownika Microsoft 365 w niestandardowym pliku mapowania lub we właściwości adresu e-mail elementu wiadomości e-mail, element nie zostanie zaimportowany.

## <a name="before-you-begin"></a>Przed rozpoczęciem

Niektóre kroki implementacji wymagane do zarchiwizowania danych usługi AT&T Network są zewnętrzne dla Microsoft 365 i muszą zostać ukończone przed utworzeniem łącznika w centrum zgodności.

- [Zamów usługę archiwizacji urządzeń przenośnych z usługi TeleMessage i uzyskaj prawidłowe](https://www.telemessage.com/mobile-archiver/order-mobile-archiver-for-o365/) konto administracyjne dla swojej organizacji. Musisz zalogować się do tego konta podczas tworzenia łącznika w Centrum zgodności.

- Uzyskaj konto usługi AT&T i dane kontaktowe dotyczące rozliczeń, aby można było wypełnić formularze dołączania usługi TeleMessage i zamówić usługę archiwizacji komunikatów w usłudze AT&T.

- Zarejestruj wszystkich użytkowników, którzy wymagają archiwizacji sieci usługi AT&T SMS/MMS na koncie TeleMessage. Podczas rejestrowania użytkowników należy użyć tego samego adresu e-mail, który jest używany dla ich konta Microsoft 365.

- Pracownicy muszą mieć firmowe i firmowe telefony komórkowe w sieci komórkowej AT&T. Archiwizowanie komunikatów w Microsoft 365 nie jest dostępne dla urządzeń należących do pracowników lub "Przynieś własne urządzenia (BYOD).

- Użytkownikowi tworzącemu łącznik usługi AT&T Network musi zostać przypisana rola administratora łącznika danych. Ta rola jest wymagana do dodawania łączników na stronie **Łączniki danych** w portalu zgodności. Ta rola jest domyślnie dodawana do wielu grup ról. Aby uzyskać listę tych grup ról, zobacz sekcję "Role w centrach zabezpieczeń i zgodności" w obszarze [Uprawnienia w Centrum zgodności & zabezpieczeń](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternatywnie administrator w organizacji może utworzyć niestandardową grupę ról, przypisać rolę administratora łącznika danych, a następnie dodać odpowiednich użytkowników jako członków. Aby uzyskać instrukcje, zobacz sekcję "Tworzenie niestandardowej grupy ról" w obszarze [Uprawnienia w portalu zgodności usługi Microsoft Purview](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Ten łącznik danych TeleMessage jest dostępny w środowiskach GCC w chmurze Microsoft 365 US Government. Aplikacje i usługi innych firm mogą obejmować przechowywanie, przesyłanie i przetwarzanie danych klientów organizacji w systemach innych firm, które znajdują się poza infrastrukturą Microsoft 365 i dlatego nie są objęte zobowiązaniami dotyczącymi usługi Microsoft Purview i ochrony danych. Firma Microsoft nie przedstawia żadnej reprezentacji, że użycie tego produktu do łączenia się z aplikacjami innych firm oznacza, że te aplikacje innych firm są zgodne z fedrampem.

## <a name="create-a-att-network-connector"></a>Tworzenie łącznika sieci at&T

Po ukończeniu wymagań wstępnych opisanych w poprzedniej sekcji możesz utworzyć łącznik usługi AT&T Network w portalu zgodności. Łącznik używa podanych informacji, aby nawiązać połączenie z witryną TeleMessage i przenieść wiadomości SMS i MMS do odpowiednich skrzynek pocztowych użytkownika w Microsoft 365.

1. Przejdź do obszaru [https://compliance.microsoft.com](https://compliance.microsoft.com/) , a następnie kliknij pozycję **Łączniki** \  **danychAt&T Network**.

2. Na stronie Opis **produktu AT&T Network** kliknij pozycję **Dodaj łącznik**

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
