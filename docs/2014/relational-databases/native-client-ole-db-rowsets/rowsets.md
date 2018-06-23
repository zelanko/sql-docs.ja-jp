---
title: 行セット |Microsoft ドキュメント
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
- rowsets [OLE DB], about rowsets
- SQL Server Native Client OLE DB provider, rowsets
- OLE DB rowsets
- OLE DB rowsets, about rowsets
- rowsets [OLE DB]
ms.assetid: 5e7b3cbe-3670-4e18-8172-2226e0b6b142
caps.latest.revision: 30
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: daa4edfaaf4339d03993f0e53375b8b406a99e86
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36165229"
---
# <a name="rowsets"></a>行セット
  行セットとは、データの列を含む行の集まりです。 行セットは、すべての OLE DB データ プロバイダーが表形式で結果セット データを公開できるようにするための重要な機能を持つオブジェクトです。  
  
 コンシューマーを使用して、セッションを作成した後、 **idbcreatesession::createsession**メソッド、コンシューマーが使用するか、 **IOpenRowset**または**IDBCreateCommand**行セットを作成するセッションのインターフェイスです。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーでは、これらのインターフェイスの両方をサポートします。 ここでは、これら両方のメソッドについて説明します。  
  
-   呼び出して行セットを作成、 **iopenrowset::openrowset**メソッドです。  
  
     この操作は、1 つのテーブル全体について行セットを作成することと同じです。 このメソッドは、1 つのベース テーブルのすべての行を含む行セットを開き、その行セットを返します。 引数のいずれかの**OpenRowset**行セットの作成元のテーブルを識別するテーブル id を指定します。  
  
-   呼び出してコマンド オブジェクトを作成、 **idbcreatecommand::createcommand**メソッドです。  
  
     コマンド オブジェクトでは、プロバイダーがサポートするコマンドが実行されます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーでは、SELECT ステートメントなどの任意の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントやストアド プロシージャへの呼び出しをコンシューマーで指定できます。 コマンド オブジェクトを使用して行セットを作成する手順は次のとおりです。  
  
    1.  コンシューマーは、 **idbcreatecommand::createcommand**を要求するコマンド オブジェクトを取得するセッションのメソッド、 **ICommandText**コマンド オブジェクトのインターフェイスです。 これは、 **ICommandText**インターフェイスを設定し、実際のコマンド テキストを取得します。 テキスト コマンドを呼び出すことによって、コンシューマー入力、 **icommandtext::setcommandtext**メソッドです。  
  
    2.  ユーザーの呼び出し、 **icommand::execute**のコマンドは、上のメソッドです。 コマンドの実行時に構築される行セット オブジェクトには、コマンドから返される結果セットが含まれます。  
  
 コンシューマーが使用できる、 **ICommandProperties**を取得またはで実行されるコマンドによって返される行セットのプロパティを設定するインターフェイス、 **icommand::execute**インターフェイスです。 最も一般的に要求されるプロパティは、行セットでサポートする必要のあるインターフェイスです。 コンシューマーはインターフェイスだけでなく、行セットやインターフェイスの動作を変更するプロパティも要求できます。  
  
 コンシューマーが行セットを解放、 **IRowset::Release**メソッドです。 行セットを解放すると、コンシューマーがその行セットに保持しているすべての行ハンドルも解放されます。 ただし、行セットを解放してもアクセサーは解放されません。 ある場合、 **IAccessor**インターフェイスがまだ解放します。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
-   [IOpenRowset を使用した行セットの作成](creating-a-rowset-with-iopenrowset.md)  
  
-   [ICommand::Execute を使用した行セットの作成](creating-rowsets-with-icommand-execute.md)  
  
-   [行セットのプロパティと動作](rowset-properties-and-behaviors.md)  
  
-   [行セットと SQL Server カーソル](rowsets-and-sql-server-cursors.md)  
  
-   [行のフェッチ](fetching-rows.md)  
  
-   [IRow による 1 行のフェッチ](fetching-a-single-row-with-irow.md)  
  
-   [ブックマーク](bookmarks.md)  
  
-   [行セット内のデータの更新](updating-data-in-rowsets.md)  
  
## <a name="see-also"></a>参照  
 [SQL Server Native Client &#40;OLE DB&#41;](../native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  