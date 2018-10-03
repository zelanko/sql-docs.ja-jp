---
title: sp_replmonitorchangepublicationthreshold (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- sp_replmonitorchangepublicationthreshold_TSQL
- sp_replmonitorchangepublicationthreshold
helpviewer_keywords:
- sp_replmonitorchangepublicationthreshold
ms.assetid: 2c3615d8-4a1a-4162-b096-97aefe6ddc16
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 0bb8c060963f92ec14d140cf3b8649216fd89bf8
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47850580"
---
# <a name="spreplmonitorchangepublicationthreshold-transact-sql"></a>sp_replmonitorchangepublicationthreshold (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  パブリケーションの監視しきい値を変更します。 このストアド プロシージャはレプリケーションの監視に使用し、ディストリビューター側でディストリビューション データベースについて実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_replmonitorchangepublicationthreshold [ @publisher = ] 'publisher'  
        , [ @publisher_db = ] 'publisher_db'  
        , [ @publication = ] 'publication'   
    [ , [ @publication_type = ] publication_type ]   
    [ , [ @metric_id = ] metric_id ]   
    [ , [ @thresholdmetricname = ] 'thresholdmetricname'   
    [ , [ @value = ] value ]   
    [ , [ @shouldalert = ] shouldalert ]   
    [ , [ @mode = ] mode ]  
```  
  
## <a name="arguments"></a>引数  
 [ **@publisher** =] **'***パブリッシャー***'**  
 パブリッシャーの名前です。 *パブリッシャー*は**sysname**、既定値はありません。  
  
 [ **@publisher_db** =] **'***publisher_db***'**  
 パブリッシャー データベースの名前を指定します。 *publisher_db*は**sysname**、既定値はありません。  
  
 [ **@publication** =] **'***パブリケーション***'**  
 監視しきい値属性を変更するパブリケーションの名前を指定します。 *パブリケーション*は**sysname**、既定値はありません。  
  
 [ **@publication_type** =] *publication_type*  
 パブリケーションの種類を指定します。 *publication_type*は**int**、これらの値のいずれかを指定できます。  
  
|値|説明|  
|-----------|-----------------|  
|**0**|トランザクション パブリケーションです。|  
|**1**|スナップショット パブリケーションです。|  
|**2**|マージ パブリケーションです。|  
|NULL (既定値)|レプリケーションは、パブリケーションの種類を決定しようと試みます。|  
  
 [ **@metric_id** =] *metric_id*  
 変更するパブリケーションしきい値の ID を指定します。 *metric_id*は**int**既定値は NULL でこれらの値のいずれかを指定できます。  
  
|値|基準名|  
|-----------|-----------------|  
|**1**|**expiration** - トランザクション パブリケーションへのサブスクリプションに期限が迫っていないかを監視します。|  
|**2**|**latency** - トランザクション パブリケーションへのサブスクリプションのパフォーマンスを監視します。|  
|**4**|**mergeexpiration** - マージ パブリケーションへのサブスクリプションに期限が迫っていないかを監視します。|  
|**5**|**mergeslowrunduration** -低帯域 (ダイアル アップ) 接続でのマージ同期の期間を監視します。|  
|**6**|**mergefastrunduration** -高帯域幅ローカル エリア ネットワーク (LAN) 接続でのマージ同期の期間を監視します。|  
|**7**|**mergefastrunspeed** : 高帯域幅 (LAN) 接続経由でのマージ同期の同期速度を監視します。|  
|**8**|**mergeslowrunspeed** -低帯域 (ダイアル アップ) 接続でのマージ同期の同期率を監視します。|  
  
 いずれかを指定する必要があります*metric_id*または*thresholdmetricname*します。 場合*thresholdmetricname*が指定されると、 *metric_id*は NULL になります。  
  
 [ **@thresholdmetricname** =] **'***thresholdmetricname***'**  
 変更するパブリケーションしきい値の名前を指定します。 *thresholdmetricname*は**sysname**既定値は NULL です。 いずれかを指定する必要があります*thresholdmetricname*または*metric_id*します。 場合*metric_id*が指定されると、 *thresholdmetricname*は NULL になります。  
  
 [ **@value** =]*値*  
 パブリケーションしきい値の新しい値を指定します。 *値*は**int**既定値は NULL です。 場合**null**、メトリックの値は更新されません。  
  
 [ **@shouldalert** =] *shouldalert*  
 パブリケーションしきい値に達したときに警告を生成するかどうかを指定します。 *shouldalert*は**ビット**、既定値は NULL です。 値**1**アラートが生成されることを意味し、値**0**アラートが生成しないことを意味します。  
  
 [ **@mode** =]*モード*  
 パブリケーションしきい値を有効にするかどうかを指定します。 *モード*は**tinyint**、既定値は**1**します。 値**1**このメトリックの監視が有効であることを意味し、値**2**このメトリックの監視が無効になっていることを意味します。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>コメント  
 **sp_replmonitorchangepublicationthreshold**はあらゆる種類のレプリケーションで使用します。  
  
## <a name="permissions"></a>アクセス許可  
 メンバーのみ、 **db_owner**または**replmonitor**ディストリビューション データベースの固定データベース ロールが実行できる**sp_replmonitorchangepublicationthreshold**します。  
  
## <a name="see-also"></a>参照  
 [Programmatically Monitor Replication (プログラムによるレプリケーションの監視)](../../relational-databases/replication/monitor/programmatically-monitor-replication.md)  
  
  
