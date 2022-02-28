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
description: Dzięki Office 365 Twoja zawartość jest szyfrowana w miejscu i w trakcie przesyłania przy użyciu najsilniejszego dostępnego szyfrowania, protokołów i technologii. Omówienie szyfrowania w aplikacji Office 365.
ms.openlocfilehash: a1ee73d7ded7a02cd7851081412d2403e0ca8f1d
ms.sourcegitcommit: da11ffdf7a09490313dfc603355799f80b0c60f9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/26/2021
ms.locfileid: "62988700"
---
# <a name="encryption"></a>Szyfrowanie

Szyfrowanie jest ważną częścią strategii ochrony plików i ochrony informacji. Ten artykuł zawiera omówienie szyfrowania danych Office 365. Uzyskaj pomoc w zadaniach szyfrowania, takich jak konfigurowanie szyfrowania dla organizacji i zabezpieczanie hasłem Office dokumentów.
  
- Aby uzyskać informacje na temat certyfikatów i technologii, takich jak TLS, zobacz [Informacje techniczne dotyczące szyfrowania](technical-reference-details-about-encryption.md) w Office 365.

- Aby uzyskać informacje na temat konfigurowania lub konfigurowania szyfrowania dla organizacji, zobacz [Konfigurowanie szyfrowania w programie Office 365 Enterprise](set-up-encryption.md).

## <a name="what-is-encryption-and-how-does-it-work-in-office-365"></a>Co to jest szyfrowanie i jak działa w Office 365?

W procesie szyfrowania dane są kodowane (określane jako zwykły tekst) w postaci szyfrowania. W przeciwieństwie do zwykłego tekstu, tekst ciphertext nie może być używany przez osoby lub komputery, chyba że i do momentu odszyfrowania tego tekstu. Odszyfrowywanie wymaga klucza szyfrowania, który mają tylko autoryzowani użytkownicy. Szyfrowanie pozwala zagwarantować, że tylko autoryzowani adresaci mogą odszyfrowywać Twoją zawartość. Zawartość obejmuje pliki, wiadomości e-mail, wpisy kalendarza i tak dalej.
  
Samo szyfrowanie nie zapobiega przechwytywaniu zawartości. Szyfrowanie jest częścią większej strategii ochrony informacji w organizacji. Używając szyfrowania, możesz zapewnić, że tylko autoryzowane podmioty mogą używać zaszyfrowanych danych.
  
Możesz korzystać z wielu warstw szyfrowania w tym samym czasie. Możesz na przykład zaszyfrować wiadomości e-mail oraz kanały komunikacji, przez które przepływają Twoje wiadomości e-mail. W Office 365 dane są szyfrowane w miejscu i w trakcie przesyłania, przy użyciu kilku silnych protokołów szyfrowania i technologii, które obejmują transport Layer Security/Secure Sockets Layer (TLS/SSL), Internet Protocol Security (IPSec) i Advanced Encryption Standard (AES).
  
## <a name="encryption-for-data-at-rest-and-data-in-transit"></a>Szyfrowanie danych w spoczynku i podczas przesyłania danych

  Przykładami danych w spoczynku są pliki przekazane do biblioteki usługi SharePoint, dane programu Project Online, dokumenty przekazane podczas spotkania programu Skype dla firm, wiadomości e-mail i załączniki przechowywane w folderach skrzynki pocztowej oraz pliki przekazane do programu OneDrive dla Firm.
  
 **Przykładami wysyłanych danych** są wiadomości e-mail, które są w trakcie dostarczanej poczty, lub konwersacje odbywające się podczas spotkania online. W Office 365 dane są przesyłania zawsze, gdy urządzenie użytkownika komunikuje się z serwerem firmy Microsoft lub gdy serwer firmy Microsoft komunikuje się z innym serwerem.
  
Dzięki Office 365 dane są zabezpieczone za pomocą wielu warstw i rodzajów szyfrowania. W poniższej tabeli przedstawiono kilka przykładów z linkami do dodatkowych informacji.
  
