---
title: "ワークロード グループ (TRANSACT-SQL) を作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/04/2018
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- WORKLOAD GROUP
- WORKLOAD_GROUP_TSQL
- CREATE WORKLOAD GROUP
- CREATE_WORKLOAD_GROUP_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- CREATE WORKLOAD GROUP statement
ms.assetid: d949e540-9517-4bca-8117-ad8358848baa
caps.latest.revision: 
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: cec1360259d78679fab31a45a074d5fbbf3779b5
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="create-workload-group-transact-sql"></a>CREATE WORKLOAD GROUP (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  リソース ガバナー ワークロード グループを作成し、そのワークロード グループをリソース ガバナー リソース プールに関連付けます。 リソース ガバナーでは使用できませんのすべてのエディション[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の各エディションでサポートされる機能の一覧については、「 [SQL Server 2016 の各エディションがサポートする機能](~/sql-server/editions-and-supported-features-for-sql-server-2016.md)」を参照してください。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [TRANSACT-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)です。  
  
## <a name="syntax"></a>構文  
  
```  
CREATE WORKLOAD GROUP group_name  
[ WITH  
    ( [ IMPORTANCE = { LOW | MEDIUM | HIGH } ]  
      [ [ , ] REQUEST_MAX_MEMORY_GRANT_PERCENT = value ]  
      [ [ , ] REQUEST_MAX_CPU_TIME_SEC = value ]  
      [ [ , ] REQUEST_MEMORY_GRANT_TIMEOUT_SEC = value ]   
      [ [ , ] MAX_DOP = value ]  
      [ [ , ] GROUP_MAX_REQUESTS = value ] )  
 ]  
[ USING {   
    [ pool_name | "default" ]    
    [ [ , ] EXTERNAL external_pool_name | "default" ] ]   
    } ]  
[ ; ]  
```  
  
## <a name="arguments"></a>引数  
 *group_name*  
 ワークロード グループのユーザー定義の名前を指定します。 *group_name*は、英数字、最大 128 文字を使用できますがのインスタンス内で一意である必要があります[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、規則に従う必要がありますと[識別子](../../relational-databases/databases/database-identifiers.md)です。  
  
 IMPORTANCE = { LOW | **MEDIUM** | HIGH }  
 ワークロード グループでの要求の相対的な重要度を指定します。 重要度は次のいずれかで、MEDIUM が既定値です。  
  
-   LOW  
-   MEDIUM (既定)    
-   HIGH  
  
> [!NOTE]  
> 内部的には、各重要度の設定は計算に使用される数値として格納されます。  
  
 IMPORTANCE は、リソース プールに対してローカルです。同じリソース プール内の異なる重要度のワークロード グループは互いに影響しますが、別のリソース プールのワークロード グループには影響しません。  
  
 REQUEST_MAX_MEMORY_GRANT_PERCENT =*value*  
 1 つの要求にプールから割り当てられる最大メモリ量を指定します。 このパーセンテージは、MAX_MEMORY_PERCENT で指定したリソース プールのサイズが基準になります。  
  
> [!NOTE]  
> 指定した量だけがクエリ実行許可メモリに割り当てられます。  
  
 *値*0 または正の整数にする必要があります。 許容範囲*値*は 0 ~ 100 です。 既定の設定*値*25 です。  
  
 次のことを考慮してください。  
  
-   設定*値*を 0 にユーザー定義のワークロード グループで SORT と HASH JOIN の操作を含むクエリが実行できなくなります。  
  
-   設定はお勧めしません*値*70 を超えているため、サーバーが他の同時実行クエリが実行されている場合に、十分な空きメモリを確保することがない可能性があります。 空きメモリを十分に確保できないと、クエリの時間切れエラー 8645 が発生します。  
  
> [!NOTE]  
>  クエリのメモリ要求がこのパラメーターによって指定されている制限を超えると、サーバーは次のように対応します。  
>   
>  ユーザー定義のワークロード グループでは、メモリ要求が制限より低くなるか、並列処理の次数が 1 になるまで、サーバーはクエリの並列処理の次数を下げます。 それでもクエリのメモリ要求が制限を超える場合は、エラー 8657 が発生します。  
>   
>  内部および既定のワークロード グループでは、そのクエリに必要なメモリの確保がサーバーによって許可されます。  
>   
>  サーバーに十分な物理メモリがない場合は、どちらの場合も時間切れエラー 8645 が発生する可能性があります。  
  
 REQUEST_MAX_CPU_TIME_SEC =*value*  
 要求が使用できる最大 CPU 時間を秒単位で指定します。 *値*0 または正の整数にする必要があります。 既定の設定*値*0 の場合は、無制限を示します。  
  
> [!NOTE]  
> 既定では、リソース ガバナーはの最大時間を超えたかどうかの続行を要求を妨げません。 ただし、イベントが生成されます。 詳細については、次を参照してください。 [CPU しきい値 Exceeded イベント クラス](../../relational-databases/event-classes/cpu-threshold-exceeded-event-class.md)です。  

> [!IMPORTANT]
> 以降で[!INCLUDE[ssSQL17](../../includes/sssql17-md.md)]CU3 を使用して、[トレース フラグ 2422](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md)、リソース ガバナーは、最大時間を超えたときに、要求は中止されます。 
  
 REQUEST_MEMORY_GRANT_TIMEOUT_SEC =*value*  
 クエリでは、使用可能になるメモリ許可 (作業バッファー メモリ) が待機できる秒単位で最大の時間を指定します。  
  
> [!NOTE]  
>  メモリ許可のタイムアウトに達しても、常にクエリが失敗するとは限りません。 クエリが失敗するのは、同時実行クエリ数が多すぎる場合だけです。 それ以外の場合、クエリは最小限のメモリ許可しか取得できないので、クエリのパフォーマンスが低下します。  
  
 *値*0 または正の整数にする必要があります。 既定の設定*値*0 では、クエリ コストに基づく内部の計算を使用して、最大時間を決定します。  
  
 MAX_DOP =*value*  
 並列処理次数 (DOP) 並列要求の最大限度を指定します。 *値*0 または正の整数にする必要があります。 許容範囲*値*は 0 ~ 64 です。 既定の設定*値*0 の場合は、グローバル設定を使用します。 MAX_DOP は次のように処理されます。  
  
-   ワークロード グループの MAX_DOP を超えない限り、クエリ ヒントとしての MAX_DOP が有効です。 MAXDOP クエリ ヒントの値がリソース ガバナーを使用して構成されている値を超える場合は、データベース エンジンがリソース ガバナーの MAXDOP 値を使用します。  
  
-   クエリ ヒントとしての MAX_DOP は、sp_configure の 'max degree of parallelism' より常に優先されます。  
  
-   ワークロード グループの MAX_DOP は、sp_configure の 'max degree of parallelism' より優先されます。  
  
-   コンパイル時にクエリが直列としてマークされている場合は、ワークロード グループまたは sp_configure の設定にかかわらず、実行時に並列に変更することはできません。  
  
-   DOP は、構成した後、許可メモリの不足時にのみ低くすることができます。 ワークロード グループの再構成は、許可メモリ キューで待機している間は認識されません。  
  
 GROUP_MAX_REQUESTS =*value*  
 ワークロード グループで実行を許可する同時要求の最大数を指定します。 *値*0 または正の整数にする必要があります。 既定の設定*値*は 0 で、無制限の要求を許可します。 同時要求の最大数に達した場合、そのグループのユーザーはログインできますが、同時要求数が指定した値を下回るまで待機状態になります。  
  
 USING { *pool_name* | **"default"** }  
 識別されるユーザー定義のリソース プールとワークロード グループを関連付ける*pool_name*です。 実質的には、これによってワークロード グループがグループ リソースに配置されます。 場合*pool_name*が指定されていないか、ワークロード グループが、定義済みのリソース ガバナーの既定のプールを使用して引数を使用しない場合。  
  
 予約語の "default" を USING で使用する場合は、引用符 ("") または角かっこ ([]) で囲む必要があります。  
  
> [!NOTE]  
>  定義済みのワークロード グループおよびリソース プールではすべて、"default" などの小文字の名前が使用されています。 大文字と小文字を区別する照合順序を使用するサーバーでは、これを考慮する必要があります。 SQL_Latin1_General_CP1_CI_AS など、大文字と小文字を区別しない照合順序を使用するサーバーでは、"default" と "Default" が同じものと見なされます。  
  
 EXTERNAL external_pool_name | “default“  
 **適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]まで)。  
  
 ワークロード グループには、外部リソース プールを指定できます。 ワークロード グループを定義し、2 つのプールに関連付けることができます。  
  
-   リソース プールを[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ワークロードおよびクエリ  
  
-   外部プロセス用の外部リソース プールです。 詳細については、次を参照してください。 [sp_execute_external_script &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md).  
  
## <a name="remarks"></a>解説  
 REQUEST_MEMORY_GRANT_PERCENT: インデックス作成では、パフォーマンスを向上させるため、最初に許可されたメモリ量を超えるワークスペース メモリの使用が許可されます。 この特別な処理には、リソース ガバナーではサポートされて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]です。 ただし、最初のメモリ許可も追加のメモリ許可も、リソース プール設定およびワークロード グループ設定によって制限されます。  
  
 **パーティション テーブルでインデックスの作成**  
  
 非固定パーティション分割されたテーブルでインデックスの作成によって消費されるメモリは、含まれるパーティションの数に比例します。 必要なメモリの合計が、リソース ガバナーのワークロード グループの設定によって課せられているクエリごとの制限 (REQUEST_MAX_MEMORY_GRANT_PERCENT) を超えると、インデックス作成の実行に失敗します。 "default" ワークロード グループでは、クエリごとの制限を超えてもクエリの開始に必要な最低限のメモリを使用できるようになっているので、そのようなクエリを実行するのに十分な量のメモリが "default" リソース プールに対して構成されていれば、同じインデックス作成を "default" ワークロード グループで実行できる可能性があります。  
  
## <a name="permissions"></a>権限  
 CONTROL SERVER 権限が必要です。  
  
## <a name="examples"></a>使用例  
 次の例は、という名前のワークロード グループを作成する方法を示しています。`newReports`です。 このワークロード グループはリソース ガバナーの既定の設定を使用し、リソース ガバナーの既定のプールに配置されます。 この例で指定、`default`プールが、これは必要ありません。  
  
```  
CREATE WORKLOAD GROUP newReports  
    USING "default" ;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [ALTER WORKLOAD GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/alter-workload-group-transact-sql.md)   
 [DROP WORKLOAD GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/drop-workload-group-transact-sql.md)   
 [CREATE RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/create-resource-pool-transact-sql.md)   
 [ALTER RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/alter-resource-pool-transact-sql.md)   
 [DROP RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/drop-resource-pool-transact-sql.md)   
 [ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;](../../t-sql/statements/alter-resource-governor-transact-sql.md)  
  
  

