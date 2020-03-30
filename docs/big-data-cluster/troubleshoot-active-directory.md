---
title: Active Directory モードでの展開のトラブルシューティング
titleSuffix: SQL Server Big Data Cluster
description: Active Directory ドメインの SQL Server ビッグ データ クラスターの展開に関するトラブルシューティングを行います。
author: rl-msft
ms.author: rafidl
ms.reviewer: mikeray
ms.date: 03/12/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 5d887eadd021641241516a1478c6ac13e0d0bdec
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/29/2020
ms.locfileid: "79191213"
---
# <a name="troubleshoot-sql-server-big-data-cluster-active-directory-mode-deployment"></a>Active Directory モードでの SQL Server ビッグ データ クラスターの展開に関するトラブルシューティング

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

この記事では、Active Directory モードでの SQL Server ビッグ データ クラスターの展開に関するトラブルシューティングについて説明します。

## <a name="check-deployment-progress"></a>展開の進行状況を確認する

デプロイには数分かかることがあります。 15 分経ってもクラスターの準備ができていない場合は、コントローラー ログで詳細を確認してください。

クラスターの展開中にポッドを確認します。

```console
kubectl get pods -n mssql-cluster
```

返されたポッドの一覧に次のものが含まれていることを確認します。

- `compute-`$
- `data-`
- `storage-`

コンピューティング、データ、およびストレージ ポッドが作成されていない場合は、ログを確認して原因を特定します。

## <a name="check-logs"></a>ログを確認する

コンピューティング、データ、またはストレージ ポッドを作成せずに展開が終了する理由を特定するには、次のログを確認します。 

- `controller.log` (`<folderOfDebugCopyLog>\debuglogs-mssql-cluster-20200219-093941\mssql-cluster\control-<suffix>\controller\controller\<date>\controller.log`) を確認します。 次のエントリを探します。

  `WARN | StatefulSet master is not ready with 0 ready pods and 3 unready pods `

- `master-0` `provisioner.log` (`<folderOfDebugCopyLog>\debuglogs-mssql-cluster-20200219-093941\mssql-cluster\master-0\mssql-server\provisioner\provisioner.log`) を確認します。

  ```
  ERROR | Failed to create sql login for domain user [<domain>.<top-level-domain>\<domain-group>]
    Traceback (most recent call last):
      File "/opt/provisioner/bin/scripts/provisioningpool.py", line 214, in executeNonQueries
        connection.execute_non_query(command)
      File "src/_mssql.pyx", line 1033, in _mssql.MSSQLConnection.execute_non_query
      File "src/_mssql.pyx", line 1061, in _mssql.MSSQLConnection.execute_non_query
      File "src/_mssql.pyx", line 1634, in _mssql.check_and_raise
      File "src/_mssql.pyx", line 1683, in _mssql.maybe_raise_MSSQLDatabaseException
    _mssql.MSSQLDatabaseException: (15401, b"Windows NT user or group '<domain>.<top-level-domain>\\<domain-group>' not found. Check the name again.DB-Lib error message 20018, severity 16:\nGeneral SQL Server error: Check messages from the SQL Server\n")
  WARNING | [3/3] Provisioning exception occurred during provisioning step: ProvisioningMasterPool.
  WARNING | Failed to create sql login for domain user [<domain>.<top-level-domain>\<domain-group>]
  WARNING | Retrying.
  ```

  上の例では、ドメイン グループのスコープがドメイン ローカルなので、ドメイン ユーザーのログインが作成されずに展開は失敗します。 ドメイン グローバルまたはドメイン ユニバーサルのスコープを持つグループを使用します。 「[Active Directory モードで [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]を展開する](deploy-active-directory.md)」では、AD グループのスコープ要件について説明されています。

## <a name="check-the-scope-of-domain-groups"></a>ドメイン グループのスコープを確認します。

ドメイン グループのスコープ (<`domain-group`>) を確認します。 [get-adgroup](/powershell/module/addsadministration/get-adgroup/) を使用します。

`<domain-group>` グループのスコープがドメイン ローカル (`DomainLocal`) の場合、展開は失敗します。 

次の PowerShell スクリプトでは、`bdcadmins` および `bdcusers` という名前の 2 つの AD グループのスコープを確認します。 名前をグループの名前に置き換えます。 

