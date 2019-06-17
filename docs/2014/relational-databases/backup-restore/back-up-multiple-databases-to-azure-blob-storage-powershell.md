---
title: PowerShell を使用して、Windows Azure Blob ストレージ サービスへの複数のデータベースのバックアップ |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: f7008339-e69d-4e20-9265-d649da670460
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 03a747825c20b1183977b6c5b8e7f46ef2aa034f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "62922576"
---
# <a name="use-powershell-to-backup-multiple-databases-to-windows-azure-blob-storage-service"></a>PowerShell の使用による Windows Azure BLOB ストレージ サービスへの複数データベースのバックアップ
  このトピックには、PowerShell コマンドレットを使用して Windows Azure BLOB ストレージ サービスへのバックアップを自動化するためのサンプル スクリプトを掲載しています。  
  
## <a name="overview-of-powershell-cmdlets-for-backup-and-restore"></a>バックアップと復元用の PowerShell コマンドレットの概要  
 バックアップ操作と復元操作を行うために使用できる 2 つの主要なコマンドレットは、`Backup-SqlDatabase` と `Restore-SqlDatabase` です。 さらに、一連の **SqlCredential** コマンドレットのように、Windows Azure BLOB ストレージへのバックアップを自動化するために必要な他のコマンドレットもあります。バックアップおよび復元操作用として [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] に用意されている PowerShell コマンドレットを次に示します。  
  
 Backup-SqlDatabase  
 このコマンドレットは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] バックアップを作成するために使用します。  
  
 Restore-SqlDatabase  
 データベースを復元するために使用します。  
  
 New-SqlCredential  
 このコマンドレットは、Windows Azure ストレージへの SQL Server バックアップに使用する SQL 資格情報を作成するために使用します。 SQL Server のバックアップと復元における資格情報およびその使用方法の詳細については、「 [SQL Server Backup and Restore with Windows Azure Blob Storage Service](sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md)」を参照してください。  
  
 Get-SqlCredential  
 このコマンドレットは、資格情報オブジェクトとそのプロパティを取得するために使用します。  
  
 Remove-SqlCredential  
 SQL 資格情報オブジェクトを削除します。  
  
 Set-SqlCredential  
 このコマンドレットは、SQL 資格情報オブジェクトのプロパティを変更または設定するために使用します。  
  
> [!TIP]  
>  資格情報コマンドレットは、Windows Azure BLOB ストレージへのバックアップと復元で使用します。  
  
### <a name="powershell-for-multi-database-multi-instance-backup-operations"></a>複数データベース/複数インスタンス バックアップ操作用の PowerShell  
 以下のセクションでは、SQL Server の複数インスタンスでの SQL 資格情報の作成、特定の SQL Server インスタンスにあるすべてのユーザー データベースのバックアップなど、さまざまな操作用のスクリプトを掲載します。 これらのスクリプトでは、使用している環境の要件に従ってバックアップ操作を自動化またはスケジュールすることができます。 ここに示すスクリプトは例であり、環境に合わせて変更または拡張することができます。  
  
 サンプル スクリプトに関する注意点を次に示します。  
  
1.  **SQL Server PowerShell パスの移動:** Windows PowerShell では、PowerShell プロバイダーによってサポートされているオブジェクトの階層を表すパス構造を移動するコマンドレットが実装されています。 そのパス内のノードへ移動したときに、他のコマンドレットを使用して、現在のオブジェクトの基本的な操作を実行することができます。  
  
2.  `Get-ChildItem` コマンドレット:によって返される情報、 `Get-ChildItem` SQL Server PowerShell パス内の場所によって異なります。 たとえば、場所がコンピューター レベルである場合、このコマンドレットはコンピューターにインストールされているすべての SQL Server データベース エンジン インスタンスを返します。 もう 1 つの例として、場所がデータベースなどのオブジェクト レベルである場合、このコマンドレットはデータベース オブジェクトのリストを返します。  既定では、`Get-ChildItem` コマンドレットはシステム オブジェクトを返しません。  -Force パラメーターを使用すると、システム オブジェクトを表示できます。  
  
     詳細については、「 [Navigate SQL Server PowerShell Paths](../../powershell/navigate-sql-server-powershell-paths.md)」をご参照ください。  
  
3.  各コード サンプルは変数値を変更して個別に試すことができますが、Windows Azure ストレージ アカウントおよび SQL 資格情報の作成は前提条件であり、Windows Azure BLOB ストレージ サービスへのすべてのバックアップ操作と復元操作に必要です。  
  
