---
title: コマンドの実行 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: bddfd1c50163f6a74286043c2bc5e871ce366c1d
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37417691"
---
# <a name="executing-a-command"></a>コマンドを実行します。
  データ ソースへの接続を確立するには、コンシューマーは呼び出し、 **idbcreatesession::createsession**セッションを作成するメソッド。 セッションは、コマンド、行セット、またはトランザクションのファクトリとして動作します。  
  
 個別のテーブルやインデックスを直接操作するには、`IOpenRowset` インターフェイスを要求します。 `IOpenRowset::OpenRowset` メソッドは、1 つのベース テーブルまたはベース インデックスからのすべての行が含まれる行セットを開いて返します。  
  
 コマンドを実行する (SELECT など\*FROM Authors)、コンシューマーの要求、`IDBCreateCommand`インターフェイス。 `IDBCreateCommand::CreateCommand` メソッドを実行してコマンド オブジェクトを作成し、`ICommandText` インターフェイスを要求できます。 実行するコマンドを指定するには、`ICommandText::SetCommandText` メソッドを使用します。  
  
 コマンドを実行するには、`Execute` コマンドを使用します。 コマンドには、任意の SQL ステートメントやプロシージャ名を指定できます。 コマンドを実行しても、必ず結果セット (行セット) オブジェクトが得られるわけではありません。 SELECT * FROM Authors などのコマンドでは、結果セットが得られます。  
  
## <a name="see-also"></a>参照  
 [SQL Server Native Client OLE DB プロバイダー アプリケーションの作成](creating-a-sql-server-native-client-ole-db-provider-application.md)  
  
  
