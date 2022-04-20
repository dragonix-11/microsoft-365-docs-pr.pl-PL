---
title: Podsumowanie Microsoft 365 zabezpieczeń przedsiębiorstwa dla firmy Contoso Corporation
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
description: Jak firma Contoso korzysta z funkcji zabezpieczeń Microsoft 365 dla przedsiębiorstw.
ms.openlocfilehash: a03fcd9570ca29bcbf535e3248b19836a9598b40
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2022
ms.locfileid: "64936032"
---
# <a name="summary-of-microsoft-365-for-enterprise-security-for-the-contoso-corporation"></a>Podsumowanie Microsoft 365 zabezpieczeń przedsiębiorstwa dla firmy Contoso Corporation

Aby uzyskać zgodę na wdrożenie Microsoft 365 dla przedsiębiorstw, dział zabezpieczeń IT firmy Contoso przeprowadził gruntowny przegląd zabezpieczeń. Zidentyfikowano następujące wymagania dotyczące zabezpieczeń dla chmury:

- Użyj najsilniejszych metod uwierzytelniania, aby uzyskać dostęp pracowników do zasobów w chmurze.
- Upewnij się, że komputery i urządzenia przenośne łączą się z aplikacjami i uzyskują do nich dostęp w bezpieczny sposób.
- Ochrona komputerów i wiadomości e-mail przed złośliwym oprogramowaniem.
- Uprawnienia do zasobów cyfrowych opartych na chmurze określają, kto może uzyskiwać dostęp do tego, co i co mogą robić, i są przeznaczone dla dostępu z najniższymi uprawnieniami
- Wrażliwe i wysoce regulowane zasoby cyfrowe są oznaczone etykietami, szyfrowane i przechowywane w bezpiecznych lokalizacjach.
- Wysoce regulowane zasoby cyfrowe są chronione za pomocą dodatkowego szyfrowania i uprawnień.
- Pracownicy działu zabezpieczeń IT mogą monitorować bieżącą postawę zabezpieczeń z centralnych pulpitów nawigacyjnych i otrzymywać powiadomienia o zdarzeniach zabezpieczeń w celu szybkiego reagowania i ograniczania ryzyka.

## <a name="the-contoso-path-to-microsoft-365-security-readiness"></a>Ścieżka firmy Contoso do Microsoft 365 gotowości zabezpieczeń

Firma Contoso wykonaj następujące kroki, aby przygotować swoje zabezpieczenia do wdrożenia Microsoft 365 dla przedsiębiorstw:

1. Ograniczanie kont administratorów dla chmury

   Firma Contoso dokonała obszernego przeglądu istniejących kont administratorów Active Directory Domain Services (AD DS) i skonfigurowała szereg dedykowanych kont i grup administratorów chmury.

2. Klasyfikowanie danych na trzy poziomy zabezpieczeń

   Firma Contoso dokonała dokładnego przeglądu i określiła trzy poziomy, które zostały użyte do zidentyfikowania Microsoft 365 funkcji przedsiębiorstwa w celu ochrony najcenniejszych danych.

3. Określanie zasad dostępu, przechowywania i ochrony informacji dla poziomów danych

   Na podstawie poziomów danych firma Contoso określiła szczegółowe wymagania dotyczące kwalifikowania przyszłych obciążeń IT, które są przenoszone do chmury.

Aby postępować zgodnie z najlepszymi rozwiązaniami dotyczącymi zabezpieczeń i Microsoft 365 wymaganiami dotyczącymi wdrażania w przedsiębiorstwie, administratorzy zabezpieczeń firmy Contoso i jego dział IT wdrożyli wiele funkcji i funkcji zabezpieczeń, zgodnie z opisem w poniższych sekcjach.

## <a name="identity-and-access-management"></a>Zarządzanie tożsamościami i dostępem 

- Dedykowane konta administratora globalnego z uwierzytelnianiem wieloskładnikowymi i usługą PIM

  Zamiast przypisywać rolę administratora globalnego do codziennych kont użytkowników, firma Contoso utworzyła trzy dedykowane konta administratora globalnego z silnymi hasłami. Konta są chronione przez usługę Azure AD Multi-Factor Authentication (MFA) i Azure Active Directory (Azure AD) Privileged Identity Management (PIM). *Usługa PIM jest dostępna tylko w przypadku Microsoft 365 E5.*

  Logowanie się przy użyciu **administratora kontrolera domeny usługi Azure AD** lub konta **administratora globalnego** odbywa się tylko w przypadku określonych zadań administracyjnych. Hasła są znane tylko wyznaczonym pracownikom i mogą być używane tylko w okresie skonfigurowanym w usłudze Azure AD PIM.

  Administratorzy zabezpieczeń firmy Contoso przypisyli mniejsze role administratora do kont, które są odpowiednie dla funkcji zadania tego procesu roboczego IT.

  Aby uzyskać więcej informacji, zobacz [Informacje o rolach administratora Microsoft 365](/office365/admin/add-users/about-admin-roles).

