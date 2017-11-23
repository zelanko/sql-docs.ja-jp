---
title: "リソース プールを変更 (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 05/01/2017
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
- ALTER_RESOURCE_POOL_TSQL
- ALTER RESOURCE POOL
dev_langs: TSQL
helpviewer_keywords: ALTER RESOURCE POOL
ms.assetid: 9c1c4cfb-0e3b-4f01-bf57-3fce94c7d1d4
caps.latest.revision: "47"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 357dab163aca094928f5c417c605dcb699c922b1
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="alter-resource-pool-transact-sql"></a>ALTER RESOURCE POOL (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  既存のリソース ガバナー リソース プール構成を変更[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [TRANSACT-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)です。  
  
## <a name="syntax"></a>構文  
  
```  
ALTER RESOURCE POOL { pool_name | "default" }  
[WITH  
    ( [ MIN_CPU_PERCENT = value ]  
    [ [ , ] MAX_CPU_PERCENT = value ]   
    [ [ , ] CAP_CPU_PERCENT = value ]   
    [ [ , ] AFFINITY {
                        SCHEDULER = AUTO 
                      | ( <scheduler_range_spec> ) 
                      | NUMANODE = ( <NUMA_node_range_spec> )
                      }]   
    [ [ , ] MIN_MEMORY_PERCENT = value ]  
    [ [ , ] MAX_MEMORY_PERCENT = value ]   
    [ [ , ] MIN_IOPS_PER_VOLUME = value ]  
    [ [ , ] MAX_IOPS_PER_VOLUME = value ]  
)]   
[;]  
  
<scheduler_range_spec> ::=  
{SCHED_ID | SCHED_ID TO SCHED_ID}[,…n]  
  
<NUMA_node_range_spec> ::=  
{NUMA_node_ID | NUMA_node_ID TO NUMA_node_ID}[,…n]  
```  
  
## <a name="arguments"></a>引数  
 { *pool_name* | **"default"** }  
 既存のユーザー定義のリソース プール、または [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] をインストールする際に作成される既定のリソース プールの名前です。  
  
 "default" を ALTER RESOURCE POOL で使用する場合は、システム予約語の DEFAULT と競合しないように引用符 ("") または角かっこ ([]) で囲む必要があります。 詳細については、「[データベース識別子](../../relational-databases/databases/database-identifiers.md)」を参照してください。  
  
> [!NOTE]  
>  定義済みのワークロード グループおよびリソース プールはすべて、"default" などの小文字の名前を使用しています。 大文字と小文字を区別する照合順序を使用するサーバーでは、これを考慮する必要があります。 SQL_Latin1_General_CP1_CI_AS など、大文字と小文字を区別しない照合順序を使用するサーバーでは、"default" と "Default" が同じものと見なされます。  
  
 MIN_CPU_PERCENT =*値*  
 CPU の競合がある場合に、リソース プールのすべての要求に保証される平均 CPU 帯域幅を指定します。 *値*整数で、既定の設定は 0 です。 許容範囲*値*は 0 ~ 100 です。  
  
 MAX_CPU_PERCENT =*値*  
 CPU の競合がある場合に、このリソース プールのすべての要求に割り当てられる最大平均 CPU 帯域幅を指定します。 *値*で、既定の設定 100 の整数です。 許容範囲*値*は 1 ~ 100 です。  
  
 CAP_CPU_PERCENT =*値*  
 **適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 リソース プールでは、要求のターゲットの最大 CPU 容量を指定します。 *値*で、既定の設定 100 の整数です。 許容範囲*値*は 1 ~ 100 です。  
  
> [!NOTE]  
>  統計の性質により、CPU の管理、急増の CAP_CPU_PERCENT で指定された値を超える場合があります。  
  
 AFFINITY {SCHEDULER = AUTO | (Scheduler_range_spec) | NUMANODE = (NUMA_node_range_spec)}  
 **適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 リソース プールを特定のスケジューラにアタッチします。 既定値は AUTO です。  
  
 AFFINITY SCHEDULER (Scheduler_range_spec) マップをリソース プールを =、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]指定した Id によって識別されます。 これらの Id の値にマップがの scheduler_id column 内[sys.dm_os_schedulers &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-os-schedulers-transact-sql.md).  
  
 AFFINITY NAMANODE = (NUMA_node_range_spec) を使用すると、リソース プールは、指定した NUMA ノードまたはノードの範囲に対応する物理 CPU にマップされた [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のスケジューラに関連付けられます。 次の TRANSACT-SQL クエリを使用するを物理 NUMA 構成の間のマッピングを検出し、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]スケジューラ Id。  
  
```  
SELECT osn.memory_node_id AS [numa_node_id], sc.cpu_id, sc.scheduler_id  
FROM sys.dm_os_nodes AS osn  
INNER JOIN sys.dm_os_schedulers AS sc 
   ON osn.node_id = sc.parent_node_id 
      AND sc.scheduler_id < 1048576;  
```  
  
 MIN_MEMORY_PERCENT =*値*  
 他のリソース プールとは共有できないこのリソース プール用に予約されるメモリの最小量を指定します。 *値*整数で、既定の設定は 0 です。 許容範囲*値*は 0 ~ 100 です。  
  
 MAX_MEMORY_PERCENT =*値*  
 このリソース プールの要求で使用できる合計サーバー メモリを指定します。 *値*で、既定の設定 100 の整数です。 許容範囲*値*は 1 ~ 100 です。  
  
 MIN_IOPS_PER_VOLUME =*値*  
 **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 リソース プール用に確保するために、ディスク ボリュームごとに、1 秒あたりの最小 I/O 操作 (IOPS) を指定します。 許容範囲*値*は 0 ~ 2 ^31-1 (2,147, 483,647) です。 プールに最小しきい値を指定しない場合は 0 を指定します。  
  
 MAX_IOPS_PER_VOLUME =*値*  
 **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 リソース プールに許された、ディスク ボリュームごとの 1 秒あたりの最大 I/O 操作 (IOPS) 回数を指定します。 許容範囲*値*は 0 ~ 2 ^31-1 (2,147, 483,647) です。 プールに無制限のしきい値を設定する場合は 0 を指定します。 既定値は 0 です。  
  
 プールの MAX_IOPS_PER_VOLUME を 0 に設定した場合、プールは管理されなくなり、他のプールで MIN_IOPS_PER_VOLUME が設定されていても、システムですべての IOPS を行うことがあります。 この場合、IO についてこのプールが管理されるようにするには、このプールの MAX_IOPS_PER_VOLUME の値をより大きな数値 (たとえば、最大値 2^31-1) に設定することをお勧めします。  
  
## <a name="remarks"></a>解説  
 MAX_CPU_PERCENT および MAX_MEMORY_PERCENT する必要がありますより大きいか等しい MIN_CPU_PERCENT および MIN_MEMORY_PERCENT、それぞれします。  
  
 MAX_CPU_PERCENT は、使用可能になる場合、MAX_CPU_PERCENT の値を上回る CPU 容量を使用できます。 CAP_CPU_PERCENT 上の定期的な急増にありますが、ワークロード追加の CPU 容量が使用可能な場合にも、同時の期間延長を CAP_CPU_PERCENT を超えることはありません。  
  
 関連付けられた各コンポーネント (スケジューラまたは NUMA ノード) の CPU 使用率の合計が 100% を超えることはできません。  
  
 DDL ステートメントを実行する場合、リソース ガバナーの状態について詳しく理解しておくことをお勧めします。 詳細については、次を参照してください。[リソース ガバナー](../../relational-databases/resource-governor/resource-governor.md)です。  
  
 設定に影響するプランを変更するときに、新しい設定のみを有効以前にキャッシュされたプランで DBCC FREEPROCCACHE を実行した後 (*pool_name*) ここで、 *pool_name*リソースの名前を指定しますガバナー リソース プールです。  
  
-   1 つのスケジューラに複数のスケジューラからのアフィニティを変更する場合は、DBCC FREEPROCCACHE を実行する必要はありません並列プランが直列モードで実行できるため。 ただし、ある可能性がありますいないほど効率的で、直列プランとしてコンパイルされるプラン。  
  
-   複数のスケジューラに 1 つのスケジューラからのアフィニティを変更する場合は、DBCC FREEPROCCACHE を実行する必要はありません。 ただし、直列プランは、並列で実行することはできません、それぞれのキャッシュをクリアすることが新しいプランを可能性があるため、並列処理を使用してをコンパイルします。  
  
> [!CAUTION]  
>  1 つ以上のワークロード グループに関連付けられているリソース プールからキャッシュされたプランを削除するに影響するすべてのワークロード グループによって識別されるユーザー定義のリソース プールと*pool_name*です。  
  
## <a name="permissions"></a>Permissions  
 CONTROL SERVER 権限が必要です。  
  
## <a name="examples"></a>使用例  
 次の例は上すべての既定のリソース プールの設定を保持、`default`除くプール`MAX_CPU_PERCENT`に変更する`25`です。  
  
```  
ALTER RESOURCE POOL "default"  
WITH  
     ( MAX_CPU_PERCENT = 25);  
GO  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
```  
  
 次の例で、`CAP_CPU_PERCENT`がハード キャップを 80% に設定し、 `AFFINITY SCHEDULER` 8 の個別の値と 12 ~ 16 の範囲に設定されています。  
  
**適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
```  
ALTER RESOURCE POOL Pool25  
WITH(   
     MIN_CPU_PERCENT = 5,  
     MAX_CPU_PERCENT = 10,       
     CAP_CPU_PERCENT = 80,  
     AFFINITY SCHEDULER = (8, 12 TO 16),   
     MIN_MEMORY_PERCENT = 5,  
     MAX_MEMORY_PERCENT = 15  
);  
  
GO  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
  
```  
  
## <a name="see-also"></a>参照  
 [[リソース ガバナー]](../../relational-databases/resource-governor/resource-governor.md)   
 [CREATE RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/create-resource-pool-transact-sql.md)   
 [DROP RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/drop-resource-pool-transact-sql.md)   
 [CREATE WORKLOAD GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/create-workload-group-transact-sql.md)   
 [ALTER WORKLOAD GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/alter-workload-group-transact-sql.md)   
 [DROP WORKLOAD GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/drop-workload-group-transact-sql.md)   
 [ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;](../../t-sql/statements/alter-resource-governor-transact-sql.md)  
  
  
