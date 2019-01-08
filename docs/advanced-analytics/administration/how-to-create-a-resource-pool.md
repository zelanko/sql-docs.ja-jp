---
title: R と Python の SQL Server Machine Learning Services のリソース プールを作成する方法
description: SQL Server 2016 または SQL Server 2017 データベース エンジン インスタンス上の R または Python のプロセス用の SQL Server リソース プールを定義します。
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: c0fcc673e61f2ee188b169a2d46f1da6a4ffd2df
ms.sourcegitcommit: 33712a0587c1cdc90de6dada88d727f8623efd11
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/19/2018
ms.locfileid: "53596863"
---
# <a name="how-to-create-a-resource-pool-for-machine-learning-in-sql-server"></a>SQL Server で機械学習用リソース プールを作成する方法
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

この記事では、作成して、SQL Server で R と Python の machine learning ワークロードの管理専用のリソース プールを使用する方法について説明します。 既にインストールしている、機械学習の機能を有効になっていると想定して R や Python などの外部プロセスによって使用されるリソースのより細かい管理をサポートするためにインスタンスを再構成するとします。

プロセスには、複数のステップが含まれています。

1.  既存のリソース プールの状態を確認します。 どのようなサービスは、既存のリソースを使用しているかを理解することが重要です。
2.  サーバー リソース プールを変更します。
3.  外部プロセス用の新しいリソース プールを作成します。
4.  外部スクリプト要求を識別する分類子関数を作成します。
5.  新しい外部リソース プールが指定したクライアントまたはアカウントから R または Python のジョブをキャプチャすることを確認します。

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
  
    -   データベース エンジンで使用できる最大のコンピューター メモリの量を減らします。
  
    -   外部プロセスで使用できるコンピューターの最大メモリを増やします。

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
    >  これらは; を開始するだけの推奨設定です。機械学習、環境やワークロードに適したバランスを判断するには、他のサーバー プロセスからタスクを評価する必要があります。

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
  
## <a name="create-a-classification-function-for-machine-learning"></a>機械学習の分類子関数を作成します。
  
分類子関数は、受信タスクを検査して、タスクが現在のリソース プールを使用して実行できるかどうかを決定します。 分類子関数の条件を満たしていないタスクは、サーバーの既定のリソース プールに割り当てられます。
  
1. 分類子関数を使用することによってリソース ガバナー リソース プールを決定するを指定することで開始します。 割り当てることができます、 **null**分類子関数のプレース ホルダーとして。
  
    ```sql
    ALTER RESOURCE GOVERNOR WITH (classifier_function = NULL);
    ALTER RESOURCE GOVERNOR RECONFIGURE;
    ```
  
     詳細については、「[ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;](../../t-sql/statements/alter-resource-governor-transact-sql.md)」を参照してください。
  
2.  各リソース プールの分類子関数では、ステートメントまたはリソース プールに割り当てる必要がある受信要求の種類を定義します。
  
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

変更が行われたことを確認するには、これらのインスタンスのリソース プールに関連付けられているワークロード グループのそれぞれのサーバーのメモリと CPU の構成を参照してください。

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
    |1|internal|Medium|25|0|0|0|0|1|2|
    |2|既定値 (default)|Medium|25|0|0|0|0|2|2|
    |256|ds_wg|Medium|25|0|0|0|0|2|256|
  
2.  新しいカタログ ビューを使用して[sys.resource_governor_external_resource_pools &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-resource-governor-external-resource-pools-transact-sql.md)、すべての外部リソース プールを表示します。
  
    ```sql
    SELECT * FROM sys.resource_governor_external_resource_pools;
    ```

    **サンプルの結果**
    
    |external_pool_id|NAME|max_cpu_percent|max_memory_percent|max_processes|version|
    |-|-|-|-|-|-|
    |2|既定値 (default)|100|20|0|2|
    |256|ds_ep|100|40|0|1|
  
     詳細については、「[Resource Governor Catalog Views &#40;Transact-SQL&#41; (リソース ガバナーのカタログ ビュー (Transact-SQL))](../../relational-databases/system-catalog-views/resource-governor-catalog-views-transact-sql.md)」を参照してください。
  
3.  該当する場合に、外部リソース プールに関係付けられているコンピューターのリソースに関する情報を返すには、次のステートメントを実行します。
  
    ```sql
    SELECT * FROM sys.resource_governor_external_resource_pool_affinity;
    ```
  
     ここでは、プールは、AUTO のアフィニティで作成されたため、情報は表示されません。 詳細については、「 [sys.dm_resource_governor_resource_pool_affinity &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-resource-pool-affinity-transact-sql.md)」を参照してください。

## <a name="see-also"></a>関連項目

サーバー リソースの管理の詳細についてを参照してください。

+  [リソース ガバナー](../../relational-databases/resource-governor/resource-governor.md) 
+ [リソース ガバナー関連の動的管理ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/resource-governor-related-dynamic-management-views-transact-sql.md)

リソース ガバナンスの machine learning の概要についてを参照してください。

+  [Machine Learning サービスのリソース ガバナンス](../../advanced-analytics/r/resource-governance-for-r-services.md)
