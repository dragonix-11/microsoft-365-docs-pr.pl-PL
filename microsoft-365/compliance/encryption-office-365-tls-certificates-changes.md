---
title: Zmiany certyfikatu TLS pakietu Office
description: Jak przygotować się do nadchodzących zmian w certyfikatach TLS pakietu Office.
author: pshelton-skype
ms.author: pshelton
manager: toddbeckett
ms.topic: article
audience: Developer
ms.date: 3/7/2022
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.openlocfilehash: 65b0ffd5d605302dd62369471b65c1ac10aacd40
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66641773"
---
# <a name="office-tls-certificate-changes"></a>Zmiany certyfikatu TLS pakietu Office

Platforma Microsoft 365 aktualizuje usługi obsługujące komunikaty, spotkania, telefonię, głos i wideo w celu używania certyfikatów TLS z innego zestawu głównych urzędów certyfikacji. Ta zmiana jest wprowadzona, ponieważ bieżący główny urząd certyfikacji wygaśnie w maju 2025 r.

Produkty, których dotyczy problem, obejmują:
- Microsoft Teams
- Skype
- Skype dla firm Online
- Microsoft Dynamics 365
- GroupMe
- Kaizala
- Azure Communication Services

Punkty końcowe, których dotyczy problem, obejmują (ale nie są ograniczone do):
- *.teams.microsoft.com
- *.skype.com
- *.skypeforbusiness.com
- *.groupme.com
- *.communication.azure.com
- *.operatorconnect.microsoft.com

Ponadto punkty końcowe usługi Teams i Skype dla firm Online w wystąpieniach chmury krajowej dla instytucji rządowych USA platformy Microsoft 365 dokonają tej samej zmiany, wpływając na punkty końcowe, takie jak:
- *.gcc.teams.microsoft.com
- *.dod.teams.microsoft.us
- *.gov.teams.microsoft.us
- *.online.dod.skypeforbusiness.us
- *.online.gov.skypeforbusiness.us
- *.um-dod.office365.us
- *.um.office365.us

Ta zmiana nie wpłynie na certyfikaty, domeny ani usługi używane w wystąpieniach chmury krajowej w Chinach lub Niemczech platformy Microsoft 365.

Wszystkie informacje o certyfikatach w tym artykule zostały wcześniej udostępnione w [łańcuchach szyfrowania platformy Microsoft 365](./encryption-office-365-certificate-chains.md) nie później niż w październiku 2020 r.

## <a name="when-will-this-change-happen"></a>Kiedy nastąpi ta zmiana?

Usługi zaczęły przechodzić do nowych głównych urzędów certyfikacji w styczniu 2022 r. i będą kontynuowane do października 2022 r.

## <a name="what-is-changing"></a>Co się zmienia?

Obecnie większość certyfikatów protokołu TLS używanych przez usługi platformy Microsoft 365 jest łączona z następującym głównym urzędem certyfikacji:

