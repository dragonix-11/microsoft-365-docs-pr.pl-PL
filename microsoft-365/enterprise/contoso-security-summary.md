---
title: Podsumowanie funkcji Microsoft 365 zabezpieczeń przedsiębiorstwa dla firmy Contoso Corporation
author: kelleyvice-msft
f1.keywords:
- NOCSH
ms.author: kvice
manager: laurawi
ms.date: 10/02/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- Strat_O365_Enterprise
ms.custom: ''
description: Jak firma Contoso korzysta z funkcji zabezpieczeń usługi Microsoft 365 dla przedsiębiorstw.
ms.openlocfilehash: 15fd559b6dade63d56647c8f5f3437a57d27a56b
ms.sourcegitcommit: 1ef176c79a0e6dbb51834fe30807409d4e94847c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/19/2021
ms.locfileid: "63005257"
---
# <a name="summary-of-microsoft-365-for-enterprise-security-for-the-contoso-corporation"></a>Podsumowanie funkcji Microsoft 365 zabezpieczeń przedsiębiorstwa dla firmy Contoso Corporation

Aby uzyskać zgodę na wdrożenie usługi Microsoft 365 dla przedsiębiorstw, dział zabezpieczeń IT firmy Contoso przeszł dokładny przegląd zabezpieczeń. Zidentyfikują one następujące wymagania dotyczące zabezpieczeń chmury:

- Użyj najsilniejszych metod uwierzytelniania, aby uzyskać dostęp pracownika do zasobów w chmurze.
- Upewnij się, że komputery i urządzenia przenośne łączą się z aplikacjami i uzyskaj do nich dostęp w bezpieczny sposób.
- Chroń komputery i pocztę e-mail przed złośliwym oprogramowaniem.
- Uprawnienia do zasobów cyfrowych opartych na chmurze określają, kto i jakie uprawnienia może uzyskać, oraz są zaprojektowane pod kątem dostępu o najmniejszych uprawnieniach
- Poufne i ściśle uregulowane zasoby cyfrowe są oznaczane etykietami, szyfrowane i przechowywane w bezpiecznych lokalizacjach.
- Wysoce uregulowane zasoby cyfrowe są chronione za pomocą dodatkowego szyfrowania i uprawnień.
- Pracownicy indyjscy mogą monitorować bieżącą pocztę zabezpieczeń z centralnych pulpitów nawigacyjnych i być powiadamiani o zdarzeniach zabezpieczeń w celu szybkiego reagowania i złagodzenia wpływu.

## <a name="the-contoso-path-to-microsoft-365-security-readiness"></a>Ścieżka contosoowa do Microsoft 365 zabezpieczeń

Firma Contoso wykonać poniższe kroki w celu przygotowania ich zabezpieczeń do wdrożenia usługi Microsoft 365 dla przedsiębiorstw:

1. Ograniczanie kont administratora w chmurze

   Firma Contoso przeglądała swoje istniejące konta Usługi domenowe w usłudze Active Directory administratorów (AD DS) i schowała serię dedykowanych kont i grup administratora w chmurze.

2. Klasyfikowanie danych w trzech poziomach zabezpieczeń

   Firma Contoso przemyślała i ustaliła trzy poziomy, które zostały użyte do zidentyfikowania Microsoft 365 funkcji przedsiębiorstwa w celu ochrony najcenniejszych danych.

3. Określanie zasad dostępu, przechowywania i ochrony informacji dla poziomów danych

   Na podstawie poziomów danych firma Contoso określała szczegółowe wymagania kwalifikowania przyszłych obciążeń IT przenoszonych do chmury.

Aby postępować zgodnie z najlepszymi rozwiązaniami w zakresie zabezpieczeń i Microsoft 365 w zakresie wdrażania w przedsiębiorstwie, administratorzy zabezpieczeń firmy Contoso i jego dział informatyczny wdrożyli wiele funkcji i możliwości zabezpieczeń, zgodnie z opisem w poniższych sekcjach.

## <a name="identity-and-access-management"></a>Zarządzanie tożsamością i dostępem 

