---
title: "外部リソース プールを変更 (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/13/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: ALTER_EXTERNAL_RESOURCE_POOL_TSQL
dev_langs: TSQL
helpviewer_keywords: ALTER EXTERNAL RESOURCE POOL statement
ms.assetid: 634c327d-971b-49ba-b8a2-e243a04040db
caps.latest.revision: "10"
author: jeannt
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: cb4073a8114e953dc9df87614a63e074ab8c9683
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="alter-external-resource-pool-transact-sql"></a>外部リソース プールを変更 (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]
**適用されます:** [!INCLUDE[sssql15-md](../../includes/sssql15-md.md)] [!INCLUDE[rsql-productname-md](../../includes/rsql-productname-md.md)]と[!INCLUDE[sssql17-md](../../includes/sssql17-md.md)][!INCLUDE[rsql-productnamenew-md](../../includes/rsql-productnamenew-md.md)]

外部プロセスで使用できるリソースを指定するリソース ガバナーの外部プールを変更します。 

+ [!INCLUDE[rsql-productname-md](../../includes/rsql-productname-md.md)]で[!INCLUDE[sssql15-md](../../includes/sssql15-md.md)]、外部プールを管理`rterm.exe`、 `BxlServer.exe`、およびそれらにより生成された他のプロセスです。

+ [!INCLUDE[rsql-productnamenew-md](../../includes/rsql-productnamenew-md.md)]外部プールが、以前のバージョンに登録されている R のプロセスを制御する SQL Server の 2017 だけでなく`python.exe`、 `BxlServer.exe`、およびそれらにより生成された他のプロセスです。

 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [TRANSACT-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)です。

## <a name="syntax"></a>構文

```sql
ALTER EXTERNAL RESOURCE POOL { pool_name | "default" }
[ WITH (
    [ MAX_CPU_PERCENT = value ]
    [ [ , ] AFFINITY CPU =
            {
                AUTO
              | ( <cpu_range_spec> )
              | NUMANODE = (( <NUMA_node_id> )
            } ]   
    [ [ , ] MAX_MEMORY_PERCENT = value ]
    [ [ , ] MAX_PROCESSES = value ]
    )
]
[ ; ]
  
<CPU_range_spec> ::=
{ CPU_ID | CPU_ID  TO CPU_ID } [ ,...n ]
```  
  
## <a name="arguments"></a>引数

{ *pool_name* |"default"}  
既存のユーザー定義の外部リソース プールまたはときに作成される既定の外部リソース プールの名前は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]がインストールされています。
"default"は、引用符で囲む必要があります ("") または角かっこ () を使用すると`ALTER EXTERNAL RESOURCE POOL`と競合しないように`DEFAULT`、これは、システム予約語です。


MAX_CPU_PERCENT =*値*  
最大平均 CPU 帯域幅 CPU の競合がある場合、外部リソース プールのすべての要求を受信できることを指定します。 *値*で、既定の設定 100 の整数です。 許容範囲*値*は 1 ~ 100 です。


アフィニティ {CPU = 自動 |( \<CPU_range_spec >) |NUMANODE = (\<NUMA_node_range_spec >)}  
外部リソース プールを特定の Cpu にアタッチします。 既定値は AUTO です。

アフィニティ CPU = **(** \<CPU_range_spec > **)**外部リソース プールをマップする、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]特定 CPU_IDs で識別される Cpu。 AFFINITY NUMANODE を使用すると = **(** \<NUMA_node_range_spec > **)**、外部リソース プールが関連付けられ、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]指定した NUMA に対応する物理 Cpuノードまたはノードの範囲です。


MAX_MEMORY_PERCENT =*値*  
この外部リソース プールの要求で使用できる合計サーバー メモリを指定します。 *値*で、既定の設定 100 の整数です。 許容範囲*値*は 1 ~ 100 です。


MAX_PROCESSES =*値*  
外部リソース プールのプロセスの最大数を指定します。 その後、コンピューター リソースによってのみにバインドされていると、プールに対して無制限のしきい値を設定する場合は 0 を指定します。 既定値は 0 です。

## <a name="remarks"></a>解説

[!INCLUDE[ssDE](../../includes/ssde-md.md)]を実行するときに、リソース プールを実装して、 [ALTER RESOURCE GOVERNOR RECONFIGURE](../../t-sql/statements/alter-resource-governor-transact-sql.md)ステートメントです。

リソース プールの概要については、次を参照してください。[リソース ガバナー リソース プール](../../relational-databases/resource-governor/resource-governor-resource-pool.md)、 [sys.resource_governor_external_resource_pools &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-resource-governor-external-resource-pools-transact-sql.md)、および[sys.dm_resource_governor_external_resource_pool_affinity &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-external-resource-pool-affinity-transact-sql.md).  

Machine learning のジョブを制御するために外部のリソース プールの使用に特有について、次を参照してください[機械学習で SQL Server のリソース管理](../../advanced-analytics/r/resource-governance-for-r-services.md)しています.。
## <a name="permissions"></a>Permissions

必要があります`CONTROL SERVER`権限です。

## <a name="examples"></a>使用例

次のステートメントでは、50% をコンピューターで使用可能なメモリの 25% の最大メモリ量の CPU 使用率を制限する、外部プールを変更します。
  
```sql
ALTER EXTERNAL RESOURCE POOL ep_1
WITH (
    MAX_CPU_PERCENT = 50
    , AFFINITY CPU = AUTO
    , MAX_MEMORY_PERCENT = 25
);
GO
ALTER RESOURCE GOVERNOR RECONFIGURE;
GO
```

## <a name="see-also"></a>参照

[SQL Server での機械学習用リソース ガバナンス](../../advanced-analytics/r/resource-governance-for-r-services.md)

[external scripts enabled サーバー構成オプション](../../database-engine/configure-windows/external-scripts-enabled-server-configuration-option.md)

[CREATE EXTERNAL RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-resource-pool-transact-sql.md)

[外部リソース プールの削除 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-external-resource-pool-transact-sql.md)

[ALTER RESOURCE POOL &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-resource-pool-transact-sql.md)

[WORKLOAD GROUP &#40; を作成します。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-workload-group-transact-sql.md)

[リソース ガバナー リソース プール](../../relational-databases/resource-governor/resource-governor-resource-pool.md)

[ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;](../../t-sql/statements/alter-resource-governor-transact-sql.md) 