### <a name="create-a-sql-credential-on-all-the-instances-of-sql-server"></a>SQL Server のすべてのインスタンスで SQL 資格情報を作成する  
 2 種類のサンプル スクリプトがあり、いずれもコンピューター上のすべての SQL Server インスタンスで SQL 資格情報 "mybackupToURL" を作成します。 最初の例では単純に資格情報を作成し、例外をトラップしません。  たとえば、コンピューター上のいずれかのインスタンスに同じ名前の資格情報が既に存在する場合、このスクリプトは失敗します。 2 番目の例ではエラーをトラップし、スクリプトを続行できます。  
  
```  
  
import-module sqlps  
  
# create variables  
$storageAccount = "mystorageaccount"  
$storageKey = "<storageaccesskeyvalue>"  
$secureString = convertto-securestring $storageKey  -asplaintext -force  
$credentialName = "mybackuptoURL"  
  
#cd to computer level  
cd sqlserver:\sql\COMPUTERNAME  
# get the list of instances  
$instances = Get-childitem  
#pipe the instances to new-sqlcredentail cmdlet to create SQL credential  
$instances | new-sqlcredential -Name $credentialName  -Identity $storageAccount -Secret $secureString  
```  
  
```  
  
import-module sqlps  
  
# set the parameter values  
  
$storageAccount = "mystorageaccount"  
$storageKey = "<storageaccesskeyvalue>"  
$secureString = convertto-securestring $storageKey  -asplaintext -force  
$credentialName = "mybackuptoURL"  
  
#cd to computer level  
cd sqlserver:\sql\COMPUTERNAME  
# get the list of instances  
$instances = Get-childitem  
#loop through instances and create a SQL credential, output any errors  
foreach ($instance in $instances)  
{  
    Try  
{  
     new-sqlcredential -Name $credentialName -path "SQLServer:\SQL\$($instance.name)" -Identity $storageAccount -Secret $secureString -ea Stop   
}  
Catch [Exception]  
    {  
  
            write-host "instance - $($instance.name): "$_.Exception.Message  
  
    }  
  
 }  
  
```  
  
### <a name="remove-a-sql-credential-from-all-the-instances-of-sql-server"></a>SQL Server のすべてのインスタンスから SQL 資格情報を削除する  
 このスクリプトは、コンピューターにインストールされているすべての SQL Server インスタンスから特定の資格情報を削除する場合に使用できます。 特定のインスタンスに資格情報オブジェクトが存在しない場合は、エラー メッセージが表示され、すべてのインスタンスが確認されるまでスクリプトが続行されます。  
  
```  
  
import-module sqlps  
  
cd SQLServer:\SQL\COMPUTERNAME  
$credentialName = "mybackuptoURL"  
  
$instances = Get-childitem  
  
foreach ($instance in $instances)  
   {   
    try  
        {  
            $path = "SQLServer:\SQL\$($instance.name)\credentials\$credentialName"   
            Remove-sqlCredential -path $path -ea stop   
         }  
         catch [Exception]  
         {  
            write-host $_.Exception.Message  
  
        }  
  
    }  
```  
  
### <a name="full-database-backup-for-all-databases-including-system-databases"></a>すべてのデータベース (システム データベースを含む) の完全バックアップ  
 次のスクリプトでは、コンピューター上のすべてのデータベースのバックアップを作成します。 これには、ユーザー データベースと **msdb** システム データベースの両方が含まれます。 スクリプトでは、 **tempdb** システム データベースと **model** システム データベースを除外します。  
  
```  
  
import-module sqlps  
# set the parameter values  
$storageAccount = "mystorageaccount"  
$blobContainer = "privatecontainertest"  
$backupUrlContainer = "https://$storageAccount.blob.core.windows.net/$blobContainer/"  
$credentialName = "mybackuptoURL"  
  
# cd to computer level  
  
cd SQLServer:\SQL\COMPUTERNAME  
$instances = Get-childitem   
# loop through each instances and backup up all the  databases -filter out tempdb and model databases  
  
 foreach ($instance in $instances)  
 {  
   $path = "sqlserver:\sql\$($instance.name)\databases"  
   $alldatabases = get-childitem -Force -path $path |Where-object {$_.name -ne "tempdb" -and $_.name -ne "model"}   
  
   $alldatabases | Backup-SqlDatabase -BackupContainer $backupUrlContainer -SqlCredential $credentialName -Compression On -script   
 }  
  
```  
  
### <a name="full-database-backup-for-all-user-databases"></a>すべてのユーザー データベースの完全バックアップ  
 次のスクリプトは、コンピューター上にあるすべての SQL Server インスタンスのユーザー データベースをすべてバックアップするために使用できます。  
  
