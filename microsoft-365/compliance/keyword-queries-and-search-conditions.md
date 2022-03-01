---
title: Zapytania słów kluczowych i warunki wyszukiwania dotyczące zbierania elektronicznych materiałów dowodowych
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: article
f1_keywords:
- ms.o365.cc.SearchQueryLearnMore
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
ms.assetid: c4639c2e-7223-4302-8e0d-b6e10f1c3be3
ms.custom:
- seo-marvel-apr2020
description: Informacje o właściwościach wiadomości e-mail i dokumentów, które można wyszukiwać przy użyciu narzędzi wyszukiwania zbierania elektronicznych materiałów dowodowych w programie Microsoft 365.
ms.openlocfilehash: 390d0721dc5b256da224c70573953e23bbb91225
ms.sourcegitcommit: aac7e002ec6e10a41baa2d0bd38614b0ed471a70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/27/2022
ms.locfileid: "63009668"
---
# <a name="keyword-queries-and-search-conditions-for-ediscovery"></a>Zapytania słów kluczowych i warunki wyszukiwania dotyczące zbierania elektronicznych materiałów dowodowych

W tym artykule opisano właściwości wiadomości e-mail i dokumentów, które można wyszukiwać w elementach poczty e-mail i konwersacjach na czacie w programie Exchange Online oraz dokumenty przechowywane w witrynach usług SharePoint i OneDrive dla Firm przy użyciu narzędzi wyszukiwania zbierania elektronicznych materiałów dowodowych w Microsoft Teams Centrum zgodności platformy Microsoft 365. Obejmuje to wyszukiwanie zawartości, podstawowe zbierania elektronicznych materiałów dowodowych i Advanced eDiscovery (wyszukiwania zbierania elektronicznych materiałów dowodowych w Advanced eDiscovery są nazywane *kolekcjami*). Do wyszukiwania tych właściwości **\*** możesz również użyć poleceń cmdlet -ComplianceSearch w programie PowerShell & w Centrum zabezpieczeń i zgodności. W tym artykule opisano również:

- Uściślij wyniki wyszukiwania za pomocą operatorów wyszukiwania, warunków wyszukiwania i innych technik zapytań wyszukiwania.
- Wyszukiwanie typów danych poufnych i niestandardowych typów danych poufnych w SharePoint i OneDrive dla Firm.
- Wyszukiwanie zawartości witryny, która jest udostępniana użytkownikom spoza organizacji

Aby uzyskać instrukcje krok po kroku dotyczące tworzenia różnych wyszukiwań zbierania elektronicznych materiałów dowodowych, zobacz:

- [Przeszukiwanie zawartości](content-search.md)
- [Wyszukiwanie zawartości w podstawowym zbierania elektronicznych materiałów dowodowych](search-for-content-in-core-ediscovery.md)
- [Tworzenie kolekcji roboczej w programie Advanced eDiscovery](create-draft-collection.md)

> [!NOTE]
> Podczas wyszukiwania zbierania elektronicznych materiałów dowodowych w programie Centrum zgodności platformy Microsoft 365 **\*** i odpowiadających im poleceń cmdlet -ComplianceSearch w Centrum zabezpieczeń & zgodności programu PowerShell jest używany język KQL (Keyword Query Language). Aby uzyskać bardziej szczegółowe informacje, zobacz [Informacje dotyczące składni języka kwerend słów kluczowych](/sharepoint/dev/general-development/keyword-query-language-kql-syntax-reference).

## <a name="searchable-email-properties"></a>Właściwości poczty e-mail z polem wyszukiwania

W poniższej tabeli wymieniono właściwości wiadomości **e-mail**, które można przeszukiwać za pomocą narzędzi wyszukiwania zbierania elektronicznych materiałów dowodowych w programie Centrum zgodności platformy Microsoft 365 lub za pomocą polecenia cmdlet **New-ComplianceSearch lub Set-ComplianceSearch**. Tabela zawiera przykład składni  _właściwość:wartość_ dla każdej właściwości oraz opis wyników wyszukiwania zwróconych w przykładach. Możesz wpisać te pary w  `property:value` polu słów kluczowych na temat wyszukiwania zbierania elektronicznych materiałów dowodowych.

> [!NOTE]
> Wyszukując właściwości poczty e-mail, nie można wyszukiwać elementów, w których określona właściwość jest pusta lub pusta. Na przykład użycie pary *właściwość:wartość* **tematu:"" w** celu wyszukania wiadomości e-mail z pustym wierszem tematu spowoduje zwrócenie zerowych wyników. Dotyczy to również wyszukiwania właściwości witryny i kontaktu.

