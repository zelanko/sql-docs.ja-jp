---
title: sp_publisherproperty (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
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
- sp_publisherproperty
- sp_publisherproperty_TSQL
helpviewer_keywords:
- sp_publisherproperty
ms.assetid: 0ed1ebc1-a1bd-4aed-9f46-615c5cf07827
caps.latest.revision: 27
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 9648cb4a11317c23e776cc3e7c3c6f8412674153
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sppublisherproperty-transact-sql"></a>sp_publisherproperty (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  表示、またはパブリッシャーのプロパティの変更ではない[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリッシャーです。 このストアド プロシージャは、ディストリビューター側で実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_publisherproperty [ @publisher = ] 'publisher'   
   [ , [ @propertyname = ] 'propertyname' ]   
   [ , [ @propertyvalue = ] 'propertyvalue' ]  
```  
  
## <a name="arguments"></a>引数  
 [**@publisher** =] **'***パブリッシャー***'**  
 異種パブリッシャーの名前を指定します。 *パブリッシャー*は**sysname**、既定値はありません。  
  
 [**@propertyname** =] **'***propertyname***'**  
 設定するプロパティの名前を指定します。 *propertyname*は**sysname**値は次のいずれかを指定できます。  
  
|値|Description|  
|-----------|-----------------|  
|**xactsetbatching**|パブリッシャーのトランザクションが、後続の処理のために、トランザクション全体で一貫性のあるセット (Xactsets と呼ばれます) にまとめられるかどうかを示します。 値**有効になっている**Xactsets 作成できることを既定値であることを意味します。 値**無効になっている**ことがない新しい Xactsets 既存の Xactsets は処理手段が作成されます。|  
|**xactsetjob**|Xactsets を作成するために Xactset ジョブを有効にするかどうかを示します。 値**有効になっている**パブリッシャー側で Xactsets を作成する、Xactset ジョブが定期的に実行されることを意味します。 値**無効になっている**Xactsets がポーリングするときは、パブリッシャーの変更時に、ログ リーダー エージェントによってに作成しただけのことを意味します。|  
|**xactsetjobinterval**|Xactset ジョブの実行間隔 (分単位) です。|  
  
 ときに*propertyname*が省略されているすべての設定可能なプロパティが返されます。  
  
 [**@propertyvalue** =] **'***propertyvalue***'**  
 プロパティ設定の新しい値を指定します。 *propertyvalue*は**sysname**既定値は NULL です。 ときに*propertyvalue*を省略すると、現在の設定、プロパティが返されます。  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**propertyname**|**sysname**|設定可能な次のパブリケーション プロパティを返します。<br /><br /> **xactsetbatching**<br /><br /> **xactsetjob**<br /><br /> **xactsetjobinterval**|  
|**propertyvalue**|**sysname**|内のプロパティの現在の設定は、 **propertyname**列です。|  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_publisherproperty**のトランザクション レプリケーションで使用される非[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリッシャーです。  
  
 ときにのみ*パブリッシャー*を指定すると、結果セットには、設定可能なすべてのプロパティの現在の設定が含まれています。  
  
 ときに*propertyname*を指定すると、結果セットの名前付きのプロパティのみが表示されます。  
  
 すべてのパラメーターを指定した場合は、プロパティが変更され、結果セットは返されません。  
  
 変更するときに、 **xactsetjobinterval**実行中のジョブのプロパティは、新しい間隔を有効にするには、ジョブを再起動する必要があります。  
  
## <a name="permissions"></a>権限  
 メンバーにのみ、 **sysadmin** 、ディストリビューター側の固定サーバー ロールが実行できる**sp_publisherproperty**です。  
  
## <a name="see-also"></a>参照  
 [Oracle パブリッシャー用のトランザクション セット ジョブの構成 &#40;レプリケーション Transact-SQL プログラミング&#41;](../../relational-databases/replication/administration/configure-the-transaction-set-job-for-an-oracle-publisher.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
