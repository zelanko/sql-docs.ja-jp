---
title: "コマンドの実行 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-ole-db-provider
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- commands [SQL Server Native Client]
- OLE DB, executing commands
- sessions [SQL Server Native Client]
- OLE DB extensions for XML
- SQL Server Native Client OLE DB provider, command execution
ms.assetid: bb0b3cbf-fe45-46ba-b2ec-c5a39e3c7081
caps.latest.revision: "40"
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 495f632181ec7697c08002684e2f6e77f272d39a
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="executing-a-command"></a>コマンドの実行
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  データ ソースへの接続を確立すると、コンシューマーは呼び出し、 **idbcreatesession::createsession**セッションを作成するメソッド。 セッションは、コマンド、行セット、またはトランザクションのファクトリとして動作します。  
  
 コンシューマーが要求する個々 のテーブルまたはインデックスを直接操作する、 **IOpenRowset**インターフェイスです。 **Iopenrowset::openrowset**メソッドを開き、単一のベース テーブルまたはインデックスからすべての行を含む行セットを返します。  
  
 コマンドを実行する (SELECT など\*FROM Authors)、コンシューマーの要求、 **IDBCreateCommand**インターフェイスです。 コンシューマーが実行できる、 **idbcreatecommand::createcommand**コマンド オブジェクトを作成し、要求をメソッド、 **ICommandText**インターフェイスです。 **Icommandtext::setcommandtext**メソッドを使用して、コマンドを実行するを指定します。  
  
 **Execute**コマンドを実行するコマンドを使用します。 コマンドには、任意の SQL ステートメントやプロシージャ名を指定できます。 コマンドを実行しても、必ず結果セット (行セット) オブジェクトが得られるわけではありません。 SELECT * FROM Authors などのコマンドでは、結果セットが得られます。  
  
## <a name="see-also"></a>参照  
 [SQL Server Native Client OLE DB プロバイダー アプリケーションの作成](../../relational-databases/native-client-ole-db-provider/creating-a-sql-server-native-client-ole-db-provider-application.md)  
  
  
