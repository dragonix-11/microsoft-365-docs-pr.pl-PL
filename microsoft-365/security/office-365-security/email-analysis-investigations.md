---
title: Analiza poczty e-mail w badaniach nad programem Microsoft Defender dla Office 365
f1.keywords:
- NOCSH
author: dansimp
ms.author: dansimp
manager: dansimp
audience: ITPro
ms.topic: article
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
keywords: automatyczna reakcja na incydenty, badania, działania naprawcze i ochrona przed zagrożeniami
description: Zobacz, jak działa analiza wiadomości e-mail w badaniach w programie Microsoft Defender dla Office 365.
ms.custom:
- air
- seo-marvel-mar2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 5737a2d1974805dc55b85b7ff8f4117cbc1da898
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63318189"
---
# <a name="email-analysis-in-investigations-for-microsoft-defender-for-office-365"></a>Analiza poczty e-mail w badaniach nad programem Microsoft Defender dla Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Microsoft Defender dla Office 365 plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Podczas automatycznego badania alertów usługa Microsoft Defender dla systemu Office 365 analizuje oryginalną wiadomość e-mail pod celu zidentyfikowania zagrożeń i identyfikuje inne wiadomości e-mail związane z oryginalną wiadomością e-mail i potencjalnie w ramach ataków. Ta analiza jest ważna, ponieważ ataki poczty e-mail rzadko zawierają jedną wiadomość e-mail.

Analiza automatycznej analizy poczty e-mail identyfikuje klastry poczty e-mail przy użyciu atrybutów z oryginalnej wiadomości e-mail do kwerendy dotyczącej wiadomości e-mail wysyłanych i otrzymywanych przez Twoją organizację. Przypomina to analityka operacji zabezpieczeń, który może poszukać powiązanych wiadomości e-mail w Eksploratorze lub łowiectwo zaawansowane. Do identyfikowania zgodnych wiadomości e-mail używa się kilku zapytań, ponieważ atakujący zazwyczaj płynną zmiana parametrów wiadomości e-mail w celu uniknięcia wykrywania zabezpieczeń. Analiza klastrowania wykonuje te testy w celu ustalenia sposobu obsługi wiadomości e-mail biorących udział w analizie:

- Analiza poczty e-mail tworzy zapytania (klastry) wiadomości e-mail przy użyciu atrybutów z oryginalnej wiadomości e-mail — wartości nadawcy (adres IP, domena wysyłająca) i zawartość (temat, identyfikator klastrów) w celu znalezienia powiązanych wiadomości e-mail.
- Jeśli analiza oryginalnych adresów URL i plików wiadomości e-mail będzie się identyfikować, że niektóre są złośliwe (złośliwe lub wyłudające), będą również tworzyć zapytania lub grupy wiadomości e-mail zawierające złośliwy adres URL lub plik.
- Analiza grupowania poczty e-mail zlicza zagrożenia skojarzone z zgodnymi wiadomościami e-mail w klastrze, aby ustalić, czy te wiadomości e-mail są złośliwe, podejrzane lub nie mają żadnych wyraźnych zagrożeń. Jeśli grupa wiadomości e-mail spełniających to zapytanie ma wystarczająco dużo spamu, normalnego wyłudu, wysokiego ufności wyłudu lub zagrożeń związanych z złośliwym oprogramowaniem, grupa wiadomości e-mail otrzymuje zastosowany do niego typ zagrożenia.
- Analiza grupowania poczty e-mail sprawdza również najnowszą lokalizację dostarczania oryginalnych wiadomości e-mail i wiadomości e-mail w grupach poczty e-mail, aby pomóc w zidentyfikowaniu, czy wiadomości e-mail nadal wymagają usunięcia, czy zostały już usunięte lub zostały usunięte bądź niemożliwe. Taka analiza jest ważna, ponieważ osoby atakujące morph złośliwej zawartości oraz zasady zabezpieczeń i ochrona mogą się różnić w zależności od skrzynki pocztowej. Funkcja ta umożliwia prowadzenie sytuacji, w których złośliwa zawartość może nadal być w skrzynkach pocztowych, nawet jeśli co najmniej jedna złośliwa wiadomość e-mail została wykryta i usunięta przez automatyczne przeczyszczanie bez godziny (ZAP).
- Grupowanie wiadomości e-mail uznane za złośliwe ze względu na złośliwe oprogramowanie, phish, złośliwe pliki lub złośliwe adresy URL będą otrzymywać oczekujące działanie w celu "miękkiego usunięcia" wiadomości e-mail, gdy nadal znajdują się one w skrzynce pocztowej w chmurze (skrzynce odbiorczej lub folderze wiadomości-śmieci). Jeśli złośliwych wiadomości e-mail lub grup poczty e-mail nie ma tylko "Nie ma w skrzynce pocztowej" (zablokowany, poddany kwarantannie, niepowodzenie, "miękkie usunięcie itp.") lub "Lokalnie/zewnętrznie" z żadnymi w skrzynce pocztowej w chmurze, nie zostanie skonfigurować żadne oczekujące działanie w celu ich usunięcia.
- Jeśli którykolwiek z grup poczty e-mail zostanie określony jako złośliwy, zagrożenie zidentyfikowane przez klaster zostanie zastosowane z powrotem do oryginalnej wiadomości e-mail, która jest zaangażowana w badanie. Takie zachowanie przypomina analityka operacji zabezpieczających, który korzysta z wyników wyszukiwania poczty e-mail w celu określenia werdyktu oryginalnej wiadomości e-mail na podstawie zgodnych wiadomości e-mail. Dzięki temu niezależnie od tego, czy adresy URL, pliki lub źródłowe wskaźniki poczty e-mail w oryginalnej wiadomości e-mail są wykrywane, czy nie, system może identyfikować złośliwe wiadomości e-mail, które mogą być wykrywane za pomocą personalizacji, płynna zmiana, morphingu, technik atakujących lub innych technik atakujących.
- W śledztwie w sprawie naruszenia bezpieczeństwa użytkowników są tworzone dodatkowe klastry poczty e-mail w celu identyfikowania potencjalnych problemów z pocztą e-mail tworzona przez skrzynkę pocztową. Ten proces obejmuje oczyszczanie klastrów poczty e-mail (prawidłowe wiadomości e-mail od użytkownika, potencjalne eksstrukcje danych oraz potencjalne wiadomości e-mail poleceń i kontrolek), podejrzane klastry poczty e-mail (wiadomości e-mail zawierające spam lub zwykły kod) oraz złośliwe klastry wiadomości (wiadomości e-mail zawierające złośliwe oprogramowanie lub wiadomości o dużej pewności). Te klastry poczty e-mail dostarczają dane analityków operacji zabezpieczających w celu ustalenia, jakich innych problemów należy rozwiązać w przypadku naruszenia bezpieczeństwa, oraz wglądu w to, które wiadomości e-mail mogą wyzwolić oryginalne alerty (na przykład wyłudzy/spam, które wyzwoliły ograniczenia wysyłania przez użytkowników)

