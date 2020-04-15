---
title: 32 ビット ドライバーで 32 ビット アプリケーションを使用する |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC drivers [ODBC], 32-bit applications
- 32-bit applications with 32-bit drivers [ODBC]
ms.assetid: 0cdd5788-5642-4280-8d53-b4ec461aafa1
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 31512f9339b9d46225bb4f1198cb617a48509acb
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307603"
---
# <a name="using-32-bit-applications-with-32-bit-drivers"></a>32 ビット ドライバーで 32 ビット アプリケーションを使用
32 ビット ドライバーを使用して 32 ビット アプリケーションを実行できます。 32 ビット アプリケーションと 32 ビット ドライバーは、Win32® API を使用します。  
  
## <a name="architecture"></a>Architecture  
 次の図は、32 ビット アプリケーションが 32 ビット ドライバーと通信する方法を示しています。 アプリケーションは、32 ビット ドライバー マネージャーを呼び出し、32 ビット ドライバーを呼び出します。  
  
 ![32&#45;ビットアプリが32&#45;ビットドライバと通信する方法](../../odbc/microsoft/media/sdka6.gif "SDKA6")  
  
> [!IMPORTANT]  
>  WindowsNT/Windows2000 では、32 ビット サンキング インストーラ DLL を使用しないでください。 32 ビット インストーラー DLL と同じファイル名を持ちますが、別の DLL です。  
  
## <a name="administration"></a>管理  
 ODBC データ ソース アドミニストレータを使用して、32 ビット ドライバのデータ ソースを管理できます。 Windows 2000 を実行しているコンピュータで ODBC アドミニストレータを開くには、Windows のコントロール パネルを開き、[**管理ツール**] をダブルクリックして、[**データ ソース (ODBC)]** をダブルクリックします。 以前のバージョンの Windows を実行しているコンピュータでは、アイコンの名前は**32 ビット ODBC**または単に**ODBC**です。  
  
## <a name="components"></a>Components  
 ODBC コンポーネントには、32 ビット ドライバーを使用して 32 ビット アプリケーションを実行するための次のファイルが含まれています。 これらのコンポーネントは \Redist ディレクトリにあります。  
  
|ファイル名|説明|  
|---------------|-----------------|  
|Odbc32.dll|32 ビット ドライバー マネージャー|  
|Odbccp32.dll|32 ビット インストーラー DLL|  
|Odbcad32.exe|32 ビット ODBC アドミニストレーター プログラム|  
|Odbcinst.hlp|インストーラ ヘルプ ファイル|  
|Msvcrt40.dll|C ランタイム ライブラリ|
