---
title: "ODBC テーブル値パラメーターの使用 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-table-valued-parameters
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (ODBC), scenarios
- ODBC, table-valued parameters
ms.assetid: f1b73932-4570-4a8a-baa0-0f229d9c32ee
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 050d0e33419b2f73fba8e5e7fd011d786fcb9f21
ms.sourcegitcommit: a0aa5e611a0e6ebb74ac1e2f613e8916dc7a7617
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2018
---
# <a name="uses-of-odbc-table-valued-parameters"></a>ODBC テーブル値パラメーターの使用
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  このトピックでは、ODBC でテーブル値パラメーターを使用する主なユーザー シナリオについて説明します。  
  
-   複数行のバッファーに完全にバインドされるテーブル値パラメーター (すべての値をメモリ内に保持した TVP としてデータを送信する)  
  
-   行のストリーミングを使用するテーブル値パラメーター (実行時のデータを使用する TVP としてデータを送信する)  
  
-   システム カタログからテーブル値パラメーターのメタデータを取得  
  
-   準備されたステートメント用にテーブル値パラメーターのメタデータを取得  
  
## <a name="table-valued-parameter-with-fully-bound-multirow-buffers-send-data-as-a-tvp-with-all-values-in-memory"></a>複数行のバッファーに完全にバインドされるテーブル値パラメーター (すべての値をメモリ内に保持した TVP としてデータを送信する)  
 複数行のバッファーに完全にバインドされる形式で使用する場合、すべてのパラメーター値はメモリ内から使用できます。 このような形式は OLTP トランザクションなどでは一般的に行われ、テーブル値パラメーターを 1 つのストアド プロシージャにパッケージ化できます。 テーブル値パラメーターを使用しないと、複雑な複数のステートメントで構成されるバッチを動的に生成し、サーバーを複数回呼び出すことになります。  
  
 使用してテーブル値パラメーター自体がバインドされている[SQLBindParameter](http://go.microsoft.com/fwlink/?LinkId=59328)と共に他のパラメーターです。 すべてのパラメーターをバインドすると後、アプリケーションは各テーブル値パラメーターのパラメーター フォーカスの属性 SQL_SOPT_SS_PARAM_FOCUS を設定し、テーブル値パラメーターの列に対して SQLBindParameter を呼び出します。  
  
 テーブル値パラメーターのサーバー型は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 固有の新しい型 SQL_SS_TABLE です。 SQL_SS_TABLE の C データ型へのバインドは、常に SQL_C_DEFAULT にする必要があります。 テーブル値パラメーターにバインドされたパラメーターについては、データが転送されません。このパラメーターは、テーブルのメタデータを渡し、テーブル値パラメーターを構成する列にデータを渡す方法を制御するために使用されます。  
  
 テーブル値パラメーターの長さには、サーバーに送信される行数が設定されます。 *ColumnSize* SQLBindParameter のテーブル値パラメーターのパラメーターを送信できる最大行数を指定します。 これは、列バッファーの配列のサイズ。 *ParameterValuePtr* SQLBindParameter にテーブル値パラメーターのパラメーター バッファーです。 *ParameterValuePtr*とそれに関連する*BufferLength*必要な場合に、テーブル値パラメーターの型名を渡すために使用します。 型名は、ストアド プロシージャの呼び出しには必要ありませんが、SQL ステートメントには必要です。  
  
 SQLBindParameter への呼び出しで、テーブル値パラメーターの型名を指定すると、ANSI アプリケーションとしてビルドされているアプリケーションであっても、Unicode 値として常に指定する必要があります。 Sqlsetdescfield によるを使用して、テーブル値パラメーターの型名を指定するときに、アプリケーションを構築する方法に準拠したリテラルを使用できます。 ODBC ドライバー マネージャーで、必要な Unicode 変換を実行します。  
  
 テーブル値パラメーターおよびテーブル値パラメーター列のメタデータは、SQLGetDescRec、SQLSetDescRec、SQLGetDescField、および SQLSetDescField を使用して個別に明示的に操作できます。 ただし、SQLBindParameter のオーバー ロードは通常方が便利です、ほとんどの場合の明示的な記述子のアクセスが必要ないです。 この方法は、テーブル値パラメーターの影響を受ける記述子フィールドは若干異なるする点を除いて他のデータ型の場合は、SQLBindParameter の定義と一致します。  
  
 アプリケーションでは、場合によっては、動的な SQL を含むテーブル値パラメーターを使用して、テーブル値パラメーターの型名を指定する必要があります。 そうでは、テーブル値パラメーターは、接続の現在の既定のスキーマで定義されていない場合は、SQL_CA_SS_TYPE_CATALOG_NAME および SQL_CA_SS_TYPE_SCHEMA_NAME を SQLSetDescField を使用して設定する必要があります。 テーブル型の定義とテーブル値パラメーターは同じデータベースに存在する必要があるため、アプリケーションでテーブル値パラメーターを使用する場合は、SQL_CA_SS_TYPE_CATALOG_NAME を設定しないでください。 それ以外の場合、sqlsetdescfield によるエラーが報告されます。  
  
 このシナリオのサンプル コードはプロシージャ`demo_fixed_TVP_binding`で[テーブル値パラメーター &#40;ODBC&#41;](../../relational-databases/native-client-odbc-how-to/use-table-valued-parameters-odbc.md)です。  
  
## <a name="table-valued-parameter-with-row-streaming-send-data-as-a-tvp-using-data-at-execution"></a>行のストリーミングを使用するテーブル値パラメーター (実行時のデータを使用する TVP としてデータを送信する)  
 このシナリオでは、要求に応じてアプリケーションからドライバーに行が渡され、サーバーにストリーム送信されます。 これにより、すべての行をメモリ内にバッファリングする必要がなくなります。 これは、一括挿入や一括更新のシナリオの代表的な例です。 テーブル値パラメーターは、パフォーマンスの点ではパラメーター配列と一括コピーとの間に位置します。 つまり、テーブル値パラメーターは、パラメーター配列と同程度にプログラミングが容易ですが、サーバー側の柔軟性が増します。  
  
 テーブル値パラメーターとその列は、前の「複数行のバッファーに完全にバインドされるテーブル値パラメーター」で説明したとおりにバインドされますが、テーブル値パラメーター自体の長さのインジケーターは、SQL_DATA_AT_EXEC に設定されます。 ドライバーまたはに応答する SQLExecute SQLExecuteDirect 実行時データ パラメーターの通常の方法で、つまり、SQL_NEED_DATA を返すことによってです。 SQLParamData がの値を返します、ドライバー、テーブル値パラメーターのデータを受け入れる準備ができたら*ParameterValuePtr* SQLBindParameter にします。  
  
 アプリケーションでは、テーブル値パラメーターの SQLPutData を使用して、テーブル値パラメーターを構成する列のデータの可用性を示します。 テーブル値パラメーターの SQLPutData が呼び出されたときに*DataPtr*必要がありますは常に null と*StrLen_or_Ind*する必要があります 0 または値のいずれかに指定された配列のサイズ以下でなければテーブル値パラメーターのバッファー (、 *ColumnSize* SQLBindParameter のパラメーター)。 0 はテーブル値パラメーターの行がなくなったことを示すため、ドライバーはプロシージャの次の実パラメーターの処理に進みます。 ときに*StrLen_or_Ind*が 0 ではなく、ドライバーは処理、テーブル値パラメーターを構成する列と同じ方法で非 – テーブル値パラメーターのパラメーター バインドと: 各テーブル値パラメーター列は、実際のデータを指定できます長さ、SQL_NULL_DATA、またはそれには、その長さ/インジケーター バッファーを使用して実行時データを指定できます。 テーブル値パラメーター列の値渡しでは、文字またはバイナリ値が個別に渡されるときに通常どおり SQLPutData への呼び出しが繰り返されます。  
  
 テーブル値パラメーターのすべての列が処理されたら、ドライバーはテーブル値パラメーターに戻り、テーブル値パラメーターのデータの次の行を処理します。 したがって、実行時データのテーブル値パラメーターの場合、バインドされたパラメーターを順番にスキャンする通常の方法には従いません。 SQLPutData がで呼び出されるまでにバインドされたテーブル値パラメーターをポーリングする*StrLen_Or_IndPtr* 0、れた時点で、ドライバーがテーブル値パラメーターの列をスキップし、[次へ] の実際のストアド プロシージャのパラメーターを移動します。  SQLPutData にインジケーター値が渡されたは、1 以上、ときに、ドライバー テーブル値パラメーター列と行順番に処理があるすべてのバインドされている行および列の値になるまでです。 その後、ドライバーはテーブル値パラメーターに戻ります。 SQLParamData からテーブル値パラメーターのトークンを受け取ると、テーブル値パラメーターの SQLPutData (hstmt、NULL の場合、n) を呼び出し、間、アプリケーション設定する必要がありますテーブル値パラメーターの構成要素である列のデータとインジケーター バッファーの内容を次の行またはサーバーに渡される行数。  
  
 このシナリオのサンプル コードは、ルーチン`demo_variable_TVP_binding`で[テーブル値パラメーター &#40;ODBC&#41;](../../relational-databases/native-client-odbc-how-to/use-table-valued-parameters-odbc.md)です。  
  
## <a name="retrieving-table-valued-parameter-metadata-from-the-system-catalog"></a>システム カタログからテーブル値パラメーターのメタデータを取得  
 アプリケーションを呼び出すと SQLProcedureColumns テーブル値パラメーターのパラメーターを持つ手順については、DATA_TYPE が SQL_SS_TABLE れ、TYPE_NAME はテーブル値パラメーターのテーブル型の名前として返されます。 SQLProcedureColumns から返される結果セットに 2 つの列が追加されます: SS_TYPE_CATALOG_NAME が、テーブル値パラメーターのテーブル型が定義されているし、スキーマの名前を返します、カタログの名前を返します場所、テーブル値パラメーターのテーブル型が定義されています。 SS_TYPE_CATALOG_NAME および SS_TYPE_SCHEMA_NAME で以前のバージョンで追加されたすべてのドライバーの特定列の前に表示、ODBC 仕様に準拠して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、および ODBC 自体によって指定すべての列の後にします。  
  
 新しい列は、テーブル値パラメーター用だけでなく、CLR ユーザー定義型パラメーター用にも作成されます。 UDT パラメーターの既存のスキーマ列とカタログ列も依然として作成されますが、共通のスキーマ列とカタログ列を必要とするデータ型にもそれらの列を含めておくと、今後アプリケーション開発が簡単になります  (XML スキーマ コレクションは多少異なり、この変更には含まれていないことに注意してください)。  
  
 アプリケーションでは、SQLTables を使用して、テーブル型の名前は永続的なテーブル、システム テーブルおよびビューの場合、同じ方法を調べます。 アプリケーションでテーブル値パラメーターに関連付けられたテーブル型を識別できるように、新しいテーブル型として TABLE TYPE が導入されました。 テーブル型と通常のテーブルでは、異なる名前空間を使用します。 つまり、テーブル型と実際のテーブルに、同じ名前を使用できます。 これに対処するために、新しいステートメント属性として SQL_SOPT_SS_NAME_SCOPE が導入されました。 この属性は、かどうか SQLTables と他のカタログ関数、テーブルの名前をパラメーターとして受け取るを解釈する実際のテーブルの名前とテーブル名またはテーブル型の名前を指定します。  
  
 アプリケーションでは、SQLColumns を使用して、永続的なテーブルの場合は、SQL_SOPT_SS_NAME_SCOPE が機能する実際のテーブルではなくテーブル型を示すために最初に設定する必要がありますが、同じ方法でテーブル型の列を調べます。 SQLPrimaryKeys はもう一度 SQL_SOPT_SS_NAME_SCOPE を使用して、テーブル型でも使用できます。  
  
 このシナリオのサンプル コードは、ルーチン`demo_metadata_from_catalog_APIs`で[テーブル値パラメーター &#40;ODBC&#41;](../../relational-databases/native-client-odbc-how-to/use-table-valued-parameters-odbc.md)です。  
  
## <a name="retrieving-table-valued-parameter-metadata-for-a-prepared-statement"></a>準備されたステートメント用にテーブル値パラメーターのメタデータを取得  
 このシナリオでは、アプリケーションは、テーブル値パラメーターのメタデータを取得するのに SQLNumParameters と SQLDescribeParam を使用します。  
  
 IPD フィールド SQL_CA_SS_TYPE_NAME は、テーブル値パラメーターの型名を取得するために使用されます。 IPD フィールド SQL_CA_SS_TYPE_SCHEMA_NAME と SQL_CA_SS_TYPE_CATALOG_NAME は、それぞれスキーマとカタログを取得するために使用されます。  
  
 テーブル型の定義とテーブル値パラメーターは同じデータベースに存在する必要があります。 Sqlsetdescfield によるはテーブル値パラメーターを使用する場合、アプリケーションで SQL_CA_SS_TYPE_CATALOG_NAME を設定する場合、エラーを報告します。  
  
 SQL_CA_SS_TYPE_CATALOG_NAME および SQL_CA_SS_TYPE_SCHEMA_NAME を使用すると、CLR ユーザー定義型パラメーターに関連付けられたカタログとスキーマも取得できます。 SQL_CA_SS_TYPE_CATALOG_NAME および SQL_CA_SS_TYPE_SCHEMA_NAME は、CLR UDT 型の既存の型固有のカタログ スキーマの属性の代わりに使用します。  
  
 アプリケーションは、SQLDescribeParam は、テーブル値パラメーター列の列のメタデータを返さないため、このシナリオではテーブル値パラメーターの列のメタデータを取得するのに SQLColumns を使用します。  
  
 このユース ケースのサンプル コードは、ルーチン`demo_metadata_from_prepared_statement`で[テーブル値パラメーター &#40;ODBC&#41;](../../relational-databases/native-client-odbc-how-to/use-table-valued-parameters-odbc.md)です。  
  
## <a name="see-also"></a>参照  
 [テーブル値パラメーター &#40; ODBC &#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)  
  
  
