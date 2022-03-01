---
title: Znajdź oprogramowanie wymuszające okup dzięki zaawansowanej chłonie
description: Użyj zaawansowanego wyszukiwania, aby znaleźć urządzenia, na które potencjalnie wpływa oprogramowanie wymuszające okup.
keywords: zaawansowane wyszukiwania, oprogramowanie wymuszające okup, skup na zagrożeniach, cyberzagrożenia, wyszukiwanie, zapytanie, telemetria, Microsoft 365, Microsoft 365 Defender
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: maccruz
author: schmurky
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
- m365solution-ransomware
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: 79dee9b6750e21d9b2482d4a0482d87d7fc7434b
ms.sourcegitcommit: 4af23696ff8b44872330202fe5dbfd2a69d9ddbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/30/2021
ms.locfileid: "62996816"
---
# <a name="hunt-for-ransomware"></a>Poszukiwania oprogramowania wymuszającego okup

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Dotyczy:**
- Microsoft 365 Defender

Oprogramowanie wymuszające okup szybko przekształciło się w złośliwe oprogramowanie w prosty towarzysze wpływające na poszczególnych użytkowników komputerów na poważne zagrożenia branżowe i instytucje rządowe. Chociaż [Microsoft 365 Defender](microsoft-365-defender.md) udostępnia wiele funkcji, które wykrywają i blokują oprogramowanie wymuszające okup oraz skojarzone z nimi działania łamania zabezpieczeń, proaktywne sprawdzanie znaków naruszenia bezpieczeństwa może pomóc chronić sieć.

