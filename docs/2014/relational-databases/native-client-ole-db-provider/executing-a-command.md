---
title: コマンドを実行する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- commands [SQL Server Native Client]
- OLE DB, executing commands
- sessions [SQL Server Native Client]
- OLE DB extensions for XML
- SQL Server Native Client OLE DB provider, command execution
ms.assetid: bb0b3cbf-fe45-46ba-b2ec-c5a39e3c7081
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5f94cc014a04c3392fefb61f4fa291a8f5a44ad8
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "62638455"
---
# <a name="executing-a-command"></a>コマンドの実行
  データソースへの接続が確立されると、コンシューマーは**IDBCreateSession:: CreateSession**メソッドを呼び出してセッションを作成します。 セッションは、コマンド、行セット、またはトランザクションのファクトリとして動作します。  
  
 個別のテーブルやインデックスを直接操作するには、`IOpenRowset` インターフェイスを要求します。 
  `IOpenRowset::OpenRowset` メソッドは、1 つのベース テーブルまたはベース インデックスからのすべての行が含まれる行セットを開いて返します。  
  
 コマンド (SELECT \* FROM Authors など) を実行するために、コンシューマーは`IDBCreateCommand`インターフェイスを要求します。 
  `IDBCreateCommand::CreateCommand` メソッドを実行してコマンド オブジェクトを作成し、`ICommandText` インターフェイスを要求できます。 実行するコマンドを指定するには、`ICommandText::SetCommandText` メソッドを使用します。  
  
 コマンドを実行するには、`Execute` コマンドを使用します。 コマンドには、任意の SQL ステートメントやプロシージャ名を指定できます。 コマンドを実行しても、必ず結果セット (行セット) オブジェクトが得られるわけではありません。 SELECT * FROM Authors などのコマンドでは、結果セットが得られます。  
  
## <a name="see-also"></a>参照  
 [SQL Server Native Client OLE DB プロバイダー アプリケーションの作成](creating-a-sql-server-native-client-ole-db-provider-application.md)  
  
  
