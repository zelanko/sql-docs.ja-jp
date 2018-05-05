---
title: データ ファイルとフォーマット ファイルを使用して |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: native-client-odbc-bulk-copy-operations
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- bulk copy [ODBC], file formats
- ODBC, functions
- SQL Server Native Client ODBC driver, bulk copy
- bulk copy [SQL Server Native Client]
- ODBC, bulk copy operations
- bulk copy [ODBC], data files
ms.assetid: c01b7155-3f0a-473d-90b7-87a97bc56ca5
caps.latest.revision: 30
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 4473473b97545a522ed0a051a69104d2b3d69af8
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="using-data-files-and-format-files"></a>データ ファイルとフォーマット ファイルの使用
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  最も単純な一括コピー プログラムでは次の操作を実行します。  
  
1.  呼び出し[bcp_init](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-init.md)を指定するテーブルからの一括コピー出力 (BCP_OUT を設定する) またはデータ ファイルを表示します。  
  
2.  呼び出し[bcp_exec](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-exec.md)を一括コピー操作を実行します。  
  
 データ ファイルはネイティブ モードで作成されるので、テーブルやビューのすべての列から取得したデータは、データベースと同じ形式でデータ ファイルに格納されます。 その後、同様の手順を使用して、このデータ ファイルをサーバーに一括コピーできます。ただし、DB_OUT ではなく DB_IN を設定します。 この操作は、コピー元のテーブルとコピー先のテーブルの構造が厳密に同じ場合にのみ機能します。 結果のデータ ファイルにも入力として使用できる、 **bcp**ユーティリティを使用して、 **/n** (ネイティブ モード) スイッチ。  
  
 テーブルやビューから直接取得するのではなく、[!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントの結果セットを一括コピー出力するには、次の操作を実行します。  
  
1.  呼び出す**bcp_init**一括コピーを指定する、出力が、テーブル名に NULL を指定します。  
  
2.  呼び出す[bcp_control](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-control.md)で*eOption*に BCPHINTS を設定し、 *iValue* TRANSACT-SQL ステートメントを含む SQLTCHAR 文字列へのポインターに設定します。  
  
3.  呼び出す**bcp_exec**を一括コピー操作を実行します。  
  
 結果セットを生成するステートメントであればどのような [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントも使用できます。 作成されるデータ ファイルには [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントの最初の結果セットが格納されます。 [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントで複数の結果セットが生成される場合、一括コピーでは、最初の結果セットよりも後にある結果セットは無視されます。  
  
 も、テーブル内の別の形式でデータを格納する列のデータ ファイルを作成するには[bcp_columns](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-columns.md)変更される列の数を指定する呼び出して[bcp_colfmt](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-colfmt.md)列ごとにフォーマットが変更するにです。 これは、呼び出した後**bcp_init**呼び出す前に**bcp_exec**です。 **bcp_colfmt**データ ファイル内で列のデータが格納される形式を指定します。 一括コピー入力または一括コピー出力時に、この処理を利用できます。使用することも**bcp_colfmt**を行と列ターミネータを設定します。 たとえば、データにタブ文字が含まれていない場合を作成、タブ区切りファイルを使用して**bcp_colfmt**列ごとにターミネータがタブ文字を設定します。  
  
 ときに一括コピー出力を使用して**bcp_colfmt**、呼び出すことで作成したデータ ファイルを記述したフォーマット ファイルを簡単に作成できます[bcp_writefmt](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-writefmt.md)を最後に呼び出した後**bcp_colfmt**.  
  
 一括コピーするときに、フォーマット ファイルで説明されているデータ ファイルから、呼び出すことによって、フォーマット ファイルを読み取る[bcp_readfmt](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-readfmt.md)後**bcp_init**前に**bcp_exec**です。  
  
 **Bcp_control**関数への一括コピー時にいくつかのオプションを制御する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データ ファイルからです。 **bcp_control**エラーの終了前に、一括コピーの開始、停止、行、バッチ サイズをファイル内の行の最大数などのオプションを設定します。  
  
## <a name="see-also"></a>参照  
 [一括コピー操作を実行する&#40;ODBC&#41;](../../relational-databases/native-client-odbc-bulk-copy-operations/performing-bulk-copy-operations-odbc.md)  
  
  
