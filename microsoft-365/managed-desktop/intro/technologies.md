---
title: technologie Microsoft Managed Desktop
description: W tym artykule wymieniono technologie i aplikacje używane w Microsoft Managed Desktop.
keywords: Microsoft Managed Desktop, Microsoft 365, usługa, dokumentacja
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
ms.openlocfilehash: d7a7b6889451d83aaa6c2b53c1dce6ed035f9916
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2022
ms.locfileid: "64945632"
---
# <a name="microsoft-managed-desktop-technologies"></a>technologie Microsoft Managed Desktop

W tym artykule wymieniono technologie i aplikacje używane w Microsoft Managed Desktop.

<!-- Microsoft 365 E5; Device as a Service -->
<!-- in O365 table, standard suite, removed this sentence "Please see the Installation of Project/Visio 64bit Click to Run Addendum for important deployment instructions. -->

Microsoft 365 Enterprise licencjonowanie jest wymagane dla wszystkich użytkowników Microsoft Managed Desktop. Aby uzyskać więcej informacji na temat wymagań licencyjnych dotyczących usługi, zobacz [Wymagania wstępne dotyczące Microsoft Managed Desktop](../get-ready/prerequisites.md).

W tym artykule podsumowano składniki zawarte w wymaganych licencjach Enterprise oraz sposób, w jaki usługa używa każdego składnika z urządzeniami Microsoft Managed Desktop. Określone role i obowiązki dla każdego obszaru są szczegółowo opisane w Microsoft Managed Desktop dokumentacji.

## <a name="office-365-e3-or-e5"></a>Office 365 E3 lub E5

| Rezultat | Informacji |
| ----- | ----- |
| Aplikacje Microsoft 365 dla przedsiębiorstw (64-bitowe) | Następujące aplikacje Office zostaną dostarczone wraz z urządzeniem:<br><ul><li>Word</li><li>Excel</li><li>PowerPoint</li><li>Outlook</li><li>Publisher</li><li>Access</li><li>Skype dla firm</li><li>OneNote</li></ul><br>64-bitowe pełne wersje Microsoft Project i Microsoft Visio nie są uwzględniane. Jednak ponieważ instalacja tych aplikacji zależy od Aplikacje Microsoft 365 instalacji Enterprise, Microsoft Managed Desktop utworzono domyślne wdrożenia Microsoft Intune i grupy zabezpieczeń, których można użyć do wdrożenia tych aplikacji w licencjonowanych użytkowników. Aby uzyskać więcej informacji, zobacz [Instalowanie Microsoft Project lub microsoft Visio na urządzeniach Microsoft Managed Desktop](../get-started/project-visio.md). |
| OneDrive | Azure Active Directory logowanie jednokrotne jest włączone dla użytkowników, gdy po raz pierwszy logują się do OneDrive.<br><br>Dostępne są znane foldery Przekierowywanie folderów dla folderów Pulpit, Dokument i Obrazy. Te foldery są włączone i konfigurowane przez Microsoft Managed Desktop. |
| Aplikacje ze sklepu | Microsoft Sway i Power BI nie są dostarczane z urządzeniem. Te aplikacje są dostępne do pobrania z Microsoft Store. |
| Aplikacje Win32 | Teams nie jest dostarczana z urządzeniem, ale jest spakowana i dostarczana przez firmę Microsoft dla urządzeń Microsoft Managed Desktop. Klient usługi Azure Information Protection nie jest dostarczany z urządzeniem, ale można go spakować do wdrożenia. |
| Aplikacje internetowe | Następujące aplikacje internetowe nie są dostarczane z urządzeniem: <ul><li>Yammer</li><li>Office w przeglądarce</li><li>Delve</li><li>Flow</li><li>StaffHub</li><li>Power Apps</li><li>Planner</li></ul> <br>Użytkownicy mogą uzyskiwać dostęp do wersji internetowej tych aplikacji za pomocą przeglądarki. |

## <a name="windows-10-enterprise-e5-or-e3-with-microsoft-defender-for-endpoint"></a>Windows 10 Enterprise E5 lub E3 z Ochrona punktu końcowego w usłudze Microsoft Defender

Zalecamy, aby administratorzy IT skonfigurowali następujące ustawienia.

> [!NOTE]
> Te ustawienia nie są uwzględniane ani zarządzane w ramach Microsoft Managed Desktop.

