---
title: sp_replmonitorhelppublisher (TRANSACT-SQL) |Microsoft ドキュメント
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
- sp_replmonitorhelppublisher_TSQL
- sp_replmonitorhelppublisher
helpviewer_keywords:
- sp_replmonitorhelppublisher
ms.assetid: 171501fe-4b74-4647-96c3-7691c777e01b
caps.latest.revision: 27
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: eba8e8226f0e1b12210be07568e7a5fc1126522f
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32999549"
---
# <a name="spreplmonitorhelppublisher-transact-sql"></a>sp_replmonitorhelppublisher (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  ディストリビューターに関連付けられた 1 つ以上のパブリッシャーに関する現在の状態情報を返します。 このストアド プロシージャはレプリケーションの監視に使用し、ディストリビューター側でディストリビューション データベースについて実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_replmonitorhelppublisher [ [ @publisher = ] 'publisher' ]  
    [ , [ @refreshpolicy = ] refreshpolicy ]  
```  
  
## <a name="arguments"></a>引数  
 [ **@publisher** =] **'***パブリッシャー***'**  
 状態を監視しているパブリッシャーの名前を指定します。 *パブリッシャー*は**sysname**既定値は NULL です。 NULL の場合、ディストリビューターを使用するすべてのパブリッシャーに対して情報が返されます。  
  
 [  **@refreshpolicy=** ] *refreshpolicy*  
 内部使用のみです。  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**パブリッシャー**|**sysname**|パブリッシャーの名前です。|  
|**distribution_db**|**sysname**|指定されたパブリッシャーによって使用されるディストリビューション データベースの名前です。|  
|**ステータス**|**int**|このパブリッシャー側のパブリケーションに関連付けられているすべてのレプリケーション エージェントの最大の状態です。次のいずれかの値をとります。<br /><br /> **1** = 開始<br /><br /> **2** = に成功しました<br /><br /> **3** = 実行中<br /><br /> **4** = アイドル状態<br /><br /> **5** = 再試行<br /><br /> **6** = に失敗しました|  
|**警告**|**int**|このパブリッシャー側のパブリケーションに属しているサブスクリプションによって生成される最大しきい値警告です。次の 1 つ以上の値の論理和になります。<br /><br /> **1** = expiration: トランザクション パブリケーションに対するサブスクリプションが、保有期間のしきい値内で同期されていません。<br /><br /> **2** = 待機時間、トランザクション パブリッシャーからサブスクライバーにデータをレプリケートにかかった時間 (秒) がしきい値を超えています。<br /><br /> **4** = mergeexpiration 保有期間のしきい値内で、マージ パブリケーションに対するサブスクリプションが同期されていません。<br /><br /> **8** = mergefastrunduration - マージ サブスクリプションの同期の完了にかかった時間のしきい値を超過、秒単位で高速ネットワーク接続します。<br /><br /> **16** = mergeslowrunduration - マージ サブスクリプションの同期の完了にかかった時間低速またはダイヤルアップ ネットワーク接続経由で (秒単位) がしきい値を超えています。<br /><br /> **32** = mergefastrunspeed 配信率、マージ サブスクリプションの同期中の行は、高速ネットワーク接続経由でのしきい値の割合を 1 秒あたりの行を維持するために失敗しました。<br /><br /> **64** = mergeslowrunspeed 配信率、マージ サブスクリプションの同期中の行が低速またはダイヤルアップ ネットワーク接続経由でのしきい値の割合を 1 秒あたりの行を維持するために失敗しました。|  
|**publicationcount**|**int**|パブリッシャーに属しているパブリケーションの数です。|  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_replmonitorhelppublisher**はあらゆる種類のレプリケーションで使用します。  
  
## <a name="permissions"></a>権限  
 メンバーにのみ、 **sysadmin**のメンバー、またはディストリビューターの固定サーバー ロール、 **db_owner**または**replmonitor**ディストリビューション データベースの固定データベース ロールのことができます実行**sp_replmonitorhelppublisher**です。  
  
## <a name="see-also"></a>参照  
 [Programmatically Monitor Replication (プログラムによるレプリケーションの監視)](../../relational-databases/replication/monitor/programmatically-monitor-replication.md)  
  
  
