---
title: "sys.allocation_units (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.allocation_units_TSQL
- sys.allocation_units
- allocation_units_TSQL
- allocation_units
dev_langs: TSQL
helpviewer_keywords: sys.allocation_units catalog view
ms.assetid: ec9de780-68fd-4551-b70b-2d3ab3709b3e
caps.latest.revision: "44"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 5b689c65c59357ff4910701051125e4bd58361ea
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="sysallocationunits-transact-sql"></a>sys.allocation_units (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  データベース内のアロケーション ユニットごとに 1 行のデータを格納します。  
  
||  
|-|  
|**適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [現在のバージョン](http://go.microsoft.com/fwlink/p/?LinkId=299658)まで)。|  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|allocation_unit_id|**bigint**|アロケーション ユニットの ID。 データベース内で一意です。|  
|型|**tinyint**|アロケーション ユニットの種類。<br /><br /> 0 = 削除済み<br /><br /> 1 = 行内データ (LOB データ型を除くすべてのデータ型)<br /><br /> 2 = ラージ オブジェクト (LOB) データ (**テキスト**、 **ntext**、**イメージ**、 **xml**、大きな値型、および CLR ユーザー定義型)<br /><br /> 3 = 行オーバーフロー データ|  
|type_desc|**nvarchar (60)**|アロケーション ユニットの種類の説明。<br /><br /> **削除**<br /><br /> **IN_ROW_DATA**<br /><br /> **LOB_DATA**<br /><br /> **ROW_OVERFLOW_DATA**|  
|container_id|**bigint**|アロケーション ユニットと関連するストレージ コンテナーの ID。<br /><br /> type = 1 または 3 の場合、container_id = sys.partitions.hobt_id になります。<br /><br /> type = 2 の場合、container_id = sys.partitions.partition_id になります。<br /><br /> 0 = 遅延削除のマークが付いたアロケーション ユニット|  
|data_space_id|**int**|アロケーション ユニットが存在するファイル グループの ID。|  
|total_pages|**bigint**|アロケーション ユニットにより割り当てまたは予約されたページの総数。|  
|used_pages|**bigint**|実際に使用される総ページ数。|  
|data_pages|**bigint**|次のデータが含まれている使用済みのページ数。<br /><br /> 行内データ<br /><br /> LOB データ<br /><br /> 行オーバーフロー データ<br /><br /> <br /><br /> 返される値には、内部インデックス ページとアロケーション管理ページを除外します。|  
  
> [!NOTE]  
>  ドロップまたは大規模なインデックスを再構築またはドロップまたは大規模なテーブルを切り捨てるしたときに、[!INCLUDE[ssDE](../../includes/ssde-md.md)]トランザクションがコミットされた後に、まで、実際のページの割り当て解除と、関連するロックを延期します。 削除操作が延期された場合、割り当てられた領域は、すぐには解放されません。 このため、ラージ オブジェクトを削除するか切り捨てた直後に sys.allocation_units を実行して返された値は、実際に使用できるディスク領域を反映していないことがあります。  
  
## <a name="permissions"></a>Permissions  
 ロール **public** のメンバーシップが必要です。 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [sys.partitions および #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-partitions-transact-sql.md)   
 [オブジェクト カタログ ビュー &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
