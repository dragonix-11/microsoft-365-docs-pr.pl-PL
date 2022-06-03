---
title: Konfigurowanie dzierżawy platformy Microsoft 365 w celu zwiększenia bezpieczeństwa
f1.keywords:
- NOCSH
ms.author: bcarter
author: BrendaCarter
manager: laurawi
ms.date: 04/06/2022
audience: ITPro
ms.topic: article
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- Strat_O365_IP
- M365-security-compliance
search.appverid: MET150
ms.assetid: 8d274fe3-db51-4107-ba64-865e7155b355
ms.custom:
- seo-marvel-apr2020
- admindeeplinkSPO
description: W tym temacie przedstawiono zalecaną konfigurację ustawień dla całej dzierżawy, które mają wpływ na bezpieczeństwo środowiska Microsoft 365.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: a1a9b7e6a006eb63078f237ce1078d6aa825fa14
ms.sourcegitcommit: 35f167725bec5fd4fe131781a53d96b060cf232d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/03/2022
ms.locfileid: "65872368"
---
# <a name="configure-your-microsoft-365-tenant-for-increased-security"></a>Konfigurowanie dzierżawy platformy Microsoft 365 w celu zwiększenia bezpieczeństwa

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Usługi Microsoft Defender dla usługi Office 365 (plan 1 i plan 2)](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

W tym temacie przedstawiono zalecaną konfigurację ustawień dla całej dzierżawy, które mają wpływ na bezpieczeństwo środowiska Microsoft 365. Twoje potrzeby w zakresie zabezpieczeń mogą wymagać większej lub mniejszej liczby zabezpieczeń. Użyj tych zaleceń jako punktu początkowego.

## <a name="check-office-365-secure-score"></a>Sprawdzanie Office 365 wskaźnika bezpieczeństwa

Office 365 Wskaźnik bezpieczeństwa analizuje zabezpieczenia organizacji na podstawie zwykłych działań i ustawień zabezpieczeń oraz przypisuje ocenę. Zacznij od zanotowania bieżącego wyniku. Dostosowanie niektórych ustawień dla całej dzierżawy spowoduje zwiększenie oceny. Celem nie jest osiągnięcie maksymalnego wyniku, ale świadomość możliwości ochrony środowiska, które nie wpływają negatywnie na produktywność użytkowników. Zobacz [Wskaźnik bezpieczeństwa firmy Microsoft](../defender/microsoft-secure-score.md).

## <a name="tune-threat-management-policies-in-the-microsoft-365-defender-portal"></a>Dostrajanie zasad zarządzania zagrożeniami w portalu Microsoft 365 Defender

Portal Microsoft 365 Defender zawiera funkcje, które chronią środowisko. Zawiera również raporty i pulpity nawigacyjne, których można używać do monitorowania i podejmowania działań. Niektóre obszary mają domyślne konfiguracje zasad. Niektóre obszary nie zawierają domyślnych zasad ani reguł. Odwiedź te zasady w obszarze **Zasady współpracy** \> & poczty e-mail **& reguły** \> **zagrożeń** , aby dostosować ustawienia zarządzania zagrożeniami w bezpieczniejszym środowisku.

|Obszar|Domyślne zasady?|Zalecenie|
|---|---|---|
|**Ochrona przed wyłudzaniem informacji**|Tak|Skonfiguruj domyślne zasady ochrony przed wyłudzaniem informacji zgodnie z opisem tutaj: [Konfigurowanie ustawień ochrony przed wyłudzaniem informacji w ramach operacji EOP i Ochrona usługi Office 365 w usłudze Defender](protect-against-threats.md#part-2---anti-phishing-protection-in-eop-and-defender-for-office-365). <p> Więcej informacji: <ul><li>[Zasady ochrony przed wyłudzaniem informacji w Microsoft 365](set-up-anti-phishing-policies.md)</li><li>[Zalecane ustawienia zasad ochrony przed wyłudzaniem informacji w Ochrona usługi Office 365 w usłudze Microsoft Defender](recommended-settings-for-eop-and-office365.md#anti-phishing-policy-settings-in-microsoft-defender-for-office-365)</li><li> [Szczegółowe informacje o podszywaniu się](impersonation-insight.md)</li><li>[Fałszowanie szczegółowych informacji wywiadowczych w ramach EOP](learn-about-spoof-intelligence.md)</li><li>[Zarządzaj listą dozwolonych/zablokowanych dzierżaw](tenant-allow-block-list.md).</li></ul>|
|**Aparat chroniący przed złośliwym oprogramowaniem**|Tak|Skonfiguruj domyślne zasady ochrony przed złośliwym oprogramowaniem zgodnie z opisem tutaj: [Konfigurowanie ustawień ochrony przed złośliwym oprogramowaniem w usłudze EOP](protect-against-threats.md#part-1---anti-malware-protection-in-eop). <p> Więcej informacji: <ul><li>[Ochrona przed złośliwym oprogramowaniem](anti-malware-protection.md)</li><li>[Zalecane ustawienia zasad ochrony przed złośliwym oprogramowaniem](recommended-settings-for-eop-and-office365.md#eop-anti-malware-policy-settings)</li><li>[Konfigurowanie zasad ochrony przed złośliwym oprogramowaniem](configure-anti-malware-policies.md)</li></ul>|
|**Bezpieczne załączniki w usłudze Defender dla Office 365**|Nie|Skonfiguruj ustawienia globalne dla załączników Sejf i utwórz zasady załączników Sejf zgodnie z opisem poniżej: [Konfigurowanie ustawień załączników Sejf w Ochrona usługi Office 365 w usłudze Microsoft Defender](protect-against-threats.md#safe-attachments-policies-in-microsoft-defender-for-office-365). <p> Więcej informacji: <ul><li>[Zalecane ustawienia załączników Sejf](recommended-settings-for-eop-and-office365.md#safe-attachments-settings)</li><li>[Sejf załączników w Ochrona usługi Office 365 w usłudze Microsoft Defender](safe-attachments.md)</li><li>[Konfigurowanie zasad załączników Sejf](set-up-safe-attachments-policies.md)</li><li>[Bezpieczne załączniki dla programu SharePoint, usługi OneDrive i aplikacji Microsoft Teams](mdo-for-spo-odb-and-teams.md)</li><li>[Bezpieczne dokumenty w usłudze Microsoft 365 E5](safe-docs.md)</li></ul>|
|**linki Sejf w Ochrona usługi Office 365 w usłudze Microsoft Defender**|Nie|Skonfiguruj ustawienia globalne dla linków Sejf i utwórz zasady linków Sejf zgodnie z opisem w tym miejscu: [Konfigurowanie ustawień linków Sejf w Ochrona usługi Office 365 w usłudze Microsoft Defender](protect-against-threats.md#safe-links-policies-in-microsoft-defender-for-office-365). <p> Więcej informacji: <ul><li>[Zalecane ustawienia linków Sejf](recommended-settings-for-eop-and-office365.md#safe-links-settings)</li><li>[Konfigurowanie zasad linków Sejf](set-up-safe-links-policies.md)</li><li>[linki Sejf w Ochrona usługi Office 365 w usłudze Microsoft Defender](safe-links.md)</li><li>[Konfigurowanie ustawień globalnych dla linków Sejf w Ochrona usługi Office 365 w usłudze Microsoft Defender](configure-global-settings-for-safe-links.md)</li></ul>|
|**Ochrona przed spamem (filtrowanie poczty)**|Tak|Skonfiguruj domyślne zasady ochrony przed spamem zgodnie z opisem tutaj: [Konfigurowanie ustawień ochrony przed spamem w usłudze EOP](protect-against-threats.md#part-3---anti-spam-protection-in-eop) <p> Więcej informacji: <ul><li>[Zalecane ustawienia zasad ochrony przed spamem](recommended-settings-for-eop-and-office365.md#eop-anti-spam-policy-settings)</li><li>[Ochrona przed spamem w ramach EOP](anti-spam-protection.md)</li><li>[Konfigurowanie zasad ochrony przed spamem w ramach EOP](configure-your-spam-filter-policies.md)</li></ul>|
|***Uwierzytelnianie za pomocą poczty e-***|Tak|Uwierzytelnianie poczty e-mail używa rekordów DNS do dodawania weryfikowalnych informacji do wiadomości e-mail dotyczących źródła wiadomości i nadawcy. Microsoft 365 automatycznie konfiguruje uwierzytelnianie poczty e-mail dla domeny domyślnej (onmicrosoft.com), ale administratorzy Microsoft 365 mogą również skonfigurować uwierzytelnianie poczty e-mail dla domen niestandardowych. Używane są trzy metody uwierzytelniania: <ul><li>Struktura zasad nadawcy (lub SPF).</li><ul><li>Aby uzyskać informacje o konfiguracji, zobacz [Konfigurowanie SPF w Microsoft 365, aby zapobiec fałszowaniu](set-up-spf-in-office-365-to-help-prevent-spoofing.md).</li></ul> <li>DomainKeys Identified Mail (DKIM).</li><ul><li>Zobacz [Używanie modułu DKIM do weryfikowania wychodzących wiadomości e-mail wysyłanych z domeny niestandardowej](use-dkim-to-validate-outbound-email.md).</li><li>Po skonfigurowaniu modułu DKIM włącz go w portalu Microsoft 365 Defender.</li></ul><li>Uwierzytelnianie, raportowanie i zgodność komunikatów oparte na domenie (DMARC).</li><ul><li>W przypadku konfiguracji DMARC [użyj funkcji DMARC, aby zweryfikować pocztę e-mail w Microsoft 365](use-dmarc-to-validate-email.md).</li></ul></ul>|

> [!NOTE]
> W przypadku niestandardowych wdrożeń SPF, wdrożeń hybrydowych i rozwiązywania problemów: [Jak Microsoft 365 używa struktury zasad nadawcy (SPF), aby zapobiec fałszowaniu](how-office-365-uses-spf-to-prevent-spoofing.md).

## <a name="view-dashboards-and-reports-in-the-microsoft-365-defender-portal"></a>Wyświetlanie pulpitów nawigacyjnych i raportów w portalu Microsoft 365 Defender

Odwiedź te raporty i pulpity nawigacyjne, aby dowiedzieć się więcej o kondycji środowiska. Dane w tych raportach staną się bardziej rozbudowane, ponieważ organizacja korzysta z usług Office 365. Na razie zapoznaj się z tym, co można monitorować i podejmować działania.

|Pulpit nawigacyjny|Opis|
|---|---|
|Raporty zabezpieczeń poczty e-mail|Te raporty są dostępne w Exchange Online Protection. Aby uzyskać więcej informacji, zobacz [Wyświetlanie raportów zabezpieczeń poczty e-mail w portalu Microsoft 365 Defender](view-email-security-reports.md).|
|raporty Ochrona usługi Office 365 w usłudze Defender|Raporty są dostępne tylko w Ochrona usługi Office 365 w usłudze Defender. Aby uzyskać więcej informacji, zobacz [Wyświetlanie raportów Ochrona usługi Office 365 w usłudze Defender w portalu Microsoft 365 Defender](view-reports-for-mdo.md).|
|Raporty i szczegółowe informacje dotyczące przepływu poczty|Te raporty i szczegółowe informacje są dostępne w centrum administracyjnym Exchange (EAC). Aby uzyskać więcej informacji, zobacz [Raporty przepływu poczty](/exchange/monitoring/mail-flow-reports/mail-flow-reports) i [Szczegółowe informacje o przepływie poczty](/exchange/monitoring/mail-flow-insights/mail-flow-insights).|
|[Eksplorator zagrożeń (lub wykrywanie w czasie rzeczywistym)](threat-explorer.md)|Jeśli badasz lub doświadczasz ataku na dzierżawę, użyj Eksploratora (lub wykrywania w czasie rzeczywistym) do analizowania zagrożeń. Eksplorator (i raport wykrywania w czasie rzeczywistym) pokazuje liczbę ataków w czasie i można analizować te dane według rodzin zagrożeń, infrastruktury atakującej i innych. Możesz również oznaczyć dowolną podejrzaną wiadomość e-mail dla listy zdarzeń.|

## <a name="configure-additional-exchange-online-tenant-wide-settings"></a>Konfigurowanie dodatkowych ustawień Exchange Online całej dzierżawy

Poniżej przedstawiono kilka dodatkowych ustawień, które są zalecane.

|Obszar|Zalecenie|
|---|---|
|**Reguły przepływu poczty** (nazywane również regułami transportu)|Dodaj regułę przepływu poczty, aby chronić przed oprogramowaniem wymuszającym okup, blokując typy plików wykonywalnych i Office typy plików zawierające makra. Aby uzyskać więcej informacji, zobacz [Używanie reguł przepływu poczty do sprawdzania załączników wiadomości w Exchange Online](/exchange/security-and-compliance/mail-flow-rules/inspect-message-attachments). <p> Zapoznaj się z tymi dodatkowymi tematami: <ul><li>[Ochrona przed oprogramowaniem wymuszającym okup](../../admin/security-and-compliance/secure-your-business-data.md)</li><li>[Złośliwe oprogramowanie i ochrona przed oprogramowaniem wymuszającym okup w Microsoft 365](/compliance/assurance/assurance-malware-and-ransomware-protection)</li><li>[Odzyskiwanie po ataku wymuszającym okup w Office 365](recover-from-ransomware.md)</li></ul> <p> Utwórz regułę przepływu poczty, aby uniemożliwić automatyczne przekazywanie wiadomości e-mail do domen zewnętrznych. Aby uzyskać więcej informacji, zobacz [Mitigating Client External Forwarding Rules with Secure Score (Ograniczanie reguł przekazywania zewnętrznego klienta przy użyciu wskaźnika bezpieczeństwa](/archive/blogs/office365security/mitigating-client-external-forwarding-rules-with-secure-score)). <p> Więcej informacji: [Reguły przepływu poczty (reguły transportu) w Exchange Online](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rules)|
|**Nowoczesne uwierzytelnianie**|Nowoczesne uwierzytelnianie jest wymaganie wstępne do korzystania z uwierzytelniania wieloskładnikowego (MFA). Uwierzytelnianie wieloskładnikowe jest zalecane do zabezpieczania dostępu do zasobów w chmurze, w tym poczty e-mail. <p> Zobacz następujące tematy: <ul><li>[Włączanie lub wyłączanie nowoczesnego uwierzytelniania w Exchange Online](/Exchange/clients-and-mobile-in-exchange-online/enable-or-disable-modern-authentication-in-exchange-online)</li><li>[Skype dla firm Online: włączanie dzierżawy na potrzeby nowoczesnego uwierzytelniania](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx)</li></ul> <p> Nowoczesne uwierzytelnianie jest domyślnie włączone dla klientów Office 2016, SharePoint Online i OneDrive dla Firm. <p> Więcej informacji: [Jak działa nowoczesne uwierzytelnianie dla aplikacji klienckich Office 2013 i Office 2016](../../enterprise/modern-auth-for-office-2013-and-2016.md)|

## <a name="configure-tenant-wide-sharing-policies-in-sharepoint-admin-center"></a>Konfigurowanie zasad udostępniania dla całej dzierżawy w centrum administracyjnym SharePoint

Zalecenia firmy Microsoft dotyczące konfigurowania witryn zespołów SharePoint na coraz większym poziomie ochrony, począwszy od ochrony punktu odniesienia. Aby uzyskać więcej informacji, zobacz [Zalecenia dotyczące zasad dotyczące zabezpieczania witryn i plików SharePoint](sharepoint-file-access-policies.md).

SharePoint witryny zespołu skonfigurowane na poziomie punktu odniesienia zezwalają na udostępnianie plików użytkownikom zewnętrznym przy użyciu linków dostępu anonimowego. To podejście jest zalecane zamiast wysyłania plików w wiadomości e-mail.

Aby zapewnić obsługę celów ochrony punktu odniesienia, skonfiguruj zasady udostępniania dla całej dzierżawy zgodnie z zaleceniami w tym miejscu. Ustawienia udostępniania dla poszczególnych witryn mogą być bardziej restrykcyjne niż te zasady dla całej dzierżawy, ale nie bardziej permisywne.

|Obszar|Zawiera zasady domyślne|Zalecenie|
|---|---|---|
|**Udostępnianie** (SharePoint Online i OneDrive dla Firm)|Tak|Udostępnianie zewnętrzne jest domyślnie włączone. Zalecane są następujące ustawienia: <ul><li>Zezwalaj na udostępnianie uwierzytelnionym użytkownikom zewnętrznym i używanie linków dostępu anonimowego (ustawienie domyślne).</li><li>Linki dostępu anonimowego wygasają w ciągu tylu dni. Wprowadź liczbę, jeśli jest to wymagane, na przykład 30 dni.</li><li>Domyślny typ łącza — wybierz pozycję Wewnętrzne (tylko osoby w organizacji). Użytkownicy, którzy chcą udostępniać za pomocą linków anonimowych, muszą wybrać tę opcję z menu udostępniania.</li></ul> <p> Więcej informacji: [Omówienie udostępniania zewnętrznego](/sharepoint/external-sharing-overview)|

SharePoint centrum administracyjne i centrum administracyjne OneDrive dla Firm zawierają te same ustawienia. Ustawienia w obu centrum administracyjnym mają zastosowanie do obu tych ustawień.

## <a name="configure-settings-in-azure-active-directory"></a>Konfigurowanie ustawień w Azure Active Directory

Pamiętaj, aby odwiedzić te dwa obszary w Azure Active Directory, aby ukończyć konfigurację dla całej dzierżawy dla bezpieczniejszych środowisk.

### <a name="configure-named-locations-under-conditional-access"></a>Konfigurowanie nazwanych lokalizacji (w obszarze dostępu warunkowego)

Jeśli Twoja organizacja obejmuje biura z bezpiecznym dostępem do sieci, dodaj zakresy zaufanych adresów IP, aby Azure Active Directory jako nazwane lokalizacje. Ta funkcja pomaga zmniejszyć liczbę zgłoszonych wyników fałszywie dodatnich w przypadku zdarzeń ryzyka logowania.

Zobacz: [Nazwane lokalizacje w Azure Active Directory](/azure/active-directory/conditional-access/location-condition)

### <a name="block-apps-that-dont-support-modern-authentication"></a>Blokuj aplikacje, które nie obsługują nowoczesnego uwierzytelniania

Uwierzytelnianie wieloskładnikowe wymaga aplikacji, które obsługują nowoczesne uwierzytelnianie. Aplikacje, które nie obsługują nowoczesnego uwierzytelniania, nie mogą być blokowane przy użyciu reguł dostępu warunkowego.

W przypadku bezpiecznych środowisk należy wyłączyć uwierzytelnianie dla aplikacji, które nie obsługują nowoczesnego uwierzytelniania. Można to zrobić w Azure Active Directory za pomocą kontrolki, która wkrótce się pojawi.

W międzyczasie użyj jednej z następujących metod, aby to zrobić dla SharePoint Online i OneDrive dla Firm:

- Użyj programu PowerShell, zobacz [Blokuj aplikacje, które nie korzystają z nowoczesnego uwierzytelniania](/mem/intune/protect/app-modern-authentication-block).
- Skonfiguruj to w <a href="https://go.microsoft.com/fwlink/?linkid=2185219" target="_blank">centrum administracyjnym SharePoint</a> na stronie "dostęp do urządzenia" — "Kontrolowanie dostępu z aplikacji, które nie korzystają z nowoczesnego uwierzytelniania". Wybierz pozycję Blokuj.

## <a name="get-started-with-defender-for-cloud-apps-or-office-365-cloud-app-security"></a>Wprowadzenie z aplikacjami Defender dla Chmury lub Office 365 Cloud App Security

Użyj Office 365 Cloud App Security, aby ocenić ryzyko, otrzymywać alerty dotyczące podejrzanych działań i automatycznie podejmować działania. Wymaga planu Office 365 E5.

Możesz też użyć Microsoft Defender for Cloud Apps, aby uzyskać lepszy wgląd nawet po udzieleniu dostępu, kompleksowej kontroli i ulepszonej ochronie wszystkich aplikacji w chmurze, w tym Office 365.

Ponieważ to rozwiązanie zaleca plan EMS E5, zalecamy rozpoczęcie od Defender dla Chmury Apps, aby można było go używać z innymi aplikacjami SaaS w środowisku. Zacznij od domyślnych zasad i ustawień.

Więcej informacji:

- [Wdrażanie aplikacji Defender dla Chmury](/cloud-app-security/getting-started-with-cloud-app-security)
- [Więcej informacji o Microsoft Defender for Cloud Apps](https://www.microsoft.com/cloud-platform/cloud-app-security)
- [Co to jest Defender dla Chmury Apps?](/cloud-app-security/what-is-cloud-app-security)

:::image type="content" source="../../media/1fb2aa65-54b8-4746-9f5e-c187d339e9f5.png" alt-text="Pulpit nawigacyjny aplikacji Defender dla Chmury" lightbox="../../media/1fb2aa65-54b8-4746-9f5e-c187d339e9f5.png":::

## <a name="additional-resources"></a>Dodatkowe materiały

Te artykuły i przewodniki zawierają dodatkowe opisowe informacje dotyczące zabezpieczania środowiska Microsoft 365:

- [Wskazówki dotyczące zabezpieczeń firmy Microsoft dotyczące kampanii politycznych, organizacji non-profit i innych zwinnych organizacji](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md) (można użyć tych zaleceń w dowolnym środowisku, zwłaszcza w środowiskach tylko w chmurze)

- [Zalecane zasady zabezpieczeń i konfiguracje dla tożsamości i urządzeń](microsoft-365-policies-configurations.md) (te zalecenia obejmują pomoc dotyczącą środowisk usług AD FS)
