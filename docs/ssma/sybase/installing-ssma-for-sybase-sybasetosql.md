---
title: "SSMA の SAP ASE (SybaseToSQL) のインストール |Microsoft ドキュメント"
ms.custom: 
ms.date: 09/30/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 8d5a4ce6-b747-46e3-9184-645d56e8b35c
caps.latest.revision: 6
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 759a7084024e1c608431683de6dae5a6fb40304e
ms.openlocfilehash: 7b2c96006c5495c89486c8a86e1b60b64f2dd22c
ms.contentlocale: ja-jp
ms.lasthandoff: 10/03/2017

---
# <a name="installing-ssma-for-sap-ase-sybasetosql"></a>SSMA の SAP ASE (SybaseToSQL) のインストール
[!INCLUDE[msCoName](../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]Migration Assistant (SSMA) の SAP ASE から SAP Adaptive Server Enterprise (ASE) への移行を実行に使用するクライアント アプリケーションから成る[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または Azure SQL データベースです。 移行されたデータベースのデータの移行と ASE システム関数の使用をサポートする拡張機能パックも含まれています。  
  
元となるは、移行手順を実行するコンピューター上には、クライアント アプリケーションをインストールします。 実行しているコンピューター上の拡張機能パック ファイルをインストールする必要があります[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]移行されたデータベースをホストします。  
  
## <a name="upgrading-ssma-for-sybase"></a>アップグレードの SSMA for Sybase  
SAP ASE SSMA の以降のバージョンにアップグレードする場合は、まず、クライアントとサーバーの拡張機能パックをアンインストールして、新しいバージョンをインストールします。  
  
SAP ASE の SSMA の以前のバージョンからプロジェクトを開く場合 SSMA は、プロジェクトを新しいバージョンに変換するように求めます。 クリックする必要があります**はい**SSMA の新しいバージョンでプロジェクトを使用します。  
  
## <a name="contents"></a>目次  
  
|トピック|Description|  
|---------|---------------|  
|[SSMA の SAP ASE クライアント &#40; のインストールSybaseToSQL &#41;](../../ssma/sybase/installing-ssma-for-sybase-client-sybasetosql.md)|SSMA クライアントをインストールするための手順と情報を提供します。|  
|[SQL Server &#40; SSMA コンポーネントをインストールします。SybaseToSQL &#41;](../../ssma/sybase/installing-ssma-components-on-sql-server-sybasetosql.md)|インスタンスで拡張機能パックをインストールするための手順と情報を提供[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。|  
|[SAP ASE コンポーネント &#40; に対して SSMA を削除します。SybaseToSQL &#41;](../../ssma/sybase/removing-ssma-for-sybase-components-sybasetosql.md)|プログラムと拡張機能パックのクライアントをアンインストールするための手順を説明します。|  
  
## <a name="see-also"></a>参照  
[SAP ASE データベース Azure SQL データベース &#40; SQL Server - への移行SybaseToSQL &#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  

