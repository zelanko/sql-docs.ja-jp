---
title: sysdac_history_internal (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysdac_history_internal
- sysdac_history_internal_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysdac_history_internal
ms.assetid: 774a1678-0b27-42be-8adc-a6d7a4a56510
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 40696085bc8eb9980d1150feade91a9edd627be0
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47810394"
---
# <a name="data-tier-application-tables---sysdachistoryinternal"></a>データ層アプリケーション テーブル - sysdac_history_internal
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  データ層アプリケーション (DAC) を管理するために実行したアクションについての情報を格納します。 このテーブルに格納されます、 **dbo**のスキーマ、 **msdb**データベース。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**action_id**|**int**|アクションの識別子。|  
|**sequence_id**|**int**|アクション内のステップを識別します。|  
|**instance_id**|**uniqueidentifier**|DAC インスタンスの識別子。 この列に結合できます、 **instance_id**列[dbo.sysdac_instances &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/data-tier-application-views-dbo-sysdac-instances.md)します。|  
|**action_type**|**tinyint**|アクションの種類の識別子。<br /><br /> **0** = デプロイ<br /><br /> **1** = 作成<br /><br /> **2** = 名前の変更<br /><br /> **3** = デタッチ<br /><br /> **4** = 削除||  
|**action_type_name**|**varchar(19)**|アクションの種類の名前。<br /><br /> **deploy**<br /><br /> **create**<br /><br /> **rename**<br /><br /> **detach**<br /><br /> **delete**|  
|**dac_object_type**|**tinyint**|アクションの影響を受けるオブジェクトの種類の識別子。<br /><br /> **0** = dacpac<br /><br /> **1** = ログイン<br /><br /> **2** = データベース|  
|**dac_object_type_name**|**varchar(8)**|アクションの影響を受けるオブジェクトの種類の名前。<br /><br /> **dacpac** = DAC インスタンス<br /><br /> **login**<br /><br /> **データベース (database)**|  
|**action_status**|**tinyint**|アクションの現在のステータスを識別するコード。<br /><br /> **0** = 保留中<br /><br /> **1** = 成功<br /><br /> **2** = 失敗|  
|**action_status_name**|**varchar(11)**|アクションの現在のステータス。<br /><br /> **pending**<br /><br /> **success**<br /><br /> **fail**|  
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
  
## <a name="remarks"></a>コメント  
 DAC 管理アクション (DAC の配置、削除など) では、複数のステップが生成されます。 各アクションには、アクション識別子が割り当てられます。 各ステップは、シーケンス番号と行に割り当てられている**sysdac_history_internal**ステップの状態が記録されます。 アクション ステップが開始されると各行が作成され、操作のステータスを反映する必要に応じて更新されます。 たとえば、DAC の配置アクションを割り当てることが**action_id**内の 4 行 12 と get **sysdac_history_internal**:  
  
|||||  
|-|-|-|-|  
|**action_id**|**sequence_id**|**action_type_name**|**dac_object_type_name**|  
|12|0|作成|dacpac|  
|12|1|作成|login |  
|12|2|作成|[データベース]|  
|12|3|名前の変更|[データベース]|  
  
 削除などの DAC 操作がから行を削除しないでください**sysdac_history_internal**します。 次のクエリを使用して、不要になったのインスタンスに配置された dac の行を手動で削除することができます、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]:  
  
```sql  
DELETE FROM msdb.dbo.sysdac_history_internal  
WHERE instance_id NOT IN  
   (SELECT instance_id  
    FROM msdb.dbo.sysdac_instances_internal);  
```  
  
 アクティブな DAC の行を削除しても、DAC 操作には影響しません。唯一の影響は、DAC の完全な履歴をレポートできなくなる点のみです。  
  
> [!NOTE]  
>  現時点では、削除するためのメカニズムはありません**sysdac_history_internal**行 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]します。  
  
## <a name="permissions"></a>アクセス許可  
 sysadmin 固定サーバー ロールのメンバーシップが必要です。 このビューに読み取り専用のアクセスは、master データベースに接続するアクセス許可を持つすべてのユーザーに使用できます。  
  
## <a name="see-also"></a>参照  
 [[データ層アプリケーション]](../../relational-databases/data-tier-applications/data-tier-applications.md)   
 [dbo.sysdac_instances &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/data-tier-application-views-dbo-sysdac-instances.md)   
 [sysdac_instances_internal &#40;TRANSACT-SQL&#41;](../../relational-databases/system-tables/data-tier-application-tables-sysdac-instances-internal.md)  
  
  
