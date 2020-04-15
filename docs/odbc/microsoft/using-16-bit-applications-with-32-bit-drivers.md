---
title: 32 ビット ドライバーでの 16 ビット アプリケーションの使用 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC drivers [ODBC], 16-bit applications
- 16-bit applications with 32-bit drivers [ODBC]
ms.assetid: 68feb3b7-c01a-4f42-8df9-f9c182d89325
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c919ed8c3f3791720d67ebdcbf5cfbdbea2a0455
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307633"
---
# <a name="using-16-bit-applications-with-32-bit-drivers"></a>32 ビット ドライバーで 16 ビット アプリケーションを使用
> [!IMPORTANT]  
>  この機能は、今後のバージョンの Windows で削除される予定です。 新しい開発作業でこの機能を使用することは避け、現在この機能を使用しているアプリケーションを変更する予定です。 代わりに 32 ビットまたは 64 ビットドライバー・マネージャーを使用してください。  
  
 32 ビット ドライバーがスレッドを作成する Win32 API 関数を明示的に呼び出さない限り、Windows ベースのシステムで 32 ビット ドライバーを使用して 16 ビット アプリケーションを実行できます。 Windows (WOW) サブシステムは、アプリケーションを 16 ビット モードで実行し、オペレーティング システムへの 16 ビット呼び出しを解決します。 ODBC サンキング DLL は、アプリケーションからの 16 ビットの呼び出しを 32 ビット ドライバーに解決します。 16 ビット アプリケーションは Windows API を使用し、32 ビット ドライバーは Win32 API を使用します。  
  
## <a name="architecture"></a>Architecture  
 次の図は、16 ビット アプリケーションが 32 ビット ドライバーと通信する方法を示しています。 16 ビット ドライバー マネージャーと 32 ビット ドライバーの間には、16 ビット ODBC 呼び出しを 32 ビット ODBC 呼び出しに変換する汎用サンキング DLL です。  
  
 ![16&#45;ビットアプリが32&#45;ビットドライバと通信する方法](../../odbc/microsoft/media/sdka2.gif "sdka2")  
  
> [!NOTE]  
>  16 ビット アプリケーションが 32 ビット ドライバーとやり取りする場合、常に 32 ビット ドライバー マネージャーは、ドライバーでサポートされている ODBC のバージョンとして "2.0" を返します。  
  
## <a name="administration"></a>管理  
 ODBC データ ソース アドミニストレータを使用して、32 ビット ドライバのデータ ソースを管理できます。 ® Microsoft® Windows2000 を実行しているコンピュータで ODBC アドミニストレータを開くには、Windows のコントロール パネルを開き、[**管理ツール**] をダブルクリックして、[**データ ソース (ODBC)]** をダブルクリックします。 以前のバージョンの Windows を実行しているコンピュータでは、アイコンの名前は**32 ビット ODBC**または単に**ODBC**です。  
  
 次の図は、16 ビット アプリケーションが 32 ビット ドライバー セットアップ DLL を呼び出す方法を示しています。 16 ビット インストーラー DLL と 32 ビット ドライバーセットアップ DLL の間には、16 ビット インストーラー DLL 呼び出しを 32 ビット インストーラー DLL 呼び出しに変換する汎用サンク DLL です。  
  
 ![16&#45;ビット アプリが 32&#45;ビット ドライバー セットアップ DLL を呼び出す方法](../../odbc/microsoft/media/sdka3.gif "sdka3")  
  
 Windows 上の Windows (16 ビットから 32 ビットサンク) では、Ds32gt.dll という名前の追加のサンク DLL が、32 ビット セットアップ DLL を介して渡された 16 ビットの引数値を 16 ビットに変換します。  
  
## <a name="components"></a>Components  
 MDAC 2.8 SP1 SDK の ODBC コンポーネントには、32 ビット ドライバを使用して 16 ビット アプリケーションを実行するための次のファイルが含まれています。 これらのコンポーネントは \Redist ディレクトリにあります。  
  
|ファイル名|説明|  
|---------------|-----------------|  
|Odbc16gt.dll|16 ビット ODBC 汎用サンキング DLL|  
|Odbc32gt.dll|32 ビット ODBC 汎用サンキング DLL|  
|Odbccp32.dll|32 ビット インストーラー DLL|  
|Odbcad32.exe|32 ビット管理者プログラム|  
|Odbcinst.hlp|インストーラ ヘルプ ファイル|  
|Ds16gt.dll|16 ビット ドライバ セットアップ汎用サンキング DLL|  
|Ctl3d32.dll|32 ビット 3 次元ウィンドウ スタイル ライブラリ|  
  
 さらに、ODBC 3.51 の一部ではない 16 ビット ODBC 2.10 ドライバー マネージャーと共に、次のファイルが必要であり、16 ビット アプリケーションでインストールする必要があります。  
  
|ファイル名|説明|  
|---------------|-----------------|  
|Odbc.dll|16 ビット ドライバー マネージャー|  
|Odbcinst.dll|16 ビット インストーラー DLL|  
|ファイル名|16 ビット ODBC アドミニストレーター プログラム|
