---
title: Co nowego w programie Microsoft Defender dla punktu końcowego w systemie Android
description: Dowiedz się więcej o głównych zmianach dotyczących poprzednich wersji programu Microsoft Defender dla punktu końcowego w systemie Android.
keywords: microsoft, defender, Microsoft Defender for Endpoint, mac, installation, macos, whatsnew
ms.prod: m365-security
ms.mktglfcycl: security
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-security-compliance
ms.topic: reference
ms.technology: mde
ms.openlocfilehash: d250fefbdcc2c268563b6321ee7d91eca4881063
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63328697"
---
# <a name="whats-new-in-microsoft-defender-for-endpoint-on-android"></a>Co nowego w programie Microsoft Defender dla punktu końcowego w systemie Android

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

## <a name="microsoft-defender-for-endpoint-is-now-microsoft-defender-in-the-play-store"></a>Program Microsoft Defender for Endpoint jest teraz programem Microsoft Defender w sklepie Play

Program Microsoft Defender for Endpoint jest teraz dostępny jako **program Microsoft Defender** w sklepie Play. W tej aktualizacji aplikacja będzie dostępna w wersji Preview dla klientów indywidualnych  w Usa — zależnie od tego, jak logujesz się do aplikacji przy użyciu konta służbowego, będziesz mieć dostęp do funkcji programu Microsoft Defender dla punktu końcowego lub funkcji programu Microsoft Defender dla poszczególnych osób. Aby uzyskać [więcej informacji,](https://www.microsoft.com/en-us/microsoft-365/microsoft-defender-for-individuals) zobacz ten blog.

## <a name="threat-and-vulnerability-management"></a>Zarządzanie zagrożeniami i lukami w zabezpieczeniach

25 stycznia 2022 r. ogłosiliśmy ogólną dostępność funkcji zarządzania zagrożeniami i lukami w zabezpieczeniach w systemach Android i iOS. Aby uzyskać więcej szczegółowych informacji, [zobacz wpis w witrynie TechCommunity tutaj](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/announcing-general-availability-of-vulnerability-management/ba-p/3071663).

## <a name="upcoming-permission-changes-for-microsoft-defender-for-endpoint-running-android-11-or-later-nov-2021"></a>Nadchodzące zmiany uprawnień dla programu Microsoft Defender dla punktu końcowego z systemem Android 11 lub nowszym (lis 2021)

Kompilacja wersji: Miesiąc wydania 1.0.3501.0301: nov 2021 Microsoft Defender for Endpoint opublikowała tę aktualizację wymaganą przez [firmę Google](https://developer.android.com/distribute/play-policies#APILevel30) do uaktualnienia do interfejsu API systemu Android 30. Ta zmiana spowoduje monitowanie użytkowników o uzyskanie dostępu do nowych uprawnień do magazynowania [dla urządzeń](https://developer.android.com/training/data-storage/manage-all-files#all-files-access-google-play) z systemem Android 11 lub nowszym. Użytkownicy będą musieli zaakceptować to nowe uprawnienie do magazynowania po zaktualizowaniu aplikacji Defender w kompilacji 1.0.3501.0301 lub nowszej. Zapewni to, że funkcja zabezpieczeń aplikacji programu Defender for Endpoint będzie działać bez zakłóceń. Aby uzyskać więcej informacji, zapoznaj się z poniższymi sekcjami.

**Jak wpłynie to na Twoją organizację:** Te zmiany zajdą, jeśli korzystasz z programu Microsoft Defender dla punktu końcowego na urządzeniach z systemem Android 11 lub nowszym i zaktualizowano usługę Defender for Endpoint w celu wydania kompilacji 1.0.3501.0301 lub nowszej.

> [!NOTE]
> Nowych uprawnień do magazynowania nie może skonfigurować administrator w celu automatycznego zatwierdzania za pośrednictwem Microsoft Endpoint Manager. Użytkownik będzie musiał podjąć działania, aby udzielić dostępu do tego uprawnienia.

- **Środowisko użytkownika:** Użytkownicy otrzymają powiadomienie z informacją o brakujących uprawnieniach do zabezpieczeń aplikacji. Jeśli użytkownik odmówi tego uprawnienia, funkcja "Zabezpieczenia aplikacji" zostanie wyłączona na urządzeniu. Jeśli użytkownik nie zaakceptuje lub nie odmówi uprawnień, nadal będzie otrzymywać monit podczas odblokowywania urządzenia lub otwierania aplikacji, dopóki nie zostanie zatwierdzony.

> [!NOTE]
> Jeśli w Twojej organizacji jest przeglądana wersja zapoznawcza funkcji ochrony przed naruszeniami i jeśli użytkownik nie udzielił mu nowych uprawnień do magazynowania w ciągu 7 dni od aktualizacji do najnowszej wersji, użytkownik może utracić dostęp do zasobów firmy.

**Co należy zrobić, aby przygotować się:**

Powiadom użytkowników i pomoc techniczną (w razie potrzeby), że użytkownicy będą musieli zaakceptować nowe uprawnienia po wyświetleniu monitu po zaktualizowaniu usługi Defender dla punktu końcowego w celu kompilacji 1.0.3501.0301 lub nowszej wersji. Aby zaakceptować te uprawnienia, użytkownicy powinni:

1. Naciśnij powiadomienie w aplikacji Defender for Endpoint lub otwórz aplikację Defender for Endpoint. Użytkownicy zobaczą ekran z listą potrzebnych uprawnień. Obok uprawnienia do Storage brakuje zielonego Storage wyboru.

2. Naciśnij **pozycję Rozpocznij**.

3. Naciśnij przełącznik **Zezwalaj na dostęp, aby zarządzać wszystkimi plikami.**

4. Urządzenie jest teraz chronione.

  > [!NOTE]
  > To uprawnienie umożliwia programowi Microsoft Defender for Endpoint uzyskiwanie dostępu do magazynu na urządzeniu użytkownika, co pomaga wykrywać i usuwać złośliwe i niechciane aplikacje. Program Microsoft Defender for Endpoint uzyskuje dostęp/skanuje tylko plik pakietu aplikacji systemu Android (.defender). Na urządzeniach z profilem służbowym program Defender for Endpoint skanuje tylko pliki związane z pracą.
