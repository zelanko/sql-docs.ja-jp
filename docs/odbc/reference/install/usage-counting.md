---
title: 使用状況カウント |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- usage counts [ODBC]
- file usage counts [ODBC]
- installing ODBC components [ODBC], usage counts
- subkeys [ODBC], usage counts
ms.assetid: 0678aee9-8256-463c-89dd-77b1a0dfdd60
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 8d516a591bfde47522c0ccfe08bd2bd706218e07
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81296022"
---
# <a name="usage-counting"></a>使用状況のカウント
> [!NOTE]  
>  WINDOWS XP および Windows Server 2003 以降では、ODBC が Windows のオペレーション システムに含まれています。 ODBC は、以前のバージョンの Windows にのみ明示的にインストールしてください。  
  
 各コンポーネントのレジストリでは、コンポーネントの使用カウントと 1 つ以上のオプションのファイル使用量カウントの 2 種類の使用カウントが保持されます。 コンポーネントの使用カウントは、インストーラー DLL がレジストリ エントリを維持するのに役立ちます。 これは、ODBC コア、ドライバー、および変換プログラムのサブキーの下の UsageCount 値に格納されます。 UsageCount 値の形式とこれらのサブキーの詳細については[、「ODBC コンポーネントのレジストリ エントリ](../../../odbc/reference/install/registry-entries-for-odbc-components.md)」を参照してください。  
  
 コンポーネントが最初にインストールされると、インストーラー DLL はそのサブキーを作成し、そのサブキーの UsageCount 値のデータを 1 に設定します。 コンポーネントが再びインストールされると、インストーラー DLL は使用カウントをインクリメントします。 コンポーネントが削除されると、インストーラー DLL は使用カウントを減らします。 使用カウントが 0 に減少した場合、インストーラー DLL はコンポーネントのサブキーを削除します。  
  
> [!CAUTION]  
>  コンポーネントの使用数とファイルの使用数がゼロに達すると、アプリケーションは、ドライバー マネージャーのファイルを物理的に削除しないでください。  
  
 ファイル使用量カウントは、使用カウントを増減するのではなく、ファイルを実際にコピーまたは削除する必要がある時期を決定するのに役立ちます。 ODBC コンポーネント、つまり ODBC コンポーネントのファイルは共有され、さまざまなアプリケーションでインストールまたは削除できるため、この方法は重要です。 コンポーネントの使用カウントとファイル使用量カウントがゼロに達した場合、アプリケーションはドライバーとトランスレータファイルを削除できます。 ただし、コンポーネントの使用カウントとファイル使用量カウントの両方がゼロに達した場合、Driver Manager ファイルは削除しないでください。  
  
> [!NOTE]  
>  ファイルの使用率カウントは、WindowsNT®®/Windows2000 ではオプションです。  
  
 ファイル使用量カウントは **、SQL インストールドライバー マネージャー** **、SQL インストールドライバー ドライバードライバー、SQL****インストールトランスレータ、SQLRemoveDriver**マネージャー **、SQLRemoveDriver**、または**SQLRemove****トランスレータ**を呼び出した後、セットアップ プログラムによって管理されます。  
  
 コンポーネントを最初にインストールすると、セットアップ プログラムまたはインストーラ DLL によって、システム上に存在しないコンポーネントの各ファイルに対して、次のキーの下に値が作成されます。  
  
> [!NOTE]  
>  HKEY_LOCAL_MACHINE  
>   
>  ソフトウェア  
>   
>  Microsoft  
>   
>  Windows  
>   
>  CurrentVersion  
>   
>  共有Dlls  
  
 これらの値のデータを 1 に設定し、ファイルをシステムにコピーします。 コンポーネントを再インストールすると、セットアップ プログラムまたはインストーラー DLL によって使用量カウントが増加します。 コンポーネントが削除されると、セットアップ プログラムまたはインストーラー DLL によって使用量カウントが減ります。 使用カウントが 0 に下がると、セットアップ プログラムまたはインストーラー DLL はファイルの値を削除し、コンポーネントがドライバまたはトランスレータの場合はファイルを削除します。 ドライバー マネージャーのファイルを削除しないでください。  
  
 ファイルの使用カウント値の形式を次の表に示します。  
  
|名前|データ型|Data|  
|----------|---------------|----------|  
|*フルパス*|REG_DWORD|*count*|  
  
 たとえば、Informix 用のドライバーが Infrmx32.dll ファイルと Infrmx32.hlp ファイルを使用し、このドライバーが 2 回インストールされているとします。 Informix ドライバーの SharedDlls サブキーの下の値は次のようになります。  
  
```  
C:\WINDOWS\SYSTEM32\INFRMX32.DLL : REG_DWORD : 0x2  
C:\WINDOWS\SYSTEM32\INFRMX32.HLP : REG_DWORD : 0x2  
```
