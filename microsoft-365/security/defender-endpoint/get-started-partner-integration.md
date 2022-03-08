---
title: Zostań partnerem programu Microsoft Defender for Endpoint
ms.reviewer: ''
description: Dowiedz się, jakie kroki i wymagania należy spełnić, aby zintegrować swoje rozwiązanie z programem Microsoft Defender for Endpoint i zostać partnerem.
keywords: partner, integracja, weryfikacja rozwiązania, certyfikacja, wymagania, członek, misa, portal aplikacji
ms.prod: w10
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
ms.openlocfilehash: b063d8435817d7dd64c3febf6e3399f3876ef894
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63319829"
---
# <a name="become-a-microsoft-defender-for-endpoint-partner"></a>Zostań partnerem programu Microsoft Defender for Endpoint

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


Aby zostać partnerem rozwiązania Defender for Endpoint, musisz wykonać poniższe czynności.

## <a name="step-1-subscribe-to-a-microsoft-defender-for-endpoint-license"></a>Krok 1. Subskrybowanie licencji programu Microsoft Defender dla punktu końcowego

Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink). Subskrybowanie umożliwia korzystanie z usługi Microsoft Defender for Endpoint dzierżawy z maksymalnie trzema urządzeniami do opracowywania rozwiązań integrjących się z usługą Microsoft Defender for Endpoint.

## <a name="step-2-fulfill-the-solution-validation-and-certification-requirements"></a>Krok 2. Spełnienie wymagań sprawdzania poprawności rozwiązania i certyfikacji

Najlepszym sposobem, aby partnerzy technologii potwierdzili swoje działania integracji, jest zatwierdzenie proponowanego projektu integracji  przez klienta (\(klient może skorzystać z opcji Polecanie partnera i aplikacji partnerów API > Partner [](https://security.microsoft.com/interoperability/partnersapps)\) na stronie Aplikacji partnerskiej w programie Microsoft 365 Defender i przetestować go oraz przetestować i zmienić w zespole programu Microsoft Defender for Endpoint.

Gdy zespół usługi Microsoft Defender for Endpoint przejdą przegląd i zatwierdzi integrację, zostaniesz jej partnerem w witrynie Microsoft Intelligent Security Association.

## <a name="step-3-get-listed-in-the-microsoft-defender-for-endpoint-partner-application-portal"></a>Krok 3. Uzyskiwanie listy w portalu aplikacji partnerów programu Microsoft Defender for Endpoint

Program Microsoft Defender for Endpoint obsługuje odnajdowanie i integrację aplikacji innych firm przy użyciu strony partnera [](partner-applications.md) produktu osadzonej w portalu zarządzania programem Microsoft Defender for Endpoint.

Aby Twoja firma została wymieniona jako partner na stronie partnera w produkcie, musisz podać następujące informacje:

1. Logo kwadratowe (SVG).
2. Nazwa produktu do zaprezentowania.
3. Podaj 15-słowny opis produktu.
4. Link do strony docelowej klienta, aby ukończyć integrację lub wpis w blogu, który będzie zawierał wystarczające informacje dla klientów. Wszelkie informacje prasowe, w tym nazwa produktu programu Microsoft Defender for Endpoint, powinny być przeglądane przez zespoły marketingowe i inżynierskie. Poczekaj co najmniej 10 dni na proces przeglądu.
5. Jeśli korzystasz z wielodostępności usługi Azure AD, do śledzenia użycia aplikacji będzie potrzebna nazwa aplikacji usługi Azure AD.
6. Uwzględnij pole User-Agent w każdym wywołaniu interfejsu API wykonanym dla usługi Microsoft Defender for Endpoint publicznego zestawu interfejsów API lub Graph interfejsów API zabezpieczeń. Będą one używane do celów statystycznych, rozwiązywania problemów i rozpoznawania partnerów. Ponadto ten krok jest wymagany dla członkostwa w skojarzenia microsoft Intelligent Security Association (MISA).

   Wykonaj następujące czynności:

   - Ustaw pole User-Agent w każdym nagłówku żądania HTTP na poniższy format.

     ```http
     MdePartner-{CompanyName}-{ProductName}/{Version}
     ```

     Na przykład User-Agent:

     ```http
     MdePartner-Contoso-ContosoCognito/1.0.0
     ```

   - Aby uzyskać więcej informacji, [zobacz RFC 2616 sekcja-14.43](https://tools.ietf.org/html/rfc2616#section-14.43).

Współpraca z programem Microsoft Defender for Endpoint ułatwia naszym wspólnym klientom dalsze usprawnianie, integrację i usprawnianie obrony. Cieszymy się, że wybrano Cię na partnera programu Microsoft Defender for Endpoint i naszym wspólnym celem jest skuteczna ochrona klientów i ich zasobów przez zapobieganie współczesnym zagrożeniam i reagowanie na nie.

## <a name="misa-nomination"></a>Misa 
Dostawcy zarządzanych usług zabezpieczeń (MSSP) i niezależni dostawcy oprogramowania (ISV) mogą być nominowani do organizacji Microsoft Intelligent Security Association (MISA). Aby uzyskać więcej informacji, zobacz [strona informacje O BŁĘDACH](https://www.microsoft.com/security/business/intelligent-security-association).


## <a name="related-topics"></a>Tematy pokrewne

- [Szanse partnerów technicznych](partner-integration.md)
