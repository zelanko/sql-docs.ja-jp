---
title: sp_replmonitorhelpmergesessiondetail (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_replmonitorhelpmergesessiondetail
- sp_replmonitorhelpmergesessiondetail_TSQL
helpviewer_keywords:
- sp_replmonitorhelpmergesessiondetail
ms.assetid: 805c92fc-3169-410c-984d-f37e063b791d
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: dbafa8dd407269fa23ca37574f18a12be519c448
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/27/2019
ms.locfileid: "58534635"
---
# <a name="spreplmonitorhelpmergesessiondetail-transact-sql"></a>sp_replmonitorhelpmergesessiondetail (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  マージ レプリケーションの監視に使用する特定のレプリケーション マージ エージェント セッションに関するアーティクル レベルの詳細情報を返します。 結果セットには、セッション中に同期された各アーティクルの詳細行が含まれます。 また、セッションの初期化を表す行や、セッションのアップロードおよびダウンロード フェーズの両方を要約した行も含まれます。 このストアド プロシージャは、ディストリビューター、ディストリビューション データベースまたはサブスクライバーのサブスクリプション データベースで実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_replmonitorhelpmergesessiondetail [ @session_id = ] session_id  
```  
  
## <a name="arguments"></a>引数  
`[ @session_id = ] session_id` エージェント セッションを指定します。 *session_id*は**int**既定値はありません。  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**PhaseID**|**int**|同期セッションのフェーズです。次のいずれかの値をとります。<br /><br /> **0**初期化または概要の行を =<br /><br /> **1** = アップロード<br /><br /> **2** = ダウンロード|  
|**ArticleName**|**sysname**|同期されているアーティクルの名前。 **ArticleName**をアーティクルの詳細を表さない結果セット内の行のサマリー情報も含まれます。|  
|**PercentComplete**|**decimal**|現在実行中のセッションまたは失敗したセッションに関する特定のアーティクル詳細行で適用された合計変更のパーセントを示します。|  
|**RelativeCost**|**decimal**|時刻を示します、セッションの総同期時間の割合として、アーティクルの同期にかかります。|  
|**Duration**|**int**|エージェント セッションの長さです。|  
|**Inserts**|**int**|セッションでの挿入の数。|  
|**Updates**|**int**|セッションにおける更新数です。|  
|**Deletes**|**int**|セッションにおける削除数です。|  
|**競合**|**int**|セッションで発生した競合の数。|  
|**ErrorID**|**int**|セッション エラーの ID。|  
|**SeqNo**|**int**|結果セット内のセッションの順序です。|  
|**RowType**|**int**|結果セット内の各行が表す情報の種類を示します。<br /><br /> **0** = 初期化<br /><br /> **1** = アップロードの概要<br /><br /> **2** = アーティクルのアップロードの詳細<br /><br /> **3** = ダウンロードの概要<br /><br /> **4** = アーティクルのダウンロードの詳細|  
|**スキーマ変更**|**int**|セッションでスキーマ変更の数。|  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>コメント  
 **sp_replmonitorhelpmergesessiondetail**マージ レプリケーションを監視するために使用します。  
  
 サブスクライバーで実行されたときに**sp_replmonitorhelpmergesessiondetail**最後の 5 のマージ エージェント セッションに関する詳細な情報だけを返します。  
  
## <a name="permissions"></a>アクセス許可  
 メンバーのみ、 **db_owner**または**replmonitor**ディストリビューターでディストリビューション データベースまたはサブスクライバー側でサブスクリプション データベースの固定データベース ロールが実行できる**sp _replmonitorhelpmergesessiondetail**します。  
  
## <a name="see-also"></a>参照  
 [Programmatically Monitor Replication (プログラムによるレプリケーションの監視)](../../relational-databases/replication/monitor/programmatically-monitor-replication.md)  
  
  
