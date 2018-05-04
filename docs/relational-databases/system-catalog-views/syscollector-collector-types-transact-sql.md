---
title: syscollector_collector_types (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- syscollector_collector_types
- syscollector_collector_types_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- data collector view
- syscollector_collector_types view
ms.assetid: d5cd30bb-89fd-4814-a7e8-9074f043f90f
caps.latest.revision: 20
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 9c56b03d902a329e47496b81d4f16e7f35f4bd39
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="syscollectorcollectortypes-transact-sql"></a>syscollector_collector_types (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  コレクション アイテムのコレクターの種類に関する情報を提供します。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**collector_type_uid**|**uniqueidentifer**|コレクション型の GUID。 NULL 値は許可されません。|  
|**name**|**sysname**|コレクション型の名前。 NULL 値は許可されません。|  
|**parameter_schema**|**xml**|指定されたコレクターの種類の構成を記述する XML スキーマ。 この XML スキーマは、特定のコレクション アイテム インスタンスに関連付けられた実際の XML 構成を検証するときに使用されます。 NULL 値が許可されます。|  
|**parameter_formatter**|**xml**|コレクション セットのプロパティ ページで使用するために XML を変換するときのテンプレートを指定します。 NULL 値が許可されます。|  
|**collection_package_id**|**uniqueidentifer**|コレクション パッケージの GUID。 NULL 値は許可されません。|  
|**collection_package_path**|**nvarchar (4000)**|コレクション パッケージのパス。 NULL 値が許可されます。|  
|**collection_package_name**|**sysname**|コレクション パッケージの名前。 NULL 値は許可されません。|  
|**upload_package_id**|**uniqueidentifer**|アップロード パッケージの GUID。 NULL 値は許可されません。|  
|**upload_package_path**|**nvarchar (4000)**|アップロード パッケージのパス。 NULL 値が許可されます。|  
|**upload_package_name**|**sysname**|アップロード パッケージの名前。 NULL 値は許可されません。|  
|**is_system**|**bit**|オン (1) またはオフ (0) を示す、コレクター型は、データ コレクターで出荷された場合、または後で追加された場合、 **dc_admin**です。 たとえば、社内またはサード パーティによって開発されたカスタム型が考えられます。 NULL 値は許可されません。|  
  
## <a name="permissions"></a>権限  
 SELECT 権限が必要**dc_operator**、 **dc_proxy**です。  
  
## <a name="change-history"></a>変更履歴  
  
|変更内容|  
|---------------------|  
|更新**collection_type_uid**列名を**collector_type_uid**です。|  
|説明を修正、 **parameter_schema**列値が null 許容であることを示します。|  
|追加、 **parameter_formatter**列です。|  
|データ型を修正、 **collection_package_path**列、値が null 許容であることを示す説明を更新します。|  
|データ型を修正、 **upload_package_path**列、値が null 許容であることを示す説明を更新します。|  
  
## <a name="see-also"></a>参照  
 [データ コレクター ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql.md)   
 [データ コレクターのビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/data-collector-views-transact-sql.md)   
 [[データ コレクション]](../../relational-databases/data-collection/data-collection.md)  
  
  
