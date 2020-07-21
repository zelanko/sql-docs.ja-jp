---
title: コマンドの実行 | Microsoft Docs
description: コマンドの実行
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- commands [OLE DB Driver for SQL Server]
- OLE DB, executing commands
- sessions [OLE DB Driver for SQL Server]
- OLE DB extensions for XML
- OLE DB Driver for SQL Server, command execution
author: pmasl
ms.author: pelopes
ms.openlocfilehash: f13c9177a74212b849572881f114e503a9530286
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/29/2020
ms.locfileid: "67994990"
---
# <a name="executing-a-command"></a>コマンドの実行
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  データ ソースへの接続が確立されたら、コンシューマーは **IDBCreateSession::CreateSession** メソッドを呼び出してセッションを作成します。 セッションは、コマンド、行セット、またはトランザクションのファクトリとして動作します。  
  
 個別のテーブルやインデックスを直接操作するには、**IOpenRowset** インターフェイスを要求します。 **IOpenRowset::OpenRowset** メソッドは、1 つのベース テーブルまたはベース インデックスからのすべての行が含まれる行セットを開いて返します。  
  
 SELECT \* FROM Authors などのコマンドを実行するには、**IDBCreateCommand** インターフェイスを要求します。 コンシューマーは **IDBCreateCommand::CreateCommand** メソッドを実行してコマンド オブジェクトを作成し、**ICommandText** インターフェイスを要求できます。 実行するコマンドを指定するには、**ICommandText::SetCommandText** メソッドを使用します。  
  
 コマンドを実行するには、**Execute** コマンドを使用します。 コマンドには、任意の SQL ステートメントやプロシージャ名を指定できます。 コマンドを実行しても、必ず結果セット (行セット) オブジェクトが得られるわけではありません。 SELECT * FROM Authors などのコマンドでは、結果セットが得られます。  
  
## <a name="see-also"></a>参照  
 [OLE DB Driver for SQL Server のアプリケーションの作成](../../oledb/ole-db-driver/creating-a-oledb-driver-for-sql-server-application.md)  
  
  
