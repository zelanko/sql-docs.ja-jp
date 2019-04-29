---
title: SMO 名前空間 |Microsoft Docs
ms.custom: ''
ms.date: 08/02/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- object models [SMO]
- SMO [SQL Server], namespaces
- namespaces [SMO]
- SQL Server Management Objects, namespaces
ms.assetid: 7bfabe4d-9f4c-4bc9-b998-93bd2b50ee8a
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 717b2171b535405cc0bc075ceafd50107fb68bed
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62943118"
---
# <a name="smo-object-model-namespaces"></a>SMO オブジェクト モデル名前空間
[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 管理オブジェクト (SMO) にはさまざまな名前空間があります。 それぞれの名前空間は、SMO 内の機能の各領域を表しています。  
  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]、SMO アセンブリは C:\Program files \microsoft SQL Server\130\SDK\Assemblies\ フォルダーにあります。  
  
## <a name="namespaces"></a>名前空間  
 SMO 名前空間は次のとおりです。  
  
|クラス|関数|  
|-----------|--------------|  
|<xref:Microsoft.SqlServer.Management.Smo>|インスタンス クラス、ユーティリティ クラス、およびプログラムで操作するために使用される列挙体を含む[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。|  
|<xref:Microsoft.SqlServer.Management.Common>|接続クラスなど、レプリケーション管理オブジェクト (RMO) および SMO に共通のクラスが含まれています。|  
|<xref:Microsoft.SqlServer.Management.Smo.Agent>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントを表すクラスが含まれています。|  
|<xref:Microsoft.SqlServer.Management.Smo.Wmi>|WMI プロバイダーを表すクラスが含まれています。|  
|<xref:Microsoft.SqlServer.Management.Smo.RegisteredServers>|登録済みサーバーを表すクラスが含まれています。|  
|<xref:Microsoft.SqlServer.Management.Smo.Mail>|データベース メールを表すクラスが含まれています。|  
|<xref:Microsoft.SqlServer.Management.Smo.Broker>|[!INCLUDE[ssSB](../../includes/sssb-md.md)] を表すクラスが含まれています。|  
  
  