- Dedykowane konta administratora globalnego z uwierzytelniania wieloskładnikowego i usługi pim

  Zamiast przypisywać rolę administratora globalnego do codziennych kont użytkowników, firma Contoso utworzyła trzy dedykowane konta administratora globalnego z silnymi hasłami. Konta są chronione przez usługę Azure AD Multi-Factor Authentication (MFA) i usługę Azure Active Directory (Azure AD) Privileged Identity Management (PIM). *Program PIM jest dostępny tylko w przypadku Microsoft 365 E5.*

  Logowanie się przy użyciu administratora **dc usługi Azure AD** lub  konta administratora globalnego jest wykonywane tylko dla określonych zadań administracyjnych. Hasła są znane tylko wyznaczonym pracownikom i mogą być używane tylko w okresie skonfigurowanym w usłudze Azure AD PIM.

  Administratorzy zabezpieczeń firmy Contoso przypisyli mniejsze role administratora do kont odpowiednich do funkcji pracownika IT.

  Aby uzyskać więcej informacji, zobacz [Informacje Microsoft 365 administratorów](/office365/admin/add-users/about-admin-roles).

- Uwierzytelniania wieloskładnikowego dla wszystkich kont użytkowników

  Uwierzytelniania wieloskładnikowego dodaje dodatkową warstwę ochrony do procesu logowania. Wymaga to od użytkowników potwierdzenia rozmowy telefonicznej, wiadomości SMS lub powiadomienia aplikacji na smartfonie po prawidłowym wprowadzeniu hasła. W przypadku uwierzytelniania wieloskładnikowego konta użytkowników usługi Azure AD są chronione przed nieautoryzowanym logowaniem, nawet jeśli hasło do konta zostało naruszone.

   - Aby chronić się przed naruszeniami subskrypcji usługi Microsoft 365, firma Contoso wymaga uwierzytelniania wieloskładnikowego na wszystkich kontach administratora dc usługi **Azure AD** lub administratora **globalnego**.
   - W celu ochrony przed atakami wyłudzających informacje, w których atakujący naruszono poświadczenia zaufanej osoby w organizacji i wysyła złośliwe wiadomości e-mail, firma Contoso włączyła uwierzytelniania wieloskładnikowego dla wszystkich kont użytkowników, w tym menedżerów i kadry kierowniczej.

- Bezpieczniejszy dostęp urządzeń i aplikacji dzięki zasadom dostępu warunkowego

  Firma Contoso używa [zasad dostępu warunkowego](../security/office-365-security/microsoft-365-policies-configurations.md) dla tożsamości, urządzeń, Exchange Online i SharePoint. Zasady dostępu warunkowego tożsamości obejmują wymaganie zmiany hasła dla użytkowników wysokiego ryzyka i blokowanie klientów przed używaniem aplikacji, które nie obsługują nowoczesnego uwierzytelniania. Zasady dotyczące urządzeń obejmują definicję zatwierdzonych aplikacji i wymaganie zgodności komputerów i urządzeń przenośnych. Exchange Online dostępu warunkowego obejmują blokowanie klientów programu ActiveSync i konfigurowanie Office 365 szyfrowania wiadomości. SharePoint dostępu warunkowego obejmują dodatkową ochronę witryn poufnych i ściśle chronionych.

- Windows Hello dla firm

  Firma Contoso [wdrożyła usługę Windows Hello dla](/windows/security/identity-protection/hello-for-business/hello-identity-verification) firm, aby wyeliminować konieczność logowania się za pośrednictwem silnego uwierzytelniania dwuskładnikowego na komputerach i urządzeniach przenośnych z systemem Windows 10 Enterprise.

- Windows Defender Credential Guard

  Aby zablokować docelowe ataki i złośliwe oprogramowanie działające w systemie operacyjnym z uprawnieniami administracyjnymi, firma Contoso włączyła funkcję [Windows Defender Credential Guard](/windows/security/identity-protection/credential-guard/credential-guard) za pośrednictwem AD DS grupy.

## <a name="threat-protection"></a>Ochrona przed zagrożeniami

- Ochrona przed złośliwym oprogramowaniem za pomocą Program antywirusowy Windows Defender

  Firma Contoso używa oprogramowania [Program antywirusowy Windows Defender](/windows/security/threat-protection/windows-defender-antivirus/windows-defender-antivirus-in-windows-10) ochrony przed złośliwym oprogramowaniem i zarządzania złośliwym oprogramowaniem na komputerach i urządzeniach z systemem Windows 10 Enterprise.

- Zabezpieczanie przepływu poczty e-mail i rejestrowania inspekcji skrzynki pocztowej za pomocą programu Microsoft Defender dla Office 365 

  Firma Contoso używa programów Exchange Online Protection [Defender for Office 365](/office365/securitycompliance/office-365-atp) do ochrony przed nieznanym złośliwym oprogramowaniem, wirusami i złośliwymi adresami URL przesyłanych za pośrednictwem wiadomości e-mail.

  Włączono również rejestrowanie inspekcji skrzynki pocztowej firmy Contoso w celu określenia, kto loguje się do skrzynek pocztowych użytkowników, wysyła wiadomości i wykonuje inne działania wykonywane przez właściciela skrzynki pocztowej, użytkownika delegowanego lub administratora.

