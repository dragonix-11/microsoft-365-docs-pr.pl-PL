---
title: Migrowanie z usługi ochrony innej firmy do Ochrona usługi Office 365 w usłudze Microsoft Defender
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: Admin
ms.date: ''
ms.topic: conceptual
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
ms.custom: ''
description: Poznaj właściwy sposób migracji z usług ochrony innych firm lub urządzeń, takich jak Google Postini, Barracuda Spam and Virus Firewall lub Cisco IronPort, aby Ochrona usługi Office 365 w usłudze Microsoft Defender ochronę.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 2f67135e2b8a3700a2fb6a6e24fc4f66696db2e3
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65098719"
---
# <a name="migrate-from-a-third-party-protection-service-or-device-to-microsoft-defender-for-office-365"></a>Migrowanie z usługi ochrony innej firmy lub urządzenia do Ochrona usługi Office 365 w usłudze Microsoft Defender

**Dotyczy**
- [Usługi Microsoft Defender dla usługi Office 365 (plan 1 i plan 2)](defender-for-office-365.md)

Jeśli masz już istniejącą usługę ochrony innej firmy lub urządzenie znajdujące się przed Microsoft 365, możesz użyć tego przewodnika do migracji ochrony w celu Ochrona usługi Office 365 w usłudze Microsoft Defender  aby uzyskać korzyści wynikające ze skonsolidowanego środowiska zarządzania, potencjalnie obniżonych kosztów (przy użyciu produktów, za które już płacisz) oraz dojrzałego produktu ze zintegrowaną ochroną bezpieczeństwa. Aby uzyskać więcej informacji, zobacz [Ochrona usługi Office 365 w usłudze Microsoft Defender](https://www.microsoft.com/security/business/threat-protection/office-365-defender).

Ten przewodnik zawiera konkretne i praktyczne kroki migracji oraz przyjmuje następujące fakty:

- Masz już Microsoft 365 skrzynki pocztowe, ale obecnie używasz usługi lub urządzenia innej firmy do ochrony poczty e-mail. Poczta z Internetu przepływa przez usługę ochrony przed dostarczeniem do organizacji Microsoft 365, a ochrona Microsoft 365 jest jak najmniejsza (nigdy nie jest całkowicie wyłączona, na przykład ochrona przed złośliwym oprogramowaniem jest zawsze wymuszana).

  :::image type="content" source="../../media/mdo-migration-before.png" alt-text="Poczta przepływa z Internetu za pośrednictwem usługi ochrony lub urządzenia innej firmy przed dostarczeniem do Microsoft 365" lightbox="../../media/mdo-migration-before.png":::

- Jesteś poza fazą badania i rozważania dotyczącą ochrony przez Ochrona usługi Office 365 w usłudze Defender. Jeśli musisz ocenić Ochrona usługi Office 365 w usłudze Defender, aby zdecydować, czy jest to odpowiednie dla Twojej organizacji, zalecamy rozważenie opcji opisanych w [temacie Wypróbuj Ochrona usługi Office 365 w usłudze Microsoft Defender](try-microsoft-defender-for-office-365.md).

- Masz już zakupione licencje Ochrona usługi Office 365 w usłudze Defender.

- Musisz wycofać istniejącą usługę ochrony innej firmy, co oznacza, że ostatecznie musisz wskazać rekordy MX dla domen poczty e-mail, aby Microsoft 365. Gdy skończysz, poczta z Internetu będzie przepływać bezpośrednio do Microsoft 365 i będzie chroniona wyłącznie przez Exchange Online Protection (EOP) i Ochrona usługi Office 365 w usłudze Defender.

  :::image type="content" source="../../media/mdo-migration-after.png" alt-text="Poczta przepływa z Internetu do Microsoft 365" lightbox="../../media/mdo-migration-after.png":::

Wyeliminowanie istniejącej usługi ochrony na rzecz Ochrona usługi Office 365 w usłudze Defender jest dużym krokiem, którego nie należy lekceważyć ani spieszyć się z wprowadzaniem zmian. Wskazówki zawarte w tym przewodniku migracji pomogą Ci w uporządkowaniu przenoszenia ochrony z minimalnymi zakłóceniami dla użytkowników.

Bardzo ogólne kroki migracji przedstawiono na poniższym diagramie. Rzeczywiste kroki są wymienione w sekcji o nazwie [Proces migracji](#the-migration-process) w dalszej części tego artykułu.

:::image type="content" source="../../media/mdo-migration-overview.png" alt-text="Proces migracji z rozwiązania ochrony innej firmy lub urządzenia do Ochrona usługi Office 365 w usłudze Defender" lightbox="../../media/mdo-migration-overview.png":::

## <a name="why-use-the-steps-in-this-guide"></a>Dlaczego warto skorzystać z kroków opisanych w tym przewodniku?

W branży IT niespodzianki są na ogół złe. Po prostu przerzucanie rekordów MX, aby wskazać Microsoft 365 bez wcześniejszych i przemyślanych testów, spowoduje wiele niespodzianek. Przykład:

- Ty lub Twoi poprzednicy prawdopodobnie poświęcacie dużo czasu i wysiłku, dostosowując istniejącą usługę ochrony w celu optymalnego dostarczania poczty (innymi słowy blokując to, co należy zablokować, i zezwalając na to, co musi być dozwolone). Niemal gwarantowana pewność, że nie wszystkie dostosowania w bieżącej usłudze ochrony są wymagane w Ochrona usługi Office 365 w usłudze Defender. Istnieje również bardzo możliwe, że Ochrona usługi Office 365 w usłudze Defender wprowadzi nowe problemy (zezwalanie lub bloki), które nie wystąpiły lub nie były wymagane w bieżącej usłudze ochrony.
- Dział pomocy technicznej i pracownicy ochrony muszą wiedzieć, co robić w Ochrona usługi Office 365 w usłudze Defender. Jeśli na przykład użytkownik skarży się na brakujący komunikat, czy dział pomocy technicznej wie, gdzie i jak go szukać? Prawdopodobnie znają narzędzia w istniejącej usłudze ochrony, ale co z narzędziami w Ochrona usługi Office 365 w usłudze Defender?

Jeśli natomiast wykonasz kroki opisane w tym przewodniku migracji, uzyskasz następujące wymierne korzyści dla migracji:

- Minimalne zakłócenia dla użytkowników.
- Obiektywne dane z Ochrona usługi Office 365 w usłudze Defender, których można używać podczas raportowania postępu i powodzenia migracji do zarządzania.
- Wczesne zaangażowanie i instrukcje dla personelu pomocy technicznej i pracowników ochrony.

Tym bardziej zapoznasz się ze sposobem, w jaki Ochrona usługi Office 365 w usłudze Defender wpłynie na organizację, tym lepsze będzie przejście dla użytkowników, pracowników pomocy technicznej, pracowników ochrony i zarządzania.

Ten przewodnik migracji zawiera plan stopniowego "obracania wybierania", dzięki czemu można monitorować i testować wpływ Ochrona usługi Office 365 w usłudze Defender na użytkowników i ich wiadomości e-mail, aby można było szybko reagować na wszelkie napotkane problemy.

## <a name="the-migration-process"></a>Proces migracji

Proces migracji z usługi ochrony innej firmy do Ochrona usługi Office 365 w usłudze Defender można podzielić na trzy fazy, zgodnie z opisem w poniższej tabeli:

:::image type="content" source="../../media/phase-diagrams/migration-phases.png" alt-text="Proces migracji do Ochrona usługi Office 365 w usłudze Defender" lightbox="../../media/phase-diagrams/migration-phases.png":::

|Fazy|Opis|
|---|---|
|[Przygotowanie do migracji](migrate-to-defender-for-office-365-prepare.md)|<ol><li>[Spis ustawień w istniejącej usłudze ochrony](migrate-to-defender-for-office-365-prepare.md#inventory-the-settings-at-your-existing-protection-service)</li><li>[Sprawdź istniejącą konfigurację ochrony w Microsoft 365](migrate-to-defender-for-office-365-prepare.md#check-your-existing-protection-configuration-in-microsoft-365)</li><li>[Sprawdzanie konfiguracji routingu poczty](migrate-to-defender-for-office-365-prepare.md#check-your-mail-routing-configuration)</li><li>[Przenoszenie funkcji modyfikujące komunikaty do Microsoft 365](migrate-to-defender-for-office-365-prepare.md#move-features-that-modify-messages-into-microsoft-365)</li><li>[Definiowanie środowiska spamu i użytkowników zbiorczych](migrate-to-defender-for-office-365-prepare.md#define-spam-and-bulk-user-experiences)</li><li>[Identyfikowanie i wyznaczanie kont priorytetów](migrate-to-defender-for-office-365-prepare.md#identify-and-designate-priority-accounts)</li></ol>|
|[Konfigurowanie Ochrona usługi Office 365 w usłudze Defender](migrate-to-defender-for-office-365-setup.md)|<ol><li>[Tworzenie grup dystrybucyjnych dla użytkowników pilotażowych](migrate-to-defender-for-office-365-setup.md#step-1-create-distribution-groups-for-pilot-users)</li><li>[Konfigurowanie przesyłania przez użytkownika na potrzeby raportowania komunikatów użytkowników](migrate-to-defender-for-office-365-setup.md#step-2-configure-user-submission-for-user-message-reporting)</li><li>[Obsługa lub tworzenie reguły przepływu poczty SCL=-1](migrate-to-defender-for-office-365-setup.md#step-3-maintain-or-create-the-scl-1-mail-flow-rule)</li><li>[Konfigurowanie rozszerzonego filtrowania dla łączników](migrate-to-defender-for-office-365-setup.md#step-4-configure-enhanced-filtering-for-connectors)</li><li>[Tworzenie zasad ochrony pilotażowej](migrate-to-defender-for-office-365-setup.md#step-5-create-pilot-protection-policies)</li></ol>|
|[Dołączanie do Ochrona usługi Office 365 w usłudze Defender](migrate-to-defender-for-office-365-onboard.md)|<ol><li>[Rozpoczynanie dołączania Teams zabezpieczeń](migrate-to-defender-for-office-365-onboard.md#step-1-begin-onboarding-security-teams)</li><li>[(Opcjonalnie) Wykluczenie użytkowników pilotażowych z filtrowania według istniejącej usługi ochrony](migrate-to-defender-for-office-365-onboard.md#step-2-optional-exempt-pilot-users-from-filtering-by-your-existing-protection-service)</li><li>[Dostrajanie inteligencji fałszowania](migrate-to-defender-for-office-365-onboard.md#step-3-tune-spoof-intelligence)</li><li>[Dostrajanie ochrony przed personifikacją i analizy skrzynek pocztowych](migrate-to-defender-for-office-365-onboard.md#step-4-tune-impersonation-protection-and-mailbox-intelligence)</li><li>[Mierzenie i dostosowywanie danych przesyłanych przez użytkowników przy użyciu danych przesyłanych przez użytkownika](migrate-to-defender-for-office-365-onboard.md#step-5-use-data-from-user-submissions-to-measure-and-adjust)</li><li>[(Opcjonalnie) Dodawanie większej liczby użytkowników do pilotażu i iterowanie](migrate-to-defender-for-office-365-onboard.md#step-6-optional-add-more-users-to-your-pilot-and-iterate)</li><li>[Rozszerzanie ochrony Microsoft 365 na wszystkich użytkowników i wyłączanie reguły przepływu poczty SCL=-1](migrate-to-defender-for-office-365-onboard.md#step-7-extend-microsoft-365-protection-to-all-users-and-turn-off-the-scl-1-mail-flow-rule)</li><li>[Przełączanie rekordów MX](migrate-to-defender-for-office-365-onboard.md#step-8-switch-your-mx-records)</li></ol>|

## <a name="next-step"></a>Następny krok

- Przejdź do [fazy 1: Przygotowanie](migrate-to-defender-for-office-365-prepare.md).
