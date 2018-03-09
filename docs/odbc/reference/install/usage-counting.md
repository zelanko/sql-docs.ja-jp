---
title: "使用状況カウント |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- usage counts [ODBC]
- file usage counts [ODBC]
- installing ODBC components [ODBC], usage counts
- subkeys [ODBC], usage counts
ms.assetid: 0678aee9-8256-463c-89dd-77b1a0dfdd60
caps.latest.revision: "8"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: deb6923a2e842241eea1434997194f6e6d19ce1a
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="usage-counting"></a>使用状況のカウント
> [!NOTE]  
>  Windows XP および Windows Server 2003 以降、Windows オペレーティング システムに ODBC が含まれます。 以前のバージョンの Windows で ODBC を明示的にのみインストールしてください。  
  
 2 つの種類の使用率カウントは各コンポーネントのレジストリで保持されます。 コンポーネントの使用率カウントと省略可能なファイル使用状況カウントが 1 つまたは複数です。 コンポーネントの使用率カウントは、インストーラー DLL は、レジストリ エントリを保持します。 ODBC Core、ドライバー、およびトランスレーター サブキーの下で UsageCount 値で格納されます。 詳細については、これらのサブキーと UsageCount 値の形式の場合、次を参照してください。 [ODBC コンポーネントのレジストリ エントリ](../../../odbc/reference/install/registry-entries-for-odbc-components.md)です。  
  
 コンポーネントが最初にインストールされたときにインストーラー DLL のサブキーを作成および UsageCount 値のデータをそのサブキーを 1 に設定します。 コンポーネントがインストールすると、もう一度インストーラー DLL は、使用率カウントをインクリメントします。 コンポーネントが削除されたときに、インストーラー DLL の使用状況カウントをデクリメントします。 使用率カウントを 0 になる場合、インストーラーの DLL は、コンポーネントのサブキーを削除します。  
  
> [!CAUTION]  
>  アプリケーションに物理的に削除しないでドライバー マネージャーのファイル コンポーネントの使用率カウントとファイルの使用率カウントは 0 に達した場合。  
  
 ファイルの使用状況のカウントを決めるファイル必要があります実際にあるコピーまたは削除されたときとは対照的にインクリメントまたはデクリメント使用率カウントします。 これは、機能は、ODBC コンポーネントとそのため、ODBC コンポーネント内のファイル共有しできますをインストールまたは削除のさまざまなアプリケーションであるため重要です。 アプリケーションは、コンポーネントの使用率カウントとファイルの使用率カウントが 0 になる場合、ドライバーおよび変換プログラムのファイルを削除できます。 ドライバー マネージャーのファイルは、しないで、ただし、これらのファイルは、ファイルの使用率カウントはインクリメントされませんが他のアプリケーションで使用できるために達するコンポーネントの使用率カウントとファイルの使用率カウントの両方が 0、削除します。  
  
> [!NOTE]  
>  ファイル使用状況のカウントは、オプションで Microsoft® WindowsNT®/windows 2000 です。  
  
 ファイル使用状況カウントは、呼び出された後に、セットアップ プログラムによって維持**SQLInstallDriverManager**、 **SQLInstallDriverEx**、 **SQLInstallTranslatorEx**、 **SQLRemoveDriverManager**、 **SQLRemoveDriver**、または**SQLRemoveTranslator**です。  
  
 コンポーネントが最初にインストールされたときに、セットアップ プログラムまたはインストーラー DLL を作成の各ファイルの次のキーの下で値が既にシステムにそのコンポーネントに。  
  
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
>  SharedDlls  
  
 これらの値のデータを 1 に設定し、ファイル システムにコピーします。 コンポーネントがインストールすると、もう一度セットアップ プログラムまたは DLL のインストーラーは、使用状況カウントをインクリメントします。 コンポーネントが削除されると、セットアップ プログラムまたはインストーラー DLL デクリメント、使用率をカウントします。 任意の使用率カウントを 0 になる場合、セットアップ プログラムまたは DLL のインストーラー ファイルの値を削除し、コンポーネントがドライバーや、トランスレーターの場合は、ファイルを削除します。 ドライバー マネージャーのファイルは削除されません必要があります。  
  
 ファイルの使用状況カウントの値の形式は次の表に示します。  
  
|[オブジェクト名]|データ型|data|  
|----------|---------------|----------|  
|*完全パス*|REG_DWORD|*count*|  
  
 たとえば、Informix 用のドライバーが、Infrmx32.dll および Infrmx32.hlp ファイルを使用するいるとし、このドライバーが 2 回インストールされているとします。 Informix ドライバーの SharedDlls サブキーの下の値に次のようになります。  
  
```  
C:\WINDOWS\SYSTEM32\INFRMX32.DLL : REG_DWORD : 0x2  
C:\WINDOWS\SYSTEM32\INFRMX32.HLP : REG_DWORD : 0x2  
```
