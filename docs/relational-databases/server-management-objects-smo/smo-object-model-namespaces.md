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
author: markingmyname
ms.author: maghan
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 192e3b98e7091ba337fa1b0090c6add2a255a97a
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.contentlocale: ja-JP
ms.lasthandoff: 07/06/2020
ms.locfileid: "86012283"
---
# <a name="smo-object-model-namespaces"></a>SMO オブジェクト モデル名前空間
[!INCLUDE [SQL Server ASDB, ASDBMI, ASDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 管理オブジェクト (SMO) にはさまざまな名前空間があります。 それぞれの名前空間は、SMO 内の機能の各領域を表しています。  
  
 では、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] SMO アセンブリは C:\Program ARE SQL Server\130\SDK\Assemblies フォルダーにあります。  
  
## <a name="namespaces"></a>名前空間  
 SMO 名前空間は次のとおりです。  
  
|クラス|関数|  
|-----------|--------------|  
|<xref:Microsoft.SqlServer.Management.Smo>|プログラムによって操作するために使用されるインスタンスクラス、ユーティリティクラス、および列挙が含まれてい [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。|  
|<xref:Microsoft.SqlServer.Management.Common>|接続クラスなど、レプリケーション管理オブジェクト (RMO) および SMO に共通のクラスが含まれています。|  
|<xref:Microsoft.SqlServer.Management.Smo.Agent>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントを表すクラスが含まれています。|  
|<xref:Microsoft.SqlServer.Management.Smo.Wmi>|WMI プロバイダーを表すクラスが含まれています。|  
|<xref:Microsoft.SqlServer.Management.Smo.RegisteredServers>|登録済みサーバーを表すクラスが含まれています。|  
|<xref:Microsoft.SqlServer.Management.Smo.Mail>|データベース メールを表すクラスが含まれています。|  
|<xref:Microsoft.SqlServer.Management.Smo.Broker>|[!INCLUDE[ssSB](../../includes/sssb-md.md)] を表すクラスが含まれています。|  
  
  
