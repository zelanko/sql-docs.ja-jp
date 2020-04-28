---
title: allocation_units (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.allocation_units_TSQL
- sys.allocation_units
- allocation_units_TSQL
- allocation_units
dev_langs:
- TSQL
helpviewer_keywords:
- sys.allocation_units catalog view
ms.assetid: ec9de780-68fd-4551-b70b-2d3ab3709b3e
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 73ee5d7ac8bd512b69cc187f9860b9e7f2c38a78
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "68001297"
---
# <a name="sysallocation_units-transact-sql"></a>sys.allocation_units (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  データベース内のアロケーションユニットごとに1行のデータを格納します。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|allocation_unit_id|**bigint**|アロケーションユニットの ID。 データベース内で一意です。|  
|type|**tinyint**|アロケーションユニットの種類:<br /><br /> 0 = 削除された<br /><br /> 1 = 行内データ (LOB データ型を除くすべてのデータ型)<br /><br /> 2 = ラージオブジェクト (LOB) データ (**テキスト**,、 **ntext**,、**イメージ**,、 **xml**,、大きな値の型と CLR ユーザー定義型)<br /><br /> 3 = 行オーバーフローデータ|  
|type_desc|**nvarchar(60)**|アロケーション ユニットの種類の説明。<br /><br /> **アロケーション**<br /><br /> **IN_ROW_DATA**<br /><br /> **LOB_DATA**<br /><br /> **ROW_OVERFLOW_DATA**|  
|container_id|**bigint**|アロケーションユニットに関連付けられているストレージコンテナーの ID。<br /><br /> type = 1 または 3 の場合、container_id = sys.partitions.hobt_id になります。<br /><br /> type = 2 の場合、container_id = sys.partitions.partition_id になります。<br /><br /> 0 = 遅延削除用にマークされたアロケーションユニット|  
|data_space_id|**int**|このアロケーションユニットが存在するファイルグループの ID。|  
|total_pages|**bigint**|このアロケーションユニットによって割り当てられた、または予約されているページの合計数。|  
|used_pages|**bigint**|実際に使用されているページの合計数。|  
|data_pages|**bigint**|使用されているページの数:<br /><br /> In-row data<br /><br /> LOB データ<br /><br /> Row-overflow data<br /><br /> <br /><br /> 返される値には、内部インデックスページとアロケーション管理ページは含まれないことに注意してください。|  
  
> [!NOTE]  
>  大きなインデックスを削除または再構築したり、大きなテーブルを削除し[!INCLUDE[ssDE](../../includes/ssde-md.md)]たり切り捨てたりすると、では、トランザクションがコミットされるまで、実際のページの割り当て解除とそれに関連付けられているロックが延期されます。 遅延削除操作では、割り当てられた領域はすぐに解放されません。 このため、ラージ オブジェクトを削除するか切り捨てた直後に sys.allocation_units を実行して返された値は、実際に使用できるディスク領域を反映していないことがあります。  
  
## <a name="permissions"></a>アクセス許可  
 ロール **public** のメンバーシップが必要です。  詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [SQL&#41;&#40;Transact-sql のパーティション分割](../../relational-databases/system-catalog-views/sys-partitions-transact-sql.md)   
 [オブジェクトカタログビュー &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
