---
title: Dołączanie usługi Microsoft Defender dla IoT za pomocą Ochrona punktu końcowego w usłudze Microsoft Defender
description: Dołącz do usługi Microsoft Defender for IoT, aby uzyskać wgląd i oceny zabezpieczeń skoncentrowane na urządzeniach IoT.
keywords: włączanie łącznika siem, siem, łącznika, informacji o zabezpieczeniach i zdarzeń
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: siosulli
author: siosulli
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: a70b61ff9a27b10e66b6f4537751790eaabc59af
ms.sourcegitcommit: 44ece87e3e0c0c851dfc1e77211ac3e5e4a5b973
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/05/2022
ms.locfileid: "66617287"
---
# <a name="onboard-with-microsoft-defender-for-iot"></a>Dołączanie do usługi Microsoft Defender dla IoT

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**

- [Ochrona punktu końcowego w usłudze Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[!include[Prerelease information](../../includes/prerelease.md)]

> Chcesz doświadczyć Ochrona punktu końcowego w usłudze Microsoft Defender? [Utwórz konto, aby skorzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-enablesiem-abovefoldlink)

Ochrona punktu końcowego w usłudze Microsoft Defender teraz bezproblemowo integruje się z usługą Microsoft Defender for IoT. Ta integracja rozszerza możliwości odnajdywania urządzeń dzięki możliwościom monitorowania bez agenta udostępnianych przez usługę Defender for IoT. Pomoże to zabezpieczyć urządzenia IoT przedsiębiorstwa podłączone do sieci IT, takie jak urządzenia voIP (Voice over Internet Protocol), drukarki i kamery. Umożliwia ona organizacjom korzystanie z jednego zintegrowanego rozwiązania, które zabezpiecza całą infrastrukturę IoT i technologii operacyjnej (OT). Aby uzyskać więcej informacji, zobacz [Ochrona sieci IoT w przedsiębiorstwie](/azure/defender-for-iot/organizations/overview-eiot).

Po zdefiniowaniu planu usługi Defender for IoT i skonfigurowaniu czujnika sieciowego IoT w przedsiębiorstwie dane urządzenia automatycznie uruchamiają przesyłanie strumieniowe do portali Defender for Endpoint i Defender for IoT. 

Integracja usługi Defender for IoT zapewnia większą widoczność, aby ułatwić lokalizowanie, identyfikowanie i zabezpieczanie urządzeń IoT w sieci. Dzięki temu uzyskasz jeden ujednolicony widok pełnego spisu OT/IoT wraz z pozostałymi urządzeniami IT (stacjami roboczymi, serwerami i urządzeniami przenośnymi).

Klienci, którzy zostali dołączeni do usługi Defender for IoT, mają również zalecenia dotyczące zabezpieczeń dotyczące oceny luk w zabezpieczeniach i błędnej konfiguracji dla urządzeń IoT.

## <a name="prerequisites"></a>Wymagania wstępne

Aby zmodyfikować ustawienia integracji usługi Defender for Endpoint, użytkownik musi mieć następujące role:

- Administrator globalny dzierżawy w usłudze Azure Active Directory
- Administrator zabezpieczeń dla subskrypcji platformy Azure, która będzie używana na potrzeby integracji usługi Microsoft Defender for IoT

## <a name="onboard-a-defender-for-iot-plan"></a>Dołączanie planu usługi Defender for IoT

1. W okienku nawigacji portalu [https://security.microsoft.com](https://security.microsoft.com/) wybierz pozycję **Ustawienia** \> **Odnajdywanie urządzeń** \> **Enterprise IoT**.

1. Wybierz następujące opcje dla planu:

   - Wybierz subskrypcję platformy Azure z listy dostępnych subskrypcji w dzierżawie usługi Azure Active Directory, w której chcesz dodać plan.

   - Wybierz plan cenowy, zobowiązanie miesięczne lub roczne albo wersję próbną. Usługa Microsoft Defender for IoT zapewnia 30-dniową bezpłatną wersję próbną dla pierwszych 1000 zatwierdzonych urządzeń do celów ewaluacyjnych.

      Aby uzyskać więcej informacji, zobacz [stronę cennika usługi Microsoft Defender for IoT](https://azure.microsoft.com/pricing/details/iot-defender/).
   
   - Wybierz liczbę zatwierdzonych urządzeń, które chcesz monitorować. Jeśli wybrano wersję próbną, ta sekcja nie jest wyświetlana, ponieważ masz domyślnie 1000 urządzeń.

## <a name="set-up-a-network-sensor"></a>Konfigurowanie czujnika sieciowego

Aby skonfigurować czujnik sieci, subskrypcja platformy Azure musi mieć plan usługi Defender for IoT z dodanymi urządzeniami IoT w przedsiębiorstwie. Aby uzyskać więcej informacji, zobacz [Wprowadzenie do usługi Defender for IoT](/azure/defender-for-iot/organizations/getting-started).

Aby dodać czujnik sieciowy, w obszarze **Konfigurowanie czujników sieciowych** wybierz link **Microsoft Defender for IoT** . Spowoduje to wprowadzenie do procesu konfiguracji czujnika dołączania w Azure Portal. Aby uzyskać więcej informacji, zobacz [Wprowadzenie do usługi Enterprise IoT](/azure/defender-for-iot/organizations/tutorial-getting-started-eiot-sensor).

## <a name="managing-your-iot-devices"></a>Zarządzanie urządzeniami IoT

Aby wyświetlić urządzenia IoT i zarządzać nimi w [portalu Microsoft 365 Defender](https://security.microsoft.com/), przejdź do **spisu urządzeń** z menu nawigacji **Punkty końcowe** i wybierz kartę **Urządzenia IoT**.

Aby uzyskać informacje na temat wyświetlania urządzeń w usłudze Defender for IoT, zobacz [Manage your IoT devices with the device inventory for organizations (Zarządzanie urządzeniami IoT przy użyciu spisu urządzeń dla organizacji](/azure/defender-for-iot/organizations/how-to-manage-device-inventory-for-organizations)).


## <a name="view-devices-alerts-recommendations-and-vulnerabilities"></a>Wyświetlanie urządzeń, alertów, zaleceń i luk w zabezpieczeniach

Po zdefiniowaniu planu i skonfigurowaniu czujnika sieciowego wyświetl wykryte dane i oceny zabezpieczeń w następujących lokalizacjach:

- Wyświetlanie danych urządzenia w usłudze Defender dla punktu końcowego lub usłudze Defender for IoT
- Wyświetlanie alertów, zaleceń i luk w zabezpieczeniach w usłudze Defender for Endpoint

Aby uzyskać więcej informacji, zobacz [stronę cennika usługi Defender for IoT](https://azure.microsoft.com/pricing/details/iot-defender/). 

## <a name="cancel-your-defender-for-iot-plan"></a>Anulowanie planu usługi Defender for IoT

Plan usługi Defender for IoT można anulować na stronie ustawień punktu końcowego usługi Defender w portalu [https://security.microsoft.com](https://security.microsoft.com/) . Po anulowaniu planu integracja zostanie zatrzymana i nie będziesz już uzyskiwać wartości oceny zabezpieczeń w usłudze Defender for Endpoint ani wykrywać nowych urządzeń w usłudze Defender for IoT.

## <a name="see-also"></a>Zobacz też

- [Omówienie wykrywania urządzeń](configure-device-discovery.md)
- [Wykrywanie urządzeń — często zadawane pytania](device-discovery-faq.md)
