---
title: Konfigurowanie łącznika do archiwizowania danych czatu ICE
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
description: Administratorzy mogą skonfigurować łącznik w celu importowania i archiwizowania danych z narzędzia CZAT ICE do Microsoft 365. Dzięki temu można archiwizować dane ze źródeł danych innych firm w programie Microsoft 365, aby zarządzać danymi innych firm przy użyciu funkcji zgodności, takich jak archiwizacja ze względu na przepisy prawne, wyszukiwanie zawartości i zasady przechowywania.
ms.openlocfilehash: c29a39c8c398a0d8721931cbcb770aa18d0f3c4b
ms.sourcegitcommit: a4729532278de62f80f2160825d446f6ecd36995
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/31/2022
ms.locfileid: "64568099"
---
# <a name="set-up-a-connector-to-archive-ice-chat-data"></a>Konfigurowanie łącznika do archiwizowania danych czatu ICE

Użyj natywnego łącznika w Centrum zgodności platformy Microsoft 365, aby zaimportować i zarchiwizować dane czatu usług finansowych z narzędzia do współpracy za pomocą czatu ICE. Po skonfigurowaniu i skonfigurowaniu łącznika połączy się on z witryną bezpiecznego portalu FTP (SFTP) w Twojej organizacji raz dziennie, konwertuje zawartość wiadomości czatu na format wiadomości e-mail, a następnie importuje te elementy do skrzynek pocztowych w programie Microsoft 365.

Po Microsoft 365 zapisaniu danych czatu ICE w skrzynkach pocztowych użytkowników możesz zastosować funkcje zgodności, takie jak archiwizacja w związku z postępowaniem sądowym, zbierania elektronicznych materiałów dowodowych, archiwizowanie, inspekcja, zgodność z komunikacją i zasady przechowywania Microsoft 365 do danych czatu ICE. Na przykład możesz przeszukiwać wiadomości w czacie ICE przy użyciu wyszukiwania zawartości lub skojarzyć skrzynkę pocztową zawierającą dane czatu ICE ze współpracownikiem w Advanced eDiscovery przypadku. Importowanie i archiwizowanie danych w programie Microsoft 365 za pomocą łącznika ice chat może ułatwić organizacji zachowania zgodności z zasadami rządowymi i przepisami regulacyjną.

## <a name="overview-of-archiving-ice-chat-data"></a>Omówienie archiwizowania danych czatu ICE

Poniższe omówienie przedstawia proces używania łącznika do archiwizowania danych czatu ICE w Microsoft 365.

![Przepływ pracy archiwizacji czatu ICE.](../media/ICEChatConnectorWorkflow.png)

1. Twoja organizacja współpracuje z czatem ICE, aby skonfigurować witrynę ICE Chat SFTP. Wraz z czatem ICE Chat skonfigurujesz czat ICE, aby kopiować wiadomości czatu do witryny ICE Chat SFTP.

2. Co 24 godziny wiadomości czatu z witryny ICE Chat są kopiowane do witryny ICE Chat SFTP.

3. Łącznik ICE Chat tworzyć w Centrum zgodności platformy Microsoft 365 łączy się z witryną ICE Chat SFTP codziennie i przenosi wiadomości czatu z poprzednich 24 godzin do bezpiecznej lokalizacji usługi Azure Storage w chmurze firmy Microsoft. Łącznik konwertuje także treść wiadomości czatu na format wiadomości e-mail.

