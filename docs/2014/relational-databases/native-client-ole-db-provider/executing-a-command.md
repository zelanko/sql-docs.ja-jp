---
title: コマンドの実行 |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- commands [SQL Server Native Client]
- OLE DB, executing commands
- sessions [SQL Server Native Client]
- OLE DB extensions for XML
- SQL Server Native Client OLE DB provider, command execution
ms.assetid: bb0b3cbf-fe45-46ba-b2ec-c5a39e3c7081
caps.latest.revision: 40
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 2d9c0f935bf4d3cd903346281080a8b08384c1e4
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36164776"
---
# <a name="executing-a-command"></a>コマンドの実行
  データ ソースへの接続を確立すると、コンシューマーは呼び出し、 **idbcreatesession::createsession**セッションを作成するメソッド。 セッションは、コマンド、行セット、またはトランザクションのファクトリとして動作します。  
  
 個別のテーブルやインデックスを直接操作するには、`IOpenRowset` インターフェイスを要求します。 `IOpenRowset::OpenRowset` メソッドは、1 つのベース テーブルまたはベース インデックスからのすべての行が含まれる行セットを開いて返します。  
  
 コマンドを実行する (SELECT など\*FROM Authors)、コンシューマーの要求、`IDBCreateCommand`インターフェイスです。 `IDBCreateCommand::CreateCommand` メソッドを実行してコマンド オブジェクトを作成し、`ICommandText` インターフェイスを要求できます。 実行するコマンドを指定するには、`ICommandText::SetCommandText` メソッドを使用します。  
  
 コマンドを実行するには、`Execute` コマンドを使用します。 コマンドには、任意の SQL ステートメントやプロシージャ名を指定できます。 コマンドを実行しても、必ず結果セット (行セット) オブジェクトが得られるわけではありません。 SELECT * FROM Authors などのコマンドでは、結果セットが得られます。  
  
## <a name="see-also"></a>参照  
 [SQL Server Native Client OLE DB プロバイダー アプリケーションの作成](creating-a-sql-server-native-client-ole-db-provider-application.md)  
  
  