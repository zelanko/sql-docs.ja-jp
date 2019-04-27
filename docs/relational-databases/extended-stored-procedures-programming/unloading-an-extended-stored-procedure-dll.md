---
title: ストアド プロシージャ DLL のアンロードの拡張 |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- extended stored procedures [SQL Server], unloading
- unloading extended stored procedures
ms.assetid: 4c75ab14-af54-4965-b376-8d75d385c941
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: d7f05ad92e5e5264801302f2f1e64c76478141d9
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62742105"
---
# <a name="unloading-an-extended-stored-procedure-dll"></a>拡張ストアド プロシージャ DLL のアンロード
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] 代わりに CLR Integration を使用してください。  
  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] DLL の関数のいずれかに呼び出しが行われるとすぐには、拡張ストアド プロシージャ DLL を読み込みます。 DLL がロードされた状態は、サーバーがシャットダウンするか、DBCC ステートメントを使用してシステム管理者によってアンロードされるまで、維持されます。 たとえば、このコマンドのアンロード、 **xp_hello.dll**、システム管理者は、サーバーをシャット ダウンせずに、このファイルの新しいバージョンをディレクトリにコピーすることができます。  
  
```  
DBCC xp_hello(FREE)  
```  
  
## <a name="see-also"></a>関連項目  
 [DBCC dllname &#40;FREE&#41; &#40;TRANSACT-SQL&#41;](../../t-sql/database-console-commands/dbcc-dllname-free-transact-sql.md)  
  
  
