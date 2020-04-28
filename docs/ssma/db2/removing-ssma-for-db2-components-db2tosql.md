---
title: SSMA for DB2 コンポーネントの削除 (DB2ToSQL) |Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 4ee0d698-6246-48eb-b963-d62be81cab6a
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 25c8222009c2ea9358c0bab2ad5ae077588fb3cb
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "68060092"
---
# <a name="removing-ssma-for-db2-components-db2tosql"></a>SSMA for DB2 コンポーネントの削除 (DB2ToSQL)
DB2 からへ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のデータベースの移行が完了したら、ssma コンポーネントのアンインストールが必要になる場合があります。 クライアントコンポーネントはいつでもアンインストールできます。 ただし、移行したデータベースで**sysdb**データベース[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の**ssma_DB2**スキーマの関数が使用されなくなっていない限り、から拡張パックをアンインストールしないでください。  
  
## <a name="uninstalling-the-ssma-for-db2-client"></a>SSMA for DB2 クライアントのアンインストール  
SSMA をアンインストールするには、[**プログラムの追加と削除**] を使用します。  
  
**SSMA をアンインストールするには**  
  
1.  [コントロール] パネルで **[プログラムの追加と削除]** を開きます。  
  
2.  ** [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] DB2 の Migration Assistant**を選択し、[**削除**] をクリックします。  
  
3.  SSMA をアンインストールすることを確認するには、[**はい**] をクリックします。  
  
## <a name="uninstalling-the-extension-pack"></a>拡張機能パックのアンインストール  
移行したデータベースが**sysdb. ssma_DB2**スキーマのオブジェクトを使用していないことが確実な場合は、スキーマから拡張機能パックを削除することにより、拡張パックを削除できます。 Windows のアンインストールはありません。  
  
## <a name="see-also"></a>参照  
[SSMA for DB2 クライアント &#40;DB2ToSQL&#41;のインストール](../../ssma/db2/installing-ssma-for-db2-client-db2tosql.md)  
[SQL Server &#40;DB2ToSQL&#41;での SSMA コンポーネントのインストール](../../ssma/db2/installing-ssma-components-on-sql-server-db2tosql.md)  
  
