---
title: "ALTER WORKLOAD GROUP (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2016
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER_WORKLOAD_GROUP_TSQL
- ALTER WORKLOAD GROUP
dev_langs: TSQL
helpviewer_keywords: ALTER WORKLOAD GROUP statement
ms.assetid: 957addce-feb0-4e54-893e-5faca3cd184c
caps.latest.revision: "56"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 7bfb6ca0200095860acec2b275020012e4b96284
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="alter-workload-group-transact-sql"></a>ALTER WORKLOAD GROUP (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  既存のリソース ガバナー ワークロード グループ構成を変更し、必要に応じてそれをリソース ガバナー リソース プールにします。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [TRANSACT-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)です。  
  
## <a name="syntax"></a>構文  
  
```  
  
ALTER WORKLOAD GROUP { group_name | "default" }  
[ WITH  
    ([ IMPORTANCE = { LOW | MEDIUM | HIGH } ]  
      [ [ , ] REQUEST_MAX_MEMORY_GRANT_PERCENT = value ]  
      [ [ , ] REQUEST_MAX_CPU_TIME_SEC = value ]  
      [ [ , ] REQUEST_MEMORY_GRANT_TIMEOUT_SEC = value ]   
      [ [ , ] MAX_DOP = value ]  
      [ [ , ] GROUP_MAX_REQUESTS = value ] )  
 ]  
[ USING { pool_name | "default" } ]  
[ ; ]  
```  
  
## <a name="arguments"></a>引数  
 *group_name* |"**既定**"  
 既存のユーザー定義のワークロード グループの名前か、リソース ガバナーの既定のワークロード グループを指定します。  
  
> [!NOTE]  
>  リソース ガバナーは、"default"を作成し、ときに内部のグループ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]がインストールされています。  
  
 オプションの "default" を ALTER WORKLOAD GROUP で使用する場合は、システム予約語の DEFAULT と競合しないように引用符 ("") または角かっこ ([]) で囲む必要があります。 詳細については、「[データベース識別子](../../relational-databases/databases/database-identifiers.md)」を参照してください。  
  
> [!NOTE]  
>  定義済みのワークロード グループおよびリソース プールはすべて、"default" などの小文字の名前を使用しています。 大文字と小文字を区別する照合順序を使用するサーバーでは、これを考慮する必要があります。 SQL_Latin1_General_CP1_CI_AS など、大文字と小文字を区別しない照合順序を使用するサーバーでは、"default" と "Default" が同じものと見なされます。  
  
 IMPORTANCE = { LOW | MEDIUM | HIGH }  
 ワークロード グループでの要求の相対的な重要度を指定します。 重要度では、次のいずれかです。  
  
-   LOW  
  
-   MEDIUM (既定)  
  
-   HIGH  
  
> [!NOTE]  
>  内部的には、各重要度の設定は計算に使用される数値として格納されます。  
  
 IMPORTANCE は、リソース プールに対してローカルです。同じリソース プール内の異なる重要度のワークロード グループは互いに影響しますが、別のリソース プールのワークロード グループには影響しません。  
  
 REQUEST_MAX_MEMORY_GRANT_PERCENT =*値*  
 1 つの要求にプールから割り当てられる最大メモリ量を指定します。 このパーセンテージは、MAX_MEMORY_PERCENT で指定したリソース プールのサイズが基準になります。  
  
> [!NOTE]  
>  指定した量だけがクエリ実行許可メモリに割り当てられます。  
  
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
  
 REQUEST_MAX_CPU_TIME_SEC =*値*  
 要求が使用できる最大 CPU 時間を秒単位で指定します。 *値*0 または正の整数にする必要があります。 既定の設定*値*0 の場合は、無制限を示します。  
  
> [!NOTE]  
>  リソース ガバナーでは、最大時間を超過しても、要求は継続されます。 ただし、イベントが生成されます。 詳細については、次を参照してください。 [CPU しきい値 Exceeded イベント クラス](../../relational-databases/event-classes/cpu-threshold-exceeded-event-class.md)です。  
  
 REQUEST_MEMORY_GRANT_TIMEOUT_SEC =*値*  
 メモリ許可 (作業バッファー メモリ) が使用可能になるのをクエリが待機できる最大時間を秒単位で指定します。  
  
> [!NOTE]  
>  メモリ許可のタイムアウトに達しても、常にクエリが失敗するとは限りません。 クエリが失敗するのは、同時実行クエリ数が多すぎる場合だけです。 それ以外の場合、クエリは最小限のメモリ許可しか取得できないので、クエリのパフォーマンスが低下します。  
  
 *値*正の整数を指定する必要があります。 既定の設定*値*0 では、クエリ コストに基づく内部の計算を使用して、最大時間を決定します。  
  
 MAX_DOP =*値*  
 並列処理次数 (DOP) 並列要求の最大限度を指定します。 *値*から 255 まで、0 または 1、正の整数でなければなりません。 ときに*値*が 0 の場合、サーバーは、max degree of parallelism を選択します。 これは既定値であり、推奨される設定。  
  
> [!NOTE]  
>  実際の値、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] MAX_DOP に可能性があります指定された値よりも小さいを設定します。 最終的な値は式の最小値によって決まります (255, *Cpu の数)*です。  
  
> [!CAUTION]  
>  MAX_DOP を変更すると、サーバーのパフォーマンスが低下することがあります。 MAX_DOP を変更する必要がある場合には、1 つの NUMA ノードで示されているハードウェア スケジューラの最大数以下の値に設定することをお勧めします。 MAX_DOP に 8 よりも大きな値を設定することはお勧めできません。  
  
 MAX_DOP は次のように処理されます。  
  
-   ワークロード グループの MAX_DOP を超えない限り、クエリ ヒントとしての MAX_DOP が受け入れられます。  
  
