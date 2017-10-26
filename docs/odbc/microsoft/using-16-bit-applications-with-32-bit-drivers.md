---
title: "16 ビット アプリケーションを使用して、32 ビット ドライバーが |Microsoft ドキュメント"
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
- ODBC drivers [ODBC], 16-bit applications
- 16-bit applications with 32-bit drivers [ODBC]
ms.assetid: 68feb3b7-c01a-4f42-8df9-f9c182d89325
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: d35585ec95bdfed62c527dfe004132c7454e5243
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="using-16-bit-applications-with-32-bit-drivers"></a>32 ビット ドライバーで 16 ビット アプリケーションを使用
> [!IMPORTANT]  
>  この機能は、Windows の将来のバージョンで削除されます。 新しい開発作業でこの機能を使用しないように、現在この機能を使用しているアプリケーションの変更を検討してください。 代わりに 32 ビットまたは 64 ビット ドライバー マネージャーを使用します。  
  
 32 ビット ドライバーがスレッドを作成する Win32 API 関数を明示的に呼び出していない限り、Windows ベースのシステムで 32 ビット ドライバーの 16 ビット アプリケーションを実行できます。 Windows on Windows (WOW) サブシステムは、16 ビット モードでアプリケーションを実行し、オペレーティング システムの 16 ビット呼び出しを解決します。 32 ビット ドライバーをアプリケーションから Dll 解決 16 ビットの呼び出しをサンキング ODBC です。 16 ビット アプリケーションが Windows API を使用して、32 ビット ドライバーは、Win32 API を使用します。  
  
## <a name="architecture"></a>Architecture  
 次の図に、どのように 16 ビット アプリケーションと 32 ビット ドライバーの通信します。 ドライバー マネージャーの 16 ビットと 32 ビット ドライバーの間では、32 ビット ODBC 呼び出しに 16 ビット ODBC 呼び出しに変換する Dll をサンク汎用的なのです。  
  
 ![どの 16 &#45; 32 &#45; と通信ビット アプリ ビット ドライバー](../../odbc/microsoft/media/sdka2.gif "sdka2")  
  
> [!NOTE]  
>  16 ビット アプリケーションは、32 ビット ドライバーを使用して相互運用、いつでも、32 ビット ドライバー マネージャーは「2.0」ODBC のバージョンとして、ドライバーでサポートを常に返します。  
  
## <a name="administration"></a>管理  
 32 ビット ドライバーのデータ ソースを管理するには、ODBC データ ソース アドミニストレーターを使用します。 Microsoft® Windows® 2000 を実行するコンピューター上の ODBC アドミニストレーターを開くには、Windows コントロール パネルを開きをダブルクリックして**管理ツール**、順にダブルクリック**データ ソース (ODBC)**です。 Microsoft Windows の以前のバージョンを実行するコンピューターで、アイコンの名前は**32 ビット ODBC**または単に**ODBC**です。  
  
 次の図は、16 ビット アプリケーションが 32 ビット ドライバーのセットアップ DLL を呼び出す方法を示します。 16 ビット インストーラー DLL と 32 ビット ドライバーのセットアップ DLL は、32 ビット インストーラー DLL の呼び出しに 16 ビットのインストーラー DLL の呼び出しを変換する汎用サンク DLL です。  
  
 ![どのように、16 &#45; ビット アプリ呼び出す 32 &#45; ビット ドライバーのセットアップ DLL](../../odbc/microsoft/media/sdka3.gif "sdka3")  
  
 Windows on Windows の (32 ビットの 16 ビット サンキング)、32 ビットの設定を使用して渡される 16 ビットの引数値 Ds32gt.dll 変換という別のサンク DLL DLL はバックアップから 16 ビット。  
  
## <a name="components"></a>コンポーネント  
 MDAC 2.8 SP1 SDK の ODBC コンポーネントには、32 ビット ドライバーの 16 ビット アプリケーションを実行するため、次のファイルが含まれています。 これらのコンポーネントが \Redist ディレクトリです。  
  
|ファイル名|Description|  
|---------------|-----------------|  
|Odbc16gt.dll|16 ビット ODBC の汎用サンク DLL|  
|Odbc32gt.dll|32 ビット ODBC の汎用サンク DLL|  
|Odbccp32.dll|32 ビット インストーラー DLL|  
|Odbcad32.exe|32 ビット プログラムを管理者|  
|Odbcinst.hlp|インストーラーのヘルプ ファイル|  
|Ds16gt.dll|16 ビット ドライバーのセットアップ DLL をサンク ジェネリック|  
|Ctl3d32.dll|32 ビットの 3 次元ウィンドウ スタイル ライブラリ|  
  
 さらに、ODBC 3.51 の一部ではない、16 ビット ODBC 2.10 ドライバー マネージャーと共に以下のファイルを必要し、16 ビット アプリケーションにインストールする必要があります。  
  
|ファイル名|Description|  
|---------------|-----------------|  
|Odbc.dll|16 ビット ドライバー マネージャー|  
|Odbcinst.dll|16 ビット インストーラー DLL|  
|Odbcadm.exe|16 ビット odbc データ ソース アドミニストレーター|

