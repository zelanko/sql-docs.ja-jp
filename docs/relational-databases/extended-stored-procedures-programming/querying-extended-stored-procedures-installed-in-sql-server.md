---
title: 拡張ストアドプロシージャのクエリ
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- extended stored procedures [SQL Server], querying
ms.assetid: e02348e6-dba6-438a-98b6-684244bb034d
author: rothja
ms.author: jroth
ms.custom: seo-dt-2019
ms.openlocfilehash: 8413f071cfb36f5cad9130d3e2b56327d9b3bf45
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85758095"
---
# <a name="querying-extended-stored-procedures-installed-in-sql-server"></a>SQL Server にインストールされた拡張ストアド プロシージャの照会
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]代わりに CLR Integration をご使用ください。  
  
 認証されたユーザーは、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **sp_helpextendedproc**システムプロシージャを実行することによって、現在定義されている拡張ストアドプロシージャと、それぞれが属している DLL の名前を表示できます。 たとえば、次の例では、 **xp_hello**が属している DLL が返されます。  
  
```  
sp_helpextendedproc 'xp_hello'  
```  
  
 拡張ストアドプロシージャを指定せずに**sp_helpextendedproc**を実行すると、すべての拡張ストアドプロシージャとその dll が表示されます。  
  
> [!IMPORTANT]  
>  ログインしたユーザーが所有しているか、権限を持っている拡張ストアド プロシージャの情報だけが返されます。 すべての拡張ストアドプロシージャの情報を表示できるのは、 **sysadmin**固定サーバーロールのメンバーと、 **db_owner**、 **db_securityadmin**、および**db_ddladmin**の固定データベースロールのメンバーだけです。  
  
## <a name="see-also"></a>関連項目  
 [sp_helpextendedproc &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-helpextendedproc-transact-sql.md)   
 [sp_addextendedproc &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-addextendedproc-transact-sql.md)   
 [sp_dropextendedproc &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropextendedproc-transact-sql.md)  
  
  
