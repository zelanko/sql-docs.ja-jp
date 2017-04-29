---
title: "データベース エンジン コマンドレットの使用 | Microsoft Docs"
ms.custom: 
ms.date: 08/04/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Cmdlets [SQL Server], Encode-Sqlname
- Encode-Sqlname cmdlet
- PowerShell [SQL Server], Encode-Sqlname
- Convert-UrnToPath cmdlet
- PowerShell [SQL Server], cmdlets
- Cmdlets [SQL Server]
- PowerShell [SQL Server], Convert-UrnToPath
- Cmdlets [SQL Server], Convert-UrnToPath
- Decode-Sqlname cmdlet
- PowerShell [SQL Server], Decode-Sqlname
- Cmdlets [SQL Server], Decode-Sqlname
ms.assetid: 720aa982-09ae-41a3-b603-a91004cfbe3e
caps.latest.revision: 25
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 457781b7e16a5722f4d232cff14b8f20c7651972
ms.lasthandoff: 04/11/2017

---
# <a name="use-the-database-engine-cmdlets"></a>データベース エンジン コマンドレットの使用
  Windows PowerShell コマンドレットは、単一の機能を実現するコマンドで、通常は **Get-Help** や **Set-MachineName** のように動詞と名詞を組み合わせた名前付け規則に従います。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 固有のコマンドレットは、Windows PowerShell 用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]プロバイダーによって提供されます。  
  
## <a name="database-engine-cmdlets"></a>データベース エンジンのコマンドレット  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]用の少数のコマンドレットが実装されます。 これらのコマンドレットは、主に新しい PowerShell スクリプトからの既存の Transact-SQL スクリプトの実行、ポリシー ベースの管理ポリシーの評価、および SQL Server プロバイダー パスでの SQL Server 識別子の指定の支援に使用されます。  
  
 Windows PowerShell スクリプトの多くは、SQL Server PowerShell プロバイダーおよび SQL Server 管理オブジェクト モデルを使用して、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] と共に動作します。 詳細については、「 [SQL Server PowerShell](../../relational-databases/scripting/sql-server-powershell.md)」を参照してください。  
  
### <a name="get-cmdlet-help"></a>コマンドレットのヘルプの利用  
 Windows PowerShell 環境では、 **Get-Help** コマンドレットを使用して各コマンドレットのヘルプ情報を参照できます。 **Get-Help** を実行すると、構文、パラメーター定義、入力と出力の種類、コマンドレットで実行される処理の説明などの情報が返されます。 詳細については、「 [Get Help SQL Server PowerShell](../../relational-databases/scripting/get-help-sql-server-powershell.md)」を参照してください。  
  
### <a name="partial-parameter-names"></a>部分的なパラメーター名  
 コマンドレット パラメーターの完全な名前を指定する必要はありません。 そのコマンドレットでサポートされている他のパラメーターと区別するのに足りる名前の一部のみを指定するだけでかまいません。 たとえば、次の例は、 **Invoke-Sqlcmd -QueryTimeout** パラメーターを指定する 3 つの方法を示します。  
  
```  
Invoke-Sqlcmd -Query "SELECT @@VERSION;" -QueryTimeout 3  
Invoke-Sqlcmd -Query "SELECT @@VERSION;" -QueryTime 3  
Invoke-Sqlcmd -Query "SELECT @@VERSION;" -QueryT 3  
```  
  
## <a name="database-engine-cmdlet-tasks"></a>データベース エンジン コマンドレットのタスク  
  
|タスクの説明|トピック|  
|----------------------|-----------|  
|**Invoke-Sqlcmd** の使用による、 **または XQuery ステートメントを含む** sqlcmd [!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプトやコマンドの実行について説明します。 **sqlcmd** の入力を、文字列の入力パラメーターとして、または開くスクリプト ファイルの名前として受け取ることができます。|[Invoke-Sqlcmd コマンドレット](../../powershell/invoke-sqlcmd-cmdlet.md)|  
|**Invoke-PolicyEvaluation** の使用による、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オブジェクトの対象セットがポリシー ベースの管理ポリシーに定義されている条件に準拠しているかどうかの報告について説明します。 必要に応じて、このコマンドレットを使用して、ポリシー条件に準拠していない対象オブジェクト内の設定可能なオプションを再構成することができます。|[Invoke-PolicyEvaluation コマンドレット](../../powershell/invoke-policyevaluation-cmdlet.md)|  
|**Encode-Sqlname** と **Decode-Sqlname** の使用による、Windows PowerShell パスではサポートされていない文字を含んだ SQL Server 識別子の処理について説明します。|[SQL Server 識別子のエンコードとデコード](../../relational-databases/scripting/encode-and-decode-sql-server-identifiers.md)|  
|**Convert-UrnToPath** の使用による、SQL Server 管理オブジェクト URN (Uniform Resource Name) から対応する SQL Server プロバイダー パスへの変換について説明します。|[URN から SQL Server プロバイダー パスへの変換](../../relational-databases/scripting/convert-urns-to-sql-server-provider-paths.md)|  
  
## <a name="see-also"></a>参照  
 [SQL Server PowerShell プロバイダー](../../relational-databases/scripting/sql-server-powershell-provider.md)   
 [SQL Server PowerShell](../../relational-databases/scripting/sql-server-powershell.md)   
[Always On 可用性グループの PowerShell コマンドレットの概要 (SQL Server)](../../database-engine/availability-groups/windows/overview-of-powershell-cmdlets-for-always-on-availability-groups-sql-server.md)
  
  

