---
title: SMO and DMO XPs サーバー構成オプション | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bcd945ba-5d81-4124-9a2b-d87491c2a369
caps.latest.revision: 14
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: fe06dd6034c8ada7c5b702655304fc245bb9d8b1
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36173304"
---
# <a name="smo-and-dmo-xps-server-configuration-option"></a>SMO and DMO XPs サーバー構成オプション
  このサーバーで [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 管理オブジェクト (SMO) の拡張ストアド プロシージャを使用するには、SMO and DMO XPs オプションを使用します。  
  
 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]の DMO は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]で削除されました。  
  
 次の表に、このオプションで使用可能な値を示します。  
  
|値|説明|  
|-----------|-------------|  
|0|SMO 拡張ストアド プロシージャ (XP) を使用できません。|  
|1|SMO 拡張ストアド プロシージャ (XP) を使用できます。 既定値です。|  
  
 この設定はすぐに有効になります。  
  
## <a name="examples"></a>使用例  
 次の例では、SMO の拡張ストアド プロシージャを有効にします。  
  
```  
sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE;  
GO  
sp_configure 'SMO and DMO XPs', 1;  
GO  
RECONFIGURE  
GO  
```  
  
## <a name="see-also"></a>参照  
 [SQL Server 管理オブジェクト &#40;SMO&#41; プログラミング ガイド](../../relational-databases/server-management-objects-smo/sql-server-management-objects-smo-programming-guide.md)  
  
  