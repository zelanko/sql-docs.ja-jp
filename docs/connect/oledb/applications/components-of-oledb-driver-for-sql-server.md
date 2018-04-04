---
title: OLE DB Driver for SQL Server のコンポーネント |Microsoft ドキュメント
description: OLE DB Driver for SQL Server のコンポーネント
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: oledb|applications
ms.reviewer: ''
ms.suite: sql
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- data access [OLE DB Driver for SQL Server], components
- components [OLE DB Driver for SQL Server]
- MSOLEDBSQL, about OLE DB Driver for SQL Server
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 18b0f0e13fefefe5e3be09d7538150cfccbfcb21
ms.sourcegitcommit: 9f4330a4b067deea396b8567747a6771f35e6eee
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/30/2018
---
# <a name="components-of-ole-db-driver-for-sql-server"></a>OLE DB Driver for SQL Server のコンポーネント
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  OLE DB Driver for SQL Server には、次のコンポーネントが含まれています。  

|コンポーネント|Description|  
|---------------|-----------------|  
|msoledbsql.dll|OLE DB 用のドライバーの SQL Server の機能すべてを含むダイナミック リンク ライブラリ (DLL) ファイル。|  
|msoledbsqlr.rll|SQL Server ライブラリの OLE DB Driver に付随するリソース ファイル。|   
|msoledbsql.h|すべての新しい定義を含むヘッダー ファイルを SQL Server の OLE DB Driver は、SQL Server の OLE DB Driver を使用するために必要です。 このヘッダー ファイルには、sqloledb.h ヘッダー ファイルが置き換えられます。<br /><br /> 注: 参照できます msoledbsql.h と同じプログラム内で sqloledb.h sqloledb.h を最初に定義されている限りです。|  
|msoledbsql.lib|直接の呼び出しに必要なライブラリ ファイル、 **bcp**ユーティリティ関数は、OLE DB Driver for SQL Server の一部であります。<br /><br /> 注意: msoledbsql.lib ファイルを参照するプログラミング コードで、する必要があります msoledbsql.dll ファイルがシステム パス、および構成するユーザーのシステム パスであるかどうかを確認するアプリケーションを使用します。|  

## <a name="see-also"></a>参照  
 [SQL Server の OLE DB ドライバーとアプリケーションの構築](../../oledb/applications/building-applications-with-oledb-driver-for-sql-server.md)  
