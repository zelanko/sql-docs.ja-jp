---
title: Microsoft OLE DB Driver for SQL Server | Microsoft Docs
description: OLE DB Driver for SQL Server のコンポーネント
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- data access [OLE DB Driver for SQL Server], components
- components [OLE DB Driver for SQL Server]
- MSOLEDBSQL, about OLE DB Driver for SQL Server
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: 164b87135257f812898c254fd7fd4f5c762c72ec
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47735250"
---
# <a name="components-of-ole-db-driver-for-sql-server"></a>OLE DB Driver for SQL Server のコンポーネント
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  OLE DB Driver for SQL Server には、次のコンポーネントが含まれています。  

|コンポーネント|[説明]|  
|---------------|-----------------|  
|msoledbsql.dll|すべての OLE DB Driver for SQL Server の機能を含むダイナミック リンク ライブラリ (DLL) ファイル。|  
|msoledbsqlr.rll|SQL Server ライブラリの OLE DB driver 付随するリソース ファイル。|   
|msoledbsql.h|すべての新しい定義を含むヘッダー ファイルを SQL Server の OLE DB Driver for SQL Server OLE DB ドライバーを使用するために必要です。 このヘッダー ファイルでは、sqloledb.h ヘッダー ファイルを置き換えます。<br /><br /> 注: と参照できます msoledbsql.h 同じプログラム内で sqloledb.h sqloledb.h を最初に定義されている限り、します。|  
|msoledbsql.lib|直接の呼び出しに必要なライブラリ ファイル、 [OpenSqlFilestream](../../../relational-databases/blob/access-filestream-data-with-opensqlfilestream.md)関数は、OLE DB Driver for SQL Server の一部であります。<br /><br /> プログラミング コードで sqlncli11.lib ファイルを参照する場合、使用しているコンピューターのシステム パス、およびアプリケーションを使用するユーザーのシステム パスに sqlncli11.dll ファイルが含まれることを確認する必要があります。|  

## <a name="see-also"></a>参照  
 [OLE DB Driver for SQL Server を使用したアプリケーションの構築](../../oledb/applications/building-applications-with-oledb-driver-for-sql-server.md)  
