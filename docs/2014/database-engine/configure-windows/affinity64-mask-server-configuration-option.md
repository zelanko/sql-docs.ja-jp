---
title: affinity64 mask サーバー構成オプション | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- processor affinity [SQL Server]
- affinity64 mask option
- binding processors [SQL Server]
ms.assetid: 75ed08c7-f85c-4e15-9ee1-e7bc545d3293
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 20e4cf3af48fa560293a9de05e768410d561a33b
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "62786701"
---
# <a name="affinity64-mask-server-configuration-option"></a>affinity64 mask サーバー構成オプション
  affinity64 mask を使用すると、affinity mask オプションと同様に、プロセッサが特定のスレッドにバインドされます。 affinity mask を使用して最初の 32 プロセッサをバインドし、affinity64 mask を使用してコンピューター上の残りのプロセッサをバインドします。 このオプションは 64 ビット版の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]でのみ表示されます。  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepNextAvoid](../../includes/ssnotedepnextavoid-md.md)] 代わりに [ALTER SERVER CONFIGURATION &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-server-configuration-transact-sql) を使用します。  
  
## <a name="see-also"></a>参照  
 [affinity mask サーバー構成オプション](affinity-mask-server-configuration-option.md)   
 [リソースの利用状況の監視 &#40;System Monitor&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)   
 [サーバー構成オプション &#40;SQL Server&#41;](server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)   
 [RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql)  
  
  
