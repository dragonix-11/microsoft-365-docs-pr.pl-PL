---
title: Informacje podstawowe o systemie DNS
f1.keywords:
- NOCSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: high
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- okr_smb
- AdminTemplateSet
- admindeeplinkMAC
search.appverid:
- MET150
- MOE150
- GEA150
- BSA160
ms.assetid: 854b6b2b-0255-4089-8019-b765cff70377
ROBOTS: NOINDEX
description: System nazw domen mapuje nazwy hostów komputerów na adresy IP, a znajomość podstaw systemu DNS i rejestratora domen może ułatwić zarządzanie domenami.
ms.openlocfilehash: efe5c8b4a043c3a8f4bdf49da85201ab0cbae7c9
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63317349"
---
# <a name="dns-basics"></a>Informacje podstawowe o systemie DNS

 **[Zajrzyj do często zadawanych pytań dotyczących domen](../setup/domains-faq.yml)**, jeśli nie możesz znaleźć szukanych informacji. 
  
::: moniker range="o365-worldwide"

Zarządzanie nazwami domen, takimi jak contoso.com, odbywa się przy użyciu globalnego systemu rejestratorów domen i baz danych. System nazw domen (DNS) zapewnia mapowanie między zrozumiałymi dla człowieka nazwami hosta i adresami IP komputerów używanymi przez urządzenia sieciowe. Znajomość podstawowych informacji o systemie DNS i rejestratorze domen może pomóc w zarządzaniu domenami.

## <a name="watch-domains--dns-an-overview"></a>Obejrzyj: Domeny i DNS: omówienie
  
