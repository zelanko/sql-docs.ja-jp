---
title: "ファイルとバージョン番号 |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: smo
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- SQL Server Management Objects, versions
- components [SMO]
- files [SMO], components
- SMO [SQL Server], versions
- versions [SMO]
ms.assetid: 510907b6-e7a9-41bd-b892-d6d99a5118e1
caps.latest.revision: "34"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 1a81684285e79e8e79ca1eca79ef24310d64502e
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="files-and-version-numbers"></a>ファイルとバージョン番号
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]必要なすべての SQL Server 管理オブジェクト (SMO) コンポーネントが Microsoft.SqlServer.SqlManagementObjects NuGet パッケージに含まれています。 SMO は複数のマネージ アセンブリに実装されます。 クライアント上またはサーバー上のいずれかで SMO アプリケーションを開発することができます。  

>>[!Important]
SMO アセンブリのファイル バージョンは、メジャーとして表示されます。**0**します。Build.Revision です。 埋め込まれたアセンブリのバージョンはメジャーです。**100**です。Build.Revision です。 これは、1 つの更新には影響しません、それ以外の各アプリケーションで使用される SMO のバージョンを別々 に保管します。
>>
>>このためする必要があります**いない**これらのバージョンのアセンブリをグローバル アセンブリ キャッシュ (GAC) にインストールします。 そうになる場合、他のアプリケーションなど[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Management Studio を中断します。 
  
|ファイル|Description|  
|-----------|-----------------|  
|Microsoft.SqlServer.ConnectionInfo.dll|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスへの接続のサポートが含まれています。|  
|Microsoft.SqlServer.ServiceBrokerEnum.dll|[!INCLUDE[msCoName](../../includes/msconame-md.md)] Service Broker のプログラミングのサポートが含まれています。 Service Broker にアクセスするプログラムにのみ必要です。|  
|Microsoft.SqlServer.Smo.dll|SMO クラスの大部分が含まれます。|  
|Microsoft.SqlServer.SmoExtended.dll<br /><br /> Microsoft.SqlServer.Management.Sdk.Sfc.dll<br /><br /> Microsoft.SqlServer.SqlEnum.dll|SMO クラスのサポートが含まれています。|  
|Microsoft.SqlServer.WmiEnum.dll|Windows Management Instrumentation (WMI) プロバイダー クラスが含まれています。 WMI プロバイダー クラスを使用するプログラムにのみ必要です。|  
|Microsoft.SqlServer.RegSvrEnum.dll|登録済みサーバー クラスが含まれています。 登録済みサーバー クラスを使用するプログラムにのみ必要です。|  
  
  
