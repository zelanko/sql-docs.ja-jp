---
title: MSSQL_ENG014010 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG014010 error
ms.assetid: 6ea84f2f-e7a2-4028-9ea9-af0d2eba660e
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: eb0387cebdda52817143e0e3da98c20f4c49da50
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "62667089"
---
# <a name="mssqleng014010"></a>MSSQL_ENG014010
    
## <a name="message-details"></a>メッセージの詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|14010|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|シンボル名||  
|メッセージ テキスト|サーバー '%s' はサブスクリプション サーバーとして定義されていません。|  
  
## <a name="explanation"></a>説明  
 レプリケーションでは、コンピューター名とオプションのインスタンス名 (クラスター化されたインスタンスの場合は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 仮想サーバー名とオプションのインスタンス名) を使用して、トポロジのすべてのサーバーを登録する必要があります。 レプリケーションが正しく機能するためには、トポロジの各サーバーに対して `SELECT @@SERVERNAME` によって返された値が、コンピューター名または仮想サーバー名と、オプションのインスタンス名で一致している必要があります。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスのいずれかを IP アドレスまたは完全修飾ドメイン名 (FQDN) で登録している場合、レプリケーションはサポートされません。 レプリケーションを構成するときに、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] インスタンスのいずれかを IP アドレスまたは FQDN で登録した場合、このエラーが発生することがあります。  
  
## <a name="user-action"></a>ユーザーの操作  
 トポロジのすべての [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスが適切に登録されていることを確認してください。 コンピューターのネットワーク名と SQL Server インスタンスの名前が異なる場合は、次のいずれかを実行してください。  
  
-   SQL Server インスタンス名を有効なネットワーク名として追加します。 代替ネットワーク名を設定する 1 つの方法は、その名前をローカル ホスト ファイルに追加することです。 ローカル ホスト ファイルは、既定では、WINDOWS\system32\drivers\etc または WINNT\system32\drivers\etc にあります。詳細については、Windows のマニュアルを参照してください。  
  
     たとえば、コンピューター名が comp1、そのコンピューターの IP アドレスが 10.193.17.129、インスタンス名が inst1/instname の場合、ホスト ファイルに次のエントリを追加します。  
  
     10.193.17.129 inst1  
  
-   レプリケーションを削除し、各 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスを登録して、レプリケーションを再設定します。 @@SERVERNAME の値が、クラスター化されていないインスタンスに対して適切でない場合は、次の手順を実行してください。  
  
    ```  
    sp_dropserver '<old_name>', 'droplogins'  
    go  
    sp_addserver '<new_name>', 'local'  
    go  
    ```  
  
     [sp_addserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addserver-transact-sql) ストアド プロシージャを実行したら、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービスを再起動し、@@SERVERNAME への変更を有効にする必要があります。  
  
     @@SERVERNAME の値がクラスター化されたインスタンスに対して適切でない場合は、クラスター アドミニストレーターを使用して名前を変更する必要があります。 詳細については、「[Always On フェールオーバー クラスター インスタンス &#40;SQL Server&#41;](../../sql-server/failover-clusters/windows/always-on-failover-cluster-instances-sql-server.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [@@SERVERNAME &#40;Transact-SQL&#41;](/sql/t-sql/functions/servername-transact-sql)   
 [エラーとイベントのリファレンス &#40;レプリケーション&#41;](errors-and-events-reference-replication.md)  
  
  
