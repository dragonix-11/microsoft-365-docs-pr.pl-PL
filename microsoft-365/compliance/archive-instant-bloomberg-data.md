---
title: Konfigurowanie łącznika do archiwizowania danych błyskawicznego kwiatowej góry
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
search.appverid:
- MET150
ms.collection: M365-security-compliance
ms.custom: seo-marvel-apr2020
description: Dowiedz się, jak administratorzy mogą skonfigurować łącznik danych i używać go do importowania i archiwizowania danych z narzędzia czatu Instant Bloomberg w programie Microsoft 365.
ms.openlocfilehash: 14495a219ce73b8d0cd4e937b4feae9aa2210da1
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63313331"
---
# <a name="set-up-a-connector-to-archive-instant-bloomberg-data"></a>Konfigurowanie łącznika do archiwizowania danych błyskawicznego kwiatowej góry

Użyj natywnego łącznika w Centrum zgodności platformy Microsoft 365 do importowania i archiwizowania danych czatu usług finansowych za pomocą narzędzia do współpracy [Błyskawicznej Bloomberg](https://www.bloomberg.com/professional/product/collaboration/). Po skonfigurowaniu i skonfigurowaniu łącznika połączy się on z witryną BLOOMberg secure FTP (SFTP) Twojej organizacji raz dziennie, konwertuje zawartość wiadomości czatu na format wiadomości e-mail, a następnie importuje te elementy do skrzynek pocztowych w programie Microsoft 365.

Po zapisaniu danych Błyskawicznego rozkwitania ( Instant Bloomberg) w skrzynkach pocztowych użytkowników możesz zastosować funkcje zgodności usługi Microsoft 365, takie jak archiwizacja w związku z postępowaniem sądowym, wyszukiwanie zawartości, In-Place archiwizowanie, inspekcja, zgodność z komunikacją i zasady przechowywania Microsoft 365 do danych Błyskawicznego rozkwitania. Możesz na przykład przeszukać wiadomości czatu Błyskawicznego Bloomberga za pomocą funkcji przeszukiwania zawartości lub skojarzyć skrzynkę pocztową zawierającą dane błyskawicznego Kwiatberga ze współpracownikiem w Advanced eDiscovery przypadku. Importowanie i archiwizowanie danych w programie Microsoft 365 za pomocą łącznika błyskawicznego Bloomberga może ułatwić organizacji zachowania zgodności z zasadami rządowymi i przepisami prawa.

## <a name="overview-of-archiving-instant-bloomberg-data"></a>Omówienie archiwizowania danych błyskawicznego rozkwitania góry

Poniższe omówienie przedstawia proces używania łącznika do archiwizowania danych czatu Błyskawicznego Bloomberga w programie Microsoft 365. 

![Błyskawiczne importowanie i archiwizowanie materiałów bloomberg.](../media/InstantBloombergDataArchiving.png)

1. Twoja organizacja współpracuje z Bloombergiem, aby skonfigurować witrynę Bloomberg SFTP. Wraz z Bloombergiem skonfigurujesz błyskawiczną bloombergę w celu kopiowania wiadomości czatu do twojej witryny Bloomberg SFTP.

2. Co 24 godziny wiadomości czatu z błyskawicznej bloomberga są kopiowane do witryny Bloomberg SFTP.

3. Łącznik błyskawicznego Bloomberga, który tworzysz w programie Centrum zgodności platformy Microsoft 365, łączy się z witryną Bloomberg SFTP codziennie i przesyła wiadomości czatu z poprzednich 24 godzin do bezpiecznego obszaru usługi Azure Storage w chmurze firmy Microsoft. Łącznik konwertuje także treść wiadomości czatu na format wiadomości e-mail.

4. Łącznik zaim importuje elementy wiadomości czatu do skrzynki pocztowej określonego użytkownika. W skrzynce pocztowej określonego użytkownika zostanie utworzony nowy folder o nazwie InstantBloomberg i elementy zostaną do niego zaimportowane. Łącznik działa przy użyciu wartości właściwości *CorporateEmailAddress* . Każda wiadomość czatu zawiera tę właściwość, która jest wypełniana adresem e-mail każdego uczestnika wiadomości czatu. Oprócz automatycznego mapowania użytkowników przy użyciu wartości właściwości *CorporateEmailAddress* możesz również zdefiniować mapowanie niestandardowe, przesyłając plik mapowania CSV. Ten plik mapowania powinien zawierać identyfikator UUID Bloomberga i Microsoft 365 adres skrzynki pocztowej dla każdego użytkownika. Jeśli włączysz automatyczne mapowanie użytkowników i udostępnisz mapowanie niestandardowe, dla każdego elementu czatu łącznik najpierw przyjrzy się plikowi mapowania niestandardowego. Jeśli użytkownik nie znajdzie prawidłowego Microsoft 365 odpowiadającego identyfikatorowi UUID użytkownika Bloomberga, łącznik użyje właściwości *CorporateEmailAddress* elementu czatu. Jeśli łącznik nie znajdzie prawidłowego użytkownika Microsoft 365 w pliku mapowania niestandardowego lub właściwości *CorporateEmailAddress* elementu czatu, element nie zostanie zaimportowany.

## <a name="before-you-set-up-a-connector"></a>Przed skonfigurowaniem łącznika

Niektóre kroki implementacji wymagane do archiwizacji danych błyskawicznego Bloomberga znajdują się poza Microsoft 365 i muszą zostać ukończone, zanim będzie można utworzyć łącznik w centrum zgodności.

- Aby skonfigurować łącznik Instant Bloomberg, musisz używać klawiszy i kluczowych zwrotów dla plików PGP (Pretty Good Privacy) i Secure Shell (SSH). Te klucze są używane do konfigurowania witryny Bloomberg SFTP i używane przez łącznik do łączenia się z witryną Bloomberg SFTP w celu importowania danych do Microsoft 365. Klawisz PGP służy do konfigurowania szyfrowania danych przesyłanych z witryny Bloomberg SFTP do Microsoft 365. Klawisz SSH służy do konfigurowania bezpiecznej powłoki w celu umożliwienia bezpiecznego logowania zdalnego, gdy łącznik łączy się z witryną Bloomberg SFTP.

  Podczas konfigurowania łącznika możesz używać kluczy publicznych i kluczowych zwrotów dostarczanych przez firmę Microsoft lub możesz używać własnych kluczy prywatnych i zwrotów. Zalecamy używanie kluczy publicznych dostarczonych przez firmę Microsoft. Jednak jeśli organizacja skonfigurowała już witrynę Bloomberg SFTP przy użyciu kluczy prywatnych, możesz utworzyć łącznik, używając tych samych kluczy prywatnych.

- [Zasubskrybuj usługę Bloomberg Anywhere](https://www.bloomberg.com/professional/product/remote-access/?bbgsum-page=DG-WS-PROF-PROD-BBA). Jest to wymagane, aby można było zalogować się do bloomberg Anywhere, aby uzyskać dostęp do witryny Bloomberg SFTP, która jest wymagana do skonfigurowania i skonfigurowania.

- Skonfiguruj witrynę Bloomberg SFTP (Secure file transfer protocol). Po pracy z Bloombergiem w celu skonfigurowania witryny SFTP dane z błyskawicznego Bloomberga są codziennie przekazywane do tej witryny. Łącznik, który utworzysz w kroku 2, połączy się z tą witryną SFTP i przeniesie dane czatu do Microsoft 365 pocztowych. SfTP szyfruje również dane czatu Błyskawicznego Bloomberga, które są wysyłane do skrzynek pocztowych podczas procesu przenoszenia.

  Aby uzyskać informacje na temat Bloomberg SFTP (nazywanej również *BB-SFTP*):

  - Zobacz dokument "SFTP Connectivity Standards" (Standardy łączności SFTP) w oknie [pomocy technicznej Bloomberga](https://www.bloomberg.com/professional/support/documentation/).

  - Skontaktuj [się z działem obsługi klienta Bloomberg](https://service.bloomberg.com/portal/sessions/new?utm_source=bloomberg-menu&utm_medium=csc).

  Po zakończeniu współpracy z Bloombergiem w celu skonfigurowania witryny SFTP, Bloomberg udostępni Ci pewne informacje, gdy odpowiesz na wiadomość e-mail implementacji Bloomberga. Zapisz kopię poniższych informacji. Za jego pomocą możesz skonfigurować łącznik w kroku 3.

  - Firmowy kod, który jest identyfikatorem Twojej organizacji i jest używany do logowania się do witryny Bloomberg SFTP.

  - Hasło do witryny Bloomberg SFTP

  - Adres URL witryny Bloomberg SFTP (na przykład sftp.bloomberg.com)

  - Numer portu witryny Bloomberg SFTP

- Łącznik Instant Bloomberg może zaimportować łącznie 200 000 elementów w jednym dniu. Jeśli w witrynie SFTP istnieje więcej niż 200 000 elementów, żadne z tych elementów nie zostaną zaimportowane do Microsoft 365.

- Użytkownik, który w kroku 3 (i który pobiera klucze publiczne i adres IP w kroku 1), musi mieć przypisaną rolę administratora łącznika danych. Ta rola jest wymagana do dodawania łączników na **stronie Łączniki** danych w Centrum zgodności platformy Microsoft 365. Ta rola jest domyślnie dodawana do wielu grup ról. Aby uzyskać listę tych grup ról, zobacz sekcję "Role w centrach zabezpieczeń i zgodności" w sekcji Uprawnienia w Centrum zabezpieczeń & [zgodności](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Administrator w organizacji może również utworzyć niestandardową grupę ról, przypisać rolę administrator łącznika danych, a następnie dodać odpowiednich użytkowników jako członków. Aby uzyskać instrukcje, zobacz sekcję "Tworzenie niestandardowej grupy ról" w sekcji Uprawnienia [w Centrum zgodności platformy Microsoft 365](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

## <a name="set-up-a-connector-using-public-keys"></a>Konfigurowanie łącznika przy użyciu kluczy publicznych

W tej sekcji opisano sposób skonfigurowania łącznika błyskawicznego Bloomberga przy użyciu kluczy publicznych dla plików PGP (Pretty Good Privacy) i Secure Shell (SSH).

### <a name="step-1-obtain-pgp-and-ssh-and-public-keys"></a>Krok 1. Uzyskiwanie PGP i SSH oraz kluczy publicznych

Pierwszym krokiem jest uzyskanie kopii kluczy publicznych dla plików PGP (Pretty Good Privacy) i Secure Shell (SSH). Za pomocą tych kluczy w kroku 2 konfigurujesz witrynę Bloomberg SFTP, aby umożliwić łącznikowi (który został przez Ciebie przez Ciebie utworzyć w kroku 3) łączenie się z witryną SFTP i przenoszenie danych czatu Błyskawicznego Bloomberga do skrzynek pocztowych Microsoft 365 pocztowych. Adres IP uzyskasz również w tym kroku, którego używasz podczas konfigurowania witryny Bloomberg SFTP.

1. Przejdź do łączników <https://compliance.microsoft.com> **danych w lewym okienku narracji i** kliknij je.

2. Na stronie **Łączniki danych** w obszarze **Błyskawiczna góra kwiatowa** kliknij pozycję **Widok**.

3. Na stronie **opisowej produktu Instant Bloomberg** kliknij pozycję **Dodaj łącznik**.

4. Na stronie **Warunki użytkowania usługi** kliknij pozycję **Zaakceptuj**.

5. Na stronie **Dodaj poświadczenia dla źródła** zawartości kliknij pozycję Chcę używać kluczy publicznych **PGP i SSH dostarczonych przez firmę Microsoft**.

   ![Wybierz opcję, aby użyć kluczy publicznych.](../media/InstantBloombergPublicKeysOption.png)

6. W obszarze krok 1 kliknij linki Pobierz **klucz SSH**, Pobierz klucz **PGP** i Pobierz adres **IP** , aby zapisać kopię każdego pliku na komputerze lokalnym.

   ![Linki do pobierania kluczy publicznych i adresu IP.](../media/InstantBloombergPublicKeyDownloadLinks.png)

   Te pliki zawierają następujące elementy używane do konfigurowania witryny Bloomberg SFTP w kroku 2:

   - Klucz publiczny PGP: Ten klucz służy do konfigurowania szyfrowania danych przesyłanych z witryny Bloomberg SFTP do Microsoft 365.

   - Klucz publiczny SSH: Ten klucz służy do konfigurowania bezpiecznej powłoki w celu umożliwienia bezpiecznego logowania zdalnego, gdy łącznik łączy się z witryną Bloomberg SFTP.

   - Adres IP: Witryna Bloomberg SFTP jest skonfigurowana do akceptowania żądań połączenia z tego adresu IP. Ten sam adres IP jest używany przez łącznik Instant Bloomberga do łączenia się z witryną SFTP i przesyłania danych Błyskawicznego Bloomberga do Microsoft 365.

7. Kliknij **przycisk Anuluj** , aby zamknąć kreatora. Powrócisz do tego kreatora w kroku 3, aby utworzyć łącznik.

### <a name="step-2-configure-the-bloomberg-sftp-site"></a>Krok 2. Konfigurowanie witryny Bloomberg SFTP

Następnym krokiem jest użycie kluczy publicznych PGP i SSH oraz adresu IP uzyskanego w kroku 1 w celu skonfigurowania szyfrowania PGP i uwierzytelniania SSH dla witryny Bloomberg SFTP. Dzięki temu łącznik błyskawicznego Bloomberga (Instant Bloomberg) utworzyć w kroku 3, połączy się z witryną Bloomberg SFTP i przekieruje dane błyskawicznego Bloomberga do Microsoft 365. Aby skonfigurować witrynę Bloomberg SFTP, musisz współpracować z działem obsługi klienta Bloomberg. Skontaktuj [się z działem obsługi klienta Bloomberg,](https://service.bloomberg.com/portal/sessions/new?utm_source=bloomberg-menu&utm_medium=csc) aby uzyskać pomoc. 

> [!IMPORTANT]
> Bloomberg zaleca, aby dołączyć trzy pliki pobrane w kroku 1 do wiadomości e-mail i wysłać je do zespołu obsługi klienta podczas współpracy z nimi w celu skonfigurowania witryny Bloomberg SFTP.

### <a name="step-3-create-an-instant-bloomberg-connector"></a>Krok 3. Tworzenie łącznika błyskawicznego Bloomberga

Ostatnim krokiem jest utworzenie łącznika błyskawicznego Bloomberga w Centrum zgodności platformy Microsoft 365. Łącznik używa podanej informacji do nawiązania połączenia z witryną Bloomberg SFTP i przeniesienia wiadomości czatu do odpowiednich skrzynek pocztowych użytkowników w programie Microsoft 365.

1. Przejdź do, <https://compliance.microsoft.com> a następnie kliknij pozycję **Łączniki danychInstant** >  **Bloomberg**.

2. Na stronie **opisowej produktu Instant Bloomberg** kliknij pozycję **Dodaj łącznik**.

3. Na stronie **Warunki użytkowania usługi** kliknij pozycję **Zaakceptuj**.

4. Na stronie **Dodawanie poświadczeń dla witryny Bloomberg SFTP** w obszarze Krok 3 wprowadź wymagane informacje w poniższych polach, a następnie kliknij przycisk **Dalej**.

    - **Kod firmy:** Identyfikator organizacji używany jako nazwa użytkownika witryny Bloomberg SFTP.

    - **Hasło:** Hasło do witryny Bloomberg SFTP.

    - **SFTP URL:** Adres URL witryny Bloomberg SFTP (na przykład `sftp.bloomberg.com`). W tej wartości możesz również użyć adresu IP.

    - **Port SFTP:** Numer portu witryny Bloomberg SFTP. Łącznik używa tego portu do łączenia się z witryną SFTP.

5. Na **stronie Wybierz typy danych do zaimportowania** wybierz wymagane typy danych do zaimportowania **oprócz wiadomości**

6. Na stronie **Błyskawiczne mapowanie użytkowników bloomberga** do Microsoft 365 użytkowników włącz automatyczne mapowanie użytkowników i zapewnij niestandardowe mapowanie użytkowników zgodnie z wymaganiami.

   > [!NOTE]
   > Łącznik zaim importuje elementy wiadomości czatu do skrzynki pocztowej określonego użytkownika. W skrzynce pocztowej określonego użytkownika zostanie utworzony nowy folder o nazwie **InstantBloomberg** i elementy zostaną do niego zaimportowane. Łącznik działa przy użyciu wartości właściwości *CorporateEmailAddress* . Każda wiadomość czatu zawiera tę właściwość, a jej adres e-mail zostanie wypełniony adresem e-mail każdego uczestnika wiadomości czatu. Oprócz automatycznego mapowania użytkowników przy użyciu wartości właściwości *CorporateEmailAddress* możesz także zdefiniować mapowanie niestandardowe, przesyłając plik mapowania plików CSV. Plik mapowania powinien zawierać identyfikator UUID Bloomberga i odpowiedni Microsoft 365 adres skrzynki pocztowej dla każdego użytkownika. Jeśli włączysz automatyczne mapowanie użytkowników i udostępnisz mapowanie niestandardowe, dla każdego elementu czatu łącznik najpierw przyjrzy się plikowi mapowania niestandardowego. Jeśli użytkownik nie znajdzie prawidłowego Microsoft 365 odpowiadającego identyfikatorowi UUID użytkownika Bloomberga, łącznik użyje właściwości *CorporateEmailAddress* elementu czatu. Jeśli łącznik nie znajdzie prawidłowego użytkownika Microsoft 365 w pliku mapowania niestandardowego lub właściwości *CorporateEmailAddress* elementu czatu, element nie zostanie zaimportowany.

7. Kliknij **przycisk Dalej**, przejrzyj ustawienia, a następnie kliknij przycisk **Zakończ,** aby utworzyć łącznik.

8. Przejdź do **strony Łączniki** danych, aby wyświetlić postęp procesu importowania nowego łącznika. Kliknij łącznik, aby wyświetlić stronę wysuwu zawierającą informacje o łączniku.

## <a name="set-up-a-connector-using-private-keys"></a>Konfigurowanie łącznika przy użyciu kluczy prywatnych

W krokach w tej sekcji popisano, jak skonfigurować łącznik instant Bloomberg przy użyciu kluczy prywatnych PGP i SSH. Ta opcja konfiguracji łącznika jest przeznaczona dla organizacji, które już skonfigurowały witrynę Bloomberg SFTP przy użyciu kluczy prywatnych.

### <a name="step-1-obtain-an-ip-address-to-configure-the-bloomberg-sftp-site"></a>Krok 1. Uzyskiwanie adresu IP w celu skonfigurowania witryny Bloomberg SFTP

> [!NOTE]
> Jeśli Twoja organizacja skonfigurowała wcześniej witrynę Bloomberg SFTP do archiwizowania danych wiadomości Bloomberga przy użyciu kluczy prywatnych PGP i SSH, nie musisz konfigurować innej. Tę samą witrynę SFTP można określić podczas tworzenia łącznika w kroku 2.

Jeśli Twoja organizacja użyła kluczy prywatnych PGP i SSH do skonfigurowania witryny Bloomberg SFTP, musisz uzyskać adres IP i przekazać go działowi obsługi klienta Bloomberg. Witryna Bloomberg SFTP musi być skonfigurowana do akceptowania żądań połączeń z tego adresu IP. Ten sam adres IP jest używany przez łącznik Instant Bloomberga do łączenia się z witryną SFTP i przesyłania danych Błyskawicznego Bloomberga do Microsoft 365.

Aby uzyskać adres IP:

1. Przejdź do łączników <https://compliance.microsoft.com> **danych w lewym okienku narracji i** kliknij je.

2. Na stronie **Łączniki danych** w obszarze **Błyskawiczna góra kwiatowa** kliknij pozycję **Widok**.

3. Na stronie **opisowej produktu Instant Bloomberg** kliknij pozycję **Dodaj łącznik**.

4. Na stronie **Warunki użytkowania usługi** kliknij pozycję **Zaakceptuj**.

5. Na stronie **Dodaj poświadczenia dla źródła zawartości** kliknij pozycję **Chcę używać kluczy prywatnych PGP i SSH**.

6. W obszarze krok 1 kliknij pozycję **Pobierz adres IP** , aby zapisać kopię pliku adresu IP na komputerze lokalnym.

   ![Pobierz adres IP.](../media/InstantBloombergConnectorIPAddress.png)

7. Kliknij **przycisk Anuluj** , aby zamknąć kreatora. Powrócisz do tego kreatora w kroku 2, aby utworzyć łącznik.

Musisz współpracować z działem obsługi klienta Bloomberg, aby skonfigurować witrynę Bloomberg SFTP w celu akceptowania żądań połączeń z tego adresu IP. Skontaktuj [się z działem obsługi klienta Bloomberg,](https://service.bloomberg.com/portal/sessions/new?utm_source=bloomberg-menu&utm_medium=csc) aby uzyskać pomoc.

### <a name="step-2-create-an-instant-bloomberg-connector"></a>Krok 2. Tworzenie łącznika błyskawicznego Bloomberga

Po skonfigurowaniu witryny Bloomberg SFTP następnym krokiem jest utworzenie łącznika błyskawicznego Bloomberg w Centrum zgodności platformy Microsoft 365. Łącznik używa podanych informacji do nawiązania połączenia z witryną Bloomberg SFTP i przeniesienia wiadomości e-mail do odpowiednich skrzynek pocztowych użytkowników w programie Microsoft 365. Aby wykonać ten krok, upewnij się, że masz kopie tych samych kluczy prywatnych i kluczowych zwrotów, które zostały użyte do skonfigurowania Twojej witryny Bloomberg SFTP.

1. Przejdź do łączników <https://compliance.microsoft.com> **danych w lewym okienku narracji i** kliknij je.

2. Na stronie **Łączniki danych** w obszarze **Błyskawiczna góra kwiatowa** kliknij pozycję **Widok**.

3. Na stronie **opisowej produktu Instant Bloomberg** kliknij pozycję **Dodaj łącznik**.

4. Na stronie **Warunki użytkowania usługi** kliknij pozycję **Zaakceptuj**.

5. Na stronie **Dodaj poświadczenia dla źródła zawartości** kliknij pozycję **Chcę używać kluczy prywatnych PGP i SSH**.

   ![Wybierz opcję, aby użyć kluczy prywatnych.](../media/InstantBloombergPrivateKeysOption.png)

6. W obszarze Krok 3 wprowadź wymagane informacje w następujących polach, a następnie kliknij pozycję **Sprawdź poprawność połączenia**.

      - **Nazwa:** Nazwa łącznika. Musi być unikatowy w Twojej organizacji.

      - **Kod firmy:** Identyfikator organizacji używany jako nazwa użytkownika witryny Bloomberg SFTP.

      - **Hasło:** Hasło do witryny Bloomberg SFTP Twojej organizacji.

      - **SFTP URL:** Adres URL witryny Bloomberg SFTP (na przykład `sftp.bloomberg.com`). W tej wartości możesz również użyć adresu IP.

      - **Port SFTP:** Numer portu witryny Bloomberg SFTP. Łącznik używa tego portu do łączenia się z witryną SFTP.

      - **Klucz prywatny PGP:** Klucz prywatny PGP dla witryny Bloomberg SFTP. Pamiętaj o uwzględnieniu całej wartości klucza prywatnego, łącznie z pierwszym i końcową łącznie z blokiem klucza.

      - **Hasło klucza PGP:** Kod dostępu do klucza prywatnego PGP.

      - **Klucz prywatny SSH:** Klucz prywatny SSH dla witryny Bloomberg SFTP. Pamiętaj o uwzględnieniu całej wartości klucza prywatnego, łącznie z pierwszym i końcową łącznie z blokiem klucza.

      - **Kluczowy zwrot SSH:** Kod dostępu do klucza prywatnego SSH.

7. Po pomyślnym weryfikacji połączenia kliknij przycisk **Dalej**.

8. Na stronie **Błyskawiczne mapowanie użytkowników witryny Bloomberg do Microsoft 365 użytkowników** włącz automatyczne mapowanie użytkowników i w razie potrzeby zapewnij niestandardowe mapowanie użytkowników.

   > [!NOTE]
   > Łącznik zaim importuje elementy wiadomości czatu do skrzynki pocztowej określonego użytkownika. W skrzynce pocztowej określonego użytkownika zostanie utworzony nowy folder o nazwie **InstantBloomberg** i elementy zostaną do niego zaimportowane. Łącznik działa przy użyciu wartości właściwości *CorporateEmailAddress* . Każda wiadomość czatu zawiera tę właściwość, a jej adres e-mail zostanie wypełniony adresem e-mail każdego uczestnika wiadomości czatu. Oprócz automatycznego mapowania użytkowników przy użyciu wartości właściwości *CorporateEmailAddress* możesz także zdefiniować mapowanie niestandardowe, przesyłając plik mapowania plików CSV. Plik mapowania powinien zawierać identyfikator UUID Bloomberga i odpowiedni Microsoft 365 adres skrzynki pocztowej dla każdego użytkownika. Jeśli włączysz automatyczne mapowanie użytkowników i udostępnisz mapowanie niestandardowe, dla każdego elementu czatu łącznik najpierw przyjrzy się plikowi mapowania niestandardowego. Jeśli użytkownik nie znajdzie prawidłowego Microsoft 365 odpowiadającego identyfikatorowi UUID użytkownika Bloomberga, łącznik użyje właściwości *CorporateEmailAddress* elementu czatu. Jeśli łącznik nie znajdzie prawidłowego użytkownika Microsoft 365 w pliku mapowania niestandardowego lub właściwości *CorporateEmailAddress* elementu czatu, element nie zostanie zaimportowany.

9. Kliknij **przycisk Dalej**, przejrzyj ustawienia, a następnie kliknij przycisk **Zakończ,** aby utworzyć łącznik.

10. Przejdź do **strony Łączniki** danych, aby wyświetlić postęp procesu importowania nowego łącznika. Kliknij łącznik, aby wyświetlić stronę wysuwu zawierającą informacje o łączniku.
