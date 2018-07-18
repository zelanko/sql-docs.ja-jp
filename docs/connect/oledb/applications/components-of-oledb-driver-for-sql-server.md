---
title: OLE DB Driver for SQL Server のコンポーネント |Microsoft ドキュメント
description: OLE DB Driver for SQL Server のコンポーネント
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|applications
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- data access [OLE DB Driver for SQL Server], components
- components [OLE DB Driver for SQL Server]
- MSOLEDBSQL, about OLE DB Driver for SQL Server
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 78b72796de5aa4ac2fb9bc0793f98365b7d8281e
ms.sourcegitcommit: 354ed9c8fac7014adb0d752518a91d8c86cdce81
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/14/2018
ms.locfileid: "35611687"
---
# <a name="components-of-ole-db-driver-for-sql-server"></a>OLE DB Driver for SQL Server のコンポーネント
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-asdbmi-md](../../../includes/appliesto-ss-asdb-asdw-pdw-asdbmi-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  OLE DB Driver for SQL Server には、次のコンポーネントが含まれています。  

|コンポーネント|説明|  
|---------------|-----------------|  
|msoledbsql.dll|OLE DB 用のドライバーの SQL Server の機能すべてを含むダイナミック リンク ライブラリ (DLL) ファイル。|  
|msoledbsqlr.rll|SQL Server ライブラリの OLE DB Driver に付随するリソース ファイル。|   
|msoledbsql.h|すべての新しい定義を含むヘッダー ファイルを SQL Server の OLE DB Driver は、SQL Server の OLE DB Driver を使用するために必要です。 このヘッダー ファイルには、sqloledb.h ヘッダー ファイルが置き換えられます。<br /><br /> 注: 参照できます msoledbsql.h と同じプログラム内で sqloledb.h sqloledb.h を最初に定義されている限りです。|  
|msoledbsql.lib|直接の呼び出しに必要なライブラリ ファイル、 [OpenSqlFilestream](../../../relational-databases/blob/access-filestream-data-with-opensqlfilestream.md)関数は、OLE DB Driver for SQL Server の一部であります。<br /><br /> 注意: msoledbsql.lib ファイルを参照するプログラミング コードで、する必要があります msoledbsql.dll ファイルがシステム パス、および構成するユーザーのシステム パスであるかどうかを確認するアプリケーションを使用します。|  

## <a name="see-also"></a>参照  
 [OLE DB Driver for SQL Server を使用したアプリケーションの構築](../../oledb/applications/building-applications-with-oledb-driver-for-sql-server.md)  
