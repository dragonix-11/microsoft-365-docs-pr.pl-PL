---
title: Pola metadanych dokumentu w środowisku zbierania elektronicznych materiałów dowodowych (Premium)
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
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
description: W tym artykule zdefiniowano pola metadanych dla dokumentów w zestawie przeglądów w przypadku Zbieranie elektronicznych materiałów dowodowych w Microsoft Purview (Premium) na platformie Microsoft 365.
ms.openlocfilehash: a6fc8479d3ecd2b89c0331220fb7f88f46bda1e4
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66629756"
---
# <a name="document-metadata-fields-in-ediscovery-premium"></a>Pola metadanych dokumentu w środowisku zbierania elektronicznych materiałów dowodowych (Premium)

W poniższej tabeli wymieniono pola metadanych dla dokumentów w zestawie przeglądów w przypadku Zbieranie elektronicznych materiałów dowodowych w Microsoft Purview (Premium). Tabela zawiera następujące informacje:

- **Nazwa pola** i **nazwa pola wyświetlanego:** nazwa pola metadanych i nazwa pola wyświetlanego podczas wyświetlania metadanych pliku wybranego dokumentu w zestawie przeglądów. Niektóre pola metadanych nie są uwzględniane podczas wyświetlania metadanych pliku dokumentu. Te pola są wyróżnione gwiazdką (*).

- **Nazwa pola z możliwością wyszukiwania:** Nazwa właściwości, którą można wyszukać podczas uruchamiania [zapytania zestawu przeglądów](review-set-search.md). Pusta komórka oznacza, że nie można wyszukać pola w zapytaniu zestawu przeglądów.

- **Wyeksportowana nazwa pola:** Nazwa pola metadanych, które jest uwzględniane podczas eksportowania dokumentów.  Pusta komórka oznacza, że pole nie jest dołączone do wyeksportowanych metadanych.

- **Opis:** Opis pola metadanych.

> [!NOTE]
> Pole **Słowa kluczowe** w [wyszukiwaniu zestawu przeglądów](./review-set-search.md) używa języka zapytań słów kluczowych (KQL). Pól wymienionych w kolumnie **Nazwa pola z możliwością wyszukiwania** można użyć w polu Słowa kluczowe w wyszukiwaniu zestawu przeglądów w celu utworzenia złożonych zapytań bez konieczności używania **konstruktora** zapytań. Aby uzyskać więcej informacji na temat języka KQL, zobacz [Dokumentacja składni języka zapytań słów kluczowych](/sharepoint/dev/general-development/keyword-query-language-kql-syntax-reference).

<br>

****

