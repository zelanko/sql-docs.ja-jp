---
title: "WMI Provider for Configuration Management の使用 |Microsoft ドキュメント"
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
- permissions [WMI]
- connection strings [WMI]
- security [WMI]
- WMI Provider for Configuration Management, connection strings
- WMI Provider for Configuration Management, security
- late binding [WMI]
- WMI Provider for Configuration Management, late binding
- binding [WMI]
ms.assetid: 34daa922-7074-41d0-9077-042bb18c222a
caps.latest.revision: 
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: df9bbccadc0abb2ea1c8ca26093b8bdd0b893179
ms.sourcegitcommit: 0d904c23663cebafc48609671156c5ccd8521315
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/19/2018
---
# <a name="working-with-the-wmi-provider-for-configuration-management"></a>WMI Provider for Configuration Management の操作
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  WMI Provider for Computer Management を使用したプログラミングを行う前に、次の点について考慮してください。  
  
## <a name="binding"></a>Binding  
 WMI Provider for Configuration Management は、COM オブジェクト モデルであり、事前バインドも遅延バインドもサポートしています。 遅延バインドを行う場合、VBScript などのスクリプト言語を使用して、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービス、ネットワーク設定、別名をプログラムで操作することができます。  
  
 スクリプト言語を使用する WMI プロバイダーの実装のプログラミングに関する詳細については、次を参照してください。、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] MSDN [Web サイト](http://go.microsoft.com/fwlink/?linkid=15426)です。  
  
## <a name="specifying-a-connection-string"></a>接続文字列を指定します。  
 アプリケーションは、プロバイダーによって定義された WMI 名前空間に接続することで、WMI Provider for Configuration Management を [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスにダイレクトします。 Windows WMI サービスは、この名前空間をプロバイダー DLL にマップし、これをメモリに読み込みます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスはすべて、1 つの WMI 名前空間で表されます。 名前空間の既定値は次のとおりです。  
  
```  
\\.\root\Microsoft\SqlServer\ComputerManagement12\instance_name  
```  
  
 `instance_name` の既定値は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の既定のインストール内の `MSSQLSERVER` になります。  
  
 **注:**場合は、コンピューターが適切に構成されていることを確認する必要があります Windows ファイアウォール経由で接続します。 Windows Management Instrumentation のマニュアルの「Windows ファイアウォール経由の接続」記事を参照してください[!INCLUDE[msCoName](../../includes/msconame-md.md)]MSDN [Web サイト](http://go.microsoft.com/fwlink/?linkid=15426)です。  
  
## <a name="permissions-and-server-authentication"></a>権限とサーバー認証  
 WMI Provider for Configuration Management にアクセスするには、クライアント WMI 管理スクリプトが、対象となるコンピューター上の管理者のコンテキストで実行されている必要があります。 アクセスするユーザーは、管理するコンピューターのローカル Windows 管理者グループのメンバーである必要があります。  
  
 管理者は、グループ ポリシーを設定して、WMI プロバイダーへのユーザー アクセスを制御することができます。 グループ ポリシーの設定の詳細については、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーのヘルプの「グループ ポリシーと MMC」を参照してください。  
  
 WMI 管理スクリプトを使用すると、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービスが実行されるアカウントを更新することができます。  
  
 WMI Provider for Configuration Management では、セキュリティ証明書がサポートされています。 証明書の詳細については、次を参照してください。[暗号化階層](../../relational-databases/security/encryption/encryption-hierarchy.md)です。  
  
## <a name="see-also"></a>参照  
 [SQL Server 構成マネージャー](../../relational-databases/sql-server-configuration-manager.md)  
  
  
