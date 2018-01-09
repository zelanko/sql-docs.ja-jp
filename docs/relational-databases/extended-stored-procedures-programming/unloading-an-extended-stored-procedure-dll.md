---
title: "ストアド プロシージャ DLL のアンロードの拡張 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: extended-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- extended stored procedures [SQL Server], unloading
- unloading extended stored procedures
ms.assetid: 4c75ab14-af54-4965-b376-8d75d385c941
caps.latest.revision: "33"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 31afe06af1285f2537a0712bdd8bd7d14e31e98f
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="unloading-an-extended-stored-procedure-dll"></a>拡張ストアド プロシージャ DLL のアンロード
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] 代わりに CLR Integration を使用してください。  
  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]呼び出しが DLL の関数のいずれかに加えられるとすぐに、拡張ストアド プロシージャ DLL を読み込みます。 DLL がロードされた状態は、サーバーがシャットダウンするか、DBCC ステートメントを使用してシステム管理者によってアンロードされるまで、維持されます。 たとえば、このコマンドのアンロード、 **xp_hello.dll**、システム管理者は、サーバーをシャット ダウンせずに、このファイルの新しいバージョンをディレクトリにコピーを許可します。  
  
```  
DBCC xp_hello(FREE)  
```  
  
## <a name="see-also"></a>参照  
 [DBCC dllname &#40;です。空き &#41;&#40;です。TRANSACT-SQL と #41 です。](../../t-sql/database-console-commands/dbcc-dllname-free-transact-sql.md)  
  
  