> [!VIDEO https://www.microsoft.com/videoplayer/embed/c005f2a4-90ad-46fe-b1ab-90f41f2a9d53?autoplay=false]
  
::: moniker-end

::: moniker range="o365-21vianet"

Zarządzanie nazwami domen, takimi jak contoso.com, odbywa się przy użyciu globalnego systemu rejestratorów domen i baz danych. System nazw domen (DNS) zapewnia mapowanie między zrozumiałymi dla człowieka nazwami hosta i adresami IP komputerów używanymi przez urządzenia sieciowe. Zrozumienie podstaw systemu DNS i funkcjonowania rejestratorów domen ułatwi administratorom zarządzanie domenami.
  
::: moniker-end

## <a name="what-are-domain-names"></a>Co to są nazwy domen?

Nazwy domen są używane w adresach URL oraz e-mail i mają różne poziomy. Na przykład adres mail.contoso.com jest nazwą domeny z następującymi trzema poziomami:
  
- **.com** jest domeną najwyższego poziomu, 
    
- **contoso** jest domeną drugiego poziomu, 
    
- **mail** jest domeną trzeciego poziomu. 
    
Dlaczego warto używać domeny trzeciego poziomu? Czasami potrzebne są różne nazwy domen dla witryny o charakterze marketingowym lub dla bloga. Na przykład blog.contoso.com. W Microsoft zazwyczaj jest dodawana domena drugiego poziomu, na przykład contoso.com, ale można też używać domen trzeciego poziomu.
  
Aby dowiedzieć się więcej o tym, co można zrobić z domenami w ramach poszczególnych typów oferty, zapoznaj się z [opisem platform usług Microsoft 365 i Office 365](/office365/servicedescriptions/office-365-platform-service-description/domains).
  
## <a name="understand-dns-record-types"></a>Opis typów rekordów DNS

Rekordy DNS, przechowywane na hoście DNS, służą do kierowania ruchu dla domeny. W poniższej tabeli opisano często używane rekordy DNS oraz sposoby ich używania.
  
|**Rekord serwera nazw (NS)**|**Identyfikuje serwery nazw będące „autorytatywnymi serwerami nazw” dla określonej domeny. Zmiana tych serwerów powoduje zmianę lokalizacji zarządzania rekordami DNS oraz zmianę miejsca, w którym system DNS szuka informacji o serwerach poczty itp. Możesz używać serwerów nazw usługi Microsoft lub kontynuować korzystanie z serwerów wcześniej skonfigurowanych do współdziałania z Twoją domeną.**|
|:-----|:-----|
|Rekord (rekord adresu)  <br/> |Kojarzy nazwę domeny z adresem IP.  <br/> |
|Rekord CNAME (alias lub nazwa kanoniczna)  <br/> |Przekierowuje jedną domenę do innej domeny w systemie DNS. Gdy serwer nazw będzie szukać domeny i znajdzie jej rekord CNAME, zastąpi pierwszą nazwę domeny rekordem CNAME, a następnie poszuka nowej nazwy.  <br/> |
|Rekord MX (usługa wymiany poczty)  <br/> |Wskazuje, dokąd ma być wysyłana poczta e-mail. Zawiera także pole priorytetu umożliwiające wysyłanie poczty do różnych serwerów w ustalonej kolejności priorytetów.  <br/> |
|Rekord SPF (struktura zasad dotyczących nadawców)  <br/> |Rekord TXT, który ułatwia zapobieganie spoofingowi poczty e-mail i wyłudzaniu informacji.  <br/> |
|Rekord SRV (rekord usługi)  <br/> |Używane przez usługi Skype dla firm Online i Exchange Online do koordynowania przepływu informacji między usługami Microsoft. Rekordy SRV są na przykład wymagane do wyświetlania informacji o obecności w aplikacji Outlook Web App oraz do korzystania z usługi Skype dla firm Online, programu Skype lub innych narzędzi do wymiany wiadomości błyskawicznych z osobami w innych firmach.  <br/> |
|TTL (czas wygaśnięcia)  <br/> |Czas przechowywania rekordu DNS na serwerze nazw przed wyszukaniem zaktualizowanej wersji przez ten serwer.  <br/> |
   
## <a name="how-does-dns-work"></a>Jak działa system DNS?

Częścią procesu konfigurowania domeny w usłudze w chmurze, takiej jak Microsoft 365, jest zmiana lub dodanie [rekordów DNS](dns-basics.md) dla tej domeny. Te zmiany są wymagane z powodu sposobu współdziałania Internetu z systemem DNS (Domain Name System) i nazwami domen w celu lokalizowania odpowiednich miejsc do wysyłania i znajdowania elementów, takich jak wiadomości e-mail i witryny internetowe. 
  
Internet jest skonfigurowany pod kątem używania systemu DNS, czyli systemu nazw domen, który umożliwia stosowanie znajomych nazw, takich jak contoso.com, w celu lokalizowania określonych miejsc w Internecie, które są w rzeczywistości oznaczone trudnymi do zapamiętania numerami nazywanymi adresami IP (Internet Protocol). Adresy IP wyglądają mniej więcej tak: 70.42.241.42. Widać zatem, że o wiele łatwiej jest określać lokalizacje, takie jak hosty poczty e-mail i witryny internetowe, za pomocą nazw domen.
  
Mówiąc krótko: rekordy DNS wskazują, gdzie w Internecie należy wysyłać wiadomości e-mail (np. zaadresowane do jacek@contoso.com) i szukać witryn internetowych (np. www.contoso.com) używających Twojej nazwy domeny. Gdy umieścisz odpowiednie informacje w odpowiednich rekordach DNS dla swojej domeny, system DNS będzie wszystkim poprawnie kierował, aby na przykład Twoje wiadomości e-mail trafiały do usługi Microsoft 365, a nie gdzieś indziej.
  
Rekordy DNS domeny mogą być także pomocne w inny sposób. Na przykład program Exchange sprawdza rekord DNS, który umożliwia programowi Outlook automatyczne konfigurowanie połączenia z odpowiednim serwerem Exchange.
  
### <a name="dns-records-help-the-internet-send-email-to-the-right-place"></a>Rekordy DNS pomagają sieci Internet wysyłać wiadomości e-mail do właściwych miejsc

Jak wyjaśniono powyżej, system DNS zasadniczo kieruje ruchem w Internecie, mapując przyjazne nazwy domen na trudne do zapamiętania adresy IP. Jeden rekord DNS, nazywany rekordem MX, służy do wysyłania wiadomości e-mail do odpowiedniego hosta.
  
Rekordy DNS są jak bazy danych z informacjami o Twojej domenie. Rekordy i ich wartości są przechowywane w tak zwanym pliku strefy, który zawiera listę wszystkich rekordów dla Twojej domeny i ich wartości. Rejestratorzy domen i inne firmy zajmujące się hostingiem DNS oferują w swoich witrynach internetowych interfejs użytkownika, który umożliwia edytowanie rekordów w pliku strefy danej domeny. Tam właśnie możesz zaktualizować rekord MX dla swojej domeny, aby wiadomości e-mail były wysyłane do usługi Microsoft 365.
  
 *Gdy w następnym kroku zmienisz adres e-mail na usługę Microsoft 365 przez zaktualizowanie rekordu MX domeny, WSZYSTKIE wiadomości e-mail wysyłane do tej domeny zaczną docierać do usługi Microsoft 365.*  Jeśli inne osoby używają Twojej domeny do obsługi poczty e-mail, należy skonfigurować skrzynki pocztowe usługi Microsoft 365 dla wszystkich tych osób. 
  
Brzmi skomplikowanie? Nie martw się, przeprowadzimy Cię przez każdy krok konfigurowania domeny w usłudze Microsoft.
  
### <a name="dns-tells-the-internet-where-to-look-for-websites-too"></a>System DNS wskazuje sieci Internet, gdzie szukać witryn internetowych

Gdy wpisujesz adres witryny internetowej, na przykład www.contoso.com, Internet najpierw szuka na jednym z serwerów DNS tak zwanego rekordu serwera nazw (NS) dla (w tym przypadku) domeny contoso.com. Rekord serwera nazw wskazuje sieci Internet, gdzie należy szukać pliku strefy zawierającego wszystkie pozostałe wartości rekordu DNS dla tej domeny. Istnieje wiele serwerów DNS i wszystkie są ze sobą połączone. Serwery współpracują ze sobą, aby śledzić wszystkie zarejestrowane nazwy domen, które muszą być unikatowe, i miejsca przechowywania plików stref domen.
  
::: moniker range="o365-worldwide"

Załóżmy, że rekord serwera nazw dla domeny contoso.com wskazuje nazwę „godaddy.com”. Teraz Internet wie, że w witrynie GoDaddy.com należy szukać pliku strefy zawierającego listę wszystkich pozostałych rekordów DNS dla domeny contoso.com. Te rekordy DNS zawierają rekord MX, który mówi, gdzie mają być wysyłane wiadomości e-mail dla domeny contoso.com, a także inne rekordy. Jeśli rekord MX ma wartość, która mówi (w języku technicznym) „wyślij wiadomość e-mail do usługi Microsoft 365”, tam właśnie będą kierowane wszystkie wiadomości e-mail wysyłane na adres contoso.com (np. jacek@contoso.com). Następnie, jeśli tylko w tej lokalizacji znajduje się skrzynka pocztowa o nazwie „jacek”, wiadomość e-mail zostanie dostarczona.

::: moniker-end

::: moniker range="o365-21vianet"

Załóżmy, że rekord serwera nazw dla domeny contoso.com wskazuje nazwę „hichina.com”. Teraz Internet wie, że w witrynie hichina.com należy szukać pliku strefy zawierającego listę wszystkich pozostałych rekordów DNS dla domeny contoso.com. Te rekordy DNS zawierają rekord MX, który mówi, gdzie mają być wysyłane wiadomości e-mail dla domeny contoso.com, a także inne rekordy. Jeśli rekord MX ma wartość, która mówi (w języku technicznym) „wyślij wiadomość e-mail do usługi Microsoft 365”, tam właśnie będą kierowane wszystkie wiadomości e-mail wysyłane na adres contoso.com (np. jacek@contoso.com). Następnie, jeśli tylko w tej lokalizacji znajduje się skrzynka pocztowa o nazwie „jacek”, wiadomość e-mail zostanie dostarczona.

::: moniker-end

Rzeczywiste wartości, które musisz wprowadzić, aby to wszystko działało z usługą Microsoft 365, są podawane podczas konfigurowania domeny, w procedurze konfigurowania domeny. Jeśli przeprowadzasz konfigurację ręcznie, kopiujesz i wklejasz odpowiednie wartości do właściwych rekordów DNS (rekord MX, rekordy CNAME i tak dalej) na swoim hoście DNS, który może być rejestratorem Twojej domeny, ale nie musi.
  
::: moniker range="o365-worldwide"

Dlaczego plik strefy domeny może znajdować się w innym miejscu poza rejestratorem domen? Możesz zarejestrować swoją nazwę domeny u rejestratora domen, takiego jak GoDaddy, ale Twoje rekordy DNS mogą być zarządzane gdzie indziej, w osobnej firmie zajmującej się hostingiem DNS lub hostingiem internetowym. Rekordy serwerów nazw dla Twojej domeny przechowują tę informację, aby wszystkie serwery DNS wiedziały, gdzie szukać.

::: moniker-end

::: moniker range="o365-21vianet"

Dlaczego plik strefy domeny może znajdować się w innym miejscu poza rejestratorem domen? Możesz zarejestrować swoją nazwę domeny u rejestratora domen, takiego jak HiChina, ale Twoje rekordy DNS mogą być zarządzane gdzie indziej, w osobnej firmie zajmującej się hostingiem DNS lub hostingiem internetowym. Rekordy serwerów nazw dla Twojej domeny przechowują tę informację, aby wszystkie serwery DNS wiedziały, gdzie szukać.

::: moniker-end

::: moniker range="o365-worldwide"
## <a name="why-add-a-domain-in-microsoft-365"></a>Dlaczego warto dodać domenę na platformie Microsoft 365?


Dodanie domeny niestandardowej, na przykład fourthcoffee.com, do usługi Microsoft 365 umożliwia korzystanie z krótszych i przyjaźniejszych adresów e-mail oraz z identyfikatora użytkownika w usłudze. Po utworzeniu konta usługi Microsoft 365 masz [do dyspozycji domenę do użycia](../setup/domains-faq.yml), ale znajduje się ona w domenie „onmicrosoft.com”. Wiele osób woli dodać domenę swojej organizacji lub firmy, jeśli zamierza używać usługi Microsoft 365 do obsługi poczty e-mail. 
  
> [!NOTE]
> Jeśli chcesz tylko pobrać aplikacje Microsoft, takie jak programy Outlook i Word, oraz używać ich, nie musisz dodawać domeny: [zainstaluj pakiet Office na komputerze PC lub Mac](https://support.microsoft.com/office/4414eaaf-0478-48be-9c42-23adc4716658). 
  
Nazwy domeny w usłudze Microsoft 365 można używać w adresie e-mail, adresie publicznej witryny internetowej i adresie wiadomości błyskawicznych.
  
- **Adres e-mail.** Nazwa domeny umożliwia dostosowanie adresu e-mail, dzięki czemu można używać krótszego, łatwiejszego do zapamiętania adresu, niż [początkowy adres e-mail w domenie onmicrosoft.com](../setup/domains-faq.yml) dostarczony z Twoim kontem. Zamiast adresu jacek@contoso.onmicrosoft.com, adres e-mail (będący również kontem firmowym używanym do logowania się do usługi Microsoft 365) może mieć postać jacek@contoso.com. 
    
- **Witryna internetowa.** Jeśli masz subskrypcję usługi Microsoft 365 obejmującą publiczną witrynę internetową usługi SharePoint Online (została ona już wycofana ze sprzedaży), ma ona adres początkowy typu: contoso-public.sharepoint.com. Jeśli konfigurujesz witrynę internetową dla swojej firmy, możesz zmienić adres tej witryny za pomocą niestandardowej nazwy domeny na adres typu www.contoso.com. 
    
- **Wiadomości błyskawiczne.** Adres usługi Skype dla firm Online również można dostosować do korzystania z Twojej nazwy domeny, dzięki czemu osoby w Twojej organizacji będą mogły kontaktować się ze sobą w usłudze Skype dla firm Online przy użyciu krótszego, łatwiejszego do zapamiętania adresu (takiego jak jacek@contoso.com). 
    
::: moniker-end

## <a name="the-dns-records-required-for-microsoft-365"></a>Rekordy DNS wymagane dla usługi Microsoft 365

Istnieje szereg rekordów DNS wymaganych do współdziałania usługi Microsoft 365 z Twoją domeną. Oprócz rekordu MX domeny, konfigurowanego w celu wysyłania wiadomości e-mail do usługi Microsoft 365, istnieją rekordy ułatwiające zadania, takie jak upewnianie się, że program Outlook może automatycznie łączyć się z właściwym serwerem programu Exchange, konfigurowanie wiadomości błyskawicznych i zabezpieczanie przed wiadomościami-śmieciami w poczcie e-mail.
  
Możesz [znaleźć listę wartości](information-for-dns-records.md) potrzebnych do skonfigurowania domeny. Znajdują się one bezpośrednio w <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">centrum administracyjnym platformy Microsoft 365</a>. 
  
Ewentualnie, jeśli planujesz wdrożenie, warto przejrzeć listę wszystkich rekordów DNS wymaganych przez usługę Microsoft 365, poznać ich funkcje i przykładowe wartości. Zapoznaj się [rekordami systemu nazw domen zewnętrznych dla platformy Microsoft 365](../../enterprise/external-domain-name-system-records.md).
  
## <a name="next-steps"></a>Następne kroki

Zapoznaj się z następującymi zasobami: 
  
- Nie masz pewności, gdzie jest zarejestrowana Twoja domena? [Uzyskaj pomoc dotyczącą znajdowania rejestratora domen](find-your-domain-registrar.md).
- Dowiedz się, [dlaczego musisz wykonać kroki kreatora](../setup/add-domain.md), zanim będzie można używać własnej domeny z usługą Microsoft 365.

## <a name="related-content"></a>Zawartość pokrewna

[Często zadawane pytania dotyczące domen](../setup/domains-faq.yml)  (artykuł)\
[Znajdowanie i rozwiązywanie problemów po dodaniu swojej domeny lub rekordów DNS](find-and-fix-issues.md) (artykuł)\
[Zarządzanie domenami](/admin) (strona linku)