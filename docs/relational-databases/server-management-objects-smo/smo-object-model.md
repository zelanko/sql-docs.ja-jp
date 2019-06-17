---
title: SMO オブジェクト モデル |マイクロソフトのドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
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
manager: craigg
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: b9e2178b40d431f242f2270c24317e6b76a5e876
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "62942877"
---
# <a name="smo-object-model"></a>SMO オブジェクト モデル
[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

  SMO オブジェクト モデルは、オブジェクトの階層で構成されています。 <xref:Microsoft.SqlServer.Management.Smo.Server> オブジェクトはトップ レベル オブジェクトであるため、すべてのインスタンス クラス オブジェクトは <xref:Microsoft.SqlServer.Management.Smo.Server> オブジェクトの下位に位置します。  
  
 <xref:Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer> クラスは、個別のオブジェクト階層を持ったトップ レベル クラスです。 <xref:Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer>オブジェクトが表す[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]サービスおよびネットワーク設定、WMI プロバイダーで使用できます。  
  
 <xref:Microsoft.SqlServer.Management.Smo.Server> オブジェクトおよび <xref:Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer> オブジェクトに加え、<xref:Microsoft.SqlServer.Management.Smo.Transfer>、<xref:Microsoft.SqlServer.Management.Smo.Backup>、<xref:Microsoft.SqlServer.Management.Smo.Restore> など、タスクや操作を表す複数のユーティリティ クラスがあります。  
  
 SMO オブジェクト モデルは、複数の名前空間で構成されています。 詳細については、「[SMO 名前空間](../../relational-databases/server-management-objects-smo/smo-object-model-namespaces.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [SMO オブジェクト モデル ダイアグラム](../../relational-databases/server-management-objects-smo/smo-object-model-diagram.md)   
 [SMO 名前空間](../../relational-databases/server-management-objects-smo/smo-object-model-namespaces.md)   
 [構成管理用の WMI プロバイダーの概念](../../relational-databases/wmi-provider-configuration/wmi-provider-for-configuration-management.md)  
  
  
