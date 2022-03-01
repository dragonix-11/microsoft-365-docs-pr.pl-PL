---
title: Obrazy urządzeń
description: Wymagania dotyczące obrazów podczas zamawiania nowych urządzeń lub ponownego korzystania z istniejących urządzeń
keywords: Microsoft Managed Desktop, Microsoft 365, usługa, dokumentacja
ms.service: m365-md
author: tiaraquan
f1.keywords:
- NOCSH
ms.author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
manager: dougeby
ms.topic: article
audience: Admin
ms.openlocfilehash: 535dfc84ced9c4a2935d8e2c44c1e4c6135e9373
ms.sourcegitcommit: a6651b841f111ea2776cab88bf2c80f805fa8e09
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/13/2022
ms.locfileid: "63033827"
---
# <a name="device-images"></a>Obrazy urządzeń


Niezależnie od tego, czy zamówisz [](#existing-devices) nowe [urządzenia](#new-devices), czy ponownie użyj istniejących, masz kilka opcji, aby zapewnić, że obraz na urządzeniu spełnia [nasze wymagania dotyczące urządzenia](device-requirements.md#check-hardware-requirements).

## <a name="new-devices"></a>Nowe urządzenia
W przypadku zamówienia nowego urządzenia [od zatwierdzonego](device-requirements.md#minimum-requirements) producenta wykonaj poniższe czynności, aby upewnić się, że urządzenia są w nich zainstalowane Microsoft Managed Desktop obrazem i konfiguracją oprogramowania. Za każdym razem, gdy zamierzasz zarejestrować określony model urządzenia w usłudze po raz pierwszy, warto przetestować przykład, aby upewnić się, że zapewni to oczekiwaną obsługę użytkownika. Aby uzyskać więcej informacji, zobacz [Weryfikowanie nowych urządzeń](/microsoft-365/managed-desktop/get-started/validate-device).

### <a name="dell"></a>Dell
Należy bezpośrednio do przedstawiciela handlowego firmy Dell upewnić się, że obraz zatwierdzony przez firmę Microsoft Managed Desktop został zastosowany do urządzeń, na których jest zamówienia. Aby uzyskać więcej pytań na temat urządzeń firmy Dell, obrazu i procesu zamawiania, skontaktuj się z MMD_at_dell@dell.com.

### <a name="hp"></a>HP 
Podczas zamówienia nowych urządzeń w firmie HP upewnij się, że używasz określonej sku wymienionej w sekcji Dodatkowe wymagania dla każdego modelu w witrynie Kup [Windows Pro](https://www.microsoft.com/windows/business/devices#view-all-filter) urządzeń biznesowych (przefiltruj widok, aby wyświetlić Microsoft Managed Desktop urządzenia).

Jeśli zamawiasz urządzenie od firmy HP, które zostało zatwierdzone jako wyjątek, ale [](customizing.md) nie jest obecnie wymienione na stronie Lista urządzeń, upewnij się, że zażądaj, aby ta sKU była używana dla Twojego modelu. We współpracy z hp, aby uzyskać te informacje przy użyciu Twojego żądania wyjątku. Jeśli masz pytania dotyczące urządzeń i instrukcji dotyczących zamawiania urządzeń, możesz również skontaktować się bezpośrednio z hp, używając tych adresów:
 
- Ameryka Północna: mmd-americas@hp.com
- Europa/Bliski Wschód/Afryka: mmd-emea@hp.com
- Azja pacyfik/Japonia: mmd-apj@hp.com
- Globalne: mmd@hp.com

### <a name="lenovo"></a>Lenovo
W przypadku zamawiania urządzeń firmy Lenovo do użycia w Microsoft Managed Desktop należy wskazać określony numer części uwzględniony w zamówieniu. Skontaktuj się z przedstawicielem handlowym Lenovo lub partnerem handlowym Lenovo Channel i poproś go o *utworzenie "specjalnego* modelu oferty" z systemem spełniającym [nasze wymagania dotyczące urządzeń](device-requirements.md#minimum-requirements). Aby dołączyć wstępnie załadowany obraz zgodny z programem Microsoft Managed Desktop, poproś przedstawiciela handlowego o odwołanie się do informacji "System *building block part number SBB0Q94938 — Włączenie MMD*". We współpracy z przedstawicielem handlowym Lenovo lub partnerem handlowym Lenovo Channel można uzyskać zalecane usługi, pomoc techniczną i usługi przetwarzania obrazu.

### <a name="microsoft"></a>Microsoft
Wszystkie urządzenia firmy Microsoft spełniające wymagania dotyczące urządzeń są wyposażone w obraz, który współpracuje Microsoft Managed Desktop. Nie są wymagane żadne inne kroki.

Aby uzyskać najnowszy obraz dostępny w fabrycznej na urządzeniu firmy Microsoft, należy współpracować z specjalistą ds. urządzeń Surface w celu użycia procesu "Po natłoku" urządzenia Surface.

## <a name="existing-devices"></a>Istniejące urządzenia

Możesz ponownie używać istniejących urządzeń, jeśli spełniają one zarówno wymagania dotyczące urządzeń  [,](device-requirements.md#minimum-requirements) jak i [wymagania dotyczące oprogramowania](device-requirements.md#installed-software). Postępuj zgodnie z instrukcjami odpowiednimi dla producenta.

Można ponownie zaimportować urządzenia za pomocą obrazu producenta lub za pomocą Microsoft Managed Desktop obrazu uniwersalnego. Aby uzyskać odpowiedni obraz producenta, możesz zamówić co najmniej jedno [nowe](#new-devices) urządzenie w modelu, który jest wyzysowywany ponownie. Następnie możesz uzyskać obraz z tego urządzenia i zastosować go do innych urządzeń o dokładnie tym samym modelu.

> [!NOTE]
> To Ty ponosisz odpowiedzialność za tworzenie, testowanie i wdrażanie obrazów. Zalecamy również używanie odpowiednich obrazów dostarczonych przez producenta, jeśli to możliwe, zamiast obrazów niestandardowych — w tym "obraz uniwersalny".

### <a name="hp"></a>HP

Komputery komercyjne HP dostarczane z firmowym obrazem HP Ready zawierają kod . Plik WIM do odzyskiwania. Za pomocą tego obrazu możesz zastosować obraz przywracania fabrycznego do innych urządzeń tego samego modelu.

Ta procedura spowoduje usunięcie wszystkich danych z urządzenia, dlatego przed rozpoczęciem należy wykonać kopię zapasową wszystkich danych, które chcesz zachować.

1. [Utwórz dysk USB z rozruchem za](/windows-hardware/manufacture/desktop/winpe-create-usb-bootable-drive) pomocą winPE.
2. Skopiuj następujące pliki z pliku C:\\SOURCES na dysk USB:
    - Plik WIM przywracania ustawień fabrycznych (na przykład HPEliteBook840G7NotebookPCCR2004.wim\_\_\_\_\_\_\_)
    - WDEKSUJ. CMD
    - ReCreatePartitions.txt
3. [Rozruch urządzenia do systemu WinPE](https://store.hp.com/us/en/tech-takes/how-to-boot-from-usb-drive-on-windows-10-pcs) dysk USB.
4. W wierszu polecenia uruchom polecenie [Diskpart.exe](/windows-server/administration/windows-commands/diskpart#additional-references).
5. W części Dysk uruchom program `list disk`, a następnie zwróć uwagę na podstawowy numer dysku magazynu (zazwyczaj Dysk 0).
6. Zamknij część dysku, wpisując .`exit`
7. W wierszu polecenia uruchom polecenie `deploy.cmd <sys_disk> <recovery_wim>`, gdzie *sys_disk* to numer dysku podstawowego miejsca do magazynowania, który właśnie został określony, a *recovery_wim to nazwa* pliku . Plik WIM skopiowany wcześniej.
8. Usuń dysk USB, a następnie uruchom ponownie urządzenie.

### <a name="microsoft"></a>Microsoft 

Urządzenia Surface firmy Microsoft zawierają obrazy "odzyskiwanie elementów [metalowych"](https://support.microsoft.com/en-us/surfacerecoveryimage) , które są specyficzne dla każdego modelu. Za pomocą tych obrazów można ponownie zaimportować urządzenia.

Te obrazy używają środowiska Windows odzyskiwania (WinRE) i jest to proces ręczny (nie zautomatyzowany). Wykonaj czynności opisane w [tece Tworzenie i używanie dysku odzyskiwania USB dla urządzenia Surface](https://support.microsoft.com/surface/creating-and-using-a-usb-recovery-drive-for-surface-677852e2-ed34-45cb-40ef-398fc7d62c07).


### <a name="universal-image"></a>Obraz uniwersalny
Microsoft Managed Desktop utworzono obraz zawierający wiele Windows Pro i Aplikacje Microsoft 365 dla Enterprise, których można użyć w Microsoft Managed Desktop. Najlepiej jednak używać obrazów odpowiednich dla pliku Microsoft Managed Desktop dostarczonego przez producenta, jeśli to możliwe, nawet jeśli oznacza to starszą wersję Windows, która następnie musi zostać zaktualizowana po tym, jak użytkownik się wyedytuje. Używanie obrazu Microsoft Managed Desktop uniwersalnego powinno być ostateczną opcją.

- Obraz jest aktualizowany za pomocą najnowszych Windows aktualizacji jakości co miesiąc co 30–60 dni, a Aplikacje Microsoft 365 dla Enterprise aktualizacji co najmniej dwa razy do roku.
- Obraz zawiera pakiet inicjowania obsługi odzyskiwania, aby zapewnić Aplikacje Microsoft 365 odzyskiwania Enterprise następujących po następujących Windows odzyskiwania.
- Obraz można wdrożyć za pomocą dysków USB. Zawiera on proces wstawiania sterowników (opisany w dokumentacji dołączonej do obrazu).
- Dołączone skrypty i foldery można modyfikować w celu używania ich razem z innymi dostosowaniami, takimi jak dodawanie konkretnych aktualizacji skumulowanych, kod kopii pliku lub wykonywanie innych testów.
- Sterowniki i aktualizacje jakości są dodawane Windows podczas wdrażania z dysku USB.

> [!NOTE]
> Odpowiedzialność za dodanie wszystkich potrzebnych sterowników, przeprowadzenie wszystkich testów i upewnienie się, że nie występują problemy z ostatecznym wdrożeniem obrazu, spoczywa na Twoim obowiązkówu. Zapewniamy uniwersalny obraz "w stanie, w który jest", ale dostarczamy wskazówek technicznych i odpowiadamy na pytania. Kontakt MMDImage@microsoft.com.

Przesyłaj żądania dotyczące zawartości i dokumentacji uniwersalnego obrazu, tworząc żądanie zmiany w [portalu administracyjnym](../get-started/access-admin-portal.md).


