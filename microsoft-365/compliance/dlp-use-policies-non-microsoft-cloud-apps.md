---
title: Korzystanie z zasad ochrony przed utratą danych dla aplikacji w chmurze innych niż firmy Microsoft
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
description: Dowiedz się, jak używać zasad dlp dla aplikacji w chmurze innych niż firmy Microsoft.
ms.openlocfilehash: b374f9b85d41b6dd6a5281e17347dffd414361da
ms.sourcegitcommit: 1ef176c79a0e6dbb51834fe30807409d4e94847c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/19/2021
ms.locfileid: "63005248"
---
# <a name="use-data-loss-prevention-policies-for-non-microsoft-cloud-apps"></a>Korzystanie z zasad ochrony przed utratą danych dla aplikacji w chmurze innych niż firmy Microsoft

Zasady ochrony przed utratą danych (DLP) dla aplikacji w chmurze innych niż firmy Microsoft są częścią pakietu funkcji ochrony przed utratą danych firmy Microsoft 365. Korzystając z tych funkcji, możesz odnajdować i chronić poufne elementy w Microsoft 365 usługach firmy Microsoft. Aby uzyskać więcej informacji na temat wszystkich usług firmy Microsoft w zakresie ochrony przed utratą danych, zobacz [Informacje na temat ochrony przed utratą danych](dlp-learn-about-dlp.md).

Zasady DLP mogą być stosowane do aplikacji w chmurze innych niż firmy Microsoft w celu monitorowania i wykrywania, gdy poufne elementy są używane i udostępniane za pośrednictwem aplikacji w chmurze innych niż firmy Microsoft. Zasady te zapewniają widoczność i kontrolę nad prawidłowym używaniem i ochroną oraz pomagają zapobiec ryzykownych zachowaniom, które mogłyby je naruszyć.

## <a name="before-you-begin"></a>Przed rozpoczęciem

### <a name="skusubscriptions-licensing"></a>Licencjonowanie subskrypcji/licencji na subskrypcje sKU

Przed rozpoczęciem używania zasad DLP w aplikacjach w chmurze innych niż firma Microsoft potwierdź swoją [Microsoft 365 subskrypcję](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=1) i dodatki. Aby uzyskać dostęp do tej funkcji i korzystać z nich, musisz mieć jedną z tych subskrypcji lub dodatków:

- Microsoft 365 E5
- Zgodność platformy Microsoft 365 E5
- Zabezpieczenia platformy Microsoft 365 E5

### <a name="permissions"></a>Uprawnienia
Użytkownik, który tworzy zasady DLP, powinien:

- Administrator globalny
- Administrator zgodności: przypisywanie w usłudze Azure AD
- Administrator danych zgodności: przypisywanie w usłudze Azure AD

### <a name="prepare-your-defender-for-cloud-apps-environment"></a>Przygotowywanie środowiska usługi Defender dla aplikacji w chmurze

Zasady DLP dla aplikacji w chmurze innych niż firmy Microsoft korzystają z funkcji DLP aplikacji w chmurze usługi Defender. Aby z niego korzystać, należy przygotować środowisko usługi Defender dla aplikacji w chmurze. Aby uzyskać instrukcje, [zobacz Ustawianie natychmiastowego wglądu, ochrony i akcji zarządzania dla aplikacji](/cloud-app-security/getting-started-with-cloud-app-security#step-1-set-instant-visibility-protection-and-governance-actions-for-your-apps).

### <a name="connect-a-non-microsoft-cloud-app"></a>Połączenie aplikację w chmurze firmy Microsoft

Aby używać zasad DLP do konkretnej aplikacji w chmurze innych niż firmy Microsoft, aplikacja musi być połączona z usługą Defender for Cloud Apps. Aby uzyskać informacje, zobacz:

- [Połączenie Box](/cloud-app-security/connect-box-to-microsoft-cloud-app-security)
- [Połączenie Dropbox](/cloud-app-security/connect-dropbox-to-microsoft-cloud-app-security)
- [Połączenie G-Workspace](/cloud-app-security/connect-google-apps-to-microsoft-cloud-app-security)
- [Połączenie Salesforce](/cloud-app-security/connect-salesforce-to-microsoft-cloud-app-security)
- [Połączenie Cisco Webex](/cloud-app-security/connect-webex-to-microsoft-cloud-app-security)

Po połączeniu aplikacji w chmurze z usługą Defender dla aplikacji w chmurze możesz utworzyć dla nich Microsoft 365 DLP.

> [!NOTE]
> Za pomocą programu Microsoft Defender dla aplikacji w chmurze można również tworzyć zasady DLP dla aplikacji w chmurze firmy Microsoft. Jednak zalecane jest używanie funkcji ochrony przed Microsoft 365 do tworzenia zasad DLP i zarządzania nimi w aplikacjach firmy Microsoft w chmurze.

## <a name="create-a-dlp-policy-to-a-non-microsoft-cloud-app"></a>Tworzenie zasad DLP dla aplikacji w chmurze innych niż firmy Microsoft

Po wybraniu lokalizacji zasad DLP włącz lokalizację programu **Microsoft Defender dla aplikacji w** chmurze.

- Aby wybrać konkretną aplikację lub wystąpienie, wybierz **pozycję Wybierz wystąpienie**.
- Jeśli nie wybierzesz wystąpienia, zasady będą używane wszystkie połączone aplikacje w dzierżawie usługi Microsoft Defender dla aplikacji w chmurze.

   ![Lokalizacje do zastosowania zasad.](../media/1-dlp-non-microsoft-cloud-app-choose-instance.png)

   ![Box-US i Box-General.](../media/2-dlp-non-microsoft-cloud-app-box.png)

Możesz wybrać różne akcje dla każdej obsługiwanej aplikacji w chmurze innych niż firmy Microsoft. Dla każdej aplikacji istnieją różne możliwe akcje (w zależności od interfejsu API aplikacji w chmurze).

![Utwórz regułę.](../media/3-dlp-non-microsoft-cloud-app-create-rule.png)

Podczas tworzenia reguły w zasadach DLP możesz wybrać akcję dla aplikacji w chmurze innych niż firmy Microsoft. Aby ograniczyć aplikacje innych firm, wybierz **pozycję Ogranicz aplikacje innych firm**.

![Ograniczanie aplikacji innych firm.](../media/4-dlp-non-microsoft-cloud-app-restrict-third-party-apps.png)

> [!NOTE]
> Zasady DLP stosowane do aplikacji innych niż firmy Microsoft używają programu Microsoft Defender dla aplikacji w chmurze. Po utworzeniu zasad DLP dla aplikacji innych niż firmy Microsoft te same zasady zostaną automatycznie utworzone w usłudze Microsoft Defender dla aplikacji w chmurze.

Aby uzyskać informacje na temat tworzenia i konfigurowania zasad DLP, zobacz [Tworzenie testowania i dostosowywanie zasad DLP](./create-test-tune-dlp-policy.md).

## <a name="see-also"></a>Zobacz też

- [Tworzenie i dostosowywanie zasad DLP](./create-test-tune-dlp-policy.md)
- [Wprowadzenie do domyślnych zasad DLP](./get-started-with-the-default-dlp-policy.md)
- [Tworzenie zasad DLP na podstawie szablonu](./create-a-dlp-policy-from-a-template.md)
