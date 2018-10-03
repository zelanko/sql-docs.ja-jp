---
title: ファイルとバージョン番号 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- SQL Server Management Objects, versions
- components [SMO]
- files [SMO], components
- SMO [SQL Server], versions
- versions [SMO]
ms.assetid: 510907b6-e7a9-41bd-b892-d6d99a5118e1
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 333406ee6d7596c1aa8187b26476fb39f220c36e
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48219624"
---
# <a name="files-and-version-numbers"></a>ファイルとバージョン番号
  必要なすべて[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスの一部として管理オブジェクト (SMO) コンポーネントがインストールされている[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]クライアントまたはサーバー。 SMO は複数のマネージド アセンブリに実装されます。 クライアント上またはサーバー上のいずれかで SMO アプリケーションを開発することができます。  
  
|ディレクトリ|ファイル|説明|  
|---------------|----------|-----------------|  
|[!INCLUDE[ssSampPathSDK](../../includes/sssamppathsdk-md.md)]|Microsoft.SqlServer.ConnectionInfo.dll|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスへの接続のサポートが含まれています。|  
|[!INCLUDE[ssSampPathSDK](../../includes/sssamppathsdk-md.md)]|Microsoft.SqlServer.ServiceBrokerEnum.dll|[!INCLUDE[msCoName](../../includes/msconame-md.md)] Service Broker のプログラミングのサポートが含まれています。 Service Broker にアクセスするプログラムにのみ必要です。|  
|[!INCLUDE[ssSampPathSDK](../../includes/sssamppathsdk-md.md)]|Microsoft.SqlServer.Smo.dll|SMO クラスの大部分が含まれます。|  
|[!INCLUDE[ssSampPathSDK](../../includes/sssamppathsdk-md.md)]|Microsoft.SqlServer.SmoExtended.dll<br /><br /> Microsoft.SqlServer.Management.Sdk.Sfc.dll<br /><br /> Microsoft.SqlServer.SqlEnum.dll|SMO クラスのサポートが含まれています。|  
|[!INCLUDE[ssSampPathSDK](../../includes/sssamppathsdk-md.md)]|Microsoft.SqlServer.WmiEnum.dll|Windows Management Instrumentation (WMI) プロバイダー クラスが含まれています。 WMI プロバイダー クラスを使用するプログラムにのみ必要です。|  
|[!INCLUDE[ssSampPathSDK](../../includes/sssamppathsdk-md.md)]|Microsoft.SqlServer.RegSvrEnum.dll|登録済みサーバー クラスが含まれています。 登録済みサーバー クラスを使用するプログラムにのみ必要です。|  
  
  
