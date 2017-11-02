---
title: "Oracle コンポーネント (OracleToSQL) に対して SSMA を削除する |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Uninstalling the Extension Pack
ms.assetid: 8b527a56-4e52-487a-9ac9-2320388e6d7d
caps.latest.revision: 6
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: b0a8ea64d46ae878e9e40e98a0b302ceb0850d90
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="removing-ssma--for-oracle-components-oracletosql"></a>Oracle コンポーネント (OracleToSQL) に対して SSMA を削除します。
終了したらに Oracle からデータベースを移行する[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]、SSMA コンポーネントをアンインストールする場合があります。 クライアント コンポーネントは、いつでもアンインストールできます。 ただしから、拡張機能パックをアンインストールする必要がありますいない[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]、移行されたデータベースが不要になった関数を使用する場合を除き、 **ssma_oracle**のスキーマ、 **sysdb**データベース。  
  
## <a name="uninstalling-the-ssma-for-oracle-client"></a>Oracle クライアントの SSMA をアンインストールしています  
SSMA をアンインストールするを使用**プログラム追加と削除**です。  
  
**SSMA をアンインストールするには**  
  
1.  コントロール パネルで、開く**プログラム追加と削除**です。  
  
2.  選択 **[!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Migration Assistant for Oracle**、クリックして**削除**です。  
  
3.  SSMA をアンインストールすることを確認する をクリックして**はい**です。  
  
## <a name="uninstalling-the-extension-pack"></a>拡張機能パックをアンインストールします。  
移行したデータベースが内のオブジェクトを使用しないことを確認する場合は、 **sysdb.ssma_oracle**スキーマを使用して、拡張機能パックを削除することができます**プログラム追加と削除**です。  
  
**拡張機能パックをアンインストールするには**  
  
1.  コントロール パネルで、開く**プログラム追加と削除**です。  
  
2.  選択**Microsoft SQL Server Migration Assistant for Oracle の拡張機能パック**、クリックして**削除**です。  
  
3.  拡張機能パックをアンインストールすることを確認する をクリックして**はい**です。  
  
4.  ユーティリティ データベース スクリプト ページで、インスタンスでインスタンスを選択し、をクリックして**次**です。  
  
5.  接続パラメーター ページで、認証方法を選択し、をクリックして**次**です。  
  
    Windows 認証は、Windows 資格情報を使用してのインスタンスにログオンしよう[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。 選択した場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]を入力する必要があります、認証、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]ログイン名とパスワード。  
  
6.  操作の完了 ページで、 **OK**です。  
  
7.  [完了] ページで、をクリックして**終了**です。  
  
アンインストール後にオブジェクトを確認できます、 **sysdb.ssma_oracle**スキーマ、および場合によっては、全体**sysdb**データベースを使用して、取り外されて[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)]です。 ただし、他の SSMA 製品を使用する場合も使用、 **sysdb**データベース。 場合は、データベースが存在し、他のデータベースにはこのデータベース内のオブジェクトが参照されていないことを確認して、データベースをデタッチすることができます。  
  
## <a name="see-also"></a>参照  
[Oracle クライアント &#40;OracleToSQL"&"#41 です。 SSMA をインストールします。](../../ssma/oracle/installing-ssma-for-oracle-client-oracletosql.md)  
[SQL Server &#40;OracleToSQL&#41; SSMA コンポーネントをインストールします。](../../ssma/oracle/installing-ssma-components-on-sql-server-oracletosql.md)  
  

