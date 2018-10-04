---
title: sp_publisherproperty (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- sp_publisherproperty
- sp_publisherproperty_TSQL
helpviewer_keywords:
- sp_publisherproperty
ms.assetid: 0ed1ebc1-a1bd-4aed-9f46-615c5cf07827
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 002e8a5ffc7a619aeda3e8372e30631e96fa9d30
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47679430"
---
# <a name="sppublisherproperty-transact-sql"></a>sp_publisherproperty (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  表示、またはパブリッシャーのプロパティの変更以外[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリッシャーです。 このストアド プロシージャは、ディストリビューター側で実行されます。  
  
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
  
|値|説明|  
|-----------|-----------------|  
|**xactsetbatching**|パブリッシャーのトランザクションが、後続の処理のために、トランザクション全体で一貫性のあるセット (Xactsets と呼ばれます) にまとめられるかどうかを示します。 値**有効になっている**Xactsets を作成できること、既定値であることを意味します。 値**無効になっている**ない新しい Xactsets 既存の Xactsets は処理する手段が作成されます。|  
|**xactsetjob**|Xactsets を作成するために Xactset ジョブを有効にするかどうかを示します。 値**有効になっている**パブリッシャー側で Xactsets を作成する Xactset ジョブが定期的に実行されることを意味します。 値**無効になっている**Xactsets がポーリングするときは、パブリッシャーの変更時に、ログ リーダー エージェントによってに作成しただけのことを意味します。|  
|**xactsetjobinterval**|Xactset ジョブの実行間隔 (分単位) です。|  
  
 ときに*propertyname*を省略するとすべての設定可能なプロパティが返されます。  
  
 [**@propertyvalue** =] **'***propertyvalue***'**  
 プロパティ設定の新しい値を指定します。 *propertyvalue*は**sysname**既定値は NULL です。 ときに*propertyvalue*を省略すると、現在の設定、プロパティが返されます。  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**propertyname**|**sysname**|設定可能な次のパブリケーション プロパティを返します。<br /><br /> **xactsetbatching**<br /><br /> **xactsetjob**<br /><br /> **xactsetjobinterval**|  
|**propertyvalue**|**sysname**|内のプロパティの現在の設定は、 **propertyname**列。|  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>コメント  
 **sp_publisherproperty**のトランザクション レプリケーションで使用が非[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリッシャー。  
  
 のみ*パブリッシャー*を指定すると、結果セットに設定できるすべてのプロパティの現在の設定が含まれています。  
  
 ときに*propertyname*を指定すると、結果セットの名前付きのプロパティのみが表示されます。  
  
 すべてのパラメーターを指定した場合は、プロパティが変更され、結果セットは返されません。  
  
 変更するときに、 **xactsetjobinterval**実行中のジョブのプロパティと新しい間隔を有効にするジョブを再起動する必要があります。  
  
## <a name="permissions"></a>アクセス許可  
 メンバーのみ、 **sysadmin** 、ディストリビューター側の固定サーバー ロールが実行できる**sp_publisherproperty**します。  
  
## <a name="see-also"></a>参照  
 [Oracle パブリッシャー用のトランザクション セット ジョブの構成 &#40;レプリケーション Transact-SQL プログラミング&#41;](../../relational-databases/replication/administration/configure-the-transaction-set-job-for-an-oracle-publisher.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
