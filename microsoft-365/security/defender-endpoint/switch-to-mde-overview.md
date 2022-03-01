---
title: Przejście z ochrony punktu końcowego innych niż firma Microsoft na program Microsoft Defender dla punktu końcowego
description: Przejdź na usługę Microsoft Defender for Endpoint, która zawiera Program antywirusowy Microsoft Defender rozwiązania do ochrony punktu końcowego.
keywords: migracja, windows defender, zaawansowana ochrona punktu końcowego, oprogramowanie antywirusowe, ochrona przed złośliwym oprogramowaniem, tryb pasywny, tryb aktywny
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: deniseb
author: denisebmsft
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-migratetomdatp
- m365solution-overview
- m365solution-mcafeemigrate
- m365solution-symantecmigrate
- m365initiative-defender-endpoint
ms.topic: overview
ms.custom: migrationguides
ms.date: 11/29/2021
ms.reviewer: jesquive, chventou, jonix, chriggs, owtho
ms.technology: mde
ms.openlocfilehash: eb0971c6f5b8fd8bf37f3d33cb65cff8d331e0d0
ms.sourcegitcommit: aac7e002ec6e10a41baa2d0bd38614b0ed471a70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/27/2022
ms.locfileid: "63009583"
---
# <a name="make-the-switch-from-non-microsoft-endpoint-protection-to-microsoft-defender-for-endpoint"></a>Przejście z ochrony punktu końcowego innych niż firma Microsoft na program Microsoft Defender dla punktu końcowego

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804) Jeśli rozważasz zmianę rozwiązania ochrony punktu końcowego innego niż firma Microsoft na program [Microsoft Defender for Endpoint](microsoft-defender-endpoint.md) (Defender for Endpoint) lub jesteś na etapie planowania, użyj tego artykułu jako przewodnika. W tym artykule opisano ogólny proces przechodzenia do usługi Defender dla punktu końcowego.

:::image type="content" source="images/nonms-mde-migration.png" alt-text="Przełącz swoje rozwiązanie ochrony punktu końcowego na program Defender dla punktu końcowego.":::

Po rozpoczęciu pracy z usługą Defender for Endpoint zaczniesz od ochrony przed oprogramowaniem antywirusowym/złośliwym firmy Microsoft w trybie aktywnym. Następnie konfigurujesz tryb Program antywirusowy Microsoft Defender pasywnego i dodajesz urządzenia do usługi Defender for Endpoint. Następnie skonfiguruj funkcje ochrony punktu końcowego, ustaw Program antywirusowy Microsoft Defender tryb aktywny i sprawdź, czy wszystko działa poprawnie. Na koniec należy usunąć rozwiązanie inne niż firmy Microsoft.

## <a name="the-migration-process"></a>Proces migracji

Proces migrowania do usługi Defender for Endpoint można podzielić na trzy fazy, zgodnie z opisem w poniższej tabeli:

![Proces migracji MDE.](images/phase-diagrams/migration-phases.png)

<br/><br/>

|Faza|Opis|
|--|--|
|[Przygotowywanie do migracji](switch-to-mde-phase-1.md)|W [okresie **przygotowywanie**](switch-to-mde-phase-1.md): <br/>1. Aktualizowanie urządzeń w organizacji.<br/>2. Uzyskaj program Defender dla punktu końcowego.<br/>3. Planowanie ról i uprawnień oraz udzielanie dostępu do portalu Microsoft 365 Defender sieci.<br/>4. Skonfiguruj ustawienia serwera proxy i Internetu urządzenia, aby włączyć komunikację między urządzeniami organizacji a usługą Defender for Endpoint. |
|[Konfigurowanie usługi Defender dla punktu końcowego](switch-to-mde-phase-2.md)|Na [etapie **konfiguracji**](switch-to-mde-phase-2.md): <br/>1. Włącz/ponownie Program antywirusowy Microsoft Defender i ustaw go jako pasywny.<br/>2. Konfigurowanie usługi Defender dla punktu końcowego.<br/>3. Dodaj program Defender for Endpoint do listy wykluczeń istniejącego rozwiązania.<br/>4. Dodaj istniejące rozwiązanie do listy wykluczeń dla Program antywirusowy Microsoft Defender.<br/>5. Konfigurowanie grup urządzeń, kolekcji i jednostek organizacyjnych.<br/>6. Skonfiguruj zasady ochrony przed złośliwym oprogramowaniem i ustawienia ochrony w czasie rzeczywistym.|
|[Onboard to Defender for Endpoint](switch-to-mde-phase-3.md)|W [fazie **na wsadu**](switch-to-mde-phase-3.md): <br/>1. Nawłoń urządzenia do usługi Defender for Endpoint.<br/>2. Uruchom test wykrywania.<br/>3. Upewnij się, Program antywirusowy Microsoft Defender działa w trybie pasywnym.<br/>4. Pobierz aktualizacje dla Program antywirusowy Microsoft Defender.<br/>5. Odinstaluj istniejące rozwiązanie do ochrony punktu końcowego.<br/>6. Upewnij się, że program Defender for Endpoint działa poprawnie.|