Analiza grupowania poczty e-mail za pomocą zapytań o podobnym podobieństwu i złośliwej jednostki zapewnia, że problemy z pocztą e-mail są w pełni identyfikowane i czyszczone, nawet jeśli w przypadku zidentyfikowania tylko jednej wiadomości e-mail w ramach ataku zostanie zidentyfikowana tylko jedna wiadomość e-mail. Za pomocą linków z widoków panelu bocznego klasteru poczty e-mail można otwierać zapytania w Eksploratorze lub łowy zaawansowane, aby przeprowadzać bardziej szczegółowe analizy i w razie potrzeby zmieniać zapytania. Ta funkcja umożliwia ręczne uściślianie i rozwiązywanie problemów, jeśli zapytania klastrów poczty e-mail są zbyt wąskie lub zbyt szerokie (w tym niepowiązane wiadomości e-mail).

Oto dodatkowe ulepszenia analizy poczty e-mail w badaniach.

## <a name="air-investigation-ignores-advanced-delivery-items-secops-mailbox-and-phishedu-messages"></a>Funkcja AIR investigation ignoruje zaawansowane elementy dostarczania (skrzynka pocztowa usługi SecOps i wiadomości phishEDU)

Podczas analizy grupowania poczty e-mail wszystkie zapytania grupujące ignorują skrzynki pocztowe zabezpieczeń ustawione jako skrzynki pocztowe operacji zabezpieczeń w zaawansowanych zasadach dostarczania. Podobnie zapytania grupujące pocztę e-mail ignorują wiadomości symulacyjne phish (education) skonfigurowane w zaawansowanych zasadach dostarczania. Ani wartości wykluczeń SecOps, ani PhishEdu nie są wyświetlane w zapytaniu, aby atrybuty klastrowania były prostsze i łatwiejsze do odczytania. To wyłączenie gwarantuje, że analizy zagrożeń i operacyjne skrzynki pocztowe (skrzynki pocztowe usługi SecOps) i symulacje phish (PhishEdu) są ignorowane podczas analizy zagrożeń i nie są usuwane podczas jakiegokolwiek rozwiązywania problemów.

>[!Note]
>Podczas otwierania klastrów poczty e-mail w celu wyświetlenia go w Eksploratorze ze szczegółów grup poczty e-mail filtry skrzynek pocztowych PhishEdu i SecOps będą stosowane w Eksploratorze, ale nie będą wyświetlane. Jeśli zmienisz filtry, daty lub odświeżenie zapytania w Eksploratorze na stronie — wówczas wykluczenia filtrowania PhishEdu/SecOps zostaną usunięte, a wiadomości e-mail zgodne z tymi ustawieniami zostaną ponownie wyświetlone. Jeśli odświeżysz stronę Eksploratora przy użyciu funkcji odświeżania w przeglądarce, zostaną załadowane ponownie oryginalne filtry zapytań, w tym filtry PhishEdu/SecOps, ale usunięcie wszystkich kolejnych wprowadzonych zmian.
>

