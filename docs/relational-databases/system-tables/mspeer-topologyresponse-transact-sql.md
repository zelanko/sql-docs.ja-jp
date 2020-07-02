---
title: MSpeer_topologyresponse (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSpeer_topologyresponse
- MSpeer_topologyresponse_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSpeer_topologyresponse
ms.assetid: 1bc5c0c6-c432-405c-89fd-e953d173a247
author: CarlRabeler
ms.author: carlrab
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: b8edfe5033d198eaca52a8cf320e9b3dac9960e7
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85751647"
---
# <a name="mspeer_topologyresponse-transact-sql"></a>MSpeer_topologyresponse (Transact-sql)
[!INCLUDE [sql-asdb-asdbmi-asdw-pdw](../../includes/applies-to-version/sql-asdb-asdbmi-asdw-pdw.md)]

  トポロジ状態要求に対する各ノードの応答を保存するために、ピア ツー ピア レプリケーションで使用されます。 このテーブルは、パブリケーションデータベースに格納されます。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|request_id|**int**|[MSpeer_topologyrequest](../../relational-databases/system-tables/mspeer-topologyrequest-transact-sql.md)テーブルのトポロジ状態要求エントリを識別します。|  
|peer|**sysname**|応答を生成したサーバーインスタンスの名前。|  
|peer_version|**int**|パブリッシャーのバージョン番号を識別します。|  
|peer_db|**sysname**|応答を生成したピアのサブスクリプションデータベース。|  
|originator_id|**int**|競合検出のためにトポロジの各ノードを識別します。 詳細については、「 [ピア ツー ピア レプリケーションにおける競合検出](../../relational-databases/replication/transactional/peer-to-peer-conflict-detection-in-peer-to-peer-replication.md)」を参照してください。|  
|peer_conflict_retention|**int**|メタデータが競合テーブルに格納される期間 (日数)。|  
|received_date|**datetime**|トポロジ要求を受信した時刻です。|  
|connection_info|**xml**|要求に応答したノードに関する情報。|  
  
## <a name="see-also"></a>関連項目  
 [レプリケーションテーブル &#40;Transact-sql&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
