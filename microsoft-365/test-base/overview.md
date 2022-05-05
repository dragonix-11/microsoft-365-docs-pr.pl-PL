---
title: Omówienie
description: Omówienie bazy testów
search.appverid: MET150
author: Tinacyt
ms.author: tinachen
manager: rshastri
audience: Software-Vendor
ms.topic: how-to
ms.date: 07/06/2021
ms.service: virtual-desktop
ms.localizationpriority: medium
ms.collection: TestBase-M365
ms.custom: ''
ms.reviewer: mapatel
f1.keywords: NOCSH
ms.openlocfilehash: 13eaea1e62dd030f86e08d885ad743d673d6142c
ms.sourcegitcommit: b16520d8bfe04b29274f7a129d90ef116bb77f69
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/05/2022
ms.locfileid: "65231698"
---
# <a name="what-is-test-base-for-microsoft-365"></a>Co to jest baza testowa dla Microsoft 365?

Baza testowa to usługa platformy Azure, która umożliwia testowanie aplikacji opartych na danych przy jednoczesnym zapewnieniu użytkownikom dostępu do inteligentnych testów z dowolnego miejsca na świecie.

Następujące jednostki są zachęcane do dołączania swoich aplikacji, plików binarnych i skryptów testowych do bazy testowej dla usługi Microsoft 365: niezależni dostawcy oprogramowania (ISV), integratorzy systemu (SI) w celu weryfikowania swoich aplikacji i specjalistów IT, którzy chcą weryfikować swoje aplikacje biznesowe poprzez integrację z Microsoft Intune.

## <a name="why-test-your-application-with-test-base"></a>Dlaczego warto przetestować aplikację przy użyciu bazy testowej?

Usługa Test Base for Microsoft 365 może w razie potrzeby dostosować się do rozszerzenia macierzy testowania, dzięki czemu będziesz mieć pewność co do integralności, zgodności i użyteczności aplikacji.

Baza testowa umożliwia aplikacji kontynuowanie pracy zgodnie z oczekiwaniami, nawet jeśli zależności platformy są różne, a nowe aktualizacje są stosowane przez usługę aktualizacji Windows. Dzięki bazie testów można uniknąć pogorszenia, przedłużających się zobowiązań czasowych oraz kosztów konfigurowania i utrzymywania złożonego środowiska laboratoryjnego na potrzeby testowania aplikacji.

Ponadto można automatycznie testować zgodność z aktualizacjami zabezpieczeń i funkcji dla Windows przy użyciu bezpiecznych maszyn wirtualnych, jednocześnie uzyskując dostęp do światowej klasy analizy na potrzeby testowania aplikacji. Możesz również przetestować aplikacje pod kątem zgodności z wstępnymi aktualizacjami zabezpieczeń systemu Windows, przesyłając żądanie uzyskania dostępu.

## <a name="how-does-test-base-work"></a>Jak działa baza testów?

Aby zarejestrować się w usłudze Test Base, zobacz [Tworzenie nowego konta bazy testów](createAccount.md).

Po zarejestrowaniu klienta w usłudze Test Base wystarczy rozpocząć przekazywanie pakietów aplikacji do testowania.

Po pomyślnym przekazaniu pakiety są testowane pod kątem Windows aktualizacji wersji wstępnej.

Po pomyślnym zakończeniu testów początkowych klient może dokładnie zapoznać się ze szczegółowymi informacjami na temat analizy wydajności i regresji, aby wykryć, czy aktualizacje zawartości w wersji wstępnej w jakikolwiek sposób obniżają wydajność aplikacji.

Jeśli jednak pakiet nie przeszedł żadnego testu, klient może również wykorzystać Szczegółowe informacje z regresji pamięci lub procesora CPU, aby skorygować awarię, a następnie zaktualizować pakiet w razie potrzeby.

W przypadku bazy testowej klient może użyć jednej lokalizacji do zarządzania wszystkimi testowanymi pakietami, co może również ułatwić przekazywanie i aktualizowanie pakietów w celu generowania nowych wersji aplikacji w razie potrzeby.

> [!NOTE]
> **Aby klienci mogli korzystać z zawartości aktualizacji przed wydaniem, muszą w szczególności zażądać do niej dostępu. Po zatwierdzeniu żądania dostępu do aktualizacji wersji wstępnej przekazane pakiety zostaną automatycznie przetestowane pod kątem wersji wstępnej Windows aktualizacji wersji systemu operacyjnego wybranych podczas dołączania**.

Następnie po udostępnieniu nowych Windows aktualizacji wersji wstępnej pakiety aplikacji są automatycznie testowane z nową zawartością w wersji wstępnej. Następnie może być wymagana dodatkowa runda szczegółowych informacji. Jeśli klienci nie zażądają konkretnie dostępu, pakiety aplikacji będą testowane tylko w bieżącej wersji Windows.

Po pomyślnym przetestowaniu pakietów klienci mogą dostarczać je swoim klientom oprogramowania i użytkownikom końcowym z ufnością i zapewnieniem, że baza testowa wykonała swoje zadanie.

## <a name="next-steps"></a>Następne kroki

Aby rozpocząć pracę, postępuj zgodnie z linkiem
> [!div class="nextstepaction"]
> [Tworzenie nowego konta bazy testowej | Microsoft Docs](createaccount.md)
