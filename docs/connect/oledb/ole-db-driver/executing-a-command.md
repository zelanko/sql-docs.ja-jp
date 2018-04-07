---
title: コマンドの実行 |Microsoft ドキュメント
description: コマンドの実行
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: oledb-driver-for-sql-server
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- commands [OLE DB Driver for SQL Server]
- OLE DB, executing commands
- sessions [OLE DB Driver for SQL Server]
- OLE DB extensions for XML
- OLE DB Driver for SQL Server, command execution
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 48e6fd74fcf6468be92aac9d70a1c4b8ab3a967d
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/06/2018
---
# <a name="executing-a-command"></a>コマンドの実行
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  データ ソースへの接続を確立すると、コンシューマーは呼び出し、 **idbcreatesession::createsession**セッションを作成するメソッド。 セッションは、コマンド、行セット、またはトランザクションのファクトリとして動作します。  
  
 コンシューマーが要求する個々 のテーブルまたはインデックスを直接操作する、 **IOpenRowset**インターフェイスです。 **Iopenrowset::openrowset**メソッドを開き、単一のベース テーブルまたはインデックスからすべての行を含む行セットを返します。  
  
 コマンドを実行する (SELECT など\*FROM Authors)、コンシューマーの要求、 **IDBCreateCommand**インターフェイスです。 コンシューマーが実行できる、 **idbcreatecommand::createcommand**コマンド オブジェクトを作成し、要求をメソッド、 **ICommandText**インターフェイスです。 **Icommandtext::setcommandtext**メソッドを使用して、コマンドを実行するを指定します。  
  
 **Execute**コマンドを実行するコマンドを使用します。 コマンドには、任意の SQL ステートメントやプロシージャ名を指定できます。 コマンドを実行しても、必ず結果セット (行セット) オブジェクトが得られるわけではありません。 SELECT * FROM Authors などのコマンドでは、結果セットが得られます。  
  
## <a name="see-also"></a>参照  
 [OLE DB Driver for SQL Server のアプリケーションの作成](../../oledb/ole-db-driver/creating-a-oledb-driver-for-sql-server-application.md)  
  
  
