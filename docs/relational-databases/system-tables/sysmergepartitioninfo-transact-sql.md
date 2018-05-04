---
title: sysmergepartitioninfo (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sysmergepartitioninfo_TSQL
- sysmergepartitioninfo
dev_langs:
- TSQL
helpviewer_keywords:
- sysmergepartitioninfo system table
ms.assetid: 7429ad2c-dd33-4f7d-89cc-700e083af518
caps.latest.revision: 25
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: bcf556a371dc391b41e08778434b25131bfcf09e
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sysmergepartitioninfo-transact-sql"></a>sysmergepartitioninfo (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  各アーティクルのパーティションに関する情報を提供します。 ローカル データベースに定義されているマージ アーティクルごとに 1 行のデータを格納します。 このテーブルは、パブリケーション データベースとサブスクリプション データベースに保存されます。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**artid**|**uniqueidentifier**|指定したアーティクルの一意な ID 番号です。|  
|**pubid**|**uniqueidentifier**|このパブリケーションの一意な ID 番号です。パブリケーションが追加されるときに生成されます。|  
|**partition_view_id**|**int**|このテーブルに関するパーティション ビューの ID です。 このビューには、アーティクル内の各行から、そのビューが所属する別のパーティション ID へのマッピングが表示されます。|  
|**repl_view_id**|**int**|追加されます。|  
|**partition_deleted_view_rule**|**nvarchar (4000)**|マージ レプリケーション トリガー内で、列の古い値に基づいて削除または更新された各行のパーティション ID を取得するために使用される SQL ステートメントです。|  
|**partition_inserted_view_rule**|**nvarchar (4000)**|マージ レプリケーション トリガー内で、列の新しい値に基づいて挿入または更新された各行のパーティション ID を取得するために使用される SQL ステートメントです。|  
|**membership_eval_proc_name**|**sysname**|内の行の現在のパーティション Id を評価するプロシージャの名前**MSmerge_contents**です。|  
|**column_list**|**nvarchar (4000)**|アーティクル内でレプリケートされた列のコンマ区切りの一覧です。|  
|**column_list_blob**|**nvarchar (4000)**|Binary Large Object の列を含む、アーティクル内でレプリケートされた列のコンマ区切りの一覧です。|  
|**expand_proc**|**sysname**|パーティションで新しく挿入された親行のすべての子行と、パーティション変更が行われているか削除されている親行に対して Id を再評価するプロシージャの名前です。|  
|**logical_record_parent_nickname**|**int**|論理レコード内の、指定されたアーティクルのトップレベルにある親のニックネームです。|  
|**logical_record_view**|**int**|それぞれの子の rowguid に対応する、トップレベルにある親アーティクルの rowguid を出力するビューです。|  
|**logical_record_deleted_view_rule**|**nvarchar (4000)**|ような**logical_record_view**子テーブル内の行、"deleted"には、update および delete トリガーを除いて、します。|  
|**logical_record_level_conflict_detection**|**bit**|競合を、論理レコード レベルと、行または列レベルのどちらで検出するかを示します。<br /><br /> **0** = 行または列レベルの競合検出を使用します。<br /><br /> **1** = 論理レコードの競合検出を使用する、パブリッシャーで行の変更と、個別の変更は、同じ論理行を行、サブスクライバーのレコードは、競合として処理します。<br /><br /> この値が**1**、論理レコード レベルの競合解決だけを使用できます。|  
|**logical_record_level_conflict_resolution**|**bit**|競合を、論理レコード レベルと、行または列レベルのどちらで解決するかを示します。<br /><br /> **0** = 行または列レベルの解決を使用します。<br /><br /> **1** = の場合に、論理レコード全体が優先されるデータ競合の側を優先されなかった論理レコード全体が上書きされます。<br /><br /> 値**1**両方論理レコード レベルの検出、行または列レベルの検出に使用することができます。|  
|**partition_options**|**tinyint**|アーティクル内のデータをパーティション分割する方法を定義します。パーティション分割することにより、すべての行が 1 つのパーティションまたは 1 つのサブスクリプションに属している場合に、パフォーマンスを最適化できます。 *partition_options*値は次のいずれかになります。<br /><br /> **0** = フィルター選択は、アーティクルまたはいずれかが静的では各パーティションでは、つまり「重複する」パーティションのデータの一意なサブセットを生成しません。<br /><br /> **1** = パーティションが重複している場合、およびサブスクライバーで実行された DML 更新は、行が属するパーティションを変更できません。<br /><br /> **2** = フィルター選択は、アーティクルには、重複しないパーティションが得られますが、複数のサブスクライバーが同じパーティションを受け取ることができます。<br /><br /> **3** = フィルター選択は、アーティクルには、各サブスクリプションに対して一意では、重複しないパーティションが得られます。|  
  
## <a name="see-also"></a>参照  
 [レプリケーション テーブル &#40; です。TRANSACT-SQL と &#41; です。](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
