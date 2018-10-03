---
title: SQL Server からプロシージャが格納されている拡張を削除する |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
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
ms.openlocfilehash: 19149de4fb5a0e62886006b620375bda5b25c9b2
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48227802"
---
# <a name="removing-an-extended-stored-procedure-from-sql-server"></a>SQL Server からの拡張ストアド プロシージャの削除
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] 代わりに CLR Integration を使用してください。  
  
 ユーザー定義拡張ストアド プロシージャ DLL では、各拡張ストアド プロシージャ関数を削除するには、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]システム管理者が実行する必要があります、 **sp_dropextendedproc**システム ストアド プロシージャの名前を指定します関数とその関数が存在する DLL の名前。 たとえば、このコマンドは、関数を削除します**xp_hello**から xp_hello.dll という名前の DLL に配置されている、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:。  
  
```  
sp_dropextendedproc 'xp_hello'  
```  
  
 以降で[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]、 **sp_dropextendedproc**システム拡張ストアド プロシージャを削除できません。 代わりに、システム管理者がする拡張ストアド プロシージャに対する EXECUTE 権限を拒否する必要があります、**パブリック**ロール。  
  
## <a name="see-also"></a>参照  
 [sp_dropextendedproc &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropextendedproc-transact-sql)  
  
  
