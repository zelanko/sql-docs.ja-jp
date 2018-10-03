---
title: WMI Provider for Configuration Management の理解 |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- WMI Provider for Configuration Management, operations supported
ms.assetid: 92323972-7943-4208-bbf4-050774fb6027
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: c19e95b895283e0f2530925fbbcfcd3eee94a522
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47740280"
---
# <a name="understanding-the-wmi-provider-for-configuration-management"></a>WMI Provider for Configuration Management について
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成管理用 WMI プロバイダーを提供します。 これにより、WMI (Windows Management Instrumentation) を使用して、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービス、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のクライアントおよびサーバーのネットワーク設定、およびサーバー別名を管理することができます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービス、ネットワーク設定、および別名は、\microsoft\sqlserver\computermanagement WMI オブジェクトによって表される*nn*コンピューターの名前空間。 指定されたコンピューター上で WMI プロバイダーを使用して接続が確立された後、サービス、ネットワーク設定、別名は、WQL またはスクリプティング言語を使用してクエリを行うことができます。  
  
 WMI プロバイダーは、インスタンス プロバイダーです。 インスタンスを提供、 [WMI クラス](../../relational-databases/wmi-provider-configuration-classes/wmi-provider-for-configuration-management-classes.md)次の非同期操作をサポートしています。  
  
 インスタンスの取得  
 特定のクラス型インスタンスの取得です。  
  
 列挙型  
 クラス型のすべてのインスタンスの列挙です。  
  
 変更  
 クラス型の特定のインスタンスの変更です。  
  
 クラスには、クラスのプロパティの変更を許可するメソッドがあります。  
  
 削除  
 クラス型の特定のインスタンスの削除です。  
  
 クエリ処理  
 フィルターに基づいたクラス型のインスタンスの列挙です。  
  
 構成管理用 WMI プロバイダーを使用して管理アプリケーションの例については、次を参照してください。 [WQL を使用して、WMI Provider for Configuration Management でのスクリプト言語](../../relational-databases/wmi-provider-configuration/using-wql-and-scripting-languages-with-the-wmi-provider.md)します。  
  
 WMI プロバイダーを使用して管理アプリケーションのプログラミングの詳細については、WMI のドキュメントを参照してください、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework SDK。  
  
## <a name="see-also"></a>参照  
 [WMI Provider for Configuration Management の使用](../../relational-databases/wmi-provider-configuration/working-with-the-wmi-provider-for-configuration-management.md)   
 [WQL およびスクリプティング言語での WMI Provider for Configuration Management の使用](../../relational-databases/wmi-provider-configuration/using-wql-and-scripting-languages-with-the-wmi-provider.md)  
  
  
