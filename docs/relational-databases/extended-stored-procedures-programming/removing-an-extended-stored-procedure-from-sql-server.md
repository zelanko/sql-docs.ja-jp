---
title: SQL Server からプロシージャが格納されている拡張を削除する |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
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
ms.openlocfilehash: f69de90386263df8b2be4638e257dcf58cf5dad7
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68064304"
---
# <a name="removing-an-extended-stored-procedure-from-sql-server"></a>SQL Server からの拡張ストアド プロシージャの削除
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] 代わりに CLR Integration を使用してください。  
  
 ユーザー定義拡張ストアド プロシージャ DLL では、各拡張ストアド プロシージャ関数を削除するには、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]システム管理者が実行する必要があります、 **sp_dropextendedproc**システム ストアド プロシージャの名前を指定します関数とその関数が存在する DLL の名前。 たとえば、このコマンドは、関数を削除します**xp_hello**から xp_hello.dll という名前の DLL に配置されている、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:。  
  
```  
sp_dropextendedproc 'xp_hello'  
```  
  
 以降で[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]、 **sp_dropextendedproc**システム拡張ストアド プロシージャを削除できません。 代わりに、システム管理者がする拡張ストアド プロシージャに対する EXECUTE 権限を拒否する必要があります、**パブリック**ロール。  
  
## <a name="see-also"></a>関連項目  
 [sp_dropextendedproc &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropextendedproc-transact-sql.md)  
  
  