4. Łącznik zaim importuje elementy wiadomości czatu do skrzynek pocztowych konkretnych użytkowników. W skrzynkach pocztowych użytkowników zostanie utworzony nowy folder o nazwie **ICE Chat** , a elementy wiadomości czatu zostaną zaimportowane do tego folderu. Łącznik działa przy użyciu wartości właściwości *SenderEmail i* *RecipientEmail* . Każda wiadomość czatu zawiera te właściwości, które są wypełnione adresem e-mail nadawcy i każdego adresata/uczestnika wiadomości czatu.

   Oprócz automatycznego mapowania użytkowników, które korzysta z wartości właściwości *SenderEmail* i *RecipientEmail* (co oznacza, że łącznik importuje wiadomość czatu do skrzynki pocztowej nadawcy i skrzynek pocztowych każdego adresata), możesz również zdefiniować niestandardowe mapowanie użytkowników, przesyłając plik mapowania plików CSV. Ten plik mapowania zawiera identyfikator *wiadomości błyskawicznych* w czacie ICE oraz Microsoft 365 adres skrzynki pocztowej dla każdego użytkownika w organizacji. Jeśli włączysz automatyczne mapowanie użytkowników i udostępnisz plik mapowania niestandardowego, dla każdego elementu czatu łącznik najpierw przyjrzy się plikowi mapowania niestandardowego. Jeśli nie znajdzie ona prawidłowego konta użytkownika programu Microsoft 365 odpowiadającego identyfikatorowi imId czatu ICE, łącznik użyje właściwości *SenderEmail* i *RecipientEmail* elementu czatu do zaimportowania elementu do skrzynek pocztowych uczestników czatu. Jeśli łącznik nie znajdzie prawidłowego użytkownika Microsoft 365 w pliku mapowania niestandardowego albo we właściwościach *SenderEmail* i *RecipientEmail*, element nie zostanie zaimportowany.

## <a name="before-you-set-up-a-connector"></a>Przed skonfigurowaniem łącznika

Niektóre kroki implementacji wymagane do archiwizowania danych czatu ICE są zewnętrzne Microsoft 365 i muszą zostać ukończone, zanim będzie można utworzyć łącznik w centrum zgodności.

