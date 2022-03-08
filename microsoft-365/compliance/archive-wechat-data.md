---
title: Konfigurowanie łącznika do archiwizowania danych programu WeChat w Microsoft 365
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
description: Skonfiguruj łącznik w aplikacji i użyj go w Centrum zgodności platformy Microsoft 365 do importowania i archiwizowania danych weChat w Microsoft 365.
ms.openlocfilehash: f2adb42dfd8145658e8861c752cfb9c11e306f52
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63328221"
---
# <a name="set-up-a-connector-to-archive-wechat-data"></a>Konfigurowanie łącznika do archiwizowania danych z programu WeChat

Za pomocą łącznika TeleMessage w aplikacji Centrum zgodności platformy Microsoft 365 importować i archiwizować połączenia WeChat i WeCom, czaty, załączniki, pliki i wiadomości odwołane. Po skonfigurowaniu i skonfigurowaniu łącznika połączy się on z kontem teleMessage Twojej organizacji i zaimekuje komunikację mobilną pracowników za pomocą archiwum programu TeleMessage WeChat do skrzynek pocztowych w usłudze Microsoft 365.

Po zapisaniu danych łącznika programu WeChat Archiver w skrzynkach pocztowych użytkowników możesz stosować funkcje zgodności usługi Microsoft 365, takie jak archiwizacja w związku z postępowaniem sądowym, zbierania elektronicznych materiałów dowodowych, In-Place archiwizowanie, inspekcja, zgodność z komunikacją i zasady przechowywania Microsoft 365 do danych komunikacji weChat. Na przykład możesz przeszukiwać komunikację w uczycie WeChat przy użyciu wyszukiwania zawartości lub skojarzyć skrzynkę pocztową zawierającą dane łącznika archiwacza WeChat ze współpracownikiem w Advanced eDiscovery przypadku. Importowanie i archiwizowanie danych w programie Microsoft 365 za pomocą łącznika archiwum programu WeChat może ułatwić twojej organizacji zgodność z przepisami prawa dotyczącymi ładu korporacyjnego i przepisami prawnymi.

## <a name="overview-of-archiving-wechat-communication-data"></a>Omówienie archiwizowania danych komunikacyjnych z programu WeChat

Poniższe omówienie przedstawia proces używania łącznika do archiwizowania danych dotyczących komunikacji z programu WeChat w Microsoft 365.

![Archiwizacja przepływu pracy dla danych archiwum programu WeChat.](../media/WeChatConnectorWorkflow.png)

1. Twoja organizacja współpracuje z programem TeleMessage w celu skonfigurowania łącznika archiwum wechat.

2. W czasie rzeczywistym dane z programu WeChat organizacji są kopiowane do witryny TeleMessage.

3. Łącznik programu WeChat Archiver, który tworzysz w Centrum zgodności platformy Microsoft 365, łączy się z witryną TeleMessage każdego dnia i przesyła wiadomości e-mail z poprzednich 24 godzin do bezpiecznego obszaru usługi Azure Storage w chmurze firmy Microsoft.

4. Łącznik importuje elementy komunikacji mobilnej do skrzynki pocztowej określonego użytkownika. W skrzynce pocztowej określonego użytkownika zostanie utworzony nowy folder o nazwie Archiwum programu WeChat, a elementy zostaną do niego zaimportowane. Łącznik mapuje dane przy użyciu wartości *właściwości Adres e-mail* użytkownika. Każda wiadomość e-mail zawiera tę właściwość, która jest wypełniana adresem e-mail każdego uczestnika wiadomości e-mail. Oprócz automatycznego mapowania użytkowników przy użyciu wartości właściwości Adres e-mail użytkownika możesz również zdefiniować mapowanie niestandardowe, przesyłając plik mapowania plików CSV. Ten plik mapowania powinien zawierać numer telefonu komórkowego użytkownika i odpowiadający mu adres Microsoft 365 pocztowej dla każdego użytkownika. Jeśli włączysz automatyczne mapowanie użytkowników i udostępnisz mapowanie niestandardowe, dla każdego elementu poczty e-mail łącznik najpierw przyjrzy się plikowi mapowania niestandardowego. Jeśli użytkownik nie znajdzie prawidłowego Microsoft 365 odpowiadającego numerowi telefonu komórkowego użytkownika, łącznik użyje właściwości adres e-mail użytkownika elementu poczty e-mail. Jeśli łącznik nie znajdzie prawidłowego użytkownika Microsoft 365 w pliku mapowania niestandardowego lub właściwości adresu e-mail użytkownika elementu poczty  e-mail, element nie zostanie zaimportowany.

## <a name="before-you-set-up-a-connector"></a>Przed skonfigurowaniem łącznika

