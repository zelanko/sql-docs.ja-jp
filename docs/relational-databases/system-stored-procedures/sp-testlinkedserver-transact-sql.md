---
title: sp_testlinkedserver (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_testlinkedserver
- sp_testlinkedserver_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_testlinkedserver
ms.assetid: e63ca7d4-47d6-455e-9aac-421f9683dadc
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 4f92be41bc657b562ad64da7e1093e64d1e6077a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47625620"
---
# <a name="sptestlinkedserver-transact-sql"></a>sp_testlinkedserver (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  リンク サーバーへの接続をテストします。 テストが成功しなかった場合は、例外が発生し、失敗の理由が示されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_testlinkedserver [ @servername ] = servername  
```  
  
## <a name="arguments"></a>引数  
 [  **@servername =** ]*servername*  
 リンク サーバー名です。 *servername*は**sysname**既定値はありません。  
  
## <a name="result-sets"></a>結果セット  
 なし  
  
## <a name="permissions"></a>アクセス許可  
 権限は確認されませんが、呼び出しには適切なログイン マッピングが必要です。  
  
## <a name="examples"></a>使用例  
 次の例では、というリンク サーバーを作成する`SEATTLESales`、および接続をテストします。  
  
```  
USE master;  
GO  
EXEC sp_addlinkedserver   
    'SEATTLESales',  
    N'SQL Server';  
GO  
sp_testlinkedserver SEATTLESales;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [sp_addlinkedserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md)   
 [sp_addlinkedsrvlogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addlinkedsrvlogin-transact-sql.md)  
  
  