| Nazwa pospolita urzędu certyfikacji | Odcisk palca (SHA1) |
|--|--|
| [Baltimore CyberTrust Root](https://cacerts.digicert.com/BaltimoreCyberTrustRoot.crt) | d4de20d05e66fc53fe1a50882c78db2852cae474 |

z jednym z następujących pośrednich urzędów certyfikacji:

| Nazwa pospolita urzędu certyfikacji | Odcisk palca (SHA1) |
|--|--|
| [Microsoft RSA TLS CA 01](https://www.microsoft.com/pki/mscorp/Microsoft%20RSA%20TLS%20CA%2001.crt) | 703d7a8f0ebf55aaa59f98eaf4a206004eb2516a |
| [Microsoft RSA TLS CA 02](https://www.microsoft.com/pki/mscorp/Microsoft%20RSA%20TLS%20CA%2002.crt) | b0c2d2d13cdd56cdaa6ab6e2c04440be4a429c75 |

Nowe certyfikaty protokołu TLS używane przez usługi Microsoft 365 będą teraz zawierać łańcuch do jednego z następujących głównych urzędów certyfikacji:

| Nazwa pospolita urzędu certyfikacji | Odcisk palca (SHA1) |
|--|--|
| [DigiCert Global Root G2](https://cacerts.digicert.com/DigiCertGlobalRootG2.crt) | df3c24f9bfd666761b268073fe06d1cc8d4f82a4 |
| [Główny urząd certyfikacji RSA firmy Microsoft 2017](https://www.microsoft.com/pkiops/certs/Microsoft%20RSA%20Root%20Certificate%20Authority%202017.crt) | 73a5e64a3bff8316ff0edccc618a906e4eae4d74 | 
| [Główny urząd certyfikacji Microsoft ECC 2017](https://www.microsoft.com/pkiops/certs/Microsoft%20ECC%20Root%20Certificate%20Authority%202017.crt) | 999a64c37ff47d9fab95f14769891460eec4c3c5 |

z jednym z następujących pośrednich urzędów certyfikacji:

| Nazwa pospolita urzędu certyfikacji | Odcisk palca (SHA1) |
|--|--|
| [Urząd certyfikacji wystawiający protokół TLS platformy Microsoft Azure 01](https://www.microsoft.com/pkiops/certs/Microsoft%20Azure%20TLS%20Issuing%20CA%2001%20-%20xsign.crt) | 2f2877c5d778c31e0f29c7e371df5471bd6731733 |
| [Microsoft Azure TLS Issuing CA 02](https://www.microsoft.com/pkiops/certs/Microsoft%20Azure%20TLS%20Issuing%20CA%2002%20-%20xsign.crt) | e7eea674ca718e3befd90858e09f8372ad0ae2aaa |
| [Microsoft Azure TLS Issuing CA 05](https://www.microsoft.com/pkiops/certs/Microsoft%20Azure%20TLS%20Issuing%20CA%2005%20-%20xsign.crt) | 6c3af02e7f269aa73afd0eff2a88a4a1f04ed1e5 |
| [Microsoft Azure TLS Issuing CA 06](https://www.microsoft.com/pkiops/certs/Microsoft%20Azure%20TLS%20Issuing%20CA%2006%20-%20xsign.crt) | 30e01761ab97e59a06b41ef20af6f2de7ef4f7b0 |

Na przykład jest to prawidłowy certyfikat z jednym z nowych łańcuchów certyfikatów:

![Łańcuch certyfikatów protokołu TLS usługi Teams](../media/teams-tls-certificate-chain.png)

## <a name="will-this-change-affect-me"></a>Czy ta zmiana wpłynie na mnie?

Główny urząd certyfikacji "DigiCert Global Root G2" jest powszechnie zaufany przez systemy operacyjne, w tym Windows, macOS, Android i iOS oraz przez przeglądarki, takie jak Microsoft Edge, Chrome, Safari i Firefox. Oczekujemy, że **nie będzie to miało wpływu na większość klientów platformy Microsoft 365**. 

Może to jednak **mieć wpływ na aplikację, jeśli jawnie określi listę akceptowalnych urzędów certyfikacji**. Ta praktyka jest nazywana "przypinaniem certyfikatu". Klienci, którzy nie mają nowych głównych urzędów certyfikacji na liście akceptowalnych urzędów certyfikacji, otrzymają błędy weryfikacji certyfikatu, które mogą mieć wpływ na dostępność lub funkcję aplikacji.

Poniżej przedstawiono kilka sposobów wykrywania, czy może to mieć wpływ na aplikację:

- Wyszukaj w kodzie źródłowym odcisk palca, nazwę pospolitą lub inne właściwości dowolnego z pośrednich urzędów certyfikacji znajdujących się [tutaj](https://www.microsoft.com/pki/mscorp/cps/default.htm). Jeśli wystąpi dopasowanie, będzie to miało wpływ na aplikację. Aby rozwiązać ten problem, zaktualizuj kod źródłowy, aby dodać właściwości nowych urzędów certyfikacji. Najlepszym rozwiązaniem jest zapewnienie, że urzędy certyfikacji można dodawać lub edytować w krótkim czasie. Przepisy branżowe wymagają wymiany certyfikatów urzędu certyfikacji w ciągu siedmiu dni w pewnych okolicznościach, więc aplikacje implementujące przypinanie certyfikatów muszą szybko reagować na te zmiany.

- Platforma .NET uwidacznia `System.Net.ServicePointManager.ServerCertificateValidationCallback` funkcje i `System.Net.HttpWebRequest.ServerCertificateValidationCallback` wywołania zwrotnego, które umożliwiają deweloperom używanie logiki niestandardowej w celu określenia, czy certyfikaty są prawidłowe, zamiast polegać na standardowym magazynie certyfikatów systemu Windows. Deweloper może dodać logikę sprawdzaną pod kątem określonej nazwy pospolitej lub odcisku palca lub zezwalać tylko na określony główny urząd certyfikacji, taki jak "Baltimore CyberTrust Root". Jeśli aplikacja używa tych funkcji wywołania zwrotnego, upewnij się, że akceptuje ona zarówno stare, jak i nowe główne i pośrednie urzędy certyfikacji.

- Aplikacje natywne mogą używać programu `WINHTTP_CALLBACK_STATUS_SENDING_REQUEST`, co umożliwia aplikacjom natywnym implementowanie logiki weryfikacji certyfikatów niestandardowych. Użycie tego powiadomienia jest rzadkie i wymaga znacznej ilości kodu niestandardowego do zaimplementowania. Podobnie jak powyżej, upewnij się, że aplikacja akceptuje zarówno stare, jak i nowe główne i pośrednie urzędy certyfikacji. 

- Jeśli używasz aplikacji integrującej się z usługą Microsoft Teams, Skype, Skype dla firm Online lub interfejsami API usługi Microsoft Dynamics i nie masz pewności, czy używa ona przypinania certyfikatów, skontaktuj się z dostawcą aplikacji.

- Różne systemy operacyjne i środowiska uruchomieniowe języka komunikujące się z usługami platformy Azure mogą wymagać wykonania innych kroków w celu poprawnego skompilowania i zweryfikowania nowych łańcuchów certyfikatów:
   - **Linux**: wiele dystrybucji wymaga dodania urzędów certyfikacji do `/etc/ssl/certs`programu . Aby uzyskać szczegółowe instrukcje, zapoznaj się z dokumentacją dystrybucji.
   - **Java**: upewnij się, że magazyn kluczy Java zawiera urzędy certyfikacji wymienione powyżej.
   - **System Windows działający w środowiskach rozłączonych**: systemy działające w środowiskach bez połączenia muszą mieć nowe główne urzędy certyfikacji dodane do magazynu `Trusted Root Certification Authorities` i nowe pośrednie urzędy certyfikacji dodane do magazynu `Intermediate Certification Authorities` .
   - **Android**: zapoznaj się z dokumentacją dotyczącą urządzenia i wersji systemu Android.
   - **Urządzenia IoT lub urządzenia osadzone**: urządzenia osadzone, takie jak skrzynki górne zestawu telewizorów, często są dostarczane z ograniczonym zestawem certyfikatów urzędu głównego i nie mają łatwego sposobu aktualizowania magazynu certyfikatów. Jeśli piszesz kod dla niestandardowych urządzeń osadzonych lub IoT lub zarządzasz nimi, upewnij się, że urządzenia ufają nowym głównym urzędom certyfikacji. Może być konieczne skontaktowanie się z producentem urządzenia.

- Jeśli masz środowisko, w którym reguły zapory zezwalają na wywołania wychodzące tylko do określonych punktów końcowych, zezwalaj na następujące adresy URL listy odwołania certyfikatów (CRL) lub Protokołu OCSP (Online Certificate Status Protocol):
   - `http://crl3.digicert.com`
   - `http://crl4.digicert.com`
   - `http://ocsp.digicert.com`
   - `http://crl.microsoft.com`
   - `http://oneocsp.microsoft.com`
   - `http://ocsp.msocsp.com`
   - `http://www.microsoft.com/pkiops`

- Jeśli ta zmiana wpłynie na Ciebie, mogą pojawić się komunikaty o błędach zależne od typu środowiska, w jakim działasz, i scenariusza, na który ma to wpływ. Sprawdź dzienniki zdarzeń aplikacji systemu Windows, dzienniki zdarzeń CAPI2 i niestandardowe dzienniki aplikacji pod kątem komunikatów, które wyglądają następująco:
   ```output
   An operation failed because the following certificate has validation errors:
   
   Subject Name: CN=teams.microsoft.com
   Issuer Name: CN=Microsoft Azure TLS Issuing CA 01, O=Microsoft Corporation, C=US
   
   Errors:
   
   The root of the certificate chain is not a trusted root authority.
   ```

## <a name="when-can-i-retire-the-old-ca-information"></a>Kiedy mogę wycofać stare informacje o urzędzie certyfikacji?

Bieżące certyfikaty głównego urzędu certyfikacji, pośredniego urzędu certyfikacji i liścia nie zostaną odwołane. Istniejące nazwy wspólne urzędu certyfikacji i/lub odciski palca będą wymagane co najmniej do października 2023 r. na podstawie okresu istnienia istniejących certyfikatów.

## <a name="known-issues"></a>Znane problemy

W bardzo rzadkich okolicznościach użytkownicy przedsiębiorstwa mogą zobaczyć błędy weryfikacji certyfikatu, w których główny urząd certyfikacji "DigiCert Global Root G2" jest wyświetlany jako odwołany. Jest to spowodowane znaną usterką systemu Windows w obu następujących warunkach:

- Główny urząd certyfikacji znajduje się w [magazynie certyfikatów CurrentUser\Root](/windows/win32/seccrypto/system-store-locations#cert_system_store_current_user) i nie ma `NotBeforeFileTime` właściwości i `NotBeforeEKU`
- Główny urząd certyfikacji znajduje się również w [magazynie certyfikatów LocalMachine\AuthRoot](/windows/win32/seccrypto/system-store-locations#cert_system_store_local_machine), ale ma właściwości `NotBeforeFileTime` i `NotBeforeEKU`

Wszystkie certyfikaty liści wystawione z tego głównego urzędu certyfikacji po tym, jak `NotBeforeFileTime` pojawią się odwołane. 

Administratorzy mogą zidentyfikować i rozwiązać ten problem, sprawdzając dziennik CAPI2 pod kątem tego błędu:

```text
Log Name:      Microsoft-Windows-CAPI2/Operational
Source:        Microsoft-Windows-CAPI2
Date:          6/23/2022 8:36:39 AM
Event ID:      11
Task Category: Build Chain
Level:         Error
[...]
        <ChainElement>
          <Certificate fileRef="DF3C24F9BFD666761B268073FE06D1CC8D4F82A4.cer" subjectName="DigiCert Global Root G2" />
          [...]
          <TrustStatus>
            <ErrorStatus value="4000024" CERT_TRUST_IS_REVOKED="true" CERT_TRUST_IS_UNTRUSTED_ROOT="true" CERT_TRUST_IS_EXPLICIT_DISTRUST="true" />
            <InfoStatus value="10C" CERT_TRUST_HAS_NAME_MATCH_ISSUER="true" CERT_TRUST_IS_SELF_SIGNED="true" CERT_TRUST_HAS_PREFERRED_ISSUER="true" />
          </TrustStatus>
          [...]
          <RevocationInfo freshnessTime="PT0S">
            <RevocationResult value="80092010">The certificate is revoked.</RevocationResult>
          </RevocationInfo>
        </ChainElement>
      </CertificateChain>
      <EventAuxInfo ProcessName="Teams.exe" />
      <Result value="80092010">The certificate is revoked.</Result>
```
Zwróć uwagę na obecność `CERT_TRUST_IS_EXPLICIT_DISTRUST="true"` elementu. 

Możesz potwierdzić, że istnieją dwie kopie głównego urzędu certyfikacji o różnych `NotBeforeFileTime` właściwościach, uruchamiając następujące `certutil` polecenia i porównując dane wyjściowe:

```
certutil -store -v authroot DF3C24F9BFD666761B268073FE06D1CC8D4F82A4
certutil -user -store -v root DF3C24F9BFD666761B268073FE06D1CC8D4F82A4
```

Użytkownik może rozwiązać ten problem, usuwając kopię głównego urzędu certyfikacji w magazynie certyfikatów `CurrentUser\Root` :
```
certutil -user -delstore root DF3C24F9BFD666761B268073FE06D1CC8D4F82A4
```