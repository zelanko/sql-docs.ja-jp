---
title: WQL とスクリプトを使用して WMI プロバイダーにアクセスする
description: WQL エディター、クエリツール、またはスクリプト言語を使用して、WMI プロバイダーを使用して SQL Server サービスおよびネットワーク設定にアクセスする方法について説明します。
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
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
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 14f0e64a884cf74b5fcb849a8f8527a6dad5de1e
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/08/2020
ms.locfileid: "89520172"
---
# <a name="using-wql-and-scripting-languages-with-the-wmi-provider"></a>WMI プロバイダーでの WQL とスクリプト言語の使用
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  管理アプリケーションが、WMI (Windows Management Instrumentation) Provider for Configuration Management オブジェクトを使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービスおよびネットワーク設定にアクセスするには、次の 2 つの方法があります。  
  
-   WQL エディターまたはクエリ ツール (WBEMTest.exe など) を使用して、WQL (WMI Query Language) でオブジェクト セットを照会する方法  
  
-   VBScript などのスクリプティング言語を使用する方法  
  
 または、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービスおよびネットワーク設定は、SMO で WMI マネージド オブジェクトを使用してプログラムで管理することもできます。 WMI マネージオブジェクトのプログラミングの詳細については、「 [Wmi プロバイダーを使用したサービスとネットワーク設定の管理](../../relational-databases/server-management-objects-smo/tasks/managing-services-and-network-settings-by-using-wmi-provider.md)」を参照してください。  
  
 WMI provider for Configuration Management には、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーおよび [!INCLUDE[msCoName](../../includes/msconame-md.md)] 管理コンソールを使用してアクセスすることができます。 ユーザーインターフェイスから WMI プロバイダーにアクセスする方法の詳細については、「 [サービスの管理方法に関するトピック &#40;SQL Server 構成マネージャー&#41;](https://msdn.microsoft.com/library/78dee169-df0c-4c95-9af7-bf033bc9fdc6)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [WQL を使用した構成管理用 WMI プロバイダーへのアクセス](../../relational-databases/wmi-provider-configuration/access-wmi-provider-for-configuration-management-using-wql.md)   
 [VBScript を使用して WMI プロバイダーにアクセスする](../../relational-databases/wmi-provider-configuration/access-wmi-provider-for-configuration-management-using-vbscript.md)  
  
  
