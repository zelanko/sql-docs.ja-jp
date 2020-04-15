---
title: デスクトップ データベース ドライバのアーキテクチャ |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Jet-based ODBC drivers [ODBC], architecture
- ODBC desktop database drivers [ODBC], architecture
- desktop database drivers [ODBC], architecture
ms.assetid: 8b4d13f7-ab37-40b4-a9c6-145e7385352f
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ae6fb72bb3ed0a9bca1571eb572bbfbd20fe9995
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81288742"
---
# <a name="desktop-database-drivers-architecture"></a>デスクトップ データベース ドライバーのアーキテクチャ
これらのドライバは、Windows 95 以降、または Windows NT 4.0 および Windows 2000 で使用するために設計されています。 Windows 95 以降では、32 ビット アプリケーションのみがサポートされます。16 ビットおよび 32 ビットのアプリケーションは、Windows NT 4.0 および Windows 2000 でサポートされています。  
  
> [!NOTE]  
>  これらのドライバで使用する ODBC のバージョンについては *、『ODBC プログラマ リファレンス*』および過去および現在のリリース ノートを参照してください。 これらのドライバは、特に指定された領域を除き *、ODBC プログラマ リファレンス*に準拠しています。  
  
 ODBC デスクトップ データベース ドライバには、Access、dBASE、Excel、パラドックス、およびテキスト用の 32 ビット ドライバが含まれています。 16 ビット ドライバーは含まれていません。 (マイクロソフトフォックスプロのドライバは別々に入手できます)。  
  
 Windows 95 以降のアプリケーション/ドライバ アーキテクチャは次のとおりです。  
  
 ![アプリ&#47;ドライバー アーキテクチャ: Windows 95 以降](../../odbc/microsoft/media/odbcjetarch1.gif "ODBCジェットアーチ1")  
  
 Windows 95 で 16 ビット アプリケーションでこれらのドライバーを使用することはサポートされていません。  
  
 Windows NT 4.0 および Windows 2000 のアプリケーション/ドライバ アーキテクチャは次のとおりです。  
  
 ![アプリケーション&#47;ドライバ アーキテクチャ: NT 4.0 および Windows 2000](../../odbc/microsoft/media/odbcjetarch2.gif "2")  
  
 デスクトップ データベース ドライバは 2 層ドライバーです。 2 層構成では、ドライバーは、クエリの解析、検証、最適化、および実行のプロセスを実行しません。 代わりに、これらのタスクを実行します。 ODBC API 呼び出しを処理し、SQL エンジンとして機能します。 Microsoft Jet は、ドライバーの不可欠な、切っても切れない部分となっています: それはドライバーと一緒に出荷され、コンピューター上の他のアプリケーションを使用していない場合でも、ドライバーと一緒に存在します。  
  
 デスクトップ データベース ドライバは、6 つの異なるドライバ (正確には、ODBC[ドライバ マネージャ](../../odbc/reference/the-driver-manager.md)が 6 つの異なる方法で使用する 1 つのドライバ ファイル (Odbcjt32.dll) で構成されています。 データ ソースのレジストリ エントリの DRIVERID フラグは、ドライバー マネージャーが使用する Odbcjt32.dll のドライバーを決定します。 アプリケーションは **、SQLDriverConnect**への呼び出しに含まれる接続文字列でこのフラグを渡します。 既定では、フラグは、Access ドライバーの ID です。  
  
 ドライバセットアップファイルは、セットアップ時にDRIVERIDフラグを変更します。 Microsoft Access ドライバーを除くすべてのドライバーには、関連付けられているセットアップ DLL があります。 データ ソースの[MICROSOFT ODBC データ ソース アドミニストレータ](../../odbc/admin/odbc-data-source-administrator.md)で **[セットアップ**] をクリックすると、ODBC インストーラー DLL (Odbcinst.dll) は、セットアップ DLL を読み込みます。 セットアップ DLL は、ODBC インストーラー関数**をエクスポートします**。 ウィンドウ ハンドルが**SQLConfigDataSource**に渡された場合、この関数はセットアップ ウィンドウを表示し、ユーザー インターフェイスから選択したドライバーに応じて DRIVERID フラグを変更します。  
  
 プログラムによってファイルが作成されると、NULL ウィンドウ ハンドルが**SQLConfigDataSource**に渡され、関数は関数呼び出しの*引数 lpszDriver*に従って DRIVERID フラグを変更して、動的にデータ ソースを作成します。  
  
 Odbcjt32.dll は、マイクロソフトのジェット API の上に ODBC 関数を実装しています。 ただし、ODBC 関数と Jet 関数の間に直接マッピングはありません。 カーソル モデルや SQL マッピングなど、多くの要因によって、関数の直接的な相関関係が妨げられます。  
  
 ODBC ドライバーは、マイクロソフトの Jet エンジンと ODBC ドライバー マネージャーの間に存在します。 アプリケーションによって呼び出される一部の ODBC 関数は、ドライバー マネージャーによって処理され、ドライバーに渡されません。 これらの関数では、ドライバ マネージャに直接接続されていないため、関数呼び出しが表示されることはありません。
