---
title: SQL Server にインストールされている拡張ストアドプロシージャに対してクエリを実行する |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- extended stored procedures [SQL Server], querying
ms.assetid: e02348e6-dba6-438a-98b6-684244bb034d
author: rothja
ms.author: jroth
ms.openlocfilehash: 3f44db9053ad18c3a6902a30aaab4f81610c5a8c
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85050830"
---
# <a name="querying-extended-stored-procedures-installed-in-sql-server"></a>SQL Server にインストールされた拡張ストアド プロシージャの照会
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]代わりに CLR Integration をご使用ください。  
  
 認証されたユーザーは、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **sp_helpextendedproc**システムプロシージャを実行することによって、現在定義されている拡張ストアドプロシージャと、それぞれが属している DLL の名前を表示できます。 たとえば、次の例では、 **xp_hello**が属している DLL が返されます。  
  
```  
sp_helpextendedproc 'xp_hello'  
```  
  
 拡張ストアドプロシージャを指定せずに**sp_helpextendedproc**を実行すると、すべての拡張ストアドプロシージャとその dll が表示されます。  
  
> [!IMPORTANT]  
>  ログインしたユーザーが所有しているか、権限を持っている拡張ストアド プロシージャの情報だけが返されます。 すべての拡張ストアドプロシージャの情報を表示できるのは、 **sysadmin**固定サーバーロールのメンバーと、 **db_owner**、 **db_securityadmin**、および**db_ddladmin**の固定データベースロールのメンバーだけです。  
  
## <a name="see-also"></a>参照  
 [sp_helpextendedproc &#40;Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-helpextendedproc-transact-sql)   
 [sp_addextendedproc &#40;Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-addextendedproc-transact-sql)   
 [sp_dropextendedproc &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropextendedproc-transact-sql)  
  
  
