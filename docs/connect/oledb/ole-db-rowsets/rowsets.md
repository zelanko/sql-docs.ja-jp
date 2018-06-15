---
title: 行セット |Microsoft ドキュメント
description: OLE DB Driver for SQL Server での行セット
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- rowsets [OLE DB], about rowsets
- OLE DB Driver for SQL Server, rowsets
- OLE DB rowsets
- OLE DB rowsets, about rowsets
- rowsets [OLE DB]
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 5e03aa5a887f25e9909ff2c755cfbfa598166475
ms.sourcegitcommit: f16003fd1ca28b5e06d5700e730f681720006816
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2018
ms.locfileid: "35306701"
---
# <a name="rowsets"></a>行セット
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  行セットとは、データの列を含む行の集まりです。 行セットは、すべての OLE DB データ プロバイダーが表形式で結果セット データを公開できるようにするための重要な機能を持つオブジェクトです。  
  
 コンシューマーを使用して、セッションを作成した後、 **idbcreatesession::createsession**メソッド、コンシューマーが使用するか、 **IOpenRowset**または**IDBCreateCommand**行セットを作成するセッションのインターフェイスです。 SQL Server の OLE DB Driver は、これらのインターフェイスの両方をサポートします。 ここでは、これら両方のメソッドについて説明します。  
  
-   呼び出して行セットを作成、 **iopenrowset::openrowset**メソッドです。  
  
     この操作は、1 つのテーブル全体について行セットを作成することと同じです。 このメソッドは、1 つのベース テーブルのすべての行を含む行セットを開き、その行セットを返します。 引数のいずれかの**OpenRowset**行セットの作成元のテーブルを識別するテーブル id を指定します。  
  
-   呼び出してコマンド オブジェクトを作成、 **idbcreatecommand::createcommand**メソッドです。  
  
     コマンド オブジェクトでは、プロバイダーがサポートするコマンドが実行されます。 OLE DB Driver for SQL Server、コンシューマーはいずれかを指定して[!INCLUDE[tsql](../../../includes/tsql-md.md)]ステートメントでは、SELECT ステートメントまたはストアド プロシージャの呼び出しなどです。 コマンド オブジェクトを使用して行セットを作成する手順は次のとおりです。  
  
    1.  コンシューマーは、 **idbcreatecommand::createcommand**を要求するコマンド オブジェクトを取得するセッションのメソッド、 **ICommandText**コマンド オブジェクトのインターフェイスです。 これは、 **ICommandText**インターフェイスを設定し、実際のコマンド テキストを取得します。 テキスト コマンドを呼び出すことによって、コンシューマー入力、 **icommandtext::setcommandtext**メソッドです。  
  
    2.  ユーザーの呼び出し、 **icommand::execute**のコマンドは、上のメソッドです。 コマンドの実行時に構築される行セット オブジェクトには、コマンドから返される結果セットが含まれます。  
  
 コンシューマーが使用できる、 **ICommandProperties**を取得またはで実行されるコマンドによって返される行セットのプロパティを設定するインターフェイス、 **icommand::execute**インターフェイスです。 最も一般的に要求されるプロパティは、行セットでサポートする必要のあるインターフェイスです。 コンシューマーはインターフェイスだけでなく、行セットやインターフェイスの動作を変更するプロパティも要求できます。  
  
 コンシューマーが行セットを解放、 **IRowset::Release**メソッドです。 行セットを解放すると、コンシューマーがその行セットに保持しているすべての行ハンドルも解放されます。 ただし、行セットを解放してもアクセサーは解放されません。 ある場合、 **IAccessor**インターフェイスがまだ解放します。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
-   [IOpenRowset を使用した行セットの作成](../../oledb/ole-db-rowsets/creating-a-rowset-with-iopenrowset.md)  
  
-   [ICommand::Execute を使用した行セットの作成](../../oledb/ole-db-rowsets/creating-rowsets-with-icommand-execute.md)  
  
-   [行セットのプロパティと動作](../../oledb/ole-db-rowsets/rowset-properties-and-behaviors.md)  
  
-   [行セットと SQL Server カーソル](../../oledb/ole-db-rowsets/rowsets-and-sql-server-cursors.md)  
  
-   [行のフェッチ](../../oledb/ole-db-rowsets/fetching-rows.md)  
  
-   [IRow による 1 行のフェッチ](../../oledb/ole-db-rowsets/fetching-a-single-row-with-irow.md)  
  
-   [ブックマーク](../../oledb/ole-db-rowsets/bookmarks.md)  
  
-   [行セット内のデータの更新](../../oledb/ole-db-rowsets/updating-data-in-rowsets.md)  
  
## <a name="see-also"></a>参照  
 [OLE DB Driver for SQL Server のプログラミング](../../oledb/ole-db/oledb-driver-for-sql-server-programming.md)  
  
  
