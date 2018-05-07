---
title: SSMA の SAP ASE (SybaseToSQL) のインストール |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/29/2017
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
ms.assetid: 8d5a4ce6-b747-46e3-9184-645d56e8b35c
caps.latest.revision: 6
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 336012819c23b02ac0527a70da930c5b74686e7a
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="installing-ssma-for-sap-ase-sybasetosql"></a>SSMA の SAP ASE (SybaseToSQL) のインストール
[!INCLUDE[msCoName](../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Migration Assistant (SSMA) の SAP Adaptive Server Enterprise (ASE) を SAP ASE からの移行の実行に使用するクライアント アプリケーションから成る[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または Azure SQL データベースです。 移行されたデータベースのデータの移行と ASE システム関数の使用をサポートする拡張機能パックも含まれています。  
  
移行手順を実行するコンピューターにクライアント アプリケーションをインストールします。 実行しているコンピューターに拡張機能パック ファイルのインストール[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]でホストされるようには、データベースを移行します。  
  
## <a name="upgrading-ssma-for-sap-ase"></a>SAP ASE for SSMA をアップグレードします。  
SAP ASE for SSMA の以降のバージョンにアップグレードする場合は、クライアントとサーバーの拡張機能パックをアンインストールする必要があります最初。 新しいバージョンをインストールします。  
  
SAP ASE の SSMA の以前のバージョンからプロジェクトを開く場合 SSMA は、プロジェクトを新しいバージョンに変換するように求めます。 をクリックして**はい**SSMA の新しいバージョンでプロジェクトを使用します。  
  
## <a name="contents"></a>目次  
  
|[アーティクル]|Description|  
|---------|---------------|  
|[SSMA の SAP ASE クライアントのインストール&#40;SybaseToSQL&#41;](../../ssma/sybase/installing-ssma-for-sybase-client-sybasetosql.md)|SSMA for SAP ASE クライアントをインストールするための手順と情報を提供します。|  
|[SSMA コンポーネントを SQL Server インストール&#40;SybaseToSQL&#41;](../../ssma/sybase/installing-ssma-components-on-sql-server-sybasetosql.md)|インスタンスで拡張機能パックをインストールするための手順と情報を提供[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。|  
|[SAP ASE コンポーネントに対して SSMA を削除する&#40;SybaseToSQL&#41;](../../ssma/sybase/removing-ssma-for-sybase-components-sybasetosql.md)|プログラムと拡張機能パックのクライアントをアンインストールするための手順を説明します。|  
  
## <a name="see-also"></a>参照  
[SQL Server - Azure SQL データベースにデータベースを移行する SAP ASE &#40;SybaseToSQL&#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
