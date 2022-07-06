---
title: Używanie zasad DLP dla aplikacji w chmurze innych niż Microsoft
f1.keywords:
- CSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: article
f1_keywords:
- ms.o365.cc.DLPLandingPage
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MET150
ms.custom:
- seo-marvel-apr2020
description: Dowiedz się, jak używać zasad dlp dla aplikacji w chmurze innych niż Microsoft.
ms.openlocfilehash: a50849b53819a7c5872c3ec8cb279ffa8d14e27f
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66634410"
---
# <a name="use-data-loss-prevention-policies-for-non-microsoft-cloud-apps"></a>Używanie zasad ochrony przed utratą danych dla aplikacji w chmurze innych niż Microsoft

Możesz określić zakres zasad DLP, aby Microsoft Defender for Cloud Apps do monitorowania, wykrywania i wykonywania akcji, gdy elementy poufne są używane i udostępniane za pośrednictwem aplikacji w chmurze innych niż Microsoft.

## <a name="before-you-begin"></a>Przed rozpoczęciem

### <a name="skusubscriptions-licensing"></a>Licencjonowanie jednostek SKU/subskrypcji

Przed rozpoczęciem korzystania z zasad DLP potwierdź [subskrypcję platformy Microsoft 365](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=1) i wszelkie dodatki. Aby uzyskać dostęp do tej funkcji i korzystać z niej, musisz mieć jedną z następujących subskrypcji lub dodatków:

- Microsoft 365 E5
- Zgodność platformy Microsoft 365 E5
- Zabezpieczenia platformy Microsoft 365 E5

### <a name="permissions"></a>Uprawnienia
Użytkownik, który tworzy zasady DLP, powinien mieć następujące uprawnienia:

- Administrator globalny
- Administrator zgodności: przypisywanie w Azure AD
- Administrator danych zgodności: przypisywanie w Azure AD

### <a name="prepare-your-defender-for-cloud-apps-environment"></a>Przygotowywanie środowiska usługi Defender for Cloud Apps

Przed skonfigurowaniem zasad DLP o zakresie Microsoft Defender for Cloud Apps należy przygotować środowisko usługi Defender for Cloud Apps. Aby uzyskać instrukcje, zobacz [Szybki start: rozpoczynanie pracy z Microsoft Defender for Cloud Apps](/defender-cloud-apps/get-started).

### <a name="connect-a-non-microsoft-cloud-app"></a>Łączenie aplikacji w chmurze innej niż Microsoft

Aby korzystać z zasad DLP, które są ograniczone do określonej aplikacji w chmurze innej niż Microsoft, aplikacja musi być połączona z usługą Defender for Cloud Apps. Aby uzyskać informacje, zobacz:

- [Connect Box](/defender-cloud-apps/connect-box)
- [Łączenie z usługą Dropbox](/defender-cloud-apps/connect-dropbox)
- [Łączenie z obszarem roboczym Google](/defender-cloud-apps/connect-google-workspace)
- [Łączenie z usługą Salesforce](/defender-cloud-apps/connect-salesforce)
- [Łączenie aplikacji Cisco Webex](/defender-cloud-apps/connect-webex)

Po połączeniu aplikacji w chmurze z usługą Defender for Cloud Apps można utworzyć dla nich zasady DLP.

## <a name="create-a-dlp-policy-scoped-to-a-non-microsoft-cloud-app"></a>Tworzenie zasad DLP o zakresie aplikacji w chmurze spoza firmy Microsoft

Zapoznaj się [z artykułem Tworzenie, testowanie i dostrajanie zasad DLP](create-test-tune-dlp-policy.md) dla procedur tworzenia zasad DLP. Należy pamiętać o tych kwestiach podczas konfigurowania zasad.

- Wybierz opcję włącz **lokalizację Microsoft Defender for Cloud Apps**.
- Aby wybrać określoną aplikację lub wystąpienie, wybierz pozycję **Wybierz wystąpienie**. Jeśli nie wybierzesz wystąpienia, zasady będą ograniczone do wszystkich połączonych aplikacji w dzierżawie Microsoft Defender for Cloud Apps.
- Możesz wybrać jedną z wielu **akcji** do wymuszenia w aplikacjach innych firm. Aby ograniczyć aplikacje innych firm, wybierz pozycję **Ogranicz aplikacje innych firm,** a następnie wybierz określone akcje.

![lista akcji do wymuszenia w połączonych aplikacjach w chmurze](../media/dlp-non-microsoft-cloud-app-restrict-third-party-apps.png)

> [!NOTE]
> Podczas tworzenia zasad DLP o zakresie Microsoft Defender for Cloud Apps te same zasady zostaną automatycznie utworzone w Microsoft Defender for Cloud Apps.

## <a name="see-also"></a>Zobacz też

- [Tworzenie testu i dostrajanie zasad DLP](./create-test-tune-dlp-policy.md)
- [Wprowadzenie do domyślnych zasad DLP](./get-started-with-the-default-dlp-policy.md)
- [Twórz zasady DLP na podstawie szablonu](./create-a-dlp-policy-from-a-template.md)
