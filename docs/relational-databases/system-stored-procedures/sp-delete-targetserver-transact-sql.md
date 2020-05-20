---
title: sp_delete_targetserver (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_delete_targetserver
- sp_delete_targetserver_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_delete_targetserver
ms.assetid: cc438701-ad91-419d-9f23-ebc4c548c700
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 0ccefc43c687c60d1dee030bf5f16a4b138224dd
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "82833297"
---
# <a name="sp_delete_targetserver-transact-sql"></a>sp_delete_targetserver (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  指定されたサーバーを使用可能な対象サーバーの一覧から削除します。  
   
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_delete_targetserver [ @server_name = ] 'server'   
     [ , [ @clear_downloadlist = ] clear_downloadlist ]  
     [ , [ @post_defection = ] post_defection ]  
```  
  
## <a name="arguments"></a>引数  
`[ @server_name = ] 'server'`使用可能な対象サーバーとして削除するサーバーの名前を指定します。 *サーバー*は**nvarchar (30)**,、既定値はありません。  
  
`[ @clear_downloadlist = ] clear_downloadlist`対象サーバーのダウンロードリストをクリアするかどうかを指定します。 *clear_downloadlist*の型は**bit**で、既定値は**1**です。 *Clear_downloadlist*が**1**の場合、サーバーを削除する前に、サーバーのダウンロード一覧がクリアされます。 *Clear_downloadlist*が**0**の場合、ダウンロードリストはクリアされません。  
  
`[ @post_defection = ] post_defection`対象サーバーに参加解除の命令を送信するかどうかを指定します。 *post_defection*の型は**bit**で、既定値は1です。 *Post_defection*が**1**の場合、サーバーを削除する前に、この手順によって対象サーバーに欠陥命令がポストされます。 *Post_defection*が**0**の場合、この手順では、対象サーバーに欠陥を通知しません。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="result-sets"></a>結果セット  
 なし  
  
## <a name="remarks"></a>解説  
 対象サーバーを削除する通常の方法は、対象サーバーで**sp_msx_defect**を呼び出すことです。 手動で参加解除する必要がある場合にのみ**sp_delete_targetserver**を使用します。  
  
## <a name="permissions"></a>アクセス許可  
 このストアドプロシージャを実行するには、 **sysadmin**固定サーバーロールがユーザーに付与されている必要があります。  
  
## <a name="examples"></a>使用例  
 次の例では、 `LONDON1` 使用可能なジョブサーバーからサーバーを削除します。  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_delete_targetserver  
  @server_name = N'LONDON1' ;  
GO  
```  
  
## <a name="see-also"></a>関連項目  
 [sp_help_targetserver &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-help-targetserver-transact-sql.md)   
 [sp_msx_defect &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-msx-defect-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
