---
title: 削除する拡張からストアド プロシージャの SQL Server |Microsoft ドキュメント
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
- deleting extended stored procedures
- removing extended stored procedures
- extended stored procedures [SQL Server], removing
- dropping extended stored procedures
ms.assetid: 7827e574-3f59-4279-9a9b-532582e041cb
caps.latest.revision: 36
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: f1e60be2d8075c676a74539d8add407a2b7e8ab5
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36179317"
---
# <a name="removing-an-extended-stored-procedure-from-sql-server"></a>SQL Server からの拡張ストアド プロシージャの削除
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] 代わりに CLR Integration を使用してください。  
  
 ユーザー定義された拡張ストアド プロシージャの DLL、各拡張ストアド プロシージャ関数を削除する、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]システム管理者が実行する必要があります、 **sp_dropextendedproc**システム ストアド プロシージャの名前を指定します関数とその関数が存在する DLL の名前。 このコマンドで関数を削除するなど、 **xp_hello**から xp_hello.dll という名前の DLL 内にある[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
```  
sp_dropextendedproc 'xp_hello'  
```  
  
 以降で[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]、 **sp_dropextendedproc**もシステム拡張ストアド プロシージャは削除されません。 システム管理者が、拡張ストアド プロシージャに対する EXECUTE 権限を拒否する代わりに、**パブリック**ロール。  
  
## <a name="see-also"></a>参照  
 [sp_dropextendedproc &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropextendedproc-transact-sql)  
  
  