- Ice Chat nalicza dla klientów opłatę za zgodność zewnętrzną. Twoja organizacja powinna skontaktować się z grupą sprzedaży Ice Chat w celu omówienia i podpisania umowy dotyczącej usług danych ICE Chat, którą można uzyskać na stronie [https://www.theice.com/publicdocs/agreements/ICE\_Data\_Services\_Agreement.pdf](https://www.theice.com/publicdocs/agreements/ICE\_Data\_Services\_Agreement.pdf). Niniejsza umowa jest zawarta między czatem ICE a Twoją organizacją i nie obejmuje firmy Microsoft. Po skonfigurowaniu witryny SFTP czatu ICE w kroku 2 czat ICE podaje poświadczenia FTP bezpośrednio dla Twojej organizacji. Następnie należy podać te poświadczenia firmie Microsoft podczas konfigurowania łącznika w kroku 3.

- Przed utworzeniem łącznika w kroku 3 należy skonfigurować witrynę ICE Chat SFTP. Po zakończeniu pracy w czacie ICE w celu skonfigurowania witryny SFTP dane z portalu ICE Chat są codziennie przekazywane do witryny SFTP. Łącznik, który tworzysz w kroku 3, łączy się z tą witryną SFTP i przesyła dane czatu do Microsoft 365 pocztowych. SfTP szyfruje również dane czatu ICE, które są wysyłane do skrzynek pocztowych w trakcie procesu przenoszenia.

- Aby skonfigurować łącznik ice chat, musisz używać klawiszy i kluczowych zwrotów dla plików PGP (Pretty Good Privacy) i Secure Shell (SSH). Te klucze służą do konfigurowania witryny ICE Chat SFTP i są używane przez łącznik do łączenia się z witryną ICE Chat SFTP w celu importowania danych do Microsoft 365. Klawisz PGP służy do konfigurowania szyfrowania danych przesyłanych z witryny ICE Chat SFTP do Microsoft 365. Klawisz SSH służy do konfigurowania bezpiecznej powłoki w celu umożliwienia bezpiecznego logowania zdalnego, gdy łącznik łączy się z witryną ICE Chat SFTP.

  Podczas konfigurowania łącznika możesz używać kluczy publicznych i kluczowych zwrotów dostarczanych przez firmę Microsoft lub możesz używać własnych kluczy prywatnych i zwrotów. Zalecamy używanie kluczy publicznych dostarczonych przez firmę Microsoft. Jeśli jednak organizacja skonfigurowała już witrynę ICE Chat SFTP przy użyciu kluczy prywatnych, możesz utworzyć łącznik, używając tych samych kluczy prywatnych.

- Łącznik ICE Chat może importować łącznie 200 000 elementów w jednym dniu. Jeśli w witrynie SFTP istnieje więcej niż 200 000 elementów, żadne z tych elementów nie zostaną zaimportowane do Microsoft 365.

- Administrator, który tworzy łącznik ice chat w kroku 3 (oraz kto pobiera klucze publiczne i adres IP w kroku 1), musi mieć przypisaną rolę Administratora łącznika danych. Ta rola jest wymagana do dodawania łączników na **stronie Łączniki** danych w Centrum zgodności platformy Microsoft 365. Ta rola jest domyślnie dodawana do wielu grup ról. Aby uzyskać listę tych grup ról, zobacz sekcję "Role w centrach zabezpieczeń i zgodności" w sekcji Uprawnienia w Centrum zabezpieczeń & [zgodności](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Administrator w organizacji może również utworzyć niestandardową grupę ról, przypisać rolę administrator łącznika danych, a następnie dodać odpowiednich użytkowników jako członków. Aby uzyskać instrukcje, zobacz sekcję "Tworzenie niestandardowej grupy ról" w sekcji Uprawnienia [w Centrum zgodności platformy Microsoft 365](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

## <a name="set-up-a-connector-using-public-keys"></a>Konfigurowanie łącznika przy użyciu kluczy publicznych

W krokach w tej sekcji popisano, jak skonfigurować łącznik ICE Chat przy użyciu kluczy publicznych dla plików PGP (Pretty Good Privacy) i Secure Shell (SSH).

### <a name="step-1-obtain-pgp-and-ssh-public-keys"></a>Krok 1. Uzyskiwanie kluczy publicznych PGP i SSH

Pierwszym krokiem jest uzyskanie kopii kluczy publicznych dla plików PGP (Pretty Good Privacy) i Secure Shell (SSH). Użyj tych klawiszy w kroku 2, aby skonfigurować witrynę ICE Chat SFTP w celu umożliwienia łącznikowi (który został przez Ciebie utworzyć w kroku 3) łączenia się z witryną SFTP i przenoszenia danych czatu ICE do Microsoft 365 pocztowych. Uzyskasz również adres IP w tym kroku, którego używasz podczas konfigurowania witryny ICE Chat SFTP.

1. Przejdź do łączników [https://compliance.microsoft.com](https://compliance.microsoft.com) **danych w lewym okienku narracji i** kliknij je.

2. Na stronie **Łączniki danych** w obszarze **CZAT ICE** kliknij pozycję **Widok**.

3. Na stronie **Czat z LODEM** kliknij pozycję **Dodaj łącznik**.

4. Na stronie **Warunki użytkowania usługi** kliknij pozycję **Zaakceptuj**.

5. Na stronie **Dodaj poświadczenia dla źródła** zawartości kliknij pozycję Chcę używać kluczy publicznych **PGP i SSH dostarczonych przez firmę Microsoft**.

   ![Wybierz opcję, aby użyć kluczy publicznych.](../media/ICEChatPublicKeysOption.png)

6. W obszarze krok 1 kliknij linki Pobierz **klucz SSH**, Pobierz klucz **PGP** i Pobierz adres **IP** , aby zapisać kopię każdego pliku na komputerze lokalnym.

   ![Linki do pobierania kluczy publicznych i adresu IP.](../media/ICEChatPublicKeyDownloadLinks.png)

   Te pliki zawierają następujące elementy, które są używane do konfigurowania witryny ICE Chat SFTP w kroku 2:

   - Klucz publiczny PGP: Ten klucz służy do konfigurowania szyfrowania danych przesyłanych z witryny ICE Chat SFTP w celu Microsoft 365.

   - Klucz publiczny SSH: Ten klucz służy do konfigurowania bezpiecznego protokołu SSH w celu umożliwienia bezpiecznego logowania zdalnego, gdy łącznik łączy się z witryną ICE Chat SFTP.

   - Adres IP: Witryna ICE Chat SFTP jest skonfigurowana do akceptowania żądania połączenia tylko z tego adresu IP, który jest używany przez łącznik ICE Chat, który został utworzyć w kroku 3.

7. Kliknij **przycisk Anuluj** , aby zamknąć kreatora. Powrócisz do tego kreatora w kroku 3, aby utworzyć łącznik.

### <a name="step-2-configure-the-ice-chat-sftp-site"></a>Krok 2. Konfigurowanie witryny ICE Chat SFTP

Następnym krokiem jest użycie kluczy publicznych PGP i SSH oraz adresu IP uzyskanego w kroku 1 w celu skonfigurowania szyfrowania PGP i uwierzytelniania SSH dla witryny ICE Chat SFTP. Dzięki temu łącznik ice chatu, który utworzysz w kroku 3, połączy się z witryną ICE Chat SFTP i przenieś dane czatu ICE Microsoft 365. Musisz współpracować z działem obsługi klienta ICE Chat, aby skonfigurować witrynę ICE Chat SFTP.

### <a name="step-3-create-an-ice-chat-connector"></a>Krok 3. Tworzenie łącznika ice chat

Ostatnim krokiem jest utworzenie łącznika ICE Chat w Centrum zgodności platformy Microsoft 365. Łącznik korzysta z informacji, które pozyskasz, aby połączyć się z witryną ICE Chat SFTP i przenieść wiadomości czatu do odpowiednich skrzynek pocztowych użytkowników w Microsoft 365.

1. Przejdź do łączników [https://compliance.microsoft.com](https://compliance.microsoft.com) **danych w lewym okienku narracji i** kliknij je.

2. Na stronie **Łączniki danych** w obszarze **CZAT ICE** kliknij pozycję **Widok**.

3. Na stronie **Czat z LODEM** kliknij pozycję **Dodaj łącznik**.

4. Na stronie **Warunki użytkowania usługi** kliknij pozycję **Zaakceptuj**.

5. Na stronie **Dodawanie poświadczeń dla źródła zawartości** kliknij pozycję Chcę używać kluczy publicznych **PGP i SSH**.

6. W obszarze Krok 3 wprowadź wymagane informacje w następujących polach, a następnie kliknij pozycję **Sprawdź poprawność połączenia**.

   - **Kod firmy:** Identyfikator organizacji, który jest używany jako nazwa użytkownika witryny ICE Chat SFTP.

   - **Hasło:** Hasło do witryny ICE Chat SFTP.

   - **SFTP URL:** Adres URL witryny ICE Chat SFTP (na przykład `sftp.theice.com`). W tej wartości możesz również użyć adresu IP.

   - **Port SFTP:** Numer portu witryny ICE Chat SFTP. Łącznik używa tego portu do łączenia się z witryną SFTP.

7. Po pomyślnym weryfikacji połączenia kliknij przycisk **Dalej**.

8. Na stronie **Definiowanie** użytkownika określ użytkowników, dla których mają być importowane dane.

     - **Wszyscy użytkownicy w Organizacji**. Zaznacz tę opcję, aby zaimportować dane wszystkich użytkowników.

     - **Tylko użytkownicy, którzy mają zawieszenie w postępowaniem sądowym**. Zaznacz tę opcję, aby importować dane tylko tych użytkowników, których skrzynki pocztowe są umieszczone w związku z postępowaniem sądowym. Ta opcja powoduje importowanie danych do skrzynek pocztowych użytkowników, dla których właściwość LitigationHoldEnabled ma wartość True. Aby uzyskać więcej informacji, zobacz [Tworzenie postępowania w związku z postępowaniem sądowym](create-a-litigation-hold.md).

9. Na stronie **Mapowanie użytkowników zewnętrznych Microsoft 365 użytkowników** włącz automatyczne mapowanie użytkowników i zapewnij niestandardowe mapowanie użytkowników zgodnie z wymaganiami. Na tej stronie możesz pobrać kopię pliku CSV mapowania użytkowników. Możesz dodać mapowania użytkowników do pliku, a następnie przekazać go.

   > [!NOTE]
   > Jak wyjaśniono wcześniej, plik CSV niestandardowego mapowania zawiera identyfikator ICE Chat i Microsoft 365 adres skrzynki pocztowej dla każdego użytkownika. Jeśli włączysz automatyczne mapowanie użytkowników i udostępnisz mapowanie niestandardowe dla każdego elementu czatu, łącznik najpierw przyjrzy się plikowi mapowania niestandardowego. Jeśli użytkownik nie znajdzie prawidłowego użytkownika programu Microsoft 365 odpowiadającego identyfikatorowi imid czatu ICE, łącznik zaimportuje element do skrzynek pocztowych użytkowników określonych we właściwościach *SenderEmail* i *RecipientEmail* elementu czatu. Jeśli łącznik nie znajdzie prawidłowego użytkownika Microsoft 365 za pomocą automatycznego lub niestandardowego mapowania użytkowników, element nie zostanie zaimportowany.

10. Kliknij **przycisk Dalej**, przejrzyj ustawienia, a następnie kliknij przycisk **Zakończ,** aby utworzyć łącznik.

11. Przejdź do **strony Łączniki** danych, aby wyświetlić postęp procesu importowania nowego łącznika.

## <a name="set-up-a-connector-using-private-keys"></a>Konfigurowanie łącznika przy użyciu kluczy prywatnych

W krokach w tej sekcji popisano, jak skonfigurować łącznik ICE Chat przy użyciu kluczy prywatnych PGP i SSH. Ta opcja konfiguracji łącznika jest przeznaczona dla organizacji, które już skonfigurowały witrynę ICE Chat SFTP przy użyciu kluczy prywatnych.

### <a name="step-1-obtain-an-ip-address-to-configure-the-ice-chat-sftp-site"></a>Krok 1. Uzyskiwanie adresu IP w celu skonfigurowania witryny ICE Chat SFTP

Jeśli Twoja organizacja użyła kluczy prywatnych PGP i SSH do skonfigurowania witryny ICE Chat SFTP, musisz uzyskać adres IP i przekazać go działowi obsługi klienta ICE Chat. Witryna ICE Chat SFTP musi być skonfigurowana do akceptowania żądań połączeń z tego adresu IP. Ten sam adres IP jest używany przez łącznik ICE Chat do łączenia się z witryną SFTP i przesyłania danych czatu ICE Microsoft 365.

Aby uzyskać adres IP:

1. Przejdź do łączników <https://compliance.microsoft.com> **danych w lewym okienku narracji i** kliknij je.

2. Na stronie **Łączniki danych** w obszarze **CZAT ICE** kliknij pozycję **Widok**.

3. Na stronie **opisów produktu w** czacie ICE kliknij **pozycję Dodaj łącznik**

4. Na stronie **Warunki użytkowania usługi** kliknij pozycję **Zaakceptuj**.

5. Na stronie **Dodaj poświadczenia dla źródła zawartości** kliknij pozycję **Chcę używać kluczy prywatnych PGP i SSH**.

   ![Wybierz opcję, aby użyć kluczy prywatnych.](../media/ICEChatPrivateKeysOption.png)

6. W obszarze krok 1 kliknij pozycję **Pobierz adres IP** , aby zapisać kopię pliku adresu IP na komputerze lokalnym.

   ![Pobierz adres IP.](../media/ICEChatConnectorIPAddress.png)

7. Kliknij **przycisk Anuluj** , aby zamknąć kreatora. Powrócisz do tego kreatora w kroku 2, aby utworzyć łącznik.

Musisz współpracować z działem obsługi klienta ICE Chat, aby skonfigurować witrynę ICE Chat SFTP w celu akceptowania żądań połączeń z tego adresu IP.

### <a name="step-2-create-an-ice-chat-connector"></a>Krok 2. Tworzenie łącznika ice chat

Po skonfigurowaniu witryny SFTP czatu ICE Chat następnym krokiem jest utworzenie łącznika ICE Chat w Centrum zgodności platformy Microsoft 365. Łącznik używa podanych przez Ciebie informacji do łączenia się z witryną ICE Chat SFTP i przesyłania wiadomości e-mail do odpowiadających im skrzynek pocztowych użytkowników w Microsoft 365. Aby wykonać ten krok, upewnij się, że masz kopie tych samych kluczy prywatnych i kluczowych zwrotów, które zostały użyte do skonfigurowania witryny ICE Chat SFTP.

1. Przejdź do łączników <https://compliance.microsoft.com> **danych w lewym okienku narracji i** kliknij je.

2. Na stronie **Łączniki danych** w obszarze **CZAT ICE** kliknij pozycję **Widok**.

3. Na stronie **opisów produktu w** czacie ICE kliknij **pozycję Dodaj łącznik**

4. Na stronie **Warunki użytkowania usługi** kliknij pozycję **Zaakceptuj**.

5. Na stronie **Dodaj poświadczenia dla źródła zawartości** kliknij pozycję **Chcę używać kluczy prywatnych PGP i SSH**.

6. W obszarze Krok 3 wprowadź wymagane informacje w następujących polach, a następnie kliknij pozycję **Sprawdź poprawność połączenia**.

      - **Nazwa:** Nazwa łącznika. Musi być unikatowy w Twojej organizacji.

      - **Kod firmy:** Identyfikator organizacji używany jako nazwa użytkownika witryny ICE Chat SFTP.

      - **Hasło:** Hasło do witryny SFTP czatów ICE w Twojej organizacji.

      - **SFTP URL:** Adres URL witryny ICE Chat SFTP (na przykład `sftp.theice.com`). W tej wartości możesz również użyć adresu IP.

      - **Port SFTP:** Numer portu witryny ICE Chat SFTP. Łącznik używa tego portu do łączenia się z witryną SFTP.

      - **Klucz prywatny PGP:** Klucz prywatny PGP dla witryny ICE Chat SFTP. Pamiętaj o uwzględnieniu całej wartości klucza prywatnego, łącznie z pierwszym i końcową łącznie z blokiem klucza.

      - **Hasło klucza PGP:** Kod dostępu do klucza prywatnego PGP.

      - **Klucz prywatny SSH:** Klucz prywatny SSH dla witryny ICE Chat SFTP. Pamiętaj o uwzględnieniu całej wartości klucza prywatnego, łącznie z pierwszym i końcową łącznie z blokiem klucza.

      - **Kluczowy zwrot SSH:** Kod dostępu do klucza prywatnego SSH.

7. Po pomyślnym weryfikacji połączenia kliknij przycisk **Dalej**.

8. Na stronie **Definiowanie** użytkownika określ użytkowników, dla których mają być importowane dane.

     - **Wszyscy użytkownicy w Organizacji**. Zaznacz tę opcję, aby zaimportować dane wszystkich użytkowników.

     - **Tylko użytkownicy, którzy mają zawieszenie w postępowaniem sądowym**. Zaznacz tę opcję, aby importować dane tylko tych użytkowników, których skrzynki pocztowe są umieszczone w związku z postępowaniem sądowym. Ta opcja powoduje importowanie danych do skrzynek pocztowych użytkowników, dla których właściwość LitigationHoldEnabled ma wartość True. Aby uzyskać więcej informacji, zobacz [Tworzenie postępowania w związku z postępowaniem sądowym](create-a-litigation-hold.md).

9. Na stronie **Mapowanie użytkowników czatu ICE do Microsoft 365 użytkowników** włącz automatyczne mapowanie użytkowników i w razie potrzeby udostępnij niestandardowe mapowanie użytkowników.

   > [!NOTE]
   > Jak wyjaśniono wcześniej, plik CSV niestandardowego mapowania zawiera identyfikator ICE Chat i Microsoft 365 adres skrzynki pocztowej dla każdego użytkownika. Jeśli włączysz automatyczne mapowanie użytkowników i udostępnisz mapowanie niestandardowe dla każdego elementu czatu, łącznik najpierw przyjrzy się plikowi mapowania niestandardowego. Jeśli użytkownik nie znajdzie prawidłowego użytkownika programu Microsoft 365 odpowiadającego identyfikatorowi imid czatu ICE, łącznik zaimportuje element do skrzynek pocztowych użytkowników określonych we właściwościach *SenderEmail* i *RecipientEmail* elementu czatu. Jeśli łącznik nie znajdzie prawidłowego użytkownika Microsoft 365 za pomocą automatycznego lub niestandardowego mapowania użytkowników, element nie zostanie zaimportowany.

10. Kliknij **przycisk Dalej**, przejrzyj ustawienia, a następnie kliknij przycisk **Zakończ,** aby utworzyć łącznik.

11. Przejdź do **strony Łączniki** danych, aby wyświetlić postęp procesu importowania nowego łącznika. Kliknij łącznik, aby wyświetlić stronę wysuwu zawierającą informacje o łączniku.
