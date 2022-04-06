---
title: Włączanie współtworzenia dokumentów zaszyfrowanych za pomocą etykiet poufności w Microsoft 365
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
audience: Admin
ms.service: O365-seccomp
ms.date: ''
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
ms.topic: article
description: Włącz ustawienie, które umożliwia współtworzenie i automatyczne zapisywanie w aplikacjach klasycznych dla dokumentów oznaczonych etykietami i zaszyfrowanych w SharePoint i OneDrive.
ms.openlocfilehash: baa2236915d37917e4ed69e5356db31262795d57
ms.sourcegitcommit: 2f6a0096038d09f0e43e1231b01c19e0b40fb358
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2022
ms.locfileid: "64687212"
---
# <a name="enable-co-authoring-for-files-encrypted-with-sensitivity-labels"></a>Włączanie współtworzyła pliki zaszyfrowane przy użyciu etykiet poufności

>*[Microsoft 365 wskazówki dotyczące licencjonowania dotyczące zgodności & zabezpieczeń](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

Włącz ustawienie, aby obsługiwać [współtworzynie](https://support.office.com/article/ee1509b4-1f6e-401e-b04a-782d26f564a4) aplikacji klasycznych Office, tak aby po oznaczeniu i zaszyfrowaniu dokumentów za pomocą [etykiet poufności](sensitivity-labels.md) wielu użytkowników może edytować te dokumenty w tym samym czasie.

Bez włączenia tego ustawienia dla dzierżawy użytkownicy muszą wyewidencjonować zaszyfrowany dokument przechowywany w SharePoint lub OneDrive podczas korzystania z Office aplikacji klasycznych. W związku z tym nie mogą współpracować w czasie rzeczywistym. Mogą też używać Office w sieci Web, gdy [etykiety poufności są włączone dla plików Office w SharePoint i OneDrive](sensitivity-labels-sharepoint-onedrive-files.md).

Ponadto włączenie tej funkcji powoduje obsługę funkcji [automatycznego zapisywania](https://support.office.com/article/what-is-autosave-6d6bd723-ebfd-4e40-b5f6-ae6e8088f7a5) dla tych plików oznaczonych etykietami i zaszyfrowanych.

Aby przeczytać ogłoszenie o wersji, zobacz wpis w blogu [Współtworzenie Microsoft Information Protection zaszyfrowane dokumenty są teraz ogólnie dostępne](https://techcommunity.microsoft.com/t5/security-compliance-and-identity/co-authoring-on-microsoft-information-protection-encrypted/ba-p/2693718).

## <a name="metadata-changes-for-sensitivity-labels"></a>Zmiany metadanych etykiet poufności

> [!IMPORTANT]
> Po włączeniu ustawienia współtworzenia informacje o etykietowaniu nieszyfrowanych plików nie są już zapisywane we właściwościach niestandardowych.
> 
> Nie włączaj tego ustawienia, jeśli używasz żadnych aplikacji, usług, skryptów lub narzędzi, które odczytują lub zapisują metadane etykietowania w starej lokalizacji.

Przed włączeniem ustawienia umożliwiającego współtworzenie Office aplikacji klasycznych należy zrozumieć, że ta akcja wprowadza zmiany w metadanych etykietowania, które są zapisywane i odczytywane z Office plików.

Metadane etykietowania zawierają informacje identyfikujące dzierżawę i zastosowany etykietę poufności. Zmiana wprowadzana przez to ustawienie to format metadanych i lokalizacja plików programu Word, Excel i PowerPoint. Nie musisz podejmować żadnych działań w przypadku zaszyfrowanych plików lub wiadomości e-mail, ponieważ zmiana metadanych dla zaszyfrowanych plików jest zgodna z poprzednimi wersjami i nie ma żadnych zmian w wiadomościach e-mail. Należy jednak pamiętać o zmianach metadanych dla zaszyfrowanych plików, które można automatycznie uaktualnić, ale nie są zgodne z poprzednimi wersjami.

Ta zmiana dotyczy zarówno plików, które są nowo oznaczone, jak i plików, które są już oznaczone etykietami. W przypadku korzystania z aplikacji i usług obsługujących ustawienie współtworzyło:
- W przypadku plików, które są nowo oznaczone etykietami, do etykietowania metadanych jest używany tylko nowy format i lokalizacja.
- W przypadku plików, które są już oznaczone etykietą, następnym razem, gdy plik zostanie otwarty i zapisany, jeśli plik ma metadane w starym formacie i lokalizacji, te informacje zostaną skopiowane do nowego formatu i lokalizacji.

Więcej informacji na temat tej zmiany metadanych można znaleźć w następujących zasobach:

- Wpis w blogu: [Nadchodzące zmiany w Storage metadanych Microsoft Information Protection](https://techcommunity.microsoft.com/t5/microsoft-security-and/upcoming-changes-to-microsoft-information-protection-metadata/ba-p/1904418)

- Open Specifications: [2.6.3 LabelInfo versus Custom Document Properties (Specyfikacje otwierania: 2.6.3 LabelInfo i właściwości dokumentu niestandardowego)](/openspecs/office_file_formats/ms-offcrypto/13939de6-c833-44ab-b213-e0088bf02341)

Z powodu tych zmian nie włączaj tego ustawienia, jeśli masz w organizacji jakiekolwiek aplikacje, usługi, skrypty lub narzędzia, które odczytują lub zapisują metadane etykietowania w starej lokalizacji. Jeśli to zrobisz, przykładowe konsekwencje:

- Dokument, który jest oznaczony etykietą, jest wyświetlany użytkownikom jako nieoznaczony.

- Dokument wyświetla użytkownikom nieaktualną etykietę.

- Współtworzenie i automatyczne zapisywanie nie będą działać w przypadku dokumentu oznaczonego etykietą i zaszyfrowanego, jeśli inny użytkownik otworzy go w aplikacji klasycznej Office, która nie obsługuje nowych metadanych etykietowania. Należy pamiętać, że ten scenariusz może również wystąpić w przypadku użytkowników spoza organizacji, jeśli użytkownicy zewnętrzni i zaproszeni goście mają otwarty plik.

- Reguła przepływu poczty Exchange Online, która [identyfikuje etykiety jako właściwości niestandardowe w załącznikach Office](/azure/information-protection/configure-exo-rules#example-2-rule-that-applies-the-encrypt-only-option-to-emails-when-they-have-attachments-that-are-labeled-confidential--partners-and-these-emails-are-sent-outside-the-organization) nie może zaszyfrować wiadomości e-mail i załącznika lub niepoprawnie je szyfruje.

Zapoznaj się z poniższą sekcją, aby uzyskać listę aplikacji i usług obsługujących to ustawienie oraz zmiany metadanych etykietowania.

## <a name="prerequisites"></a>Wymagania wstępne

Przed włączeniem tej funkcji upewnij się, że znasz następujące wymagania wstępne.

- Aby włączyć tę funkcję, musisz być administratorem globalnym.

- Etykiety poufności muszą być [włączone dla plików Office w SharePoint i OneDrive](sensitivity-labels-sharepoint-onedrive-files.md) dla dzierżawy. Jeśli ta funkcja nie jest jeszcze włączona, zostanie ona automatycznie włączona po wybraniu ustawienia, aby włączyć współtworowanie plików z etykietami poufności.

- Aplikacje Microsoft 365 dla przedsiębiorstw:
    - **Windows**: minimalna wersja 2107 z bieżącego kanału lub miesięcznego kanału Enterprise lub minimalna wersja 2202 z kanału Semi-Annual Enterprise
    - **macOS**: minimalna wersja 16.51
    - **iOS**: teraz w wersji zapoznawczej po [wybraniu](#opt-in-to-the-preview-of-co-authoring-for-ios-and-android) minimalnej wersji 2.58
    - **Android**: teraz w wersji zapoznawczej po [wybraniu](#opt-in-to-the-preview-of-co-authoring-for-ios-and-android) minimalnej wersji 16.0.14931

- Wszystkie aplikacje, usługi i narzędzia operacyjne w dzierżawie muszą obsługiwać nowe [metadane etykietowania](#metadata-changes-for-sensitivity-labels). Jeśli używasz dowolnej z następujących opcji, sprawdź wymagane minimalne wersje:
    
    - **Klient i skaner ujednoliconego etykietowania platformy Azure Information Protection:**
        - Minimalna wersja [2.12.62.0](/information-protection/rms-client/unifiedlabelingclient-version-release-history#version-212620) , którą można zainstalować z [Centrum pobierania Microsoft](https://www.microsoft.com/en-us/download/details.aspx?id=53018)
    
    - **aplikacja synchronizacja usługi OneDrive dla Windows lub macOS:**
        - Minimalna wersja 19.002.0121.0008
    
    - **Ochrona przed utratą danych punktu końcowego (Endpoint DLP):**
        - Windows 10 1809 z 4601383 KB
        - Windows 10 1903 i 1909 z kb 4601380
        - Windows 10 2004 r. z 4601382 KB
        - Windows wersje późniejsze niż Windows 10 2004 r. są obsługiwane bez aktualizacji KB
    
    - **Aplikacje i usługi korzystające z zestawu Microsoft Information Protection SDK:** 
        - Minimalna wersja wersji 1.7 

Microsoft 365 usługi automatycznie obsługują nowe metadane etykietowania po włączeniu tej funkcji. Przykład:

- [Zasady automatycznego etykietowania](apply-sensitivity-label-automatically.md#how-to-configure-auto-labeling-policies-for-sharepoint-onedrive-and-exchange)
- [Zasady DLP, które używają etykiet poufności jako warunków](dlp-sensitivity-label-as-condition.md)
- [Microsoft Defender for Cloud Apps skonfigurowane do stosowania etykiet poufności](/cloud-app-security/best-practices#discover-classify-label-and-protect-regulated-and-sensitive-data-stored-in-the-cloud)

### <a name="opt-in-to-the-preview-of-co-authoring-for-ios-and-android"></a>Zaloguj się do wersji zapoznawczej współautora dla systemów iOS i Android

Aby wypróbować wersję zapoznawczą współtworzynia dla systemów iOS i Android, musisz mieć minimalne wersje podane w poprzedniej sekcji, a także zażądać dodania dzierżawy do wersji zapoznawczej: [Zgoda na włączenie współtworzynia plików zaszyfrowanych za pomocą etykiet poufności na urządzeniach przenośnych](https://ncv.microsoft.com/5Oob3oDj1O)

Aby uzyskać więcej informacji, zobacz następujące ogłoszenie wpisu w blogu: [Współtworzenie Microsoft Information Protection zaszyfrowanych dokumentów jest teraz w publicznej wersji zapoznawczej na urządzeniach przenośnych](https://techcommunity.microsoft.com/t5/security-compliance-and-identity/co-authoring-on-microsoft-information-protection-encrypted/ba-p/3081369)

## <a name="limitations"></a>Ograniczenia

Przed włączeniem ustawienia dzierżawy dla współtworzyła pliki zaszyfrowane z etykietami poufności, upewnij się, że rozumiesz następujące ograniczenia tej funkcji.

- Ze względu na [zmiany metadanych etykietowania](#metadata-changes-for-sensitivity-labels) wszystkie aplikacje, usługi i narzędzia operacyjne w dzierżawie muszą obsługiwać nowe metadane etykietowania w celu zapewnienia spójnego i niezawodnego środowiska etykietowania.
    
    Specyficzne dla Excel: Metadane etykiety poufności, która nie stosuje szyfrowania, można usunąć z pliku, jeśli ktoś edytuje i zapisze ten plik przy użyciu wersji Excel, która nie obsługuje zmian metadanych etykiet poufności.

- Obsługa aplikacji Office dla systemów iOS i Android jest obecnie dostępna w [wersji zapoznawczej](https://office.com/insider).

- Współtworzenie i automatyczne zapisywanie nie są obsługiwane i nie działają w przypadku dokumentów oznaczonych etykietami i szyfrowanych Office, które używają dowolnej z [następujących konfiguracji szyfrowania](encryption-sensitivity-labels.md#configure-encryption-settings):
    - **Zezwalaj użytkownikom na przypisywanie uprawnień, gdy zastosują etykietę** i pole wyboru **W programie Word, PowerPoint i Excel, zostanie wybrany monit o określenie uprawnień**. Ta konfiguracja jest czasami określana jako "uprawnienia zdefiniowane przez użytkownika".
    - **Dostęp użytkownika do zawartości wygasa** jest ustawiony na wartość inną niż **Nigdy**.
    - **Wybrano opcję Podwójne szyfrowanie kluczy** .
    
    W przypadku etykiet z dowolną z tych konfiguracji szyfrowania etykiety są wyświetlane w aplikacjach Office. Jednak gdy użytkownicy wybierają te etykiety i nikt inny nie edytuje dokumentu, zostanie wyświetlony komunikat o tym, że współtworzenie i autozapisanie nie będą dostępne. Jeśli ktoś edytuje dokument, użytkownicy zobaczą komunikat, że etykiet nie można zastosować.

- Jeśli używasz klienta ujednoliconego etykietowania usługi Azure Information Protection: zapoznaj się z dokumentacją tego klienta etykietowania, aby uzyskać [więcej wymagań lub ograniczeń](/azure/information-protection/known-issues#known-issues-for-co-authoring). 
    > [!NOTE]
    > Te ograniczenia dotyczące ujednoliconego klienta etykietowania obejmują [zmianę okna dialogowego](/azure/information-protection/known-issues#user-interface-changes-when-applying-labels) dla użytkowników, którzy wybierają etykiety, które monitują ich o wybranie uprawnień.

## <a name="how-to-enable-co-authoring-for-files-with-sensitivity-labels"></a>Jak włączyć współtwoerowanie plików z etykietami poufności

> [!CAUTION]
> Włączenie tego ustawienia jest akcją jednokierunkową. Włącz ją dopiero po przeczytaniu i zrozumieniu zmian metadanych, wymagań wstępnych, ograniczeń i wszelkich znanych problemów udokumentowanych na tej stronie.

Jeśli to ustawienie zostało już włączone w okresie zapoznawczym, nie są potrzebne żadne dalsze działania i można pominąć tę procedurę.

1. Zaloguj się do [Centrum zgodności platformy Microsoft 365](https://compliance.microsoft.com) jako administrator globalny dzierżawy.

2. W okienku nawigacji wybierz pozycję **Ustawienia** >  **Tworzenie dla plików z plikami poufności**.

2. Na stronie **Współtworzenie plików z etykietami poufności** przeczytaj opis podsumowania, wymagania wstępne, oczekiwania i ostrzeżenie, że nie można wyłączyć tego ustawienia po jego włączeniu.
    
    Następnie wybierz pozycję **Włącz współtwoerowanie plików z etykietami poufności** i **Zastosuj**:
    
    ![Opcja włączenia współtworzyła pliki z etykietami poufności.](../media/co-authoring-tenant-option-for-sensitivity-labels.png)

3. Poczekaj 24 godziny na replikację tego ustawienia w całym środowisku, zanim użyjesz tej nowej funkcji do współtworzyła.

## <a name="contact-support-if-you-need-to-disable-this-feature"></a>Skontaktuj się z pomocą techniczną, jeśli chcesz wyłączyć tę funkcję

> [!IMPORTANT]
> Jeśli musisz wyłączyć tę funkcję, pamiętaj, że informacje o etykietowaniu mogą zostać utracone.

Po włączeniu współtwonia plików z etykietami poufności dla dzierżawy nie można samodzielnie wyłączyć tego ustawienia. Dlatego tak ważne jest sprawdzenie i zrozumienie wymagań wstępnych, konsekwencji i ograniczeń przed włączeniem tego ustawienia.

![Opcja, która pokazuje włączone współtwoerowanie etykiet poufności.](../media/co-authoring-tenant-option-set-for-sensitivity-labels.png)

Jak widać na zrzucie ekranu po włączeniu tego ustawienia, możesz skontaktować się z [pomoc techniczna firmy Microsoft](../admin/get-help-support.md) i poprosić o wyłączenie tego ustawienia. To żądanie może potrwać kilka dni i musisz udowodnić, że jesteś administratorem globalnym dzierżawy. Spodziewaj się, że będą obowiązywać zwykłe opłaty za pomoc techniczną. 

Jeśli inżynier pomocy technicznej wyłączy to ustawienie dla dzierżawy:

- W przypadku aplikacji i usług obsługujących nowe metadane etykietowania powrót do oryginalnego formatu i lokalizacji metadanych po odczytaniu lub zapisaniu etykiet.

- Nowy format metadanych i lokalizacja dla dokumentów Office, które były używane podczas włączania ustawienia, nie zostaną skopiowane do oryginalnego formatu i lokalizacji. W rezultacie te informacje dotyczące etykietowania niezaszyfrowanych plików programu Word, Excel i PowerPoint zostaną utracone.

- Współtwoerowanie i automatyczne zapisywanie nie działają już w dzierżawie w przypadku dokumentów oznaczonych etykietami i zaszyfrowanych.

- Etykiety poufności pozostają włączone dla plików Office w OneDrive i SharePoint.
