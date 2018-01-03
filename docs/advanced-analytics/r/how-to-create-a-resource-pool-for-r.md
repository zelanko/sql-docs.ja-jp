---
title: "機械学習用リソース プールを作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/13/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c7f7f6e4-774d-4b45-b94a-f06c51718475
caps.latest.revision: "19"
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Inactive
ms.openlocfilehash: f5699ed583f0fd40657f3be5f132b879681a7942
ms.sourcegitcommit: 23433249be7ee3502c5b4d442179ea47305ceeea
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2017
---
# <a name="create-a-resource-pool-for-machine-learning"></a>機械学習用リソース プールを作成します。

このトピックでは、SQL Server の machine learning ワークロードを管理するためには、具体的には、リソース プールを作成する方法について説明します。 既にインストールしている、機械学習の機能を有効になっていると想定し、R、Python などの外部プロセスによって使用されているリソースのより詳細な管理をサポートするためにインスタンスを再構成します。

プロセスには、複数のステップが含まれます。

1.  既存のリソース プールの状態を確認します。 これは既存のリソースを使用しているどのようなサービスを理解することが重要です。
2.  サーバー リソース プールを変更します。
3.  外部プロセス用に新しいリソース プールを作成します。
4.  外部スクリプトの要求を識別する分類子関数を作成します。
5.  新しい外部リソース プールが指定したクライアントまたはアカウントから R または Python のジョブをキャプチャすることを確認します。

**適用されます:** [!INCLUDE[sssql15-md](../../includes/sssql15-md.md)] [!INCLUDE[rsql-productname-md](../../includes/rsql-productname-md.md)]と[!INCLUDE[sscurrent-md](../../includes/sscurrent-md.md)][!INCLUDE[rsql-productnamenew-md](../../includes/rsql-productnamenew-md.md)]

##  <a name="bkmk_ReviewStatus"></a>既存のリソース プールの状態を確認する
  
1.  次のようなステートメントを使用すると、サーバーの既定のプールに割り当てられたリソースをチェックできます。
  
    ```sql
    SELECT * FROM sys.resource_governor_resource_pools WHERE name = 'default'
    ```

    **サンプルの結果**

    |pool_id|NAME|min_cpu_percent|max_cpu_percent|min_memory_percent|max_memory_percent|cap_cpu_percent|min_iops_per_volume|max_iops_per_volume|
    |-|-|-|-|-|-|-|-|-|
    |2|既定値 (default)|0|100|0|100|100|0|0|

2.  既定の**外部**リソース プールに割り当てられているリソースを確認します。
  
    ```sql
    SELECT * FROM sys.resource_governor_external_resource_pools WHERE name = 'default'
    ```

    **サンプルの結果**

    |external_pool_id|NAME|max_cpu_percent|max_memory_percent|max_processes|version|
    |-|-|-|-|-|-|
    |2|既定値 (default)|100|20|0|2|
 
3.  これらのサーバー既定の設定で、外部のランタイムをリソース不足のため、ほとんどのタスクを完了するがあります。 これを変更するには、サーバーのリソース使用率を次のように変更する必要があります。
  
    -   データベース エンジンで使用できる最大コンピューター メモリの量を減らします。
  
    -   外部プロセスで使用できる最大のコンピューターのメモリを増やします。

## <a name="modify-server-resource-usage"></a>サーバーのリソース使用率を変更する

1.  [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] で、次のステートメントを実行して、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のメモリ使用量を [最大サーバー メモリ] の値の **60%** に制限します。

    ```sql
    ALTER RESOURCE POOL "default" WITH (max_memory_percent = 60);
    ```
  
2.  同様に、次のステートメントを実行して、外部プロセスによるメモリの使用量をコンピューター リソース全体の **40%** に制限します。
  
    ```sql
    ALTER EXTERNAL RESOURCE POOL "default" WITH (max_memory_percent = 40);
    ```
  
3.  これらの変更を適用するには、リソース ガバナーを次のように再構成して再起動する必要があります。
  
    ```sql
    ALTER RESOURCE GOVERNOR RECONFIGURE;
    ```
  
    > [!NOTE]
    >  これらは; で開始するだけの推奨設定です。機械学習の他のサーバー プロセスを環境とワークロードのバランスを判断する照らし合わせてタスクを評価する必要があります。

## <a name="create-a-user-defined-external-resource-pool"></a>ユーザー定義の外部リソース プールを作成する
  
1.  リソース ガバナーの構成に対する変更はサーバー全体に適用され、サーバーの既定のプールを使用するワークロードだけではなく、外部プールを使用するワークロードにも影響します。
  
     そのため、優先するワークロードを細かく制御するために、新しいユーザー定義の外部リソース プールを作成できます。 さらに、分類子関数を定義して、外部リソース プールに割り当てる必要があります。 **外部**キーワードは新しいです。
  
     新しい "*ユーザー定義の外部リソース プール*" の作成から始めます。 次の例では、プールに **ds_ep** という名前を付けています。
  
    ```sql
    CREATE EXTERNAL RESOURCE POOL ds_ep WITH (max_memory_percent = 40);
    ```

