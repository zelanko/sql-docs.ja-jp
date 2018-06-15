---
title: affinity64 Input-Output mask サーバー構成オプション | Microsoft Docs
ms.custom: ''
ms.date: 03/02/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.suite: sql
ms.technology: configuration
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- processor affinity [SQL Server]
- binding processors [SQL Server]
- affinity64 I/O mask option
ms.assetid: d304eae7-5116-40ee-a0fa-0a3c0bc20c01
caps.latest.revision: 18
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: b8e4499d960ac2e96e494754920f124371f56c3e
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32863648"
---
# <a name="affinity64-input-output-mask-server-configuration-option"></a>affinity64 Input-Output mask サーバー構成オプション
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  **affinity64 I/O mask** オプションでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のディスク I/O を指定した CPU のサブセットにバインドします。このオプションは、 **affinity I/O mask** オプションに似ています。 **affinity I/O mask** を使用して最初の 32 プロセッサをバインドし、 **affinity64 I/O mask** を使用してコンピューター上の残りのプロセッサをバインドします。 **affinity64 I/O mask**オプションを再構成した場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスを再起動する必要があります。 このオプションは 64 ビット版の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]でのみ表示されます。  
  
## <a name="see-also"></a>参照  
 [affinity Input-Output mask サーバー構成オプション](../../database-engine/configure-windows/affinity-input-output-mask-server-configuration-option.md)   
 [リソースの利用状況の監視 &#40;System Monitor&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)   
 [サーバー構成オプション &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [RECONFIGURE &#40;Transact-SQL&#41;](../../t-sql/language-elements/reconfigure-transact-sql.md)  
  
  
