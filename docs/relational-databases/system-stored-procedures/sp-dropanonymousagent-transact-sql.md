---
title: sp_dropanonymousagent (TRANSACT-SQL) |Microsoft ドキュメント
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
- sp_dropanonymousagent
- sp_dropanonymousagent_TSQL
helpviewer_keywords:
- sp_dropanonymousagent
ms.assetid: 4cb96efa-9358-44a3-a8ee-a7e181bed089
caps.latest.revision: 25
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 10b75c7c2e083a09dbebfc720487511397a1af90
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="spdropanonymousagent-transact-sql"></a>sp_dropanonymousagent (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  ディストリビューターにおけるレプリケーション モニター用の匿名エージェントをパブリッシャーから削除します。 このストアド プロシージャは、任意のデータベース上のパブリッシャー側で実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_dropanonymousagent [ @subid= ] sub_id    , [ @type= ] type  
```  
  
## <a name="arguments"></a>引数  
 [  **@subid=**] *sub_id*  
 匿名サブスクリプションのグローバル識別子を指定します。 *sub_id*は**uniqueidentifier**、既定値はありません。 この識別子は、サブスクライバーで取得できるを使用して**sp_helppullsubscription**です。 値、 **subid**返された結果セットのフィールドがこのグローバル識別子。  
  
 [  **@type=**]*型*  
 サブスクリプションの種類を指定します。 *型*は**int**、既定値はありません。 有効な値は**1**または**2**です。 指定**1**スナップショット レプリケーションまたはトランザクション レプリケーションのディストリビューション エージェントを使用する場合は、します。 指定**2**場合は、マージ レプリケーション マージ エージェントを使用します。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_dropanonymousagent**はあらゆる種類のレプリケーションで使用します。  
  
 このストアド プロシージャは、匿名サブスクリプション エージェントを削除するときのみ使用します。このストアド プロシージャを使用して、既知のサブスクリプションを削除することはできません。  
  
## <a name="permissions"></a>権限  
 メンバーにのみ、 **db_owner**ディストリビューション データベースの固定データベース ロールが実行できる**sp_dropanonymousagent**です。  
  
## <a name="see-also"></a>参照  
 [レプリケーション ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
