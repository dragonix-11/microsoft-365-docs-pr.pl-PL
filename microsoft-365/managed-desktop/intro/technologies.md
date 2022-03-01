---
title: Microsoft Managed Desktop technologii
description: W tym artykule wymieniono technologie i aplikacje używane w Microsoft Managed Desktop.
keywords: Microsoft Managed Desktop, Microsoft 365, usługa, dokumentacja
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
ms.openlocfilehash: ec99a478cb085e3e7692d2e489851d4abf4c2bb4
ms.sourcegitcommit: a6651b841f111ea2776cab88bf2c80f805fa8e09
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/13/2022
ms.locfileid: "63026738"
---
# <a name="microsoft-managed-desktop-technologies"></a>Microsoft Managed Desktop technologii

W tym artykule wymieniono technologie i aplikacje używane w Microsoft Managed Desktop.

<!-- Microsoft 365 E5; Device as a Service -->
<!-- in O365 table, standard suite, removed this sentence "Please see the Installation of Project/Visio 64bit Click to Run Addendum for important deployment instructions. -->

Microsoft 365 Enterprise licencji jest wymagane dla wszystkich Microsoft Managed Desktop użytkowników. Aby uzyskać więcej informacji na temat wymagań licencjonowania usługi, zobacz [Wymagania wstępne dotyczące Microsoft Managed Desktop](../get-ready/prerequisites.md).

Ten artykuł zawiera podsumowanie składników zawartych w wymaganych licencjach usługi Enterprise, wraz z opisem sposobu, w jaki usługa używa każdego składnika z Microsoft Managed Desktop urządzeniami. Konkretne role i obowiązki dotyczące poszczególnych obszarów są szczegółowo Microsoft Managed Desktop dokumentacji. 

## <a name="office-365-e3-or-e5"></a>Office 365 E3 lub E5

| Rezultat |Informacje |
--- |--- 
Aplikacje Microsoft 365 dla przedsiębiorstw (64-bitowa) | Następujące Office zostaną dostarczone z urządzeniem: Word, Excel, PowerPoint, Outlook, Publisher, Access, Skype dla firm, OneNote.<br><br>Wersje 64-bitowe pełnych wersji pakietu Microsoft Project i microsoft Visio nie są dostępne. Jednak ponieważ instalacja tych aplikacji zależy od instalacji Aplikacje Microsoft 365 dla przedsiębiorstw, w programie Microsoft Managed Desktop utworzono domyślne wdrożenia programu Microsoft Intune i grupy zabezpieczeń, których można następnie użyć do ich wdrożenia licencjonowanym użytkownikom. Aby uzyskać więcej informacji, zobacz [Instalowanie aplikacji Microsoft Project microsoft Visio na Microsoft Managed Desktop urządzeniach](../get-started/project-visio.md).
OneDrive |Azure Active Directory logowanie pojedyncze jest włączone dla użytkowników, którzy logują się po raz pierwszy OneDrive.<br><br>Uwzględniono przekierowanie znanego folderu dla folderów "Pulpit", "Dokument" i "Obrazy". włączone i skonfigurowane przez Microsoft Managed Desktop.
Aplikacje ze Sklepu | Aplikacje Microsoft Sway i Power BI nie są dostarczane z tym urządzeniem. Te aplikacje są dostępne do pobrania ze strony Microsoft Store.
Aplikacje Win32 | Teams nie jest dostarczana z urządzeniem, ale jest spakowana i zapewniana przez firmę Microsoft na Microsoft Managed Desktop urządzeniach. Klient Azure Information Protection nie jest dosyłany z urządzeniem, ale możesz go spakował do wdrożenia.
Aplikacje sieci Web | Yammer, Office w przeglądarce, urządzeniach Delve, Flow, StaffHub, Power Apps i Planner nie są dostarczane z urządzeniem. Użytkownicy mogą uzyskać dostęp do wersji tych aplikacji w sieci Web za pomocą przeglądarki.

## <a name="windows-10-enterprise-e5-or-e3-with-microsoft-defender-for-endpoint"></a>Windows 10 Enterprise E5 lub E3 z usługą Microsoft Defender for Endpoint

Zalecamy, aby administratorzy IT skonfigurować następujące ustawienia. Te ustawienia nie są uwzględniane ani zarządzane w ramach Microsoft Managed Desktop.

