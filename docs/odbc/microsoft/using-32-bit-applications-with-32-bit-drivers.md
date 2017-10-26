---
title: "32 ビット ドライバーが 32 ビット アプリケーションを使用して |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ODBC drivers [ODBC], 32-bit applications
- 32-bit applications with 32-bit drivers [ODBC]
ms.assetid: 0cdd5788-5642-4280-8d53-b4ec461aafa1
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: e37da481e8068edb966b8f8ace4f129989cce990
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="using-32-bit-applications-with-32-bit-drivers"></a>32 ビット ドライバーが 32 ビット アプリケーションを使用します。
32 ビット ドライバーでは、32 ビット アプリケーションを実行できます。 32 ビット アプリケーションと 32 ビット ドライバーは、Win32® API を使用します。  
  
## <a name="architecture"></a>Architecture  
 次の図に、方法は、32 ビット アプリケーションと 32 ビット ドライバーの通信します。 アプリケーションでは、32 ビット ドライバーを呼び出し、32 ビット ドライバー マネージャーを呼び出します。  
  
 ![どの 32 &#45; 32 &#45; と通信ビット アプリ ビット ドライバー](../../odbc/microsoft/media/sdka6.gif "sdka6")  
  
> [!IMPORTANT]  
>  Windows Nt または windows 2000 では、32 ビット サンク インストーラー DLL を使わないでください。 32 ビット インストーラー DLL と同じファイル名がある、他の DLL です。  
  
## <a name="administration"></a>管理  
 32 ビット ドライバーのデータ ソースを管理するには、ODBC データ ソース アドミニストレーターを使用します。 Windows 2000 を実行するコンピューター上の ODBC アドミニストレーターを開くには、Windows コントロール パネルを開きをダブルクリックして**管理ツール**、順にダブルクリック**データ ソース (ODBC)**です。 Microsoft Windows の以前のバージョンを実行するコンピューターで、アイコンの名前は**32 ビット ODBC**または単に**ODBC**です。  
  
## <a name="components"></a>コンポーネント  
 ODBC コンポーネントには、32 ビット ドライバーが 32 ビット アプリケーションを実行するため、次のファイルが含まれています。 これらのコンポーネントが \Redist ディレクトリです。  
  
|ファイル名|Description|  
|---------------|-----------------|  
|Odbc32.dll|32 ビット ドライバー マネージャー|  
|Odbccp32.dll|32 ビット インストーラー DLL|  
|Odbcad32.exe|32 ビット odbc データ ソース アドミニストレーター|  
|Odbcinst.hlp|インストーラーのヘルプ ファイル|  
|Msvcrt40.dll|C ランタイム ライブラリ|