## <a name="air-updates-pending-email-action-status"></a>Aktualizacje AIR oczekujące na stan akcji poczty e-mail

Analiza wiadomości e-mail z badania oblicza w czasie badania zagrożenia i lokalizacje poczty e-mail w celu utworzenia dowodów i akcji badania. Te dane mogą być nieaktualne i nieaktualne, gdy działania poza badaniem wpływają na wiadomości e-mail biorące udział w śledztwie. Na przykład działania związane z operacjami zabezpieczeń ręcznego chłoniania i rozwiązywania problemów mogą oczyścić wiadomości e-mail uwzględnione w śledztwie. Podobnie akcje usuwania zatwierdzone w równoległych badaniach lub automatyczne przeczyszczanie automatyczne (ZAP, Zero-godzinne) automatyczne akcje kwarantanny mogą spowodować usunięcie wiadomości e-mail. Ponadto opóźnione wykrywanie zagrożeń po dostarczeniu wiadomości e-mail może zmienić liczbę zagrożeń uwzględnionych w zapytaniach e-mail/grupach prowadzonych w związku z prowadzonym badaniem.

Aby upewnić się, że akcje analizy są aktualne, wszelkie badanie, w którym występują akcje oczekujące, będzie okresowo ponownie uruchamiać zapytania analizy poczty e-mail w celu zaktualizowania lokalizacji i zagrożeń poczty e-mail.

- Zmiana danych klastrów poczty e-mail spowoduje zaktualizowanie zagrożeń i najnowszych lokalizacji dostarczania.
- Jeśli w skrzynce pocztowej nie ma już wiadomości e-mail lub grupowania poczty e-mail z akcjami oczekującymi, to akcja oczekująca zostanie anulowana, a złośliwy adres e-mail/klaster zostanie uznany za działania naprawcze.
- Po zakończeniu działania wszystkich zagrożeń związanych z badaniem lub ich anulowaniu zgodnie z powyższymi informacjami stan badania zostanie rozwiązany, a pierwotny alert zostanie rozwiązany.

## <a name="the-display-of-incident-evidence-for-email-and-email-clusters"></a>Wyświetlanie dowodów zdarzenia w przypadku poczty e-mail i grup poczty e-mail

Na karcie Dowód i odpowiedź na zdarzenie, na podstawie wiadomości e-mail **, są** teraz wyświetlane następujące informacje.

:::image type="content" source="../../media/email-analysis-investigations/email-analysis-evidence-example.png" alt-text="Przykład informacji analizy wiadomości e-mail w materiałach dowodowych i odpowiedzi." lightbox="../../media/email-analysis-investigations/email-analysis-evidence-example.png":::

Z numerowanych objaśnień na ilustracji:

1. Oprócz Centrum akcji możesz także wykonywać **działania naprawcze**.
2. Można podjąć działania naprawcze dla grup poczty e-mail ze złośliwym werdyktem (ale nie **podejrzanym**).
3. W przypadku e-maili werdykt spamu wyłudzanie informacji jest podzielone na wysokie zaufanie i normalny wyłudzanie informacji.

   W przypadku złośliwego werdyktu kategorie zagrożeń to złośliwe oprogramowanie, wyłudzy o dużej pewności, złośliwy adres URL i złośliwy plik.

   W przypadku podejrzanego werdyktu kategorie zagrożeń to spam i zwykły wyłud.

4. Liczba wiadomości e-mail według jest oparta na najnowszej lokalizacji dostarczania i zawiera liczniki wiadomości e-mail w skrzynkach pocztowych, nie w skrzynkach pocztowych ani lokalnie.
5. Uwzględnia datę i czas zapytania, które może zostać zaktualizowane w celu uzyskania najnowszych danych.

W przypadku grup poczty e-mail lub  poczty e-mail na karcie Jednostki zdarzenia pozycja Prevented **oznacza, że** w skrzynce pocztowej nie było złośliwych wiadomości e-mail dla tego elementu (poczty lub klastrów). Oto przykład.

:::image type="content" source="../../media/email-analysis-investigations/email-analysis-evidence-example-prevented.png" alt-text="Przykład wiadomości e-mail, która jest blokowana." lightbox="../../media/email-analysis-investigations/email-analysis-evidence-example-prevented.png":::

W tym przykładzie wiadomość e-mail jest złośliwa, ale nie znajduje się w skrzynce pocztowej.

## <a name="next-steps"></a>Następne kroki

- [Wyświetlanie oczekujących lub ukończonych działań naprawczych](air-review-approve-pending-completed-actions.md)
