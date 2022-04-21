---
title: Konfigurowanie łącznika do archiwizowania błyskawicznych danych bloomberga
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: 04/06/2022
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection: M365-security-compliance
ms.custom: seo-marvel-apr2020
description: Dowiedz się, jak administratorzy mogą konfigurować łącznik danych i używać go do importowania i archiwizowania danych z narzędzia instant bloomberg chat do Microsoft 365.
ms.openlocfilehash: 22b581c332e8accad567bb7eb8b29e57ec981044
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2022
ms.locfileid: "64998137"
---
# <a name="set-up-a-connector-to-archive-instant-bloomberg-data"></a>Konfigurowanie łącznika do archiwizowania błyskawicznych danych bloomberga

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Użyj natywnego łącznika w portalu zgodności usługi Microsoft Purview, aby zaimportować i zarchiwizować dane czatu usług finansowych z narzędzia [instant bloomberg](https://www.bloomberg.com/professional/product/collaboration/) collaboration. Po skonfigurowaniu i skonfigurowaniu łącznika łączy się on z bezpieczną witryną FTP (SFTP) organizacji raz dziennie, konwertuje zawartość wiadomości czatu na format wiadomości e-mail, a następnie importuje te elementy do skrzynek pocztowych w Microsoft 365.

Po zapisaniu danych instant Bloomberg w skrzynkach pocztowych użytkowników można zastosować funkcje usługi Microsoft Purview, takie jak blokada postępowania sądowego, wyszukiwanie zawartości, archiwizowanie In-Place, inspekcja, zgodność z komunikacją i zasady przechowywania Microsoft 365 do danych instant Bloomberg. Możesz na przykład wyszukiwać wiadomości czatu w usłudze Instant Bloomberg przy użyciu wyszukiwania zawartości lub skojarzyć skrzynkę pocztową zawierającą dane instant Bloomberg z opiekunem w przypadku zbierania elektronicznych materiałów dowodowych w usłudze Microsoft Purview (Premium). Użycie łącznika Instant Bloomberg do importowania i archiwizowania danych w Microsoft 365 może pomóc twojej organizacji zachować zgodność z zasadami rządowymi i regulacyjnymi.

## <a name="overview-of-archiving-instant-bloomberg-data"></a>Omówienie archiwizacji błyskawicznych danych bloomberga

W poniższym omówieniu wyjaśniono proces używania łącznika do archiwizowania danych czatu Instant Bloomberg w Microsoft 365. 

![Błyskawiczny proces importowania i archiwizacji bloomberga.](../media/InstantBloombergDataArchiving.png)

1. Twoja organizacja współpracuje z bloombergiem w celu utworzenia witryny Bloomberg SFTP. Będziesz również współpracować z bloombergiem, aby skonfigurować instant Bloomberg do kopiowania wiadomości czatu do witryny Bloomberg SFTP.

2. Raz na 24 godziny, wiadomości czatu z Instant Bloomberg są kopiowane do witryny Bloomberg SFTP.

3. Łącznik Instant Bloomberg tworzony w portalu zgodności codziennie łączy się z witryną Bloomberg SFTP i przesyła komunikaty rozmów z poprzednich 24 godzin do bezpiecznego obszaru usługi Azure Storage w chmurze firmy Microsoft. Łącznik konwertuje również zawartość masażu czatu na format wiadomości e-mail.

4. Łącznik importuje elementy wiadomości czatu do skrzynki pocztowej określonego użytkownika. Nowy folder o nazwie InstantBloomberg jest tworzony w skrzynce pocztowej określonego użytkownika i elementy zostaną do niego zaimportowane. Łącznik wykonuje to przy użyciu wartości właściwości *CorporateEmailAddress* . Każda wiadomość czatu zawiera tę właściwość, która jest wypełniana adresem e-mail każdego uczestnika wiadomości czatu. Oprócz automatycznego mapowania użytkowników przy użyciu wartości właściwości *CorporateEmailAddress* można również zdefiniować mapowanie niestandardowe, przekazując plik mapowania CSV. Ten plik mapowania powinien zawierać identyfikator UUID bloomberga i odpowiedni adres skrzynki pocztowej Microsoft 365 dla każdego użytkownika. Jeśli włączysz automatyczne mapowanie użytkowników i udostępnisz mapowanie niestandardowe, dla każdego elementu czatu łącznik najpierw przyjrzy się plikowi mapowania niestandardowego. Jeśli nie znajdzie prawidłowego użytkownika Microsoft 365, który odpowiada identyfikatorowi UUID bloomberga użytkownika, łącznik *użyje właściwości CorporateEmailAddress* elementu czatu. Jeśli łącznik nie znajdzie prawidłowego użytkownika Microsoft 365 w pliku mapowania niestandardowego lub właściwości *CorporateEmailAddress* elementu czatu, element nie zostanie zaimportowany.

## <a name="before-you-set-up-a-connector"></a>Przed skonfigurowaniem łącznika

Niektóre kroki implementacji wymagane do zarchiwizowania danych instant Bloomberg są zewnętrzne dla Microsoft 365 i muszą zostać ukończone przed utworzeniem łącznika w centrum zgodności.

- Aby skonfigurować łącznik Instant Bloomberg, musisz użyć kluczy i haseł kluczy dla bardzo dobrej prywatności (PGP) i bezpiecznej powłoki (SSH). Te klucze są używane do konfigurowania witryny Bloomberg SFTP i używane przez łącznik do łączenia się z witryną Bloomberg SFTP w celu importowania danych do Microsoft 365. Klucz PGP służy do konfigurowania szyfrowania danych przesyłanych z witryny Bloomberg SFTP do Microsoft 365. Klucz SSH służy do konfigurowania bezpiecznej powłoki w celu włączenia bezpiecznego zdalnego logowania, gdy łącznik nawiązuje połączenie z witryną Bloomberg SFTP.

  Podczas konfigurowania łącznika możesz użyć kluczy publicznych i haseł kluczy udostępnianych przez firmę Microsoft lub użyć własnych kluczy prywatnych i haseł. Zalecamy użycie kluczy publicznych dostarczonych przez firmę Microsoft. Jeśli jednak organizacja już skonfigurowała witrynę Bloomberg SFTP przy użyciu kluczy prywatnych, możesz utworzyć łącznik przy użyciu tych samych kluczy prywatnych.

- Subskrybuj [bloomberg anywhere](https://www.bloomberg.com/professional/product/remote-access/?bbgsum-page=DG-WS-PROF-PROD-BBA). Jest to wymagane, aby można było zalogować się do witryny Bloomberg Anywhere, aby uzyskać dostęp do witryny Bloomberg SFTP, którą należy skonfigurować i skonfigurować.

- Skonfiguruj witrynę Bloomberg SFTP (protokół bezpiecznego transferu plików). Po współpracy z Bloombergiem w celu skonfigurowania witryny SFTP dane z Instant Bloomberg są codziennie przekazywane do witryny SFTP. Łącznik utworzony w kroku 2 łączy się z tą witryną SFTP i przesyła dane czatu do Microsoft 365 skrzynek pocztowych. Protokół SFTP szyfruje również dane czatu Instant Bloomberg wysyłane do skrzynek pocztowych podczas procesu transferu.

  Aby uzyskać informacje o Bloomberg SFTP (zwany również *BB-SFTP*):

  - Zobacz dokument "Standardy łączności SFTP" w witrynie [Bloomberg Support](https://www.bloomberg.com/professional/support/documentation/).

  - Skontaktuj się z [pomocą techniczną bloomberga](https://service.bloomberg.com/portal/sessions/new?utm_source=bloomberg-menu&utm_medium=csc).

  Po współpracy z bloombergiem w celu skonfigurowania witryny SFTP, Bloomberg przekaże Ci pewne informacje po udzieleniu odpowiedzi na wiadomość e-mail dotyczącą implementacji bloomberga. Zapisz kopię poniższych informacji. Służy do konfigurowania łącznika w kroku 3.

  - Kod firmy, który jest identyfikatorem organizacji i służy do logowania się do witryny Bloomberg SFTP.

  - Hasło do witryny Bloomberg SFTP

  - Adres URL witryny Bloomberg SFTP (na przykład sftp.bloomberg.com)

  - Numer portu witryny Bloomberg SFTP

- Łącznik Instant Bloomberg może zaimportować łącznie 200 000 elementów w ciągu jednego dnia. Jeśli w witrynie SFTP znajduje się więcej niż 200 000 elementów, żaden z tych elementów nie zostanie zaimportowany do Microsoft 365.

- Użytkownik, który tworzy łącznik Instant Bloomberg w kroku 3 (i pobiera klucze publiczne i adres IP w kroku 1) musi mieć przypisaną rolę administratora łącznika danych. Ta rola jest wymagana do dodawania łączników na stronie **Łączniki danych** w portalu zgodności. Ta rola jest domyślnie dodawana do wielu grup ról. Aby uzyskać listę tych grup ról, zobacz sekcję "Role w centrach zabezpieczeń i zgodności" w obszarze [Uprawnienia w Centrum zgodności & zabezpieczeń](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternatywnie administrator w organizacji może utworzyć niestandardową grupę ról, przypisać rolę administratora łącznika danych, a następnie dodać odpowiednich użytkowników jako członków. Aby uzyskać instrukcje, zobacz sekcję "Tworzenie niestandardowej grupy ról" w obszarze [Uprawnienia w portalu zgodności usługi Microsoft Purview](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

## <a name="set-up-a-connector-using-public-keys"></a>Konfigurowanie łącznika przy użyciu kluczy publicznych

Kroki opisane w tej sekcji pokazują, jak skonfigurować łącznik Instant Bloomberg przy użyciu kluczy publicznych dla bardzo dobrej prywatności (PGP) i bezpiecznej powłoki (SSH).

### <a name="step-1-obtain-pgp-and-ssh-and-public-keys"></a>Krok 1. Uzyskiwanie kluczy PGP i SSH oraz kluczy publicznych

Pierwszym krokiem jest uzyskanie kopii kluczy publicznych dla bardzo dobrej prywatności (PGP) i bezpiecznej powłoki (SSH). Użyjesz tych kluczy w kroku 2, aby skonfigurować witrynę Bloomberg SFTP, aby umożliwić łącznikowi (utworzonemu w kroku 3) łączenie się z witryną SFTP i przesyłanie danych czatu Instant Bloomberg do Microsoft 365 skrzynek pocztowych. W tym kroku uzyskasz również adres IP używany podczas konfigurowania witryny Bloomberg SFTP.

1. Przejdź do strony <https://compliance.microsoft.com> i kliknij pozycję **Łączniki danych** w lewym pasku nawigacyjnym.

2. Na stronie **Łączniki danych** w obszarze **Instant Bloomberg** kliknij pozycję **Wyświetl**.

3. Na stronie Opis produktu **Instant Bloomberg** kliknij pozycję **Dodaj łącznik**

4. Na stronie **Warunki korzystania z usługi** kliknij pozycję **Akceptuj**.

5. Na stronie **Dodawanie poświadczeń dla źródła zawartości** kliknij **pozycję Chcę użyć kluczy publicznych PGP i SSH dostarczonych przez firmę Microsoft**.

   ![Wybierz opcję używania kluczy publicznych.](../media/InstantBloombergPublicKeysOption.png)

6. W kroku 1 kliknij **pozycję Pobierz klucz SSH**, **pobierz klucz PGP** i pobierz linki **adresów IP** , aby zapisać kopię każdego pliku na komputerze lokalnym.

   ![Linki do pobierania kluczy publicznych i adresu IP.](../media/InstantBloombergPublicKeyDownloadLinks.png)

   Te pliki zawierają następujące elementy, które są używane do konfigurowania witryny Bloomberg SFTP w kroku 2:

   - Klucz publiczny PGP: ten klucz służy do konfigurowania szyfrowania danych przesyłanych z witryny Bloomberg SFTP do Microsoft 365.

   - Klucz publiczny SSH: ten klucz służy do konfigurowania bezpiecznej powłoki w celu włączenia bezpiecznego zdalnego logowania, gdy łącznik łączy się z witryną Bloomberg SFTP.

   - Adres IP: witryna Bloomberg SFTP jest skonfigurowana do akceptowania żądań połączenia z tego adresu IP. Ten sam adres IP jest używany przez łącznik Instant Bloomberg do nawiązywania połączenia z witryną SFTP i przesyłania danych Instant Bloomberg do Microsoft 365.

7. Kliknij **przycisk Anuluj** , aby zamknąć kreatora. Wrócisz do tego kreatora w kroku 3, aby utworzyć łącznik.

### <a name="step-2-configure-the-bloomberg-sftp-site"></a>Krok 2. Konfigurowanie witryny Bloomberg SFTP

Następnym krokiem jest użycie kluczy publicznych PGP i SSH oraz adresu IP uzyskanego w kroku 1 w celu skonfigurowania szyfrowania PGP i uwierzytelniania SSH dla witryny Bloomberg SFTP. Dzięki temu łącznik Instant Bloomberg utworzony w kroku 3 łączy się z witryną Bloomberg SFTP i przesyła dane Instant Bloomberg do Microsoft 365. Aby skonfigurować witrynę Bloomberg SFTP, musisz współpracować z działem obsługi klienta bloomberga. Skontaktuj się z [pomocą techniczną bloomberga](https://service.bloomberg.com/portal/sessions/new?utm_source=bloomberg-menu&utm_medium=csc) , aby uzyskać pomoc. 

> [!IMPORTANT]
> Bloomberg zaleca dołączenie trzech plików pobranych w kroku 1 do wiadomości e-mail i wysłanie ich do zespołu obsługi klienta podczas pracy z nimi w celu skonfigurowania witryny Bloomberg SFTP.

### <a name="step-3-create-an-instant-bloomberg-connector"></a>Krok 3. Tworzenie łącznika Instant Bloomberg

Ostatnim krokiem jest utworzenie łącznika Instant Bloomberg w portalu zgodności. Łącznik używa podanych informacji, aby nawiązać połączenie z witryną Bloomberg SFTP i przenieść wiadomości czatu do odpowiednich skrzynek pocztowych użytkownika w Microsoft 365.

1. Przejdź do obszaru <https://compliance.microsoft.com> , a następnie kliknij pozycję **Łączniki** >  **danychInstant Bloomberg**.

2. Na stronie Opis produktu **Instant Bloomberg** kliknij pozycję **Dodaj łącznik**

3. Na stronie **Warunki korzystania z usługi** kliknij pozycję **Akceptuj**.

4. Na stronie **Dodawanie poświadczeń dla witryny Bloomberg SFTP** w obszarze Krok 3 wprowadź wymagane informacje w poniższych polach, a następnie kliknij przycisk **Dalej**.

    - **Kod firmy:** Identyfikator organizacji, który jest używany jako nazwa użytkownika witryny Bloomberg SFTP.

    - **Hasło:** Hasło do witryny Bloomberg SFTP.

    - **Adres URL protokołu SFTP:** Adres URL witryny Bloomberg SFTP (na przykład `sftp.bloomberg.com`). Możesz również użyć adresu IP dla tej wartości.

    - **Port SFTP:** Numer portu witryny Bloomberg SFTP. Łącznik używa tego portu do nawiązywania połączenia z lokacją SFTP.

5. Na stronie **Definiowanie użytkownika** wybierz jedną z następujących opcji, aby określić użytkowników, których dane chcesz zaimportować.

    - **Wszyscy użytkownicy w organizacji**. Wybierz tę opcję, aby zaimportować dane dla wszystkich użytkowników.

    - **Blokada dotyczy tylko użytkowników w postępowaniu sądowym**. Wybierz tę opcję, aby zaimportować dane tylko dla użytkowników, których skrzynki pocztowe zostały wstrzymane w postępowaniu sądowym. Ta opcja importuje dane do skrzynek pocztowych użytkowników z właściwością LitigationHoldEnabled ustawioną na wartość True. Aby uzyskać więcej informacji, zobacz [Tworzenie blokady postępowania sądowego](create-a-litigation-hold.md).

6. Na stronie **Wybieranie typów danych do zaimportowania** wybierz wymagane typy danych do zaimportowania oprócz pozycji **Komunikaty**

7. Na stronie **Mapowanie błyskawicznych użytkowników bloomberga w celu Microsoft 365 użytkowników** włącz automatyczne mapowanie użytkowników i w razie potrzeby udostępnij niestandardowe mapowanie użytkowników

   > [!NOTE]
   > Łącznik importuje elementy wiadomości czatu do skrzynki pocztowej określonego użytkownika. Nowy folder o nazwie **InstantBloomberg** jest tworzony w skrzynce pocztowej określonego użytkownika i elementy zostaną do niego zaimportowane. Łącznik jest używany przy użyciu wartości właściwości *CorporateEmailAddress* . Każda wiadomość czatu zawiera tę właściwość, a właściwość jest wypełniana adresem e-mail każdego uczestnika wiadomości czatu. Oprócz automatycznego mapowania użytkowników przy użyciu wartości właściwości *CorporateEmailAddress* można również zdefiniować mapowanie niestandardowe, przekazując plik mapowania CSV. Plik mapowania powinien zawierać identyfikator UUID bloomberga i odpowiedni adres skrzynki pocztowej Microsoft 365 dla każdego użytkownika. Jeśli włączysz automatyczne mapowanie użytkowników i udostępnisz mapowanie niestandardowe, dla każdego elementu czatu łącznik najpierw przyjrzy się niestandardowemu plikowi mapowania. Jeśli nie znajdzie prawidłowego użytkownika Microsoft 365, który odpowiada identyfikatorowi UUID bloomberga użytkownika, łącznik *użyje właściwości CorporateEmailAddress* elementu czatu. Jeśli łącznik nie znajdzie prawidłowego użytkownika Microsoft 365 w niestandardowym pliku mapowania lub we właściwości *CorporateEmailAddress* elementu czatu, element nie zostanie zaimportowany.

7. Kliknij **przycisk Dalej**, przejrzyj ustawienia, a następnie kliknij przycisk **Zakończ** , aby utworzyć łącznik.

8. Przejdź do strony **Łączniki danych** , aby zobaczyć postęp procesu importowania nowego łącznika. Kliknij łącznik, aby wyświetlić stronę wysuwaną zawierającą informacje o łączniku.

## <a name="set-up-a-connector-using-private-keys"></a>Konfigurowanie łącznika przy użyciu kluczy prywatnych

Kroki opisane w tej sekcji pokazują, jak skonfigurować łącznik Instant Bloomberg przy użyciu kluczy prywatnych PGP i SSH. Ta opcja konfiguracji łącznika jest przeznaczona dla organizacji, które już skonfigurowały witrynę Bloomberg SFTP przy użyciu kluczy prywatnych.

### <a name="step-1-obtain-an-ip-address-to-configure-the-bloomberg-sftp-site"></a>Krok 1. Uzyskiwanie adresu IP w celu skonfigurowania witryny Bloomberg SFTP

> [!NOTE]
> Jeśli twoja organizacja wcześniej skonfigurowała witrynę Bloomberg SFTP do archiwizowania danych komunikatów Bloomberg przy użyciu kluczy prywatnych PGP i SSH, nie musisz konfigurować kolejnej. Tę samą lokację SFTP można określić podczas tworzenia łącznika w kroku 2.

Jeśli Twoja organizacja użyła kluczy prywatnych PGP i SSH do skonfigurowania witryny Bloomberg SFTP, musisz uzyskać adres IP i przekazać go do pomocy technicznej bloomberga. Witryna Bloomberg SFTP musi być skonfigurowana do akceptowania żądań połączenia z tego adresu IP. Ten sam adres IP jest używany przez łącznik Instant Bloomberg do nawiązywania połączenia z witryną SFTP i przesyłania danych Instant Bloomberg do Microsoft 365.

Aby uzyskać adres IP:

1. Przejdź do strony <https://compliance.microsoft.com> i kliknij pozycję **Łączniki danych** w lewym pasku nawigacyjnym.

2. Na stronie **Łączniki danych** w obszarze **Instant Bloomberg** kliknij pozycję **Wyświetl**.

3. Na stronie Opis produktu **Instant Bloomberg** kliknij pozycję **Dodaj łącznik**

4. Na stronie **Warunki korzystania z usługi** kliknij pozycję **Akceptuj**.

5. Na stronie **Dodawanie poświadczeń dla źródła zawartości** kliknij **pozycję Chcę używać kluczy prywatnych PGP i SSH**.

6. W kroku 1 kliknij pozycję **Pobierz adres IP** , aby zapisać kopię pliku adresu IP na komputerze lokalnym.

   ![Pobierz adres IP.](../media/InstantBloombergConnectorIPAddress.png)

7. Kliknij **przycisk Anuluj** , aby zamknąć kreatora. Wrócisz do tego kreatora w kroku 2, aby utworzyć łącznik.

Aby skonfigurować witrynę Bloomberg SFTP do akceptowania żądań połączeń z tego adresu IP, musisz współpracować z działem obsługi klienta bloomberga. Skontaktuj się z [pomocą techniczną bloomberga](https://service.bloomberg.com/portal/sessions/new?utm_source=bloomberg-menu&utm_medium=csc) , aby uzyskać pomoc.

### <a name="step-2-create-an-instant-bloomberg-connector"></a>Krok 2. Tworzenie łącznika Instant Bloomberg

Po skonfigurowaniu witryny Bloomberg SFTP następnym krokiem jest utworzenie łącznika Instant Bloomberg w portalu zgodności. Łącznik używa podanych informacji, aby nawiązać połączenie z witryną Bloomberg SFTP i przenieść wiadomości e-mail do odpowiednich skrzynek pocztowych użytkownika w Microsoft 365. Aby wykonać ten krok, upewnij się, że masz kopie tych samych kluczy prywatnych i haseł kluczy, których użyto do skonfigurowania witryny Bloomberg SFTP.

1. Przejdź do strony <https://compliance.microsoft.com> i kliknij pozycję **Łączniki danych** w lewym pasku nawigacyjnym.

2. Na stronie **Łączniki danych** w obszarze **Instant Bloomberg** kliknij pozycję **Wyświetl**.

3. Na stronie Opis produktu **Instant Bloomberg** kliknij pozycję **Dodaj łącznik**

4. Na stronie **Warunki korzystania z usługi** kliknij pozycję **Akceptuj**.

5. Na stronie **Dodawanie poświadczeń dla źródła zawartości** kliknij **pozycję Chcę używać kluczy prywatnych PGP i SSH**.

   ![Wybierz opcję używania kluczy prywatnych.](../media/InstantBloombergPrivateKeysOption.png)

6. W obszarze Krok 3 wprowadź wymagane informacje w poniższych polach, a następnie kliknij pozycję **Weryfikuj połączenie**.

      - **Nazwa:** Nazwa łącznika. Musi być unikatowa w organizacji.

      - **Kod firmy:** Identyfikator organizacji, który jest używany jako nazwa użytkownika witryny Bloomberg SFTP.

      - **Hasło:** Hasło do witryny Bloomberg SFTP organizacji.

      - **Adres URL protokołu SFTP:** Adres URL witryny Bloomberg SFTP (na przykład `sftp.bloomberg.com`). Możesz również użyć adresu IP dla tej wartości.

      - **Port SFTP:** Numer portu witryny Bloomberg SFTP. Łącznik używa tego portu do nawiązywania połączenia z lokacją SFTP.

      - **Klucz prywatny PGP:** Klucz prywatny PGP dla witryny Bloomberg SFTP. Pamiętaj o uwzględnieniu całej wartości klucza prywatnego, w tym początkowych i końcowych wierszy bloku kluczy.

      - **Hasło klucza PGP:** Hasło klucza prywatnego PGP.

      - **Klucz prywatny SSH:** Klucz prywatny SSH dla witryny Bloomberg SFTP. Pamiętaj o uwzględnieniu całej wartości klucza prywatnego, w tym początkowych i końcowych wierszy bloku kluczy.

      - **Hasło klucza SSH:** Hasło klucza prywatnego SSH.

7. Po pomyślnym zweryfikowaniu połączenia kliknij przycisk **Dalej**.

8. Na stronie **Definiowanie użytkownika** wybierz jedną z następujących opcji, aby określić użytkowników, których dane chcesz zaimportować.

    - **Wszyscy użytkownicy w organizacji**. Wybierz tę opcję, aby zaimportować dane dla wszystkich użytkowników.

    - **Blokada dotyczy tylko użytkowników w postępowaniu sądowym**. Wybierz tę opcję, aby zaimportować dane tylko dla użytkowników, których skrzynki pocztowe zostały wstrzymane w postępowaniu sądowym. Ta opcja importuje dane do skrzynek pocztowych użytkowników z właściwością LitigationHoldEnabled ustawioną na wartość True. Aby uzyskać więcej informacji, zobacz [Tworzenie blokady postępowania sądowego](create-a-litigation-hold.md).

9. Na stronie **Mapowanie błyskawicznych użytkowników bloomberga w celu Microsoft 365 użytkowników** włącz automatyczne mapowanie użytkowników i w razie potrzeby udostępnij niestandardowe mapowanie użytkowników.

   > [!NOTE]
   > Łącznik importuje elementy wiadomości czatu do skrzynki pocztowej określonego użytkownika. Nowy folder o nazwie **InstantBloomberg** jest tworzony w skrzynce pocztowej określonego użytkownika i elementy zostaną do niego zaimportowane. Łącznik jest używany przy użyciu wartości właściwości *CorporateEmailAddress* . Każda wiadomość czatu zawiera tę właściwość, a właściwość jest wypełniana adresem e-mail każdego uczestnika wiadomości czatu. Oprócz automatycznego mapowania użytkowników przy użyciu wartości właściwości *CorporateEmailAddress* można również zdefiniować mapowanie niestandardowe, przekazując plik mapowania CSV. Plik mapowania powinien zawierać identyfikator UUID bloomberga i odpowiedni adres skrzynki pocztowej Microsoft 365 dla każdego użytkownika. Jeśli włączysz automatyczne mapowanie użytkowników i udostępnisz mapowanie niestandardowe, dla każdego elementu czatu łącznik najpierw przyjrzy się niestandardowemu plikowi mapowania. Jeśli nie znajdzie prawidłowego użytkownika Microsoft 365, który odpowiada identyfikatorowi UUID bloomberga użytkownika, łącznik *użyje właściwości CorporateEmailAddress* elementu czatu. Jeśli łącznik nie znajdzie prawidłowego użytkownika Microsoft 365 w niestandardowym pliku mapowania lub we właściwości *CorporateEmailAddress* elementu czatu, element nie zostanie zaimportowany.

10. Kliknij **przycisk Dalej**, przejrzyj ustawienia, a następnie kliknij przycisk **Zakończ** , aby utworzyć łącznik.

11. Przejdź do strony **Łączniki danych** , aby zobaczyć postęp procesu importowania nowego łącznika. Kliknij łącznik, aby wyświetlić stronę wysuwaną zawierającą informacje o łączniku.
