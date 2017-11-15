---
title: "SQLPS モジュールのインポート | Microsoft Docs"
ms.custom: 
ms.date: 08/01/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a972c56e-b2af-4fe6-abbd-817406e2c93a
caps.latest.revision: "12"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: cbd6691bf8fab45e58b41ad8e78166dd425ba605
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="import-the-sqlps-module"></a>SQLPS モジュールのインポート
  PowerShell から [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を管理する方法としては、 **sqlps** モジュールを Windows PowerShell 環境にインポートする方法を推奨します。 このモジュールによって、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のスナップインと管理アセンブリが読み込まれ、登録されます。  Windows PowerShell 3.0 以降、モジュールのコマンドレットまたは関数をコマンドで使用すると、モジュールは自動的にインポートされます。 この機能は、PSModulePath 環境変数値に含まれるディレクトリのすべてのモジュールで動作します。  詳細については、「 [Importing a PowerShell Module](https://msdn.microsoft.com/library/dd878284(v=vs.85).aspx)」(PowerShell モジュールのインポート) を参照してください。
  
1.  **はじめに:**  [セキュリティ](#Security)  
  
2.  **モジュールを読み込むには:**  [sqlps モジュールの読み込み](#LoadSqlps)  
  
## <a name="before-you-begin"></a>はじめに  
 **sqlps** モジュールを Windows PowerShell にインポートした後は、次のことができます。  
  
-   Windows PowerShell コマンドを対話的に実行する。  
  
-   Windows PowerShell スクリプト ファイルを実行する。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コマンドレットを実行する。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] プロバイダー パスを使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オブジェクトの階層内を移動する。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の管理オブジェクト モデル (Microsoft.SqlServer.Management.Smo など) を使用して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のオブジェクトを管理する。  
  
> [!NOTE]  
>  2 つの SQL Server コマンドレット (**Encode-Sqlname** および **Decode-Sqlname**) の名前で使用されている動詞は、Windows PowerShell で承認されている動詞と一致しません。 このことは、コマンドレットの操作には影響しませんが、 **sqlps** モジュールがセッションにインポートされるときに、Windows PowerShell による警告が発生します。  
  
###  <a name="Security"></a> セキュリティ  
 既定では、Windows PowerShell 実行時のスクリプト実行ポリシーは **[Restricted]**に設定されます。これにより、Windows PowerShell スクリプトの実行が防止されます。 **sqlps** モジュールを読み込むには、 **Set-ExecutionPolicy** コマンドレットを使用して署名されたスクリプトまたは任意のスクリプトの実行を有効にすることができます。 信頼できるソースからのスクリプト以外は実行しないでください。また、適切な NTFS 権限を使用して、すべての入力ファイルと出力ファイルのセキュリティを保護してください。 Windows PowerShell スクリプトの有効化の詳細については、「 [Windows PowerShell スクリプトの実行](http://www.microsoft.com/technet/scriptcenter/topics/winpsh/manual/run.mspx)」を参照してください。  
  
##  <a name="LoadSqlps"></a> sqlps モジュールの読み込み  
 **Windows PowerShell に sqlps モジュールを読み込むには**  
  
1.  適切なスクリプト実行ポリシーを設定するには、 **Set-ExecutionPolicy** コマンドレットを使用します。  
  
2.  sqlps モジュールをインポートするには、 **Import-Module** コマンドレットを使用します。 **Encode-Sqlname** および **Decode-Sqlname** についての警告を抑制する場合は、 **DisableNameChecking**パラメーターを指定します。  
  
### <a name="example"></a>例  
 この例は **sqlps** モジュールを読み込み、名前のチェックを無効にします。  
  
```powershell 
# Import the SQL Server Module.    
Import-Module Sqlps -DisableNameChecking;

# To check whether the module is installed.
Get-Module -ListAvailable -Name Sqlps;
```  
  
> [!NOTE]  
>  **sqlps** モジュールがパスにない場合は、モジュールの場所に変更するか、スクリプト内のフル パスを使用します (パス内のスペースがあるフォルダーの二重引用符を使用)。 **sqlps** モジュールは、SQL Server インスタンスの Tools\Powershell フォルダーにあります。  
  
 ![[トップに戻る] リンクで使用される矢印アイコン](../../analysis-services/instances/media/uparrow16x16.gif "[トップに戻る] リンクで使用される矢印アイコン") [&#91;トップ&#93;]()  
  
## <a name="see-also"></a>参照  
 [SQL Server PowerShell](../../relational-databases/scripting/sql-server-powershell.md)   
 [SQL Server PowerShell プロバイダー](../../relational-databases/scripting/sql-server-powershell-provider.md)   
 [データベース エンジン コマンドレットの使用](../../relational-databases/scripting/use-the-database-engine-cmdlets.md)  
 [PowerShell モジュールのインストール](https://msdn.microsoft.com/library/dd878350(v=vs.85).aspx)  
 [Import-Module](https://technet.microsoft.com/library/hh849725.aspx)
  
  