|**Rodzaje zawartości**|**Technologie szyfrowania**|**Zasoby, aby dowiedzieć się więcej**|
|:-----|:-----|:-----|
|Pliki na urządzeniu. Te pliki mogą obejmować wiadomości e-mail zapisane w folderze, dokumenty Office zapisane na komputerze, tablecie lub telefonie albo dane zapisane w chmurze firmy Microsoft.  <br/> |Funkcją BitLocker w centrach danych firmy Microsoft. Funkcji BitLocker można także używać na komputerach klienckich, takich Windows komputerach i tabletach.  <br/> DKM (Distributed Key Manager) w centrach danych firmy Microsoft  <br/> Klucz klienta dla Microsoft 365  <br/> |[Windows IT: BitLocker](/windows/device-security/bitlocker/bitlocker-overview) <br/> [Centrum zaufania firmy Microsoft: Szyfrowanie](https://www.microsoft.com/TrustCenter/Security/Encryption) <br/> [Seria kontrolek zabezpieczeń w chmurze: Szyfrowanie danych w spoczynku](https://blogs.microsoft.com/microsoftsecure/2015/09/10/cloud-security-controls-series-encrypting-data-at-rest) <br/> [Jak Exchange Online sekrety poczty e-mail](exchange-online-secures-email-secrets.md) <br/> [Szyfrowanie usługi przy użyciu klucza klienta](customer-key-overview.md) <br/> |
|Pliki między użytkownikami. Te pliki mogą zawierać Office lub elementy SharePoint list udostępnionych między użytkownikami.  <br/> |TLS dla przesyłanych plików  <br/> |[Data Encryption in OneDrive for Business and SharePoint Online](data-encryption-in-odb-and-spo.md) <br/> [Skype dla firm Online: Zabezpieczenia i archiwizacja](/office365/servicedescriptions/skype-for-business-online-service-description/skype-for-business-online-features) <br/> |
|Wiadomości e-mail między adresatami. Ta wiadomość e-mail zawiera wiadomości e-mail hostowane przez Exchange Online.  <br/> |Szyfrowanie wiadomości usługi Office 365 usługi Azure Rights Management, usług S/MIME i TLS do przesyłania wiadomości e-mail  <br/> |[Szyfrowanie wiadomości usługi Office 365 (OME)](ome.md) <br/> [Szyfrowanie wiadomości e-mail w Office 365](email-encryption.md) <br/> [Jak Exchange Online usługi TLS do zabezpieczania połączeń e-mail w Office 365](exchange-online-uses-tls-to-secure-email-connections.md) <br/> |
|Czaty, wiadomości i pliki między adresatami przy użyciu Microsoft Teams. <br/> |Teams wiadomości błyskawicznych są szyfrowane przy Teams TLS i MTLS. Ruch multimedialny jest szyfrowany przy użyciu bezpiecznego protokołu RTP (SRTP). Teams do wymiany kluczy szyfrowania używa algorytmów zgodnych z FIPS (Federal Information Processing Standard). <br/> |[Szyfrowanie Teams](/microsoftteams/teams-security-guide#encryption-for-teams) <br/> |

## <a name="what-if-i-need-more-control-over-encryption-to-meet-security-and-compliance-requirements"></a>Co zrobić, jeśli potrzebuję większej kontroli nad szyfrowaniem, aby spełnić wymagania dotyczące zabezpieczeń i zgodności?

Microsoft 365 rozwiązania zarządzane przez firmę Microsoft do szyfrowania plików, szyfrowania plików i szyfrowania skrzynek pocztowych w Office 365. Ponadto firma Microsoft udostępnia rozwiązania do szyfrowania, które możesz zarządzać i kontrolować. Te rozwiązania szyfrowania są zbudowane na platformie Azure.
  
Aby dowiedzieć się więcej, zobacz następujące zasoby:
  
- [Co to jest usługa Azure Rights Management?](/information-protection/understand-explore/what-is-azure-rms)

- [Aktywowanie usługi Zarządzanie prawami w centrum administracyjnym](../enterprise/activate-rms-in-microsoft-365.md)

- [Set up Information Rights Management (IRM) in SharePoint admin center](set-up-irm-in-sp-admin-center.md)

- [Szyfrowanie usługi przy użyciu klucza klienta w Office 365](customer-key-overview.md)

- [Szyfrowanie dwukluczowych danych dla Microsoft 365](double-key-encryption.md)

## <a name="how-do-i"></a>Jak to zrobić?

|**Aby wykonać to zadanie**|**Zobacz te zasoby**|
|:-----|:-----|
|Konfigurowanie szyfrowania dla mojej organizacji|[Konfigurowanie szyfrowania w Office 365 Enterprise](set-up-encryption.md)|
|Wyświetlanie szczegółów certyfikatów, technologii i pakietów szyfrowania TLS|[Szczegóły techniczne dotyczące szyfrowania](technical-reference-details-about-encryption.md)|
|Praca z zaszyfrowanymi wiadomościami na urządzeniu przenośnym|[Wyświetlanie zaszyfrowanych wiadomości na urządzeniu z systemem](https://support.office.com/article/83d60f17-2305-407a-a762-7d518401fdeb) [AndroidWyświetlaj zaszyfrowane wiadomości na iPhone lub iPad](https://support.microsoft.com/en-us/office/view-protected-messages-on-your-iphone-or-ipad-4d631321-0d26-4bcc-a483-d294dd0b1caf)|
|Szyfruj dokument przy użyciu ochrony hasłem. (Ochrona hasłem nie jest obsługiwana w przeglądarce. Aby chronić hasło, używaj Excel, PowerPoint programu Word). |[Dodawanie lub usuwanie ochrony dokumentu, skoroszytu lub prezentacji](https://support.office.com/article/05084cc3-300d-4c1a-8416-38d3e37d6826). Wybierz **sekcję Dodaj ochronę** , a następnie zobacz **Szyfrowanie przy użyciu hasła**.|
|Usuwanie szyfrowania z dokumentu|[Dodawanie lub usuwanie ochrony dokumentu, skoroszytu lub prezentacji](https://support.office.com/article/05084cc3-300d-4c1a-8416-38d3e37d6826). Wybierz **sekcję Usuwanie ochrony** , a następnie zobacz **Usuwanie szyfrowania hasłem**.  |

## <a name="related-topics"></a>Tematy pokrewne

[Planowanie pod Microsoft 365 zabezpieczeń i ochrony informacji](plan-for-security-and-compliance.md)

[10 najlepszych sposobów zabezpieczania planów Microsoft 365 dla firm](/office365/admin/security-and-compliance/secure-your-business-data)

[Szyfrowanie i przepływ odtwarzania na poziomie wideo usługi Microsoft Stream](/stream/network-overview#video-level-encryption-and-playback-flow)