| Rezultat | Informacji |
| ----- | ----- |
| Windows Hello dla firm | Należy zaimplementować Windows Hello dla firm, aby zastąpić hasła silnym uwierzytelnianiem dwuskładnikowym dla urządzeń Microsoft Managed Desktop. Aby uzyskać więcej informacji, zobacz [Windows Hello dla firm](/windows/security/identity-protection/hello-for-business/hello-identity-verification). |
| Wirtualizacja aplikacji | Pakiety wirtualizacji aplikacji (App-V) można wdrożyć przy użyciu klienta zarządzania aplikacjami Intune Win32. Aby uzyskać więcej informacji, zobacz [Wirtualizacja aplikacji](/windows/application-management/app-v/appv-technical-reference). |
| Zapobieganie utracie danych w usłudze Microsoft Purview | Należy zaimplementować zapobieganie utracie danych, aby monitorować akcje podejmowane w przypadku elementów, które zostały uznane za wrażliwe, oraz aby zapobiec niezamierzonemu udostępnianiu tych elementów. Aby uzyskać więcej informacji, zobacz [Zapobieganie utracie danych](../../compliance/endpoint-dlp-learn-about.md). |

Funkcje uwzględnione i zarządzane w ramach Microsoft Managed Desktop:

| Rezultat | Informacji |
| ----- | ----- |
| Szyfrowanie dysków funkcji BitLocker | Szyfrowanie dysków funkcji BitLocker służy do szyfrowania wszystkich dysków systemowych. Aby uzyskać więcej informacji, zobacz [Szyfrowanie dysków funkcji BitLocker](/windows/security/information-protection/bitlocker/bitlocker-overview). |
| Windows Defender System Guard | Chroni integralność systemu podczas uruchamiania i sprawdza, czy integralność systemu została naprawdę zachowana. Aby uzyskać więcej informacji, zobacz [Windows Defender System Guard](/windows/security/threat-protection/windows-defender-system-guard/system-guard-how-hardware-based-root-of-trust-helps-protect-windows). |
| Windows Defender Credential Guard | Windows Defender Credential Guard używa zabezpieczeń opartych na wirtualizacji do izolowania wpisów tajnych, aby tylko uprzywilejowane oprogramowanie systemowe mogło uzyskiwać do nich dostęp. Aby uzyskać więcej informacji, zobacz [Windows Defender System Guard](/windows/security/threat-protection/windows-defender-system-guard/system-guard-how-hardware-based-root-of-trust-helps-protect-windows). |
| Ochrona punktu końcowego w usłudze Microsoft Defender — wykrywanie i reagowanie na punkty końcowe | Microsoft Managed Desktop Operacje zabezpieczeń reagują na alerty i podejmuje działania w celu skorygowania zagrożeń przy użyciu wykrywania punktów końcowych i reagowania. Aby uzyskać więcej informacji, zobacz [Ochrona punktu końcowego w usłudze Microsoft Defender — Wykrywanie i reagowanie punktów końcowych](/windows/security/threat-protection/microsoft-defender-atp/overview-endpoint-detection-response). |
| Ochrona punktu końcowego w usłudze Microsoft Defender — Eksperci od zagrożeń | Microsoft Managed Desktop integruje się ze szczegółowymi informacjami i danymi ekspertów od zagrożeń za pośrednictwem powiadomień o ukierunkowanych atakach. Przed włączeniem tej usługi musisz wyrazić dodatkową zgodę. Aby uzyskać więcej informacji, zobacz [Ochrona punktu końcowego w usłudze Microsoft Defender — Eksperci od zagrożeń](/windows/security/threat-protection/microsoft-defender-atp/microsoft-threat-experts). |
| Ochrona punktu końcowego w usłudze Microsoft Defender — zarządzanie zagrożeniami i lukami w zabezpieczeniach | Wymagane do przyszłego użycia w planie usługi Microsoft Managed Desktop. Aby uzyskać więcej informacji, zobacz [Ochrona punktu końcowego w usłudze Microsoft Defender — Zarządzanie zagrożeniami i lukami w zabezpieczeniach](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt). |
| Ochrona punktu końcowego w usłudze Microsoft Defender — zmniejszanie obszaru podatnego na ataki | Dotyczy ryzykownych zachowań oprogramowania, które są często nadużywane przez osoby atakujące. Aby uzyskać więcej informacji, zobacz [Ochrona punktu końcowego w usłudze Microsoft Defender — Zmniejszanie obszaru podatnego na ataki](/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction). |
| Ochrona punktu końcowego w usłudze Microsoft Defender — Exploit Protection | Chroni przed złośliwym oprogramowaniem wykorzystującym luki w zabezpieczeniach do infekowania urządzeń i rozprzestrzenia się, automatycznie stosując techniki ograniczania ryzyka luk w zabezpieczeniach do procesów i aplikacji systemu operacyjnego. Aby uzyskać więcej informacji, zobacz [Ochrona punktu końcowego w usłudze Microsoft Defender — Exploit Protection](/windows/security/threat-protection/microsoft-defender-atp/exploit-protection). |
| Ochrona punktu końcowego w usłudze Microsoft Defender — ochrona sieci | Rozszerza zakres Microsoft Defender SmartScreen, aby zablokować cały wychodzący ruch HTTP i HTTPS, który próbuje nawiązać połączenie ze źródłami o niskiej reputacji. Aby uzyskać więcej informacji, zobacz [Ochrona punktu końcowego w usłudze Microsoft Defender — Ochrona sieci](/windows/security/threat-protection/microsoft-defender-atp/network-protection). |
| Ochrona przed naruszeniami w usłudze Microsoft Defender | Windows ochrona przed naruszeniami jest używana do zapobiegania zmianom ustawień zabezpieczeń, takich jak ochrona przed wirusami. Aby uzyskać więcej informacji, zobacz [Ochrona przed naruszeniami w usłudze Microsoft Defender](/windows/security/threat-protection/microsoft-defender-antivirus/prevent-changes-to-security-settings-with-tamper-protection). |
| Program antywirusowy Microsoft Defender ochrona antywirusowa oparta na zachowaniu, heurystycznym i w czasie rzeczywistym | Zawsze należy skanować pod kątem zagrożeń dotyczących plików i procesów, które mogą nie zostać wykryte jako złośliwe oprogramowanie. Aby uzyskać więcej informacji, zobacz [Program antywirusowy Microsoft Defender ochrona antywirusowa oparta na zachowaniu, heurystycznym i w czasie rzeczywistym](../../security/defender-endpoint/microsoft-defender-antivirus-in-windows-10.md). |
| Program antywirusowy Microsoft Defender ochrona dostarczana przez chmurę | Zapewnia dynamiczną niemal natychmiastową, zautomatyzowaną ochronę przed nowymi i pojawiającym się zagrożeniami. Aby uzyskać więcej informacji, zobacz [Program antywirusowy Microsoft Defender Ochrona dostarczana przez chmurę](/windows/security/threat-protection/microsoft-defender-antivirus/utilize-microsoft-cloud-protection-microsoft-defender-antivirus). |
| Ochrona punktu końcowego w usłudze Microsoft Defender — "Blokuj od pierwszego wejrzenia" | Zapewnia wykrywanie i blokowanie nowego złośliwego oprogramowania, gdy Windows wykrywa podejrzany lub nieznany plik. Aby uzyskać więcej informacji, zobacz [Ochrona punktu końcowego w usłudze Microsoft Defender — Blokuj od pierwszego wejrzenia](/windows/security/threat-protection/microsoft-defender-antivirus/configure-block-at-first-sight-microsoft-defender-antivirus). |
| Program antywirusowy Microsoft Defender potencjalnie niechciane aplikacje | Służy do blokowania aplikacji, które mogą powodować powolne uruchamianie maszyny, wyświetlanie nieoczekiwanych reklam lub, w najgorszym przypadku, instalowanie innego oprogramowania, które może być nieoczekiwane lub niepożądane. Aby uzyskać więcej informacji, zobacz [Program antywirusowy Microsoft Defender Potencjalnie niepożądane aplikacje](/windows/security/threat-protection/microsoft-defender-antivirus/detect-block-potentially-unwanted-apps-microsoft-defender-antivirus). |
| zapora Windows Defender z zabezpieczeniami zaawansowanymi | Oparta na hoście dwukierunkowa filtrowanie ruchu sieciowego dla urządzenia Windows Defender Zapora blokuje nieautoryzowany ruch sieciowy przepływający do lub z urządzenia lokalnego. Aby uzyskać więcej informacji, zobacz [Windows Defender Firewall with Advanced Security (Zapora Windows Defender z zabezpieczeniami zaawansowanymi](/windows/security/threat-protection/windows-firewall/windows-firewall-with-advanced-security)). |
| Kontrola konta użytkownika | Kontrola konta użytkownika przełącza się do bezpiecznego pulpitu, gdy zadanie lub akcja wymaga dostępu typu konta administratora. Microsoft Managed Desktop użytkownicy mają przypisany dostęp użytkowników standardowych podczas rejestracji. Aby uzyskać więcej informacji, zobacz [Kontrola konta użytkownika](/windows/security/identity-protection/user-account-control/how-user-account-control-works). |

## <a name="enterprise-mobility--security-e5"></a>Enterprise Mobility + Security E5

| Rezultat | Informacji |
| ----- | ----- |
| Enterprise Mobility + Security E3<br><br>Azure Active Directory — wersja Premium P2 | Do zarządzania urządzeniami MDM można używać wszystkich funkcji Enterprise Mobility + Security E3.<br><br>Możesz użyć Azure Active Directory — wersja Premium P2 jako opcjonalnej funkcji z Microsoft Managed Desktop. |
| Microsoft Defender for Cloud Apps | Możesz użyć tej opcjonalnej funkcji z Microsoft Managed Desktop.
| Azure Information Protection P2  | Możesz użyć tej opcjonalnej funkcji z Microsoft Managed Desktop.
