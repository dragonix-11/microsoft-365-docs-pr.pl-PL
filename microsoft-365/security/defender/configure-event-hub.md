---
title: Konfigurowanie centrum zdarzeń
description: Dowiedz się, jak skonfigurować centrum zdarzeń
keywords: centrum zdarzeń, konfigurowanie, szczegółowe informacje
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-security-compliance
ms.custom: admindeeplinkDEFENDER
ms.topic: article
MS.technology: mde
ms.openlocfilehash: 40211d37b8b036f93b826a383d9d0aa87f44fc68
ms.sourcegitcommit: 292de1a7e5ecc2e9e6187126aebba6d3b9416dff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/06/2022
ms.locfileid: "65243079"
---
# <a name="configure-your-event-hub"></a>Konfigurowanie centrum zdarzeń

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

Dowiedz się, jak skonfigurować centrum zdarzeń, aby umożliwić pozyskiwanie zdarzeń z Microsoft 365 Defender.

## <a name="set-up-the-required-resource-provider-in-the-event-hub-subscription"></a>Konfigurowanie wymaganego dostawcy zasobów w subskrypcji centrum zdarzeń

1. Zaloguj się do witryny [Azure Portal](https://portal.azure.com).
1. Wybierz pozycję **Subskrypcje** > **{ Wybierz subskrypcję centrum zdarzeń, która zostanie wdrożona dla dostawców** **zasobów**. > 
1. Sprawdź, czy plik **Microsoft.Szczegółowe informacje** Dostawca jest zarejestrowany. W przeciwnym razie zarejestruj go.

:::image type="content" source="../../media/f893db7a7b1f7aa520e8b9257cc72562.png" alt-text="Strona dostawcy usług w portalu Microsoft Azure" lightbox="../../media/f893db7a7b1f7aa520e8b9257cc72562.png":::

## <a name="set-up-azure-active-directory-app-registration"></a>Konfigurowanie rejestracji aplikacji Azure Active Directory

> ! [UWAGA] Musisz mieć rolę administratora lub Azure Active Directory (AAD), aby umożliwić spoza administratorom rejestrowanie aplikacji. Musisz również mieć rolę właściciel lub administrator dostępu użytkowników, aby przypisać jednostkę usługi do roli. Aby uzyskać więcej informacji, zobacz [Tworzenie jednostki usługi & aplikacji Azure AD w portalu — Platforma tożsamości Microsoft \| Microsoft Docs](/azure/active-directory/develop/howto-create-service-principal-portal).

1. Utwórz nową rejestrację (która z natury tworzy jednostkę usługi) w **Azure Active Directory** \> **Rejestracje aplikacji** \> **Nowej rejestracji.**

1. Wypełnij formularz tylko nazwą (nie jest wymagany identyfikator URI przekierowania).

    :::image type="content" source="../../media/336bc84e6be23900c43232b4ef0c253c.png" alt-text="Sekcja wyświetlania nazwy aplikacji w portalu Microsoft Azure" lightbox="../../media/336bc84e6be23900c43232b4ef0c253c.png":::


    :::image type="content" source="../../media/06ac04c4ff713c2065cec2ef2f99a294.png" alt-text="Sekcja Informacje o przeglądzie w portalu Microsoft Azure" lightbox="../../media/06ac04c4ff713c2065cec2ef2f99a294.png":::

1. Utwórz wpis tajny, klikając pozycję **Certyfikaty & wpisy tajne** \> **Nowy klucz tajny klienta**:

    :::image type="content" source="../../media/d2ef88d3d2310d2c60c294b569cdf02e.png" alt-text="Sekcja Klucz tajny klienta w portalu Microsoft Azure" lightbox="../../media/d2ef88d3d2310d2c60c294b569cdf02e.png":::
    

> [!WARNING]
> **Nie będzie można ponownie uzyskać dostępu do wpisu tajnego klienta, więc pamiętaj, aby go zapisać**.

## <a name="set-up-event-hub-namespace"></a>Konfigurowanie przestrzeni nazw centrum zdarzeń

1. Utwórz przestrzeń nazw centrum zdarzeń:

    Przejdź **do obszaru Event Hub \> Dodaj** i wybierz warstwę cenową, jednostki przepływności i automatyczne nadmuchiwanie (wymaga standardowej ceny i w obszarze funkcji) odpowiednie dla oczekiwanego obciążenia. Aby uzyskać więcej informacji, zobacz [Cennik — centrum zdarzeń \| Microsoft Azure](https://azure.microsoft.com/pricing/details/event-hubs/)

    > [!NOTE]
    > Możesz użyć istniejącego centrum zdarzeń, ale przepływność i skalowanie są ustawiane na poziomie przestrzeni nazw, dlatego zaleca się umieszczenie centrum zdarzeń we własnej przestrzeni nazw.

   :::image type="content" source="../../media/ebc4ca37c342ad1da75c4aee4018e51a.png" alt-text="Sekcja centrum zdarzeń w portalu Microsoft Azure" lightbox="../../media/ebc4ca37c342ad1da75c4aee4018e51a.png":::

1. Potrzebny będzie również identyfikator zasobu tej przestrzeni nazw centrum zdarzeń. Przejdź do strony \> Przestrzeni nazw usługi Azure Event Hub Właściwości. Skopiuj tekst w obszarze Identyfikator zasobu i zapisz go do użycia w sekcji konfiguracji Microsoft 365 poniżej.

    :::image type="content" source="../../media/759498162a4e93cbf17c4130d704d164.png" alt-text="Sekcja właściwości usługi Event Hubs w portalu Microsoft Azure" lightbox="../../media/759498162a4e93cbf17c4130d704d164.png":::


1. Po utworzeniu przestrzeni nazw centrum zdarzeń należy dodać jednostkę usługi rejestracji aplikacji jako czytelnik, Azure Event Hubs odbiornik danych oraz użytkownika, który będzie logować się do Microsoft 365 Defender jako współautor (można to zrobić również na poziomie grupy zasobów lub subskrypcji).

    Ten krok można wykonać w **obszarze Przestrzeń nazw** \> centrum zdarzeń **Access Control (IAM)** \> **Dodaj** i sprawdź w obszarze **Przypisania ról**:

    :::image type="content" source="../../media/9c9c29137b90d5858920202d87680d16.png" alt-text="Sekcja jednostka usługi rejestracji aplikacji w portalu Microsoft Azure" lightbox="../../media/9c9c29137b90d5858920202d87680d16.png":::

## <a name="set-up-event-hub"></a>Konfigurowanie centrum zdarzeń

**Opcja 1:**

Centrum zdarzeń można utworzyć w przestrzeni nazw, a **wszystkie** typy zdarzeń (tabele) wybrane do wyeksportowania zostaną zapisane w tym **centrum zdarzeń** .

**Opcja 2:**

Zamiast eksportować wszystkie typy zdarzeń (tabele) do jednego centrum zdarzeń, można wyeksportować każdą tabelę do innego centrum zdarzeń w przestrzeni nazw centrum zdarzeń (jedno centrum zdarzeń na typ zdarzenia).

W tej opcji Microsoft 365 Defender utworzy centrum zdarzeń dla Ciebie.

> [!NOTE]
> Jeśli używasz przestrzeni nazw centrum zdarzeń, która **nie** jest częścią klastra centrum zdarzeń, możesz wybrać maksymalnie 10 typów zdarzeń (tabel) do wyeksportowania w każdej Ustawienia eksportu zdefiniowanej przez Ciebie ze względu na ograniczenie platformy Azure do 10 centrów zdarzeń na przestrzeń nazw centrum zdarzeń.

Przykład:

:::image type="content" source="../../media/005c1f6c10c34420d387f594987f9ffe.png" alt-text="Sekcja centrum zdarzeń w portalu Microsoft Azure" lightbox="../../media/005c1f6c10c34420d387f594987f9ffe.png":::

Jeśli wybierzesz tę opcję, możesz przejść do sekcji [Konfigurowanie Microsoft 365 Defender wysyłania tabel wiadomości e-mail](#configure-microsoft-365-defender-to-send-email-tables).

Utwórz centrum zdarzeń w przestrzeni nazw, wybierając pozycję Centrum \> **zdarzeń** **i Centrum zdarzeń**.

Liczba partycji umożliwia zwiększenie przepływności za pośrednictwem równoległości, dlatego zaleca się zwiększenie tej liczby na podstawie oczekiwanego obciążenia. Zalecane są domyślne wartości przechowywania i przechwytywania komunikatów 1 i wyłączone.

:::image type="content" source="../../media/1db04b8ec02a6298d7cc70419ac6e6a9.png" alt-text="Sekcja tworzenia centrum zdarzeń w portalu Microsoft Azure" lightbox="../../media/1db04b8ec02a6298d7cc70419ac6e6a9.png":::
 

W przypadku tego centrum zdarzeń (a nie przestrzeni nazw) należy skonfigurować zasady dostępu współdzielonego przy użyciu opcji Wyślij oświadczenia nasłuchiwania. Kliknij  zasady \> **dostępu współdzielonego** centrum **zdarzeń** \> **+ Dodaj**, a następnie nadaj mu nazwę zasad (nie jest używana gdzie indziej) i zaznacz pozycję Wyślij i **nasłuchiwaj**.

:::image type="content" source="../../media/1867d13f46dc6a0f4cdae6cf00df24db.png" alt-text="Strona Zasady dostępu współdzielonego w portalu Microsoft Azure" lightbox="../../media/1867d13f46dc6a0f4cdae6cf00df24db.png":::

## <a name="configure-microsoft-365-defender-to-send-email-tables"></a>Konfigurowanie Microsoft 365 Defender do wysyłania tabel wiadomości e-mail

### <a name="set-up-microsoft-365-defender-send-email-tables-to-splunk-via-event-hub"></a>Konfigurowanie Microsoft 365 Defender wysyłania tabel poczty e-mail do aplikacji Splunk za pośrednictwem centrum zdarzeń

1. Zaloguj się do <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a> przy użyciu konta, które spełnia wszystkie następujące wymagania dotyczące roli:

    - Rola współautora na poziomie *zasobu przestrzeni nazw* centrum zdarzeń lub nowszej dla centrum zdarzeń, do którego będziesz eksportować. Bez tego uprawnienia podczas próby zapisania ustawień zostanie wyświetlony błąd eksportu.

    - Rola administratora globalnego lub administratora zabezpieczeń w dzierżawie powiązana z Microsoft 365 Defender i platformą Azure.

      :::image type="content" source="../../media/55d5b1c21dd58692fb12a6c1c35bd4fa.png" alt-text="Strona Ustawienia portalu Microsoft 365 Defender" lightbox="../../media/55d5b1c21dd58692fb12a6c1c35bd4fa.png":::

1. Kliknij pozycję **Eksportuj nieprzetworzone \> dane +Dodaj**.

    Teraz użyjesz danych, które zostały zarejestrowane powyżej.

    **Nazwa**: ta wartość jest lokalna i powinna być dowolną wartością działającą w twoim środowisku.

    **Prześlij zdarzenia do centrum zdarzeń**: zaznacz to pole wyboru.

    **Identyfikator zasobu centrum zdarzeń**: ta wartość to identyfikator zasobu przestrzeni nazw centrum zdarzeń, który został zapisany podczas konfigurowania centrum zdarzeń.

    **Nazwa centrum zdarzeń**: jeśli centrum zdarzeń zostało utworzone w przestrzeni nazw centrum zdarzeń, wklej nazwę centrum zdarzeń zarejestrowaną powyżej.

    Jeśli zdecydujesz się zezwolić Microsoft 365 Defender na utworzenie centrum zdarzeń dla każdego typu zdarzeń (tabel), pozostaw to pole puste.

    **Typy zdarzeń**: wybierz zaawansowane tabele wyszukiwania zagrożeń, które mają zostać przekazane do centrum zdarzeń, a następnie do aplikacji niestandardowej. Tabele alertów pochodzą z Microsoft 365 Defender, tabele urządzeń pochodzą z Ochrona punktu końcowego w usłudze Microsoft Defender (EDR), a tabele poczty e-mail pochodzą z Ochrona usługi Office 365 w usłudze Microsoft Defender. Zdarzenia poczty e-mail rejestrują wszystkie transakcje poczty e-mail. Adres URL (linki Sejf), załącznik (Sejf załączniki) i zdarzenia po dostarczeniu (ZAP) są również rejestrowane i mogą być przyłączone do zdarzeń poczty e-mail w polu NetworkMessageId.

    :::image type="content" source="../../media/3b2ad64b6ef0f88cf0175f8d57ef8b97.png" alt-text="Strona ustawień interfejsu API przesyłania strumieniowego w portalu Microsoft Azure" lightbox="../../media/3b2ad64b6ef0f88cf0175f8d57ef8b97.png":::

1. Pamiętaj, aby kliknąć pozycję **Prześlij**.

### <a name="verify-that-the-events-are-being-exported-to-the-event-hub"></a>Sprawdź, czy zdarzenia są eksportowane do centrum zdarzeń

Możesz sprawdzić, czy zdarzenia są wysyłane do centrum zdarzeń, uruchamiając podstawowe zapytanie zaawansowane wyszukiwania zagrożeń. Wybierz pozycję **Wyszukiwanie zagrożeń** \> — **zaawansowane zapytanie** **wyszukiwania zagrożeń** \> i wprowadź następujące zapytanie:

```console
EmailEvents
|joinkind=fullouterEmailAttachmentInfoonNetworkMessageId
|joinkind=fullouterEmailUrlInfoonNetworkMessageId
|joinkind=fullouterEmailPostDeliveryEventsonNetworkMessageId
|whereTimestamp\>ago(1h)
|count
```

Spowoduje to pokazanie, ile wiadomości e-mail odebrano w ciągu ostatniej godziny dołączonych do wszystkich innych tabel. Spowoduje to również wyświetlenie zdarzeń, które można wyeksportować do centrów zdarzeń. Jeśli ta liczba pokazuje wartość 0, nie zobaczysz żadnych danych wychodzących do centrum zdarzeń.

:::image type="content" source="../../media/c305e57dc6f72fa9eb035943f244738e.png" alt-text="Strona zaawansowanego wyszukiwania zagrożeń w portalu Microsoft Azure" lightbox="../../media/c305e57dc6f72fa9eb035943f244738e.png":::

Po sprawdzeniu, czy istnieją dane do wyeksportowania, możesz wyświetlić stronę centrum zdarzeń, aby sprawdzić, czy komunikaty są przychodzące. Może to potrwać do jednej godziny.

1. Na platformie Azure przejdź do pozycji Centrum \> **zdarzeń** Kliknij centrum **zdarzeń** \> **przestrzeni** \> nazw Kliknij centrum **zdarzeń**.
1. W obszarze **Przegląd** przewiń w dół i na grafie Komunikaty powinny zostać wyświetlone komunikaty przychodzące. Jeśli nie widzisz żadnych wyników, nie będzie żadnych komunikatów do pozyskiwania przez aplikację niestandardową.

:::image type="content" source="../../media/e88060e315d76e74269a3fc866df047f.png" alt-text="Strona Przegląd w Microsoft 365 Azure Portal" lightbox="../../media/e88060e315d76e74269a3fc866df047f.png":::
