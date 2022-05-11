---
title: Szyfrowanie w Microsoft 365
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 8/15/2019
audience: Admin
ms.topic: overview
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: 0a322724-08ca-43db-b69a-afbfa20484cd
ms.collection:
- M365-security-compliance
- Strat_O365_IP
- m365solution-mip
- m365initiative-compliance
description: Dzięki Office 365 zawartość jest szyfrowana w spoczynku i przesyłana przy użyciu najsilniejszego szyfrowania, protokołów i dostępnych technologii. Zapoznaj się z omówieniem szyfrowania w Office 365.
ms.openlocfilehash: 5f866931eba3078074b47c9cc8c5ed310489b9bb
ms.sourcegitcommit: 7dc7e9fd76adf848f941919f86ca25eecc704015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/11/2022
ms.locfileid: "65319270"
---
# <a name="encryption"></a>Szyfrowanie

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Szyfrowanie jest ważną częścią strategii ochrony plików i ochrony informacji. Ten artykuł zawiera omówienie szyfrowania dla Office 365. Uzyskaj pomoc dotyczącą zadań szyfrowania, takich jak konfigurowanie szyfrowania dla organizacji i jak chronić hasła Office dokumentów.
  
- Aby uzyskać informacje o certyfikatach i technologiach, takich jak protokół TLS, zobacz [Informacje techniczne dotyczące szyfrowania w Office 365](technical-reference-details-about-encryption.md).

- Aby uzyskać informacje na temat konfigurowania lub konfigurowania szyfrowania dla organizacji, zobacz [Konfigurowanie szyfrowania w Office 365 Enterprise](set-up-encryption.md).

## <a name="what-is-encryption-and-how-does-it-work-in-office-365"></a>Co to jest szyfrowanie i jak działa w Office 365?

Proces szyfrowania koduje dane (nazywane zwykłego tekstu) do szyfru. W przeciwieństwie do zwykłego tekstu, szyfrowanie nie może być używane przez osoby lub komputery, chyba że i dopóki nie zostanie odszyfrowany szyfrowany. Odszyfrowywanie wymaga klucza szyfrowania, który mają tylko autoryzowani użytkownicy. Szyfrowanie pomaga zagwarantować, że tylko autoryzowani adresaci mogą odszyfrować twoją zawartość. Zawartość zawiera pliki, wiadomości e-mail, wpisy kalendarza itd.
  
Samo szyfrowanie nie uniemożliwia przechwytywania zawartości. Szyfrowanie jest częścią większej strategii ochrony informacji w organizacji. Korzystając z szyfrowania, możesz upewnić się, że tylko autoryzowane strony mogą używać zaszyfrowanych danych.
  
W tym samym czasie można mieć wiele warstw szyfrowania. Możesz na przykład szyfrować wiadomości e-mail oraz kanały komunikacyjne, za pośrednictwem których przepływa wiadomość e-mail. Dzięki Office 365 dane są szyfrowane w spoczynku i przesyłane przy użyciu kilku silnych protokołów szyfrowania i technologii, które obejmują zabezpieczenia warstwy transportowej/warstwę bezpiecznych gniazd (TLS/SSL), zabezpieczenia protokołu internetowego (IPSec) i zaawansowaną warstwę szyfrowania (AES).
  
## <a name="encryption-for-data-at-rest-and-data-in-transit"></a>Szyfrowanie danych magazynowanych i danych podczas przesyłania

 **Przykłady danych magazynowanych** obejmują pliki przekazane do biblioteki SharePoint, dane Project Online, dokumenty przekazane podczas spotkania Skype dla firm, wiadomości e-mail i załączniki przechowywane w folderach w skrzynce pocztowej oraz pliki przekazane do OneDrive dla Firm.
  
 **Przykłady danych przesyłanych** obejmują wiadomości e-mail, które są w trakcie dostarczania, lub konwersacje, które odbywają się na spotkaniu online. W Office 365 dane są przesyłane za każdym razem, gdy urządzenie użytkownika komunikuje się z serwerem firmy Microsoft lub gdy serwer firmy Microsoft komunikuje się z innym serwerem.
  
Dzięki Office 365 wiele warstw i rodzajów szyfrowania współdziała ze sobą w celu zabezpieczenia danych. Poniższa tabela zawiera kilka przykładów z linkami do dodatkowych informacji.
  
