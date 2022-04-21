---
title: Konfigurowanie łącznika do archiwizowania danych WhatsApp w Microsoft 365
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
description: Administratorzy mogą skonfigurować łącznik TeleMessage do importowania i archiwizowania danych WhatsApp w Microsoft 365. Umożliwia to archiwizowanie danych ze źródeł danych innych firm w Microsoft 365 dzięki czemu można używać funkcji zgodności, takich jak blokada prawna, wyszukiwanie zawartości i zasady przechowywania, aby zarządzać danymi innych firm w organizacji.
ms.openlocfilehash: e473e9a83bd035209cbc2cb07aa3fb93386e47d9
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2022
ms.locfileid: "65000449"
---
# <a name="set-up-a-connector-to-archive-whatsapp-data"></a>Konfigurowanie łącznika do archiwizowania danych WhatsApp

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Użyj łącznika TeleMessage w portalu zgodności usługi Microsoft Purview, aby zaimportować i zarchiwizować wywołania WhatsApp, czaty, załączniki, pliki i usunięte komunikaty. Po skonfigurowaniu i skonfigurowaniu łącznika łączy się on z kontem telemessage organizacji raz dziennie i importuje komunikację mobilną pracowników przy użyciu usługi TeleMessage WhatsApp Telefon Archiver lub TeleMessage WhatsApp Cloud Archiver do skrzynek pocztowych w Microsoft 365.

Po zapisaniu danych WhatsApp w skrzynkach pocztowych użytkowników można zastosować funkcje usługi Microsoft Purview, takie jak blokada postępowania sądowego, wyszukiwanie zawartości i zasady przechowywania Microsoft 365 do danych WhatsApp. Na przykład można wyszukiwać wiadomości WhatsApp przy użyciu wyszukiwania zawartości lub skojarzyć skrzynkę pocztową zawierającą wiadomości WhatsApp z opiekunem w przypadku zbierania elektronicznych materiałów dowodowych (Premium). Importowanie i archiwizowanie danych w Microsoft 365 przy użyciu łącznika WhatsApp może pomóc twojej organizacji zachować zgodność z zasadami rządowymi i regulacyjnymi.

## <a name="overview-of-archiving-whatsapp-data"></a>Omówienie archiwizacji danych WhatsApp

W poniższym omówieniu wyjaśniono proces używania łącznika do archiwizowania danych WhatsApp w Microsoft 365.

![Przepływ pracy archiwizacji whatsApp.](../media/WhatsAppConnectorWorkflow.png)

