---
title: SMO オブジェクトモデル |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- object models [SMO]
- SMO [SQL Server], object model
- SQL Server Management Objects, object model
ms.assetid: bd6e59b6-ca46-42c0-adb2-c9d64cf6e00b
author: stevestein
ms.author: sstein
ms.openlocfilehash: c973e381a6cc7de44a0072d012147271eaa609ca
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85055213"
---
# <a name="smo-object-model"></a>SMO オブジェクト モデル
  SMO オブジェクト モデルは、オブジェクトの階層で構成されています。 <xref:Microsoft.SqlServer.Management.Smo.Server> オブジェクトはトップ レベル オブジェクトであるため、すべてのインスタンス クラス オブジェクトは <xref:Microsoft.SqlServer.Management.Smo.Server> オブジェクトの下位に位置します。  
  
 <xref:Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer> クラスは、個別のオブジェクト階層を持ったトップ レベル クラスです。 <xref:Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer>オブジェクトは、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] WMI プロバイダーを通じて使用できるサービスとネットワーク設定を表します。  
  
 <xref:Microsoft.SqlServer.Management.Smo.Server> オブジェクトおよび <xref:Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer> オブジェクトに加え、<xref:Microsoft.SqlServer.Management.Smo.Transfer>、<xref:Microsoft.SqlServer.Management.Smo.Backup>、<xref:Microsoft.SqlServer.Management.Smo.Restore> など、タスクや操作を表す複数のユーティリティ クラスがあります。  
  
 SMO オブジェクト モデルは、複数の名前空間で構成されています。 詳細については、「[SMO 名前空間](smo-object-model-namespaces.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [SMO オブジェクトモデルの図](smo-object-model-diagram.md)   
 [SMO 名前空間](smo-object-model-namespaces.md)   
 [構成管理用の WMI プロバイダーの概念](../wmi-provider-configuration/wmi-provider-for-configuration-management.md)  
  
  