> [Przeczytaj o oprogramowaniem wymuszającym okup obsługiwanym przez człowieka](https://www.microsoft.com/security/blog/2020/03/05/human-operated-ransomware-attacks-a-preventable-disaster/)

W [przypadku zaawansowanego](advanced-hunting-overview.md) wyszukiwania Microsoft 365 Defender możesz tworzyć zapytania, które lokalizują poszczególne artefakty skojarzone z działaniem oprogramowania wymuszającego okup. Możesz również uruchamiać bardziej zaawansowane zapytania, które mogą poszukać znaków aktywności i podać te znaki, aby znaleźć urządzenia wymagające natychmiastowej uwagi.

## <a name="signs-of-ransomware-activity"></a>Znaki aktywności oprogramowania wymuszającego okup
Twórcy zabezpieczeń firmy Microsoft obserwowali różne typowe, a jednocześnie delikatne artefakty w wielu kampanieach wymuszających okup, które są publikowane przez zaawansowane intruzów. Te znaki zwykle wymagają użycia narzędzi systemowych w celu przygotowania się do szyfrowania, zapobiegania wykrywaniu i wyczyszczenia dowodów forensic.

| Aktywność oprogramowania wymuszającego okup | Typowe narzędzia | Cel |
|--|--|--|
| Zatrzymywanie procesów | _taskkill.exe_, _zatrzymanie sieci_ | Upewnij się, że pliki kierowane do szyfrowania nie są blokowane przez różne aplikacje. |
| Wyłączanie usług | _sc.exe_ | - Upewnij się, że pliki kierowane do szyfrowania nie są blokowane przez różne aplikacje.<br>- Zapobieganie przerywaniu szyfrowania i innych działań oprogramowania wymuszającego okup przez oprogramowanie zabezpieczające.<br>- Zaprzestanie tworzenia kopii zapasowych oprogramowania do odzyskania.  |
| Usuwanie dzienników i plików | _cipher.exe_, _wevtutil_, _fsutil.exe_ | Usuwanie dowodów forensic. |
| Usuwanie kopii cienia  | _vsadmin.exe_, _wmic.exe_ | Usuń kopie w tle dysku, których można używać do odzyskiwania zaszyfrowanych plików. |
| Usuwanie i zatrzymywanie kopii zapasowych | _wbadmin.exe_ | Usuń istniejące kopie zapasowe i zatrzymaj zaplanowane zadania wykonywania kopii zapasowych, uniemożliwiając odzyskiwanie po szyfrowaniu. |
| Modyfikowanie ustawień rozruchu | _bcdedit.exe_ | Wyłącz ostrzeżenia i automatyczne naprawy po błędach rozruchu, które mogą być spowodowane przez proces szyfrowania. |
| Wyłączanie narzędzi do odzyskiwania | _schtasks.exe_, _regedit.exe_, | Wyłącz przywracanie systemu i inne opcje odzyskiwania systemu. |

## <a name="check-for-individual-signs-of-ransomware-activity"></a>Sprawdzanie indywidualnych znaków aktywności oprogramowania wymuszającego okup
Wiele działań, które stanowią zachowanie oprogramowania wymuszającego okup, łącznie z działaniami opisanymi w poprzedniej sekcji, może być chłonić. Podczas lokalizowania oprogramowania wymuszającego okup za pomocą poniższych zapytań uruchom więcej niż jedno zapytanie, aby sprawdzić, czy te same urządzenia wyeksncjonują różne znaki możliwej aktywności oprogramowania wymuszającego okup.

### <a name="stopping-multiple-processes-using-_taskkillexe_"></a>Zatrzymywanie wielu procesów przy _taskkill.exe_
To zapytanie sprawdza próby zatrzymania co najmniej 10 oddzielnych procesów przy użyciu _taskkill.exe_ narzędziowego. [Uruchamianie zapytania](https://security.microsoft.com/hunting?query=H4sIAAAAAAAEAI2RS2vCUBCFz7rgfwiuIkit3eumVSgtpYvuS9SLDTY2eLUvxN_eb8YHKlFkyNzJzDkn505aailRX7mmGlFlmhNBhUrOSGeuT3L0s6QqNaMagolEcMyCbApjx2e8TYhcH8Q1mB-emq50z_lF39gvBzo9-gEF-6Yhlyh9653ejCfRK6zCsaZfuJOu-x2jkqqN-0Yls-8-gp6dZ52OVuT6Sad1plulyN0KIkMt15_zt7zHDe8OBwv3btoJToa7Tnp0T8Ou9WzfT761gPOm3_FQ16Zxp2qcCdg33_rlyokG-iXv7_4BRNMnhkortmvTW6rqnZ7bgP2Vtm70D3d9wcFaAgAA&runQuery=true&timeRangeId=week)

```kusto
// Find attempts to stop processes using taskkill.exe
DeviceProcessEvents
| where Timestamp > ago(1d)
| where FileName =~ "taskkill.exe" 
| summarize taskKillCount = dcount(ProcessCommandLine), TaskKillList = make_set(ProcessCommandLine) by DeviceId, bin(Timestamp, 2m)
| where taskKillCount > 10
```
  
### <a name="stopping-processes-using-_net-stop_"></a>Zatrzymywanie procesów przy _użyciu zatrzymania sieci_
To zapytanie sprawdza próby zatrzymania co najmniej 10 oddzielnych procesów przy użyciu _polecenia net stop_ . [Uruchamianie zapytania](https://security.microsoft.com/hunting?query=H4sIAAAAAAAEAI2RQUvDUBCE5yz0P4ScUijWereXVkGQIti7aA1pqakhL7VVxN_ebzc1NBChPLJv2Z2ZN5sdaqhId1ppozeyF1WcVLkK7kCl0gcx-F2QFSrJFmACJ3XMlmgKGfmGWnXC6OlCU2qfIIz12OLfUk_h2FuG_IG505JayRdpDit3bIW33B2M3WeGSqIRrvudTJvpnWzmPKvc6JcYHx1eEvd8savV07e9TchzTt198AlNZ0kluNLfjHHjIPAvak4J_tvx9XtPR6ypbn1icxShvGgqyVkO-hrAm7VUrRcaTWOs6T_7hs7XjfSqL-Lpvu5BDLxjqKRjI9a9Juvew__T2x5HutIB3T1qt4QCAAA&runQuery=true&timeRangeId=week)

```kusto
// Find attempts to stop processes using net stop
DeviceProcessEvents
| where Timestamp > ago(1d)
| where FileName =~ "net.exe" and ProcessCommandLine has "stop"
| summarize netStopCount = dcount(ProcessCommandLine), NetStopList = make_set(ProcessCommandLine) by DeviceId, bin(Timestamp, 2m)
| where netStopCount > 10
```
### <a name="deletion-of-data-on-multiple-drives-using-_cipherexe_"></a>Usuwanie danych na wielu dyskach przy użyciu _cipher.exe_
To zapytanie sprawdza próby usunięcia danych na wielu dyskach przy użyciu _cipher.exe_. To działanie jest zwykle wykonywane przez oprogramowanie wymuszające okup, aby zapobiec odzyskiwaniu danych po szyfrowaniu. [Uruchamianie zapytania](https://security.microsoft.com/hunting?query=H4sIAAAAAAAEAI1SXUvDQBCcZ8H_cOQpgWLoD7AvVUEo4oPvElO1pblUcmn9QPztzk6TEuEsIdzdZndndm73cuRwWGDLb0PrhWfDs8Qab1jhmX8X3D-4HJbcK66W0Rqv8hT8K4RsiPW0PHbMasVQdbiGf3vaAec4wxWtPT0lz3vhSsUCrpVVE33I_Cb6vdNhTA9EeeVaVc8KDjOugmq2SDFlrSyKvCHS1NwJZ55L_HBPondNGDGWXP2JdyMnv927UnXHWwf6l4MunupXTOPfXszVT8_smriFOCxrRU-QclOQDLgCNRwQ1u8vZc8H2o1xp-7a7U1NefSko6pnmKjakNVi4chpiA39j-rGeF6HJ3xyH76NW2ZMFLGsNDJ9i05pZSPmVdDfq-jncfqtOuU5zSuQz6Zq92w7Hfbm-9cUm-d_vZ9J9S81O2KIfAMAAA&runQuery=true&timeRangeId=week)

```kusto
// Look for cipher.exe deleting data from multiple drives
DeviceProcessEvents
| where Timestamp > ago(1d)
| where FileName =~ "cipher.exe" 
// cipher.exe /w flag used for deleting data 
| where ProcessCommandLine has "/w" 
| summarize CipherCount = dcount(ProcessCommandLine),
CipherList = make_set(ProcessCommandLine) by DeviceId, bin(Timestamp, 1m) 
// cipher.exe accessing multiple drives in a short timeframe 
| where CipherCount > 1
```

### <a name="clearing-of-forensic-evidence-from-event-logs-using-_wevtutil_"></a>Czyszczenie dowodów forensic z dzienników zdarzeń przy _użyciu narzędzia wevtutil_
To zapytanie sprawdza próby wyczyszczenia co najmniej 10 wpisów dziennika z dzienników zdarzeń przy _użyciu narzędzia wevtutil_. [Uruchamianie zapytania](https://security.microsoft.com/hunting?query=H4sIAAAAAAAEAJWRTU_CQBCG37OJ_2HDqSQkwMGjXgoHEg4cUI-m2hUaqGu6BaPxx_vsEFCTxmA225nOvB_tzFBDOc0VOBuyZ2JD3CnKEwMVpzfyPbVWlba8t9Sdnsi9CsPXdLfWf7Wq4xm0QuVSF5oYv4LhtQAfLIucKXWvF5gH5Ke5rak1prKEVRu2xalG3emGW6AdlGmsUv1O5m-fnLzmFHiV_G9FTKg1lUjs6Z5vucPvljsD0TOXhP6_Vm7841dFZnPAN2A_DDu36eSnCSbNnc3B6Zpb4nasZGf59zWA963orZdcEiKelBNvQ_fBNny-utOj3nn-3OUMxMA6CZV1bCt1r8i6d_TXFNKWxxrpC48hm8miAgAA&runQuery=true&timeRangeId=week)

```kusto
// Look for use of wevtutil to clear multiple logs
DeviceProcessEvents
| where Timestamp > ago(1d)
| where ProcessCommandLine has "WEVTUTIL" and ProcessCommandLine has "CL"
| summarize LogClearCount = dcount(ProcessCommandLine), ClearedLogList = make_set(ProcessCommandLine) by DeviceId, bin(Timestamp, 5m)
| where LogClearCount > 10
```

### <a name="turning-off-services-using-_scexe_"></a>Wyłączanie usług przy użyciu _sc.exe_
To zapytanie sprawdza próby wyłączenia co najmniej 10 istniejących usług przy użyciu _sc.exe._ [Uruchamianie zapytania](https://security.microsoft.com/hunting?query=H4sIAAAAAAAEAKWST2vCQBDF31nodwg5RZCqhx7bi3ooeCjovaQxraIxxfU_fvj-ZoiiEIqlhM3Ozrz3ZnZm22or0lAl3xzrk33FHpTpUbn2rEgTzfCk-tACa6kvR-Qgt5wzrKAHNdTHOnveiJZVLGiAP4e5rpAnFHaauoZlGMMqHLsmT6FvfC-slFylEnWpoVnLvM3Twy74UnJNuJdVa6gpnsAe-81iVzbE3_kZiCV9mlHZf3Sue5pzii-3C9pU3BWYo_NGKPdvGJZh4x2N9Owzyi6e5K5qmmrVKg_9dNY11hzvu0_8fu0ItQP_6zfxCqLlEUMlNVO36BNW_ax_74K9l646-gFts39I1AIAAA&runQuery=true&timeRangeId=week)

```kusto
// Look for sc.exe disabling services
DeviceProcessEvents
| where Timestamp > ago(1d)
| where ProcessCommandLine has "sc" and ProcessCommandLine has "config" and ProcessCommandLine has "disabled"
| summarize ScDisableCount = dcount(ProcessCommandLine), ScDisableList = make_set(ProcessCommandLine) by DeviceId, bin(Timestamp, 5m)
| where ScDisableCount > 10
```

### <a name="turning-off-system-restore"></a>Wyłączanie przywracania systemu
To zapytanie identyfikuje próby zatrzymania przywracania systemu i uniemożliwić systemowi tworzenie punktów przywracania, które mogą być używane do odzyskiwania danych zaszyfrowanych przez oprogramowanie wymuszające okup. [Uruchamianie zapytania](https://security.microsoft.com/hunting?query=H4sIAAAAAAAEAK2S3UrDQBCFz7XgO6y9id4o6HWvrIVCkaJPENOYFNumZGO1ID673w4xJA1isbJMZnZ-zpzM7EiptlooQc9UqjDLc-7wp1qrwj7Via44MzK35FTotTI5PXMr0aVe8cy15NzoGo-zqg_0m3KQSsRpQtbC6uMGpdt3jHeJfU_GymqG-uQb9XpcEn1HIuvmGpZT0Aq99Dim4G3ousNO8K04sSE6EEN22kL6jvzO-LaDNW2QzqxLmGBsPo9vUMt_oA8Na3DQv3vwcmPiifpmds48jkhut8T2FLikxm_T4bI_m_6uQt-wrXO28lPPSBcdziOqPFlP9RYy47tDKtuZM07hVtSvaJ_HYRPL63-NyMgtmtWv5684jy2WDx2O0ZEM562ZBLQvURxur6gDAAA&runQuery=true&timeRangeId=week)

```kusto
DeviceProcessEvents
//Pivoting for rundll32  
| where InitiatingProcessFileName =~ 'rundll32.exe'   
//Looking for empty command line   
and InitiatingProcessCommandLine !contains " " and InitiatingProcessCommandLine != ""  
//Looking for schtasks.exe as the created process  
and FileName in~ ('schtasks.exe')  
//Disabling system restore   
and ProcessCommandLine has 'Change' and ProcessCommandLine has 'SystemRestore' 
and ProcessCommandLine has 'disable'
```

### <a name="backup-deletion"></a>Usuwanie kopii zapasowej
To zapytanie identyfikuje korzystanie _zwmic.exew_ celu usunięcia migawek kopii w tle przed rozpoczęciem szyfrowania. [Uruchamianie zapytania](https://security.microsoft.com/hunting?query=H4sIAAAAAAAEAJWS2wqCQBCG_-ugd5CupTfoqgMIEV70AqFLGp5QyYLo2fsavEjxwlhWZ7-df2Z2dndyuitVxD9UrdKshrGHOxVqsZda6CVPnRJYzfR0QJVhnXRRbmSjN98VXrlFXEMfzNWkfphti50zLmSMdURfmFcCaSxqY3aMX4eqVKUn1OsV_8eLWX_rbwcVVhblBovY8bT76U-AxoedWeeWp7WzV0YDMqSQFNZavuuopnHH_Iku-lbJnLPMyxnYDTp4bZ5P9M5uNpsZIWSn7l_CuNoPSggb4z4CAAA&runQuery=true&timeRangeId=week)

```kusto
DeviceProcessEvents
| where FileName =~ "wmic.exe"
| where ProcessCommandLine has "shadowcopy" and ProcessCommandLine has "delete"
| project DeviceId, Timestamp, InitiatingProcessFileName, FileName,
ProcessCommandLine, InitiatingProcessIntegrityLevel, InitiatingProcessParentFileName
```

## <a name="check-for-multiple-signs-of-ransomware-activity"></a>Sprawdzanie, czy nie ma wielu znaków aktywności oprogramowania wymuszającego okup
Zamiast uruchamiać kilka zapytań osobno, możesz również użyć kompleksowego zapytania, które sprawdza wiele znaków aktywności oprogramowania wymuszającego okup w celu zidentyfikowania urządzeń, których dotyczy problem. Następujące konsolidowane zapytanie:
- Wyszukuje zarówno stosunkowo konkretny, jak i subtelny znak aktywności oprogramowania wymuszającego okup
- Ważą obecność tych znaków
- Identyfikuje urządzenia z większą szansą na bycie celem oprogramowania wymuszającego okup 

Po uruchomieniu to konsolidowane zapytanie zwraca listę urządzeń, które wyeks obsługiwały wiele znaków ataków. Pokazano także liczbę poszczególnych typów aktywności oprogramowania wymuszającego okup. Aby uruchomić to skonsolidowane zapytanie, skopiuj je bezpośrednio do zaawansowanego edytora zapytań [wyszukiwania](https://security.microsoft.com/advanced-hunting). 

```kusto
// Find attempts to stop processes using taskkill.exe
let taskKill = DeviceProcessEvents
| where Timestamp > ago(1d)
| where FileName =~ "taskkill.exe" 
| summarize taskKillCount = dcount(ProcessCommandLine), TaskKillList = make_set(ProcessCommandLine) by DeviceId, bin(Timestamp, 2m)
| where taskKillCount > 10;
// Find attempts to stop processes using net stop
let netStop = DeviceProcessEvents
| where Timestamp > ago(1d)
| where FileName =~ "net.exe" and ProcessCommandLine has "stop"
| summarize netStopCount = dcount(ProcessCommandLine), NetStopList = make_set(ProcessCommandLine) by DeviceId, bin(Timestamp, 2m)
| where netStopCount > 10;
// Look for cipher.exe deleting data from multiple drives
let cipher = DeviceProcessEvents
| where Timestamp > ago(1d)
| where FileName =~ "cipher.exe" 
// cipher.exe /w flag used for deleting data 
| where ProcessCommandLine has "/w" 
| summarize CipherCount = dcount(ProcessCommandLine), 
CipherList = make_set(ProcessCommandLine) by DeviceId, bin(Timestamp, 1m) 
// cipher.exe accessing multiple drives in a short timeframe 
| where CipherCount > 1;
// Look for use of wevtutil to clear multiple logs
let wevtutilClear = DeviceProcessEvents
| where Timestamp > ago(1d)
| where ProcessCommandLine has "WEVTUTIL" and ProcessCommandLine has "CL"
| summarize LogClearCount = dcount(ProcessCommandLine), ClearedLogList = make_set(ProcessCommandLine) by DeviceId, bin(Timestamp, 5m)
| where LogClearCount > 10;
// Look for sc.exe disabling services
let scDisable = DeviceProcessEvents
| where Timestamp > ago(1d)
| where ProcessCommandLine has "sc" and ProcessCommandLine has "config" and ProcessCommandLine has "disabled"
| summarize ScDisableCount = dcount(ProcessCommandLine), ScDisableList = make_set(ProcessCommandLine) by DeviceId, bin(Timestamp, 5m)
| where ScDisableCount > 10;
// Main query for counting and aggregating evidence
DeviceProcessEvents
| where Timestamp > ago(1d)
| where FileName =~ "vssadmin.exe" and ProcessCommandLine has_any("list shadows", "delete shadows")
or FileName =~ "fsutil.exe" and ProcessCommandLine has "usn" and ProcessCommandLine has "deletejournal"
or ProcessCommandLine has("bcdedit") and ProcessCommandLine has_any("recoveryenabled no", "bootstatuspolicy ignoreallfailures")
or ProcessCommandLine has "wbadmin" and ProcessCommandLine has "delete" and ProcessCommandLine has_any("backup", "catalog", "systemstatebackup")
or (ProcessCommandLine has "wevtutil" and ProcessCommandLine has "cl") 
or (ProcessCommandLine has "wmic" and ProcessCommandLine has "shadowcopy delete")
or (ProcessCommandLine has "sc" and ProcessCommandLine has "config" and ProcessCommandLine has "disabled")
| extend Bcdedit = iff(ProcessCommandLine has "bcdedit" and ProcessCommandLine has_any("recoveryenabled no", "bootstatuspolicy ignoreallfailures"), 1, 0)
| extend ShadowCopyDelete = iff (ProcessCommandLine has "shadowcopy delete", 1, 0)
| extend VssAdminShadows = iff(ProcessCommandLine has "vssadmin" and ProcessCommandLine has_any("list shadows", "delete shadows"), 1, 0)
| extend Wbadmin = iff(ProcessCommandLine has "wbadmin" and ProcessCommandLine has "delete" and ProcessCommandLine has_any("backup", "catalog", "systemstatebackup"), 1,0)
| extend Fsutil = iff(ProcessCommandLine has "fsutil" and ProcessCommandLine has "usn" and ProcessCommandLine has "deletejournal", 1, 0)
| summarize FirstActivity = min(Timestamp), ReportId = any(ReportId), Commands = make_set(ProcessCommandLine) by DeviceId, Fsutil, Wbadmin, ShadowCopyDelete, Bcdedit, VssAdminShadows, bin(Timestamp, 6h)
// Joining extra evidence
| join kind=leftouter (wevtutilClear) on $left.DeviceId == $right.DeviceId
| join kind=leftouter (cipher) on $left.DeviceId == $right.DeviceId
| join kind=leftouter (netStop) on $left.DeviceId == $right.DeviceId
| join kind=leftouter (taskKill) on $left.DeviceId == $right.DeviceId
| join kind=leftouter (scDisable) on $left.DeviceId == $right.DeviceId
| extend WevtutilUse = iff(LogClearCount > 10, 1, 0)
| extend CipherUse = iff(CipherCount > 1, 1, 0)
| extend NetStopUse = iff(netStopCount > 10, 1, 0)
| extend TaskkillUse = iff(taskKillCount > 10, 1, 0)
| extend ScDisableUse = iff(ScDisableCount > 10, 1, 0)
// Adding up all evidence
| mv-expand CommandList = NetStopList, TaskKillList, ClearedLogList, CipherList, Commands, ScDisableList
// Format results
| summarize BcdEdit = iff(make_set(Bcdedit) contains "1" , 1, 0), NetStop10PlusCommands = iff(make_set(NetStopUse) contains "1", 1, 0), Wevtutil10PlusLogsCleared = iff(make_set(WevtutilUse) contains "1", 1, 0),
CipherMultipleDrives = iff(make_set(CipherUse) contains "1", 1, 0), Fsutil = iff(make_set(Fsutil) contains "1", 1, 0), ShadowCopyDelete = iff(make_set(ShadowCopyDelete) contains "1", 1, 0),
Wbadmin = iff(make_set(Wbadmin) contains "1", 1, 0), TaskKill10PlusCommand = iff(make_set(TaskkillUse) contains "1", 1, 0), VssAdminShadow = iff(make_set(VssAdminShadows) contains "1", 1, 0), 
ScDisable = iff(make_set(ScDisableUse) contains "1", 1, 0), TotalEvidenceCount = count(CommandList), EvidenceList = make_set(Commands), StartofBehavior = min(FirstActivity) by DeviceId, bin(Timestamp, 1d)
| extend UniqueEvidenceCount = BcdEdit + NetStop10PlusCommands + Wevtutil10PlusLogsCleared + CipherMultipleDrives + Wbadmin + Fsutil + TaskKill10PlusCommand + VssAdminShadow + ScDisable + ShadowCopyDelete
| where UniqueEvidenceCount > 2
```
### <a name="understand-and-tweak-the-query-results"></a>Opis i dostosowanie wyników zapytania
Konsolidowane zapytanie zwraca następujące wyniki:

- **DeviceId** — identyfikuje urządzenie, którego dotyczy problem 
- **TimeStamp** — po raz pierwszy obserwuje się na urządzeniu jakiekolwiek oznaki aktywności oprogramowania wymuszającego okup
- **Określone znaki aktywności —** liczba dla każdego znaku wyświetlanego w wielu kolumnach, na przykład _BcdEdit_ lub _FsUtil_
- **TotalEvidenceCount** — liczba obserwowanych znaków
- **UniqueEvidenceCount** — liczba typów obserwowanych znaków

:::image type="content" source="../../media/advanced-hunting-ransomware-query.png" alt-text="Przykład konsolidowane zapytanie dotyczące działania oprogramowania wymuszającego okup w portalu Microsoft 365 Defender sieci Microsoft 365 Defender sieci":::

*Wyniki kwerend pokazujące urządzenia, których dotyczy problem, i liczby różnych znaków aktywności oprogramowania wymuszającego okup*

Domyślnie w wynikach zapytania są zwracane tylko urządzenia, które mają więcej niż dwa typy aktywności oprogramowania wymuszającego okup. Aby wyświetlić wszystkie urządzenia z dowolnymi znakami aktywności oprogramowania wymuszającego okup, zmodyfikuj `where` poniższy operator i ustaw liczbę na zero (0). Aby wyświetlić mniej urządzeń, ustaw wyższą liczbę. 

```kusto
| where UniqueEvidenceCount > 2
```

## <a name="related-topics"></a>Tematy pokrewne
- [Omówienie zaawansowanego wyszukiwania](advanced-hunting-overview.md)
- [Poznaw język zapytań](advanced-hunting-query-language.md)
- [Praca z wynikami zapytania](advanced-hunting-query-results.md)
- [Używanie zapytań udostępnionych](advanced-hunting-shared-queries.md)
- [Opis schematu](advanced-hunting-schema-tables.md)
- [Stosowanie najlepszych rozwiązań kwerend](advanced-hunting-best-practices.md)

## <a name="additional-ransomware-resources"></a>Dodatkowe zasoby oprogramowania wymuszającego okup

Najważniejsze informacje od firmy Microsoft:

- [Coraz większe zagrożenie związane z oprogramowaniem wymuszającym okup](https://blogs.microsoft.com/on-the-issues/2021/07/20/the-growing-threat-of-ransomware/) (Microsoft) w wpisie w blogu Problemy z 20 lipca 2021 r.
- [Oprogramowanie wymuszające okup obsługiwane przez człowieka](/security/compass/human-operated-ransomware)
- [Błyskawiczna ochrona przed oprogramowaniem wymuszającym okup i wymuszającym okup](/security/compass/protect-against-ransomware)
- [2021: Microsoft Digital Defense Report](https://www.microsoft.com/security/business/microsoft-digital-defense-report) (zobacz strony 10-19)
- [Oprogramowanie wymuszające okup: natłok](https://security.microsoft.com/threatanalytics3/05658b6c-dc62-496d-ad3c-c6a795a33c27/overview) i bieżący raport analizy zagrożeń w portalu Microsoft 365 Defender okup

Microsoft 365:

- [Wdrażanie ochrony przed oprogramowaniem wymuszającym okup dla Microsoft 365 dzierżawy](/microsoft-365/solutions/ransomware-protection-microsoft-365)
- [Zmaksymalizuj odporność oprogramowania wymuszającego okup na platformie Azure Microsoft 365](https://azure.microsoft.com/resources/maximize-ransomware-resiliency-with-azure-and-microsoft-365/)
- [Odzyskiwanie po atakach oprogramowania wymuszającego okup](/microsoft-365/security/office-365-security/recover-from-ransomware)
- [Ochrona przed złośliwym oprogramowaniem i oprogramowaniem wymuszającym okup](/compliance/assurance/assurance-malware-and-ransomware-protection)
- [Ochrona komputera Windows przed oprogramowaniem wymuszającym okup](https://support.microsoft.com//windows/protect-your-pc-from-ransomware-08ed68a7-939f-726c-7e84-a72ba92c01c3)
- [Obsługa oprogramowania wymuszającego okup w SharePoint Online](/sharepoint/troubleshoot/security/handling-ransomware-in-sharepoint-online)
- [Raporty analizy zagrożeń dotyczące oprogramowania wymuszającego](https://security.microsoft.com/threatanalytics3?page_size=30&filters=tags%3DRansomware&ordering=-lastUpdatedOn&fields=displayName,alertsCount,impactedEntities,reportType,createdOn,lastUpdatedOn,tags,flag) okup w Microsoft 365 Defender sieci

Microsoft Azure:

- [Obrony platformy Azure w przypadku ataków na oprogramowanie wymuszające okup](https://azure.microsoft.com/resources/azure-defenses-for-ransomware-attack/)
- [Zmaksymalizuj odporność oprogramowania wymuszającego okup na platformie Azure Microsoft 365](https://azure.microsoft.com/resources/maximize-ransomware-resiliency-with-azure-and-microsoft-365/)
- [Plan tworzenia kopii zapasowej i przywracania w celu ochrony przed oprogramowaniem wymuszającym okup](/security/compass/backup-plan-to-protect-against-ransomware)
- [Pomóż chronić przed oprogramowaniem wymuszającym okup Microsoft Azure kopii zapasowej](https://www.youtube.com/watch?v=VhLOr2_1MCg) (26-minutowy klip wideo)
- [Odzyskiwanie po najechania na tożsamość tożsamości przez tożsamość](/azure/security/fundamentals/recover-from-identity-compromise)
- [Zaawansowane wykrywanie wieloetapowego ataku w programie Microsoft Sentinel](/azure/sentinel/fusion#ransomware)
- [Wykrywanie oprogramowania wymuszającego okup w programie Microsoft Sentinel](https://techcommunity.microsoft.com/t5/azure-sentinel/what-s-new-fusion-detection-for-ransomware/ba-p/2621373)

Program Microsoft Defender dla aplikacji w chmurze:

-  [Tworzenie zasad wykrywania anomaly w usłudze Defender dla aplikacji w chmurze](/cloud-app-security/anomaly-detection-policy)

Wpisy w blogu zespołu zabezpieczeń firmy Microsoft:

- [3 kroki, aby zapobiec oprogramowaniem wymuszającym okup i odzyskać je (wrzesień 2021 r.)](https://www.microsoft.com/security/blog/2021/09/07/3-steps-to-prevent-and-recover-from-ransomware/)
- [Przewodnik dotyczący zwalczania oprogramowania wymuszającego okup obsługiwany przez człowieka: część 1 (wrzesień 2021 r.)](https://www.microsoft.com/security/blog/2021/09/20/a-guide-to-combatting-human-operated-ransomware-part-1/)

  Kluczowe instrukcje dotyczące sposobu, w jaki zespół wykrywanie i odpowiedzi firmy Microsoft przeprowadza badania zdarzeń oprogramowania wymuszającego okup.

- [Przewodnik dotyczący zwalczania oprogramowania wymuszającego okup obsługiwany przez człowieka: część 2 (wrzesień 2021 r.)](https://www.microsoft.com/security/blog/2021/09/27/a-guide-to-combatting-human-operated-ransomware-part-2/)

  Rekomendacje i najlepsze rozwiązania.

- [Odporność dzięki zrozumieniu zagrożeń związanych z sezonowością: część 4. — poruszanie się po bieżących zagrożeniach (maj 2021 r.)](https://www.microsoft.com/security/blog/2021/05/26/becoming-resilient-by-understanding-cybersecurity-risks-part-4-navigating-current-threats/)

  Zobacz sekcję **Oprogramowanie wymuszające okup** .

- [Ataki oprogramowania wymuszającego okup przez ludzi: zapobiegalna awaria oprogramowania wymuszającego okup (marzec 2020 r.)](https://www.microsoft.com/security/blog/2020/03/05/human-operated-ransomware-attacks-a-preventable-disaster/)

  Zawiera analizy łańcucha ataków rzeczywistego.

- [Odpowiedź oprogramowania wymuszającego okup — na płatność lub nie? (Grudzień 2019 r.)](https://www.microsoft.com/security/blog/2019/12/16/ransomware-response-to-pay-or-not-to-pay/)
- [Norsk Nie odpowiada na ataki oprogramowania wymuszającego okup z przezroczystością (grudzień 2019 r.)](https://www.microsoft.com/security/blog/2019/12/17/norsk-hydro-ransomware-attack-transparency/)
