---
title: 拡張ストアドプロシージャ DLL のアンロード |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- extended stored procedures [SQL Server], unloading
- unloading extended stored procedures
ms.assetid: 4c75ab14-af54-4965-b376-8d75d385c941
author: rothja
ms.author: jroth
ms.openlocfilehash: 7bd4855390e95d949ab769d6567d6f106959dcde
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85050836"
---
# <a name="unloading-an-extended-stored-procedure-dll"></a>拡張ストアド プロシージャ DLL のアンロード
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] 代わりに CLR Integration を使用してください。  
  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]dll のいずれかの関数が呼び出されるとすぐに、拡張ストアドプロシージャ DLL を読み込みます。 DLL がロードされた状態は、サーバーがシャットダウンするか、DBCC ステートメントを使用してシステム管理者によってアンロードされるまで、維持されます。 たとえば、次のコマンドは、 **xp_hello.dll**をアンロードします。これにより、システム管理者は、サーバーをシャットダウンすることなく、このファイルの新しいバージョンをディレクトリにコピーできます。  
  
```  
DBCC xp_hello(FREE)  
```  
  
## <a name="see-also"></a>参照  
 [DBCC dllname &#40;FREE&#41; &#40;Transact-sql&#41;](/sql/t-sql/database-console-commands/dbcc-dllname-free-transact-sql)  
  
  