```  
  
import-module sqlps   
  
$storageAccount = "mystorageaccount"  
$blobContainer = "privatecontainertest"  
$backupUrlContainer = "https://$storageAccount.blob.core.windows.net/$blobContainer/"  
$credentialName = "mybackuptoURL"  
  
# cd to computer level  
  
cd SQLServer:\SQL\COMPUTERNAME  
$instances = Get-childitem   
# loop through each instances and backup up all the user databases  
 foreach ($instance in $instances)  
 {  
    $databases = dir "sqlserver:\sql\$($instance.name)\databases"  
   $databases | Backup-SqlDatabase -BackupContainer $backupUrlContainer -SqlCredential $credentialName -Compression On   
 }  
```  
  
### <a name="full-database-backup-for-master-and-msdb-system-databases-on-all-the-instances-of-sql-server"></a>すべての SQL Server インスタンスの master と msdb (システム データベース) の完全バックアップ  
 次のスクリプトは、コンピューター上にインストールされているすべての SQL Server インスタンスの **master** データベースと **msdb** データベースをバックアップするために使用できます。  
  
```  
  
import-module sqlps  
  
$storageAccount = "mystorageaccount"  
$blobContainer = "privatecontainertest"  
$backupUrlContainer = "https://$storageAccount.blob.core.windows.net/$blobContainer/"  
$credentialName = "mybackupToUrl"  
$sysDbs = "master", "msdb"  
  
#cd to computer level  
cd sqlserver:\sql\COMPUTERNAME  
$instances = Get-childitem   
foreach ($instance in $instances)  
 {  
      foreach ($s in $sysdbs)  
     {  
Backup-SqlDatabase -Database $s -path "sqlserver:\sql\$($instance.name)" -BackupContainer  $backupUrlContainer -SqlCredential $credentialName -Compression On   
}    
 }  
  
```  
  
### <a name="full-database-backup-for-all-user-databases-on-an-instance-of-sql-server"></a>SQL Server インスタンスのすべてのユーザー データベースの完全バックアップ  
 次のスクリプトは、SQL Server の名前付きインスタンスで使用可能なユーザー データベースのみをバックアップするために使用します。 $srvPath パラメーターの値を変更することで、同じスクリプトをコンピューター上の既定インスタンスに使用することもできます。  
  
```  
  
import-module sqlps  
  
$storageAccount = "mystorageaccount"  
$blobContainer = "privatecontainertest"  
$backupUrlContainer = "https://$storageAccount.blob.core.windows.net/$blobContainer/"  
$srvPath = "SQLServer:\SQL\COMPUTERNAME\INSTANCENAME"  # for default instance, the $srvpath variable is "SQLSERVER:\SQL\COMPUTERNAME\DEFAULT"  
$credentialName = "mybackupToUrl"  
  
#cd to computer level  
cd sqlserver:\sql\COMPUTERNAME  
  
#retrieves the database objects for a specific instance  
$databases = dir $srvPath\databases  
  
#backup all the user databases  
$databases | Backup-SqlDatabase -BackupContainer $backupUrlContainer -SqlCredential $credentialName -Compression On  
```  
  
### <a name="full-database-backup-for-only-system-databases-master-and-msdb-on-an-instance-of-sql-server"></a>SQL Server インスタンスのシステム データベース (master と msdb) のみの完全バックアップ  
 次のスクリプトは、SQL Server の名前付きインスタンスの **master** データベースと **msdb** データベースをバックアップするために使用できます。 $srvPath パラメーターの値を変更することで、同じスクリプトをコンピューター上の既定インスタンスに使用することもできます。  
  
```  
  
import-module sqlps  
  
$storageAccount = "mystorageaccount"  
$blobContainer = "privatecontainertest"  
$backupUrlContainer = "https://$storageAccount.blob.core.windows.net/$blobContainer/"  
$srvPath = "SQLServer:\SQL\COMPUTERNAME\INSTANCENAME" # for default instance, the $srvpath variable is "SQLSERVER:\SQL\COMPUTERNAME\DEFAULT"  
$credentialName = "mybackupToUrl"  
  
#navigate to instance level  
cd $srvPath  
  
$sysDbs = "master", "msdb"  
foreach ($s in $sysDbs)   
{  
Backup-SqlDatabase -Database $s -BackupContainer $backupUrlContainer -SqlCredential $credentialName -Compression On  
}  
  
```  
  
## <a name="see-also"></a>参照  
 [SQL Server Backup and Restore with Windows Azure Blob Storage Service](sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md)   
 [SQL Server Backup to URL に関するベスト プラクティスとトラブルシューティング](sql-server-backup-to-url-best-practices-and-troubleshooting.md)  
  
  
