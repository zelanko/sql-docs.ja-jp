---
title: sp_get_distributor (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
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
- sp_get_distributor
- sp_get_distributor_TSQL
helpviewer_keywords:
- sp_get_distributor
ms.assetid: f0134448-bc17-4f2f-bd81-619351ce56ac
caps.latest.revision: 34
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 1f4cd34760ff4bd447bc5a2621508629264adee1
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="spgetdistributor-transact-sql"></a>sp_get_distributor (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  ディストリビューターがサーバーにインストールされているかどうかを調べます。 このストアド プロシージャは、任意のデータベース上の、ディストリビューターを検索しているコンピューターで実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_get_distributor   
```  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**インストールされています。**|**int**|**0** = No です。**1** = [はい]|  
|**ディストリビューション サーバー**|**sysname**|ディストリビューター サーバーの名前。|  
|**ディストリビューション db がインストールされています。**|**int**|**0** = No です。**1** = [はい]|  
|**ディストリビューション パブリッシャーは、します。**|**int**|**0** = No です。**1** = [はい]|  
|**リモート ディストリビューション パブリッシャーします。**|**int**|**0** = No です。**1** = [はい]|  
  
## <a name="remarks"></a>解説  
 **sp_get_distributor**で主に使用される、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]スナップショット、トランザクション、およびマージ レプリケーションでします。  
  
## <a name="permissions"></a>権限  
 すべてのユーザーが実行できる**sp_get_distributor**です。 NULL 以外の結果セットが返されます場合、このストアド プロシージャがのメンバーによって実行される、 **db_owner**または**replmonitor**のメンバー、ディストリビューション データベースの固定データベース ロール、 **db_owner**に少なくとも 1 つのパブリッシュされたデータベースの固定データベース ロール。 NULL 以外の結果セットも返されるには、少なくともこのストアド プロシージャがのパブリケーション アクセス リスト (PAL) のユーザーによって実行されたときに 1 つのパブリッシュされたデータベース、またはディストリビューション データベースの SQL Server 以外のパブリッシャーの PAL でも実行できます**sp_get_distributor**です。  
  
## <a name="see-also"></a>参照  
 [パブリッシングとディストリビューションの構成](../../relational-databases/replication/configure-publishing-and-distribution.md)   
 [ディストリビューターおよびパブリッシャーの情報スクリプト](../../relational-databases/replication/administration/distributor-and-publisher-information-script.md)   
 [レプリケーション ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
