---
title: 一括コピー操作 (ODBC) の実行 |マイクロソフトのドキュメント
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: native-client-odbc-bulk-copy-operations
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, bulk copy
- bulk copy [ODBC]
- ODBC, bulk copy operations
- minimally logged operations [SQL Server Native Client]
- bulk copy [ODBC], about bulk copy
ms.assetid: 5c793405-487c-4f52-88b8-0091d529afb3
caps.latest.revision: 38
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: c8d524f69e36f5a6ef9ebea47f3c1689d8128b7e
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "43067615"
---
# <a name="performing-bulk-copy-operations-odbc"></a>一括コピー操作の実行 (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  ODBC 標準では、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の一括コピー操作が直接サポートされません。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーでは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 7.0 以降のインスタンスに接続するときに、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の一括コピー操作を実行する DB-Library 関数がサポートされます。 このドライバー固有の拡張機能では、一括コピー関数を使用する既存の DB-Library アプリケーションを簡単にアップグレードできる手段が用意されています。 次のファイルには、一括コピー専用のサポートが含まれています。  
  
-   sqlncli.h  
  
     一括コピー関数の関数プロトタイプと定数定義が含まれています。 一括コピー操作を実行する ODBC アプリケーションでは、sqlncli.h をインクルードする必要があります。このファイルは、コンパイル時にアプリケーションのインクルード パスに存在している必要があります。  
  
-   sqlncli11.lib  
  
     リンカーのライブラリ パスに存在し、リンクされるファイルとして指定する必要があります。 sqlncli11.lib は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーに付属しています。  
  
-   sqlncli11.dll  
  
     実行時に存在する必要があります。 sqlncli11.dll は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーに付属しています。  
  
> [!NOTE]  
>  ODBC **SQLBulkOperations**関数へのリレーションシップを持たない、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]一括コピー関数。 アプリケーションでは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 固有の一括コピー関数を使用して、一括コピー操作を実行する必要があります。  
  
## <a name="minimally-logging-bulk-copies"></a>一括コピーの最小ログ記録  
 完全復旧モデルでは、一括読み込みで実行されたすべての行挿入操作が、トランザクション ログに完全に記録されます。 ただし大量のデータを読み込むと、トランザクション ログがすぐにいっぱいになる可能性があります。 特定の条件下では、最小ログ記録が可能になります。 最小ログ記録を行うことで、一括読み込み操作によってログ領域がいっぱいになる可能性が少なくなります。また、これは完全なログ記録よりも効率的です。  
  
 最小ログ記録を使用する方法の詳細については、次を参照してください。[一括インポートで最小ログ記録の前提条件](../../relational-databases/import-export/prerequisites-for-minimal-logging-in-bulk-import.md)します。  
  
## <a name="remarks"></a>コメント  
 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降で bcp.exe を使用すると、[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] より前のバージョンでは発生しなかった状況でエラーが発生することがあります。 これは、新しいバージョンでは bcp.exe でデータ型が暗黙的に変換されなくなったためです。 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] より前のバージョンでは、対象テーブルのデータ型が money データ型の場合、bcp.exe で数値データが money データ型に変換されました。 ただし、その際には、余分なフィールドは単純に切り捨てられていました。 以降で[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]に対象のテーブルに合わせて切り捨てられますが、すべてのデータがある場合、ファイルと対象のテーブル、bcp.exe の間で型が一致しないデータのエラーが発生する場合は、します。 このエラーを解決するには、対象のデータ型に合わせてデータを修正します。 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] より前のリリースの bcp.exe を使用することもできます。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
-   [データ ファイルとフォーマット ファイルの使用](../../relational-databases/native-client-odbc-bulk-copy-operations/using-data-files-and-format-files.md)  
  
-   [プログラム変数からの一括コピー](../../relational-databases/native-client-odbc-bulk-copy-operations/bulk-copying-from-program-variables.md)  
  
-   [一括コピー バッチ サイズの管理](../../relational-databases/native-client-odbc-bulk-copy-operations/managing-bulk-copy-batch-sizes.md)  
  
-   [テキスト データと画像データの一括コピー](../../relational-databases/native-client-odbc-bulk-copy-operations/bulk-copying-text-and-image-data.md)  
  
-   [DB-Library から ODBC への一括コピーの変換](../../relational-databases/native-client-odbc-bulk-copy-operations/converting-from-db-library-to-odbc-bulk-copy.md)  
  
## <a name="see-also"></a>参照  
 [SQL Server Native Client &#40;ODBC&#41;](../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)   
 [データの一括インポートと一括エクスポート &#40;SQL Server&#41;](../../relational-databases/import-export/bulk-import-and-export-of-data-sql-server.md)  
  
  
