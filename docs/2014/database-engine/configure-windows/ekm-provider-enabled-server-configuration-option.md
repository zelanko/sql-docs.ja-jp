---
title: EKM provider enabled サーバー構成オプション | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- external encryption provider
helpviewer_keywords:
- EKM provider enabled option
ms.assetid: da58ed50-3a13-4172-9065-960559d8f383
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 136056f848c85c2fbe8c572a5866c4e23b3a85b5
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "62782221"
---
# <a name="ekm-provider-enabled-server-configuration-option"></a>EKM provider enabled サーバー構成オプション
  
  `EKM provider enabled` オプションは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] での拡張キー管理デバイスのサポートを制御します。 既定では、このオプションはオフになっています。  
  
 この機能を有効または無効にするには、次の `sp_configure` コマンドのいずれかを実行します。  
  
```  
/* Enable the external encryption provider option */  
sp_configure 'EKM provider enabled', 1  
/* Disable the external encryption provider option */  
sp_configure 'EKM provider enabled', 0  
```  
  
> [!NOTE]  
>  このオプションは [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のすべてのエディションで有効になっているわけではありません。 の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]各エディションでサポートされる機能の一覧については、「 [SQL Server 2014 の各エディションがサポートする機能](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [拡張キー管理 &#40;EKM&#41;](../../relational-databases/security/encryption/extensible-key-management-ekm.md)   
 [サーバー構成オプション &#40;SQL Server&#41;](server-configuration-options-sql-server.md)   
 [リソースの利用状況の監視 &#40;System Monitor&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)   
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)   
 [RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql)  
  
  
