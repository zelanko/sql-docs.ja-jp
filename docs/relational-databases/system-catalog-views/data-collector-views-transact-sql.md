---
title: データコレクタービュー (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- data collector view
- data collector [SQL Server], views
ms.assetid: a005e885-7813-4c7e-b332-b01d9e9d4054
author: stevestein
ms.author: sstein
ms.openlocfilehash: 9e412f796a5b04f980557b5a3131763811aa78da
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68033173"
---
# <a name="data-collector-views-transact-sql"></a>データ コレクターのビュー (Transact-SQL)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  データコレクターには、データコレクターの構成に関する情報を表示するための次のビューが用意されています。これには、コレクター型のプロパティ、コレクションセット、コレクションセットの項目、およびコレクションセットの実行時に取得される実行の統計情報が表示されます。ラン. これらのビューは、 **msdb**データベースにあり、基になるテーブルの抽象レイヤーも提供します。 この抽象化により、テーブルへの直接アクセスを防止しながら、関連付けられているアプリケーションに影響を与えることなくテーブルを変更できるようにすることで、セキュリティが強化されます。  
  
|||  
|-|-|  
|[syscollector_collection_items &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/syscollector-collection-items-transact-sql.md)|[syscollector_collection_sets &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/syscollector-collection-sets-transact-sql.md)|  
|[syscollector_collector_types &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/syscollector-collector-types-transact-sql.md)|[syscollector_config_store &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/syscollector-config-store-transact-sql.md)|  
|[syscollector_execution_log &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/syscollector-execution-log-transact-sql.md)|[syscollector_execution_log_full &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/syscollector-execution-log-full-transact-sql.md)|  
|[syscollector_execution_stats &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/syscollector-execution-stats-transact-sql.md)||  
  
## <a name="see-also"></a>参照  
 [データコレクション](../../relational-databases/data-collection/data-collection.md)   
 [データコレクターストアドプロシージャ &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql.md)  
  
  
