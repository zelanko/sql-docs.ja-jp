---
title: "MSSQL_ENG014117 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSSQL_ENG014117 エラー"
ms.assetid: e5906a76-9511-4c47-8826-8c765b58a39d
caps.latest.revision: 18
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 17
---
# MSSQL_ENG014117
    
## メッセージの詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|14117|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|シンボル名||  
|メッセージ テキスト|'%s' はディストリビューション データベースとして構成されていません。|  
  
## 説明  
 このエラーは、次のいずれかまたは両方に該当する場合に発生する可能性があります。  
  
-   指定されたディストリビューション データベースのエントリが表示されない **msdb.MSdistributiondbs**します。  
  
-   ローカル サーバーのエントリがない、 **マスター** データベース、またはエントリをあるが正しくありません。  
  
     レプリケーションでは、コンピューター名とオプションのインスタンス名 (クラスター化されたインスタンスの場合は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 仮想サーバー名とオプションのインスタンス名) を使用して、トポロジのすべてのサーバーを登録する必要があります。 レプリケーションが正しく機能するためには、トポロジの各サーバーに対して `SELECT @@SERVERNAME` によって返された値が、コンピューター名または仮想サーバー名と、オプションのインスタンス名で一致している必要があります。  
  
     [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスのいずれかを IP アドレスまたは完全修飾ドメイン名 (FQDN) で登録している場合、レプリケーションはサポートされません。 レプリケーションの構成時に、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 内に IP アドレスまたは FQDN で登録された [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] インスタンスがあった場合、このエラーが発生する可能性があります。  
  
## ユーザーの操作  
 ディストリビューター インスタンスが正しく登録されているかどうかを確認します。 コンピューターのネットワーク名と SQL Server インスタンスの名前が異なる場合は、次のいずれかを実行してください。  
  
-   SQL Server インスタンス名を有効なネットワーク名として追加します。 代替ネットワーク名を設定する 1 つの方法は、その名前をローカル ホスト ファイルに追加することです。 ローカル ホスト ファイルは、既定では、WINDOWS\system32\drivers\etc または WINNT\system32\drivers\etc にあります。詳細については、Windows のマニュアルを参照してください。  
  
     たとえば、コンピューター名が comp1、そのコンピューターの IP アドレスが 10.193.17.129、インスタンス名が inst1/instname の場合、ホスト ファイルに次のエントリを追加します。  
  
     10.193.17.129 inst1  
  
-   ディストリビューションを無効化し、インスタンスを登録して、ディストリビューションを再設定してください。 @@SERVERNAME の値が、クラスター化されていないインスタンスに対して適切でない場合は、次の手順を実行してください。  
  
    ```  
    sp_dropserver '<old_name>', 'droplogins'  
    go  
    sp_addserver '<new_name>', 'local'  
    go  
    ```  
  
     実行した後、 [sp_addserver & #40 です。Transact SQL と #41;](../../relational-databases/system-stored-procedures/sp-addserver-transact-sql.md) 再起動が必要なストアド プロシージャ、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 変更 @@SERVERNAME を有効にするにはサービスです。  
  
     @@SERVERNAME の値がクラスター化されたインスタンスに対して適切でない場合は、クラスター アドミニストレーターを使用して名前を変更する必要があります。 詳細については、次を参照してください。 [AlwaysOn フェールオーバー クラスター インスタンスと #40 です。SQL Server と #41;](../Topic/AlwaysOn%20Failover%20Cluster%20Instances%20\(SQL%20Server\).md)します。  
  
 ディストリビューター インスタンスが正しく登録されていることを確認した後にディストリビューション データベースが表示されることを確認します **msdb.MSdistributiondbs**します。 表示されていない場合は、次の手順を実行します。  
  
1.  ディストリビューション構成のスクリプトを作成します。 詳しくは、「 [Scripting Replication](../../relational-databases/replication/scripting-replication.md)」をご覧ください。  
  
2.  ディストリビューションを無効化してから、再度有効化します。 詳細については、次を参照してください。 [ディストリビューションの構成](../../relational-databases/replication/configure-distribution.md)します。  
  
## 参照  
 [エラーとイベントのリファレンスと #40 です。レプリケーションと #41 です。](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  