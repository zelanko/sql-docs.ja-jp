---
title: "SQL Server Native Client を使用する場合 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, about SQL Server Native Client ODBC driver
- SQLNCLI, about SQL Server Native Client
- data access [SQL Server Native Client], about SQL Server Native Client
ms.assetid: 08f18b36-209d-4cf7-9623-ebc61859a91d
caps.latest.revision: "37"
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 5244bd7ed81e7aeaf11ef63c1a65c28f4094004c
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="when-to-use-sql-server-native-client"></a>SQL Server Native Client を使用する場合
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースのデータにアクセスする際に使用できるテクノロジの 1 つです。  別のデータ アクセス テクノロジの詳細については、次を参照してください[データ アクセス テクノロジのロードマップ。](http://go.microsoft.com/fwlink/?LinkID=179186)  
  
 アプリケーションのデータ アクセス テクノロジとして [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client を使用するかどうかを決める場合は、いくつかの要素を検討する必要があります。  
  
 新しいアプリケーションで、Microsoft Visual C# や Visual Basic などのマネージ プログラミング言語を使用しており、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の新機能にアクセスする必要がある場合は、.NET Framework に含まれている .NET Framework Data Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を使用する必要があります。  
  
 COM ベースのアプリケーションを開発しており、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で導入された新機能にアクセスする必要がある場合は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client を使用する必要があります。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の新機能にアクセスする必要がない場合は、引き続き Windows Data Access Components (WDAC) を使用できます。  
  
 既存の OLE DB アプリケーションや ODBC アプリケーションの場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の新機能にアクセスする必要があるかどうかが重要な問題になります。 アプリケーションが既に完成していて、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の新機能を必要としない場合は、引き続き WDAC を使用できます。 など、これらの新機能にアクセスする必要が場合は、 [xml データ型](../../t-sql/xml/xml-transact-sql.md)、使用する必要があります[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client です。  
  
 行のバージョン管理機能を使用した Read Committed トランザクション分離は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client と MDAC の両方でサポートされていますが、スナップショット トランザクション分離は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client のみでサポートされています  (プログラミング用語では、"行のバージョン管理機能を使用した Read Committed トランザクション分離" は "Read Committed トランザクション" と同義です)。  
  
 間の相違点について[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client と MDAC を参照してください。 [MDAC から SQL Server Native Client へのアプリケーションの更新](../../relational-databases/native-client/applications/updating-an-application-to-sql-server-native-client-from-mdac.md)です。  
  
## <a name="see-also"></a>参照  
 [SQL Server Native Client プログラミング](../../relational-databases/native-client/sql-server-native-client-programming.md)   
 [ODBC の操作方法に関するトピック](../../relational-databases/native-client-odbc-how-to/odbc-how-to-topics.md)   
 [OLE DB の操作方法に関するトピック](../../relational-databases/native-client-ole-db-how-to/ole-db-how-to-topics.md)  
  
  
