---
title: sp_dropserver (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 09/07/2018
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_dropserver_TSQL
- sp_dropserver
dev_langs:
- TSQL
helpviewer_keywords:
- sp_dropserver
ms.assetid: 0fc83e35-0caa-49a3-a4b6-a1890d4f46ef
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: 0155b154a1d63343c157bc2eca6e5cbd7c1b8968
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68124833"
---
# <a name="sp_dropserver-transact-sql"></a>sp_dropserver (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md.md)]

  
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のローカル インスタンスにある、既知のリモート サーバーおよびリンク サーバーの一覧からサーバーを削除します。  
  
 ![リンクアイコン](../../database-engine/configure-windows/media/topic-link.gif "[リンク] アイコン") [Transact-sql 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>構文  
  
```sql  
sp_dropserver [ @server = ] 'server'   
     [ , [ @droplogins = ] { 'droplogins' | NULL} ]  
```  
  
## <a name="arguments"></a>引数  
 *server*  
 削除するサーバーを指定します。 *サーバー*は**sysname**,、既定値はありません。 *サーバー*が存在している必要があります。  
  
 *droplogins*  
 **Droplogins**を指定した場合に、*サーバー*の関連するリモートサーバーおよびリンクサーバーログインも削除する必要があることを示します。 **`@droplogins`** の型は**char (10)** で、既定値は NULL です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="remarks"></a>解説  
 リモートおよびリンクサーバーのログインエントリが関連付けられているサーバーで**sp_dropserver**を実行した場合、またはレプリケーションパブリッシャーとして構成されている場合は、エラーメッセージが返されます。 サーバーを削除するときに、サーバーのすべてのリモートおよびリンクサーバーのログインを削除するには、 **droplogins**引数を使用します。  
  
 **sp_dropserver**は、ユーザー定義のトランザクション内では実行できません。  
  
## <a name="permissions"></a>アクセス許可  
 サーバーに対する ALTER ANY LINKED SERVER 権限が必要です。  
  
## <a name="examples"></a>例  
 次の例では、リモート サーバー `ACCOUNTS` とそれに関連するすべてのリモート ログインを、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のローカル インスタンスから削除します。  
  
```  
sp_dropserver 'ACCOUNTS', 'droplogins';  
```  
  
## <a name="see-also"></a>参照  
 [セキュリティストアドプロシージャ &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [sp_addserver &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-addserver-transact-sql.md)   
 [sp_dropremotelogin &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-dropremotelogin-transact-sql.md)   
 [sp_helpremotelogin &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-helpremotelogin-transact-sql.md)   
 [sp_helpserver &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-helpserver-transact-sql.md)   
 [システムストアドプロシージャ &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