- Uwierzytelnianie wieloskładnikowe dla wszystkich kont użytkowników

  Uwierzytelnianie wieloskładnikowe dodaje dodatkową warstwę ochrony do procesu logowania. Wymaga to od użytkowników potwierdzenia połączenia telefonicznego, wiadomości SMS lub powiadomienia aplikacji na smartfonie po poprawnym wprowadzeniu hasła. W przypadku uwierzytelniania wieloskładnikowego konta użytkowników usługi Azure AD są chronione przed nieautoryzowanym logowaniem, nawet jeśli hasło konta zostało naruszone.

   - Aby chronić przed naruszeniem zabezpieczeń subskrypcji Microsoft 365, firma Contoso wymaga uwierzytelniania wieloskładnikowego na wszystkich kontach **administratora kontrolera domeny usługi Azure AD** lub **kontach administratora globalnego**.
   - Aby chronić przed atakami wyłudzania informacji, w których osoba atakująca narusza poświadczenia zaufanej osoby w organizacji i wysyła złośliwe wiadomości e-mail, firma Contoso włączyła uwierzytelnianie wieloskładnikowe na wszystkich kontach użytkowników, w tym menedżerów i kadry kierowniczej.

- Bezpieczniejszy dostęp do urządzeń i aplikacji przy użyciu zasad dostępu warunkowego

  Firma Contoso używa [zasad dostępu warunkowego](../security/office-365-security/microsoft-365-policies-configurations.md) dla tożsamości, urządzeń, Exchange Online i SharePoint. Zasady dostępu warunkowego tożsamości obejmują wymaganie zmian haseł dla użytkowników wysokiego ryzyka i blokowanie klientom korzystania z aplikacji, które nie obsługują nowoczesnego uwierzytelniania. Zasady urządzeń obejmują definicję zatwierdzonych aplikacji i wymagają zgodnych komputerów i urządzeń przenośnych. Exchange Online zasady dostępu warunkowego obejmują blokowanie klientów usługi ActiveSync i konfigurowanie szyfrowania komunikatów Office 365. SharePoint zasady dostępu warunkowego obejmują dodatkową ochronę poufnych i wysoce regulowanych witryn.

- Windows Hello dla firm

  Firma Contoso wdrożyła [Windows Hello dla firm](/windows/security/identity-protection/hello-for-business/hello-identity-verification), aby ostatecznie wyeliminować potrzebę haseł poprzez silne uwierzytelnianie dwuskładnikowe na komputerach i urządzeniach przenośnych z uruchomionymi Windows 10 Enterprise.

- Windows Defender Credential Guard

  Aby zablokować ukierunkowane ataki i złośliwe oprogramowanie działające w systemie operacyjnym z uprawnieniami administracyjnymi, firma Contoso [włączyła Windows Defender Credential Guard](/windows/security/identity-protection/credential-guard/credential-guard) za pośrednictwem zasad grupy usług AD DS.

## <a name="threat-protection"></a>Ochrona przed zagrożeniami

- Ochrona przed złośliwym oprogramowaniem za pomocą Program antywirusowy Windows Defender

  Firma Contoso używa [Program antywirusowy Windows Defender](/windows/security/threat-protection/windows-defender-antivirus/windows-defender-antivirus-in-windows-10) do ochrony przed złośliwym oprogramowaniem i zarządzania złośliwym oprogramowaniem dla komputerów i urządzeń z uruchomionymi Windows 10 Enterprise.

- Bezpieczny przepływ poczty e-mail i rejestrowanie inspekcji skrzynki pocztowej przy użyciu Ochrona usługi Office 365 w usłudze Microsoft Defender 

  Firma Contoso używa Exchange Online Protection i [Ochrona usługi Office 365 w usłudze Defender](/office365/securitycompliance/office-365-atp) do ochrony przed nieznanym złośliwym oprogramowaniem, wirusami i złośliwymi adresami URL przesyłanych za pośrednictwem wiadomości e-mail.

  Firma Contoso włączyła również rejestrowanie inspekcji skrzynek pocztowych, aby określić, kto loguje się do skrzynek pocztowych użytkowników, wysyła wiadomości i wykonuje inne działania wykonywane przez właściciela skrzynki pocztowej, delegowanego użytkownika lub administratora.

