---
title: SMO 名前空間 |Microsoft Docs
ms.custom: ''
ms.date: 08/02/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: smo
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- object models [SMO]
- SMO [SQL Server], namespaces
- namespaces [SMO]
- SQL Server Management Objects, namespaces
ms.assetid: 7bfabe4d-9f4c-4bc9-b998-93bd2b50ee8a
caps.latest.revision: 39
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: 9688b97d469e9ec3687c9d005d776987785ebc5d
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/06/2018
ms.locfileid: "39550392"
---
# <a name="smo-object-model-namespaces"></a>SMO オブジェクト モデル名前空間
[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 管理オブジェクト (SMO) にはさまざまな名前空間があります。 それぞれの名前空間は、SMO 内の機能の各領域を表しています。  
  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]、SMO アセンブリは C:\Program files \microsoft SQL Server\130\SDK\Assemblies\ フォルダーにあります。  
  
## <a name="namespaces"></a>名前空間  
 SMO 名前空間は次のとおりです。  
  
|クラス|機能|  
|-----------|--------------|  
|<xref:Microsoft.SqlServer.Management.Smo>|インスタンス クラス、ユーティリティ クラス、およびプログラムで操作するために使用される列挙体を含む[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。|  
|<xref:Microsoft.SqlServer.Management.Common>|接続クラスなど、レプリケーション管理オブジェクト (RMO) および SMO に共通のクラスが含まれています。|  
|<xref:Microsoft.SqlServer.Management.Smo.Agent>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントを表すクラスが含まれています。|  
|<xref:Microsoft.SqlServer.Management.Smo.Wmi>|WMI プロバイダーを表すクラスが含まれています。|  
|<xref:Microsoft.SqlServer.Management.Smo.RegisteredServers>|登録済みサーバーを表すクラスが含まれています。|  
|<xref:Microsoft.SqlServer.Management.Smo.Mail>|データベース メールを表すクラスが含まれています。|  
|<xref:Microsoft.SqlServer.Management.Smo.Broker>|[!INCLUDE[ssSB](../../includes/sssb-md.md)] を表すクラスが含まれています。|  
  
  
