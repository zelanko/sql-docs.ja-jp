---
title: sp_changedistpublisher (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_changedistpublisher_TSQL
- sp_changedistpublisher
helpviewer_keywords:
- sp_changedistpublisher
ms.assetid: 7ef5c89d-faaa-4f8e-aef7-00649ebc8bc9
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 06a0e5e2edb793a94e8d8542ca17734f23824121
ms.sourcegitcommit: 2db83830514d23691b914466a314dfeb49094b3c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/27/2019
ms.locfileid: "58494025"
---
# <a name="spchangedistpublisher-transact-sql"></a>sp_changedistpublisher (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  ディストリビューション パブリッシャーのプロパティを変更します。 このストアド プロシージャは、ディストリビューターのすべてのデータベースで実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_changedistpublisher [ @publisher = ] 'publisher'  
    [ , [ @property = ] 'property' ]  
    [ , [ @value = ] 'value' ]  
    [ , [ @storage_connection_string = ] 'storage_connection_string']
```  
  
## <a name="arguments"></a>引数  
`[ @publisher = ] 'publisher'` パブリッシャーの名前です。 *パブリッシャー* は **sysname** 、既定値はありません。  
  
`[ @property = ] 'property'` 指定されたパブリッシャーを変更するプロパティです。 *プロパティ*は**sysname**これらの値のいずれかを指定できます。  
  
`[ @value = ] 'value'` 指定されたプロパティの値です。 *値*は**nvarchar (255)**、既定値は NULL です。  
  
`[ @storage_connection_string = ] 'storage_connection_string'` SQL Database マネージ インスタンスに必要なは、Azure SQL Database の記憶域ボリュームのアクセス キーが一致する必要があります。 


 > [!INCLUDE[Azure SQL Database link](../../includes/azure-sql-db-repl-for-more-information.md)]
 
 次の表に、パブリッシャーのプロパティと、それぞれの値を示します。  
  
|プロパティ|値|説明|  
|--------------|------------|-----------------|  
|**active**|**true**|パブリッシャーをアクティブにします。|  
||**false**|パブリッシャーを非アクティブ化します。|  
|**distribution_db**||ディストリビューション データベースの名前です。|  
|**login**||ログイン名です。|  
|**password**||指定したログインに対する複雑なパスワード。|  
|**security_mode**|**1**|パブリッシャーに接続するときに Windows 認証を使用。 *これ以外は変更できません*[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] *パブリッシャーです。*|  
||**0**|使用[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリッシャーに接続するときに認証します。 *これ以外は変更できません*[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] *パブリッシャーです。*|  
|**working_directory**||パブリケーションのデータおよびスキーマ ファイルを保存するために使用する作業ディレクトリです。|  
|NULL (既定値)||使用可能なすべて*プロパティ*オプションが出力されます。| 
|**storage_connection_string**| アクセス キー | データベースが Azure SQL Database マネージ インスタンスの場合は、作業ディレクトリのアクセス キー。 
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>コメント  
 **sp_changedistpublisher**はあらゆる種類のレプリケーションで使用します。  
  
## <a name="permissions"></a>アクセス許可  
 メンバーのみ、 **sysadmin**固定サーバー ロールが実行できる**sp_changedistpublisher**します。  
  
## <a name="see-also"></a>参照  
 [View and Modify Distributor and Publisher Properties (ディストリビューターとパブリッシャーのプロパティの表示および変更)](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)   
 [sp_adddistpublisher &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-adddistpublisher-transact-sql.md)   
 [sp_dropdistpublisher &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropdistpublisher-transact-sql.md)   
 [sp_helpdistpublisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpdistpublisher-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
