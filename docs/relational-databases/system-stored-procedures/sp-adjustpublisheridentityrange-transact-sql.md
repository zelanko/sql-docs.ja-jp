---
title: sp_adjustpublisheridentityrange (TRANSACT-SQL) |Microsoft ドキュメント
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
- sp_adjustpublisheridentityrange_TSQL
- sp_adjustpublisheridentityrange
helpviewer_keywords:
- sp_adjustpublisheridentityrange
ms.assetid: 64f111fd-fb7d-4459-93f7-65f0f8dd7efe
caps.latest.revision: 28
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: e8d39485c2ed9519353a2175fa4e127a5900b0e0
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="spadjustpublisheridentityrange-transact-sql"></a>sp_adjustpublisheridentityrange (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  パブリケーションの ID 範囲を調整し、パブリケーションのしきい値に基づいて新しい範囲を再割り当てします。 このストアド プロシージャは、パブリッシャー側でパブリケーション データベースについて実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_adjustpublisheridentityrange [ [ @publication = ] 'publication' ]  
    [ , [ @table_name = ] 'table_name' ]  
    [ , [ @table_owner= ] 'table_owner' ]  
```  
  
## <a name="arguments"></a>引数  
 [ **@publication=**] **'***publication***'**  
 新しい ID 範囲が再割り当てされるパブリケーションの名前を指定します。 *パブリケーション*は**sysname**、既定値は NULL です。  
  
 [ **@table_name=**] **'***table_name***'**  
 新しい ID 範囲が再割り当てされるテーブルの名前を指定します。 *table_name*は**sysname**、既定値は NULL です。  
  
 [ **@table_owner=**] **'***table_owner***'**  
 パブリッシャーのテーブルの所有者を指定します。 *table_owner*は**sysname**、既定値は NULL です。 場合*table_owner*が指定されていない、現在のユーザーの名前を使用します。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_adjustpublisheridentityrange**はあらゆる種類のレプリケーションで使用します。  
  
 自動 ID 範囲が有効になっているパブリケーションの場合は、ディストリビューション エージェントまたはマージ エージェントが、パブリケーションのしきい値に基づいてパブリケーションの ID 範囲を自動的に調整します。 ただし、何らかの理由により、ディストリビューション エージェントまたはマージ エージェントが実行されていない時間の期間の範囲の id のリソースが大量に消費されて、ポイントのしきい値の場合は、ユーザーが呼び出せる**sp_adjustpublisheridentityrange**パブリッシャーを新しい範囲の値を割り当てられません。  
  
 実行時に**sp_adjustpublisheridentityrange**か、*パブリケーション*または*table_name*指定する必要があります。 両方を指定した場合、または両方とも指定しなかった場合は、エラーが返されます。  
  
## <a name="permissions"></a>権限  
 メンバーにのみ、 **sysadmin**固定サーバー ロールまたは**db_owner**固定データベース ロールが実行できる**sp_adjustpublisheridentityrange**です。  
  
## <a name="see-also"></a>参照  
 [Id 列をレプリケートします。](../../relational-databases/replication/publish/replicate-identity-columns.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