-   クエリ ヒントとしての MAX_DOP は、sp_configure の 'max degree of parallelism' より常に優先されます。  
  
-   ワークロード グループの MAX_DOP は、sp_configure の 'max degree of parallelism' より優先されます。  
  
-   コンパイル時にクエリが直列 (MAX_DOP = 1 ) としてマークされている場合は、ワークロード グループまたは sp_configure の設定にかかわらず、実行時に並列に変更することはできません。  
  
 DOP は、構成した後、許可メモリの不足時にのみ低くすることができます。 ワークロード グループの再構成は、許可メモリ キューで待機している間は認識されません。  
  
 GROUP_MAX_REQUESTS =*値*  
 ワークロード グループで実行を許可する同時要求の最大数を指定します。 *値*0 または正の整数にする必要があります。 既定の設定*値*は 0 で、無制限の要求を許可します。 同時要求の最大数に達した場合、そのグループのユーザーはログインできますが、同時要求数が指定した値を下回るまで待機状態になります。  
  
 使用して { *pool_name* |"**既定**"}  
 識別されるユーザー定義のリソース プールとワークロード グループを関連付ける*pool_name*、リソース プールのワークロード グループ有効ではします。 場合*pool_name*が指定されていないか、ワークロード グループが、定義済みのリソース ガバナーの既定のプールを使用して引数を使用しない場合。  
  
 オプションの "default" を ALTER WORKLOAD GROUP で使用する場合は、システム予約語の DEFAULT と競合しないように引用符 ("") または角かっこ ([]) で囲む必要があります。 詳細については、「[データベース識別子](../../relational-databases/databases/database-identifiers.md)」を参照してください。  
  
> [!NOTE]  
>  オプションの "default" は、大文字と小文字が区別されます。  
  
## <a name="remarks"></a>解説  
 ALTER WORKLOAD GROUP は、既定のグループに対して使用できます。  
  
 ワークロード グループの構成の変更は、ALTER RESOURCE GOVERNOR RECONFIGURE を実行しないと有効になりません。 設定に影響するプランを変更するときに、新しい設定のみを有効以前にキャッシュされたプランで DBCC FREEPROCCACHE を実行した後 (*pool_name*) ここで、 *pool_name*リソースの名前を指定しますガバナー リソース プールのワークロード グループに関連付けられています。  
  
-   場合 1 を MAX_DOP を変更する場合は、DBCC FREEPROCCACHE を実行するは必要ありません並列プランが直列モードで実行できるため、します。 ただし、ある可能性がありますいないほど効率的で、直列プランとしてコンパイルされるプラン。  
  
-   場合は 0 を 1 から MAX_DOP を変更するか、DBCC FREEPROCCACHE を実行する、1 より大きい値は必要ありません。 ただし、直列プランは、並列で実行することはできません、それぞれのキャッシュをクリアすることが新しいプランを可能性があるため、並列処理を使用してをコンパイルします。  
  
> [!CAUTION]  
>  1 つ以上のワークロード グループに関連付けられているリソース プールからキャッシュされたプランを削除するに影響するすべてのワークロード グループによって識別されるユーザー定義のリソース プールと*pool_name*です。  
  
 DDL ステートメントを実行する場合、リソース ガバナーの状態について詳しく理解しておくことをお勧めします。 詳細については、次を参照してください。[リソース ガバナー](../../relational-databases/resource-governor/resource-governor.md)です。  
  
 REQUEST_MEMORY_GRANT_PERCENT: [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] のインデックス作成では、パフォーマンスを向上させるため、最初に許可されたメモリ量を超えるワークスペース メモリの使用が許可されます。 この特別な処理は、今後のバージョンのリソース ガバナーでもサポートされますが、最初のメモリ許可も追加のメモリ許可もリソース プール設定とワークロード グループ設定によって制限されます。  
  
 **パーティション テーブルでインデックスの作成**  
  
 非固定パーティション分割されたテーブルでインデックスの作成によって消費されるメモリは、含まれるパーティションの数に比例します。  必要なメモリの合計が、リソース ガバナーのワークロード グループの設定によって課せられているクエリごとの制限 (REQUEST_MAX_MEMORY_GRANT_PERCENT) を超えると、インデックス作成の実行に失敗します。 "default" ワークロード グループでは、[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] との互換性のために、クエリごとの制限を超えてもクエリの開始に必要な最低限のメモリを使用できるようになっているので、そのようなクエリを実行するのに十分な量のメモリが "default" リソース プールに対して構成されていれば、同じインデックス作成を "default" ワークロード グループで実行できる可能性があります。  
  
## <a name="permissions"></a>Permissions  
 CONTROL SERVER 権限が必要です。  
  
## <a name="examples"></a>使用例  
 次の例は、既定のグループからの要求の重要度を変更する方法を示します`MEDIUM`に`LOW`です。  
  
```  
ALTER WORKLOAD GROUP "default"  
WITH (IMPORTANCE = LOW);  
GO  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
```  
  
 次の例は、ワークロード グループを現在のプールから既定のプールに移動する方法を示しています。  
  
```  
ALTER WORKLOAD GROUP adHoc  
USING [default];  
GO  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [[リソース ガバナー]](../../relational-databases/resource-governor/resource-governor.md)   
 [CREATE WORKLOAD GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/create-workload-group-transact-sql.md)   
 [DROP WORKLOAD GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/drop-workload-group-transact-sql.md)   
 [CREATE RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/create-resource-pool-transact-sql.md)   
 [ALTER RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/alter-resource-pool-transact-sql.md)   
 [DROP RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/drop-resource-pool-transact-sql.md)   
 [ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;](../../t-sql/statements/alter-resource-governor-transact-sql.md)  
  
  
