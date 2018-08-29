---
title: sp_replmonitorhelppublicationthresholds (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_replmonitorhelppublicationthresholds
- sp_replmonitorhelppublicationthresholds_TSQL
helpviewer_keywords:
- sp_replmonitorhelppublicationthresholds
ms.assetid: d6b1aa4b-3369-4255-a892-c0e5cc9cb693
caps.latest.revision: 21
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d87de8d4ab74bc5c9d776b9d08e9e0680e2530cd
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "43032240"
---
# <a name="spreplmonitorhelppublicationthresholds-transact-sql"></a>sp_replmonitorhelppublicationthresholds (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  監視対象のパブリケーションに対するしきい値の測定基準セットを返します。 このストアド プロシージャはレプリケーションの監視に使用し、ディストリビューター側でディストリビューション データベースについて実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_replmonitorhelppublicationthresholds [ @publisher = ] 'publisher'  
        , [ @publisher_db = ] 'publisher_db'  
        , [ @publication = ] 'publication'   
    [ , [ @publication_type = ] publication_type ]   
    [ , [ @thresholdmetricname = ] 'thresholdmetricname'  
```  
  
## <a name="arguments"></a>引数  
 [ **@publisher**=] **'***パブリッシャー***'**  
 パブリッシャーの名前です。 *パブリッシャー*は**sysname**、既定値はありません。  
  
 [ **@publisher_db**=] **'***publisher_db***'**  
 パブリッシャー データベースの名前を指定します。 *publisher_db*は**sysname**、既定値はありません。  
  
 [ **@publication**=] **'***パブリケーション***'**  
 パブリケーションの名前です。 *パブリケーション*は**sysname**、既定値はありません。  
  
 [ **@publication_type**=] *publication_type*  
 パブリケーションの種類を指定します。 *publication_type*は**int**、これらの値のいずれかを指定できます。  
  
|値|説明|  
|-----------|-----------------|  
|**0**|トランザクション パブリケーションです。|  
|**1**|スナップショット パブリケーションです。|  
|**2**|マージ パブリケーションです。|  
|NULL (既定値)|レプリケーションでは、パブリケーションの種類の判別が試行されます。|  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**metric_id**|**int**|レプリケーション パフォーマンス測定基準の ID。次のいずれかになります。<br /><br /> **1expiration** -トランザクション パブリケーションに対するサブスクリプションの期限が迫っていないか監視します。<br /><br /> **2latency** -トランザクション パブリケーションに対するサブスクリプションのパフォーマンスを監視します。<br /><br /> **4mergeexpiration** -マージ パブリケーションへのサブスクリプションが迫っていないか有効期限を監視します。<br /><br /> **5mergeslowrunduration** -低帯域 (ダイアル アップ) 接続でのマージ同期の期間を監視します。<br /><br /> **6mergefastrunduration** -高帯域 (LAN) 接続でのマージ同期の期間を監視します。<br /><br /> **7mergefastrunspeed** -高帯域 (LAN) 接続でのマージ同期の同期率を監視します。<br /><br /> **8mergeslowrunspeed** -低帯域 (ダイアル アップ) 接続でのマージ同期の同期率を監視します。|  
|**title**|**sysname**|レプリケーション パフォーマンス測定基準の名前。|  
|**value**|**int**|パフォーマンス測定単位のしきい値。|  
|**shouldalert**|**bit**|メトリックがこのパブリケーションに定義されたしきい値を超えた場合にアラートを生成するかどうかは、します。値**1**アラートを発生させることを示します。|  
|**isenabled**|**bit**|このパブリケーションのこのレプリケーションのパフォーマンス メトリックの監視が有効になっているかどうかは、します。値**1**監視が有効になっていることを示します。|  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>コメント  
 **sp_replmonitorhelppublicationthresholds**はあらゆる種類のレプリケーションで使用します。  
  
## <a name="permissions"></a>アクセス許可  
 メンバーのみ、 **db_owner**または**replmonitor** 、ディストリビューション データベースの固定データベース ロールが実行できる**sp_replmonitorhelppublicationthresholds**します。  
  
## <a name="see-also"></a>参照  
 [Programmatically Monitor Replication (プログラムによるレプリケーションの監視)](../../relational-databases/replication/monitor/programmatically-monitor-replication.md)  
  
  