|Właściwość|Opis właściwości|Przykłady|Wyniki wyszukiwania zwrócone w przykładach|
|---|---|---|---|
|Nazwy załączników|Nazwy plików dołączonych do wiadomości e-mail.|`attachmentnames:annualreport.ppt` <p> `attachmentnames:annual*` <br/> `attachmentnames:.pptx`|Wiadomości z dołączonym plikiem o nazwie annualreport.ppt. W drugim przykładzie użycie symbolu wieloznacznego ( * ) zwraca wiadomości z wyrazem "roczny" w nazwie pliku załącznika. W trzecim przykładzie są zwracane wszystkie załączniki z rozszerzeniem pptx.|
|UDW|Pole UDW wiadomości e-mail. <sup>1</sup>|`bcc:pilarp@contoso.com` <p> `bcc:pilarp` <p> `bcc:"Pilar Pinilla"`|We wszystkich przykładach zwracane są wiadomości z pilarem Pinilla uwzględnioną w polu UDW.|
|Kategoria|Kategorie do przeszukania. Kategorie mogą być definiowane przez użytkowników za pomocą Outlook lub Outlook w sieci Web (wcześniej nazywanego Outlook Web App). Dopuszczalne wartości: <ul><li>niebieski<li>zielony<li>pomarańczowy<li>purpurowy<li>czerwony<li>żółty</li></ul>|`category:"Red Category"`|Wiadomości, do których przypisano czerwoną kategorię w źródłowych skrzynkach pocztowych.|
|DW|Pole DW wiadomości e-mail. <sup>1</sup>|`cc:pilarp@contoso.com` <p> `cc:"Pilar Pinilla"`|W obu przykładach wiadomości z pilarem Pinilla określone w polu DW.|
|Folderid|Identyfikator folderu (GUID) określonego folderu skrzynki pocztowej. Jeśli korzystasz z tej właściwości, pamiętaj, aby przeszukać skrzynkę pocztową, w którym znajduje się określony folder. Przeszukiwany będzie tylko określony folder. Podfoldery w folderze nie będą przeszukiwane. Aby wyszukać podfoldery, należy użyć właściwości Folderid dla podfolderu, który ma zostać przeszukany. <p> Aby uzyskać więcej informacji na temat wyszukiwania właściwości Folderid i używania skryptu do uzyskiwania identyfikatorów folderów dla określonej skrzynki pocztowej, zobacz Używanie wyszukiwania zawartości dla kolekcji [docelowej](use-content-search-for-targeted-collections.md).|`folderid:4D6DD7F943C29041A65787E30F02AD1F00000000013A0000` <p> `folderid:2370FB455F82FC44BE31397F47B632A70000000001160000 AND participants:garthf@contoso.com`|W pierwszym przykładzie są zwracane wszystkie elementy z określonego folderu skrzynki pocztowej. W drugim przykładzie są zwracane wszystkie elementy z określonego folderu skrzynki pocztowej, które zostały wysłane lub odebrane przez garthf@contoso.com.|
|Od|Nadawca wiadomości e-mail. <sup>1</sup>|`from:pilarp@contoso.com` <p> `from:contoso.com`|Wiadomości wysłane przez określonego użytkownika lub wysłane z określonej domeny.|
|HasAttachment|Wskazuje, czy wiadomość ma załącznik. Użyj wartości **prawda lub** **fałsz**.|`from:pilar@contoso.com AND hasattachment:true`|Wiadomości wysłane przez określonego użytkownika, które mają załączniki.|
|Ważność|Ważność wiadomości e-mail, którą nadawca może określić podczas wysyłania wiadomości. Domyślnie wiadomości są wysyłane z normalnym ważnością, chyba że nadawca ustawia ważność jako **wysoką** lub **niską**.|`importance:high` <p> `importance:medium` <p> `importance:low`|Wiadomości o wysokiej, średniej ważności lub niskiej ważności.|
|IsRead|Wskazuje, czy wiadomości zostały przeczytane. Użyj wartości **prawda lub** **fałsz**.|`isread:true` <p> `isread:false`|W pierwszym przykładzie są zwracane wiadomości z właściwością IsRead ustawioną na **wartość True (Prawda**). Drugi przykład zwraca wiadomości z właściwością IsRead ustawioną na wartość **False (Fałsz**).|
|ItemClass|Ta właściwość pozwala przeszukiwać określone typy danych innych firm, które twoja organizacja zaimportowała do Office 365. Użyj następującej składni tej właściwości:  `itemclass:ipm.externaldata.<third-party data type>*`|`itemclass:ipm.externaldata.Facebook* AND subject:contoso` <p> `itemclass:ipm.externaldata.Twitter* AND from:"Ann Beebe" AND "Northwind Traders"`|W pierwszym przykładzie są zwracane elementy serwisu Facebook, które zawierają wyraz "contoso" we właściwości Temat. Drugi przykład zwraca elementy w serwisie Twitter opublikowane przez Ann Beebe i zawierające frazę słowa kluczowego "Northwind Traders". <p> Aby uzyskać pełną listę wartości do użycia dla typów danych innych firm dla właściwości ItemClass, zobacz Używanie wyszukiwania zawartości do wyszukiwania danych innych firm, które zaimportowano do [Office 365.](use-content-search-to-search-third-party-data-that-was-imported.md)|
|Rodzaj|Typ wiadomości e-mail, która ma być wyszukiwana. Możliwe wartości: <p>  kontakty <p>  dokumenty <p>  Adres e-mail <p>  dane zewnętrzne <p>  faksy <p>  wiadomości błyskawiczne <p>  dzienników <p>  spotkania <p>  microsoftteams (zwraca elementy z czatów, spotkań i połączeń w Microsoft Teams) <p>  notatki <p>  wpisy <p>  rssfeeds <p>  zadania <p>  poczta głosowa|`kind:email` <p> `kind:email OR kind:im OR kind:voicemail` <p> `kind:externaldata`|W pierwszym przykładzie są zwracane wiadomości e-mail, które spełniają kryteria wyszukiwania. W drugim przykładzie są zwracane wiadomości e-mail, konwersacje za pomocą wiadomości błyskawicznych (w tym konwersacje Skype dla firm i czaty w programie Microsoft Teams) oraz wiadomości głosowe, które spełniają kryteria wyszukiwania. W trzecim przykładzie są zwracane elementy zaimportowane do skrzynek pocztowych w programie Microsoft 365 ze źródeł danych innych firm, takich jak Twitter, Facebook i Cisco Jabber, które spełniają kryteria wyszukiwania. Aby uzyskać więcej informacji, zobacz [Archiwizowanie danych innych firm w programie Office 365](https://www.microsoft.com/?ref=go).|
|Uczestnicy|Wszystkie pola osób w wiadomości e-mail. Te pola to Od, Do, DW i <sup>UDW.1</sup>.|`participants:garthf@contoso.com` <p> `participants:contoso.com`|Wiadomości wysłane przez firmę garthf@contoso.com. Drugi przykład zwraca wszystkie wiadomości wysłane przez użytkownika lub wysłane do użytkownika w contoso.com domenie.|
|Odebrano|Data, do dnia, w który wiadomość e-mail została odebrana przez adresata.|`received:2021-04-15` <p> `received>=2021-01-01 AND received<=2021-03-31`|Wiadomości otrzymane 15 kwietnia 2021 r. Drugi przykład zwraca wszystkie wiadomości otrzymane między 1 stycznia 2021 r. a 31 marca 2021 r.|
|Adresaci|Wszystkie pola adresatów w wiadomości e-mail. Te pola to Do, DW i <sup>UDW.1</sup>|`recipients:garthf@contoso.com` <p> `recipients:contoso.com`|Wiadomości wysyłane do garthf@contoso.com. Drugi przykład zwraca wiadomości wysłane do dowolnego adresata z contoso.com domeny.|
|Wysłano|Data wysłania wiadomości e-mail przez nadawcę.|`sent:2021-07-01` <p> `sent>=2021-06-01 AND sent<=2021-07-01`|Wiadomości wysłane w określonym dniu lub wysłane w określonym zakresie dat.|
|Rozmiar|Rozmiar elementu (w bajtach).|`size>26214400` <p> `size:1..1048567`|Wiadomości o rozmiarze ponad 25 MB. Drugi przykład zwraca wiadomości o rozmiarze od 1 do 1 048 567 bajtów (1 MB).|
|Temat|Tekst w wierszu tematu wiadomości e-mail. <p> **Uwaga:** W przypadku użycia w zapytaniu właściwości Temat w wynikach wyszukiwania są zwracane wszystkie wiadomości, w których wiersz tematu zawiera wyszukiwany tekst. Oznacza to, że zapytanie nie zwraca tylko tych wiadomości, które mają dokładne dopasowanie. Jeśli na przykład zostanie wyszukana ,  `subject:"Quarterly Financials"`wyniki będą zawierać wiadomości z tematem "Kwartalne finanse 2018".|`subject:"Quarterly Financials"` <p> `subject:northwind`|Wiadomości zawierające frazę "Kwartalne finanse" w dowolnym miejscu w tekście wiersza tematu. W drugim przykładzie są zwracane wszystkie wiadomości zawierające wyraz northwind w wierszu tematu.|
|Do|Pole Do wiadomości e-mail. <sup>1</sup>|`to:annb@contoso.com` <p> `to:annb ` <br/> `to:"Ann Beebe"`|Wszystkie przykłady zwracają wiadomości, w których w wierszu Do jest określony byk Ann Beebe.|

> [!NOTE]
> <sup>1</sup> Dla wartości właściwości adresata do określenia użytkownika możesz użyć adresu e-mail (nazywanego  również główną nazwą użytkownika lub główną nazwą użytkownika), nazwy wyświetlanej lub aliasu. Na przykład za pomocą nazwy annb@contoso.com, annb lub "Ann Beebe" można określić użytkownika Anna Beebe.

### <a name="recipient-expansion"></a>Rozszerzenie adresatów

Wyszukując dowolne właściwości adresata (Od, Do, DW, UDW, Uczestnicy i Adresaci), program Microsoft 365 próbuje rozszerzyć tożsamość każdego użytkownika, wyszukując go w usłudze Azure Active Directory (Azure AD).  Jeśli użytkownik zostanie znaleziony w usłudze Azure AD, zapytanie zostanie rozwinięte, aby uwzględnić jego adres e-mail (lub nazwę UPN), alias, nazwę wyświetlaną i LegacyExchangeDN. Na przykład zapytanie, takie jak `participants:ronnie@contoso.com` rozszerza się na `participants:ronnie@contoso.com OR participants:ronnie OR participants:"Ronald Nelson" OR participants:"<LegacyExchangeDN>"`.

Aby zapobiec rozsyłaniu adresatów, dodaj symbol wieloznacznych (gwiazdkę) na końcu adresu e-mail i użyj zmniejszonej nazwy domeny. Na przykład adres e-mail `participants:"ronnie@contoso*"` należy owijać podwójnym cudzysłowem.

Pamiętaj jednak, że uniemożliwienie rozszerzenia adresatów w zapytaniu wyszukiwania może spowodować, że odpowiednie elementy nie zostaną zwrócone w wynikach wyszukiwania. Wiadomości e-Exchange w polach adresatów można zapisywać w różnych formatach tekstowych. Rozszerzenie adresatów ma na celu ograniczenie tego faktu przez zwracanie wiadomości, które mogą zawierać różne formaty tekstu. Dlatego uniemożliwianie rozszerzenia adresatów może spowodować, że zapytanie wyszukiwania nie zwróci wszystkich elementów, które mogą być istotne dla Twojego badania.

> [!NOTE]
> Jeśli chcesz przejrzeć lub zmniejszyć elementy zwrócone przez zapytanie wyszukiwania z powodu rozszerzenia adresatów, rozważ użycie funkcji Advanced eDiscovery. Możesz wyszukiwać wiadomości (korzystając z rozszerzenia adresatów), dodawać je do zestawu recenzji, a następnie sprawdzać lub zawężać wyniki za pomocą zapytań lub filtrów zestawu recenzji. Aby uzyskać więcej informacji, zobacz [Zbieranie danych dotyczących sprawy](collecting-data-for-ediscovery.md) i [Wykonywanie zapytań dotyczących danych w zestawie recenzji](review-set-search.md).

## <a name="searchable-site-properties"></a>Właściwości witryny z polem wyszukiwania

W poniższej tabeli wymieniono niektóre właściwości usług SharePoint i OneDrive dla Firm, które można przeszukiwać za pomocą narzędzi wyszukiwania zbierania elektronicznych materiałów dowodowych w Centrum zgodności usługi Microsoft 365 lub polecenia cmdlet **New-ComplianceSearch** lub **Set-ComplianceSearch**. Tabela zawiera przykład składni  _właściwość:wartość_ dla każdej właściwości oraz opis wyników wyszukiwania zwróconych w przykładach.

Aby uzyskać pełną listę właściwości SharePoint, które można przeszukiwać, zobacz Omówienie właściwości przeszukanych i zarządzanych [w programie SharePoint](/SharePoint/technical-reference/crawled-and-managed-properties-overview). Właściwości oznaczone jako **Tak w** kolumnie **Kwerenda** mogą być przeszukiwane.

|Właściwość|Opis właściwości|Przykład|Wyniki wyszukiwania zwrócone w przykładach|
|---|---|---|---|
|Autor|Pole autora z Office, które pozostaje zachowywane w przypadku skopiowania dokumentu. Jeśli na przykład użytkownik utworzy dokument i prześle go w wiadomości e-mail do innej osoby, która następnie przekaże go do SharePoint, dokument zachowa oryginalny autor. Pamiętaj, aby dla tej właściwości użyć nazwy wyświetlanej użytkownika.|`author:"Garth Fort"`|Wszystkie dokumenty autorstwa Fort Garth.|
|ContentType|Typ SharePoint elementu, takiego jak Element, Dokument lub Wideo.|`contenttype:document`|Zostaną zwrócone wszystkie dokumenty.|
|Utwórz|Data utworzenia elementu.|`created>=2021-06-01`|Wszystkie elementy utworzone 1 czerwca 2021 r. lub później.|
|CreatedBy|Osoba, która utworzyła lub przesłała element. Pamiętaj, aby dla tej właściwości użyć nazwy wyświetlanej użytkownika.|`createdby:"Garth Fort"`|Wszystkie elementy utworzone lub przekazane przez Fort Garth.|
|DetectedLanguage|Język elementu.|`detectedlanguage:english`|Wszystkie elementy w języku angielskim.|
|DocumentLink|Ścieżka (adres URL) określonego folderu w SharePoint lub OneDrive dla Firm sieci Web. W przypadku używania tej właściwości pamiętaj, aby przeszukać witrynę, w których znajduje się określony folder. <p> Aby zwrócić elementy znajdujące się w podfolderach folderu określonego dla właściwości documentlink, musisz dodać element /\* do adresu URL określonego folderu, na przykład `documentlink: "https://contoso.sharepoint.com/Shared Documents/*"` <p> <br/>Aby uzyskać więcej informacji na temat wyszukiwania właściwości documentlinku i używania skryptu do uzyskiwania adresów URL linków do dokumentów dla folderów w określonej witrynie, zobacz Używanie wyszukiwania zawartości dla kolekcji [docelowej](use-content-search-for-targeted-collections.md).|`documentlink:"https://contoso-my.sharepoint.com/personal/garthf_contoso_com/Documents/Private"` <p> `documentlink:"https://contoso-my.sharepoint.com/personal/garthf_contoso_com/Documents/Shared with Everyone/*" AND filename:confidential`|W pierwszym przykładzie są zwracane wszystkie elementy w określonym OneDrive dla Firm folderze. Drugi przykład zwraca dokumenty znajdujące się w określonym folderze witryny (i wszystkich podfolderach), które zawierają wyraz "poufne" w nazwie pliku.|
|Rozszerzenie pliku|Rozszerzenie pliku; na przykład docx, one, pptx lub xlsx.|`fileextension:xlsx`|Wszystkie Excel (Excel 2007 i nowsze)|
|Nazwa_pliku|Nazwa pliku.|`filename:"marketing plan"` <p> `filename:estimate`|W pierwszym przykładzie są zwracane pliki z dokładną frazą "plan marketingowy" w tytule. Drugi przykład zwraca pliki z wyrazem "estimate" w nazwie pliku.|
|LastModifiedTime|Data ostatniej zmiany elementu.|`lastmodifiedtime>=2021-05-01` <p> `lastmodifiedtime>=2021-05-01 AND lastmodifiedtime<=2021-06-01`|Pierwszy przykład zwraca elementy, które zostały zmienione 1 maja 2021 r. lub później. Drugi przykład zwraca elementy zmienione między 1 maja 2021 r. a 1 czerwca 2021 r.|
|ModifiedBy|Osoba, która ostatnio zmieniła element. Pamiętaj, aby dla tej właściwości użyć nazwy wyświetlanej użytkownika.|`modifiedby:"Garth Fort"`|Wszystkie elementy, które ostatnio zostały zmienione przez Fort Garth.|
|Ścieżka|Ścieżka (adres URL) określonej witryny w SharePoint lub OneDrive dla Firm sieci Web. <p> Aby zwrócić elementy tylko z określonej witryny, `/` musisz dodać końcówkę na końcu adresu URL, na przykład `path: "https://contoso.sharepoint.com/sites/international/"` <p> Aby zwrócić elementy znajdujące się w folderach w witrynie specify in the path property, musisz dodać `/*` na końcu adresu URL, na przykład  `path: "https://contoso.sharepoint.com/Shared Documents/*"` <p> **Uwaga:** Użycie tej `Path` właściwości do wyszukiwania OneDrive nie powoduje zwrócenia w wynikach wyszukiwania plików multimedialnych, takich jak pliki .png, tiff lub wav. Użyj innej właściwości witryny w zapytaniu wyszukiwania, aby wyszukać pliki multimedialne w OneDrive folderach. <br/>|`path:"https://contoso-my.sharepoint.com/personal/garthf_contoso_com/"` <p> `path:"https://contoso-my.sharepoint.com/personal/garthf_contoso_com/*" AND filename:confidential`|W pierwszym przykładzie są zwracane wszystkie elementy w określonej OneDrive dla Firm witryny. W drugim przykładzie są zwracane dokumenty znajdujące się w określonej witrynie (oraz foldery w witrynie), które zawierają wyraz "poufne" w nazwie pliku.|
|SharedWithUsersOWSUser|Dokumenty, które zostały udostępnione określoneowi użytkownikowi i wyświetlone na stronie Udostępnione  dla mnie w witrynie OneDrive dla Firm użytkownika. Są to dokumenty, które zostały jawnie udostępnione określoneowi użytkownikowi przez inne osoby w organizacji. W przypadku eksportowania dokumentów, które pasują do zapytania wyszukiwania korzystającego z właściwości SharedWithUsersOWSUser, dokumenty są eksportowane z oryginalnej lokalizacji zawartości osoby, która udostępniła dokument określoneowi użytkownikowi. Aby uzyskać więcej informacji, zobacz [Wyszukiwanie zawartości witryny udostępnionej w organizacji](#searching-for-site-content-shared-within-your-organization).|`sharedwithusersowsuser:garthf` <p> `sharedwithusersowsuser:"garthf@contoso.com"`|Oba przykłady zwracają wszystkie wewnętrzne dokumenty, które zostały jawnie udostępnione w Fortu Garth i które  są widoczne na stronie Udostępnione dla mnie w OneDrive dla Firm konta Fort Garth.|
|Witryna|Adres URL witryny lub grupy witryn w organizacji.|`site:"https://contoso-my.sharepoint.com"` <p> `site:"https://contoso.sharepoint.com/sites/teams"`|W pierwszym przykładzie są zwracane elementy OneDrive dla Firm witryny sieci Web dla wszystkich użytkowników w organizacji. Drugi przykład zwraca elementy ze wszystkich witryn zespołu.|
|Rozmiar|Rozmiar elementu (w bajtach).|`size>=1` <p> `size:1..10000`|W pierwszym przykładzie zwracana jest wartość większa niż 1 bajt. Drugi przykład zwraca elementy o rozmiarze od 1 do 10 000 bajtów.|
|Tytuł|Tytuł dokumentu. Właściwość Title to metadane określone w Microsoft Office dokumenty. Różni się ona od nazwy pliku dokumentu.|`title:"communication plan"`|Każdy dokument zawierający frazę "plan komunikacji" we właściwości metadanych tytułu dokumentu Office wiadomości.|

## <a name="searchable-contact-properties"></a>Właściwości kontaktu z polem wyszukiwania

W poniższej tabeli wymieniono właściwości kontaktów, które są indeksowane, i które można wyszukiwać przy użyciu narzędzi wyszukiwania zbierania elektronicznych materiałów dowodowych. Są to właściwości, które można skonfigurować dla kontaktów (nazywanych również kontaktami osobistymi) znajdujących się w osobistej książce adresowej skrzynki pocztowej użytkownika. Aby wyszukać kontakty, możesz wybrać skrzynki pocztowe do przeszukania, a następnie użyć co najmniej jednej właściwości kontaktu w zapytaniu słowa kluczowego.

> [!TIP]
> Aby wyszukać wartości zawierające spacje lub znaki specjalne, należy użyć znaków podwójnego cudzysłowu (" ") w celu wyszukania frazy. na przykład `businessaddress:"123 Main Street"`.

|Właściwość|Opis właściwości|
|---|---|
|BusinessAddress|Adres we właściwości **Adres** służbowy. Ta właściwość jest również nazywana adresem **służbowy** na stronie właściwości kontaktu.|
|Telefon BusinessPhone|Numer telefonu dowolnej właściwości biznesowej **Telefon** numer telefonu.|
|CompanyName|Nazwa **we właściwości Firma** .|
|Department|Nazwa właściwości **Department (** Dział).|
|DisplayName (Nazwa wyświetlana)|Nazwa wyświetlana kontaktu. Jest to nazwa we właściwości **Imię i nazwisko** kontaktu.|
|EmailAddress (Adres e-mail)|Adres dowolnej właściwości adresu e-mail kontaktu. Użytkownicy mogą dodać wiele adresów e-mail dla kontaktu. Użycie tej właściwości zwraca kontakty zgodne z dowolnymi adresami e-mail kontaktu.|
|FileAs|Właściwość **File as** (Plik jako). Ta właściwość służy do określania sposobu, w jaki kontakt ma być wymieniony na liście kontaktów użytkownika. Na przykład kontakt może być wymieniony jako  *Imię, Nazwisko*  lub  *Nazwisko, Imię*.|
|GivenName|Nazwa właściwości **Imię** .|
|HomeAddress|Adres we dowolnej właściwości **Adres** domowy.|
|Telefon Domowy|Numer telefonu we właściwościach **Domowy numer** telefonu.|
|ImAddress|Właściwość adresu wiadomości błyskawicznych, która zazwyczaj jest adresem e-mail używanym do wysyłania wiadomości błyskawicznych.|
|MiddleName|Nazwa właściwości **Drugie** imię.|
|Telefon komórkowy|Numer telefonu we właściwości **Numer** telefonu komórkowego.|
|Nick|Nazwa właściwości **Nick** .|
|Lokalizacja pakietu Office|Wartość we **właściwości Office** **lub Office lokalizacji**.|
|OtherAddress|Wartość właściwości **adresowej** Inne.|
|Surname (Nazwisko)|Nazwa właściwości **Nazwisko** .|
|Tytuł|Tytuł właściwości **Stanowisko** .|

## <a name="searchable-sensitive-data-types"></a>Typy danych poufnych, które można wyszukiwać

Za pomocą narzędzi wyszukiwania zbierania elektronicznych materiałów dowodowych w aplikacji Centrum zgodności platformy Microsoft 365 można wyszukiwać poufne dane, takie jak numery kart kredytowych czy numery PESEL, które są przechowywane w dokumentach w witrynach SharePoint i OneDrive dla Firm internetowych. Można to zrobić przy użyciu właściwości `SensitiveType` i nazwy (lub identyfikatora) typu informacji poufnych w zapytaniu słowa kluczowego. Na przykład zapytanie zwraca `SensitiveType:"Credit Card Number"` dokumenty zawierające numer karty kredytowej. Zapytanie zwraca  `SensitiveType:"U.S. Social Security Number (SSN)"` dokumenty zawierające amerykański numer PESZ.

Aby wyświetlić listę typów informacji poufnych, które można wyszukać,  \> przejdź do klasyfikacji danych **Typy** informacji poufnych w Centrum zgodności platformy Microsoft 365. Możesz też użyć polecenia cmdlet **Get-DlpSensitiveInformationType** w programie PowerShell w & Security & Compliance Center, aby wyświetlić listę typów informacji poufnych.

Aby uzyskać więcej informacji na temat tworzenia zapytań przy użyciu tej `SensitiveType` właściwości, zobacz Tworzenie zapytania w celu znalezienia [poufnych danych przechowywanych w witrynach](form-a-query-to-find-sensitive-data-stored-on-sites.md).

### <a name="limitations-for-searching-sensitive-data-types"></a>Ograniczenia dotyczące wyszukiwania typów danych poufnych

- Aby wyszukać niestandardowe typy informacji poufnych, musisz określić identyfikator typu informacji poufnych we właściwości `SensitiveType` . Użycie nazwy niestandardowego typu informacji poufnych (jak pokazano w przykładzie dla wbudowanych typów informacji poufnych w poprzedniej sekcji) nie spowoduje zwrócenia żadnych wyników. Użyj **kolumny Publisher** na stronie **Typy** informacji poufnych w Centrum zgodności (lub właściwości **Publisher** w programie PowerShell), aby odróżnić wbudowane od niestandardowych typów informacji poufnych. Wbudowane poufne typy danych mają wartość `Microsoft Corporation` właściwości **Publisher.**

  Aby wyświetlić nazwę i identyfikator niestandardowego typu danych poufnych w organizacji, uruchom następujące polecenie w programie PowerShell centrum zabezpieczeń & zgodności:

  ```powershell
  Get-DlpSensitiveInformationType | Where-Object {$_.Publisher -ne "Microsoft Corporation"} | FT Name,Id
  ```

  Następnie możesz użyć identyfikatora we właściwości `SensitiveType` wyszukiwania, aby zwrócić dokumenty zawierające niestandardowy poufny typ danych, na przykład `SensitiveType:7e13277e-6b04-3b68-94ed-1aeb9d47de37`

- Nie można używać typów informacji poufnych `SensitiveType` i właściwości wyszukiwania do wyszukiwania danych poufnych w miejscu w Exchange Online skrzynkach pocztowych. Obejmuje to wiadomości czatu 1:1, wiadomości czatu grupowego 1:N i konwersacje w kanale zespołu w Microsoft Teams, ponieważ cała ta zawartość jest przechowywana w skrzynkach pocztowych. Jednak przy użyciu zasad ochrony przed utratą danych (DLP, data loss prevention) możesz chronić poufne dane podczas przesyłania poczty e-mail. Aby uzyskać więcej informacji, zobacz [Informacje na temat ochrony przed utratą](dlp-learn-about-dlp.md) danych oraz [Wyszukiwanie i znajdowanie danych osobowych](/compliance/regulatory/gdpr).

## <a name="search-operators"></a>Operatory wyszukiwania

Logiczne operatory wyszukiwania, takie jak **ORAZ**, **LUB** i **NIE, ułatwiają** definiowanie bardziej precyzyjnych wyszukiwań, uwzględniając lub wykluczając określone wyrazy w zapytaniu wyszukiwania. Inne techniki, takie jak używanie operatorów właściwości ( `>=` takich jak lub `..`), cudzysłowów, nawiasów i symboli wieloznacznych, pomagają uściślić zapytanie wyszukiwania. W poniższej tabeli wymieniono operatory, za pomocą których można zawęzić lub poszerzyć wyniki wyszukiwania.

|Operator|Użycie|Opis|
|---|---|---|
|AND|słowo kluczowe1 AND słowo kluczowe2|Zwraca elementy, które zawierają wszystkie określone słowa kluczowe lub wyrażenia  `property:value` . Może to na przykład  `from:"Ann Beebe" AND subject:northwind` zwracać wszystkie wiadomości wysłane przez ann Beebe, które zawierały wyraz northwind w wierszu tematu. <sup>2</sup>|
|+|keyword1 + keyword2 + keyword3|Zwraca elementy zawierające  *albo i*  `keyword2`  `keyword3` *takie,*  które zawierają  `keyword1`. Dlatego ten przykład jest odpowiednikiem zapytania  `(keyword2 OR keyword3) AND keyword1`. <p> `keyword1 + keyword2` Zapytanie (ze spacją po **+** symbolu) nie jest tym samym co użycie operatora **AND**. To zapytanie będzie równoważne i  `"keyword1 + keyword2"` zwracało elementy z dokładną fazą  `"keyword1 + keyword2"`.|
|LUB|słowo kluczowe1 LUB słowo kluczowe2|Zwraca elementy, które zawierają co najmniej jedno z określonych słów kluczowych lub wyrażeń  `property:value` . <sup>2</sup>|
|NOT|keyword1 NOT keyword2 <p> NOT from:"Ann Beebe" <p> NOT kind:im|Wyklucza elementy określone za pomocą słowa kluczowego lub  `property:value` wyrażenia. W drugim przykładzie z wyłączeniem wiadomości wysłanych przez Anną Beebe. W trzecim przykładzie wyłączyliśmy wszelkie konwersacje za pomocą wiadomości błyskawicznych, takie Skype dla firm, które zostały zapisane w folderze skrzynki pocztowej Historia konwersacji. <sup>2</sup>|
|-|keyword1 -keyword2|To samo co **operator NOT** . W związku z tym to zapytanie zwraca elementy zawierające  `keyword1` elementy , i wyklucza je z nich  `keyword2`.|
|NEAR|keyword1 NEAR(n) keyword2|Zwraca elementy z wyrazami, które znajdują się blisko siebie, gdzie n oznacza liczbę wyrazów między sobą. Na przykład zwraca dowolny element, `best NEAR(5) worst` w którym wyraz "najgorsze" znajduje się w pięciu wyrazach "najlepsze". Jeśli nie zostanie określona żadna liczba, domyślna odległość wynosi osiem wyrazów. <sup>2</sup>|
|:|właściwość:wartość|Dwukropek (:) w składni  `property:value` określa, że szukana wartość właściwości zawiera określoną wartość. Na przykład zwraca wszystkie  `recipients:garthf@contoso.com` wiadomości wysłane do garthf@contoso.com.|
|=|property=value|To samo co operator **:** .|
|\<|wartośćwłasna\<|Oznacza, że przeszukiwana właściwość jest mniejsza niż określona wartość. <sup>1</sup>|
|\>|wartośćwłasna\>|Oznacza, że przeszukiwana właściwość jest większa niż określona wartość. <sup>1</sup>|
|\<=|property\<=value|Oznacza, że przeszukiwana właściwość jest mniejsza niż lub równa określonej wartości. <sup>1</sup>|
|\>=|property\>=value|Oznacza, że przeszukiwana właściwość jest większa niż lub równa określonej wartości. <sup>1</sup>|
|..|właściwość:wartość1.. wartość2|Oznacza, że przeszukiwana właściwość jest większa niż lub równa wartości1 i mniejsza niż lub równa wartości2. <sup>1</sup>|
|"  "|"wartość fair value" <p> subject:"Kwartalne dane finansowe"|W zapytaniu słowa kluczowego (w `property:value` polu Słowo kluczowe)  wpisz słowo kluczowe podwójne cudzysłów (" "), aby wyszukać dokładną frazę lub termin. Jeśli jednak używasz warunku wyszukiwania Temat  lub Temat **/** [](#search-conditions) Tytuł, nie dodawaj do wartości cudzysłowów podwójnych, ponieważ cudzysłowy są dodawane automatycznie podczas używania tych warunków wyszukiwania. Jeśli dodasz do wartości cudzysłowy, do wartości warunku zostaną dodane dwie pary podwójnych cudzysłowów i zapytanie wyszukiwania zwróci błąd. |
|\*|kot\* <p> temat:ustaw\*|Wyszukiwania prefiksów ( *nazywane także* dopasowywaniem prefiksów), gdzie symbol wieloznaczny ( * ) jest umieszczany na końcu wyrazu w słowach kluczowych lub zapytaniach `property:value` . W wyszukiwaniu prefiksów wyszukiwanie zwraca wyniki zawierające wyraz i znaki, po których następuje zero lub więcej znaków. Na przykład zwraca `title:set*` dokumenty zawierające wyrazy "set", "setup" i "setting" (oraz inne wyrazy, które zaczynają się od "zestawu") w tytule dokumentu. <p> **Uwaga:** Można używać tylko wyszukiwań prefiksów; na przykład **kot\**_ lub _* zestaw\**_. Wyszukiwania sufiksów (_*\*kot**), wyszukiwania infix (**ct\***) i wyszukiwania podrzędne (**\*\*** kot) nie są obsługiwane. <p> Ponadto dodanie ciągu ( \. ) na wyszukiwanie prefiksu spowoduje zmianę zwracanych wyników. Jest tak, ponieważ okres jest traktowany jako wyraz "stop". Na przykład wyszukanie **kota\**_ i wyszukanie argumentu _* kot.\*** spowoduje zwrócenie innych wyników. Nie zaleca się używania okresu w wyszukiwaniu prefiksów.|
|(  )|(fair OR free) ORAZ (z:contoso.com) <p> (IPO OR initial) AND (akcje LUB udziały) <p> (kwartalne finanse)|Nawiasy grupuje wyrażenia logiczne,  `property:value` elementy i słowa kluczowe. Na przykład zwraca  `(quarterly financials)` elementy zawierające wyrazy kwartalne i finansowe.|

> [!NOTE]
> <sup>1</sup> Tego operatora należy używać w przypadku właściwości, które mają wartości daty lub liczbowe.<br/> <sup>2 Operatory</sup> wyszukiwania w wartościach logicznych muszą być wielkie; na przykład **ORAZ**. W przypadku użycia operatora z małymi literami, takiego jak **i**, w zapytaniu wyszukiwania będzie on traktowany jak słowo kluczowe.

## <a name="search-conditions"></a>Warunki wyszukiwania

Możesz dodać do zapytania wyszukiwania warunki, aby zawęzić wyszukiwanie i zwrócić bardziej dopracowany zestaw wyników. Każdy warunek powoduje dodanie klauzuli do zapytania wyszukiwania WKQL, które jest tworzone i uruchamiane po rozpoczęciu wyszukiwania.

[Warunki dotyczące właściwości wspólnych](#conditions-for-common-properties)

[Warunki dotyczące właściwości poczty](#conditions-for-mail-properties)

[Warunki właściwości dokumentu](#conditions-for-document-properties)

[Operatory używane w warunkach](#operators-used-with-conditions)

[Wskazówki dotyczące korzystania z warunków](#guidelines-for-using-conditions)

[Przykłady użycia warunków w kwerendach wyszukiwania](#examples-of-using-conditions-in-search-queries)

### <a name="conditions-for-common-properties"></a>Warunki dotyczące właściwości wspólnych

Utwórz warunek przy użyciu właściwości wspólnych podczas przeszukiwania skrzynek pocztowych i witryn w tym samym wyszukiwaniu. W poniższej tabeli wymieniono dostępne właściwości, których można użyć podczas dodawania warunku.

|Warunek|Opis|
|---|---|
|Data|W przypadku wiadomości e-mail jest to data, w która wiadomość została odebrana przez adresata lub wysłana przez nadawcę. W przypadku dokumentów jest to data ostatniej modyfikacji dokumentu.|
|Nadawca/Autor|W przypadku wiadomości e-mail osoba, która wysłała wiadomość. W przypadku dokumentów osoba cytowana w polu autora może Office dokumenty. Możesz wpisać więcej niż jedno imię i nazwisko, oddzielając je przecinkami. Dwie lub więcej wartości jest logicznie połączonych **operatorem LUB** .|
|Rozmiar (w bajtach)|Zarówno w przypadku wiadomości e-mail, jak i dokumentów, rozmiar elementu (w bajtach).|
|Temat/tytuł|W przypadku wiadomości e-mail tekst w wierszu tematu wiadomości. W przypadku dokumentów jest to tytuł dokumentu. Jak wyjaśniono wcześniej, właściwość Tytuł to metadane określone w Microsoft Office dokumenty. Możesz wpisać więcej niż jedną nazwę tematu/tytułu, oddzielając ją przecinkami. Dwie lub więcej wartości jest logicznie połączonych **operatorem LUB** . <p> **Uwaga**: Nie dołączaj znaków podwójnego cudzysłowu do wartości tego warunku, ponieważ w przypadku użycia tego warunku wyszukiwania cudzysłowy są dodawane automatycznie. Jeśli do wartości zostanie dodany cudzysłów, do wartości warunku zostaną dodane dwie pary podwójnych cudzysłowów, a zapytanie wyszukiwania zwróci błąd.|
|Etykieta przechowywania|W przypadku wiadomości e-mail i dokumentów etykiety przechowywania, które zostały automatycznie przypisane do wiadomości i dokumentów przez zasady automatycznego oznaczania lub etykiety przechowywania, które zostały ręcznie przypisane przez użytkowników. Etykiety przechowywania służą do klasyfikowania wiadomości e-mail i dokumentów na temat zarządzania informacjami oraz wymuszania reguł przechowywania na podstawie ustawień zdefiniowanych na tej etykiecie. Można wpisać część nazwy etykiety przechowywania i użyć symbolu wieloznacznego lub wpisać pełną nazwę etykiety. Aby uzyskać więcej informacji na temat etykiet przechowywania, zobacz [Informacje o zasadach przechowywania i etykietach przechowywania](retention.md).|

### <a name="conditions-for-mail-properties"></a>Warunki dotyczące właściwości poczty

Utwórz warunek przy użyciu właściwości poczty podczas wyszukiwania w skrzynkach pocztowych lub folderach publicznych. W poniższej tabeli wymieniono właściwości poczty e-mail, których można użyć dla warunku. Te właściwości to podzbiór wcześniej opisanych właściwości poczty e-mail. Dla Twojej wygody opisy te są powtarzane.

|Warunek|Opis|
|---|---|
|Typ wiadomości|Typ wiadomości do wyszukania. Jest to ta sama właściwość, co właściwość E-mail typu. Możliwe wartości: <ul><li>kontakty</li><li>dokumenty</li><li>Adres e-mail</li><li>dane zewnętrzne</li><li>faks</li><li>wiadomości błyskawiczne</li><li>dzienników</li><li>spotkania</li><li>microsoftteams</li><li>notatki</li><li>wpisy</li><li>rssfeeds</li><li>zadania</li><li>poczta głosowa</li></ul>|
|Uczestnicy|Wszystkie pola osób w wiadomości e-mail. Te pola to Od, Do, DW i UDW.|
|Wpisać|Właściwość klasy wiadomości dla elementu wiadomości e-mail. Jest to ta sama właściwość co właściwość poczty e-mail ItemClass. Jest to również warunek wielowymiarowy. Aby zaznaczyć wiele klas wiadomości, przytrzymaj klawisz **CTRL** i kliknij co najmniej dwie klasy wiadomości na liście rozwijanej, którą chcesz dodać do warunku. Każda klasa wiadomości wybranej na liście będzie logicznie połączona przez operator **LUB** w odpowiednim zapytaniu wyszukiwania. <p> Aby uzyskać listę klas wiadomości (i odpowiadających im identyfikatorów klas wiadomości), które są używane przez program Exchange i które można wybrać na liście Klasa wiadomości, zobacz  Typy elementów i Klasy [wiadomości](/office/vba/outlook/Concepts/Forms/item-types-and-message-classes).|
|Odebrano|Data, do dnia, w który wiadomość e-mail została odebrana przez adresata. Jest to ta sama właściwość, co właściwość Odebrano pocztę e-mail.|
|Adresaci|Wszystkie pola adresatów w wiadomości e-mail. Te pola to Do, DW i UDW.|
|Nadawca|Nadawca wiadomości e-mail.|
|Wysłano|Data wysłania wiadomości e-mail przez nadawcę. Jest to ta sama właściwość, co właściwość Wysłano wiadomość e-mail.|
|Temat|Tekst w wierszu tematu wiadomości e-mail. <p> **Uwaga**: Nie dołączaj znaków podwójnego cudzysłowu do wartości tego warunku, ponieważ w przypadku użycia tego warunku wyszukiwania cudzysłowy są dodawane automatycznie. Jeśli do wartości zostanie dodany cudzysłów, do wartości warunku zostaną dodane dwie pary podwójnych cudzysłowów, a zapytanie wyszukiwania zwróci błąd.|
|Do|Adresat wiadomości e-mail w polu Do.|

### <a name="conditions-for-document-properties"></a>Warunki właściwości dokumentu

Utwórz warunek przy użyciu właściwości dokumentu podczas wyszukiwania dokumentów w witrynach SharePoint i OneDrive dla Firm dokumentów. W poniższej tabeli wymieniono właściwości dokumentu, których można użyć dla warunku. Te właściwości to podzbiór wcześniej opisanych właściwości witryny. Dla Twojej wygody opisy te są powtarzane.

|Warunek|Opis|
|---|---|
|Autor|Pole autora z Office, które pozostaje zachowywane w przypadku skopiowania dokumentu. Jeśli na przykład użytkownik utworzy dokument i prześle go w wiadomości e-mail do innej osoby, która następnie przekaże go do SharePoint, dokument zachowa oryginalny autor.|
|Tytuł|Tytuł dokumentu. Właściwość Title to metadane określone w Office dokumenty. Ta nazwa różni się od nazwy pliku dokumentu.|
|Utwórz|Data utworzenia dokumentu.|
|Ostatnia modyfikacja|Data ostatniej zmiany dokumentu.|
|Typ pliku|Rozszerzenie pliku; na przykład docx, one, pptx lub xlsx. Jest to ta sama właściwość co właściwość witryny FileExtension (Rozszerzenie Pliku). <p> **Uwaga:** Jeśli dołączysz warunek Typ pliku przy  użyciu operatora Równa  się lub Równa się w zapytaniu wyszukiwania, nie możesz użyć wyszukiwania prefiksu (przez dołączenie symbolu wieloznacznego ( \* ) na końcu typu pliku) do zwracania wszystkich wersji typu pliku. Jeśli to zrobisz, symbol wieloznaczny zostanie zignorowany. Jeśli na przykład dołączysz warunek `Equals any of doc*`, `.doc` zostaną zwrócone tylko pliki z rozszerzeniem. Pliki z rozszerzeniem `.docx` nie zostaną zwrócone. Aby zwrócić wszystkie wersje typu pliku, w zapytaniu słowa kluczowego używa się pary *property:value* ; na przykład `filetype:doc*`.|

### <a name="operators-used-with-conditions"></a>Operatory używane w warunkach

Podczas dodawania warunku możesz wybrać operator, który jest odpowiedni do typu właściwości warunku. W poniższej tabeli opisano operatory używane w warunkach oraz wymieniono ich odpowiednik użyty w zapytaniu wyszukiwania.

|Operator|Odpowiednik zapytania|Opis|
|---|---|---|
|Po|`property>date`|Używany z warunkami daty. Zwraca elementy, które zostały wysłane, odebrane lub zmodyfikowane po określonej dacie.|
|Przed|`property<date`|Używany z warunkami daty. Zwraca elementy, które zostały wysłane, odebrane lub zmodyfikowane przed określoną datą.|
|Between|`date..date`|Do użycia z warunkami daty i rozmiaru. W przypadku korzystania z warunku daty zwraca elementy, które zostały wysłane, odebrane lub zmodyfikowane w określonym zakresie dat. W przypadku korzystania z warunku rozmiaru zwraca elementy o rozmiarze wewnątrz określonego zakresu.|
|Zawiera dowolną z|`(property:value) OR (property:value)`|Używany z warunkami właściwości określającymi wartość ciągu. Zwraca elementy zawierające dowolną część jednej lub więcej określonych wartości ciągów.|
|Nie zawiera żadnych|`-property:value` <p> `NOT property:value`|Używany z warunkami właściwości określającymi wartość ciągu. Zwraca elementy, które nie zawierają żadnej części określonej wartości ciągu.|
|Nie równa się|`-property=value` <p> `NOT property=value`|Używany z warunkami właściwości określającymi wartość ciągu. Zwraca elementy, które nie zawierają określonego ciągu znaków.|
|Równa się|`size=value`|Zwraca elementy o określonym rozmiarze. <sup>1</sup>|
|Równa się dowolne z|`(property=value) OR (property=value)`|Używany z warunkami właściwości określającymi wartość ciągu. Zwraca elementy zgodne z jedną lub więcej określonymi wartościami ciągów.|
|Większe|`size>value`|Zwraca elementy, których określona właściwość jest większa niż określona wartość. <sup>1</sup>|
|Większe lub równe|`size>=value`|Zwraca elementy, w których określona właściwość jest większa niż lub równa określonej wartości. <sup>1</sup>|
|Mniej|`size<value`|Zwraca elementy, które są większe lub równe określonej wartości. <sup>1</sup>|
|Mniejsze lub równe|`size<=value`|Zwraca elementy, które są większe lub równe określonej wartości. <sup>1</sup>|
|Nie równa się|`size<>value`|Zwraca elementy, które nie są równe podanego rozmiaru. <sup>1</sup>|

> [!NOTE]
> <sup>1</sup> Ten operator jest dostępny tylko w przypadku warunków, które używają właściwości Size.

### <a name="guidelines-for-using-conditions"></a>Wskazówki dotyczące korzystania z warunków

Podczas korzystania z warunków wyszukiwania należy pamiętać o następujących kwestiach.

- Warunek jest logicznie połączony z zapytaniem słowa kluczowego (określonym w polu słowa kluczowego) przez operator **AND** . Oznacza to, że elementy muszą spełniać zarówno zapytanie słów kluczowych, jak i warunek, który ma zostać uwzględniony w wynikach. W ten sposób warunki ułatwiają zawężenie wyników.

- Jeśli dodasz do zapytania wyszukiwania co najmniej dwa unikatowe warunki (warunki określające różne właściwości), będą one logicznie połączone **operatorem** AND. Oznacza to, że zwracane są tylko te elementy, które spełniają wszystkie warunki (oprócz zapytania słów kluczowych).

- Jeśli dodasz więcej niż jeden warunek dla tej samej właściwości, te warunki będą logicznie połączone przez operator **LUB** . Oznacza to, że zostaną zwrócone elementy spełniające zapytanie słów kluczowych oraz jeden z warunków. Grupy o tych samych warunkach są ze sobą połączone przez operator **OR** , a następnie operator AND łączy ze sobą **zestawy** unikatowych warunków.

- Jeśli do jednego warunku dodasz wiele wartości (oddzielonych średnikami lub średnikami), te wartości zostaną połączone **operatorem LUB** . Oznacza to, że elementy są zwracane, jeśli zawierają dowolną z wartości określonej właściwości w warunku.

- Każdy warunek, który korzysta z operatora z  **logiką Zawiera** i Równa się, spowoduje zwrócenie podobnych wyników wyszukiwania dla prostych wyszukiwań ciągów. Proste wyszukiwanie ciągów to ciąg w warunku, który nie zawiera symbolu wieloznacznego). Na przykład warunek, **który używa równa** się dowolnej wartości, zwróci te same elementy, co warunek zawierający **dowolny z**.

- Zapytanie wyszukiwania utworzone za pomocą pola słów kluczowych i warunków jest wyświetlane na stronie Wyszukiwanie w okienku szczegółów dla wybranego wyszukiwania. W zapytaniu wszystko po prawej stronie notacji  `(c:c)` wskazuje warunki dodane do zapytania.

- Warunki dodają tylko właściwości do zapytania wyszukiwania. nie dodawaj operatorów. Dlatego zapytanie wyświetlane w okienku szczegółów  `(c:c)` nie wyświetla operatorów po prawej stronie notacji. Kod KQL dodaje operatory logiczne (zgodnie z wcześniej wyjaśnionymi regułami) podczas wykonywania zapytania.

- Możesz użyć kontrolki przeciągania i upuszczania, aby zmienić kolejność warunków. Kliknij kontrolkę dla warunku i przenieś go w górę lub w dół.

- Jak wyjaśniono wcześniej, niektóre właściwości warunków umożliwiają wpisanie wielu wartości (oddzielonych średnikami). Każda wartość jest logicznie połączona z operatorem **LUB** i powoduje wynik w zapytaniu `(filetype=docx) OR (filetype=pptx) OR (filetype=xlsx)`. Na poniższej ilustracji przedstawiono przykładowy warunek z wieloma wartościami.

    ![Jeden warunek z wieloma wartościami.](../media/SearchConditions1.png)

  > [!NOTE]
  > Nie można dodać wielu warunków (klikając pozycję **Dodaj warunek** dla tej samej właściwości. Zamiast tego należy podać wiele wartości warunku (oddzielonych średnikami), jak pokazano w poprzednim przykładzie.

### <a name="examples-of-using-conditions-in-search-queries"></a>Przykłady użycia warunków w kwerendach wyszukiwania

W poniższych przykładach przedstawiono wersję zapytania wyszukiwania opartą na interfejsie GUID z warunkami, składnię zapytania wyszukiwania wyświetlaną w okienku szczegółów wybranego wyszukiwania (zwróconą również przez polecenie cmdlet **Get-ComplianceSearch** ) oraz logikę odpowiadającego zapytania KQL.

#### <a name="example-1"></a>Przykład 1

W tym przykładzie są zwracane dokumenty SharePoint witrynach OneDrive dla Firm zawierających numer karty kredytowej, które zostały ostatnio zmodyfikowane przed 1 stycznia 2021 r.

**GRAFICZNE INTERFEJS UŻYTKOWNIKA**:

![Pierwszy przykład warunków wyszukiwania.](../media/SearchConditions2.png)

**Składnia zapytania wyszukiwania**:

`SensitiveType:"Credit Card Number"(c:c)(lastmodifiedtime<2021-01-01)`

**Logika zapytania wyszukiwania**:

`SensitiveType:"Credit Card Number" AND (lastmodifiedtime<2021-01-01)`

Zauważ na poprzednim zrzucie ekranu, że interfejs użytkownika wyszukiwania potwierdza, że zapytanie słów kluczowych i warunek są połączone przez operator **AND** .

#### <a name="example-2"></a>Przykład 2

W tym przykładzie są zwracane elementy lub dokumenty poczty e-mail zawierające słowo kluczowe "raport", które zostało wysłane lub utworzone przed 1 kwietnia 2021 r. i które zawierają wyraz "northwind" w polu tematu wiadomości e-mail lub we właściwości tytułu dokumentów. Kwerenda wyklucza strony sieci Web, które spełniają inne kryteria wyszukiwania.

**GRAFICZNE INTERFEJS UŻYTKOWNIKA**:

![Drugi przykład warunków wyszukiwania.](../media/SearchConditions3.png)

**Składnia zapytania wyszukiwania**:

`report(c:c)(date<2021-04-01)(subjecttitle:"northwind")(-filetype:aspx)`

**Logika zapytania wyszukiwania**:

`report AND (date<2021-04-01) AND (subjecttitle:"northwind") NOT (filetype:aspx)`

#### <a name="example-3"></a>Przykład 3

W tym przykładzie są zwracane wiadomości e-mail lub spotkania w kalendarzu, które zostały wysłane między 1 grudnia 2019 r. a 30 listopada 2020 r. i które zawierają wyrazy, które zaczynają się od słów "telefon" lub "smartfon".

**GRAFICZNE INTERFEJS UŻYTKOWNIKA**:

![Trzeci przykład warunków wyszukiwania.](../media/SearchConditions4.png)

**Składnia zapytania wyszukiwania**:

`phone* OR smartphone*(c:c)(sent=2019-12-01..2020-11-30)(kind="email")(kind="meetings")`

**Logika zapytania wyszukiwania**:

`phone* OR smartphone* AND (sent=2019-12-01..2020-11-30) AND ((kind="email") OR (kind="meetings"))`

## <a name="special-characters"></a>Znaki specjalne

Niektóre znaki specjalne nie są uwzględniane w indeksie wyszukiwania i dlatego nie można ich przeszukiwać. Obejmuje to również znaki specjalne reprezentujące operatory wyszukiwania w zapytaniu wyszukiwania. Oto lista znaków specjalnych, które zostały zastąpione przez puste miejsce w rzeczywistym zapytaniu wyszukiwania lub powodują błąd wyszukiwania.

`+ - = : ! @ # % ^ & ; _ / ? ( ) [ ] { }`

## <a name="searching-for-site-content-shared-with-external-users"></a>Wyszukiwanie zawartości witryny udostępnianej użytkownikom zewnętrznym

Za pomocą narzędzi wyszukiwania zbierania elektronicznych materiałów dowodowych w Centrum zgodności można również wyszukiwać dokumenty przechowywane w witrynach SharePoint i OneDrive dla Firm, które zostały udostępnione osobom spoza organizacji. Może to ułatwić identyfikowanie poufnych lub zastrzeżonych informacji udostępnianych poza twoją organizacją. Możesz to zrobić za pomocą właściwości w  `ViewableByExternalUsers` zapytaniu słowa kluczowego. Ta właściwość zwraca dokumenty lub witryny udostępnione użytkownikom zewnętrznym przy użyciu jednej z następujących metod udostępniania:

- Zaproszenie do udostępniania wymagające, aby użytkownicy logowali się do organizacji jako uwierzytelniony użytkownik.
- Anonimowy link gościa, który pozwala każdemu użytkownikowi mającemu ten link na uzyskiwanie dostępu do zasobu bez konieczności uwierzytelnienia.

Oto kilka przykładów:

- Zapytanie zwraca  `ViewableByExternalUsers:true AND SensitiveType:"Credit Card Number"` wszystkie elementy, które zostały udostępnione osobom spoza organizacji i zawierają numer karty kredytowej.
- Zapytanie zwróci  `ViewableByExternalUsers:true AND ContentType:document AND site:"https://contoso.sharepoint.com/Sites/Teams"` listę dokumentów udostępnionych użytkownikom zewnętrznym we wszystkich witrynach zespołu w organizacji.

> [!TIP]
> Kwerenda wyszukiwania, taka  `ViewableByExternalUsers:true AND ContentType:document` jak może zwracać wiele plików aspx w wynikach wyszukiwania. Aby wyeliminować te (lub inne typy plików), możesz  `FileExtension` użyć tej właściwości, aby wykluczyć określone typy plików, na przykład  `ViewableByExternalUsers:true AND ContentType:document NOT FileExtension:aspx`.

Co jest uważane za zawartość udostępnianą osobom spoza organizacji? Dokumenty w witrynach SharePoint i OneDrive dla Firm organizacji są udostępniane za pomocą zaproszenia do udostępniania lub udostępnionego w lokalizacjach publicznych. Na przykład następujące działania użytkownika wpływają na zawartość, która będzie przeglądana przez użytkowników zewnętrznych:

- Użytkownik udostępnia plik lub folder osobie spoza Twojej organizacji.
- Użytkownik tworzy plik udostępniony i wysyła link do pliku udostępnionego osobie spoza organizacji. Ten link umożliwia użytkownikowi zewnętrznemu wyświetlanie (lub edytowanie) pliku.
- Użytkownik wysyła zaproszenie do udostępniania lub link gościa do osoby spoza organizacji w celu wyświetlenia (lub edytowania) udostępnionego pliku.

### <a name="issues-using-the-viewablebyexternalusers-property"></a>Problemy z używaniem właściwości ViewableByExternalUsers

Mimo że właściwość  `ViewableByExternalUsers` określa stan, czy dokument lub witryna jest udostępniana użytkownikom zewnętrznym, istnieją pewne zastrzeżenia co do działania tej właściwości i jej nie odzwierciedla. W poniższych scenariuszach  `ViewableByExternalUsers` wartość właściwości nie zostanie zaktualizowana, a wyniki zapytania wyszukiwania, które używa tej właściwości, mogą być niedokładne.

- Zmiany zasad udostępniania, na przykład wyłączenie udostępniania zewnętrznego witryny lub organizacji. Mimo odwołania dostępu zewnętrznego we właściwości nadal będą wyświetlane wcześniej udostępnione dokumenty jako dostępne zewnętrznie.
- Zmiany członkostwa w grupach, na przykład dodanie lub usunięcie użytkowników zewnętrznych do grup Microsoft 365 lub Microsoft 365 zabezpieczeń. Właściwość nie będzie automatycznie aktualizowana dla elementów, do których grupa ma dostęp.
- Wysyłanie zaproszeń do udostępniania użytkownikom zewnętrznym, którzy nie zaakceptowali zaproszenia i dlatego nie ma jeszcze dostępu do zawartości.

W takich scenariuszach właściwość  `ViewableByExternalUsers` nie będzie odzwierciedlać bieżącego stanu udostępniania, dopóki witryna lub biblioteka dokumentów nie zostanie ponownie przekierowyowana i ponownie zindeksowana.

## <a name="searching-for-site-content-shared-within-your-organization"></a>Wyszukiwanie zawartości witryny udostępnionej w organizacji

Jak wyjaśniono wcześniej, można użyć tej  `SharedWithUsersOWSUser` właściwości w celu wyszukiwania dokumentów udostępnionych między osobami w organizacji. Gdy osoba udostępni plik (lub folder) inowi użytkownikowi w Twojej organizacji, OneDrive dla Firm na stronie Udostępnione dla mnie na koncie osoby, której  udostępniono plik, zostanie wyświetlony link do tego pliku. Na przykład do wyszukiwania dokumentów udostępnionych Dla Aedy Cieslisza możesz użyć tego zapytania  `SharedWithUsersOWSUser:"sarad@contoso.com"`. W przypadku eksportowania wyników tego wyszukiwania zostaną pobrane oryginalne dokumenty (znajdujące się w lokalizacji zawartości osoby, która udostępniła dokumenty Anie).

Dokumenty muszą być jawnie udostępniane określoneowi użytkownikowi, aby podczas korzystania z tej właściwości zwracane  `SharedWithUsersOWSUser` były wyniki wyszukiwania. Na przykład gdy osoba udostępnia dokument na swoim koncie usługi OneDrive, może udostępnić go każdej osobie (w organizacji lub poza nią), udostępnić go tylko osobom w organizacji lub udostępnić go konkretnej osobie. Oto zrzut ekranu przedstawiający okno Udostępnianie w  programie OneDrive, na których przedstawiono trzy opcje udostępniania.

![Tylko pliki udostępnione określonym osobom zostaną zwrócone przez zapytanie wyszukiwania, które używa właściwości SharedWithUsersOWSUser.](../media/469a4b61-68bd-4ab0-b612-ab6302973886.png)

Tylko dokumenty udostępnione przy użyciu trzeciej opcji (udostępnione określonym **osobom) zostaną** zwrócone przez zapytanie wyszukiwania używające tej  `SharedWithUsersOWSUser` właściwości.

## <a name="searching-for-skype-for-business-conversations"></a>Wyszukiwanie konwersacji Skype dla firm konwersacji

Poniższe zapytanie słów kluczowych umożliwia wyszukiwanie zawartości w konwersacjach Skype dla firm kluczowych:

```powershell
kind:im
```

Poprzednie zapytanie wyszukiwania zwraca również czaty z Microsoft Teams. Aby temu zapobiec, możesz zawęzić wyniki wyszukiwania, aby uwzględnić Skype dla firm konwersacji za pomocą następującego słowa kluczowego:

```powershell
kind:im AND subject:conversation
```

Poprzednie zapytanie słów kluczowych wyklucza czaty w programie Microsoft Teams ponieważ Skype dla firm konwersacje są zapisywane jako wiadomości e-mail z wierszem Temat, który zaczyna się od słowa "Konwersacja".

Aby wyszukać Skype dla firm, które wystąpiły w określonym przedziale dat, użyj następującego słowa kluczowego:

```powershell
kind:im AND subject:conversation AND (received=startdate..enddate)
```

## <a name="character-limits-for-searches"></a>Limity znaków dla wyszukiwań

Istnieje ograniczenie do 4000 znaków dla zapytań wyszukiwania podczas wyszukiwania zawartości w witrynach SharePoint i OneDrive kontach.
Łączną liczbę znaków w zapytaniu wyszukiwania oblicza się w ten sposób:

- Znaki w wyszukiwaniu słów kluczowych (w tym zarówno pola użytkownika, jak i pola filtru) są wliczane do tego limitu.
- Znaki we wszystkich właściwościach lokalizacji (takich jak adresy URL wszystkich SharePoint lub lokalizacji OneDrive są wliczane do tego limitu.
- Znaki we wszystkich filtrach uprawnień wyszukiwania, które są stosowane do użytkownika uruchamiacego wyszukiwanie, są liczone względem limitu.

Aby uzyskać więcej informacji o limitach znaków, zobacz Limity wyszukiwania zbierania elektronicznych [materiałów dowodowych](limits-for-content-search.md#search-limits).

> [!NOTE]
> Limit 4000 znaków dotyczy wyszukiwania zawartości, podstawowych zbierania elektronicznych materiałów dowodowych i Advanced eDiscovery.

## <a name="search-tips-and-tricks"></a>Porady i wskazówki dotyczące wyszukiwania

- W wyszukiwaniach według słów kluczowych nie jest wróżniana wielkość liter. Na przykład kot **i** **KOT** zwracają te same wyniki.

- Operatory logiczne **ORAZ**, **LUB**, **NIE** i **NEAR** muszą być wielkie.

- Spacja między dwoma słowami kluczowymi lub dwoma wyrażeniami  `property:value` jest taka sama jak użycie funkcji **ORAZ**. Na przykład zwraca  `from:"Sara Davis" subject:reorganization` wszystkie wiadomości wysłane przez Ewa Ciesoma, które zawierają wyraz reorganizacja w wierszu tematu.

- Użyj składni, która jest taka, jak w przypadku `property:value` formatu. W wartościach nie jest rozróżniana wielkość liter i operator nie może używać spacji. Jeśli istnieje spacja, szukaną wartością będzie wyszukiwanie pełnoektowe. Na przykład `to: pilarp` wyszukuje słowo kluczowe "pilarp" zamiast wiadomości wysłanych do pilarp.

- Wyszukując właściwość adresata, taką jak Do, Od, DW lub Adresaci, można użyć adresu SMTP, aliasu lub nazwy wyświetlanej w celu określenia adresata. Można na przykład użyć funkcji pilarp@contoso.com, pilarp lub "Pilar Pinilla".

- Można używać tylko wyszukiwań prefiksów; na przykład **kot\**_ lub _* zestaw\**_. Wyszukiwania sufiksów (_*\*kot**), wyszukiwania infix (**ct\***) i wyszukiwania podrzędne (**\*\*** kot) nie są obsługiwane.

- Wyszukując właściwość, użyj znaków podwójnego cudzysłowu (" "), jeśli szukana wartość zawiera wiele wyrazów. Na przykład `subject:budget Q1` zwraca wiadomości **zawierające budżet w** wierszu tematu i zawierające **K1** w dowolnym miejscu wiadomości lub dowolnej właściwości wiadomości. Użycie `subject:"budget Q1"` zwraca wszystkie wiadomości, które zawierają **tekst budżet KW1** w dowolnym miejscu wiersza tematu.

- Aby wykluczyć z wyników wyszukiwania zawartość oznaczoną określoną wartością właściwości, przed nazwą właściwości umieść znak minus (-). Nie obejmuje na przykład `-from:"Sara Davis"` żadnych wiadomości wysłanych przez Ewa Ciesoma.

- Możesz eksportować elementy na podstawie typu wiadomości. Aby na przykład wyeksportować Skype konwersacje i czaty w programie Microsoft Teams, użyj składni `kind:im`. Aby zwrócić tylko wiadomości e-mail, użyj .`kind:email` Aby zwrócić czaty, spotkania i połączenia w aplikacji Microsoft Teams, użyj .`kind:microsoftteams`

- Jak już wyjaśniono, podczas `/` wyszukiwania w witrynach podczas wyszukiwania witryn musisz dodać końcówkę na końcu adresu URL `path` , gdy używasz tej właściwości do zwracania tylko elementów w określonej witrynie. Jeśli nie uwzględnisz ciągów `/`, zostaną zwrócone elementy z witryny o podobnej nazwie ścieżki. Jeśli na przykład użyjemy tych elementów `path:sites/HelloWorld` z witryn, `sites/HelloWorld_East` o których nazwa lub `sites/HelloWorld_West` które również zostaną zwrócone, zostaną zwrócone. Aby zwrócić elementy tylko z witryny HelloWorld, musisz użyć .`path:sites/HelloWorld/`
