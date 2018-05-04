---
title: sp_replmonitorhelpmergesessiondetail (TRANSACT-SQL) |Microsoft ドキュメント
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
- sp_replmonitorhelpmergesessiondetail
- sp_replmonitorhelpmergesessiondetail_TSQL
helpviewer_keywords:
- sp_replmonitorhelpmergesessiondetail
ms.assetid: 805c92fc-3169-410c-984d-f37e063b791d
caps.latest.revision: 16
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 44bb40f02a7e8f537141f34db3bf4cc38c8b093f
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="spreplmonitorhelpmergesessiondetail-transact-sql"></a>sp_replmonitorhelpmergesessiondetail (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  マージ レプリケーションの監視に使用する特定のレプリケーション マージ エージェント セッションに関するアーティクル レベルの詳細情報を返します。 結果セットには、セッション中に同期された各アーティクルの詳細行が含まれます。 また、セッションの初期化を表す行や、セッションのアップロードおよびダウンロード フェーズの両方を要約した行も含まれます。 このストアド プロシージャは、ディストリビューター側でディストリビューション データベースについて実行されます。または、サブスクライバー側でサブスクリプション データベースについて実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_replmonitorhelpmergesessiondetail [ @session_id = ] session_id  
```  
  
## <a name="arguments"></a>引数  
 [ **@session_id** =] *session_id*  
 エージェント セッションを指定します。 *session_id*は**int**既定値はありません。  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**PhaseID**|**int**|同期セッションのフェーズです。次のいずれかの値をとります。<br /><br /> **0** = 初期化または概要の行<br /><br /> **1**アップロードを =<br /><br /> **2** = ダウンロード|  
|**ArticleName**|**sysname**|同期されているアーティクルの名前です。 **ArticleName**アーティクルの詳細を表さない結果セット内の行の概要情報も含まれます。|  
|**PercentComplete**|**decimal**|現在実行中のセッションまたは失敗したセッションに関する特定のアーティクル詳細行で適用された合計変更のパーセントを示します。|  
|**RelativeCost**|**decimal**|アーティクルの同期にかかる時間を、セッションの総同期時間のパーセンテージで示します。|  
|**Duration**|**int**|エージェント セッションの長さです。|  
|**Inserts**|**int**|セッションでの挿入の数です。|  
|**Updates**|**int**|セッションにおける更新数です。|  
|**Deletes**|**int**|セッションにおける削除数です。|  
|**競合**|**int**|セッションで発生した競合の数です。|  
|**ErrorID**|**int**|セッション エラーの ID です。|  
|**SeqNo**|**int**|結果セット内のセッションの順序です。|  
|**RowType**|**int**|結果セット内の各行が表す情報の種類を示します。<br /><br /> **0**初期化を =<br /><br /> **1** = アップロードの概要<br /><br /> **2** = アーティクルのアップロードの詳細<br /><br /> **3** = ダウンロードの概要<br /><br /> **4** = アーティクルのダウンロードの詳細|  
|**スキーマ変更**|**int**|セッションでのスキーマ変更の数です。|  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_replmonitorhelpmergesessiondetail**はマージ レプリケーションの監視に使用します。  
  
 サブスクライバーで実行されたときに**sp_replmonitorhelpmergesessiondetail**最後の 5 のマージ エージェント セッションに関する詳細な情報だけを返します。  
  
## <a name="permissions"></a>権限  
 メンバーにのみ、 **db_owner**または**replmonitor** 、ディストリビューターのディストリビューション データベースまたはサブスクライバー側でサブスクリプション データベースの固定データベース ロールが実行できる**sp _replmonitorhelpmergesessiondetail**です。  
  
## <a name="see-also"></a>参照  
 [Programmatically Monitor Replication (プログラムによるレプリケーションの監視)](../../relational-databases/replication/monitor/programmatically-monitor-replication.md)  
  
  
