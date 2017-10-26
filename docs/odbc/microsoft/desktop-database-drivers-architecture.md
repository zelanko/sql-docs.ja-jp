---
title: "デスクトップ データベース ドライバー アーキテクチャ |Microsoft ドキュメント"
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
- Jet-based ODBC drivers [ODBC], architecture
- ODBC desktop database drivers [ODBC], architecture
- desktop database drivers [ODBC], architecture
ms.assetid: 8b4d13f7-ab37-40b4-a9c6-145e7385352f
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 0b85711437c50ccc246ad1af1432d9475d1cfc3d
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="desktop-database-drivers-architecture"></a>デスクトップ データベース ドライバーのアーキテクチャ
使用するには、Microsoft Windows 95 以降、または Windows NT 4.0 および Windows 2000 には、これらのドライバーが設計されています。 Windows 95 以降; のみの 32 ビット アプリケーションがサポートされます。Windows NT 4.0 と Windows 2000 では、16 ビットおよび 32 ビット アプリケーションをサポートします。  
  
> [!NOTE]  
>  これらのドライバーで使用される ODBC のバージョンについてを参照してください、 *ODBC プログラマ リファレンス*、および過去および現在のリリース ノートします。 これらのドライバーは、以下の領域を除くに準拠している、 *ODBC プログラマ リファレンス*です。  
  
 ODBC デスクトップ データベース ドライバーには、Microsoft Access、dBASE、Excel、Paradox、およびテキストの 32 ビット ドライバーが含まれます。 なし 16 ビット ドライバーが含まれます。 (Microsoft FoxPro 用のドライバーがあるとは別にします。)  
  
 Windows 95 以降のアプリケーション/ドライバー アーキテクチャ。  
  
 ![アプリ (&) #47; ドライバーのアーキテクチャ: Windows 95 以降](../../odbc/microsoft/media/odbcjetarch1.gif "ODBCJetArch1")  
  
 Windows 95 で 16 ビット アプリケーションでこれらのドライバーの使用はサポートされていません。  
  
 Windows NT 4.0 および Windows 2000 上のアプリケーション/ドライバー アーキテクチャ。  
  
 ![アプリ (&) #47; ドライバーのアーキテクチャ: NT 4.0 および Windows 2000](../../odbc/microsoft/media/odbcjetarch2.gif "ODBCJetArch2")  
  
 デスクトップ データベース ドライバーは、2 層ドライバーです。 2 層構成で、ドライバーでは、解析、検証、最適化、およびクエリの実行のプロセスは実行されません。 代わりに、Microsoft Jet は、これらのタスクを実行します。 ODBC API の呼び出しを処理し、SQL エンジンとして機能します。 Microsoft Jet は、整数型、分離不可能の部分で、ドライバーになりました: ドライバーに付属しているし、ドライバーが存在する場合でも、コンピューター上の他のアプリケーションが使用しないことです。  
  
 デスクトップ データベース ドライバーは、6 つの異なるドライバーで構成されている — または、具体的には、1 つのドライバー ファイル (Odbcjt32.dll) を ODBC[ドライバー マネージャー](../../odbc/reference/the-driver-manager.md)は 6 つの異なる方法で使用します。 データ ソースのレジストリ エントリで DRIVERID フラグは、Odbcjt32.dll でどのドライバー、ドライバー マネージャーが使用を決定します。 アプリケーションへの呼び出しに含まれる接続文字列でこのフラグを渡します**SQLDriverConnect**です。 既定では、このフラグは、Microsoft Access ドライバーの ID です。  
  
 ドライバーのセットアップ ファイルは、セットアップ時に、DRIVERID フラグを変更します。 Microsoft Access ドライバーを除くすべてのドライバーには、関連付けられている設定 DLL が必要があります。 クリックすると、**セットアップ**で、 [Microsoft ODBC データ ソース アドミニストレーター](../../odbc/admin/odbc-data-source-administrator.md) ODBC インストーラー DLL (Odbcinst.dll) は、データ ソースのセットアップ DLL を読み込みます。 ODBC インストーラー関数をエクスポートする DLL のセットアップ**SQLConfigDataSource**です。 ウィンドウ ハンドルが渡された場合**SQLConfigDataSource**、この関数は、セットアップ ウィンドウを表示し、ユーザー インターフェイスから選択したドライバーに従って DRIVERID フラグを変更します。  
  
 NULL のウィンドウ ハンドルが渡されるファイルがプログラムによって作成されると、 **SQLConfigDataSource**、関数、データ ソースを作成、動的にに従って DRIVERID フラグを変更して、 *lpszDriver*関数呼び出しの引数。  
  
 Odbcjt32.dll では、Microsoft Jet API の上に ODBC 関数を実装します。 ODBC および Microsoft Jet の関数の間で直接マッピングただしです。 カーソル モデルでは、SQL のマッピングなど、さまざまな要因は、関数の直接的な相関関係を回避します。  
  
 ODBC ドライバーは、Microsoft Jet エンジンと ODBC ドライバー マネージャーの間に存在します。 アプリケーションによって呼び出されたいくつかの ODBC 関数がドライバー マネージャーによって処理され、ドライバーに渡されません。 Microsoft Jet をこれらの関数には、ドライバー マネージャーへの直接接続があるないために、呼び出す関数を表示されません。

