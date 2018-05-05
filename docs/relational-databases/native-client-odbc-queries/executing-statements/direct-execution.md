---
title: 実行を指示 |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: native-client-odbc-queries
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- ODBC applications, statements
- direct execution [ODBC]
- SQLExecDirect function
- statements [ODBC], direct execution
ms.assetid: fa36e1af-ed98-4abc-97c1-c4cc5d227b29
caps.latest.revision: 38
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 11dc0781c0d2bf8f0f69e6b848eee4f60c0a56ce
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="direct-execution"></a>直接実行
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  直接実行はステートメントを実行する最も基本的な方法です。 文字の文字列を格納するアプリケーションをビルド、[!INCLUDE[tsql](../../../includes/tsql-md.md)]ステートメントを使用する実行のために送信し、 **SQLExecDirect**関数。 ステートメントがサーバーに到達すると、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] がステートメントを実行プランにコンパイルしてから、すぐにその実行プランを実行します。  
  
 直接実行は、通常、実行時にステートメントを構築して実行するアプリケーションで使用され、1 回だけステートメントを実行する場合には最も効率的な方法です。 多くのデータベースでの直接実行の欠点は、SQL ステートメントを実行するたびに解析とコンパイルが必要なことで、ステートメントを複数回実行する場合はオーバーヘッドが増加します。  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] では、マルチユーザー環境で通常実行されるステートメントに関して、直接実行のパフォーマンスが大幅に向上します。また、通常、SQL ステートメントの実行にパラメーター マーカーを指定して SQLExecDirect を使用すると、準備実行に近い効率を得ることができます。  
  
 インスタンスに接続しているときに[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーを使用して[sp_executesql](../../../relational-databases/system-stored-procedures/sp-executesql-transact-sql.md) SQL ステートメントまたはで指定されたバッチを送信する**SQLExecDirect**です。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 場合、SQL ステートメントをすばやく判断するロジックを備えてまたはバッチの実行と**sp_executesql**ステートメントまたはメモリに既に存在する実行プランを生成したバッチと一致します。 一致する場合、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] は新しいプランをコンパイルしないで、単に既存のプランを再利用します。 一般的に実行される SQL ステートメントを実行することを意味**SQLExecDirect**は、ユーザー数の多いシステムでのみ使用可能になったの以前のバージョンのストアドプロシージャを再利用のプランの利点の多くを利用[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 実行プランを再利用することで得られる利点は、複数のユーザーが同じ SQL ステートメントやバッチを実行しているときにのみ効果があります。 異なるクライアントが実行する SQL ステートメントを可能な限り統一の取れたステートメントにして、実行プランの再利用を可能にするために、次のコーディング規則に従ってください。  
  
-   SQL ステートメントには定数データを含めません。代わりにプログラム変数にバインドされるパラメーター マーカーを使用します。 詳細については、次を参照してください。[ステートメント パラメーターの使用](../../../relational-databases/native-client-odbc-queries/using-statement-parameters.md)です。  
  
-   完全修飾オブジェクト名を使用します。 実行プランは、オブジェクト名が修飾されていないと再利用されません。  
  
-   アプリケーション接続では、できる限り、接続オプションとステートメント オプションの共通のセットを使用します。 あるオプションのセット (ANSI_NULLS など) を使用する接続に対して生成される実行プランは、別のオプションのセットを使用する接続には再利用されません。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーと [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは、どちらもこれらのオプションに同じ既定値を使用します。  
  
 すべてのステートメントが実行される場合**SQLExecDirect**はこれらの規則を使用してコード化された[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]営業案件が発生したときに、実行プランを再利用することができます。  
  
## <a name="see-also"></a>参照  
 [実行中のステートメント (&) #40; ODBC & #41;](../../../relational-databases/native-client-odbc-queries/executing-statements/executing-statements-odbc.md)  
  
  