1. Twoja organizacja współpracuje z usługą TeleMessage w celu skonfigurowania łącznika WhatsApp Archiver. Aby uzyskać więcej informacji, zobacz [WhatsApp Archiver](https://www.telemessage.com/office365-activation-for-whatsapp-archiver).

2. W czasie rzeczywistym dane WhatsApp twojej organizacji są kopiowane do witryny TeleMessage.

3. Łącznik WhatsApp tworzony w portalu zgodności codziennie łączy się z witryną TeleMessage i przesyła dane WhatsApp z poprzednich 24 godzin do bezpiecznej lokalizacji Storage platformy Azure w chmurze firmy Microsoft. Łącznik konwertuje również zawartość danych WhatsApp na format wiadomości e-mail.

4. Łącznik importuje dane WhatsApp do skrzynki pocztowej określonego użytkownika. Nowy folder o nazwie **WhatsApp Archiver** jest tworzony w skrzynce pocztowej określonego użytkownika, a elementy są do niego importowane. Łącznik wykonuje to mapowanie przy użyciu wartości właściwości *Adres e-mail użytkownika* . Każda wiadomość WhatsApp zawiera tę właściwość, która jest wypełniana adresem e-mail każdego uczestnika wiadomości.

   Oprócz automatycznego mapowania użytkownika przy użyciu wartości właściwości *Adres e-mail użytkownika* można również zaimplementować mapowanie niestandardowe, przekazując plik mapowania CSV. Ten plik mapowania zawiera numer telefonu komórkowego i odpowiadający Microsoft 365 adres e-mail dla użytkowników w organizacji. Jeśli włączysz automatyczne mapowanie użytkownika i mapowanie niestandardowe, dla każdego elementu WhatsApp łącznik najpierw przyjrzy się niestandardowemu plikowi mapowania. Jeśli nie znajdzie prawidłowego użytkownika Microsoft 365, który odpowiada numerowi telefonu komórkowego użytkownika, łącznik użyje wartości we właściwości adresu e-mail elementu, który próbuje zaimportować. Jeśli łącznik nie znajdzie prawidłowego Microsoft 365 użytkownika w niestandardowym pliku mapowania lub we właściwości adresu e-mail elementu WhatsApp, element nie zostanie zaimportowany.

## <a name="before-you-set-up-a-connector"></a>Przed skonfigurowaniem łącznika

Niektóre kroki implementacji wymagane do zarchiwizowania danych komunikacyjnych whatsApp są zewnętrzne dla Microsoft 365 i muszą zostać ukończone przed utworzeniem łącznika w centrum zgodności.

- [Zamów usługę WhatsApp Archiver z usługi TeleMessage i uzyskaj prawidłowe](https://www.telemessage.com/mobile-archiver/order-mobile-archiver-for-o365) konto administracyjne dla swojej organizacji. Musisz zalogować się do tego konta podczas tworzenia łącznika w Centrum zgodności.

- Zarejestruj wszystkich użytkowników, którzy wymagają archiwizacji WhatsApp na koncie TeleMessage. Podczas rejestrowania użytkowników należy użyć tego samego adresu e-mail, który jest używany dla ich konta Microsoft 365.

- Zainstaluj aplikację TeleMessage [WhatsApp Telefon Archiver](https://www.telemessage.com/mobile-archiver/whatsapp-phone-archiver-2/) na telefonach komórkowych pracowników i aktywuj ją. Możesz też zainstalować regularne aplikacje WhatsApp lub WhatsApp Business na telefonach komórkowych pracowników i aktywować usługę WhatsApp Cloud Archiver, skanując kod QR w witrynie internetowej TeleMessage. Aby uzyskać więcej informacji, zobacz [WhatsApp Cloud Archiver](https://www.telemessage.com/mobile-archiver/whatsapp-archiver/whatsapp-cloud-archiver/).

- Użytkownik, który tworzy łącznik sieci Verizon, musi mieć przypisaną rolę administratora łącznika danych. Ta rola jest wymagana do dodawania łączników na stronie **Łączniki danych** w portalu zgodności. Ta rola jest domyślnie dodawana do wielu grup ról. Aby uzyskać listę tych grup ról, zobacz sekcję "Role w centrach zabezpieczeń i zgodności" w obszarze [Uprawnienia w Centrum zgodności & zabezpieczeń](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternatywnie administrator w organizacji może utworzyć niestandardową grupę ról, przypisać rolę administratora łącznika danych, a następnie dodać odpowiednich użytkowników jako członków. Aby uzyskać instrukcje, zobacz sekcję "Tworzenie niestandardowej grupy ról" w obszarze [Uprawnienia w portalu zgodności usługi Microsoft Purview](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Ten łącznik danych TeleMessage jest dostępny w środowiskach GCC w chmurze Microsoft 365 US Government. Aplikacje i usługi innych firm mogą obejmować przechowywanie, przesyłanie i przetwarzanie danych klientów organizacji w systemach innych firm, które znajdują się poza infrastrukturą Microsoft 365 i dlatego nie są objęte zobowiązaniami dotyczącymi usługi Microsoft Purview i ochrony danych. Firma Microsoft nie przedstawia żadnej reprezentacji, że użycie tego produktu do łączenia się z aplikacjami innych firm oznacza, że te aplikacje innych firm są zgodne z fedrampem.

## <a name="create-a-whatsapp-archiver-connector"></a>Tworzenie łącznika archiwum WhatsApp

Po ukończeniu wymagań wstępnych opisanych w poprzedniej sekcji możesz utworzyć łącznik WhatsApp w portalu zgodności. Łącznik używa podanych informacji, aby nawiązać połączenie z witryną TeleMessage i przenieść dane WhatsApp do odpowiednich skrzynek pocztowych użytkownika w Microsoft 365.

1. Przejdź do obszaru [https://compliance.microsoft.com](https://compliance.microsoft.com/) , a następnie kliknij pozycję **Łączniki** >  **danychCosAplikator aplikacji**.

2. Na stronie Opis produktu **WhatsApp Archiver** kliknij pozycję **Dodaj łącznik**

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
