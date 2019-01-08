---
title: EKM provider enabled サーバー構成オプション | Microsoft Docs
ms.custom: ''
ms.date: 03/02/2017
ms.prod: sql
ms.prod_service: high-availability
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
ms.openlocfilehash: 2a4a04ec504cfbed4fb187c7dcde7f61fb083664
ms.sourcegitcommit: 6443f9a281904af93f0f5b78760b1c68901b7b8d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2018
ms.locfileid: "53214594"
---
# <a name="ekm-provider-enabled-server-configuration-option"></a>EKM provider enabled サーバー構成オプション
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  **EKM provider enabled** オプションは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]での拡張キー管理デバイスのサポートを制御します。 既定では、このオプションはオフになっています。  
  
 この機能を有効または無効にするには、次の **sp_configure** コマンドのいずれかを実行します。  
  
```  
/* Enable the external encryption provider option */  
sp_configure 'EKM provider enabled', 1  
/* Disable the external encryption provider option */  
sp_configure 'EKM provider enabled', 0  
```  
  
> [!NOTE]
>  このオプションは [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のすべてのエディションで有効になっているわけではありません。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の各エディションでサポートされる機能の一覧については、「 [SQL Server 2016 の各エディションがサポートする機能](~/sql-server/editions-and-supported-features-for-sql-server-2016.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [拡張キー管理 &#40;EKM&#41;](../../relational-databases/security/encryption/extensible-key-management-ekm.md)   
 [サーバー構成オプション &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [リソースの利用状況の監視 &#40;System Monitor&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [RECONFIGURE &#40;Transact-SQL&#41;](../../t-sql/language-elements/reconfigure-transact-sql.md)  
  
  