|**Rodzaje zawartości**|**Technologie szyfrowania**|**Zasoby, aby dowiedzieć się więcej**|
|:-----|:-----|:-----|
|Pliki na urządzeniu. Te pliki mogą obejmować wiadomości e-mail zapisane w folderze, Office dokumenty zapisane na komputerze, tablecie lub telefonie albo dane zapisane w chmurze firmy Microsoft.  <br/> |BitLocker w centrach danych firmy Microsoft. BitLocker mogą być również używane na maszynach klienckich, takich jak komputery Windows i tablety  <br/> Rozproszony menedżer kluczy (DKM) w centrach danych firmy Microsoft  <br/> Klucz klienta dla Microsoft 365  <br/> |[Windows Centrum IT: BitLocker](/windows/device-security/bitlocker/bitlocker-overview) <br/> [Centrum zaufania firmy Microsoft: szyfrowanie](https://www.microsoft.com/TrustCenter/Security/Encryption) <br/> [Seria kontroli zabezpieczeń w chmurze: szyfrowanie danych magazynowanych](https://blogs.microsoft.com/microsoftsecure/2015/09/10/cloud-security-controls-series-encrypting-data-at-rest) <br/> [Jak usługa Exchange Online zabezpiecza Twoje tajne wpisy poczty e-mail](exchange-online-secures-email-secrets.md) <br/> [Szyfrowanie usługi przy użyciu klucza klienta](customer-key-overview.md) <br/> |
|Pliki przesyłane między użytkownikami. Te pliki mogą zawierać dokumenty Office lub SharePoint elementy listy udostępnione użytkownikom.  <br/> |Protokół TLS dla plików przesyłane  <br/> |[Data Encryption in OneDrive for Business and SharePoint Online](data-encryption-in-odb-and-spo.md) <br/> [Skype dla firm Online: zabezpieczenia i archiwizacja](/office365/servicedescriptions/skype-for-business-online-service-description/skype-for-business-online-features) <br/> |
|Wiadomość e-mail przesyłana między adresatami. Ta wiadomość e-mail zawiera wiadomości e-mail hostowane przez Exchange Online.  <br/> |Szyfrowanie wiadomości w Microsoft Purview z usługami Azure Rights Management, S/MIME i TLS na potrzeby przesyłania wiadomości e-mail  <br/> |[Szyfrowanie essage](ome.md) <br/> [Szyfrowanie wiadomości e-mail w Office 365](email-encryption.md) <br/> [Jak usługa Exchange Online używa protokołu TLS do zabezpieczania połączeń poczty e-mail w usłudze Office 365](exchange-online-uses-tls-to-secure-email-connections.md) <br/> |
|Czaty, wiadomości i pliki przesyłane między adresatami przy użyciu Microsoft Teams. <br/> |Teams używa protokołu TLS i MTLS do szyfrowania wiadomości błyskawicznych. Ruch multimediów jest szyfrowany przy użyciu protokołu Secure RTP (SRTP). Teams używa zgodnych algorytmów FIPS (Federal Information Processing Standard) do wymiany kluczy szyfrowania. <br/> |[Szyfrowanie dla Teams](/microsoftteams/teams-security-guide#encryption-for-teams) <br/> |

## <a name="what-if-i-need-more-control-over-encryption-to-meet-security-and-compliance-requirements"></a>Co zrobić, jeśli potrzebuję większej kontroli nad szyfrowaniem, aby spełnić wymagania dotyczące zabezpieczeń i zgodności?

Microsoft 365 udostępnia rozwiązania zarządzane przez firmę Microsoft do szyfrowania woluminów, szyfrowania plików i szyfrowania skrzynek pocztowych w Office 365. Ponadto firma Microsoft udostępnia rozwiązania szyfrowania, które można zarządzać i kontrolować. Te rozwiązania szyfrowania są oparte na platformie Azure.
  
Aby dowiedzieć się więcej, zobacz następujące zasoby:
  
- [Co to jest usługa Azure Rights Management?](/information-protection/understand-explore/what-is-azure-rms)

- [Aktywowanie Rights Management w centrum administracyjnym](../enterprise/activate-rms-in-microsoft-365.md)

- [Set up Information Rights Management (IRM) in SharePoint admin center](set-up-irm-in-sp-admin-center.md)

- [Szyfrowanie usługi przy użyciu klucza klienta usługi Microsoft Purview](customer-key-overview.md)

- [Podwójne szyfrowanie kluczy](double-key-encryption.md)

## <a name="how-do-i"></a>Jak mogę...

|**Aby wykonać to zadanie**|**Zobacz te zasoby**|
|:-----|:-----|
|Konfigurowanie szyfrowania dla mojej organizacji|[Konfigurowanie szyfrowania w Office 365 Enterprise](set-up-encryption.md)|
|Wyświetlanie szczegółów dotyczących certyfikatów, technologii i zestawów szyfrowania TLS|[Szczegóły techniczne dotyczące szyfrowania](technical-reference-details-about-encryption.md)|
|Praca z zaszyfrowanymi wiadomościami na urządzeniu przenośnym|[Wyświetlanie zaszyfrowanych komunikatów na urządzeniu Android](https://support.office.com/article/83d60f17-2305-407a-a762-7d518401fdeb) [Wyświetl zaszyfrowane wiadomości w iPhone lub iPad](https://support.microsoft.com/en-us/office/view-protected-messages-on-your-iphone-or-ipad-4d631321-0d26-4bcc-a483-d294dd0b1caf)|
|Szyfrowanie dokumentu przy użyciu ochrony hasłem. (Ochrona hasłem nie jest obsługiwana w przeglądarce. Używaj klasycznych wersji programu Word, Excel i PowerPoint do ochrony hasłem). |[Dodaj lub usuń ochronę w dokumencie, skoroszycie lub prezentacji](https://support.office.com/article/05084cc3-300d-4c1a-8416-38d3e37d6826). Wybierz sekcję **Dodawanie ochrony** , a następnie zobacz **Szyfrowanie przy użyciu hasła**.|
|Usuwanie szyfrowania z dokumentu|[Dodaj lub usuń ochronę w dokumencie, skoroszycie lub prezentacji](https://support.office.com/article/05084cc3-300d-4c1a-8416-38d3e37d6826). Wybierz sekcję **Usuń ochronę** , a następnie zobacz **Usuwanie szyfrowania haseł**.  |

## <a name="related-topics"></a>Tematy pokrewne

[Planowanie Microsoft 365 możliwości zabezpieczeń i ochrony informacji](plan-for-security-and-compliance.md)

[Najlepsze rozwiązania dotyczące zabezpieczania Microsoft 365 dla planów biznesowych](/office365/admin/security-and-compliance/secure-your-business-data)

[Microsoft Stream szyfrowanie i przepływ odtwarzania na poziomie wideo](/stream/network-overview#video-level-encryption-and-playback-flow)