2.  セッション要求の管理で使用する `ds_wg` という名前のワークロード グループを作成します。 SQL クエリでは既定のプールを使用し、すべての外部プロセスのクエリでは `ds_ep` プールを使用します。
  
    ```sql
    CREATE WORKLOAD GROUP ds_wg WITH (importance = medium) USING "default", EXTERNAL "ds_ep";
    ```
  
     要求は、要求を分類することができない場合、またはその他の分類エラーが発生した場合は、既定のグループに割り当てられます。
  
     詳細については、「[Resource Governor Workload Group (リソース ガバナー ワークロード グループ)](../../relational-databases/resource-governor/resource-governor-workload-group.md)」と「[CREATE WORKLOAD GROUP &#40;Transact-SQL&#41; (ワークロード グループの作成 (TRANSACT-SQL))](../../t-sql/statements/create-workload-group-transact-sql.md)」を参照してください。
  
## <a name="create-a-classification-function-for-machine-learning"></a>機械学習の分類関数を作成します。
  
分類子関数は、受信タスクを検査して、タスクが現在のリソース プールを使用して実行できるかどうかを決定します。 分類子関数の条件を満たしていないタスクは、サーバーの既定のリソース プールに割り当てられます。
  
1. 分類子関数を使用することによってリソース ガバナー リソース プールを決定するを指定することから始めます。 割り当てることができます、 **null**分類子関数のプレース ホルダーとして。
  
    ```sql
    ALTER RESOURCE GOVERNOR WITH (classifier_function = NULL);
    ALTER RESOURCE GOVERNOR RECONFIGURE;
    ```
  
     詳細については、「[ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;](../../t-sql/statements/alter-resource-governor-transact-sql.md)」を参照してください。
  
2.  各リソース プールの分類子関数では、ステートメントまたはリソース プールに割り当てる必要が受信した要求の種類を定義します。
  
     たとえば、次の関数は、要求を送信したアプリケーションが 'Microsoft R Host' または 'RStudio' の場合は、ユーザー定義の外部リソース プールに割り当てられたスキーマの名前を返します。それ以外の場合は既定のリソース プールを返します。
  
    ```sql
    USE master
    GO
    CREATE FUNCTION is_ds_apps()
    RETURNS sysname
    WITH schemabinding
    AS
    BEGIN
        IF program_name() in ('Microsoft R Host', 'RStudio') RETURN 'ds_wg';
        RETURN 'default'
        END;
    GO
    ```
  
3.  関数を作成したら、リソース グループを再定義して、新しい分類子関数が先ほど定義した外部リソース グループに割り当てられるようにします。
  
    ```sql
    ALTER RESOURCE GOVERNOR WITH  (classifier_function = dbo.is_ds_apps);
    ALTER RESOURCE GOVERNOR WITH reconfigure;
    GO
    ```

## <a name="verify-new-resource-pools-and-affinity"></a>新しいリソース プールとアフィニティを確認する

変更が行われたことを確認するには、これらのインスタンスのリソース プールに関連付けられているワークロード グループのそれぞれのサーバー メモリと CPU の構成を確認する必要があります。

+ 既定のプール、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]サーバー
+ 外部プロセス用の既定のリソース プール
+ 外部プロセス用のユーザー定義プール

1. すべてのワークロード グループを表示するのには、次のステートメントを実行します。

    ```sql
    SELECT * FROM sys.resource_governor_workload_groups;
    ```

    **サンプルの結果**

    |group_id|NAME|importance|request_max_memory_grant_percent|request_max_cpu_time_sec|request_memory_grant_timeout_sec|max_dop|group_max_requests pool_id|pool_idd|external_pool_id|
    |-|-|-|-|-|-|-|-|-|-|
    |@shouldalert|internal|Medium|25|0|0|0|0|@shouldalert|2|
    |2|既定値 (default)|Medium|25|0|0|0|0|2|2|
    |256|ds_wg|Medium|25|0|0|0|0|2|256|
  
2.  新しいカタログ ビューを使用して[sys.resource_governor_external_resource_pools &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-resource-governor-external-resource-pools-transact-sql.md)、すべての外部リソース プールを表示します。
  
    ```sql
    SELECT * FROM sys.resource_governor_external_resource_pools;
    ```

    **サンプルの結果**
    
    |external_pool_id|NAME|max_cpu_percent|max_memory_percent|max_processes|version|
    |-|-|-|-|-|-|
    |2|既定値 (default)|100|20|0|2|
    |256|ds_ep|100|40|0|@shouldalert|
  
     詳細については、「[Resource Governor Catalog Views &#40;Transact-SQL&#41; (リソース ガバナーのカタログ ビュー (Transact-SQL))](../../relational-databases/system-catalog-views/resource-governor-catalog-views-transact-sql.md)」を参照してください。
  
3.  該当する場合は、外部リソース プールに関連付けられコンピューターのリソースに関する情報を返すには、次のステートメントを実行します。
  
    ```sql
    SELECT * FROM sys.resource_governor_external_resource_pool_affinity;
    ```
  
     ここでは、プールは、AUTO のアフィニティで作成されたため、情報は表示されません。 詳細については、「 [sys.dm_resource_governor_resource_pool_affinity &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-resource-pool-affinity-transact-sql.md)」を参照してください。

## <a name="see-also"></a>参照

サーバー リソースの管理の詳細についてを参照してください。

+  [リソース ガバナー](../../relational-databases/resource-governor/resource-governor.md) 
+ [リソース ガバナー関連の動的管理ビュー &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/resource-governor-related-dynamic-management-views-transact-sql.md)

機械学習のリソース管理の概要についてを参照してください。

+  [Machine Learning のサービスのリソース管理](../../advanced-analytics/r/resource-governance-for-r-services.md)
