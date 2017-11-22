---
title: "SSMA を削除する DB2 コンポーネント (DB2ToSQL) |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 4ee0d698-6246-48eb-b963-d62be81cab6a
caps.latest.revision: "6"
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 2a7b78b858bc4af9820dd919d46d38e283920c1f
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="removing-ssma-for-db2-components-db2tosql"></a>DB2 コンポーネント (DB2ToSQL) に対して SSMA を削除します。
終了したらを DB2 からデータベースを移行する[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]、SSMA コンポーネントをアンインストールする場合があります。 クライアント コンポーネントは、いつでもアンインストールできます。 ただしから、拡張機能パックをアンインストールする必要がありますいない[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]、移行されたデータベースが不要になった関数を使用する場合を除き、 **ssma_DB2**のスキーマ、 **sysdb**データベース。  
  
## <a name="uninstalling-the-ssma-for-db2-client"></a>SSMA の DB2 クライアントのアンインストール  
SSMA をアンインストールするを使用**プログラム追加と削除**です。  
  
**SSMA をアンインストールするには**  
  
1.  コントロール パネルで、開く**プログラム追加と削除**です。  
  
2.  選択 **[!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Migration Assistant for DB2**、クリックして**削除**です。  
  
3.  SSMA をアンインストールすることを確認する をクリックして**はい**です。  
  
## <a name="uninstalling-the-extension-pack"></a>拡張機能パックをアンインストールします。  
移行したデータベースが内のオブジェクトを使用しないことを確認する場合は、 **sysdb.ssma_DB2**スキーマ、スキーマから削除して、拡張機能パックを削除する – は Windows のアンインストールはありません  
  
## <a name="see-also"></a>参照  
[SSMA の DB2 クライアント &#40;DB2ToSQL&#41; のインストール](../../ssma/db2/installing-ssma-for-db2-client-db2tosql.md)  
[SQL Server &#40;DB2ToSQL&#41; SSMA コンポーネントをインストールします。](../../ssma/db2/installing-ssma-components-on-sql-server-db2tosql.md)  
  
