---
title: WQL を使用して、スクリプティング言語での WMI Provider for Configuration Management |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
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
caps.latest.revision: 17
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 4dc000220a4ced29074489bbc06556bbc07a18ce
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36178396"
---
# <a name="using-wql-and-scripting-languages-with-the-wmi-provider-for-configuration-management"></a>WQL およびスクリプティング言語での WMI Provider for Configuration Management の使用
  管理アプリケーションが、WMI (Windows Management Instrumentation) Provider for Configuration Management オブジェクトを使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービスおよびネットワーク設定にアクセスするには、次の 2 つの方法があります。  
  
-   WQL エディターまたはクエリ ツール (WBEMTest.exe など) を使用して、WQL (WMI Query Language) でオブジェクト セットを照会する方法  
  
-   VBScript などのスクリプティング言語を使用する方法  
  
 または、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービスおよびネットワーク設定は、SMO で WMI マネージ オブジェクトを使用してプログラムで管理することもできます。 WMI をプログラミングの詳細については、オブジェクトを管理を参照してください[Services の管理とネットワークの設定を使用して WMI プロバイダーによって](../server-management-objects-smo/tasks/managing-services-and-network-settings-by-using-wmi-provider.md)です。  
  
 WMI provider for Configuration Management には、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーおよび [!INCLUDE[msCoName](../../includes/msconame-md.md)] 管理コンソールを使用してアクセスすることができます。 ユーザー インターフェイスから WMI プロバイダーへのアクセスの詳細については、次を参照してください。 [Services の操作方法に関するトピックを管理する&#40;SQL Server 構成マネージャー&#41;](../../database-engine/managing-services-how-to-topics-sql-server-configuration-manager.md)です。  
  
## <a name="see-also"></a>参照  
 [WQL を使用して構成管理の WMI プロバイダーにアクセス](access-wmi-provider-for-configuration-management-using-wql.md)   
 [VBScript を使用して SQL Server サービスの詳細プロパティを変更する](access-wmi-provider-for-configuration-management-using-vbscript.md)  
  
  