```powershell
#Administrators and users AD groups
$Cluster_admins_group='bdcadmins'
$Cluster_users_group='bdcusers'

#Performing AD Group Checks...

#AD admin group Check
$ClusterAdminGroupScope_Result = New-Object System.Collections.ArrayList
try {
    $GroupScope = Get-ADgroup -Identity $Cluster_admins_group | Select-Object -ExpandProperty GroupScope
    
    if ($GroupScope -eq 'DomainLocal') {
        [void]$ClusterAdminGroupScope_Result.Add("Misconfiguration - $Cluster_admins_group Group scope is $GroupScope, this scope is not supported, Please change group scope to either Global or Univesal") 
    }
    else {
        [void]$ClusterAdminGroupScope_Result.Add("OK - $Cluster_admins_group Group scope is $GroupScope")
    }
}
catch {
    [void]$ClusterAdminGroupScope_Result.Add("Error - " + $_.exception.message)
}
#Ad users group check
$ClusterUsersGroupScope_Result = New-Object System.Collections.ArrayList
$GroupScope = ''
try {
    $GroupScope = Get-ADgroup -Identity $Cluster_users_group | Select-Object -ExpandProperty GroupScope
    
    if ($GroupScope -eq 'DomainLocal') {
        [void]$ClusterUsersGroupScope_Result.Add("Misconfiguration - $Cluster_users_group Group scope is $GroupScope, this scope is not supported, Please change group scope to either Global or Univesal")
    } 
    else 
    { [void]$ClusterUsersGroupScope_Result.Add("OK - $Cluster_users_group Group scope is $GroupScope") }
}
catch {
    [void]$ClusterUsersGroupScope_Result.Add("Error - " + $_.exception.message)
}

#Display the results
$ClusterUsersGroupScope_Result
```

## <a name="check-security-support-container"></a>セキュリティ サポート コンテナーを確認する 

セキュリティ サポート コンテナーのログを確認します。

次のコマンドでは、名前空間 `mssql-cluster` にあるクラスターのセキュリティ サポート ログを収集します。

```console
azdata bdc debug copy-logs -n mssql-cluster -c security-support
```

ログを抽出し、`\mssql-cluster\control-<identifier>\controller\control-rts5t-controller-stdout.log` を見つけます。

ログで次のエントリを探します。

```
ERROR    | Failed to create AD user account 'cntrl-controller'. Error code: 53. Message: Failed to create user object: Failed to add object 'CN=cntrl-controller,OU=bdc, DC=CONTOSO, DC=com' to '  <domain>.<top-level-domain>  ': Server is unwilling to perform. 
ERROR | Failed to create AD user account 'ldap-user'. Error code: 53. Message: Failed to create user object: Failed to add object 'CN=ldap-user,OU=bdc, DC=CONTOSO, DC=com' to '  <domain>.<top-level-domain>  ': Server is unwilling to perform. 
ERROR | Failed to create AD user account 'nginx-mgmtproxy'. Error code: 53. Message: Failed to create user object: Failed to add object 'CN=nginx-mgmtproxy,OU=bdc, DC=CONTOSO, DC=com' to '  <domain>.<top-level-domain>  ': Server is unwilling to perform.
```

これらのエントリは、ドメイン コントローラーの DNS サーバーに逆引き DNS エントリ (PTR レコード) がない場合に発生する可能性があります。

## <a name="verify-reverse-lookup-ptr-record"></a>逆引き検索 (PTR レコード) を検証する
    
次の PowerShell スクリプトを実行して、逆引き DNS エントリ (PTR レコード) が構成されているかどうかを確認します。

```powershell
#Domain Controller FQDN 'DCserver01.contoso.local'
$Domain_controller_FQDN = 'DCserver01.contoso.local'

#Performing Domain Controller DNS record, reverse PTR Checks...
$DcControllerDnsPtr_Result = New-Object System.Collections.ArrayList
try {
    $Domain_controller_DNS_Record = Resolve-DnsName $Domain_controller_FQDN -Type A -Server $Domain_DNS_IP_address -ErrorAction Stop
    foreach ($ip in $Domain_controller_DNS_Record.IPAddress) {
        #resolving hostname by IP address to make sure we have reverse PTR record 
        if ((Resolve-DnsName $ip).NameHost -eq $Domain_controller_FQDN) {
            [void]$DcControllerDnsPtr_Result.add("OK - $Domain_controller_FQDN has an A record with an IP $ip, Reverse PTR record is in place") 
        }
        else {
            [void]$DcControllerDnsPtr_Result.add("Missing - $Domain_controller_FQDN has an A record with an IP $ip, But no reverse PTR record was found for the host")
        }
    }
}
catch {
    [void]$DcControllerDnsPtr_Result.add("Error - " + $_.exception.message)
}

#show the results 
$DcControllerDnsPtr_Result
```

[ドメイン コントローラーの逆引き DNS エントリ (PTR レコード) を検証します](deploy-active-directory.md#verify-reverse-dns-entry-for-domain-controller)。