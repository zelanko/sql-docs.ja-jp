---
title: Sybase コンポーネント (SybaseToSQL) に対して SSMA を削除する |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssma-sybase
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: aec09593-17d9-4ec2-ac56-3cd8851406fd
caps.latest.revision: 6
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: d59d3d18b4eb5b5ec81cb12422cc16cf64592731
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="removing-ssma-for-sybase-components-sybasetosql"></a>Sybase コンポーネント (SybaseToSQL) に対して SSMA を削除します。
終了したらデータベースから Sybase Adaptive Server Enterprise (ASE) への移行[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]、SSMA コンポーネントをアンインストールする場合があります。 いつでも、クライアント コンポーネントをアンインストールすることができますが、拡張機能パックからをアンインストールしないでください[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]ない場合は、移行されたデータベースが不要になったで関数を使用していることを確認して、 **ssma_syb**のスキーマ、 **sysdb**データベース。  
  
## <a name="uninstalling-the-ssma-for-sybase-client"></a>Sybase クライアントの SSMA をアンインストールしています  
SSMA をアンインストールするを使用**プログラム追加と削除**です。  
  
**SSMA をアンインストールするには**  
  
1.  コントロール パネルで、開く**プログラム追加と削除**です。  
  
2.  選択**Microsoft SQL Server Migration Assistant for Sybase**、クリックして**削除**です。  
  
3.  SSMA をアンインストールすることを確認する をクリックして**はい**です。  
  
## <a name="uninstalling-the-extension-pack"></a>拡張機能パックをアンインストールします。  
移行したデータベースが内のオブジェクトを使用しないことを確認する場合は、 **sysdb.ssma_syb**スキーマを使用して、拡張機能パックを削除することができます**プログラム追加と削除**です。  
  
拡張機能パックをアンインストールするには  
  
1.  コントロール パネルで、開く**プログラム追加と削除**です。  
  
2.  選択**Microsoft SQL Server Migration Assistant for Sybase 拡張機能パック**、クリックして**削除**です。  
  
3.  拡張機能パックをアンインストールすることを確認する をクリックして**はい**です。  
  
4.  ユーティリティのデータベースのスクリプト ページで、インスタンスで次のようにクリックします。**次**です。  
  
5.  接続パラメーター ページで、認証方法を選択し、をクリックして**次**です。  
  
    Windows 認証は SQL Server のインスタンスにログオンしようとするのに Windows 資格情報を使用します。 SQL Server 認証を選択した場合は、SQL Server ログイン名とパスワードを入力する必要があります。  
  
6.  操作の完了 ページで、 **OK**です。  
  
7.  [完了] ページで、をクリックして**終了**です。  
  
をアンインストールした後できることを確認して、 **sysdb.ssma_syb**スキーマ、および場合によっては、全体**sysdb**データベースを使用して、が取り外されて[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)]です。 ただし、他の SSMA 製品を使用する場合も使用、 **sysdb**データベース。 場合は、データベースが存在し、他のデータベースにはこのデータベース内のオブジェクトが参照されていないことを確認して、データベースをデタッチすることができます。  
  
## <a name="see-also"></a>参照  
[SSMA の Sybase クライアントのインストール&#40;SybaseToSQL&#41;](../../ssma/sybase/installing-ssma-for-sybase-client-sybasetosql.md)  
[SSMA コンポーネントを SQL Server インストール&#40;SybaseToSQL&#41;](../../ssma/sybase/installing-ssma-components-on-sql-server-sybasetosql.md)  
  