- Za pomocą aplikacji TeleMessage skonfiguruj łącznik archiwum wechat. Aby uzyskać więcej informacji, zobacz [Aktywowanie archiwum programu TeleMessage WeChat dla Microsoft 365](https://www.telemessage.com/microsoft-365-activation-for-wechat-archiver/).

- Skonfiguruj łącznik TeleMessage dla Microsoft 365 i uzyskaj prawidłowe konto administracyjne firmy. Aby uzyskać więcej informacji, zobacz [Archiwizowanie Microsoft 365 urządzenia przenośne](https://www.telemessage.com/mobile-archiver/order-mobile-archiver-for-microsoft-365/).

- Zarejestruj wszystkich użytkowników, którzy wymagają archiwizacji weChat na koncie TeleMessage, przy użyciu tego samego adresu e-mail, który jest używany na potrzeby konta Microsoft 365 użytkownika.

- Konieczne będzie zainstalowanie aplikacji Tencent WeCom na telefonach komórkowych użytkowników w organizacji i aktywowanie jej. Aplikacja WeCom umożliwia użytkownikom komunikowanie się i rozmawianie na czacie z innymi użytkownikami weChat i WeCom.

- Użytkownik, który tworzy łącznik programu WeChat Archiver w Centrum zgodności platformy Microsoft 365 musi mieć przypisaną rolę administratora łącznika danych. Ta rola jest wymagana do dodawania łączników na **stronie Łączniki** danych w Centrum zgodności platformy Microsoft 365. Ta rola jest domyślnie dodawana do wielu grup ról. Aby uzyskać listę tych grup ról, zobacz sekcję "Role w centrach zabezpieczeń i zgodności" w sekcji Uprawnienia w Centrum zabezpieczeń & [zgodności](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Administrator w organizacji może również utworzyć niestandardową grupę ról, przypisać rolę administrator łącznika danych, a następnie dodać odpowiednich użytkowników jako członków. Aby uzyskać instrukcje, zobacz sekcję "Tworzenie niestandardowej grupy ról" w sekcji Uprawnienia [w Centrum zgodności platformy Microsoft 365](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Ten łącznik danych TeleMessage jest dostępny w GCC w chmurze dla instytucji rządowych Microsoft 365 USA. Aplikacje i usługi innych firm mogą obejmować przechowywanie, przekazywanie i przetwarzanie danych klienta Organizacji w systemach innych firm, które znajdują się poza infrastrukturą firmy Microsoft 365 i dlatego nie są objęte zobowiązaniami firmy Microsoft 365 w zakresie zgodności z przepisami i ochrony danych. Firma Microsoft nie zapewnia, że używanie tego produktu do łączenia się z aplikacjami innych firm oznacza, że te aplikacje innych firm są zgodne z fedRAMP.

## <a name="create-a-wechat-archiver-connector"></a>Tworzenie łącznika programu WeChat Archiver

Postępuj zgodnie z instrukcjami w tej sekcji, aby utworzyć łącznik programu WeChat Archiver w Centrum zgodności platformy Microsoft 365. Łącznik używa podanej przez Ciebie informacji do łączenia się z witryną TeleMessage i przesyłania danych dotyczących komunikacji z WeChat do odpowiadających im skrzynek pocztowych użytkowników w Microsoft 365.

1. Przejdź do, <https://compliance.microsoft.com> a następnie kliknij **pozycję Łączniki** **danychArchiwizator** >  programuWeChat.

2. Na stronie **opisu produktu archiwum programu WeChat** kliknij pozycję **Dodaj łącznik**.

3. Na stronie **Warunki użytkowania usługi** kliknij pozycję **Zaakceptuj**.

4. Na stronie **Login to TeleMessage** (Logowanie do telemessage) w obszarze Krok 3 wprowadź wymagane informacje w następujących polach, a następnie kliknij przycisk **Dalej**.

    - **Nazwa** użytkownika: Nazwa użytkownika aplikacji TeleMessage.

    - **Hasło**: hasło aplikacji TeleMessage.

5. Po utworzeniu łącznika możesz zamknąć okno podręczne, aby przejść do następnej strony.

6. Na stronie **Mapowanie użytkowników** włącz automatyczne mapowanie użytkowników. Możesz również przekazać plik CSV niestandardowego mapowania użytkowników.

7. Kliknij **przycisk Dalej**, przejrzyj ustawienia, a następnie kliknij przycisk **Zakończ,** aby utworzyć łącznik.

8. Przejdź do karty **Łączniki** na **stronie** Łączniki danych, aby wyświetlić postęp procesu importowania nowego łącznika.

## <a name="known-issues"></a>Znane problemy

- Obecnie importowanie załączników ani elementów większych niż 10 MB nie jest obsługuje. Obsługa większych elementów będzie dostępna w późniejszym terminie.
