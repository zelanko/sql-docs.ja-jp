---
title: クエリを実行する SQL Server にインストールされているストアド プロシージャを拡張 |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- extended stored procedures [SQL Server], querying
ms.assetid: e02348e6-dba6-438a-98b6-684244bb034d
caps.latest.revision: 30
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 25e9b8d1de6acd52182e090f40d955cc17bf5cd1
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36177303"
---
# <a name="querying-extended-stored-procedures-installed-in-sql-server"></a>SQL Server にインストールされた拡張ストアド プロシージャの照会
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]代わりに CLR Integration をご使用ください。  
  
 A [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]認証されたユーザーを表示できる現在定義されている拡張ストアド プロシージャとを実行している各 DLL の名前が属している、 **sp_helpextendedproc**システム プロシージャです。 たとえば、次の例がする DLL を返します**xp_hello**が属しています。  
  
```  
sp_helpextendedproc 'xp_hello'  
```  
  
 場合**sp_helpextendedproc**拡張ストアド プロシージャ、すべての拡張ストアド プロシージャが Dll が表示されるかを指定せずを実行します。  
  
> [!IMPORTANT]  
>  ログインしたユーザーが所有しているか、権限を持っている拡張ストアド プロシージャの情報だけが返されます。 メンバーにのみ、 **sysadmin**固定サーバー ロールおよび**db_owner**、 **db_securityadmin**、および**db_ddladmin**固定データベースロールは、すべての拡張ストアド プロシージャの情報を表示できます。  
  
## <a name="see-also"></a>参照  
 [sp_helpextendedproc &#40;TRANSACT-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpextendedproc-transact-sql)   
 [sp_addextendedproc &#40;TRANSACT-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addextendedproc-transact-sql)   
 [sp_dropextendedproc &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropextendedproc-transact-sql)  
  
  
