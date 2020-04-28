---
title: SSMA for SAP ASE のインストール (SybaseToSQL) |Microsoft Docs
ms.custom: ''
ms.date: 11/29/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 8d5a4ce6-b747-46e3-9184-645d56e8b35c
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 91a4dfcf8add3900c51e33a6e40fa874ce9f9798
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "68028974"
---
# <a name="installing-ssma-for-sap-ase-sybasetosql"></a>SSMA for SAP ASE のインストール (SybaseToSQL)
[!INCLUDE[msCoName](../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]SAP Adaptive Server Enterprise (ASE) の Migration Assistant (SSMA) は、SAP ASE からまたは Azure SQL Database へ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の移行を実行するために使用するクライアントアプリケーションで構成されています。 また、データの移行と、移行したデータベースでの ASE システム関数の使用をサポートする拡張パックも含まれています。  
  
移行手順を実行するコンピューターにクライアントアプリケーションをインストールします。 を実行[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]しているコンピューターに、移行されたデータベースをホストする拡張パックファイルをインストールします。  
  
## <a name="upgrading-ssma-for-sap-ase"></a>SSMA for SAP ASE のアップグレード  
SSMA for SAP ASE の新しいバージョンにアップグレードする場合は、最初にクライアントとサーバー拡張機能パックをアンインストールする必要があります。 その後、新しいバージョンをインストールします。  
  
以前のバージョンの SSMA for SAP ASE からプロジェクトを開くと、プロジェクトを新しいバージョンに変換するかどうかを確認するメッセージが表示されます。 新しいバージョンの SSMA でプロジェクトを使用する場合は、[**はい**] をクリックします。  
  
## <a name="contents"></a>内容  
  
|[アーティクル]|説明|  
|---------|---------------|  
|[SSMA for SAP ASE クライアント &#40;SybaseToSQL&#41;のインストール](../../ssma/sybase/installing-ssma-for-sybase-client-sybasetosql.md)|SSMA for SAP ASE クライアントをインストールするための情報と手順について説明します。|  
|[SSMA コンポーネントの SQL Server &#40;SybaseToSQL&#41;のインストール](../../ssma/sybase/installing-ssma-components-on-sql-server-sybasetosql.md)|の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンスに拡張機能パックをインストールするための情報と手順について説明します。|  
|[SSMA for SAP ASE コンポーネントの削除 &#40;SybaseToSQL&#41;](../../ssma/sybase/removing-ssma-for-sybase-components-sybasetosql.md)|クライアントプログラムと拡張機能パックをアンインストールする手順について説明します。|  
  
## <a name="see-also"></a>関連項目  
[SAP ASE データベースの SQL Server Azure SQL Database &#40;SybaseToSQL&#41;への移行](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