## <a name="whats-included-in-microsoft-defender-for-endpoint"></a>Co zawiera program Microsoft Defender for Endpoint?

W tym przewodniku po migracji skupimy [](microsoft-defender-antivirus-in-windows-10.md) się na ochronie następnej generacji [i](overview-endpoint-detection-response.md) wykrywanie i reagowanie w punktach końcowych punktem wyjścia do przechodzenia do usługi Defender dla punktu końcowego. Jednak program Defender for Endpoint oferuje znacznie więcej niż ochrona antywirusowa i ochrona punktu końcowego. Program Defender for Endpoint to ujednolicona platforma do zapobiegania wykrywaniu naruszenia, automatycznego badania i reagowania. W poniższej tabeli podsumowano funkcje i możliwości w programie Defender for Endpoint.

<br/><br/>

|Funkcja/funkcja|Opis|
|---|---|
|[Zagrożenia & zarządzanie lukami w zabezpieczeniach](next-gen-threat-and-vuln-mgt.md)|Funkcje & zarządzanie lukami w zabezpieczeniach zagrożeń ułatwiają identyfikowanie, ocenianie i korygowanie problemów w punktach końcowych (takich jak urządzenia).|
|[Zmniejszenie powierzchni ataków](overview-attack-surface-reduction.md)|Reguły ograniczania powierzchni ataków pomagają chronić urządzenia i aplikacje organizacji przed cyberatakami i atakami.|
|[Ochrona następnej generacji](microsoft-defender-antivirus-in-windows-10.md)|Ochrona następnej generacji obejmuje Program antywirusowy Microsoft Defender blokowania zagrożeń i złośliwego oprogramowania.|
|[Wykrywanie punktu końcowego i odpowiedź](overview-endpoint-detection-response.md)|Funkcje wykrywania punktów końcowych i reakcji wykrywają, analizują i reagują na próby dostępu oraz aktywne naruszenia.|
|[Zaawansowane łowy](advanced-hunting-overview.md)|Zaawansowane funkcje łowiectwo umożliwiają Twoje zespołowi operacyjnemu ds. zabezpieczeń znajdowanie wskaźników i jednostek znanych lub potencjalnych zagrożeń.|
|[Blokowanie i blokowanie zachowań](behavioral-blocking-containment.md)|Możliwości blokowania i blokowania zachowań pomagają identyfikować i zatrzymywać zagrożenia na podstawie ich zachowań i drzew procesowych nawet wtedy, gdy zagrożenie rozpoczęło się.|
|[Zautomatyzowane badanie i rozwiązywanie problemów](automated-investigations.md)|Automatyczne badanie i reagowanie umożliwia sprawdzanie alertów i podejmowanie natychmiastowych działań naprawczych w celu rozwiązania naruszeń.|
|[Służba chłoniania](microsoft-threat-experts.md) zagrożeń (Microsoft Threat Experts)|Usługi chłoniania zagrożeń zapewniają zespołom zespołów ds. bezpieczeństwa monitorowanie i analizę na poziomie ekspertów, a także pomagają zagwarantować, że nie przegapisz kluczowych zagrożeń.|

**Chcesz dowiedzieć się więcej? Zobacz [Defender, aby uzyskać informacje na temat punktu końcowego](microsoft-defender-endpoint.md).**

## <a name="next-step"></a>Następny krok

- Przejdź do [tematu Przygotowywanie do migracji](switch-to-mde-phase-1.md).