|Nazwa pola i nazwa pola wyświetlanego|Nazwa pola z możliwością wyszukiwania|Wyeksportowana nazwa pola|Opis|
|---|---|---|---|
|Identyfikator zawartości załącznika|AttachmentContentId||Identyfikator zawartości załącznika elementu.|
|Ocena uprawnień klienta adwokackiego|AttorneyClientPrivilegeScore||Ocena zawartości modelu uprawnień klienta-adwokata.|
|Autor|Autor|Doc_authors|Tworzenie z metadanych dokumentu.|
|UDW|Udw|Email_bcc|Pole Bcc dla typów komunikatów. Format to **DisplayName \<SMTPAddress\>**.|
|CC|Cc|Email_cc|Pole DW dla typów komunikatów. Format to **DisplayName \<SMTPAddress\>**.|
|Etykiety zgodności|ComplianceLabels|Compliance_labels|[Etykiety przechowywania](retention.md) stosowane do zawartości w Office 365.|
|Ścieżka złożona|CompoundPath|Compound_path|Ścieżka czytelna dla człowieka opisująca źródło elementu.|
|Zawartość*|Content (Zawartość)||Wyodrębniono tekst elementu.|
|Treść konwersacji|KonwersacjaBody||Treść konwersacji elementu.|
|Identyfikator konwersacji|ConversationId|Conversation_ID|Identyfikator konwersacji z wiadomości. W przypadku aplikacji Teams 1:1 i czatów grupowych wszystkie pliki transkrypcji i ich elementy rodzinne w ramach tej samej konwersacji mają ten sam identyfikator konwersacji. Aby uzyskać więcej informacji, zobacz [przepływ pracy zbierania elektronicznych materiałów dowodowych (Premium) dla zawartości w usłudze Microsoft Teams](teams-workflow-in-advanced-ediscovery.md).|
|Identyfikator rodziny konwersacji|ConversationFamilyID|ConversationFamilyID|Identyfikator identyfikujący poszczególne elementy konwersacji, a także powiązane elementy w konwersacji.|
|Indeks konwersacji||Conversation_index|Indeks konwersacji z wiadomości.|
|Nazwa konwersacji||ConversationName|To pole zależy od typu zawartości.<br>**Czat w aplikacji Teams 1:1:** pierwsze 40 znaków pierwszej wiadomości.<br>**Czat teams 1:N:** Nazwa czatu grupowego; Jeśli nie jest dostępna, pierwsze 40 znaków pierwszego komunikatu.<br>**Post kanału usługi Teams:** Opublikuj tytuł lub podnagłówek anonsu; Jeśli nie jest dostępna, pierwsze 40 znaków pierwszego komunikatu.|
|Czas pliku PDF konwersacji|ConversationPdfTime||Data utworzenia wersji konwersacji w formacie PDF.|
|Czas nagrywania ponownej akcji konwersacji|ConversationRedactionBurnTime||Data utworzenia wersji konwersacji w formacie PDF dla czatu.|
|Temat konwersacji|KonwersacjaTopic||Temat konwersacji elementu.|
|Typ konwersacji|Typ konwersacji|Typ konwersacji|Typ konwersacji na czacie. Wartości to: <br>**Teams 1:1 i czaty grupowe oraz wszystkie konwersacje usługi Yammer:** Grupa<br>**Kanały i kanały prywatne usługi Teams:** Kanał|
|Zawiera usuniętą wiadomość|ContainsDeletedMessage|ContainsDeletedMessage|Wskazuje, czy transkrypcja czatu zawiera usuniętą wiadomość|
|Zawiera edytowany komunikat|ContainsEditedMessage|ContainsEditedMessage|Wskazuje, czy transkrypcja czatu zawiera edytowaną wiadomość|
|Tytuł anonsu usługi Teams|TeamsAnnouncementTitle|TeamsAnnouncementTitle|Tytuł z [ogłoszenia zespołu](https://support.microsoft.com/office/send-an-announcement-to-a-channel-8f244ea6-235a-4dcc-9143-9c5b801b4992).|
|||Converted_file_path|Ścieżka przekonwertowanego pliku eksportu. Tylko do użytku wewnętrznego firmy Microsoft.|
|Opiekun|Opiekun|Opiekun|Nazwa opiekuna, z którego element został skojarzony.|
|Data|Data|Data|Data jest polem obliczanym, które zależy od typu pliku.<p>**Wiadomość e-mail**: data wysłania<br>**Załączniki wiadomości e-mail**: data ostatniej modyfikacji dokumentu; jeśli nie jest dostępna, data wysłania elementu nadrzędnego<br>**Dokumenty osadzone**: data ostatniej modyfikacji dokumentu; jeśli nie jest dostępna, data ostatniej modyfikacji elementu nadrzędnego<br>**Dokumenty SPO (w tym nowoczesne załączniki)**: data ostatniej modyfikacji dokumentu; jeśli nie jest dostępna, data ostatniej modyfikacji programu SharePoint<br>**Dokumenty inne niż Office 365: data ostatniej** modyfikacji<br>**Spotkania**: data rozpoczęcia spotkania<br>**Poczta głosowa**: data wysłania<br>**Wiadomości błyskawiczne**: data wysłania<br>**Teams**: Data wysłania|
|Komentarze do dokumentu|DocComments|Doc_comments|Komentarze z metadanych dokumentu.|
|Firma zajmująca się dokumentami||Doc_company|Firma z metadanych dokumentu.|
|Data utworzenia dokumentu|CreatedTime|Doc_date_created|Utwórz datę na podstawie metadanych dokumentu.|
|DocIndex*|||Indeks w rodzinie. **-1** lub **0** oznacza, że jest to katalog główny.|
|Słowa kluczowe dokumentu||Doc_keywords|Słowa kluczowe z metadanych dokumentu.|
|Dokument zmodyfikowany przez||Doc_modified_by|Użytkownik, który ostatnio zmodyfikował dokument z metadanych dokumentu.|
|Poprawka dokumentu|Doc_Version|Doc_Version|Poprawka z metadanych dokumentu.|
|Temat dokumentu||Doc_subject|Temat z metadanych dokumentu.|
|Szablon dokumentu||Doc_template|Szablon z metadanych dokumentu.|
|DocLastSavedBy||Doc_last_saved_by|Nazwa użytkownika, który ostatnio zapisał dokument.|
|Motyw dominujący|DominantTheme|Dominant_theme|Motyw dominujący obliczony na potrzeby analizy.|
|Zduplikowany podzestaw||Duplicate_subset|Identyfikator grupy dla dokładnych duplikatów.|
|EmailAction*||Email_action|Wartości to **Brak**, **Odpowiedź** lub **Dalej**; na podstawie wiersza tematu komunikatu.|
|Zażądano potwierdzenia dostarczenia wiadomości e-mail||Email_delivery_receipt|Adres e-mail podany w nagłówkach internetowych na potrzeby potwierdzenia dostawy.|
|Znaczenie|EmailImportance|Email_importance|Ważność komunikatu: **0** — niska; **1** — normalny; **2** — wysoki|
|Ignorowane błędy przetwarzania|ErrorIgnored|Error_Ignored|Błąd został zignorowany i nie został skorygowany.|
|EmailInternetHeaders|EmailInternetHeaders|Email_internet_headers|Pełny zestaw nagłówków wiadomości e-mail z wiadomości e-mail|
|EmailLevel*||Email_level|Wskazuje poziom wiadomości w wątku wiadomości e-mail, do którego należy; załączniki dziedziczą wartość komunikatu nadrzędnego.|
|Identyfikator wiadomości e-mail||Email_message_ID|Identyfikator wiadomości internetowej z wiadomości.|
|EmailReadReceiptRequested||Email_read_receipt|Adres e-mail podany w nagłówkach internetowych na potrzeby potwierdzenia odczytu.|
|Zabezpieczenia poczty e-mail|EmailSecurity|Email_security|Ustawienie zabezpieczeń komunikatu: **0** — brak; **1** — podpisane; **2** — Szyfrowane; **3** — Zaszyfrowane i podpisane.|
|Ważność poczty e-mail|EmailSensitivity|email_sensitivity|Ustawienie poufności komunikatu: **0** — brak; **1** Osobiste; **2** — prywatny; **3** — CompanyConfidential.|
|Zestaw poczty e-mail|Zestaw poczty e-mail|Email_set|Identyfikator grupy dla wszystkich wiadomości w tym samym zestawie poczty e-mail.|
|EmailThread*||Email_thread|Położenie wiadomości w zestawie poczty e-mail; składa się z identyfikatorów węzłów z katalogu głównego do bieżącego komunikatu i są oddzielone kropkami (.).|
|||Export_native_path|Ścieżka wyeksportowanego pliku.|
|Wyodrębniony typ zawartości||Native_type|Wyodrębniony typ zawartości w postaci typu mime; na przykład **obraz/jpeg**|
|||Extracted_text_path|Ścieżka do wyodrębniony plik tekstowy w eksporcie.|
|ExtractedTextLength*||Extracted_text_length|Liczba znaków w wyodrębnionym tekście.|
|FamilyDuplicateSet*||Family_duplicate_set|Identyfikator liczbowy dla rodzin, które są dokładnymi duplikatami siebie nawzajem (ta sama zawartość i wszystkie te same załączniki).|
|Identyfikator rodziny|Identyfikator rodziny|Family_ID|Grupuje załączniki i wyodrębnione elementy z poczty e-mail i czatów z elementem nadrzędnym. Obejmuje to czat lub wiadomość e-mail oraz wszystkie załączniki i wyodrębnione elementy.|
|Rozmiar rodziny||Family_size|Liczba dokumentów w rodzinie.|
|Klasa plików|FileClass|File_class|W przypadku zawartości z programu SharePoint i usługi OneDrive: **dokument**. <br>W przypadku zawartości z programu Exchange: **adres e-mail** lub **załącznik**. <br>Zawartość aplikacji Teams lub Yammer: **Konwersacje**.|
|Identyfikator pliku|Identyfikator pliku|File_id|Identyfikator dokumentu jest unikatowy w przypadku.|
|Data utworzenia systemu plików||File_system_date_created|Data utworzenia z systemu plików (dotyczy tylko danych innych niż Office 365).|
|Data modyfikacji systemu plików||File_system_date_modified|Data modyfikacji z systemu plików (dotyczy tylko danych innych niż Office 365).|
|Typ pliku|Filetype||Typ pliku elementu na podstawie rozszerzenia pliku.|
|Identyfikator grupy|Groupid|Group_ID|Grupuje wszystkie elementy dla poczty e-mail i dokumentów. W przypadku wiadomości e-mail obejmuje to wiadomość oraz wszystkie załączniki i wyodrębnione elementy. W przypadku dokumentów obejmuje to dokument i wszystkie elementy osadzone.|
|Ma załącznik|EmailHasAttachment|Email_has_attachment|Wskazuje, czy komunikat zawiera załączniki.|
|Ma adwokata|HasAttorney||**Prawda** , gdy na liście adwokatów znajduje się co najmniej jeden z uczestników; W przeciwnym razie wartość to **False**.|
|HasText*||Has_text|Wskazuje, czy element ma tekst. możliwe wartości to **True** i **False**.|
|Niezmienny identyfikator||Immutable_ID|Ten identyfikator służy do unikatowego identyfikowania dokumentu w zestawie przeglądów. Tego pola nie można użyć w wyszukiwaniu zestawu przeglądów, a identyfikatora nie można użyć do uzyskania dostępu do dokumentu w jego lokalizacji natywnej.|
|Typ inkluzywny|Typ inkluzywny|Inclusive_type|Typ inkluzywny obliczany na potrzeby analizy: **0** — nie inkluzywny; **1** — inkluzywne; **2** — włącznie minus; **3** — kopiowanie inkluzywne.|
|W polu Odpowiedz na identyfikator||In_reply_to_ID|W odpowiedzi na identyfikator z wiadomości.|
|InputFileExtension||Original_file_extension|Oryginalne rozszerzenie pliku.|
|InputFileID||Input_file_ID|Identyfikator pliku elementu najwyższego poziomu w zestawie przeglądów. W przypadku załącznika ten identyfikator będzie identyfikatorem elementu nadrzędnego. Może służyć do grupowania rodzin razem.|
|Jest nowoczesnym załącznikem|IsModernAttachment||Ten plik jest nowoczesnym załącznikiem lub połączonym plikiem.|
|Pochodzi z wersji dokumentu|IsFromDocumentVersion||Bieżący dokument pochodzi z innej wersji innego dokumentu.|
|Jest załącznik wiadomości e-mail|IsEmailAttachment||Ten element pochodzi z załącznika wiadomości e-mail, który jest wyświetlany jako dołączony element do wiadomości.|
|Jest załącznik w tekście|IsInlineAttachment||Ten element został dołączony w tekście i jest wyświetlany w treści wiadomości.|
|Jest reprezentatywny|IsRepresentative|Is_representative|Jeden dokument w każdym zestawie dokładnych duplikatów jest oznaczony jako reprezentatywny.|
|Klasa elementu|ItemClass|Item_class|Klasa elementów dostarczana przez serwer exchange; na przykład **IPM. Uwaga**|
|Data ostatniej modyfikacji|LastModifiedDate|Doc_date_modified|Data ostatniej modyfikacji z metadanych dokumentu.|
|Identyfikator obciążenia|LoadId|Load_ID|Identyfikator zestawu obciążenia, w którym element został dodany do zestawu przeglądów.|
|Lokalizacja|Lokalizacja|Lokalizacja|Ciąg wskazujący typ lokalizacji, z której pochodzą dokumenty.<p>**Zaimportowane dane** — dane inne niż Office 365<br>**Teams** — Microsoft Teams<br>**Exchange** — skrzynki pocztowe programu Exchange<br>**SharePoint** — witryny programu SharePoint<br>**OneDrive** — konta usługi OneDrive|
|Nazwa lokalizacji|Nazwa lokalizacji|Location_name|Ciąg identyfikujący źródło elementu. W przypadku wymiany będzie to adres SMTP skrzynki pocztowej. Dla programu SharePoint i usługi OneDrive adres URL zbioru witryn.|
|||Marked_as_pivot|Ten plik jest elementem przestawnym w niemal zduplikowanym zestawie.|
|Oznaczony jako reprezentatywny|MarkAsRepresentative||Jeden dokument z każdego zestawu dokładnych duplikatów jest oznaczony jako przedstawiciele.|
|Data zakończenia spotkania|Data_spotkaniaa|Meeting_end_date|Data zakończenia spotkania.|
|Data rozpoczęcia spotkania|Data rozpoczęcia spotkania|Meeting_start_date|Data rozpoczęcia spotkania.|
|Rodzaj komunikatu|MessageKind|Message_kind|Typ wiadomości do wyszukania. Możliwe wartości: **<p>kontakty <br>docs <br>email <br>externaldata <br>faxes <br>im <br>journals <br>meetings <br>microsoftteams** (zwraca elementy z czatów, spotkań i połączeń w usłudze Microsoft Teams) **<br>notuje <br>wpisy <br>rssfeeds <br>zadania <br>poczty głosowej**|
|Identyfikator nadrzędny nowoczesnego załącznika||ModernAttachment_ParentId|Niezmienny identyfikator obiektu nadrzędnego dokumentu.|
|Rozszerzenie natywne|NativeExtension|Native_extension|Natywne rozszerzenie elementu.|
|Nazwa pliku natywnego|NativeFileName|Native_file_name|Natywna nazwa pliku elementu.|
|NativeMD5||Native_MD5|Skrót MD5 (wartość skrótu 128-bitowego) strumienia plików.|
|NativeSHA256||Native_SHA_256|Skrót SHA256 (256-bitowa wartość skrótu) strumienia plików.|
|Sortowanie ND/ET: wykluczanie załączników|NdEtSortExclAttach|ND_ET_sort_excl_attach|Łączenie zestawu wątku poczty e-mail (ET) i zestawu prawie zduplikowanych (ND). To pole służy do wydajnego sortowania w czasie przeglądu. **D jest** prefiksem do zestawów ND i **E** jest prefiksem do zestawów ET.|
|Sortowanie ND/ET: dołączanie załączników|NdEtSortInclAttach|ND_ET_sort_incl_attach|Łączenie zestawu wątku poczty e-mail (ET) i zestawu niemal zduplikowanego (ND). To pole służy do wydajnego sortowania w czasie przeglądu. **D jest** prefiksem do zestawów ND i **E** jest prefiksem do zestawów ET. Po każdym elemencie wiadomości e-mail w zestawie ET następuje jego odpowiednie załączniki.|
|Zduplikowany zestaw zbliżeniu||ND_set|Elementy podobne do dokumentu przestawnego współużytkują ten sam ND_set.|
|Autorzy usługi O365||O365_authors|Tworzenie z programu SharePoint.|
|O365 utworzony przez||O365_created_by|Utworzony przez program SharePoint.|
|Data utworzenia usługi O365||O365_date_created|Data utworzenia z programu SharePoint.|
|O365ModifiedDate||O365_date_modified|Data modyfikacji dokumentu (lub wersji dokumentu) zebranego z programu SharePoint lub OneDrive dla Firm. Jest to ta sama data modyfikacji co data wyświetlana w historii wersji w środowisku użytkownika programu SharePoint i usługi OneDrive.|
|O365 zmodyfikowany przez||O365_modified_by|Zmodyfikowane przy użyciu programu SharePoint lub OneDrive.|
|Inni opiekunowie|DedupedCustodians|Deduped_custodians|Lista opiekunów dokumentów, które są dokładne duplikaty (dla poczty e-mail, na podstawie zawartości; dla dokumentów, na podstawie skrótu).|
|Inne identyfikatory plików|DedupedFileIds|Deduped_file_IDs|Lista identyfikatorów plików dokumentów, które są dokładnymi duplikatami (dla poczty e-mail, na podstawie zawartości; dla dokumentów na podstawie skrótu).|
|Inne ścieżki|Dedupedcompoundpath|Deduped_compound_path|Lista złożonych ścieżek dokumentów, które są dokładnymi duplikatami (adres e-mail: na podstawie zawartości, dokumentów: na podstawie skrótu).|
|Identyfikator nadrzędny|Parentid|Parent_ID|Identyfikator elementu nadrzędnego.|
|Parentnode||Parent_node|Najbliższa poprzednia wiadomość e-mail w wątku wiadomości e-mail.|
|Domeny uczestników|Domeny uczestników|Email_participant_domains|Lista wszystkich domen uczestników wiadomości.|
|Uczestników|Uczestników|Email_participants|Lista wszystkich uczestników wiadomości; na przykład Sender, To, Cc, Bcc.|
|Identyfikator tabeli przestawnej|Identyfikator przestawny|Pivot_ID|Identyfikator tabeli przestawnej.|
|Potencjalnie uprzywilejowane|PotencjalniePrivileged|Potentially_privileged|Prawda, jeśli model wykrywania uprawnień adwokackiego klienta uwzględnia dokument potencjalnie uprzywilejowany|
|Stan przetwarzania|ProcessingStatus|Error_code|Stan przetwarzania po dodaniu elementu do zestawu przeglądów.|
|Odczyt percentylu|ReadPercentile||Odczyt percentyla dokumentu na podstawie istotności.|
|Otrzymał|Otrzymał|Email_date_received|Data i godzina odebrania wiadomości e-mail w formacie UTC.|
|Liczba adresatów||Recipient_count|Liczba adresatów w wiadomości.|
|Domeny adresatów|Domeny adresatów|Email_recipient_domains|Lista wszystkich domen adresatów wiadomości.|
|Adresatów|Adresatów|Email_recipients|Lista wszystkich adresatów wiadomości (Do, DW, Bcc).|
|||Redacted_file_path|Ścieżka zredagowanego pliku zastępczego w eksporcie.|
|||Redacted_text_path|Ścieżka zamiany zredagowanego pliku tekstowego w eksporcie. Tylko do użytku wewnętrznego firmy Microsoft.|
|Problem z przypadkiem tagu istotności 1||Relevance_tag_case_issue_1|Problem z wielkością liter tagu istotności 1 od istotności.|
|Wynik istotności|RelevanceScore||Wynik istotności dokumentu na podstawie istotności.|
|Tag istotności|Znacznik istotności||Wynik istotności dokumentu na podstawie istotności.|
|Identyfikator przedstawiciela|Identyfikator przedstawiciela||Identyfikator liczbowy każdego zestawu dokładnych duplikatów.|
|||Row_number|Numer wiersza elementu w pliku ładowania.|
|Nadawcy|Nadawcy|Email_sender|Pole nadawcy (od) dla typów komunikatów. Format to **DisplayName \<SmtpAddress>**.|
|Nadawca/autor|SenderAuthor||Pole obliczeniowe składające się z nadawcy lub autora elementu.|
|Domena nadawcy|Domena nadawcy|Email_sender_domain|Domena nadawcy.|
|Wysłane|Wysłane|Email_date_sent|Data wysłania wiadomości.<br>Czaty: data rozpoczęcia od transkrypcji|
|Ustaw kolejność: Najpierw inkluzywne|SetOrderInclusivesFirst|Set_order_inclusives_first|Pole sortowania — adres e-mail i załączniki: counter-chronologiczne; dokumenty: najpierw przestawny, a następnie przez malejący wynik podobieństwa.|
|Ustaw identyfikator||Set_ID|Dokumenty o podobnej zawartości (ND_set) lub wiadomości e-mail w tym samym wątku wiadomości e-mail (Email_set) współużytkuje te same Set_ID.|
|PodobieństwoPercent||Similarity_percent|Wskazuje, jak podobny jest dokument do tabeli przestawnej niemal duplikatu zestawu.|
|Natywny rozmiar pliku|Rozmiar|Native_size|Liczba bajtów elementu natywnego.|
|Temat|Temat|Email_subject|Temat wiadomości.|
|Temat/tytuł|SubjectTitle||Pole obliczeniowe składające się z tematu lub tytułu elementu.|
|Tagi|Tagi|Tagi|Tagi zastosowane w zestawie przeglądów.|
|Nazwa kanału|Kanał|Channelname|Jest to nazwa kanału usługi Teams. Dotyczy tylko zawartości usługi Microsoft Teams.|
|Nazwa zespołu|Teamname|Teamname|**Zespołów:** Nazwa zespołu<br>**Yammer:** Nazwa społeczności|
|Lista motywów|Lista motywów|Themes_list|Lista motywów obliczana na potrzeby analizy.|
|Tytuł|Tytuł|Doc_title|Tytuł z metadanych dokumentu. Tytuł z metadanych dokumentu. W przypadku zawartości usługi Teams i Yammer jest to wartość z właściwości ConversationName.|
|Do|Do|Email_to|Do pola dla typów komunikatów. Format to **DisplayName\<SmtpAddress>**|
|Unikatowy w zestawie poczty e-mail|UniqueInEmailSet||**Fałsz** , jeśli w zestawie poczty e-mail znajduje się duplikat załącznika.|
|Identyfikator grupy wersji||Version_Group_Id|Grupuje różne wersje tego samego dokumentu.|
|Versionnumber||Version_Number|Numer wersji dokumentu zebranego z programu SharePoint lub OneDrive dla Firm. Jest to ten sam numer wersji co ten wyświetlany w historii wersji w środowisku użytkownika programu SharePoint i usługi OneDrive.|
|Została skorygowana|WasRemediated|Was_Remediated|**Prawda** , jeśli element został skorygowany, w przeciwnym razie **false**.|
|Liczba wyrazów|Wordcount|Word_count|Liczba wyrazów w elemencie.|
|||||

> [!NOTE]
> Aby uzyskać więcej informacji na temat właściwości z możliwością wyszukiwania podczas wyszukiwania Office 365 lokalizacji zawartości podczas zbierania danych dla przypadku zbierania elektronicznych materiałów dowodowych (Premium), zobacz [Zapytania słów kluczowych i warunki wyszukiwania dla wyszukiwania zawartości](keyword-queries-and-search-conditions.md).
