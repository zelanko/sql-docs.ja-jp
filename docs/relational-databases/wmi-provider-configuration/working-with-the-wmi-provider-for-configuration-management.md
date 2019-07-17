---
title: WMI Provider for Configuration Management の使用 |Microsoft Docs
ms.custom: ''
ms.date: 04/12/2019
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 5e6736c73f7cda435d91e3ec9c9f523bdc08f1b3
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68139265"
---
# <a name="working-with-the-wmi-provider-for-configuration-management"></a>WMI Provider for Configuration Management の操作

[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

この記事では、コンピューターの管理用 WMI プロバイダーを使用してプログラミングする方法についてガイダンスを提供します。

## <a name="binding"></a>Binding  
 WMI Provider for Configuration Management は、COM オブジェクト モデルであり、事前バインドも遅延バインドもサポートしています。 遅延バインドを行う場合、VBScript などのスクリプト言語を使用して、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービス、ネットワーク設定、別名をプログラムで操作することができます。  
  
## <a name="specifying-a-connection-string"></a>接続文字列を指定します。

アプリケーションは、プロバイダーによって定義された WMI 名前空間に接続することで、WMI Provider for Configuration Management を [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスにダイレクトします。 Windows WMI サービスは、プロバイダー DLL でこの名前空間にマップし、メモリに DLL を読み込みます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスはすべて、1 つの WMI 名前空間で表されます。

名前空間の既定値は、次の形式です。 形式で`VV`は SQL Server のメジャー バージョン番号です。 実行して、番号が探索可能な`SELECT @@VERSION;`します。

```console
\\.\root\Microsoft\SqlServer\ComputerManagementVV
```

PowerShell では、先頭を使用して接続すると`\\.\`削除する必要があります。 たとえば、次の PowerShell コードを一覧表示すべての WMI クラスを SQL Server 2016 のメジャー バージョン 13 であります。

```powershell
Get-WmiObject -Namespace 'root\Microsoft\SqlServer\ComputerManagement13' -List
```

<!--
Updated this on 2019-04-12, per:
   ~ https://github.com/MicrosoftDocs/sql-docs/issues/1817
   ~ https://github.com/rrg92/sql-docs/commit/3d518bfc0d55f819c762abc3e5c5c9eed85abe94?diff=unified

Thus from here I (GeneMi = MightyPen) removed the following text about 'instance_name':

'root\Microsoft\SqlServer\ComputerManagement13\instance_name'

where `instance_name` defaults to `MSSQLSERVER` in a default installation of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].
-->

次の PowerShell コードを使用すると、使用可能なすべての WMI ComputerManagement 名前空間のクエリを実行します。

```powershell
gwmi -ns 'root\Microsoft\SqlServer' __NAMESPACE | ? {$_.name -match 'ComputerManagement' } | select name
```

 **注:** Windows ファイアウォール経由で接続する場合は、コンピューターが適切に構成されているかどうかを確認する必要があります。 Windows Management Instrumentation のドキュメントの「Windows ファイアウォール経由の接続」記事を参照してください[!INCLUDE[msCoName](../../includes/msconame-md.md)]MSDN [Web サイト](https://go.microsoft.com/fwlink/?linkid=15426)します。  
  
## <a name="permissions-and-server-authentication"></a>権限とサーバー認証  
 WMI Provider for Configuration Management にアクセスするには、クライアント WMI 管理スクリプトが、ターゲット コンピューター上の管理者のコンテキストで実行されている必要があります。 アクセスするユーザーは、管理するコンピューターのローカル Windows 管理者グループのメンバーである必要があります。  
  
 管理者は、グループ ポリシーを設定して、WMI プロバイダーへのユーザー アクセスを制御することができます。 グループ ポリシーの設定の詳細については、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーのヘルプの「グループ ポリシーと MMC」を参照してください。  
  
 WMI 管理スクリプトを使用すると、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービスが実行されるアカウントを更新することができます。  
  
 WMI Provider for Configuration Management では、セキュリティ証明書がサポートされています。 証明書の詳細については、次を参照してください。[暗号化階層](../../relational-databases/security/encryption/encryption-hierarchy.md)します。  
  
## <a name="see-also"></a>参照  
 [SQL Server 構成マネージャー](../../relational-databases/sql-server-configuration-manager.md)  
  
  
