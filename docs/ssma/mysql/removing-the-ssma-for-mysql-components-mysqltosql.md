---
title: "MySQL コンポーネント (MySQLToSql) に対して、SSMA を削除する |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssma-mysql
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- Uninstalling, Extension pack
- Uninstalling, SSMA for MySQL client
ms.assetid: 87cdbd49-a0c9-4b00-8a93-34188b18d11a
caps.latest.revision: "10"
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 504a35ff20ee162bef8e2524cc382dde190fb3e5
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="removing-the-ssma-for-mysql-components-mysqltosql"></a>MySQL コンポーネント (MySQLToSql) に対して、SSMA を削除します。
終了したらに mysql データベースを移行する[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]、SSMA コンポーネントをアンインストールする場合があります。 クライアント コンポーネントは、いつでもアンインストールできます。 ただし、拡張機能パックからをアンインストールする場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]、次に、SSMA をサポートしなく MySQL からサーバー側のデータ移行のエンジンを使用して、ターゲット データベース (SQL Server または SQL Azure) へのデータの移行。  
  
## <a name="uninstalling-the-ssma-for-mysql-client"></a>SSMA の MySQL クライアントのアンインストール  
SSMA をアンインストールするを使用**プログラム追加と削除**です。  
  
**SSMA をアンインストールするには**  
  
1.  コントロール パネルで、開く**プログラム追加と削除**です。  
  
2.  選択**Microsoft SQL Server Migration Assistant for MySQL**、クリックして**削除**です。  
  
3.  SSMA をアンインストールすることを確認する をクリックして**はい**です。  
  
## <a name="uninstalling-the-extension-pack"></a>拡張機能パックをアンインストールします。  
使用して、拡張機能パックを削除することができます**プログラム追加と削除**です。  
  
**拡張機能パックをアンインストールするには**  
  
1.  コントロール パネルで、開く**プログラム追加と削除**です。  
  
2.  選択**Microsoft SQL Server Migration Assistant for MySQL の拡張機能パック**、クリックして**削除**です。  
  
3.  拡張機能パックをアンインストールすることを確認する をクリックして**はい**です。  
  
4.  ユーティリティ データベース スクリプト ページで、インスタンスでインスタンスを選択し、をクリックして**次**です。  
  
5.  接続パラメーター ページで、認証方法を選択し、をクリックして**次**です。  
  
    Windows 認証は、Windows 資格情報を使用してのインスタンスにログオンしよう[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。 選択した場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]を入力する必要があります、認証、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]ログイン名とパスワード。  
  
6.  操作の完了 ページで、 **OK**です。  
  
7.  [完了] ページで、をクリックして**終了**です。  
  
オブジェクトを確認するには、アンインストール プロセスが完了した後、 **sysdb.ssma_MySQL**スキーマ、および場合によっては、全体**sysdb**データベースを使用して、取り外されて[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)]です。 ただし、他の SSMA 製品を使用する場合も使用、 **sysdb**データベース。 場合は、データベースが存在し、このデータベース内のオブジェクトに他のデータベースが参照されていないことを確認したら、データベースをデタッチすることができます。  
  
## <a name="see-also"></a>参照  
[SSMA の MySQL クライアント &#40; のインストールMySQLToSQL &#41;](../../ssma/mysql/installing-ssma-for-mysql-client-mysqltosql.md)  
[SQL Server での SSMA コンポーネントのインストール](http://msdn.microsoft.com/en-us/6772d0c5-258f-4d7b-afb0-b5f810e71af1)  
  
