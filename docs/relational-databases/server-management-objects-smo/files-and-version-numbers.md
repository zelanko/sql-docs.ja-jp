---
title: ファイルとバージョン番号 |Microsoft Docs
ms.custom: ''
ms.date: 08/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: smo
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Management Objects, versions
- components [SMO]
- files [SMO], components
- SMO [SQL Server], versions
- versions [SMO]
ms.assetid: 510907b6-e7a9-41bd-b892-d6d99a5118e1
caps.latest.revision: 34
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 10e11076ce023a3d969b4ba95a30c15de43eafa6
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "38046230"
---
# <a name="files-and-version-numbers"></a>ファイルとバージョン番号
[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

  必要なすべての SQL Server 管理オブジェクト (SMO) コンポーネントは、Microsoft.SqlServer.SqlManagementObjects NuGet パッケージに含まれています。 SMO は複数のマネージド アセンブリに実装されます。 クライアント上またはサーバー上のいずれかで SMO アプリケーションを開発することができます。  

>>[!Important]
SMO アセンブリのファイル バージョンは、メジャーとして表示されます。**0**します。Build.Revision します。 埋め込まれたアセンブリのバージョンがメジャー。**100**します。Build.Revision します。 これは、1 つの更新で、その他の要素に影響しませんは、各アプリケーションで使用される SMO のバージョンを分離します。
>>
>>このためする必要があります**いない**これらのバージョンのアセンブリをグローバル アセンブリ キャッシュ (GAC) にインストールします。 そう考えられる原因、他のアプリケーションなど[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Management Studio を中断します。 
  
|ファイル|説明|  
|-----------|-----------------|  
|Microsoft.SqlServer.ConnectionInfo.dll|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスへの接続のサポートが含まれています。|  
|Microsoft.SqlServer.ServiceBrokerEnum.dll|[!INCLUDE[msCoName](../../includes/msconame-md.md)] Service Broker のプログラミングのサポートが含まれています。 Service Broker にアクセスするプログラムにのみ必要です。|  
|Microsoft.SqlServer.Smo.dll|SMO クラスの大部分が含まれます。|  
|Microsoft.SqlServer.SmoExtended.dll<br /><br /> Microsoft.SqlServer.Management.Sdk.Sfc.dll<br /><br /> Microsoft.SqlServer.SqlEnum.dll|SMO クラスのサポートが含まれています。|  
|Microsoft.SqlServer.WmiEnum.dll|Windows Management Instrumentation (WMI) プロバイダー クラスが含まれています。 WMI プロバイダー クラスを使用するプログラムにのみ必要です。|  
|Microsoft.SqlServer.RegSvrEnum.dll|登録済みサーバー クラスが含まれています。 登録済みサーバー クラスを使用するプログラムにのみ必要です。|  
  
  
