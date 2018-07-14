---
title: SQL Server インストールの新機能 | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- installing SQL Server, what's new
- SQL Server, what's new
- SQL Server, installing
ms.assetid: c8642a96-3a09-4ec7-a9c3-c539147e6330
caps.latest.revision: 60
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 41721eea4f1e4b58f5d1e6a1d6ae99bbebc71ff5
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37255324"
---
# <a name="what39s-new-in-sql-server-installation"></a>SQL Server インストールの新機能
  Windows Vista は、[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] のサポート対象のオペレーティング システムではありません。 Service Pack 1 は、[!INCLUDE[win7](../../includes/win7-md.md)] および [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] の各オペレーティング システムの場合の最小要件として残されています。 オペレーティング システムの要件の詳細については、次を参照してください。 [Hardware and Software Requirements for Installing SQL Server 2014](hardware-and-software-requirements-for-installing-sql-server.md)します。  
  
 [!INCLUDE[ssExpCurrent](../../includes/ssexpcurrent-md.md)] のインストール時には、抽出されたパッケージを保存するディレクトリを指定するように求められます。 場所が入力されていない場合、[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] では、既定でコンピューターのシステム ドライブが使用されます。 抽出されたファイルは、 [!INCLUDE[ssExpCurrent](../../includes/ssexpcurrent-md.md)] のインストールが完了した後も残ります。  
  
 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] では、SysPrep は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のすべてのインストールでサポートされています。 現在、SysPrep はフェールオーバー クラスターのインストールをサポートしています。 詳細については、次を参照してください。 [SysPrep を使用して SQL Server のインストールに関する考慮事項](../../database-engine/install-windows/considerations-for-installing-sql-server-using-sysprep.md)と[SQL Server 2014 を使用して SysPrep インストール](../../database-engine/install-windows/install-sql-server-using-sysprep.md)します。  
  
 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] からのアップグレードはサポートされていますが、並列使用はサポートされていません。 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] の [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]サポートに関する詳細については、「 [サポートされているバージョンとエディションのアップグレード](../../database-engine/install-windows/supported-version-and-edition-upgrades.md)」を参照してください。  
  
 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]以降では、Standard Edition のデータベース エンジンのメモリ領域は 128 GB です。 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] では、Standard Edition のデータベース エンジンのメモリ領域は 64 GB でした。  
  
## <a name="see-also"></a>参照  
 [SQL Server 2014 の新機能新機能](../what-s-new-in-sql-server-2016.md)   
 [SQL Server 2014 の製品仕様](../../../2014/getting-started/sql-server-2014-product-specifications.md)   
 [SQL Server のインストール計画](../../../2014/sql-server/install/planning-a-sql-server-installation.md)   
 [SQL Server 2014 のインストールに必要なハードウェアおよびソフトウェア](hardware-and-software-requirements-for-installing-sql-server.md)  
  
  
