---
title: Microsoft OLE DB Driver for SQL Server | Microsoft Docs
description: OLE DB Driver for SQL Server をいつ使用するか
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB Driver for SQL Server
- MSOLEDBSQL, about OLE DB Driver for SQL Server
- data access [OLE DB Driver for SQL Server], about OLE DB Driver for SQL Server
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: ed4e5bc95800274d66f438e5b8cc5557d40a625c
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "43020246"
---
# <a name="when-to-use-ole-db-driver-for-sql-server"></a>OLE DB Driver for SQL Server をいつ使用するか
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../includes/driver_oledb_download.md)]

  OLE DB Driver for SQL Server がデータにアクセスするのに使用できる 1 つのテクノロジを[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データベース。  各種データ アクセス テクノロジの詳細については、「[データ アクセス テクノロジのロードマップ](http://go.microsoft.com/fwlink/?LinkID=179186)」を参照してください。  
  
 アプリケーションのデータ アクセス テクノロジとして OLE DB Driver for SQL Server を使用するかどうかを決める場合は、いくつかの要素を検討する必要があります。  
  
 新しいアプリケーションで、Microsoft Visual C# や Visual Basic などのマネージド プログラミング言語を使用しており、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の新機能にアクセスする必要がある場合は、.NET Framework に含まれている .NET Framework Data Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を使用する必要があります。  
  
 COM ベースのアプリケーションを開発しており、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で導入された新機能にアクセスする必要がある場合は、OLE DB Driver for SQL Server を使用する必要があります。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の新機能にアクセスする必要がない場合は、引き続き Windows Data Access Components (WDAC) を使用できます。  
  
 既存の OLE DB アプリケーションの場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の新機能にアクセスする必要があるかどうかが重要な問題になります。 アプリケーションが既に完成していて、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の新機能を必要としない場合は、引き続き WDAC を使用できます。 ただし、[xml データ型](../../t-sql/xml/xml-transact-sql.md)などの新機能にアクセスする必要がある場合は、OLE DB Driver for SQL Server を使用する必要があります。  
  
 両方 OLE DB Driver for SQL Server と MDAC のサポートは read committed トランザクション分離の行のバージョン管理が OLE DB ドライバーのみを使用して、SQL Server サポートのスナップショット トランザクションの分離です。 (プログラミング用語では、"行のバージョン管理機能を使用した Read Committed トランザクション分離" は "Read Committed トランザクション" と同義です)。  
  
 OLE DB Driver for SQL Server と MDAC の違いについては、次を参照してください。 [MDAC から SQL Server の OLE DB ドライバーへのアプリケーションの更新](../oledb/applications/updating-an-application-to-oledb-driver-for-sql-server-from-mdac.md)します。  
  
## <a name="see-also"></a>参照  
 [OLE DB Driver for SQL Server](../oledb/oledb-driver-for-sql-server.md)     
 [OLE DB の使用法に関するトピック](../oledb/ole-db-how-to/ole-db-how-to-topics.md)  
  
  
