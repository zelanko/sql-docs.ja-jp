---
title: sp_dropdevice (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_dropdevice_TSQL
- sp_dropdevice
dev_langs:
- TSQL
helpviewer_keywords:
- backup devices [SQL Server], deleting
- sp_dropdevice
ms.assetid: c8b07189-7c35-414b-acc1-45bd6e7e17c3
author: stevestein
ms.author: sstein
ms.openlocfilehash: 998794fd2e5fe5521587ebbb2a88c61c80cff39e
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "67927823"
---
# <a name="sp_dropdevice-transact-sql"></a>sp_dropdevice (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  のインスタンスからデータベースデバイスまたはバックアップデバイスを削除し[!INCLUDE[ssDEversion2005](../../includes/ssdeversion2005-md.md)]、 **master. dbo. sysdevices**からエントリを削除します。  
   
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_dropdevice [ @logicalname = ] 'device'   
    [ , [ @delfile = ] 'delfile' ]  
```  
  
## <a name="arguments"></a>引数  
`[ @logicalname = ] 'device'`**Master.dbo.sysdevices.name**に一覧表示されているデータベースデバイスまたはバックアップデバイスの論理名を指定します。 *デバイス*は**sysname**で、既定値はありません。  
  
`[ @delfile = ] 'delfile'`物理バックアップデバイスファイルを削除するかどうかを指定します。 *delfile*は**varchar (7)** です。 **Delfile**として指定した場合は、物理バックアップデバイスのディスクファイルが削除されます。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="result-sets"></a>結果セット  
 None  
  
## <a name="remarks"></a>Remarks  
 **sp_dropdevice**をトランザクション内で使用することはできません。  
  
## <a name="permissions"></a>アクセス許可  
 **diskadmin** 固定サーバー ロールのメンバーシップが必要です。  
  
## <a name="examples"></a>使用例  
 次の例では、テープ ダンプ デバイス `tapedump1` を[!INCLUDE[ssDE](../../includes/ssde-md.md)]から削除します。  
  
```  
EXEC sp_dropdevice 'tapedump1';  
```  
  
## <a name="see-also"></a>関連項目  
 [バックアップデバイス &#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-devices-sql-server.md)   
 [バックアップデバイス &#40;SQL Server を削除&#41;](../../relational-databases/backup-restore/delete-a-backup-device-sql-server.md)   
 [sp_addumpdevice &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql.md)   
 [sp_helpdb &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-helpdb-transact-sql.md)   
 [sp_helpdevice &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-helpdevice-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
