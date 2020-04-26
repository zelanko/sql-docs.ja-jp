---
title: SQL Server | から拡張ストアドプロシージャを削除するMicrosoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- deleting extended stored procedures
- removing extended stored procedures
- extended stored procedures [SQL Server], removing
- dropping extended stored procedures
ms.assetid: 7827e574-3f59-4279-9a9b-532582e041cb
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: bcb58ac180861641803147d1dfea621bd52df9a6
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/25/2020
ms.locfileid: "62512027"
---
# <a name="removing-an-extended-stored-procedure-from-sql-server"></a>SQL Server からの拡張ストアド プロシージャの削除
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] 代わりに CLR Integration を使用してください。  
  
 ユーザー定義の拡張ストアドプロシージャ DLL 内の各拡張ストアドプロシージャ関数を削除するに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]は、システム管理者が**sp_dropextendedproc**システムストアドプロシージャを実行して、関数の名前とその関数が存在する DLL の名前を指定する必要があります。 たとえば、次のコマンドは、xp_hello という DLL にある関数**xp_hello**をから[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]削除します。  
  
```  
sp_dropextendedproc 'xp_hello'  
```  
  
 以降で[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]は、 **sp_dropextendedproc**システムの拡張ストアドプロシージャは削除されません。 代わりに、システム管理者は、拡張ストアドプロシージャに対する EXECUTE 権限を**public**ロールに対して拒否する必要があります。  
  
## <a name="see-also"></a>参照  
 [sp_dropextendedproc &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropextendedproc-transact-sql)  
  
  