- Monitorowanie ataków i ochrona przed zagrożeniami Office 365 wykrywaniem zagrożeń i reagowaniem

  Firma Contoso [używa Office 365](/office365/securitycompliance/office-365-ti) zagrożeń i reakcji w celu ochrony użytkowników, ułatwiając identyfikowanie i reagowanie na ataki oraz zapobieganie atakom w przyszłości.

- Ochrona przed zaawansowanymi atakami za pomocą zaawansowanej analizy zagrożeń

  Firma Contoso używa [zaawansowanej analizy zagrożeń (ATA, Advanced Threat Analytics)](/advanced-threat-analytics/what-is-ata) do ochrony przed zaawansowanymi atakami ukierunkowanych.  AtA automatycznie analizuje, uczy i identyfikuje zachowanie normalne i nietypowe (działania użytkownika, urządzeń i zasobów).

## <a name="information-protection"></a>Ochrona informacji

- Ochrona poufnych i ściśle uregulowanych zasobów cyfrowych za pomocą etykiet usługi Azure Information Protection

  Firma Contoso ustaliła trzy poziomy ochrony danych i wdrożyła [etykiety wrażliwości Microsoft 365, które](../compliance/sensitivity-labels.md) użytkownicy stosują do zasobów cyfrowych. W swojej tajemnicy handlowej i innej własności intelektualnej firma Contoso używa etykiet wrażliwości w celu przechowywania danych ściśle uregulowanych. Ten proces szyfruje zawartość i ogranicza dostęp do konkretnych kont i grup użytkowników.

- Zapobieganie wyciekom danych intranetowych za pomocą ochrony przed utratą danych

  Zasady firmy Contoso [](../compliance/dlp-learn-about-dlp.md) dotyczące ochrony przed utratą danych Exchange Online, SharePoint i innych OneDrive dla Firm, aby uniemożliwić użytkownikom przypadkowe lub celowe udostępnianie poufnych danych.

- Zapobieganie wyciekom danych urządzenia Windows informacji

  Firma Contoso używa funkcji [Windows Information Protection (WIP)](/windows/security/information-protection/windows-information-protection/protect-enterprise-data-using-wip) w celu ochrony przed wyciekiem danych za pośrednictwem internetowych aplikacji i usług oraz aplikacji dla przedsiębiorstw oraz danych na urządzeniach należących do przedsiębiorstwa i urządzeniach osobistych, które pracownicy wprowadzają do pracy.

- Monitorowanie chmury za pomocą programu Microsoft Defender dla aplikacji w chmurze

  Firma Contoso używa usługi [Microsoft Defender for Cloud Apps](/cloud-app-security/what-is-cloud-app-security) do mapowania środowiska chmury, monitorowania użycia oraz wykrywania zdarzeń i zdarzeń zabezpieczających. *Program Microsoft Defender for Cloud Apps jest dostępny tylko w Microsoft 365 E5.*

- Zarządzanie urządzeniami za pomocą Microsoft Intune

  Firma Contoso [używa Microsoft Intune](/intune/introduction-intune) do rejestrowania i konfigurowania dostępu do urządzeń przenośnych i aplikacji, które na nich działają, oraz do zarządzania tym dostępem. Zasady dostępu warunkowego oparte na urządzeniach wymagają również zatwierdzonych aplikacji oraz zgodnych komputerów i urządzeń przenośnych.

## <a name="security-management"></a>Zarządzanie zabezpieczeniami

- Centralny pulpit nawigacyjny zabezpieczeń dla it z programem Microsoft Defender dla chmury

  Firma Contoso używa programu [Microsoft Defender for Cloud](https://azure.microsoft.com/services/security-center/) do prezentować ujednolicony widok ochrony przed zagrożeniami i zabezpieczeń, zarządzać zasadami zabezpieczeń w różnych obciążeniach i odpowiadać na cyberataki.

- Central security dashboard for users with Windows Defender Security Center

  Firma [Contoso wdrożyła](/windows/security/threat-protection/windows-defender-security-center/windows-defender-security-center) aplikację Zabezpieczenia Windows na swoich komputerach i urządzeniach z systemem Windows 10 Enterprise, aby użytkownicy od razu widzili swoje działania w zakresie zabezpieczeń i podejmieli działania.
