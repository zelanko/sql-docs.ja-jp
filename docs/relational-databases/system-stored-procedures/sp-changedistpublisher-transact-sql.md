---
title: sp_changedistpublisher (TRANSACT-SQL) |Microsoft ドキュメント
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
- sp_changedistpublisher_TSQL
- sp_changedistpublisher
helpviewer_keywords:
- sp_changedistpublisher
ms.assetid: 7ef5c89d-faaa-4f8e-aef7-00649ebc8bc9
caps.latest.revision: 36
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 601f09c7e04ac9515bf6aed297d27d8b5c4619e4
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="spchangedistpublisher-transact-sql"></a>sp_changedistpublisher (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  ディストリビューション パブリッシャーのプロパティを変更します。 このストアド プロシージャは、ディストリビューター側で任意のデータベースについて実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_changedistpublisher [ @publisher = ] 'publisher'  
    [ , [ @property = ] 'property' ]  
    [ , [ @value = ] 'value' ]  
```  
  
## <a name="arguments"></a>引数  
 [  **@publisher=** ] **'***パブリッシャー***'**  
 パブリッシャー名です。 *パブリッシャー*は**sysname**、既定値はありません。  
  
 [  **@property=** ] **'***プロパティ***'**  
 指定されたパブリッシャーの変更の対象となるプロパティです。 *プロパティ*は**sysname**これらの値のいずれかを指定できます。  
  
 [ **@value=** ] **'***value***'**  
 指定されたプロパティの値です。 *値*は**nvarchar (255)**、既定値は NULL です。  
  
 次の表に、パブリッシャーのプロパティと、それぞれの値を示します。  
  
|プロパティ|値|Description|  
|--------------|------------|-----------------|  
|**アクティブ**|**true**|パブリッシャーをアクティブ化します。|  
||**false**|パブリッシャーを非アクティブ化します。|  
|**distribution_db**||ディストリビューション データベースの名前です。|  
|**login**||ログイン名。|  
|**password**||指定したログインに対する複雑なパスワード。|  
|**security_mode**|**1**|パブリッシャーに接続するときに Windows 認証を使用。 *これ以外は変更できません*[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] *パブリッシャーです。*|  
||**0**|使用して[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリッシャーに接続するときに認証します。 *これ以外は変更できません*[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] *パブリッシャーです。*|  
|**working_directory**||パブリケーションのデータおよびスキーマ ファイルを保存するために使用する作業ディレクトリです。|  
|NULL (既定値)||使用可能なすべて*プロパティ*オプションが出力されます。|  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_changedistpublisher**はあらゆる種類のレプリケーションで使用します。  
  
## <a name="permissions"></a>権限  
 メンバーにのみ、 **sysadmin**固定サーバー ロールが実行できる**sp_changedistpublisher**です。  
  
## <a name="see-also"></a>参照  
 [View and Modify Distributor and Publisher Properties (ディストリビューターとパブリッシャーのプロパティの表示および変更)](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)   
 [sp_adddistpublisher &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-adddistpublisher-transact-sql.md)   
 [sp_dropdistpublisher &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropdistpublisher-transact-sql.md)   
 [sp_helpdistpublisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpdistpublisher-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
