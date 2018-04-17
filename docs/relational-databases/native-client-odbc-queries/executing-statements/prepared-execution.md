---
title: 準備実行 |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: native-client-odbc-queries
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- deferred statement preparation
- prepared execution [ODBC]
- SQLPrepare function
- ODBC applications, statements
- SQLExecute function
- statements [ODBC], prepared execution
ms.assetid: f3a9d32b-6cd7-4f0c-b38d-c8ccc4ee40c3
caps.latest.revision: 35
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: f8650a69f3fef94e0b0344bc27a36ced79a3a924
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="prepared-execution"></a>準備実行
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  ODBC API では、準備実行とは、[!INCLUDE[tsql](../../../includes/tsql-md.md)] ステートメントを繰り返し実行する際に関連して生じる解析やコンパイルのオーバーヘッドを削減する方法と定義されています。 アプリケーションでは SQL ステートメントを保持する文字列を構築してから、そのステートメントを 2 段階に分けて実行します。 呼び出す[SQLPrepare 関数](http://go.microsoft.com/fwlink/?LinkId=59360)ステートメントが解析され、実行プランにコンパイルを 1 回、[!INCLUDE[ssDE](../../../includes/ssde-md.md)]です。 呼び出して**SQLExecute**準備された実行プランの実行のたびにします。 この方法では、各実行にかかる解析とコンパイルのオーバーヘッドが抑制されます。 準備実行は、通常、同一のパラメーター化された SQL ステートメントを繰り返し実行するアプリケーションで使用されます。  
  
 ほとんどのデータベースでは、直接実行されるステートメントが実行のたびにコンパイルされるのに対し、準備実行されるステートメントは 1 回だけコンパイルされるので、準備実行は主に 4、5 回以上実行されるステートメントの場合は直接実行よりも高速になります。 準備実行では、SQL ステートメントが実行されるたびに、ドライバーはステートメント全体ではなく、実行プランの識別子とパラメーター値だけをデータ ソースに送信できるので、ネットワーク トラフィックも削減できます。  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]検出の実行プランを再利用するためのアルゴリズムが強化されたを通して直接的および準備された実行のパフォーマンスの差を減少**SQLExecDirect**です。 そのため、直接実行されるステートメントでも、準備実行のパフォーマンス上の利点の一部を利用できるようになります。 詳細については、次を参照してください。[直接実行](../../../relational-databases/native-client-odbc-queries/executing-statements/direct-execution.md)です。  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] では、準備実行がネイティブにサポートされます。 実行プランが上に構築された**SQLPrepare**し、後で実行すると実行に**SQLExecute**と呼びます。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]一時ストアド プロシージャを構築する必要はありません**SQLPrepare**、内のシステム テーブルに余分なオーバーヘッドがない**tempdb**です。  
  
 まで、ステートメントの準備は遅延パフォーマンス上の理由から、 **SQLExecute**が呼び出されたか、メタプロパティ操作 (など[SQLDescribeCol](../../../relational-databases/native-client-odbc-api/sqldescribecol.md)または[SQLDescribeParam](../../../relational-databases/native-client-odbc-api/sqldescribeparam.md) ODBC で) が使用されます。 これは既定の動作です。 準備されているステートメントのエラーは、ステートメントまたはメタプロパティ操作が実行されるまでわかりません。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC ドライバー固有のステートメント属性の SQL_SOPT_SS_DEFER_PREPARE を SQL_DP_OFF に設定することで、この既定の動作を無効にできます。  
  
 場合に遅延を準備する、いずれかを呼び出す**SQLDescribeCol**または**SQLDescribeParam**呼び出す前に**SQLExecute**サーバーに余分なラウンド トリップが生成されます。 **SQLDescribeCol**ドライバーはクエリから WHERE 句を削除し、クエリによって返される最初の結果セット内の列の説明を取得する SET FMTONLY ON を使用してサーバーに送信します。 **SQLDescribeParam**ドライバーは、式またはクエリ内のすべてのパラメーター マーカーによって参照される列の説明を取得するサーバーを呼び出します。 この方法には、サブクエリのパラメーターを解決することができないなど、いくつか制限事項もあります。  
  
 使用、余分な**SQLPrepare**で、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]旧バージョンの SQL Server に接続されている場合は特に Native Client ODBC ドライバーによりパフォーマンスが低下します。 準備実行は、1 回しか実行されないステートメントには使用しないでください。 準備実行では、クライアントからサーバーへのネットワーク上のやり取りを余分に実行する必要があるため、ステートメントを 1 回しか実行しない場合は直接実行よりも時間がかかります。 以前のバージョンの [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] では、準備実行で一時ストアド プロシージャの生成も行います。  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] では、準備されたステートメントを使用して一時オブジェクトを作成することはできません。  
  
 使用する以前の ODBC アプリケーション**SQLPrepare**いつでも[SQLBindParameter](../../../relational-databases/native-client-odbc-api/sqlbindparameter.md)が使用されました。 **SQLBindParameter**の使用は不要**SQLPrepare**で使用できます**SQLExecDirect**です。 たとえば、使用して**SQLExecDirect**で**SQLBindParameter**リターン コードを取得または実行された 1 回のみであるストアド プロシージャからパラメーターを出力します。 使用しないでください**SQLPrepare**で**SQLBindParameter**同じステートメントは複数回実行される場合を除き、します。  
  
## <a name="see-also"></a>参照  
 [実行中のステートメント (&) #40; ODBC & #41;](../../../relational-databases/native-client-odbc-queries/executing-statements/executing-statements-odbc.md)  
  
  
