---
title: sp_get_distributor (TRANSACT-SQL) |Microsoft Docs
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
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 088b2d2c6e334d48fae3e9257f76c5fd8129c15d
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "43021291"
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
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**インストールされています。**|**int**|**0** = はありません。**1** = [はい]|  
|**ディストリビューション サーバー**|**sysname**|ディストリビューター サーバーの名前。|  
|**ディストリビューション db がインストールされています。**|**int**|**0** = はありません。**1** = [はい]|  
|**ディストリビューション パブリッシャーは、します。**|**int**|**0** = はありません。**1** = [はい]|  
|**リモート ディストリビューション パブリッシャーがあります。**|**int**|**0** = はありません。**1** = [はい]|  
  
## <a name="remarks"></a>コメント  
 **sp_get_distributor**で主に使用される、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]スナップショット、トランザクション、およびマージ レプリケーションでします。  
  
## <a name="permissions"></a>アクセス許可  
 すべてのユーザーが実行できる**sp_get_distributor**します。 NULL 以外の結果セットが返されます場合、このストアド プロシージャがのメンバーによって実行される、 **db_owner**または**replmonitor**固定データベース ロールのメンバー、ディストリビューション データベース、 **db_owner**に少なくとも 1 つのパブリッシュされたデータベースの固定データベース ロール。 NULL 以外の結果セットもときに返されるこのストアド プロシージャの実行のパブリケーション アクセス リスト (PAL) 内のユーザーが少なくとも 1 つのパブリッシュされたデータベース、またはディストリビューション データベースの SQL Server 以外のパブリッシャーの PAL でを実行できますも**sp_get_distributor**します。  
  
## <a name="see-also"></a>参照  
 [パブリッシングとディストリビューションの構成](../../relational-databases/replication/configure-publishing-and-distribution.md)   
 [ディストリビューターおよびパブリッシャーの情報スクリプト](../../relational-databases/replication/administration/distributor-and-publisher-information-script.md)   
 [レプリケーション ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
