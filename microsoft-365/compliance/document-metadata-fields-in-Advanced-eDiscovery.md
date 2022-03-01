---
title: Pola metadanych dokumentu w Advanced eDiscovery
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: W tym artykule zdefiniowano pola metadanych dla dokumentów w zestawie recenzji w przypadku Advanced eDiscovery w Microsoft 365.
ms.openlocfilehash: a1ce1cf43cb2b5d741731948288ab60f48cf5352
ms.sourcegitcommit: bb493f12701f6d6ee7d5e64b541adb87470bc7bc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/18/2022
ms.locfileid: "63014921"
---
# <a name="document-metadata-fields-in-advanced-ediscovery"></a>Pola metadanych dokumentu w Advanced eDiscovery

W poniższej tabeli wymieniono pola metadanych dla dokumentów w zestawie recenzji w przypadku Advanced eDiscovery. W tabeli przedstawiono następujące informacje:

- **Nazwa pola** i nazwa pola wyświetlanego **:** nazwa pola metadanych i nazwa pola wyświetlanego podczas wyświetlania metadanych pliku wybranego dokumentu w zestawie recenzji. Podczas wyświetlania metadanych dokumentu niektóre pola metadanych nie są uwzględniane. Te pola są wyróżnione gwiazdką (*).

- **Nazwa pola, które można wyszukiwać:** Nazwa właściwości, która może być wyszukiwana podczas uruchamiania zapytania [zestawu recenzji](review-set-search.md). Pusta komórka oznacza, że nie można wyszukać pola w zapytaniu zestawu recenzji.

- **Wyeksportowano nazwę pola:** Nazwa pola metadanych uwzględnionego podczas eksportowania dokumentów.  Pusta komórka oznacza, że pole nie jest uwzględnione w eksportowanych metadanych.

- **Opis:** Opis pola metadanych.

> [!NOTE]
> Pole **Słowa kluczowe** w [wyszukiwaniu zestawu recenzji](./review-set-search.md) używa języka Keyword Query Language (KQL). Pól wymienionych w kolumnie Nazwa  pola, które można przeszukiwać, można użyć w  polu Słowa kluczowe w zestawie recenzji wyszukiwania w celu tworzenia złożonych zapytań bez konieczności korzystania z konstruktora zapytań. Aby uzyskać więcej informacji na temat języka KQL, zobacz Informacje dotyczące składni języka kwerend [słów kluczowych](/sharepoint/dev/general-development/keyword-query-language-kql-syntax-reference).

<br>

****

