---
title: "WQL を使用して、スクリプティング言語での WMI プロバイダー |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: wmi
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- queries [WMI]
- scripts [WMI]
- query language [WMI]
- WMI Query Language [WMI]
- WQL [WMI]
- WMI Provider for Configuration Management, WQL
- WMI Provider for Configuration Management, scripts
ms.assetid: c1e64905-3c2b-4974-88f4-abf17cf7e289
caps.latest.revision: 
author: JennieHubbard
ms.author: jhubbard
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: fa71b18f7acd0b5964a7ab18b2cf2fbc94015960
ms.sourcegitcommit: 37f0b59e648251be673389fa486b0a984ce22c81
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/12/2018
---
# <a name="using-wql-and-scripting-languages-with-the-wmi-provider"></a>WQL を使用して、スクリプティング言語での WMI プロバイダー
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
管理アプリケーションが、WMI (Windows Management Instrumentation) Provider for Configuration Management オブジェクトを使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービスおよびネットワーク設定にアクセスするには、次の 2 つの方法があります。  
  
-   WQL エディターまたはクエリ ツール (WBEMTest.exe など) を使用して、WQL (WMI Query Language) でオブジェクト セットを照会する方法  
  
-   VBScript などのスクリプティング言語を使用する方法  
  
 または、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービスおよびネットワーク設定は、SMO で WMI マネージ オブジェクトを使用してプログラムで管理することもできます。 WMI をプログラミングの詳細については、オブジェクトを管理を参照してください[Services の管理とネットワークの設定を使用して WMI プロバイダーによって](../../relational-databases/server-management-objects-smo/tasks/managing-services-and-network-settings-by-using-wmi-provider.md)です。  
  
 WMI provider for Configuration Management には、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーおよび [!INCLUDE[msCoName](../../includes/msconame-md.md)] 管理コンソールを使用してアクセスすることができます。 ユーザー インターフェイスから WMI プロバイダーへのアクセスの詳細については、次を参照してください。 [Services の管理方法に関するトピック &#40;です。SQL Server 構成マネージャー &#41;](http://msdn.microsoft.com/library/78dee169-df0c-4c95-9af7-bf033bc9fdc6).  
  
## <a name="see-also"></a>参照  
 [WQL を使用して構成管理の WMI プロバイダーにアクセス](../../relational-databases/wmi-provider-configuration/access-wmi-provider-for-configuration-management-using-wql.md)   
 [SQL Server サービスの詳細プロパティ VBScript を使用しての変更します。](../../relational-databases/wmi-provider-configuration/access-wmi-provider-for-configuration-management-using-vbscript.md)  
  
  
