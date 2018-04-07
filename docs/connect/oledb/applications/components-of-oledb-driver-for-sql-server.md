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
- drivers
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
ms.openlocfilehash: 82a3a0999b2d04b699a7b8b9b0299fefc04628de
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/06/2018
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
 [OLE DB Driver for SQL Server を使用したアプリケーションの構築](../../oledb/applications/building-applications-with-oledb-driver-for-sql-server.md)  
