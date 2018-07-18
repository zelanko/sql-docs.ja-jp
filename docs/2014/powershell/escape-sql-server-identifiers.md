---
title: SQL Server 識別子のエスケープ | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 8a73e945-daa6-4e5d-93da-10f000f1f3a2
caps.latest.revision: 6
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 191371a7f8f79c0fa52c4975edf1bfd25037d6e1
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37298632"
---
# <a name="escape-sql-server-identifiers"></a>SQL Server 識別子のエスケープ
  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] の区切れらた識別子には使用でき、Windows PowerShell パス名には使用できない文字をエスケープするためによく使用されるのが、Windows PowerShell のバック ティック エスケープ文字 (`) です。 ただし、エスケープできない文字もあります。 たとえば、Windows PowerShell ではコロン文字 (:) をエスケープできません。 この文字を含んだ識別子は、エンコードする必要があります。 エンコードは、すべての文字に有効であるため、エスケープよりも確実です。  
  
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
 [PowerShell での SQL Server 識別子](sql-server-identifiers-in-powershell.md)   
 [SQL Server PowerShell Provider](sql-server-powershell-provider.md)   
 [SQL Server PowerShell](sql-server-powershell.md)  
  
  