|Nazwa pola i nazwa pola wyświetlanego|Nazwa pola z polem, które można wyszukiwać|Wyeksportowano nazwę pola|Opis|
|---|---|---|---|
|Identyfikator zawartości załącznika|AttachmentContentId||Identyfikator zawartości załącznika elementu.|
|Wynik uprawnień klienta obsługi klienta|AttorneyClientPrivilegeScore||Wynik zawartości modelu uprawnień klienta obsługi klienta.|
|Autor|Autor|Doc_authors|Autor z metadanych dokumentu.|
|UDW|UDW|Email_bcc|Pole UDW dla typów wiadomości. Format to **DisplayName \<SMTPAddress\>**.|
|CC|DW|Email_cc|Pole DW dla typów wiadomości. Format to **DisplayName \<SMTPAddress\>**.|
|Etykiety zgodności|Etykiety zgodności|Compliance_labels|[Etykiety przechowywania](retention.md) stosowane do zawartości w Office 365.|
|Ścieżka złożona|CompoundPath|Compound_path|Czytelna ścieżka dla człowieka, która opisuje źródło elementu.|
|Zawartość*|Content (Zawartość)||Wyodrębniony tekst elementu.|
|Treść konwersacji|KonwersacjaBody||Treść konwersacji elementu.|
|Identyfikator konwersacji|ConversationId|Conversation_ID|Identyfikator konwersacji z wiadomości. W Teams czatach grupowych i 1:1 wszystkie pliki transkrypcji oraz elementy ich rodziny w tej samej konwersacji mają ten sam identyfikator konwersacji. Aby uzyskać więcej informacji, [zobacz Advanced eDiscovery przepływu pracy dla zawartości w programie Microsoft Teams](teams-workflow-in-advanced-ediscovery.md).|
|Identyfikator rodziny konwersacji|ConversationFamilyID|ConversationFamilyID|Identyfikator identyfikujący poszczególne elementy konwersacji oraz powiązane z nią elementy.|
|Indeks konwersacji||Conversation_index|Indeks konwersacji z wiadomości.|
|Nazwa konwersacji||ConversationName|To pole zależy od typu zawartości.<br>**Teams czacie 1:1:** pierwsze 40 znaków pierwszej wiadomości.<br>**Teams czacie 1:N:** Nazwa czatu grupowego; jeśli nie jest dostępna, pierwsze 40 znaków pierwszej wiadomości.<br>**Teams w kanale:** Stanowisko lub podgłówek ogłoszenia; jeśli nie jest dostępny, pierwszych 40 znaków pierwszej wiadomości.|
|Konwersacja (czas w formacie PDF)|ConversationPdfTime||Data utworzenia konwersacji w wersji PDF.|
|Ponowne redaction konwersacji w czasie nagrywania|ConversationRedactionBurnTime||Data utworzenia wersji PDF konwersacji na czat.|
|Temat konwersacji|ConversationTopic||Temat konwersacji elementu.|
|Typ konwersacji|ConversationType|ConversationType|Typ konwersacji na czacie. Dopuszczalne wartości: <br>**Teams czatach 1:1 i grupowych oraz wszystkich Yammer konwersacjach:** Grupowe<br>**Teams kanały i kanały prywatne:** Kanał|
|Zawiera usuniętą wiadomość|ContainsDeletedMessage|ContainsDeletedMessage|Wskazuje, czy transkrypcja czatu zawiera usuniętą wiadomość|
|Zawiera edytowaną wiadomość|ContainsEditedMessage|ContainsEditedMessage|Wskazuje, czy transkrypcja czatu zawiera edytowaną wiadomość|
|Teams tytuł ogłoszenia|TeamsAnnouncementTitle|TeamsAnnouncementTitle|Tytuł z ogłoszenia [zespołu](https://support.microsoft.com/office/send-an-announcement-to-a-channel-8f244ea6-235a-4dcc-9143-9c5b801b4992).|
|||Converted_file_path|Ścieżka przekonwertowanego pliku eksportu. Tylko do użytku wewnętrznego firmy Microsoft.|
|Szybki|Szybki|Szybki|Nazwa elementu-pogotowa, z który był skojarzony element.|
|Data|Data|Data|Data to pole obliczeniowe zależne od typu pliku.<p>Wiadomość e-mail: Data wysłania<br>Załączniki wiadomości e-mail: Data ostatniej modyfikacji dokumentu; jeśli jest niedostępne, data wysłania rodzica<br>Dokumenty osadzone: data ostatniej modyfikacji dokumentu; Jeśli nie jest dostępna, data ostatniej modyfikacji elementu nadrzędnego<br>Dokumenty spo (zawiera nowoczesne załączniki): SharePoint Data ostatniej modyfikacji; jeśli nie jest dostępna, dokumenty z datą ostatniej modyfikacji<br>Dokumenty Office 365 inne niż: Data ostatniej modyfikacji<br>Spotkania: data rozpoczęcia spotkania<br>Poczta głosowa: Data wysłania<br>Wiadomości błyskawiczne: Data wysłania<br>Teams: Data wysłania|
|Komentarze dokumentu|DocComments|Doc_comments|Komentarze z metadanych dokumentu.|
|Firma dokumentów||Doc_company|Firma z metadanych dokumentu.|
|Data utworzenia dokumentu|CreatedTime|Doc_date_created|Utwórz datę na stronie metadane dokumentu.|
|DocIndex*|||Indeks w rodzinie. **-1** lub **0** oznacza, że jest katalogem głównym.|
|Słowa kluczowe dokumentu||Doc_keywords|Słowa kluczowe z metadanych dokumentu.|
|Dokument zmodyfikowany przez||Doc_modified_by|Użytkownik, który jako ostatni zmodyfikował dokument z metadanych dokumentu.|
|Poprawka dokumentu|Doc_Version|Doc_Version|Poprawka z metadanych dokumentu.|
|Temat dokumentu||Doc_subject|Temat z metadanych dokumentu.|
|Szablon dokumentu||Doc_template|Szablon z metadanych dokumentu.|
|DocLastSavedBy||Doc_last_saved_by|Nazwa użytkownika, który ostatnio zapisował dokument.|
|Motyw dominanty|DominantTheme|Dominant_theme|Motyw dominanty obliczony na podstawie analizy.|
|Zduplikowany podzbiór||Duplicate_subset|Identyfikator grupy, aby dokładnie zduplikować dane.|
|EmailAction*||Email_action|Dostępne wartości to **Brak**, **Odpowiedz** lub **Przekaż**. na podstawie wiersza tematu wiadomości.|
|Zażądano potwierdzenia dostarczenia wiadomości e-mail||Email_delivery_receipt|Adres e-mail podany w nagłówkach internetowych dla potwierdzenia dostarczenia.|
|Ważność|EmailImportance|Email_importance|Ważność wiadomości: **0** — niska; **1** — Normalny; **2** – Wysoka|
|Ignorowane błędy przetwarzania|ErrorIgnored|Error_Ignored|Błąd został zignorowany i nie rozwiązano problemów.|
|EmailInternetHeaders|EmailInternetHeaders|Email_internet_headers|Pełny zestaw nagłówków wiadomości e-mail z wiadomości e-mail|
|EmailLevel*||Email_level|Oznacza poziom wiadomości w obrębie wątku wiadomości e-mail, do którego należy; Załączniki dziedziczą wartość wiadomości nadrzędnej.|
|Identyfikator wiadomości e-mail||Email_message_ID|Identyfikator wiadomości internetowej z wiadomości.|
|EmailReadReceiptRequested||Email_read_receipt|Adres e-mail podany w nagłówkach internetowych dla potwierdzenia przeczytania.|
|Zabezpieczenia poczty e-mail|EmailSecurity|Email_security|Ustawienie zabezpieczeń wiadomości: **0** — Brak; **1** — Podpisane; **2** - Encrypted; **3** . Szyfrowane i podpisane.|
|Charakter wiadomości e-mail|EmailSensitivity|email_sensitivity|Ustawienie wrażliwości wiadomości: **0** - Brak; **1** Osobiste; **2** — Prywatne; **3** . FirmaConfidential.|
|Zestaw wiadomości e-mail|EmailSet|Email_set|Identyfikator grupy dla wszystkich wiadomości w tym samym zestawie wiadomości e-mail.|
|EmailThread*||Email_thread|Położenie wiadomości w zestawie wiadomości e-mail; składa się z identyfikatorów węzła od katalogu głównego do bieżącej wiadomości i są rozdzielone kropkami (.).|
|||Export_native_path|Ścieżka wyeksportowanego pliku.|
|Wyodrębniony typ zawartości||Native_type|Wyodrębniony typ zawartości w formie typu mime; na przykład image **/jpeg**|
|||Extracted_text_path|Ścieżka wyodrębninego pliku tekstowego w eksporcie.|
|ExtractedTextLength*||Extracted_text_length|Liczba znaków w wyodrębnionym tekście.|
|FamilyDuplicateSet*||Family_duplicate_set|Identyfikator liczbowy rodziny, które są ze sobą identyczne (ta sama zawartość i wszystkie te same załączniki).|
|Identyfikator rodziny|FamilyId|Family_ID|Grupuje razem załączniki i wyodrębnione elementy z wiadomości e-mail i czatów z jego elementem nadrzędnym. Obejmuje to czat lub pocztę e-mail oraz wszystkie załączniki i wyodrębnione elementy.|
|Rozmiar rodzinny||Family_size|Liczba dokumentów w rodzinie.|
|Klasa pliku|FileClass|File_class|W przypadku zawartości z SharePoint i OneDrive: **Dokument**. <br>W przypadku zawartości z Exchange: Wiadomość **e-mail** lub **załącznik**. <br>W przypadku zawartości z Teams lub Yammer: **Konwersacje**.|
|Identyfikator pliku|FileId|File_ID|Unikatowy identyfikator dokumentu w ramach sprawy.|
|Data utworzenia systemu plików||File_system_date_created|Data utworzenia w systemie plików (dotyczy tylko danych Office 365 danych).|
|Data modyfikacji systemu plików||File_system_date_modified|Data modyfikacji w systemie plików (dotyczy tylko danych Office 365 danych).|
|Typ pliku|FileType (Typ pliku)||Typ pliku elementu na podstawie rozszerzenia pliku.|
|Identyfikator grupy|GroupId|Group_ID|Grupuje razem wszystkie elementy na wiadomości e-mail i dokumenty. W przypadku wiadomości e-mail obejmuje to wiadomość oraz wszystkie załączniki i wyodrębnione elementy. W przypadku dokumentów obejmuje to dokument i wszystkie elementy osadzone.|
|Ma załącznik|EmailHasAttachment|Email_has_attachment|Wskazuje, czy wiadomość ma załączniki.|
|Ma  to jęz.|HasAttortory||**Ma** wartość True (Prawda), jeśli co najmniej jeden z uczestników znajduje się na liście pełnomocników; w przeciwnym razie ta wartość to **Fałsz**.|
|HasText*||Has_text|Wskazuje, czy element zawiera tekst. dopuszczalne wartości to **Prawda i** **Fałsz**.|
|Niezmienialny identyfikator||Immutable_ID|Ten identyfikator służy do unikatowego identyfikowania dokumentu w zestawie recenzji. Tego pola nie można używać podczas wyszukiwania w zestawie recenzji i identyfikatora nie można używać do uzyskiwania dostępu do dokumentu w jego natywnej lokalizacji.|
|Typ inkluzywny|InclusiveType|Inclusive_type|Typ inkluzywny obliczany dla analiz: **0** – nie inkluzywny; **1** — włącznie; **2** — minus włącznie; **3** — kopie włącznie.|
|W  id. odpowiedzi||In_reply_to_ID|W odpowiedzi na identyfikator wiadomości.|
|InputFileExtension (Extension)||Original_file_extension|Oryginalne rozszerzenie pliku.|
|InputFileID||Input_file_ID|Identyfikator pliku elementu najwyższego poziomu w zestawie recenzji. W przypadku załącznika ten identyfikator będzie identyfikatorem elementu nadrzędnego. Można go używać do grupowania rodzin.|
|Czy nowoczesny załącznik|IsModernAttachment||Ten plik to nowoczesny załącznik lub plik połączony.|
|Pochodzi z wersji dokumentu|IsFromDocumentVersion||Bieżący dokument pochodzi z innej wersji innego dokumentu.|
|Załącznik wiadomości e-mail|IsEmailAttachment||Ten element pochodzi z załącznika wiadomości e-mail, który jest wyświetlany jako element dołączony do wiadomości.|
|Znajduje się w tekście załącznika|IsInlineAttachment||Został on dołączony w tekście i pojawi się w treści wiadomości.|
|Jest przedstawicielem|IsRepresentative|Is_representative|Jeden dokument w każdym zestawie duplikatów jest oznaczony jako reprezentatywny.|
|Klasa elementu|ItemClass|Item_class|klasa elementu dostarczana przez serwer Exchange; na przykład **IPM. Uwaga**|
|Data ostatniej modyfikacji|LastModifiedDate|Doc_date_modified|Data ostatniej modyfikacji z metadanych dokumentu.|
|Identyfikator ładowania|LoadId|Load_ID|Identyfikator zestawu ładowania, w którym element został dodany do zestawu recenzji.|
|Lokalizacja|Lokalizacja|Lokalizacja|Ciąg wskazujący typ lokalizacji, z których pochodzą dokumenty.<p>**Zaimportowane dane** — dane Office 365 danych<br>**Teams** — Microsoft Teams<br>**Exchange** — Exchange pocztowe<br>**SharePoint** — SharePoint witryn<br>**OneDrive** — OneDrive konta|
|Nazwa lokalizacji|LocationName|Location_name|Ciąg identyfikujący źródło elementu. W przypadku wymiany będzie to adres SMTP skrzynki pocztowej. w SharePoint i OneDrive adres URL zbioru witryn.|
|||Marked_as_pivot|Ten plik to tabela przestawna w niemal zduplikowanych zestawach.|
|Oznaczone jako reprezentatywne|MarkAsRepresentative||Jeden dokument z każdego zestawu dokładnych duplikatów jest oznaczony jako przedstawicieli.|
|Data zakończenia spotkania|MeetingEndDate|Meeting_end_date|Data zakończenia spotkania.|
|Data rozpoczęcia spotkania|MeetingStartDate|Meeting_start_date|Data rozpoczęcia spotkania.|
|Typ wiadomości|MessageKind|Message_kind|Typ wiadomości do wyszukania. Możliwe wartości: kontakty **<p><br>docs <br><br><br><br><br><br><br>** wysyłają wiadomości e-mail do zewnętrznychdane faksów wiadomości błyskawicznych, dzienników spotkań usługi microsoftteams (zwraca elementy z czatów, spotkań i połączeń w aplikacji Microsoft Teams) **<br><br><br>— wpisy notatek rssfeeds <br><br>** wiadomości głosowych|
|Nowoczesny identyfikator nadrzędny załącznika||ModernAttachment_ParentId|Niezmienialny identyfikator elementu nadrzędnego dokumentu.|
|Rozszerzenie natywne|NativeExtension (Natywneextension)|Native_extension|Natywne rozszerzenie elementu.|
|Natywna nazwa pliku|NativeFileName|Native_file_name|Natywna nazwa pliku elementu.|
|NativeMD5||Native_MD5|Skrót MD5 (128-bitowa wartość skrótu) strumienia pliku.|
|NativeSHA256||Native_SHA_256|Skrót SHA256 (256-bitowa wartość skrótu) strumienia pliku.|
|Sortowanie ND/ET: Wykluczanie załączników|NdEtSortExclAttach|ND_ET_sort_excl_attach|Concatenation of the email thread (ET) set and Near-duplicate (ND) set. To pole służy do wydajnego sortowania podczas przeglądania. Kod **D** jest poprzedzony zestawami ND, a **E** jest poprzedzone zestawami ET.|
|Sortowanie ND/ET: W tym załączniki|NdEtSortInclAttach|ND_ET_sort_incl_attach|Concatenation of an email thread (ET) set and near-duplicate (ND) set. To pole służy do wydajnego sortowania podczas przeglądania. Kod **D** jest poprzedzony zestawami ND, a **E** jest poprzedzone zestawami ET. Po każdym elementze wiadomości e-mail w zestawie et następuje odpowiedni załącznik.|
|Near Duplicate Set||ND_set|Elementy podobne do dokumentu przestawnego współużytkują ten sam ND_set.|
|Autorzy o365||O365_authors|Tworzenie z SharePoint.|
|O365 utworzona przez||O365_created_by|Utworzone przez z SharePoint.|
|Data utworzenia o365||O365_date_created|Data utworzenia z SharePoint.|
|O365ModifiedDate||O365_date_modified|Data modyfikacji dokumentu (lub wersji dokumentu) SharePoint lub OneDrive dla Firm dokumentu. Jest to ta sama data modyfikacji co data wyświetlana w historii wersji w p SharePoint i OneDrive użytkownika.|
|O365 zmodyfikowana przez||O365_modified_by|Zmodyfikowane przez z SharePoint lub OneDrive.|
|Inne schłody|DedupedCustodians|Deduped_custodians|Lista elementów składowych dokumentów, które są dokładnymi duplikatami (w przypadku wiadomości e-mail na podstawie zawartości; dla dokumentów na podstawie skrótu).|
|Inne identyfikatory plików|DedupedFileIds|Deduped_file_IDs|Lista identyfikatorów plików dokumentów, które są dokładnymi duplikatami (w przypadku wiadomości e-mail na podstawie zawartości; w przypadku dokumentów na podstawie skrótu).|
|Inne ścieżki|Dedupedcompoundpath|Deduped_compound_path|Lista złożonych ścieżek dokumentów, które są dokładnie duplikatami (poczta e-mail: na podstawie zawartości, dokumenty: na podstawie skrótu).|
|Identyfikator nadrzędny|ParentId|Parent_ID|Identyfikator elementu nadrzędnego.|
|Nawias||Parent_node|Najbliższa wcześniejsza wiadomość e-mail w wątku wiadomości e-mail.|
|Domeny uczestników|ParticipantDomains|Email_participant_domains|Lista wszystkich domen uczestników wiadomości.|
|Uczestnicy|Uczestnicy|Email_participants|Lista wszystkich uczestników wiadomości; Na przykład Nadawca, Do, DW, UDW.|
|Identyfikator przestawny|PivotId|Pivot_ID|Identyfikator tabeli przestawnej.|
|Potencjalnie uprzywilejowany|PotencjalniePrivileged|Potentially_privileged|Ma wartość True (Prawda), jeśli model wykrywania uprawnień obsługi klienta uzna dokument za potencjalnie uprzywilejowany|
|Stan przetwarzania|ProcessingStatus|Error_code|Stan przetwarzania po dodaniu elementu do zestawu recenzji.|
|Odczyt percentylu|ReadPercentile||Odczytaj percentyl dokumentu na podstawie istotności.|
|Odebrano|Odebrano|Email_date_received|Data i godzina otrzymania wiadomości e-mail w czasie UTC.|
|Liczba adresatów||Recipient_count|Liczba adresatów w wiadomości.|
|Domeny adresatów|RecipientDomains (Domeny adresatów)|Email_recipient_domains|Lista wszystkich domen adresatów wiadomości.|
|Adresaci|Adresaci|Email_recipients|Lista wszystkich adresatów wiadomości (Do, DW, UDW).|
|||Redacted_file_path|Ścieżka pliku zastępczego w eksporcie( redacted replacement file).|
|||Redacted_text_path|Ścieżka wymiany redacted pliku tekstowego w eksporcie. Tylko do użytku wewnętrznego firmy Microsoft.|
|Problem 1 tagu istotności||Relevance_tag_case_issue_1|Istotność tagu Problem 1 ze istotnością.|
|Wskaźnik istotności|IstotnośćScore||Wskaźnik istotności dokumentu na podstawie istotności.|
|Tag istotności|Tag istotności||Wskaźnik istotności dokumentu na podstawie istotności.|
|Identyfikator przedstawiciela|RepresentativeId||Identyfikator numeryczny każdego zestawu dokładnych duplikatów.|
|||Row_number|Numer wiersza elementu w pliku ładowania.|
|Nadawca|Nadawca|Email_sender|Pole Nadawca (Od) dla typów wiadomości. Format to **DisplayName \<SmtpAddress>**.|
|Nadawca/Autor|SenderAuthor||Pole obliczeniowe złożone z nadawcy lub autora elementu.|
|Domena nadawcy|SenderDomain|Email_sender_domain|Domena nadawcy.|
|Wysłano|Wysłano|Email_date_sent|Data wysłania wiadomości.<br>Czaty: data rozpoczęcia od transkrypcji|
|Ustaw kolejność: Pierwsze włącznie|SetOrderInclusivesFirst|Set_order_inclusives_first|Pole sortowania — wiadomości e-mail i załączniki: counter-chronological; documents: pivot first then by descending similarity score.|
|Ustaw identyfikator||Set_ID|Dokumenty o podobnej zawartości (ND_set) lub wiadomości e-mail w tym samym wątku wiadomości e-mail (Email_set) mają ten sam Set_ID.|
|SimilarityPercent||Similarity_percent|Wskazuje, jak podobny dokument jest do tabeli przestawnej najbliższego zduplikowanego zestawu.|
|Natywny rozmiar pliku|Rozmiar|Native_size|Liczba bajtów elementu natywnego.|
|Temat|Temat|Email_subject|Temat wiadomości.|
|Temat/tytuł|SubjectTitle||Pole obliczeniowe złożone z tematu lub tytułu elementu.|
|Tagi|Tagi|Tagi|Znaczniki zastosowane w zestawie recenzji.|
|Nazwa kanału|Kanał|ChannelName|To jest nazwa Teams kanału. Dotyczy tylko Microsoft Teams zawartości.|
|Nazwa zespołu|TeamName|TeamName|**Teams:** Nazwa zespołu<br>**Yammer:** Community nazwy użytkownika|
|Lista motywów|ThemesList|Themes_list|Lista motywy obliczona na podstawie analizy.|
|Tytuł|Tytuł|Doc_title|Tytuł z metadanych dokumentu. Tytuł z metadanych dokumentu. W Teams zawartości Yammer konwersacji jest to wartość z właściwości ConversationName.|
|Do|Do|Email_to|Pole Do dla typów wiadomości. Format to **DisplayName (Nazwa wyświetlana)\<SmtpAddress>**|
|Unikatowe w zestawie wiadomości e-mail|UniqueInEmailSet||**Fałsz** , jeśli w zestawie wiadomości e-mail znajduje się duplikat załącznika.|
|Identyfikator grupy wersji||Version_Group_Id|Grupuje razem różne wersje tego samego dokumentu.|
|VersionNumber||Version_Number|Numer wersji dokumentu zebranego z programu SharePoint lub OneDrive dla Firm. Jest to ten sam numer wersji co numer wyświetlany w historii wersji w p SharePoint i OneDrive użytkownika.|
|Usunięto środki zaradcze|WasRemediated|Was_Remediated|**Ma wartość True** (Prawda), jeśli usunięto działania naprawcze, a w przeciwnym razie wartość **False (Fałsz**).|
|Liczba wyrazów|WordCount|Word_count|Liczba wyrazów w pozycji.|
|||||

> [!NOTE]
> Aby uzyskać więcej informacji na temat właściwości, które można przeszukiwać podczas Office 365 lokalizacji zawartości podczas zbierania danych dotyczących sprawy Advanced eDiscovery, zobacz Zapytania słów kluczowych i warunki wyszukiwania dotyczące wyszukiwania [zawartości](keyword-queries-and-search-conditions.md).
