---
title: 複数の行セットの結果を生成するコマンド |Microsoft Docs
description: 複数行セットの結果を生成するコマンド
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|ole-db-commands
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- multiple rowsets
- rowsets [OLE DB], multiple
- OLE DB Driver for SQL Server, commands
- OLE DB Driver for SQL Server, multiple rowsets
- commands [OLE DB]
- multiple-rowset results
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 579fae980b0f612aa1317407f797be9d1ff02ed3
ms.sourcegitcommit: 50838d7e767c61dd0b5e677b6833dd5c139552f2
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 07/18/2018
ms.locfileid: "39109624"
---
# <a name="commands-generating-multiple-rowset-results"></a>複数行セットの結果を生成するコマンド
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  OLE DB Driver for SQL Server から複数の行セットを返せる[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]ステートメント。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のステートメントは、次の条件が満たされた場合に複数行セットの結果を返します。  
  
-   バッチにまとめられた SQL ステートメントが 1 つのコマンドとして実行される場合。  
  
-   ストアド プロシージャが SQL ステートメントのバッチを実装している場合。  
  
## <a name="batches"></a>バッチ  
 OLE DB Driver for SQL Server では、SQL ステートメントのバッチ区切り記号としてセミコロン文字が認識されます。  
  
```  
WCHAR*       wSQLString = L"SELECT * FROM Categories; "  
                          L"SELECT * FROM Products";  
```  
  
 複数の SQL ステートメントを 1 つのバッチにまとめて送信する方が、各 SQL ステートメントを個別に実行するよりも効率的です。 1 つのバッチを送信することで、クライアントからサーバーへのネットワーク ラウンド トリップが減少するためです。  
  
## <a name="stored-procedures"></a>ストアド プロシージャ  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] は、ストアド プロシージャ内のステートメントごとに結果セットを返します。このため、大半の [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ストアド プロシージャは複数の結果セットを返します。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
-   [IMultipleResults を使用した複数の結果セットの処理](../../oledb/ole-db-commands/using-imultipleresults-to-process-multiple-result-sets.md)  
  
## <a name="see-also"></a>参照  
 [[コマンド]](../../oledb/ole-db-commands/commands.md)  
  
  
