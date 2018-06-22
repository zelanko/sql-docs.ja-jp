---
title: SQL Server の OLE DB ドライバーを使用する場合 |Microsoft ドキュメント
description: SQL Server の OLE DB Driver を使用する場合
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
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 1aaca043dc057f6f7cc07322e6bf75822a8ebe8b
ms.sourcegitcommit: 03ba89937daeab08aa410eb03a52f1e0d212b44f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/16/2018
ms.locfileid: "35690105"
---
# <a name="when-to-use-ole-db-driver-for-sql-server"></a>SQL Server の OLE DB ドライバーを使用する場合
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-asdbmi-md](../../includes/appliesto-ss-asdb-asdw-pdw-asdbmi-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../includes/driver_oledb_download.md)]

  OLE DB Driver for SQL Server がデータにアクセスするのに使用できるテクノロジの 1 つ、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データベース。  別のデータ アクセス テクノロジの詳細については、次を参照してください[データ アクセス テクノロジのロードマップ。](http://go.microsoft.com/fwlink/?LinkID=179186)  
  
 アプリケーションのデータ アクセス テクノロジとして、SQL Server の OLE DB Driver を使用するかどうかを決定する際に、いくつかの要因を検討してください。  
  
 新しいアプリケーションで、Microsoft Visual C# や Visual Basic などのマネージ プログラミング言語を使用しており、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の新機能にアクセスする必要がある場合は、.NET Framework に含まれている .NET Framework Data Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を使用する必要があります。  
  
 COM ベースのアプリケーションを開発しておりで導入された新しい機能にアクセスする必要がある場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、SQL Server の OLE DB Driver を使用する必要があります。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の新機能にアクセスする必要がない場合は、引き続き Windows Data Access Components (WDAC) を使用できます。  
  
 新機能にアクセスする必要があるかどうかが主な問題の既存の OLE DB アプリケーションは[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。 アプリケーションが既に完成していて、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の新機能を必要としない場合は、引き続き WDAC を使用できます。 など、これらの新機能にアクセスする必要が場合は、 [xml データ型](../../t-sql/xml/xml-transact-sql.md)、SQL Server の OLE DB Driver を使用する必要があります。  
  
 両方 OLE DB Driver for SQL Server と MDAC のサポートは read committed トランザクション分離の行のバージョン管理が OLE DB ドライバーのみを使用して、SQL Server サポート スナップショット トランザクション分離のためです。 (プログラミング用語では、"行のバージョン管理機能を使用した Read Committed トランザクション分離" は "Read Committed トランザクション" と同義です)。  
  
 OLE DB Driver for SQL Server と MDAC の違いについては、次を参照してください。 [MDAC から SQL Server の OLE DB Driver をアプリケーションの更新](../oledb/applications/updating-an-application-to-oledb-driver-for-sql-server-from-mdac.md)です。  
  
## <a name="see-also"></a>参照  
 [OLE DB Driver for SQL Server](../oledb/oledb-driver-for-sql-server.md)     
 [OLE DB の使用法に関するトピック](../oledb/ole-db-how-to/ole-db-how-to-topics.md)  
  
  
