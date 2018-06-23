---
title: 結果データのフェッチ |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: native-client-odbc-results
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQLFetchScroll function
- SQL Server Native Client ODBC driver, result sets
- ODBC applications, result sets
- data types [ODBC], fetching
- SQLBindCol function
- result sets [ODBC], fetching
- fetching [ODBC]
- ODBC data types, fetching
- SQLFetch function
- SQL Server Native Client ODBC driver, data types
- SQLGetData function
ms.assetid: b289c7fb-5017-4d7e-a2d3-19401e9fc4cd
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 1cb4046f669a3d35de7c99b0d1d754bd85f067f6
ms.sourcegitcommit: a78fa85609a82e905de9db8b75d2e83257831ad9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2018
ms.locfileid: "35695874"
---
# <a name="fetching-result-data"></a>結果データのフェッチ
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  ODBC アプリケーションでは、結果データのフェッチを 3 つの方法で実行できます。  
  
 最初のオプションがに基づいて[SQLBindCol](../../relational-databases/native-client-odbc-api/sqlbindcol.md)です。 アプリケーションを使用して結果セットをフェッチ、前に**SQLBindCol**プログラム変数に結果セット内の各列をバインドします。 結果セット列にバインドされた変数に現在の行のデータ転送については、ドライバーがアプリケーションの呼び出しを時間の列をバインドすると後、 **SQLFetch**または[SQLFetchScroll](../../relational-databases/native-client-odbc-api/sqlfetchscroll.md)です。 結果セット列のデータ型とプログラム変数のデータ型が異なる場合、ドライバーによってデータ変換が処理されます。 アプリケーションに 1 より大きい設定 SQL_ATTR_ROW_ARRAY_SIZE がある場合は、結果の列を呼び出すたびに入力されるすべての変数の配列にバインドできます**SQLFetchScroll**です。  
  
 2 番目のオプションがに基づいて[SQLGetData](../../relational-databases/native-client-odbc-api/sqlgetdata.md)です。 アプリケーションが使用しない**SQLBindCol**結果にバインドするには、プログラム変数に列を設定します。 呼び出すたび**SQLFetch**、アプリケーション呼び出し**SQLGetData** 1 回、結果の各列に対して次のように設定します。 します。 **SQLGetData**特定のプログラム変数に特定の結果セット列からデータを転送するドライバーに指示し、列と変数のデータ型を指定します。 そのため、結果列のデータ型とプログラム変数のデータ型が異なる場合は、ドライバーでデータを変換できます。 **テキスト**、 **ntext**、および**イメージ**列は大きすぎて、プログラム変数に収まるように、通常を使用して取得できます**SQLGetData**です。 場合、**テキスト**、 **ntext**、または**イメージ**結果列のデータがプログラム変数よりも大きい**SQLGetData** SQL_SUCCESS_ を返しますWITH_INFO と SQLSTATE 01004 (文字列データの右側が切り捨てられました)。 連続して呼び出す**SQLGetData**の連続したチャンクを返す、**テキスト**または**イメージ**データ。 データの末尾に達すると、 **SQLGetData** SQL_SUCCESS を返します。 SQL_ATTR_ROW_ARRAY_SIZE に 1 よりも大きい値を指定すると、フェッチのたびに行セットが返されます。 使用する前に**SQLGetData**、最初に使用する必要があります**SQLSetPos**を現在の行と行セット内の特定の行を指定します。  
  
 3 番目のオプションは、の組み合わせを使用する**SQLBindCol**と**SQLGetData**です。 アプリケーションでした、たとえば、結果セットの最初の 10 個の列をバインドおよびその後、各フェッチ操作で呼び出す**SQLGetData** 3 回バインドされていない次の 3 つの列からデータを取得します。 これは通常される使用結果セットには、1 つまたは複数が含まれている**テキスト**または**イメージ**列です。  
  
 カーソル オプションに応じて、結果セットの設定、アプリケーションも使用できますのスクロール オプション**SQLFetchScroll**結果セットをスクロールします。  
  
 使用、余分な**SQLBindCol**結果にバインドするセットの列をプログラム変数には高価なため**SQLBindCol**メモリの割り当てに ODBC ドライバーが発生します。 結果列を変数にバインドすると、バインディングを有効なままにするかが呼び出されるまで[SQLFreeHandle](../../relational-databases/native-client-odbc-api/sqlfreehandle.md)を呼び出し、ステートメント ハンドルを解放する[SQLFreeStmt](../../relational-databases/native-client-odbc-api/sqlfreestmt.md)で*fOption* SQL_UNBIND に設定します。 バインドは、ステートメントが完了しても自動的には元に戻りません。  
  
 このロジックにより、異なるパラメーターを指定して同じ SELECT ステートメントを何度も実行することで、効率を上げることができます。 結果セットには、同じ構造が保持されて、いるため、結果セットのバインドを 1 回、すべての SELECT ステートメントを処理し、呼び出す**SQLFreeStmt**で*fOption*前回の実行後、SQL_UNBIND に設定します。 呼び出す必要はありません**SQLBindCol** 、せず結果セットの最初の呼び出し元の列をバインドする**SQLFreeStmt**で*fOption* SQL_UNBIND に設定すると、それまでのバインドを解放します。  
  
 使用する場合**SQLBindCol**、いずれかの操作を行方向または列方向のバインドを作成することができます。 行方向のバインドの方が、列方向のバインドよりも処理がやや高速になります。  
  
 使用することができます**SQLGetData**結果のバインドではなく列によってごとにデータを取得する設定を使用して列**SQLBindCol**です。 使用して、結果セットに数行のみが含まれている場合**SQLGetData**の代わりに**SQLBindCol**が高速であるそれ以外の場合、 **SQLBindCol**最適なパフォーマンスが得られます。 場合に常に配置しないデータ変数の同じセットで、必要がありますを使用する**SQLGetData**常に再バインドの代わりにします。 使用できるだけ**SQLGetData**に含まれる列は選択リストですべての列をバインドした後で**SQLBindCol**です。 この列は既に使用されて、列の後に表示する必要がありますも**SQLGetData**です。  
  
 ODBC 関数のデータの移動、プログラム変数の内外になどに対処する**SQLGetData**、 **SQLBindCol**、および[SQLBindParameter](../../relational-databases/native-client-odbc-api/sqlbindparameter.md)、暗黙的なデータ型のサポート変換を行います。 たとえば、整数列を文字列プログラム変数にバインドするアプリケーションでは、プログラム変数にデータを格納する前に、ドライバーが自動的にそのデータを整数から文字に変換します。  
  
 アプリケーションでのデータ変換は最小限に抑える必要があります。 列やパラメーターは、アプリケーションでの処理にデータ変換が必要な場合を除き、同じデータ型のプログラム変数にバインドする必要があります。 ただし、あるデータ型から別のデータ型に変換する必要がある場合は、アプリケーションでのデータ変換よりもドライバーによるデータ変換の方が効率的です。 通常、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーは、ネットワーク バッファーからアプリケーションの変数にデータを直接転送します。 データ変換を行うようにドライバーに要求すると、ドライバーはデータをバッファーに格納し、CPU サイクルを使用してデータを変換します。  
  
 プログラム変数を除く、列から転送されたデータを保持するのに十分な大きさにする必要があります**テキスト**、 **ntext**、および**イメージ**データ。 結果セットのデータを取得してそのデータを変数に格納するときに、その変数が小さすぎてデータを保持できない場合、ドライバーは警告を生成します。 その結果、ドライバーでは警告メッセージ用のメモリを割り当て、ドライバーとアプリケーションの両方で、警告メッセージの処理やエラーの処理に CPU サイクルが必要になります。 アプリケーションでは、取得するデータを保持するのに十分なサイズの変数を割り当てるか、選択リストで SUBSTRING 関数を使用して結果セット内の列のサイズを小さくする必要があります。  
  
 SQL_C_DEFAULT を使用して C 変数のデータ型を指定する場合は注意が必要です。 SQL_C_DEFAULT は、C 変数のデータ型と、列やパラメーターの SQL データ型を一致させることを指定します。 SQL_C_DEFAULT が指定されている場合、 **ntext**、 **nchar**、または**nvarchar**列で、Unicode データは、アプリケーションに返されます。 そのため、アプリケーションが Unicode データを処理するようにコーディングされていないと、さまざまな問題が発生する可能性があります。 同じ種類の問題が発生する可能性、 **uniqueidentifier** (SQL_GUID) データ型。  
  
 **テキスト**、 **ntext**、および**イメージ**データが大きすぎて、単一のプログラム変数には、通常と処理では通常**SQLGetData**の代わりに**SQLBindCol**です。 サーバー カーソルを使用するときに、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーはバインドされていないため、データを転送しないように最適化されて**テキスト**、 **ntext**、または**イメージ**に列を行をフェッチした時刻。 **テキスト**、 **ntext**、または**イメージ**データが実際には取得されません、サーバーからアプリケーションの問題まで**SQLGetData**用、列です。  
  
 この最適化は、アプリケーションに適用することができますようにありません**テキスト**、 **ntext**、または**イメージ**ユーザーは、カーソルを上下スクロール中にデータが表示されます。 アプリケーションが呼び出すことができます、ユーザーは、行を選択し、 **SQLGetData**を取得する、**テキスト**、 **ntext**、または**イメージ**データ。 これにより、送信、**テキスト**、 **ntext**、または**イメージ**の任意の行のデータ、ユーザーが選択されていないと非常に大量のデータの転送を保存することができます。  
  
## <a name="see-also"></a>参照  
 [結果の処理&#40;ODBC&#41;](../../relational-databases/native-client-odbc-results/processing-results-odbc.md)  
  
  
