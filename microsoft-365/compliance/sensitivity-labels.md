---
title: Dowiedz się więcej o etykietach poufności
f1.keywords:
- CSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- SPO_Content
- m365solution-mip
- m365initiative-compliance
search.appverid:
- MOE150
- MET150
description: Używanie etykiet poufności z usługi Microsoft Purview Information Protection do klasyfikowania i ochrony poufnej zawartości.
ms.custom:
- seo-marvel-apr2020
- seo-marvel-jun2020
ms.openlocfilehash: 088e84c492fe142471799139743f29be32513206
ms.sourcegitcommit: 5c64002236561000c5bd63c71423e8099e803c2d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/09/2022
ms.locfileid: "65287205"
---
# <a name="learn-about-sensitivity-labels"></a>Dowiedz się więcej o etykietach poufności

>*[Microsoft 365 wskazówki dotyczące licencjonowania dotyczące zgodności & zabezpieczeń](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

> [!NOTE]
> Jeśli szukasz informacji o etykietach poufności widocznych w aplikacjach Office, zobacz [Stosowanie etykiet poufności do plików i wiadomości e-mail w Office](https://support.microsoft.com/topic/apply-sensitivity-labels-to-your-files-and-email-in-office-2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9).
>
> Informacje na tej stronie są przeznaczone dla administratorów IT, którzy mogą tworzyć i konfigurować te etykiety.

Aby wykonać swoją pracę, osoby w organizacji współpracują z innymi osobami zarówno w organizacji, jak i poza nią. Oznacza to, że zawartość nie pozostaje już za zaporą — może poruszać się wszędzie, na urządzeniach, w aplikacjach i usługach. A gdy będzie się poruszać, chcesz, aby odbywało się to w bezpieczny, chroniony sposób, który spełnia zasady biznesowe i zgodności organizacji.

Etykiety poufności z usługi Microsoft Purview Information Protection umożliwiają klasyfikowanie i ochronę danych organizacji, jednocześnie upewniając się, że produktywność użytkowników i możliwość współpracy nie są utrudnione.

Przykład przedstawiający dostępne etykiety poufności w Excel na karcie **Narzędzia** główne na wstążce. W tym przykładzie zastosowana etykieta jest wyświetlana na pasku stanu:

![Etykieta poufności na wstążce Excel i pasku stanu.](../media/Sensitivity-label-in-Excel.png)

Aby zastosować etykiety poufności, użytkownicy muszą zalogować się przy użyciu Microsoft 365 konta służbowego.

> [!NOTE]
> W przypadku dzierżaw instytucji rządowych USA etykiety poufności są obsługiwane dla wszystkich platform.
>
> Jeśli używasz klienta i skanera ujednoliconego etykietowania usługi Azure Information Protection, zobacz [Opis usługi Azure Information Protection Premium Government.](/enterprise-mobility-security/solutions/ems-aip-premium-govt-service-description)

Etykiet poufności można użyć do:
  
- **Podaj ustawienia ochrony, które obejmują szyfrowanie i oznaczenia zawartości.** Na przykład zastosuj etykietę "Poufne" do dokumentu lub wiadomości e-mail, a etykieta szyfruje zawartość i stosuje znak wodny "Poufne". Oznaczenia zawartości obejmują nagłówki i stopki, a także znaki wodne, a szyfrowanie może również ograniczyć akcje, które autoryzowane osoby mogą podjąć w oparciu o zawartość.

- **Ochrony zawartości w aplikacjach pakietu Office na różnych platformach i urządzeniach.** Obsługiwane przez program Word, Excel, PowerPoint i Outlook w aplikacjach klasycznych Office i Office w sieci Web. Obsługiwane w systemach Windows, macOS, iOS i Android.

- **Ochrona zawartości w aplikacjach i usługach innych firm** przy użyciu Microsoft Defender for Cloud Apps. Dzięki Defender dla Chmury Apps można wykrywać, klasyfikować, oznaczać etykietami i chronić zawartość w aplikacjach i usługach innych firm, takich jak SalesForce, Box lub DropBox, nawet jeśli aplikacja lub usługa innej firmy nie odczytuje ani nie obsługuje etykiet poufności.

- **Chroń kontenery**, które obejmują witryny Teams, Grupy Microsoft 365 i SharePoint. Na przykład ustaw ustawienia prywatności, dostęp użytkowników zewnętrznych i udostępnianie zewnętrzne oraz dostęp z urządzeń niezarządzanych.

- **Rozszerzanie etykiet poufności na Power BI**: po włączeniu tej funkcji można stosować i wyświetlać etykiety w Power BI oraz chronić dane, gdy zostaną zapisane poza usługą.

- **Rozszerzanie etykiet poufności na zasoby w usłudze Microsoft Purview Data Map**: po włączeniu tej funkcji obecnie w wersji zapoznawczej można zastosować etykiety poufności do plików i schematyzowanych zasobów danych w usłudze Microsoft Purview Data Map. Schematyzowane zasoby danych obejmują SQL, Azure SQL, Azure Synapse, azure Cosmos i usług AWS RDS.

- **Rozszerzenia etykiet poufności na aplikacje i usługi innych firm.** Korzystając z zestawu Microsoft Information Protection SDK, aplikacje innych firm mogą odczytywać etykiety poufności i stosować ustawienia ochrony.

- **Klasyfikacji zawartości bez używania jakichkolwiek ustawień ochrony.** Możesz również po prostu przypisać etykietę w wyniku sklasyfikowania zawartości. Zapewnia to użytkownikom wizualne mapowanie klasyfikacji na nazwy etykiet organizacji i może używać etykiet do generowania raportów użycia i wyświetlanie danych aktywności dla poufnej zawartości. Na podstawie tych informacji zawsze można później zastosować ustawienia ochrony.

We wszystkich tych przypadkach etykiety poufności w Microsoft 365 mogą pomóc w podjęciu odpowiednich akcji w odpowiedniej zawartości. Etykiety poufności umożliwiają klasyfikowanie danych w całej organizacji i wymuszanie ustawień ochrony na podstawie tej klasyfikacji.

Aby uzyskać więcej informacji na temat tych i innych scenariuszy obsługiwanych przez etykiety poufności, zobacz [Typowe scenariusze dotyczące etykiet poufności](get-started-with-sensitivity-labels.md#common-scenarios-for-sensitivity-labels). Nowe funkcje są opracowywane przez cały czas, które obsługują etykiety poufności, więc warto również odwołać się do [planu Microsoft 365](https://aka.ms/MIPC/Roadmap).

## <a name="what-a-sensitivity-label-is"></a>Czym jest etykieta poufności

Po przypisaniu etykiety poufności do zawartości jest ona podobna do sygnatury, która jest stosowana i jest następująca:

- **Konfigurowalny.** Specyficzne dla Twojej organizacji i potrzeb biznesowych możesz tworzyć kategorie dla różnych poziomów poufnej zawartości w organizacji. Na przykład osobiste, publiczne, ogólne, poufne i wysoce poufne.

- **Wyczyść tekst.** Ponieważ etykieta jest przechowywana w czystym tekście w metadanych dla plików i wiadomości e-mail, aplikacje i usługi innych firm mogą ją odczytać, a następnie zastosować własne akcje ochronne, jeśli jest to wymagane.

- **Trwałe.** Ponieważ etykieta jest przechowywana w metadanych plików i wiadomości e-mail, etykieta jest przenoszona z zawartością, niezależnie od tego, gdzie jest zapisywana lub przechowywana. Unikatowa identyfikacja etykiet staje się podstawą do stosowania i wymuszania skonfigurowanych zasad.

W przypadku wyświetlania przez użytkowników etykieta poufności jest wyświetlana jak tag w aplikacjach, których używają, i można ją łatwo zintegrować z istniejącymi przepływami pracy.

Każdy element, który obsługuje etykiety poufności, może mieć zastosowaną pojedynczą etykietę poufności. Dokumenty i wiadomości e-mail mogą mieć zarówno etykietę poufności, jak i [etykietę przechowywania](retention.md#retention-labels) .

> [!div class="mx-imgBorder"]
> ![Etykieta poufności zastosowana do wiadomości e-mail.](../media/Sensitivity-label-on-email.png)

## <a name="what-sensitivity-labels-can-do"></a>Co mogą zrobić etykiety poufności

Po zastosowaniu etykiety poufności do wiadomości e-mail lub dokumentu wszystkie skonfigurowane ustawienia ochrony dla tej etykiety są wymuszane dla zawartości. Etykietę poufności można skonfigurować tak, aby:

- **Szyfruj** wiadomości e-mail i dokumenty, aby uniemożliwić nieautoryzowanym osobom dostęp do tych danych. Możesz również wybrać, którzy użytkownicy lub grupa mają uprawnienia do wykonywania jakich akcji i jak długo. Możesz na przykład zezwolić wszystkim użytkownikom w organizacji na modyfikowanie dokumentu, podczas gdy określona grupa w innej organizacji może go wyświetlać tylko. Alternatywnie, zamiast uprawnień zdefiniowanych przez administratora, możesz zezwolić użytkownikom na przypisywanie uprawnień do zawartości, gdy zastosują etykietę. 
    
    Aby uzyskać więcej informacji na temat ustawień **szyfrowania** podczas tworzenia lub edytowania etykiety poufności, zobacz [Ograniczanie dostępu do zawartości przy użyciu szyfrowania w etykietach poufności](encryption-sensitivity-labels.md).

- **Oznacz zawartość** podczas korzystania z aplikacji Office, dodając znaki wodne, nagłówki lub stopki do wiadomości e-mail lub dokumentów z zastosowanymi etykietami. Znaki wodne można stosować do dokumentów, ale nie do wiadomości e-mail. Przykładowy nagłówek i znak wodny:
    
    ![Znak wodny i nagłówek zastosowany do dokumentu.](../media/Sensitivity-label-watermark-header.png)
    
    Oznaczenia dynamiczne są również obsługiwane przy użyciu zmiennych. Na przykład wstaw nazwę etykiety lub nazwę dokumentu do nagłówka, stopki lub znaku wodnego. Aby uzyskać więcej informacji, zobacz [Dynamiczne oznaczenia ze zmiennymi](sensitivity-labels-office-apps.md#dynamic-markings-with-variables).
    
    Czy należy sprawdzić, kiedy są stosowane oznaczenia zawartości? Zobacz [Kiedy aplikacje Office stosują znakowanie i szyfrowanie zawartości](sensitivity-labels-office-apps.md#when-office-apps-apply-content-marking-and-encryption).
    
    Jeśli masz szablony lub przepływy pracy oparte na określonych dokumentach, przetestuj te dokumenty przy użyciu wybranych oznaczeń zawartości, zanim udostępnisz etykietę użytkownikom. Niektóre ograniczenia długości ciągów, o których należy pamiętać:
    
    Znaki wodne są ograniczone do 255 znaków. Nagłówki i stopki są ograniczone do 1024 znaków, z wyjątkiem Excel. Excel ma łączny limit 255 znaków dla nagłówków i stopek, ale ten limit obejmuje znaki, które nie są widoczne, takie jak kody formatowania. Jeśli ten limit zostanie osiągnięty, wprowadzony ciąg nie będzie wyświetlany w Excel.

- **Ochrona zawartości w kontenerach, takich jak witryny i grupy**, po włączeniu możliwości [używania etykiet poufności z Microsoft Teams, grupami Microsoft 365 i witrynami SharePoint](sensitivity-labels-teams-groups-sites.md).
    
    Nie można skonfigurować ustawień ochrony dla grup i witryn, dopóki nie włączysz tej możliwości. Ta konfiguracja etykiet nie powoduje automatycznego etykietowania dokumentów ani wiadomości e-mail, ale zamiast tego ustawienia etykiet chronią zawartość, kontrolując dostęp do kontenera, w którym można przechowywać zawartość. Te ustawienia obejmują ustawienia prywatności, dostęp użytkowników zewnętrznych i udostępnianie zewnętrzne oraz dostęp z urządzeń niezarządzanych.

- **Zastosuj etykietę automatycznie do plików i wiadomości e-mail lub zarekomenduj etykietę.** Wybierz sposób identyfikowania informacji poufnych, które mają być oznaczone etykietą, a etykieta może być stosowana automatycznie lub możesz monitować użytkowników o zastosowanie zalecanej etykiety. Jeśli zalecasz etykietę, w wierszu polecenia zostanie wyświetlony dowolny wybrany tekst. Przykład:
    
    ![Monituj o przypisanie wymaganej etykiety.](../media/Sensitivity-label-Prompt-for-required-label.png)
    
    Aby uzyskać więcej informacji na temat automatycznego **etykietowania plików i ustawień wiadomości e-mail** podczas tworzenia lub edytowania etykiety poufności, zobacz [Automatyczne stosowanie etykiet poufności do zawartości](apply-sensitivity-label-automatically.md) w przypadku aplikacji Office i [Etykietowanie w usłudze Microsoft Purview Data Map](/azure/purview/create-sensitivity-label).

- **Ustaw domyślny typ łącza udostępniania** dla witryn SharePoint i poszczególnych dokumentów. Aby zapobiec nadmiernemu udostępnianiu przez użytkowników, ustaw [domyślny zakres i uprawnienia](sensitivity-labels-default-sharing-link.md), gdy użytkownicy udostępniają dokumenty z SharePoint i OneDrive.

### <a name="label-scopes"></a>Zakresy etykiet

Podczas tworzenia etykiety poufności zostanie wyświetlony monit o skonfigurowanie zakresu etykiety, który określa dwie rzeczy:
- Jakie ustawienia etykiet można skonfigurować dla tej etykiety
- Gdzie etykieta będzie widoczna dla użytkowników

Ta konfiguracja zakresu umożliwia posiadanie etykiet poufności, które są przeznaczone tylko dla dokumentów i wiadomości e-mail i nie mogą być wybierane dla kontenerów. Podobnie etykiety poufności, które są przeznaczone tylko dla kontenerów i nie mogą być wybierane dla dokumentów i wiadomości e-mail. Możesz również wybrać zakres zasobów usługi Microsoft Purview Data Map:

![Opcje zakresu etykiet poufności.](../media/sensitivity-labels-scopes.png)

Domyślnie zawsze jest zaznaczony zakres **Pliki & wiadomości e-mail** . Inne zakresy są wybierane domyślnie, gdy funkcje są włączone dla dzierżawy:

- **Grupy & lokacje**: [Włączanie etykiet poufności dla kontenerów i synchronizowanie etykiet](sensitivity-labels-teams-groups-sites.md#how-to-enable-sensitivity-labels-for-containers-and-synchronize-labels)

- **Schematyzowane zasoby danych**: [automatyczne etykietowanie zawartości w usłudze Microsoft Purview Data Map](/azure/purview/create-sensitivity-label)

Jeśli zmienisz wartości domyślne, aby nie wszystkie zakresy były zaznaczone, zostanie wyświetlona pierwsza strona ustawień konfiguracji dla zakresów, które nie zostały wybrane, ale nie można skonfigurować ustawień. Jeśli na przykład nie wybrano zakresu plików i wiadomości e-mail, nie można wybrać opcji na następnej stronie:

![Opcje niedostępne dla etykiet poufności.](../media/sensitivity-labels-unavailable-settings.png)

Dla tych stron, które mają niedostępne opcje, wybierz pozycję **Dalej** , aby kontynuować. Możesz też wybrać pozycję **Wstecz** , aby zmienić zakres etykiety.

### <a name="label-priority-order-matters"></a>Priorytet etykiety (kwestie dotyczące kolejności)

Podczas tworzenia etykiet poufności w centrum administracyjnym są one wyświetlane na liście na karcie **Czułość** na stronie **Etykiety** . Na tej liście kolejność etykiet jest ważna, ponieważ odzwierciedla ich priorytet. Chcesz, aby najbardziej restrykcyjna etykieta poufności, taka jak Wysoce poufna, była wyświetlana u **dołu** listy, a najmniej restrykcyjna etykieta poufności, taka jak Publiczna, była wyświetlana u **góry**.

Do elementu, takiego jak dokument, adres e-mail lub kontener, można zastosować tylko jedną etykietę poufności. Jeśli ustawisz opcję wymagającą od użytkowników podania uzasadnienia zmiany etykiety na niższą klasyfikację, kolejność tej listy będzie określać niższe klasyfikacje. Jednak ta opcja nie ma zastosowania do etykiet podrzędnych, które mają priorytet etykiety nadrzędnej.

Porządkowanie płyt podrzędnych jest jednak używane z [automatycznym etykietowaniem](apply-sensitivity-label-automatically.md). Jeśli skonfigurujesz etykiety do automatycznego stosowania lub jako zalecenie, dla więcej niż jednej etykiety może zostać wyświetlonych wiele dopasowań. Aby określić etykietę, która ma zostać zastosowana lub zalecana, jest używana kolejność etykiet: wybrano ostatnią etykietę wrażliwą, a następnie, jeśli ma to zastosowanie, ostatnie etykiety podrzędne.

![Opcja utworzenia etykiety podrzędnej.](../media/Sensitivity-label-sublabel-options.png)

### <a name="sublabels-grouping-labels"></a>Etykiety podrzędne (grupowanie etykiet)

Dzięki etykietom podrzędnym można grupować co najmniej jedną etykietę poniżej etykiety nadrzędnej, którą użytkownik widzi w aplikacji pakietu Office. Na przykład w obszarze Poufne organizacja może używać kilku różnych etykiet dla określonych typów tej klasyfikacji. W tym przykładzie etykieta nadrzędna Poufne jest po prostu etykietą tekstową bez ustawień ochrony, a ponieważ ma etykiety podrzędne, nie można jej zastosować do zawartości. Zamiast tego użytkownicy muszą wybrać pozycję Poufne, aby wyświetlić etykiety podrzędne, a następnie mogą wybrać podlabel do zastosowania do zawartości.

Etykiety podrzędne to po prostu sposób prezentowania etykiet użytkownikom w grupach logicznych. Etykiety podrzędne nie dziedziczą żadnych ustawień z etykiety nadrzędnej. Po opublikowaniu etykiety podrzędnej dla użytkownika ten użytkownik może następnie zastosować tę etykietę podrzędną do zawartości, ale nie może zastosować tylko etykiety nadrzędnej.

Nie wybieraj etykiety nadrzędnej jako etykiety domyślnej ani nie konfiguruj etykiety nadrzędnej tak, aby była automatycznie stosowana (lub zalecana). Jeśli to zrobisz, etykieta nadrzędna nie zostanie zastosowana do zawartości.

Przykład wyświetlania etykiet podrzędnych dla użytkowników:

![Pogrupowane płyty podrzędne na wstążce.](../media/Sensitivity-label-grouped-labels2.png)

### <a name="editing-or-deleting-a-sensitivity-label"></a>Edytowanie lub usuwanie etykiety poufności

Jeśli usuniesz etykietę poufności z centrum administracyjnego, etykieta nie zostanie automatycznie usunięta z zawartości, a wszelkie ustawienia ochrony będą nadal wymuszane dla zawartości, która miała zastosowaną etykietę.

Jeśli edytujesz etykietę poufności, wersja etykiety, która została zastosowana do zawartości, jest wymuszana dla tej zawartości.

## <a name="what-label-policies-can-do"></a>Jakie zasady etykiet mogą robić

Po utworzeniu etykiet poufności należy je opublikować, aby udostępnić je osobom i usługom w organizacji. Etykiety poufności można następnie zastosować do Office dokumentów i wiadomości e-mail oraz innych elementów, które obsługują etykiety poufności. 

W przeciwieństwie do etykiet przechowywania publikowanych w lokalizacjach, takich jak wszystkie Exchange skrzynki pocztowe, etykiety poufności są publikowane dla użytkowników lub grup. Aplikacje obsługujące etykiety poufności mogą następnie wyświetlać je tym użytkownikom i grupom jako zastosowane etykiety lub etykiety, które mogą zastosować.

Podczas konfigurowania zasad etykiety można wykonywać następujące czynności:

- **Wybierz, którzy użytkownicy i grupy widzą etykiety.** Etykiety można publikować w dowolnej konkretnej grupie zabezpieczeń, grupie dystrybucyjnej lub grupie Microsoft 365 obsługującej adres e-mail (która może mieć [członkostwo dynamiczne](/azure/active-directory/users-groups-roles/groups-create-rule)) w Azure AD.

- **Określ etykietę domyślną** dla nieoznaczonych dokumentów i wiadomości e-mail, nowych kontenerów (po [włączeniu etykiet poufności dla Microsoft Teams, grup Microsoft 365 i witryn SharePoint](sensitivity-labels-teams-groups-sites.md), a teraz etykieta domyślna [dla zawartości Power BI](/power-bi/admin/service-security-sensitivity-label-default-label-policy). Możesz określić tę samą etykietę dla wszystkich czterech typów elementów lub różnych etykiet. Użytkownicy mogą zmienić zastosowana domyślna etykieta poufności, aby lepiej dopasować czułość zawartości lub kontenera.
    
    > [!NOTE]
    > W wersji zapoznawczej aplikacji Office korzystających z wbudowanych etykiet: to ustawienie obsługuje teraz istniejące dokumenty, gdy są otwierane przez użytkowników, a także nowe dokumenty. Ta zmiana zachowania zapewnia równość z klientem ujednoliconego etykietowania usługi Azure Information Protection. Aby uzyskać więcej informacji na temat wdrożenia aplikacji i minimalnych wersji, zobacz [tabelę możliwości](sensitivity-labels-office-apps.md#sensitivity-label-capabilities-in-word-excel-and-powerpoint) programu Word, Excel i PowerPoint.
    
    Rozważ użycie etykiety domyślnej, aby ustawić podstawowe ustawienia ochrony, które mają zostać zastosowane do całej zawartości. Jednak bez trenowania użytkownika i innych kontrolek to ustawienie może również spowodować niedokładne etykietowanie. Zazwyczaj nie jest dobrym pomysłem wybranie etykiety, która stosuje szyfrowanie jako etykietę domyślną do dokumentów. Na przykład wiele organizacji musi wysyłać i udostępniać dokumenty użytkownikom zewnętrznym, którzy mogą nie mieć aplikacji, które obsługują szyfrowanie lub mogą nie używać konta, które może być autoryzowane. Aby uzyskać więcej informacji na temat tego scenariusza, zobacz [Udostępnianie zaszyfrowanych dokumentów użytkownikom zewnętrznym](sensitivity-labels-office-apps.md#sharing-encrypted-documents-with-external-users).
    
    > [!IMPORTANT]
    > Jeśli masz [etykiety podrzędne](#sublabels-grouping-labels), uważaj, aby nie konfigurować etykiety nadrzędnej jako etykiety domyślnej.

- **Wymagaj uzasadnienia zmiany etykiety.** Jeśli użytkownik próbuje usunąć etykietę lub zastąpić ją etykietą z numerem niższego rzędu, możesz wymagać, aby użytkownik uzasadnił wykonanie tej akcji. Na przykład użytkownik otwiera dokument z etykietą Poufne (numer zamówienia 3) i zastępuje tę etykietę jedną o nazwie Public (numer zamówienia 1). W przypadku aplikacji Office ten monit o uzasadnienie jest wyzwalany raz dla sesji aplikacji podczas korzystania z wbudowanego etykietowania i dla każdego pliku podczas korzystania z klienta ujednoliconego etykietowania usługi Azure Information Protection. Administratorzy mogą odczytać przyczynę uzasadnienia wraz ze zmianą etykiety w [Eksploratorze działań](data-classification-activity-explorer.md).

    ![Monituj, gdzie użytkownicy wprowadzają uzasadnienie.](../media/Sensitivity-label-justification-required.png)

- **Wymagaj od użytkowników zastosowania etykiety** dla dokumentów i wiadomości e-mail, tylko dokumentów, kontenerów i zawartości Power BI. Te opcje, znane również jako obowiązkowe etykietowanie, zapewniają, że etykieta musi zostać zastosowana, zanim użytkownicy będą mogli zapisywać dokumenty i wysyłać wiadomości e-mail, tworzyć nowe grupy lub witryny oraz używać nieoznaczonej zawartości do Power BI.
    
    W przypadku dokumentów i wiadomości e-mail etykieta może zostać przypisana ręcznie przez użytkownika, automatycznie w wyniku skonfigurowanego warunku lub domyślnie przypisana (domyślna opcja etykiety została wcześniej opisana). Przykładowy monit, gdy użytkownik jest wymagany do przypisania etykiety:

    ![Monituj w Outlook z prośbą o zastosowanie wymaganej etykiety.](../media/sensitivity-labels-mandatory-prompt-outlook.png)
    
    Aby uzyskać więcej informacji na temat obowiązkowego etykietowania dokumentów i wiadomości e-mail, zobacz [Wymagaj od użytkowników zastosowania etykiety do poczty e-mail i dokumentów](sensitivity-labels-office-apps.md#require-users-to-apply-a-label-to-their-email-and-documents).
    
    W przypadku kontenerów etykieta musi być przypisana w momencie utworzenia grupy lub lokacji.
    
    Aby uzyskać więcej informacji na temat obowiązkowego etykietowania dla Power BI, zobacz [Obowiązkowe zasady etykiet dla Power BI](/power-bi/admin/service-security-sensitivity-label-mandatory-label-policy).
    
    Rozważ użycie tej opcji, aby zwiększyć zakres etykietowania. Jednak bez trenowania użytkowników te ustawienia mogą spowodować niedokładne etykietowanie. Ponadto, chyba że ustawiono również odpowiednią etykietę domyślną, obowiązkowe etykietowanie może frustrować użytkowników częstymi monitami.

- **Podaj link pomocy do niestandardowej strony pomocy.** Jeśli użytkownicy nie mają pewności, co oznaczają etykiety poufności ani jak należy ich używać, możesz podać adres URL Dowiedz się więcej, który znajduje się w dolnej części menu **Etykieta poufności** w aplikacjach Office:

    ![Dowiedz się więcej na temat przycisku Czułość na wstążce.](../media/Sensitivity-label-learn-more.png)

Po utworzeniu zasad etykiet, które przypisują nowe etykiety poufności do użytkowników i grup, użytkownicy zaczną widzieć te etykiety w swoich aplikacjach Office. Odczekaj do 24 godzin na replikację najnowszych zmian w całej organizacji.

Nie ma limitu liczby etykiet poufności, które można tworzyć i publikować, z jednym wyjątkiem: jeśli etykieta stosuje szyfrowanie określające użytkowników i uprawnienia, w tej konfiguracji jest obsługiwanych maksymalnie 500 etykiet. Jednak najlepszym rozwiązaniem jest obniżenie kosztów administracyjnych i zmniejszenie złożoności dla użytkowników, staraj się ograniczyć liczbę etykiet do minimum. Rzeczywiste wdrożenia okazały się zauważalnie ograniczone, gdy użytkownicy mają więcej niż pięć etykiet głównych lub więcej niż pięć etykiet podrzędnych na etykietę główną.

### <a name="label-policy-priority-order-matters"></a>Priorytet zasad etykiet (kolejność ma znaczenie)

Etykiety poufności są dostępne dla użytkowników, publikując je w zasadach etykiet poufności, które są wyświetlane na liście na karcie **Zasady poufności** na stronie **Zasady etykiet** . Podobnie jak etykiety poufności (zobacz [Priorytet etykiety (kolejność ma znaczenie)](#label-priority-order-matters)), kolejność zasad etykiet poufności jest ważna, ponieważ odzwierciedla ich priorytet. Zasady etykiet o najniższym priorytecie są wyświetlane u **góry**, a zasady etykiet o najwyższym priorytecie są wyświetlane u **dołu**.

Zasady etykiet składają się z następujących elementów:

- Zestaw etykiet.
- Użytkownicy i grupy, do których zostaną przypisane zasady z etykietami.
- Zakres ustawień zasad i zasad dla tego zakresu (np. etykieta domyślna dla plików i wiadomości e-mail).

Możesz uwzględnić użytkownika w wielu zasadach etykiet, a użytkownik pobierze wszystkie etykiety poufności i ustawienia z tych zasad. W przypadku konfliktu ustawień z wielu zasad zostaną zastosowane ustawienia z zasad o najwyższym priorytecie (najniższej pozycji). Innymi słowy, najwyższy priorytet wygrywa dla każdego ustawienia.

Jeśli nie widzisz zachowania ustawień zasad etykiety lub etykiety oczekiwanego dla użytkownika lub grupy, sprawdź kolejność zasad etykiet poufności. Może być konieczne przeniesienie zasad w dół. Aby zmienić kolejność zasad etykiet, wybierz zasady etykiet poufności, > wybrać wielokropek po prawej stronie > **Przenieś w dół** lub **Przenieś w górę**.

![Przenieś opcję na stronie dla zasad etykiet poufności.](../media/sensitivity-label-policy-priority.png)

> [!NOTE]
> Pamiętaj: w przypadku konfliktu ustawień dla użytkownika, któremu przypisano wiele zasad, zastosowano ustawienie z zasad o najwyższym priorytecie (najniższej pozycji).

## <a name="sensitivity-labels-and-azure-information-protection"></a>Etykiety poufności i usługa Azure Information Protection

Etykiety poufności wbudowane w Aplikacje Microsoft 365 na Windows, macOS, iOS i Android wyglądają i zachowują się bardzo podobnie na tych urządzeniach, aby zapewnić użytkownikom spójne środowisko etykietowania. Jednak na komputerach Windows można również użyć [klienta usługi Azure Information Protection (AIP](/azure/information-protection/rms-client/aip-clientv2)). Ten klient jest teraz w [trybie konserwacji](https://techcommunity.microsoft.com/t5/security-compliance-and-identity/announcing-aip-unified-labeling-client-maintenance-mode-and/ba-p/3043613).

Jeśli używasz klienta usługi AIP, zobacz [Dlaczego warto wybrać wbudowane etykietowanie w dodatku AIP dla aplikacji Office](sensitivity-labels-aip.md), aby zrozumieć opcje etykietowania i zarządzać nimi dla Windows komputerów.

### <a name="azure-information-protection-labels"></a>Etykiety usługi Azure Information Protection

> [!NOTE]
> Zarządzanie etykietami dla etykiet usługi Azure Information Protection w Azure Portal zostało wycofane **31 marca 2021 r**. Dowiedz się więcej z oficjalnego [powiadomienia o wycofaniu](https://techcommunity.microsoft.com/t5/azure-information-protection/announcing-timelines-for-sunsetting-label-management-in-the/ba-p/1226179).

Jeśli dzierżawa nie znajduje się jeszcze na [ujednoliconej platformie etykietowania](/azure/information-protection/faqs#how-can-i-determine-if-my-tenant-is-on-the-unified-labeling-platform), musisz najpierw aktywować ujednolicone etykietowanie, zanim będzie można używać etykiet poufności. Aby uzyskać [instrukcje, zobacz How to migrate Azure Information Protection labels to unified sensitivity labels (Jak migrować etykiety usługi Azure Information Protection do ujednoliconych etykiet poufności](/azure/information-protection/configure-policy-migrate-labels)).

## <a name="sensitivity-labels-and-the-microsoft-information-protection-sdk"></a>Etykiety poufności i zestaw SDK Microsoft Information Protection

Ponieważ etykieta poufności jest przechowywana w metadanych dokumentu, aplikacje i usługi innych firm mogą odczytywać i zapisywać w tych metadanych etykietowania w celu uzupełnienia wdrożenia etykietowania. Ponadto deweloperzy oprogramowania mogą korzystać z [zestawu Microsoft Information Protection SDK](/information-protection/develop/overview#microsoft-information-protection-sdk), aby w pełni obsługiwać funkcje etykietowania i szyfrowania na wielu platformach. Aby dowiedzieć się więcej, zobacz [ogłoszenie o ogólnej dostępności na blogu Tech Community](https://techcommunity.microsoft.com/t5/Microsoft-Information-Protection/Microsoft-Information-Protection-SDK-Now-Generally-Available/ba-p/263144). 

Możesz również dowiedzieć się więcej o [rozwiązaniach partnerskich zintegrowanych z usługą Microsoft Purview Information Protection](https://techcommunity.microsoft.com/t5/Azure-Information-Protection/Microsoft-Information-Protection-showcases-integrated-partner/ba-p/262657).

## <a name="deployment-guidance"></a>Wskazówki dotyczące wdrażania

Aby zapoznać się z planowaniem wdrożenia i wskazówkami, które obejmują informacje o licencjonowaniu, uprawnienia, strategię wdrażania, listę obsługiwanych scenariuszy i dokumentację użytkownika końcowego, zobacz [Wprowadzenie z etykietami poufności](get-started-with-sensitivity-labels.md).

Aby dowiedzieć się, jak używać etykiet poufności w celu zachowania zgodności z przepisami dotyczącymi prywatności danych, zobacz [Wdrażanie ochrony informacji dla przepisów dotyczących prywatności danych za pomocą Microsoft 365](../solutions/information-protection-deploy.md) (aka.ms/m365dataprivacy).
