---
title: "sysdac_history_internal (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sysdac_history_internal
- sysdac_history_internal_TSQL
dev_langs: TSQL
helpviewer_keywords: sysdac_history_internal
ms.assetid: 774a1678-0b27-42be-8adc-a6d7a4a56510
caps.latest.revision: "10"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ae5fd7a9f447d8658deb520964e192e29ab67a49
ms.sourcegitcommit: 2208a909ab09af3b79c62e04d3360d4d9ed970a7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2018
---
# <a name="data-tier-application-tables---sysdachistoryinternal"></a>データ層アプリケーション テーブル - sysdac_history_internal
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  データ層アプリケーション (DAC) を管理するために実行したアクションについての情報を格納します。 次の表は、 **dbo**のスキーマ、 **msdb**データベース。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**action_id**|**int**|アクションの識別子。|  
|**sequence_id**|**int**|アクション内のステップを識別します。|  
|**instance_id**|**uniqueidentifier**|DAC インスタンスの識別子。 この列に結合できます、 **instance_id**内の列[dbo.sysdac_instances &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/data-tier-application-views-dbo-sysdac-instances.md).|  
|**action_type**|**tinyint**|アクションの種類の識別子。<br /><br /> **0** = 展開<br /><br /> **1** = 作成<br /><br /> **2**名前の変更を =<br /><br /> **3** = デタッチ<br /><br /> **4** = delete|  
|**action_type_name**|**varchar(19)**|アクションの種類の名前。<br /><br /> **展開します。**<br /><br /> **作成します。**<br /><br /> **名前の変更**<br /><br /> **デタッチ**<br /><br /> **削除**|  
|**dac_object_type**|**tinyint**|アクションの影響を受けるオブジェクトの種類の識別子。<br /><br /> **0** dacpac を =<br /><br /> **1**ログインを =<br /><br /> **2** = データベース|  
|**dac_object_type_name**|**varchar (8)**|アクションの影響を受けるオブジェクトの種類の名前。<br /><br /> **dacpac** DAC インスタンスを =<br /><br /> **ログイン**<br /><br /> **データベース (database)**|  
|**action_status**|**tinyint**|アクションの現在のステータスを識別するコード。<br /><br /> **0** = 保留中<br /><br /> **1** = 成功<br /><br /> **2** = 失敗|  
|**action_status_name**|**varchar (11)**|アクションの現在のステータス。<br /><br /> **保留中**<br /><br /> **成功した場合**<br /><br /> **失敗します。**|  
|**必須**|**bit**|DAC 操作をロールバックするときに、[!INCLUDE[ssDE](../../includes/ssde-md.md)]によって使用されます。|  
|**dac_object_name_pretran**|**sysname**|アクションを含んでいるトランザクションをコミットする前のオブジェクトの名前。 データベースとログイン専用です。|  
|**dac_object_name_posttran**|**sysname**|アクションを含んでいるトランザクションをコミットした後のオブジェクトの名前。 データベースとログイン専用です。|  
|**sqlscript**|**nvarchar(max)**|データベースまたはログイン上でアクションを実行する [!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプト。|  
|**ペイロード**|**varbinary(max)**|バイナリでエンコードされた文字列に保存される DAC パッケージ定義。|  
|**コメント**|**varchar(max)**|DAC のアップグレードでの潜在的なデータ損失を許可したユーザーのログインを記録します。|  
|**error_string**|**nvarchar(max)**|アクションにエラーが発生した場合に生成されるエラー メッセージ。|  
|**created_by**|**sysname**|このエントリを作成したアクションを開始したログイン。|  
|**date_created**|**datetime**|このエントリが作成された日時。|  
|**date_modified**|**datetime**|エントリを前回変更した日時。|  
  
## <a name="remarks"></a>解説  
 DAC 管理アクション (DAC の配置、削除など) では、複数のステップが生成されます。 各アクションには、アクション識別子が割り当てられます。 各ステップには、シーケンス番号と内の行が割り当てられている**sysdac_history_internal**ステップの状態が記録されます。 アクション ステップが開始されると各行が作成され、操作のステータスを反映する必要に応じて更新されます。 たとえば、DAC の配置アクションを割り当てることができます**action_id** 4 つの行では 12 と get **sysdac_history_internal**:  
  
|||||  
|-|-|-|-|  
|**action_id**|**sequence_id**|**action_type_name**|**dac_object_type_name**|  
|12|0|作成|dacpac|  
|12|@shouldalert|作成|login |  
|12|2|作成|[データベース]|  
|12|3|名前の変更|[データベース]|  
  
 削除などの DAC 操作がから行を削除しないでください**sysdac_history_internal**です。 次のクエリを使用するには不要になったのインスタンスに配置された Dac の行を手動で削除する、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]:  
  
```sql  
DELETE FROM msdb.dbo.sysdac_history_internal  
WHERE instance_id NOT IN  
   (SELECT instance_id  
    FROM msdb.dbo.sysdac_instances_internal);  
```  
  
 アクティブな DAC の行を削除しても、DAC 操作には影響しません。唯一の影響は、DAC の完全な履歴をレポートできなくなる点のみです。  
  
> [!NOTE]  
>  現時点では、削除するためのメカニズムがない**sysdac_history_internal**行 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]です。  
  
## <a name="permissions"></a>アクセス許可  
 sysadmin 固定サーバー ロールのメンバーシップが必要です。 このビューに読み取り専用のアクセスは、master データベースに接続するアクセス許可を持つすべてのユーザーに使用できます。  
  
## <a name="see-also"></a>参照  
 [[データ層アプリケーション]](../../relational-databases/data-tier-applications/data-tier-applications.md)   
 [dbo.sysdac_instances &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/data-tier-application-views-dbo-sysdac-instances.md)   
 [sysdac_instances_internal に対応する &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-tables/data-tier-application-tables-sysdac-instances-internal.md)  
  
  
