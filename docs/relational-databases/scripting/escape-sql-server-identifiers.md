---
title: "SQL Server 識別子のエスケープ | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssms-scripting
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8a73e945-daa6-4e5d-93da-10f000f1f3a2
caps.latest.revision: "8"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c408a788fc6a59c98c46e0994f017e6dc2a69d7c
ms.sourcegitcommit: b603dcac7326bba387befe68544619e026e6a15e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="escape-sql-server-identifiers"></a>SQL Server 識別子のエスケープ
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の区切れらた識別子には使用でき、Windows PowerShell パス名には使用できない文字をエスケープするためによく使用されるのが、Windows PowerShell のバック ティック エスケープ文字 (`) です。 ただし、エスケープできない文字もあります。 たとえば、Windows PowerShell ではコロン文字 (:) をエスケープできません。 この文字を含んだ識別子は、エンコードする必要があります。 エンコードは、すべての文字に有効であるため、エスケープよりも確実です。  
  
## <a name="before-you-begin"></a>はじめに  
 通常、バック ティック文字 (`) のキーは、キーボード左上の Esc キーの下にあります (英語キーボードの場合)。  
  
## <a name="examples"></a>使用例  
 次に示すのは、# 文字をエスケープする例です。  
  
```  
cd SQLSERVER:\SQL\MyComputer\MyInstance\MyDatabase\MySchema\`#MyTempTable  
```  
  
 次に示すのは、コンピューター名として (local) を指定する際に、かっこをエスケープする例です。  
  
```  
Set-Location SQLSERVER:\SQL\`(local`)\DEFAULT  
```  
  
## <a name="see-also"></a>参照  
 [PowerShell での SQL Server 識別子](../../relational-databases/scripting/sql-server-identifiers-in-powershell.md)   
 [SQL Server PowerShell プロバイダー](../../relational-databases/scripting/sql-server-powershell-provider.md)   
 [SQL Server PowerShell](../../relational-databases/scripting/sql-server-powershell.md)  
  
  
