---
title: 準備実行 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- deferred statement preparation
- prepared execution [ODBC]
- SQLPrepare function
- ODBC applications, statements
- SQLExecute function
- statements [ODBC], prepared execution
ms.assetid: f3a9d32b-6cd7-4f0c-b38d-c8ccc4ee40c3
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 8265ed80028d5d8ac9696853a29474552f401f3e
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81297922"
---
# <a name="prepared-execution"></a>準備実行
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  ODBC API では、準備実行とは、[!INCLUDE[tsql](../../../includes/tsql-md.md)] ステートメントを繰り返し実行する際に関連して生じる解析やコンパイルのオーバーヘッドを削減する方法と定義されています。 アプリケーションでは SQL ステートメントを保持する文字列を構築してから、そのステートメントを 2 段階に分けて実行します。 [SQLPrepare 関数](https://go.microsoft.com/fwlink/?LinkId=59360)を 1 回呼び出して、ステートメントを解析し、コンパイルして[!INCLUDE[ssDE](../../../includes/ssde-md.md)]実行プランにコンパイルします。 次に、準備された実行プランの実行ごとに**SQLExecute**を呼び出します。 この方法では、各実行にかかる解析とコンパイルのオーバーヘッドが抑制されます。 準備実行は、通常、同一のパラメーター化された SQL ステートメントを繰り返し実行するアプリケーションで使用されます。  
  
 ほとんどのデータベースでは、直接実行されるステートメントが実行のたびにコンパイルされるのに対し、準備実行されるステートメントは 1 回だけコンパイルされるので、準備実行は主に 4、5 回以上実行されるステートメントの場合は直接実行よりも高速になります。 準備実行では、SQL ステートメントが実行されるたびに、ドライバーはステートメント全体ではなく、実行プランの識別子とパラメーター値だけをデータ ソースに送信できるので、ネットワーク トラフィックも削減できます。  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]**SQLExecDirect**からの実行プランを検出および再利用するためのアルゴリズムを改善することにより、直接実行と準備された実行のパフォーマンスの差を軽減します。 そのため、直接実行されるステートメントでも、準備実行のパフォーマンス上の利点の一部を利用できるようになります。 詳細については、「[直接実行](../../../relational-databases/native-client-odbc-queries/executing-statements/direct-execution.md)」を参照してください。  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] では、準備実行がネイティブにサポートされます。 実行プランは**SQLPrepare**上で構築され、後で**SQLExecute**が呼び出されたときに実行されます。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] **SQLPrepare**で一時ストアド プロシージャを構築する必要はないため、 **tempdb**のシステム テーブルに余分なオーバーヘッドはありません。  
  
 パフォーマンス上の理由から、ステートメントの準備は **、SQLExecute**が呼び出されるか、またはメタ プロパティ操作 (ODBC の[SQLDescribeCol](../../../relational-databases/native-client-odbc-api/sqldescribecol.md)や[SQLDescribeParam](../../../relational-databases/native-client-odbc-api/sqldescribeparam.md)など) が実行されるまで延期されます。 これは既定の動作です。 準備されているステートメントのエラーは、ステートメントまたはメタプロパティ操作が実行されるまでわかりません。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC ドライバー固有のステートメント属性の SQL_SOPT_SS_DEFER_PREPARE を SQL_DP_OFF に設定することで、この既定の動作を無効にできます。  
  
 遅延準備の場合は **、SQLExecute を**呼び出す前に SQLDescribeCol または**SQLDescribe** **パラム**を呼び出すと、サーバーへの余分なラウンドトリップが生成されます。 **SQLDescribeCol**では、ドライバーは、クエリから WHERE 句を削除し、クエリによって返される最初の結果セットの列の説明を取得する SET FMTONLY ON を使用してサーバーに送信します。 **SQLDescribeParam**では、ドライバーは、クエリ内の任意のパラメーター マーカーによって参照される式または列の説明を取得するサーバーを呼び出します。 この方法には、サブクエリのパラメーターを解決することができないなど、いくつか制限事項もあります。  
  
 ネイティブ クライアント ODBC ドライバ[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]で**SQLPrepare を**過剰に使用すると、特に以前のバージョンの SQL Server に接続している場合にパフォーマンスが低下します。 準備実行は、1 回しか実行されないステートメントには使用しないでください。 準備実行では、クライアントからサーバーへのネットワーク上のやり取りを余分に実行する必要があるため、ステートメントを 1 回しか実行しない場合は直接実行よりも時間がかかります。 以前のバージョンの [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] では、準備実行で一時ストアド プロシージャの生成も行います。  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] では、準備されたステートメントを使用して一時オブジェクトを作成することはできません。  
  
 一部の初期の ODBC アプリケーションでは **、SQLBindParameter が**使用されるたびに[SQLPrepare を](../../../relational-databases/native-client-odbc-api/sqlbindparameter.md)使用していました。 **SQL バインドパラメーター**は **、SQLPrepare**の使用を必要と**しません。** たとえば **、SQLExecDirect**と共に**SQLExecParameter**を使用して、1 回だけ実行されるストアド プロシージャから戻りコードまたは出力パラメータを取得します。 同じステートメント**SQLPrepare**が複数回実行されない限り **、SQLPrepare**を使用しないでください。  
  
## <a name="see-also"></a>参照  
 [ODBC&#41;&#40;ステートメントの実行](../../../relational-databases/native-client-odbc-queries/executing-statements/executing-statements-odbc.md)  
  
  
