---
title: ストアド プロシージャ DLL のアンロードの拡張 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- extended stored procedures [SQL Server], unloading
- unloading extended stored procedures
ms.assetid: 4c75ab14-af54-4965-b376-8d75d385c941
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 148a94bc0413a7fa2a7320599a612b0dcb09d5a6
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48207958"
---
# <a name="unloading-an-extended-stored-procedure-dll"></a>拡張ストアド プロシージャ DLL のアンロード
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] 代わりに CLR Integration を使用してください。  
  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] DLL の関数のいずれかに呼び出しが行われるとすぐには、拡張ストアド プロシージャ DLL を読み込みます。 DLL がロードされた状態は、サーバーがシャットダウンするか、DBCC ステートメントを使用してシステム管理者によってアンロードされるまで、維持されます。 たとえば、このコマンドのアンロード、 **xp_hello.dll**、システム管理者は、サーバーをシャット ダウンせずに、このファイルの新しいバージョンをディレクトリにコピーすることができます。  
  
```  
DBCC xp_hello(FREE)  
```  
  
## <a name="see-also"></a>参照  
 [DBCC dllname &#40;FREE&#41; &#40;TRANSACT-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-dllname-free-transact-sql)  
  
  