- Monitorowanie i zapobieganie atakom za pomocą Office 365 badania zagrożeń i reagowania na nie

  Firma Contoso używa [Office 365 badania zagrożeń i reagowania na nie](/office365/securitycompliance/office-365-ti), aby chronić użytkowników, ułatwiając identyfikowanie i rozwiązywanie ataków oraz zapobieganie przyszłym atakom.

- Ochrona przed zaawansowanymi atakami za pomocą usługi Advanced Threat Analytics

  Firma Contoso używa [usługi Advanced Threat Analytics (ATA),](/advanced-threat-analytics/what-is-ata) aby chronić się przed zaawansowanymi atakami ukierunkowanymi.  Usługa ATA automatycznie analizuje, uczy się i identyfikuje normalne i nietypowe zachowanie jednostki (użytkownika, urządzeń i zasobów).

## <a name="information-protection"></a>Ochrona informacji

- Ochrona poufnych i wysoce regulowanych zasobów cyfrowych za pomocą etykiet usługi Azure Information Protection

  Firma Contoso określiła trzy poziomy ochrony danych i wdrożyła [Microsoft 365 etykiet poufności](../compliance/sensitivity-labels.md) stosowanych przez użytkowników do zasobów cyfrowych. Ze względu na swoje tajemnice handlowe i inną własność intelektualną firma Contoso używa podlab poufności do danych wysoce regulowanych. Ten proces szyfruje zawartość i ogranicza dostęp do określonych kont użytkowników i grup.

- Zapobieganie wyciekom danych intranetowych dzięki zapobieganiu utracie danych

  Firma Contoso skonfigurowała zasady [ochrony przed utratą danych usługi Microsoft Purview](../compliance/dlp-learn-about-dlp.md) dla Exchange Online, SharePoint i OneDrive dla Firm, aby uniemożliwić użytkownikom przypadkowe lub celowe udostępnianie poufnych danych.

- Zapobieganie wyciekom danych urządzenia Windows Information Protection

  Firma Contoso używa [Windows Information Protection (WIP)](/windows/security/information-protection/windows-information-protection/protect-enterprise-data-using-wip) do ochrony przed wyciekami danych za pośrednictwem internetowych aplikacji i usług oraz aplikacji i danych przedsiębiorstwa na urządzeniach należących do przedsiębiorstwa i urządzeniach osobistych, które pracownicy wprowadzają do pracy.

- Monitorowanie chmury za pomocą Microsoft Defender for Cloud Apps

  Firma Contoso używa [Microsoft Defender for Cloud Apps](/cloud-app-security/what-is-cloud-app-security) do mapowania środowiska chmury, monitorowania jego użycia oraz wykrywania zdarzeń i zdarzeń zabezpieczeń. *Microsoft Defender for Cloud Apps jest dostępna tylko w przypadku Microsoft 365 E5.*

- Zarządzanie urządzeniami za pomocą usługi Microsoft Intune

  Firma Contoso używa [Microsoft Intune](/intune/introduction-intune) do rejestrowania i konfigurowania dostępu do urządzeń przenośnych i aplikacji na nich uruchomionych oraz zarządzania nimi. Zasady dostępu warunkowego oparte na urządzeniach wymagają również zatwierdzonych aplikacji oraz zgodnych komputerów i urządzeń przenośnych.

## <a name="security-management"></a>Zarządzanie zabezpieczeniami

- Centralny pulpit nawigacyjny zabezpieczeń dla it z Microsoft Defender dla Chmury

  Firma Contoso używa [Microsoft Defender dla Chmury](https://azure.microsoft.com/services/security-center/) do przedstawienia ujednoliconego widoku zabezpieczeń i ochrony przed zagrożeniami, zarządzania zasadami zabezpieczeń w ramach obciążeń oraz reagowania na cyberataki.

- Centralny pulpit nawigacyjny zabezpieczeń dla użytkowników z usługą Windows Defender Security Center

  Firma Contoso wdrożyła [aplikację Zabezpieczenia Windows](/windows/security/threat-protection/windows-defender-security-center/windows-defender-security-center) na swoich komputerach i urządzeniach z systemem Windows 10 Enterprise, aby użytkownicy mogli szybko zobaczyć stan zabezpieczeń i podjąć działania.