Rezultat  |Informacje
--- | ---
Windows Hello dla firm | W celu zastąpienia Windows Hello na silne uwierzytelnianie dwuskładnikowe dla Windows Hello firm należy zaimplementować Microsoft Managed Desktop firm. Aby uzyskać więcej informacji, zobacz [Windows Hello dla firm](/windows/security/identity-protection/hello-for-business/hello-identity-verification).
Wirtualizacja aplikacji | Pakiety oprogramowania Application Virtualization (App-V) można wdrażać za pomocą klienta zarządzania aplikacją Intune Win32. Aby uzyskać więcej informacji, zobacz [Wirtualizacja aplikacji](/windows/application-management/app-v/appv-technical-reference).
Microsoft 365 zapobieganie utracie danych | Aby monitorować Microsoft 365, które są podejmowane na elementach określonych jako poufne, i aby zapobiec niezamierzonemu udostępnianiu tych elementów, należy wdrożyć zapobieganie utracie danych. Aby uzyskać więcej informacji, [zobacz Microsoft 365 ochrony przed utratą danych](../../compliance/endpoint-dlp-learn-about.md).

Funkcje zawarte i zarządzane w ramach Microsoft Managed Desktop:

Rezultat |Informacje
--- |---
Szyfrowanie dysków funkcją BitLocker | Szyfrowanie dysków funkcją BitLocker służy do szyfrowania wszystkich dysków systemowych. Aby uzyskać więcej informacji, zobacz [Szyfrowanie dysków funkcją BitLocker](/windows/security/information-protection/bitlocker/bitlocker-overview).
Windows Defender System Guard | Zapewnia integralność systemu podczas uruchamiania oraz sprawdza, czy integralność systemu została rzeczywiście zachowana. Aby uzyskać więcej informacji, [zobacz Windows Defender System Guard](/windows/security/threat-protection/windows-defender-system-guard/system-guard-how-hardware-based-root-of-trust-helps-protect-windows).
Windows Defender Credential Guard | Windows Defender Credential Guard używa zabezpieczeń opartych na wirtualizacji do odizolowania sekretów, dzięki czemu tylko oprogramowanie o uprzywilejowanym systemie może uzyskać do nich dostęp. Aby uzyskać więcej informacji, [zobacz Windows Defender System Guard](/windows/security/threat-protection/windows-defender-system-guard/system-guard-how-hardware-based-root-of-trust-helps-protect-windows).
Program Microsoft Defender dla punktu końcowego — wykrywanie punktu końcowego i odpowiedź | Microsoft Managed Desktop zabezpieczeń odpowiada na alerty i podejmuje działania w celu korygowania zagrożeń za pomocą wykrywania punktu końcowego i odpowiedzi. Aby uzyskać więcej informacji, zobacz [Program Microsoft Defender for Endpoint — Wykrywanie punktu końcowego i odpowiedź](/windows/security/threat-protection/microsoft-defender-atp/overview-endpoint-detection-response).
Program Microsoft Defender dla punktu końcowego — eksperci ds. zagrożeń | Microsoft Managed Desktop się z informacjami i danymi ekspertów ds. zagrożeń za pośrednictwem ukierunkowanych powiadomień o atakach. Przed rozpoczęciem świadczenia tej usługi musisz udzielić dodatkowej zgody. Aby uzyskać więcej informacji, zobacz [Program Microsoft Defender for Endpoint — Threat Experts](/windows/security/threat-protection/microsoft-defender-atp/microsoft-threat-experts).
Program Microsoft Defender dla punktu końcowego — zarządzanie zagrożeniami i lukami w zabezpieczeniach | Wymagane do użycia w przyszłości w Microsoft Managed Desktop serwisowej. Aby uzyskać więcej informacji, zobacz [Program Microsoft Defender dla punktu końcowego — zarządzanie zagrożeniami i lukami w zabezpieczeniach](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt).
Program Microsoft Defender dla punktu końcowego — zmniejszenie ataków na powierzchnię | Zmniejszenie powierzchni ataków jest celem ryzykownych zachowań oprogramowania, które są często używane przez atakujących. Aby uzyskać więcej informacji, zobacz [Program Microsoft Defender dla punktu końcowego — zmniejszenie powierzchni ataków](/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction).
Program Microsoft Defender dla punktu końcowego — ochrona przed lukiami | Chroni przed złośliwym oprogramowaniem używanym do infekowania urządzeń i rozpowszechniania się przez automatyczne stosowanie technik wykorzystania środków zaradczych zarówno do procesów systemu operacyjnego, jak i aplikacji. Aby uzyskać więcej informacji, zobacz [Program Microsoft Defender for Endpoint — exploit Protection](/windows/security/threat-protection/microsoft-defender-atp/exploit-protection).
Program Microsoft Defender dla punktu końcowego — ochrona sieci | Ochrona sieci rozszerza zakres wiadomości Microsoft Defender SmartScreen w celu zablokowania całego ruchu wychodzącego HTTP i HTTPS, który próbuje nawiązać połączenie ze źródłami o niskiej reputacji. Aby uzyskać więcej informacji, zobacz [Program Microsoft Defender for Endpoint — Network Protection](/windows/security/threat-protection/microsoft-defender-atp/network-protection).
Microsoft Defender Tamper Protection | Windows ochrony przed naruszeniami jest używany w celu zapobiegania zmienianiu ustawień zabezpieczeń, takich jak ochrona antywirusowa. Aby uzyskać więcej informacji, zobacz [Ochrona przed naruszeniami programu Microsoft Defender](/windows/security/threat-protection/microsoft-defender-antivirus/prevent-changes-to-security-settings-with-tamper-protection).
Program antywirusowy Microsoft Defender ochrona antywirusowa oparta na zachowaniu oraz heuristic i w czasie rzeczywistym | Zawsze skanuj w poszukiwaniu zagrożeń związanych z plikami i procesami, które mogą nie być wykrywane jako złośliwe oprogramowanie. Aby uzyskać więcej informacji, Program antywirusowy Microsoft Defender ochronę antywirusową opartą na zachowaniu [oraz heuristic i w czasie rzeczywistym](../../security/defender-endpoint/microsoft-defender-antivirus-in-windows-10.md).
Program antywirusowy Microsoft Defender ochrona w chmurze | Zapewnia dynamiczną, natychmiastową, automatyczną ochronę przed nowymi i pojawiającymi się zagrożeniami. Aby uzyskać więcej informacji, [zobacz Program antywirusowy Microsoft Defender Ochrona w chmurze](/windows/security/threat-protection/microsoft-defender-antivirus/utilize-microsoft-cloud-protection-microsoft-defender-antivirus).
Program Microsoft Defender dla punktu końcowego — "Blokuj od pierwszego rzutu" | Wykrywa i blokuje nowe złośliwe oprogramowanie, gdy Windows wykrywa podejrzany lub nieznany plik. Aby uzyskać więcej informacji, zobacz [Program Microsoft Defender dla punktu końcowego — blokowanie na pierwszy rzut oka](/windows/security/threat-protection/microsoft-defender-antivirus/configure-block-at-first-sight-microsoft-defender-antivirus).
Program antywirusowy Microsoft Defender potencjalnie niechciane aplikacje | Potencjalnie niechciane aplikacje służą do blokowania aplikacji, które mogą powodować powolne uruchamianie komputera, wyświetlać nieoczekiwane reklamy lub w najgorszej sytuacji zainstalować inne oprogramowanie, które może być nieoczekiwane lub niechciane. Aby uzyskać więcej informacji, [zobacz Program antywirusowy Microsoft Defender Potencjalnie niechciane aplikacje](/windows/security/threat-protection/microsoft-defender-antivirus/detect-block-potentially-unwanted-apps-microsoft-defender-antivirus).
Windows Defender z zabezpieczeniami zaawansowanymi | Oparte na hoście, dwukierunkowe filtrowanie ruchu sieciowego dla urządzenia, zapora Windows Defender blokuje nieautoryzowany ruch sieciowy wychodzący do lub z urządzenia lokalnego. Aby uzyskać więcej informacji, zobacz [Windows Defender z zabezpieczeniami zaawansowanymi](/windows/security/threat-protection/windows-firewall/windows-firewall-with-advanced-security).
Kontrola konta użytkownika | Kontrola konta użytkownika przełącza się do bezpiecznego pulpitu, gdy zadanie lub akcja wymaga dostępu typu konta administratora. Microsoft Managed Desktop mają przypisany dostęp do standardowego dostępu użytkownika podczas rejestracji. Aby uzyskać więcej informacji, zobacz [Kontrola konta użytkownika](/windows/security/identity-protection/user-account-control/how-user-account-control-works).


## <a name="enterprise-mobility--security-e5"></a>Enterprise Mobility + Security E5

Rezultat |Informacje
 --- | ---
Enterprise Mobility + Security E3<br>Azure Active Directory — wersja Premium P2 | Do zarządzania urządzeniami MDM możesz używać Enterprise Mobility + Security E3 funkcji zarządzania urządzeniami MDM. W przypadku Azure Active Directory — wersja Premium P2 jako funkcji opcjonalnej z funkcją Microsoft Managed Desktop.
Usługa Microsoft Defender dla aplikacji w chmurze | Tej funkcji opcjonalnej można używać w Microsoft Managed Desktop.
Azure Information Protection P2  | Tej funkcji opcjonalnej można używać w Microsoft Managed Desktop.
