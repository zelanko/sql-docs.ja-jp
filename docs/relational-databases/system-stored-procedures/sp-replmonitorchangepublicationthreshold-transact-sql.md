---
title: sp_replmonitorchangepublicationthreshold (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
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
- sp_replmonitorchangepublicationthreshold_TSQL
- sp_replmonitorchangepublicationthreshold
helpviewer_keywords:
- sp_replmonitorchangepublicationthreshold
ms.assetid: 2c3615d8-4a1a-4162-b096-97aefe6ddc16
caps.latest.revision: 26
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 83006a7e001cdb787e82910780b0bdddda22b6c2
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
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
|**6**|**mergefastrunduration** -高帯域ローカル エリア ネットワーク (LAN) 接続でのマージ同期の期間を監視します。|  
|**7**|**mergefastrunspeed** : 高帯域幅 (LAN) 接続経由でのマージ同期の同期速度を監視します。|  
|**8**|**mergeslowrunspeed** -低帯域 (ダイアル アップ) 接続でのマージ同期の同期率を監視します。|  
  
 どちらかを指定する必要があります*metric_id*または*thresholdmetricname*です。 場合*thresholdmetricname*が指定すると、 *metric_id* NULL にする必要があります。  
  
 [ **@thresholdmetricname** =] **'***thresholdmetricname***'**  
 変更するパブリケーションしきい値の名前を指定します。 *thresholdmetricname*は**sysname**既定値は NULL です。 どちらかを指定する必要があります*thresholdmetricname*または*metric_id*です。 場合*metric_id*が指定すると、 *thresholdmetricname* NULL にする必要があります。  
  
 [ **@value** =]*値*  
 パブリケーションしきい値の新しい値を指定します。 *値*は**int**既定値は NULL です。 場合**null**、し、メトリックの値は更新されません。  
  
 [ **@shouldalert** =] *shouldalert*  
 パブリケーションしきい値に達したときに警告を生成するかどうかを指定します。 *shouldalert*は**ビット**、既定値は NULL です。 値**1**アラートを生成することを意味し、値は**0**アラートは生成されないことを意味します。  
  
 [ **@mode** =]*モード*  
 パブリケーションしきい値を有効にするかどうかを指定します。 *モード*は**tinyint**、既定値は**1**です。 値**1**このしきい値の監視が有効である、ことを意味し、値を**2**このしきい値の監視が無効になっていることを意味します。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_replmonitorchangepublicationthreshold**はあらゆる種類のレプリケーションで使用します。  
  
## <a name="permissions"></a>権限  
 メンバーにのみ、 **db_owner**または**replmonitor**ディストリビューション データベースの固定データベース ロールが実行できる**sp_replmonitorchangepublicationthreshold**です。  
  
## <a name="see-also"></a>参照  
 [Programmatically Monitor Replication (プログラムによるレプリケーションの監視)](../../relational-databases/replication/monitor/programmatically-monitor-replication.md)  
  
  
