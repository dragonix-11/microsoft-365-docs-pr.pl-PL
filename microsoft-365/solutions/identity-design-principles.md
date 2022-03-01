---
title: Microsoft 365 zasobów przedsiębiorstwa — architektura zabezpieczeń
description: Dowiedz się więcej na temat najlepszych strategii projektowych dotyczących architektury Enterprise Firmy Microsoft, Alex Shteynberg, technical Principal Architect w firmie Microsoft.
ms.author: bcarter
author: brendacarter
manager: bcarter
ms.audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- M365-identity-device-management
- M365-security-compliance
- M365solutions
ms.custom: seo-marvel-jun2020
f1.keywords: NOCSH
ms.openlocfilehash: 8e24242639362bddca7540cd8dfb390b0edb5e8c
ms.sourcegitcommit: 0ee2dabe402d44fecb6856af98a2ef7720d25189
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/09/2021
ms.locfileid: "62995950"
---
# <a name="to-identity-and-beyondone-architects-viewpoint"></a>Tożsamość i nie tylko — widok jednego z architektów

W tym artykule [Alex Shteynberg](https://www.linkedin.com/in/alex-shteynberg/), główny architekt ds. technicznych w firmie Microsoft, omawia najważniejsze strategie projektowe dla przedsiębiorstw, które zaadoptują Microsoft 365 i inne usługi firmy Microsoft w chmurze.

## <a name="about-the-author"></a>Informacje o autorze

![Zdjęcie Alexa Shteynberga.](../media/solutions-architecture-center/identity-and-beyond-alex-shteynberg.jpg)

Jestem głównym architektem technologii w Centrum technologii [Microsoft w Nowym Jorku](https://www.microsoft.com/mtc?rtc=1). Pracuję głównie z dużymi klientami i z złożonymi wymaganiami. Mój punkt widzenia i opinie są oparte na tych interakcjach i mogą nie mieć zastosowania do każdej sytuacji. Jednak, z mojego doświadczenia, jeśli możemy pomóc klientom w przypadku najbardziej złożonych wyzwań, możemy pomóc wszystkim klientom.

Zazwyczaj pracuję z ponad 100 klientami każdego roku. Każda organizacja ma unikatowe cechy, ale warto widzieć trendy i podobieństwa. Jednym z trendów jest na przykład zainteresowanie różnych branż dla wielu klientów. W końcu gałąź bankowa może być również kawiarnią i centrum społeczności.

W mojej roli skupiam się na pomaganiu klientom znaleźć najlepsze rozwiązanie techniczne w celu rozwiązania ich unikatowego zestawu celów biznesowych. Oficjalnie skupię się na tożsamości, zabezpieczeniach, prywatności i zgodności. Dobrze, że dotykają one wszystkiego, co robimy. Umożliwia ona udział w większości projektów. To sprawia mi sporo pracy i podoba mi się ta rola.

Mieszkam w Nowym Jorku (najlepsza!) i naprawdę podoba mi się jej kultura, żywność i ludzie (nie ruch drogowy). Chcę podróżować, gdy mogę i mam nadzieję, że zobaczę większość świata w moim życiu. Obecnie przeszukam podróż do Afryki, aby dowiedzieć się więcej o dzikiej przyrodie.

## <a name="guiding-principles"></a>Zasady wytycznych

- **Prostota jest często lepszym rozwiązaniem**: z technologią można (niemal) wykonać niemal wszystko, ale nie oznacza to, że należy. Zwłaszcza w zakresie zabezpieczeń, wielu klientów ma zbyt wiele nowych rozwiązań. Podoba mi [się ten klip](https://www.youtube.com/watch?v=SOQgABDSYZE) wideo z konferencji Google z paskiem, aby podkreślić ten punkt.
- **Ludzie, proces, technologia**: projekt [dla osób w celu](https://en.wikipedia.org/wiki/Human-centered_design) ulepszania procesu, a nie najpierw dla technologii. Nie ma żadnych "doskonałych" rozwiązań. Musimy równoważyć różne czynniki ryzyka, a decyzje będą różne dla każdej firmy. Zbyt wielu klientów projektuje podejście, których później unikają ich użytkownicy.
- **Najpierw skup się** na tym, dlaczego i "jak": Bądź irytującym 7-latkiem i milionem pytań. Nie możemy uzyskać właściwej odpowiedzi, jeśli nie znamy odpowiednich pytań, które można zadać. Wielu klientów określa sposób działania firmy, nie definiując problemu biznesowego. Istnieje zawsze wiele ścieżek, które można podjąć.
- **Długa część najlepszych rozwiązań:** należy pamiętać o tym, że najlepsze rozwiązania zmieniają się z prędkością światła. Jeśli usługa Azure AD była przejrzana ponad trzy miesiące temu, prawdopodobnie jest to nie zawsze aktualne. Wszystko w tym miejscu może ulec zmianie po opublikowaniu. Dzisiejsza opcja "Najlepsza" może nie być taka sama jak za sześć miesięcy.

## <a name="baseline-concepts"></a>Koncepcje planu bazowego

Nie pomijaj tej sekcji. Często zdarza mi się, że muszę cofać się do tych tematów, nawet dla klientów, którzy od wielu lat korzystali z usług w chmurze.
Niestety język nie jest dokładnym narzędziem. Często używamy tego samego wyrazu, aby oznaczać różne koncepcje lub różne wyrazy, aby oznaczać to samo pojęcie. Często używam poniższego diagramu do ustanawiania terminologii podstawowej i "modelu hierarchii".
<br><br>

![Ilustracja przedstawiająca dzierżawę, subskrypcję, usługę i dane.](../media/solutions-architecture-center/Identity-and-beyond-tenant-level.png)

<br>

Gdy nauczysz się popływać, lepiej zacząć w puli, a nie w środku oceanu. Nie próbuję uzyskać dokładności technicznej przy użyciu tego diagramu. Jest to model dyskusji nad pewnymi podstawowymi pojęciami.

Na diagramie:

- Dzierżawa = wystąpienie usługi Azure AD. Znajduje się on na początku hierarchii, czyli na poziomie 1 na diagramie. Można to uznać [za "granica](/azure/active-directory/users-groups-roles/licensing-directory-independence)" miejsca, w którym występują wszystkie inne zdarzenia (poza usługą [Azure AD B2B](/azure/active-directory/b2b/what-is-b2b) ). Wszystkie usługi firmy Microsoft w chmurze przedsiębiorstwa należą do jednej z tych dzierżaw. Usługi dla klientów konsumenckich są oddzielne. "Dzierżawa" jest wyświetlana w dokumentacji Office 365 dzierżawy usługi Azure, dzierżawy WVD i tak dalej. Te odmiany często powodują nieporozumienia u klientów.
- Usługi/subskrypcje (poziom 2 na diagramie) należą do jednej i tylko jednej dzierżawy. Większość usług SaaS jest 1:1 i nie można się poruszać bez migracji. Platforma Azure jest inna. Możesz przenieść [rozliczenia](/azure/cost-management-billing/manage/billing-subscription-transfer) i/lub [subskrypcję](/azure/active-directory/fundamentals/active-directory-how-subscriptions-associated-directory) do innej dzierżawy. Istnieje wielu klientów, którzy muszą przenieść subskrypcje platformy Azure. Ma to różne konsekwencje. Obiekty istniejące poza subskrypcją nie są przenosine (na przykład kontrolka dostępu oparta na rolach, kontrolka Azure RBAC i obiekty usługi Azure AD, w tym grupy, aplikacje, zasady itd.). Ponadto niektóre usługi (takie jak magazyn kluczy platformy Azure, cegłe danych itd.). Nie migruj usług bez dobrej potrzeby biznesowej. Niektóre skrypty, które mogą okazać się przydatne podczas [migracji, są udostępniane GitHub](https://github.com/lwajswaj/azure-tenant-migration).
- A given service usually has some sort of "sublevel" boundary, or Level 3 (L3). Jest to przydatne do zrozumienia podziałów zabezpieczeń, zasad, zarządzania i tak dalej. Niestety, nie istnieje nazwa ujednolicona, o których wiem. Przykładowe nazwy L3 to: Azure Subscription = [resource](/azure/azure-resource-manager/management/manage-resources-portal); Dynamics 365 CE = [instance](/dynamics365/admin/new-instance-management); Power BI = obszar [roboczy](/power-bi/service-create-the-new-workspaces); Power Apps = [środowisko](/power-platform/admin/environments-overview) itp.
- Poziom 4 to miejsce, w którym są mieszkane rzeczywiste dane. Ten "samolot danych" jest złożonym tematem. Niektóre usługi używają usługi Azure AD dla RBAC, inne nie. Omówię go nieco, gdy przejdę do tematów dotyczących delegowania.

Kilka dodatkowych pojęć, które widzę u wielu klientów (i pracowników firmy Microsoft), jest zdezorientowanych lub mam pytania dotyczące następujących kwestii:

- Każdy może [utworzyć](/azure/active-directory/fundamentals/active-directory-access-create-new-tenant) wiele dzierżaw bez [żadnych kosztów](https://azure.microsoft.com/pricing/details/active-directory/). Nie potrzebujesz obsługi administracyjnej usługi. Mam ich dziesiątki. Każda nazwa dzierżawy jest unikatowa w usłudze firmy Microsoft w chmurze na całym świecie (czyli nie może mieć żadnej nazwy dwóch dzierżaw). Wszystkie mają format TenantName.onmicrosoft.com. Istnieją również procesy, które automatycznie tworzą dzierżawców ([dzierżawy](/azure/active-directory/users-groups-roles/directory-self-service-signup) nieza zarządzania). Może się tak na przykład zdarzyć, gdy użytkownik utworzyć konto w usłudze dla przedsiębiorstwa z domeną poczty e-mail, która nie istnieje w innej dzierżawie.
- W dzierżawie zarządzanej można zarejestrować wiele domen [DNS](/azure/active-directory/fundamentals/add-custom-domain) . Nie spowoduje to zmiany oryginalnej nazwy dzierżawy. Obecnie nie ma łatwego sposobu zmiany nazwy dzierżawy (innej niż migracja). Mimo że nazwa dzierżawy nie jest z technicznego punktu widzenia krytyczna w tych dniach, niektóre mogą wydawać się ograniczane.
- Należy zarezerwować nazwę dzierżawy dla organizacji, nawet jeśli jeszcze nie planujesz wdrożenia żadnych usług. W przeciwnym razie ktoś może je od Ciebie wziąć i nie ma prostego procesu jego odbierania (ten sam problem, co nazwy DNS). Klienci zbyt często słyszą ten sposób. To, jaka nazwa dzierżawy powinna być tematem dyskusji.
- Jeśli jesteś właścicielem przestrzeni nazw DNS, musisz dodać je wszystkie do swoich dzierżaw. W przeciwnym razie przy użyciu [](/azure/active-directory/users-groups-roles/directory-self-service-signup) tej nazwy można utworzyć dzierżawę niezawiąwaną, co spowoduje zakłócenia w jej [zarządzania](/azure/active-directory/users-groups-roles/domains-admin-takeover).
- Przestrzeń nazw DNS (na przykład contoso.com) może należeć do jednej i tylko jednej dzierżawy. Ma to wpływ na różne scenariusze (na przykład udostępnianie domeny poczty e-mail podczas fuzji lub pozyskiwania itp.). Istnieje sposób zarejestrowania podtypu DNS (na przykład div.contoso.com) w innej dzierżawie, ale należy tego uniknąć. Rejestrując nazwę domeny najwyższego poziomu, zakłada się, że wszystkie poddomeny należą do tej samej dzierżawy. W scenariuszach z wieloma dzierżawami (zobacz poniżej) zwykle zaleca się używanie innej nazwy domeny najwyższego poziomu (takiej jak contoso.ch lub ch-contoso.com).
- KtoTo "właścicielem" dzierżawy? Często widzę klientów, którzy nie wiedzą, kto obecnie jest właścicielem ich dzierżawy. To jest duża czerwona flaga. Zadzwoń do pomocy technicznej Microsoft JNW. Równie problematyczne jest zarządzanie dzierżawą przez właściciela usługi (często Exchange administratora usługi). Dzierżawa będzie zawierać wszystkie usługi, które możesz chcieć mieć w przyszłości. Właściciel dzierżawy powinien być grupą, która może podjąć decyzję o włączeniu wszystkich usług w chmurze w organizacji. Innym problemem jest to, że grupa właściciela dzierżawy jest proszona o zarządzanie wszystkimi usługami. Nie jest to skalowanie dla dużych organizacji.
- Nie ma pojęcia dzierżawy podrzędnej/superdostępu. Z jakiegoś powodu ten mityczne informacje powtarzają się samo. Dotyczy to również dzierżaw [usługi Azure AD B2C](/azure/active-directory-b2c/) . Usłyszysz zbyt wiele razy komunikat "Moje środowisko B2C znajduje się w mojej dzierżawie XYZ" lub "Jak przenieść dzierżawę platformy Azure do mojej Office 365 dzierżawy?".
- W tym dokumencie skupiono się na komercyjnym chmurze na całym świecie, ponieważ jest to rozwiązanie, z jakiego korzysta większość klientów. Czasami warto wiedzieć o [suwerennych chmurach](/azure/active-directory/develop/authentication-national-cloud). Suwerenne chmury mają dodatkowe konsekwencje do omówienia, które nie są objęte tą dyskusją.

## <a name="baseline-identity-topics"></a>Tematy tożsamości według planu bazowego

Mamy wiele dokumentacji dotyczącej platformy tożsamości firmy Microsoft — usługi Azure Active Directory (Azure AD). W przypadku osób, które dopiero zaczynają, często są one przytłaczające. Nawet gdy się o tym dowiedziesz, ciągłe innowacje i zmiany mogą być trudne. W moich interakcjach z klientami często widzę, że ujęłam się jako "tłumacz" między celami biznesowymi i metodami "Dobra, lepiej, najlepsza", aby zająć się tymi tematami (oraz notatkami z ludzkich "klifów" do tych tematów). Rzadko występuje idealna odpowiedź, a decyzja "właściwa" to równowaga między różnymi czynnikami ryzyka. Poniżej przedstawiono niektóre często zadawane pytania i obszary nieporozumień, które zwykle omawiam z klientami.

### <a name="provisioning"></a>Inicjowanie obsługi administracyjnej

Usługa Azure AD nie rozwiąże problemu z powodu braku zarządzania w świecie tożsamości! [Zarządzanie tożsamością](/azure/active-directory/governance/identity-governance-overview) powinno być krytycznym elementem niezależnie od jakichkolwiek decyzji dotyczących chmury. Wymagania dotyczące zarządzania zmieniają się z czasem, dlatego jest to program, a nie narzędzie.

[Czy usługa Azure AD Połączenie](/azure/active-directory/hybrid/whatis-azure-ad-connect) [a Microsoft Identity Manager (](/microsoft-identity-manager/microsoft-identity-manager-2016)MIM) a co innego (innej firmy lub niestandardowej)? Możesz też niechcący oszczędzić sobie głowy teraz i w przyszłości, więc możesz teraz i w przyszłości przejść do usługi Azure AD Połączenie. W tym narzędziu są dostępne różnego rodzaju inteligentne rozwiązania, które należy zająć się konfiguracjami klientów i bieżącymi innowacjami.

Niektóre przypadki brzegowe, których granice mogą być dysków w kierunku bardziej złożonej architektury:

- Mam wiele lasów usług AD bez łączności sieciowej między tymi usługami. Dostępna jest nowa opcja o nazwie [Inicjowanie obsługi administracyjnej w chmurze](/azure/active-directory/cloud-provisioning/what-is-cloud-provisioning).
- Nie mam usługi Active Directory ani nie chcę jej instalować. Usługę Azure AD Połączenie skonfigurować do synchronizacji [z LDAP](/azure/active-directory/hybrid/plan-hybrid-identity-design-considerations-tools-comparison) (może być wymagany partner).
- Muszę aprowizować te same obiekty w wielu dzierżawach. Nie jest to obsługiwane technicznie, ale zależy od definicji "takiej samej".

Czy należy dostosować domyślne reguły synchronizacji ([filtrowanie](/azure/active-directory/hybrid/how-to-connect-sync-configure-filtering) obiektów, [zmienianie atrybutów](/azure/active-directory/hybrid/reference-connect-sync-attributes-synchronized), [alternatywny](/azure/active-directory/hybrid/plan-connect-userprincipalname) identyfikator logowania i tak dalej)? Omiń to! Platforma tożsamości jest równie cenna, jak usługi, które z niego korzystają. Mimo że można wykonać wszelkiego rodzaju konfiguracje pożywne, aby odpowiedzieć na to pytanie, należy przyjrzeć się wpływowi aplikacji. Jeśli filtrowane obiekty z włączoną obsługą poczty nie będą niepełne, jeśli filtrowane są obiekty z włączoną obsługą poczty. jeśli aplikacja korzysta z określonych atrybutów, filtrowanie ich będzie miało nieprzewidywalny wpływ. i tak dalej. To nie jest decyzja zespołu tożsamości.

Oprogramowanie XYZ SaaS obsługuje inicjowanie obsługi w czasie (JIT), dlaczego wymagasz ode mnie synchronizowania? Zobacz wyżej. Wiele aplikacji potrzebuje informacji "profilu" do działania. Nie możesz mieć listy adresowej, jeśli nie są dostępne wszystkie obiekty z włączoną obsługą poczty. To samo dotyczy [inicjowania obsługi użytkowników w](/azure/active-directory/app-provisioning/user-provisioning) aplikacjach zintegrowanych z usługą Azure AD.

### <a name="authentication"></a>Uwierzytelnianie

[Synchronizacja skrótów haseł](/azure/active-directory/hybrid/how-to-connect-password-hash-synchronization) (PHS) a uwierzytelnianie [pass-through](/azure/active-directory/hybrid/how-to-connect-pta-how-it-works) (PTA) a [federacja](/azure/active-directory/hybrid/how-to-connect-fed-compatibility).

Zazwyczaj istnieje dyskusja [pasjonatów federacji](/azure/active-directory/hybrid/choose-ad-authn) . Prostszy jest zazwyczaj lepszy i dlatego należy korzystać z funkcji PHS, o ile nie ma na to uzasadnionego powodu. Można również skonfigurować różne metody uwierzytelniania dla różnych domen DNS w tej samej dzierżawie.

Niektórzy klienci włączą federację + PHS głównie dla:

- Opcja [powrotu do (na](/azure/active-directory/hybrid/plan-migrate-adfs-password-hash-sync) wypadek odzyskiwania po awarii), jeśli usługa federska jest niedostępne.
- Dodatkowe funkcje (np.: [Azure AD DS](/azure/active-directory-domain-services/tutorial-configure-password-hash-sync)) i usługi zabezpieczeń (np.: [wycieki poświadczeń](/azure/active-directory/reports-monitoring/concept-risk-events#leaked-credentials))
- Pomoc techniczna dla usług na platformie Azure, które nie rozumieją uwierzytelniania federckiego (na przykład [Pliki platformy Azure](/azure/storage/files/storage-files-active-directory-overview)).

Klienci często podchodzę przez przepływ uwierzytelniania klienta, aby wyjaśnić pewne błędy. Wynik przypomina poniższy obraz, który nie jest tak dobry jak interakcyjny proces dojechania do celu.

![Przykładowa konwersacja na tablicy.](../media/solutions-architecture-center/identity-beyond-whiteboard-example.png)

Ten typ rysunku tablicy ilustruje, gdzie zasady zabezpieczeń są stosowane w ramach procesu żądania uwierzytelniania. W tym przykładzie zasady wymuszane za pośrednictwem usługi federejnej Active Directory (AD FS) są stosowane do pierwszego żądania usługi, ale nie do kolejnych żądań usługi. Jest to co najmniej jeden powód przeniesienia kontrolek zabezpieczeń do chmury.

Marzą o logowania [się jednokrotnego](/azure/active-directory/manage-apps/what-is-single-sign-on) (SSO) tak długo, jak pamiętam. Niektórzy klienci uważają, że mogą to osiągnąć, wybierając dostawcę federacji "prawego" (STS). Usługa Azure AD może znacznie ułatwić [włączenie funkcji logowania jednokrotnego](/azure/active-directory/manage-apps/plan-sso-deployment) , ale żaden system STS nie jest magiczny. Istnieje zbyt wiele "starszych" metod uwierzytelniania, które są nadal używane w krytycznych aplikacjach. Rozszerzenie usługi Azure AD o [rozwiązania partnerów](/azure/active-directory/saas-apps/tutorial-list) może dotyczyć wielu z tych scenariuszy. Logowanie jednokrotne to strategia i podróż. Nie da się do tego przejść bez przechodzenia do standardów [dotyczących aplikacji](/azure/active-directory/develop/v2-app-types). Związane z tym tematem jest podróż do [](/azure/active-directory/authentication/concept-authentication-passwordless) uwierzytelniania bez haseł, które również nie ma magicznych odpowiedzi.

[Uwierzytelnianie wieloskładnikowe](/azure/active-directory/authentication/concept-mfa-howitworks) (MFA) jest obecnie niezbędne ([tutaj,](https://techcommunity.microsoft.com/t5/azure-active-directory-identity/your-pa-word-doesn-t-matter/ba-p/731984) aby uzyskać więcej informacji). Dodaj do niego [analizę zachowania](/azure/active-directory/authentication/tutorial-risk-based-sspr-mfa) użytkownika i masz rozwiązanie, które zapobiega najczęstszym atakom cyberatak. Nawet usługi konsumenckie wymagają uwierzytelniania wieloskładnikowego. Jednak wciąż spotykam się z wieloma klientami, którzy nie chcą przechodzić do metod [nowoczesnego](../enterprise/hybrid-modern-auth-overview.md) uwierzytelniania. Największy argument jest taki, że będzie on miał wpływ na użytkowników i starsze aplikacje. Czasami dobra robota może ułatwić klientom poruszanie się po Exchange Online [nowych.](https://techcommunity.microsoft.com/t5/exchange-team-blog/basic-auth-and-exchange-online-february-2020-update/ba-p/1191282) Dostępnych jest wiele raportów [usługi](/azure/active-directory/fundamentals/concept-fundamentals-block-legacy-authentication) Azure AD, które pomogą klientom w przejściu do programu.

### <a name="authorization"></a>Autoryzacja

W [serwisie Wikipedia](https://en.wikipedia.org/wiki/Authorization) "autoryzuj" oznacza zdefiniowanie zasad dostępu. Wiele osób przyjrzyjmy się jej jako możliwości definiowania kontrolek dostępu do obiektu (pliku, usługi i tak dalej). W bieżącym świecie zagrożeń cyberprzestępczych ta koncepcja szybko rozwija się, aby dynamiczna zasada, która może reagować na różne wektory zagrożeń i szybko dostosowywać mechanizmy kontroli dostępu w odpowiedzi na te zagrożenia. Jeśli na przykład mam dostęp do mojego konta bankowego z nietypowej lokalizacji, otrzymuję dodatkowe instrukcje potwierdzenia. Aby do tego podchodzić, należy rozważyć nie tylko zasady, ale także cały ekosystem wykrywania zagrożeń i metody korelacji sygnału.

Aparat zasad usługi Azure AD jest implementowane przy użyciu zasad [dostępu warunkowego](/azure/active-directory/conditional-access/overview). Ten system jest zależny od informacji z różnych innych systemów wykrywania zagrożeń w celu podejmowania dynamicznych decyzji. Prosty widok przypomina poniższy rysunek:

![Aparat zasad w usłudze Azure AD.](../media/solutions-architecture-center/identity-and-beyond-illustration-3.png)

Połączenie wszystkich tych sygnałów umożliwia korzystanie z takich dynamicznych zasad:

- W przypadku wykrycia zagrożenia na urządzeniu dostęp do danych zostanie zmniejszony tylko do sieci Web bez możliwości ich pobierania.
- Jeśli pobierasz niezwykle dużą ilość danych, wszystko, co pobierzemy, zostanie zaszyfrowane i ograniczone.
- Jeśli uzyskujesz dostęp do usługi z urządzenia nieza zarządzania, dostęp do danych poufnych zostanie zablokowany, ale nie będzie można uzyskać dostępu do danych, które nie są ograniczone, bez możliwości kopiowania ich do innej lokalizacji.

Jeśli zgadzasz się z tą rozwiniętą definicją autoryzacji, musisz zaimplementować dodatkowe rozwiązania. To, jakie rozwiązania wdrożysz, zależy od tego, jak dynamiczne mają być zasady i które zagrożenia chcesz określić jako priorytetowe. Oto kilka przykładów takich systemów:

- [Azure AD Identity Protection](/azure/active-directory/identity-protection/)
- [Microsoft Defender for Identity](/azure-advanced-threat-protection/)
- [Ochrona punktu końcowego w usłudze Microsoft Defender](/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection)
- [Usługa Microsoft Defender dla Office 365](../security/office-365-security/defender-for-office-365.md)
- [Microsoft Defender for Cloud Apps](/cloud-app-security/) (Defender for Cloud Apps)
- [Microsoft 365 Defender](../security/defender/microsoft-365-defender.md)
- [Microsoft Intune](/mem/intune/)
- [Microsoft Information Protection](../compliance/information-protection.md) (MIP)
- [Microsoft Sentinel](/azure/sentinel/)

Poza usługą Azure AD różne usługi i aplikacje mają własne modele autoryzacji. Niektóre z nich omówiono w dalszej części sekcji delegowania.

### <a name="audit"></a>Inspekcja

Usługa Azure AD ma szczegółowe [funkcje inspekcji i](/azure/active-directory/reports-monitoring/) raportowania. Jednak nie jest to zwykle jedyne źródło informacji potrzebne do podejmowania decyzji dotyczących zabezpieczeń. Więcej dyskusji na ten temat można znaleźć w sekcji delegowania.

## <a name="theres-no-exchange"></a>Nie ma żadnych Exchange

Nie panikuj! Nie oznacza to, Exchange jest przestarzały (lub SharePoint itd.). Jest to nadal podstawowa usługa. Od pewnego czasu dostawcy technologii przeszli środowiska użytkownika (UX), aby obejmowały składniki wielu usług. Na Microsoft 365 przykład prosty jest "[nowoczesne](https://support.office.com/article/Attach-files-or-insert-pictures-in-Outlook-email-messages-BDFAFEF5-792A-42B1-9A7B-84512D7DE7FC) załączniki", gdzie załączniki do wiadomości e-mail są przechowywane w u SharePoint Online lub OneDrive dla Firm.

![Dołączanie pliku do wiadomości e-mail.](../media/solutions-architecture-center/modern-attachments.png)

W kliencie Outlook widać wiele usług, które są "połączone", nie tylko Exchange. Obejmuje to usługi Azure AD, Microsoft Search, aplikacje, profil, zgodność i Office 365 grupy.

![Outlook interfejs z objaśnieniami.](../media/solutions-architecture-center/identity-and-beyond-conceptual-screenshot.png)

Przeczytaj o [Elastyczna struktura firmy Microsoft](https://techcommunity.microsoft.com/t5/microsoft-365-blog/microsoft-ignite-blog-microsoft-fluid-framework-preview/ba-p/978268) informacji o nadchodzących możliwościach. Teraz na podglądzie mogę czytać konwersacje i odpowiadać na nie Teams bezpośrednio w programie Outlook. Ten klient Teams [jest](https://products.office.com/microsoft-teams/download-app) jednym z bardziej widocznych przykładów tej strategii.

Ogólnie trudniej jest narysować przejrzyste linie między usługami firmy Office 365 i innymi usługami w chmurach firmy Microsoft. Widzę to jako korzyść dla klientów, ponieważ mogą korzystać z łącznej innowacji we wszystkim, co robimy, nawet jeśli używają jednego składnika. Bardzo dobrze się ładuje i ma bardzo wiele konsekwencji dla wielu klientów.

Obecnie wiele grup IT klientów ma strukturę wokół "produktów". Jest to logiczne w środowisku lokalnym, ponieważ potrzebuje eksperta dla każdego konkretnego produktu. Jednak nie muszę już debugowania bazy danych usługi Active Directory ani bazy danych Exchange po tym, jak te usługi zostały przeniesione do chmury. Automatyzacja (rodzaj chmury) usuwa pewne powtarzające się zadania ręczne (zobacz, co się stało z fabryki). Zostaną one jednak zastąpione bardziej złożonymi wymaganiami, które trzeba będzie spełnić, aby zrozumieć interakcje między usługami, wpływ, potrzeby biznesowe itp. Jeśli chcesz się na to [chcieć](/learn/), przekształceń w chmurze daje wiele możliwości. Zanim przejdę do technologii, często rozmawiam z klientami na temat zarządzania zmianą w umiejętnościach IT i strukturze zespołu.

Dla wszystkich SharePoint osób i deweloperów przestań pytać "Jak mogę zrobić XYZ w SharePoint online?". Użyj [Power Automate](/power-automate/) (lub Flow) do przepływu pracy, jest to znacznie bardziej zaawansowana platforma. Użyj [programu Azure Bot Framework](/azure/bot-service/) , aby utworzyć lepszy interfejs użytkownika dla listy elementów o numerze 500 K. Zacznij korzystać [z programu Microsoft Graph](https://developer.microsoft.com/graph/) zamiast CSOM. [Microsoft Teams](/MicrosoftTeams/Teams-overview) obejmuje SharePoint ale także świat. Dostępnych jest wiele innych przykładów. Jest tam rozległy i wspaniały świat. Otwórz drzwi i zacznij [je eksplorować]().

Inny częsty wpływ ma obszar zgodności. Wydaje się, że takie podejście do różnych usług całkowicie myli wiele zasad zgodności. Wciąż widzę informacje o organizacjach o stanie "Chcę  dzienniku całej komunikacji e-mail z systemem zbierania elektronicznych materiałów dowodowych". Co to naprawdę oznacza, gdy poczta e-mail nie jest już tylko wiadomością e-mail, ale oknem do innych usług? Office 365 w zakresie [zgodności, ale](../compliance/index.yml) zmiana osób i procesów jest często znacznie trudniejsza niż technologia.

Istnieje wiele innych osób i skutki dla procesu. Według mnie jest to kluczowy i omawiane w tej sprawie obszar. Być może więcej w innym artykule.

## <a name="tenant-structure-options"></a>Opcje struktury dzierżawy

### <a name="single-tenant-vs-multi-tenant"></a>Jedna dzierżawa a wielodostępna

Na ogół większość klientów powinna mieć tylko jedną dzierżawę produkcyjną. Istnieje wiele powodów, dla których wiele dzierżaw stanowi wyzwanie (możesz wyszukać go [Bing](https://www.bing.com/search?q=office%20365%20multiple%20tenants)) lub przeczytać [ten oficjalny oficjalny list](https://aka.ms/multi-tenant-user). Jednocześnie wielu klientów korporacyjnych, z których pracuję, ma inną (małą) dzierżawę do nauki, testowania i eksperymentowania w nauce i testowania. Dostęp do usługi Azure w ramach wielu dzierżaw jest łatwiejszy dzięki [usłudze Azure Lighthouse](https://azure.microsoft.com/services/azure-lighthouse/). Office 365 i wielu innych usług SaaS mają limity dla scenariuszy między dzierżawami. Scenariusze [B2B usługi Azure AD](/azure/active-directory/b2b/what-is-b2b) mają wiele do rozważenia.

Wielu klientów kończy z wieloma dzierżawami produkcyjnymi po fuzjach i zakupach (M&A) i chcą skonsolidować ten proces. Dziś nie jest to proste i wymagałaby usług Microsoft Consulting Services (MCS) lub partnera oraz oprogramowania innej firmy. Nieustannie pracujemy inżynierowie nad różnymi scenariuszami z klientami korzystającymi z wielu dzierżaw w przyszłości.

Niektórzy klienci wybierają więcej niż jedną dzierżawę. Ta decyzja powinna być bardzo przemyślana i niemal zawsze wynikać z przyczyn biznesowych. Oto kilka przykładów:

- Struktura firmy typu przytrzymującego, w której nie jest wymagana łatwa współpraca między różnymi jednostkami oraz istnieje silne potrzeby administracyjne i inne potrzeby w zakresie izolacji.
- Po zakupieniu decyzja biznesowa o oddzieleniu dwóch jednostek została podjęta.
- Symulacja środowiska klienta, która nie zmienia środowiska produkcyjnego klienta.
- Opracowywanie oprogramowania dla klientów.

W tych scenariuszach z wieloma dzierżawami klienci często chcą zachować tę samą konfigurację we wszystkich dzierżawach lub raportować zmiany konfiguracji i użytkowników. Często oznacza to przejście z ręcznych zmian do konfiguracji jako kodu. Pomoc techniczna Microsoft Premiere oferuje warsztaty dotyczące tych typów wymagań na podstawie tego publicznego adresu IP: <https://Microsoft365dsc.com>.

### <a name="multi-geo"></a>Multi-Geo

Pytanie [brzmi "Multi-Geo](../enterprise/microsoft-365-multi-geo.md) " lub "Multi-Geo" (wielu lokalizacji geograficznych). Dzięki Office 365 multi-Geo możesz zapewniać i przechowywać dane w spoczynku w lokalizacjach geograficznych wybranych do spełnienia wymagań dotyczących [przechowywania danych.](../enterprise/o365-data-locations.md) Istnieje wiele myliń dotyczących tej funkcji. Należy pamiętać o następujących kwestiach:

- Nie zapewnia ona korzyści związanych z wydajnością. Może to sprawić, że wydajność będzie gorsza, [jeśli projekt](https://aka.ms/office365networking) sieci jest nieumiejętny. Urządzenia mogą być "blisko" sieci firmy Microsoft, a nie danych.
- Nie jest to rozwiązanie do zapewnienia zgodności [z RODO](https://www.microsoft.com/trust-center/privacy/gdpr-overview). RODO nie dotyczy przede wszystkim źródeł danych lub lokalizacji przechowywania. Istnieją inne struktury zgodności w tym zakresie.
- Nie wpływa to na delegowanie administracji (patrz poniżej) ani na [bariery informacyjne](../compliance/information-barriers.md).
- Nie jest to to samo co obsługa wielu dzierżaw i wymaga dodatkowych [przepływów pracy inicjowania obsługi administracyjnej](https://github.com/MicrosoftDocs/azure-docs-pr/blob/master/articles/active-directory/hybrid/how-to-connect-sync-feature-preferreddatalocation.md) przez użytkowników.
- Nie powoduje przeniesienia [Twojej dzierżawy](../enterprise/moving-data-to-new-datacenter-geos.md) (Usługi Azure AD) do innej lokalizacji geograficznej.

## <a name="delegation-of-administration"></a>Delegowanie administracji

W większości dużych organizacji rozdzielenie obowiązków i kontroli dostępu opartej na rolach jest konieczne. Będę z wyprzedzeniem przepraszam. Nie jest to tak proste, jak niektórzy klienci chcą go mieć. Wymagania dotyczące klienta, wymogów prawnych, zgodności z przepisami i inne są różne, a czasami mogą być w konflikcie na całym świecie. Prostota i elastyczność często znajdują się po przeciwnych stronach. Nie wywołuj mnie źle. Możemy wykonać w tym celu lepszą pracę. Z czasem wprowadzono (i będzie) istotne ulepszenia. Odwiedź lokalne Centrum [technologiczne firmy Microsoft,](https://www.microsoft.com/mtc) aby omylić model, który spełnia Twoje wymagania biznesowe, bez konieczności czytania dokumentów 379230. W tym miejscu skoncentrnę się na tym, nad czym należy się zastanowić, a nie na tym, dlaczego tak jest. Poniżej przedstawiono pięć różnych obszarów, w których należy zaplanować, oraz niektóre często zadawane pytania.

### <a name="azure-ad-and-microsoft-365-admin-centers"></a>Usługi Azure AD i Microsoft 365 administracyjne

Istnieje długa i rosnąca lista [wbudowanych ról](/azure/active-directory/roles/permissions-reference). Każda rola składa się z listy pogrupowanych uprawnień ról, aby umożliwić wykonania określonych akcji. Te uprawnienia możesz zobaczyć na karcie "Opis" w obrębie poszczególnych ról. W Centrum Administracja Microsoft 365 można również zobaczyć bardziej czytelną wersję tych Administracja Microsoft 365. Definicji wbudowanych ról nie można modyfikować. Ogólnie rzecz biorąc, grupuj je w trzy kategorie:

- **Administrator globalny**: Ta bardzo zaawansowana rola powinna być [wysoce chroniona](../enterprise/protect-your-global-administrator-accounts.md) tak samo jak w innych systemach. Typowe zalecenia to: brak stałego zadania i używanie usługi Azure AD Privileged Identity Management (PIM), silne uwierzytelnianie itp. Co ciekawe, ta rola domyślnie nie umożliwia dostępu do wszystkich funkcji. Zwykle mam wątpliwości co do dostępu do zgodności z dostępem do systemu Azure, omówiony później. Jednak ta rola zawsze może przypisywać dostęp do innych usług w dzierżawie.
- **Niektórzy administratorzy usług**: Niektóre usługi (Exchange, SharePoint, Power BI itp.) mogą korzystać z ról administracyjnych wysokiego poziomu w usłudze Azure AD. Nie jest to spójne we wszystkich usługach i omówiono więcej ról specyficznych dla usługi w późniejszym czasie.
- **Funkcje**: istnieje długa (i rosnąca) lista ról skupionych na określonych działaniach (osoby zapraszającej gościa itp.). Okresowo więcej z nich jest dodawanych w zależności od potrzeb klientów.

Nie można delegować wszystkich (chociaż przerwa maleje), co oznacza, że rola administratora globalnego musi być używana czasami. Należy rozważyć konfigurację zgodnie z kodem i automatyzacją zamiast członkostwa w tej roli przez osoby.

**Uwaga**: centrum administracyjne platformy Microsoft 365 ma bardziej przyjazny interfejs użytkownika, ale podzbiór możliwości w porównaniu z interfejsem administratora usługi Azure AD. Oba portale używają tych samych ról usługi Azure AD, więc zmiany występują w tym samym miejscu. Porada: jeśli chcesz mieć skoncentrowany interfejs użytkownika administratora zarządzania tożsamościami bez zaśmiecania ekranu systemu Azure, użyj funkcji <https://aad.portal.azure.com>.

Co w nazwie? Nie należy zakładać przy tym nazwy roli. Język nie jest bardzo dokładnym narzędziem. Celem powinno być zdefiniowanie operacji, które muszą zostać delegowane, zanim trzeba będzie określić, jakie role są potrzebne. Dodanie kogoś do roli "Czytnik zabezpieczeń" nie powoduje, że ta osoba we wszystkim widzi ustawienia zabezpieczeń.

Możliwość tworzenia ról [niestandardowych to](/azure/active-directory/users-groups-roles/roles-custom-overview) typowe pytanie. Ta liczba jest obecnie ograniczona w usłudze Azure AD (patrz poniżej), ale z czasem będzie się rozrastać. Są one stosowane do funkcji w usłudze Azure AD i mogą nie obejmować "w dół" modelu hierarchii (co omówiono powyżej). Gdy będę zajmować się "niestandardowym", zwykle wracam do głównego podmiotu — "prostszy jest lepszy".

Innym najczęstszym pytaniem jest możliwość korzystania z zakresów ról do podzbioru katalogu. Przykładem może być przykład "Administrator pomocy technicznej tylko w UE". [Do tych celów](/azure/active-directory/users-groups-roles/directory-administrative-units) mają zostać przeznaczone jednostki administracyjne. Tak jak powyżej, są one stosowane do funkcji w usłudze Azure AD i mogą nie obejmować w dół. Oczywiście pewne role nie mają sensu w zakresie (administratorzy globalni, administratorzy usług itp.).

Obecnie wszystkie te role wymagają bezpośredniego członkostwa (lub dynamicznego przypisywania, jeśli używasz usługi [Azure AD PIM](/azure/active-directory/privileged-identity-management/)). Oznacza to, że klienci muszą nimi zarządzać bezpośrednio w usłudze Azure AD i nie mogą być oparte na członkostwie w grupach zabezpieczeń. Nie jestem fanem tworzenia skryptów do zarządzania nimi, ponieważ wymaga to uruchamiania z podwyższonym poziomem uprawnień. Ogólnie zalecamy integrację interfejsu API z systemami przetwarzania, np. ServiceNow, lub korzystanie z narzędzi do zarządzania partnerami, takich jak Saviynt. Z czasem trwają prace inżynierskie nad jego rozwiązaniami.

Kilka razy wspomniano o [usłudze Azure AD PIM](/azure/active-directory/privileged-identity-management/) . Istnieje odpowiednie rozwiązanie Microsoft Identity Manager (MIM) [Privileged Access Management](/microsoft-identity-manager/pam/privileged-identity-management-for-active-directory-domain-services) (PAM) dla kontrolek lokalnych. Warto również przyjrzeć się stacjom roboczym programu [Access](/windows-server/identity/securing-privileged-access/privileged-access-workstations) z uprawnieniami (PAWs) i zarządzaniu [tożsamościami usługi Azure AD](/azure/active-directory/governance/identity-governance-overview). Dostępne są również różne narzędzia innych firm, które umożliwiają włączanie just-in-time, just-enough i dynamiczne podwyższenie roli. Jest to zazwyczaj część szerszej dyskusji na temat zabezpieczania środowiska.

Czasami scenariusze to dodawanie użytkownika zewnętrznego do roli (zobacz sekcję wielodostępną powyżej). To wystarczy. [B2B w usłudze Azure AD](/azure/active-directory/b2b/) to kolejny duży i zabawny temat, przez który będą przechodzić klienci, na przykład w innym artykule.

### <a name="security-and-compliance-center-scc"></a>Centrum zabezpieczeń i zgodności (SCC)

[Uprawnienia w Centrum Office 365 zabezpieczeń & to](../security/office-365-security/permissions-in-the-security-and-compliance-center.md) zbiór "grup ról", które są niezależne od ról usługi Azure AD. Może to być mylące, ponieważ niektóre z tych grup ról mają taką samą nazwę jak role usługi Azure AD (na przykład Czytnik zabezpieczeń), ale mogą mieć różne członkostwo. Wolę używać ról w usłudze Azure AD. Każda grupa ról składa się z co najmniej jednej "ról" (zobacz co mam na myśli o ponownej użyciu tego samego wyrazu?) i że mają członków z usługi Azure AD, które są obiektami z włączoną obsługą poczty e-mail. Ponadto można utworzyć grupę ról o takiej samej nazwie jak rola, która może lub nie może zawierać tej roli (uniknąć takich nieporozumień).

To poniekąd nowy model grup Exchange ról. Jednak Exchange Online ma własny [interfejs zarządzania grupą](/exchange/permissions-exo) ról. Niektóre grupy ról w usłudze Exchange Online są blokowane i zarządzane z usługi Azure AD lub Centrum zgodności usługi Security &, ale inne mogą mieć takie same lub podobne nazwy i są zarządzane w usłudze Exchange Online (co dodaje do nieporozumień). Zaleca się unikanie korzystania z Exchange Online użytkownika, jeśli nie potrzebujesz zakresów zarządzania Exchange projektu.

Nie można tworzyć ról niestandardowych. Role są definiowane przez usługi utworzone przez firmę Microsoft i będą się rozrastać wraz z wprowadzeniem nowych usług. Jest to podobne w pojęciu do [ról zdefiniowanych przez aplikacje w](/azure/active-directory/develop/howto-add-app-roles-in-azure-ad-apps) usłudze Azure AD. Po włączeniu nowych usług często trzeba utworzyć nowe grupy ról, aby udzielić im dostępu lub udzielić do nich pełnomocmocu (na przykład do zarządzania [ryzykiem w ramach niejawnego programu testów](../compliance/insider-risk-management-configure.md)).

Te grupy ról wymagają również bezpośredniego członkostwa i nie mogą zawierać grup usługi Azure AD. Niestety obecnie te grupy ról nie są obsługiwane przez funkcję zarządzania pim w usłudze Azure AD. Podobnie jak role w usłudze Azure AD, zwykle zalecam zarządzanie nimi za pośrednictwem interfejsów API lub produktu do zarządzania partnerami, takiego jak Saviynt lub inne.

Role & zabezpieczeń obejmują Microsoft 365 i nie można określić zakresu tych grup ról do podzestawu środowiska (tak jak w przypadku jednostek administracyjnych w usłudze Azure AD). Wielu klientów pyta, jak mogą do nich podlać. Na przykład "utwórz zasady DLP tylko dla użytkowników w UE". Obecnie, jeśli masz prawa do określonej funkcji w Centrum & zabezpieczeń, masz prawa do wszystkich funkcji objętych tą funkcją w dzierżawie. Jednak wiele zasad umożliwia kierowanie podzestawu środowiska (na przykład "udostępnij te etykiety tylko [](../compliance/create-sensitivity-labels.md#publish-sensitivity-labels-by-creating-a-label-policy) tym użytkownikom"). Właściwe zarządzanie i komunikacja są kluczowym elementem w celu uniknięcia konfliktów. Niektórzy klienci wdrażają podejście "konfiguracji jako kod" w celu rozwiązania pewnych poddelegacji w Centrum zabezpieczeń & zgodności. Niektóre określone usługi obsługują subdelegację (patrz poniżej).

Warto zauważyć, że mechanizmy kontroli zarządzane obecnie za pośrednictwem Centrum zabezpieczeń & zgodności (protection.office.com) są w trakcie migrowania do dwóch osobnych portali aadministracyjnym: security.microsoft.com i compliance.microsoft.com. Zmiana jest jedyną stałą!

### <a name="service-specific"></a>Specyficzne dla usługi

Jak wspomniano wcześniej, wielu klientów chce uzyskać bardziej szczegółowy model delegowania. Przykład często: "Zarządzanie usługą XYZ tylko dla użytkowników i lokalizacji w działze X" (lub w innym wymiarze). Możliwość wykonywania tej pracy zależy od każdej usługi i jest spójna we wszystkich usługach i możliwościach. Ponadto każda usługa może mieć osobny i unikatowy model RBAC. Zamiast omawiać wszystkie te działania (zajmie to wieki) dodaję odpowiednie linki do każdej usługi. Nie jest to pełna lista, ale to dopiero początek.

- **Exchange Online** - (/exchange/permissions-exo/permissions-exo)
- **SharePoint Online** — (/sharepoint/manage-site-collection-administrators)
- **Microsoft Teams** - (/microsoftteams/itadmin-readiness)
- **zbierania elektronicznych materiałów dowodowych** — (.. /compliance/index.yml)
  - **Filtrowanie uprawnień** — (.. /compliance/index.yml)
  - **Granice zgodności** — (.. /compliance/set-up-compliance-boundaries.md)
  - **Advanced eDiscovery** - (.. /compliance/overview-ediscovery-20.md)
- **Yammer** - (/yammer/manage-yammer-users/manage-yammer-admins)
- **Multi-geo** - (.. /enterprise/add-a-sharepoint-geo-admin.md)
- **Dynamics 365** — (/dynamics365/)

  Uwaga: ten link znajduje się w katalogu głównym dokumentacji. Istnieje wiele typów usług z odmianami w modelu administratora/delegowania.

- **Power Platform** — (/power-platform/admin/admin-documentation)
  - **Power Apps** - (/power-platform/admin/wp-security)

    Uwaga: istnieje wiele typów z odmianami w modelach administratora/delegowania.

  - **Power Automate** - (/power-automate/environments-overview-admin)
  - **Power BI** — (/power-bi/service-admin-governance)

    Uwaga: zabezpieczenia i delegowanie platformy danych (Power BI to składnik) to złożony obszar.

- **MEM/Intune** — (/mem/intune/fundamentals/role-based-access-control)
- **Microsoft Defender for Endpoint** - (/windows/security/threat-protection/microsoft-defender-atp/user-roles)
- **Microsoft 365 Defender** - (.. /security/defender/m365d-permissions.md)
- **Program Microsoft Defender dla aplikacji w chmurze** — (/cloud-app-security/manage-admins)
- **Stream** — (/stream/assign-administrator-user-role)
- **Bariery informacyjne** — (.. /compliance/information-barriers.md)

### <a name="activity-logs"></a>Dzienniki aktywności

Office 365 [ujednolicony dziennik inspekcji](../compliance/search-the-audit-log-in-security-and-compliance.md). Jest to bardzo [szczegółowy dziennik](/office/office-365-management-api/office-365-management-activity-api-schema), ale jego nazwa nie jest zbyt przeczytana. Może ona nie zawierać wszystkiego, czego potrzebujesz lub czego potrzebujesz ze względów bezpieczeństwa i zgodności. Ponadto niektórzy klienci są naprawdę zainteresowani [inspekcją zaawansowaną](../compliance/advanced-audit.md).

Oto przykłady Microsoft 365, do których dostęp uzyskuje się za pośrednictwem innych interfejsów API:

- [Azure AD](/azure/azure-monitor/platform/diagnostic-settings) (działania nie związane z usługą Office 365)
- [Exchange śledzenia wiadomości](/powershell/module/exchange/get-messagetrace)
- Systemy zagrożeń/UEBA omówione powyżej (na przykład usługa Azure AD Identity Protection, program Microsoft Defender dla aplikacji w chmurze, program Microsoft Defender for Endpoint i tak dalej)
- [ochrona informacji firmy Microsoft](../compliance/data-classification-activity-explorer.md)
- [Ochrona punktu końcowego w usłudze Microsoft Defender](/windows/security/threat-protection/microsoft-defender-atp/api-power-bi)
- [Microsoft Graph](https://graph.microsoft.com)

Ważne jest, aby najpierw zidentyfikować wszystkie źródła dziennika potrzebne na potrzeby programu zabezpieczeń i zgodności. Należy również pamiętać, że różne dzienniki mają różne limity przechowywania online.

Z perspektywy delegowania administratora większość Microsoft 365 aktywności nie ma wbudowanego modelu RBAC. Jeśli masz uprawnienia do zobaczenia dziennika, możesz zobaczyć w nim wszystko. Typowe przykładowe wymaganie klienta to: "Chcę mieć możliwość wykonywania zapytań tylko dla użytkowników w UE" (lub w innym wymiarze). Aby osiągnąć to wymaganie, musimy przenieść dzienniki do innej usługi. W chmurze firmy Microsoft zalecamy przeniesienie jej do usługi [Microsoft Sentinel](/azure/sentinel/overview) lub [Log Analytics](/azure/azure-monitor/learn/quick-create-workspace).

Diagram wysokiego poziomu:

![diagram źródeł dziennika dla programu zabezpieczeń i zgodności.](../media/solutions-architecture-center/identity-beyond-illustration-4.png)

Powyższy diagram przedstawia wbudowane możliwości wysyłania dzienników do Centrum zdarzeń i/lub usługi Azure Storage i/lub Azure Log Analytics. Nie wszystkie systemy zawierają jeszcze tę od  pudełku. Istnieją jednak inne metody wysyłania tych dzienników do tego samego repozytorium. Na przykład zobacz [Chronienie Teams za pomocą programu Microsoft Sentinel](https://techcommunity.microsoft.com/t5/azure-sentinel/protecting-your-teams-with-azure-sentinel/ba-p/1265761).

Połączenie wszystkich dzienników w jedną lokalizację przechowywania obejmuje dodatkowe korzyści, takie jak korelacje krzyżowe, niestandardowe godziny przechowywania, wzbogacanie o dane potrzebne do obsługi modelu RBAC itp. Po przechowanie danych w tym systemie magazynu można utworzyć pulpit Power BI nawigacyjny (lub inny typ wizualizacji) z odpowiednim modelem RBAC.

Dzienniki nie muszą być kierowane tylko do jednego miejsca. Korzystne może być również zintegrowanie dzienników Office 365 z usługą [Microsoft Defender for Cloud Apps](/cloud-app-security/connect-office-365-to-microsoft-cloud-app-security) lub niestandardowym modelem RBAC w [programie Power BI](../admin/usage-analytics/usage-analytics.md). Różne repozytoria mają różne korzyści i różne grupy odbiorców.

Warto wspomnieć, że w usłudze o nazwie "Microsoft 365 Defender" istnieje bardzo bogaty wbudowany system analityczny do obsługi zabezpieczeń, zagrożeń, luk i tak [Microsoft 365 Defender](../security/defender/microsoft-365-defender.md).

Wielu dużych klientów chce przenieść te dane dziennika do systemu innej firmy (na przykład SIEM). Istnieją różne metody, ale ogólnie rzecz biorąc, Centrum zdarzeń [Azure](/azure/azure-monitor/platform/stream-monitoring-data-event-hubs) [i](/graph/security-integration) Graph dobry punkt wyjścia.

### <a name="azure"></a>Azure

Często pojawia się pytanie, czy istnieje sposób rozdzielenia ról o wysokich uprawnieniach między usługami Azure AD, Azure i SaaS (np.: administrator globalny usługi Office 365 ale nie platformy Azure).  Nie naprawdę.  Architektura wielodostępna jest wymagana, jeśli wymagane jest pełne rozdzielenie administracyjne, ale powoduje to znaczącą [złożoność](https://aka.ms/multi-tenant-user) (patrz wyżej). Wszystkie te usługi są częścią tej samej granicy zabezpieczeń/tożsamości (spójrz na model hierarchii powyżej).

Ważne jest zrozumienie relacji między różnymi usługami w tej samej dzierżawie. Współpracują z wieloma klientami, którzy pracują nad rozwiązaniami biznesowymi, które obejmują platformy Azure, Office 365 i Power Platform (a także często usługi lokalne oraz usługi w chmurze innych firm). Jednym z typowych przykładów:

1. Chcę współpracować nad zestawem dokumentów/obrazów/itp. (Office 365)
2. Wyślij każdy z nich w ramach procesu zatwierdzania (Power Platform)
3. Po zatwierdzeniu wszystkich składników połącz je w ujednolicony interfejs [API microsoft Graph microsoft Graph](/azure/active-directory/develop/microsoft-graph-intro).  Nie jest to niemożliwe, ale znacznie bardziej złożone w celu zaprojektowania rozwiązania obejmującego [wiele dzierżaw](/azure/active-directory/develop/single-and-multi-tenant-apps).

Kontrola dostępu Role-Based Azure umożliwia zarządzanie dostępem precyzyjnie na platformie Azure. Za pomocą RBAC możesz zarządzać dostępem do zasobów, przysłając użytkownikom jak najmniej uprawnień potrzebnych do wykonywania ich zadań. Szczegóły tego dokumentu nie są już dostępne, ale aby uzyskać więcej informacji na temat RBAC, zobacz Co to jest kontrola dostępu oparta na rolach [(RBAC, role based access control) na platformie Azure?](/azure/role-based-access-control/overview) RBAC jest ważny, ale tylko stanowi część kwestii dotyczących zarządzania dla platformy Azure. [Cloud Adoption Framework](/azure/cloud-adoption-framework/govern/) to doskonały punkt wyjścia, aby dowiedzieć się więcej. Podoba mi się mój [znajomy, Andres Wienet](https://www.linkedin.com/in/andres-ravinet/), który krok po kroku przechadzę się po klientach, jednak poszczególne składniki decydują o tym. Widok wysokiego poziomu dla różnych elementów (nie tak dobry jak proces tworzenia rzeczywistego modelu klienta) wygląda tak:

![High-level view of Azure components for delegated administration.](../media/solutions-architecture-center/identity-beyond-illustration-5.png)

Jak widać na powyższym obrazie, w ramach projektu należy rozważyć wiele innych usług (np.: Zasady [platformy Azure](/azure/governance/policy/overview), Plany platformy [Azure](/azure/governance/blueprints/overview)[, grupy](/azure/governance/management-groups/) zarządzania itp.).

## <a name="conclusion"></a>Wnioski

Rozpoczęte jako krótkie podsumowanie, zakończone dłużej, niż oczekiwano.  Mam nadzieję, że teraz możesz uzyskać szczegółowe informacje na temat tworzenia modelu delegowania dla Twojej organizacji.  Ta konwersacja jest bardzo wspólna dla klientów. Nie istnieje jeden model, który działa dla wszystkich. Oczekiwanie na kilka planowanych ulepszeń od inżynierów firmy Microsoft przed dokumentowaniem typowych wzorców, które widzimy u klientów. W międzyczasie możesz współpracować ze swoim zespołem ds. konta Microsoft, aby zorganizować wizyty w najbliższym Centrum [technologii firmy Microsoft](https://www.microsoft.com/mtc).  Do zobaczenia!
