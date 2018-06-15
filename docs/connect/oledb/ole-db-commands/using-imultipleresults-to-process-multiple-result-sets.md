---
title: IMultipleResults を使用して、複数の結果セットを処理する |Microsoft ドキュメント
description: IMultipleResults を使用して、複数の結果を処理する設定します。
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
- IMultipleResults interface
- multiple-rowset results
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 59e39d472be21161d27b0449c1f2e81d31a09c4d
ms.sourcegitcommit: e1bc8c486680e6d6929c0f5885d97d013a537149
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2018
ms.locfileid: "35666282"
---
# <a name="using-imultipleresults-to-process-multiple-result-sets"></a>IMultipleResults を使用した複数の結果セットの処理
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-asdbmi-md](../../../includes/appliesto-ss-asdb-asdw-pdw-asdbmi-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  コンシューマーを使用して、 **IMultipleResults**コマンドの実行を SQL Server の OLE DB ドライバーによって返される結果を処理するインターフェイスです。 OLE DB Driver for SQL Server の実行でコマンドを送信するときに[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]ステートメントを実行し、すべての結果を返します。  
  
 クライアントはコマンドの実行結果をすべて処理する必要があります。 コマンドの実行を SQL Server の OLE DB Driver は、結果として複数の行セット オブジェクトを生成できますが、ために、使用、 **IMultipleResults**インターフェイスをアプリケーション データの取得に、クライアントが開始したラウンド トリップが完了したことを確認してください。  
  
 次[!INCLUDE[tsql](../../../includes/tsql-md.md)]ステートメントでは、複数の行セット、一部を含む行のデータを生成、 **OrderDetails**テーブルと COMPUTE BY 句の一部を含む結果。  
  
```  
SELECT OrderID, FullPrice = (UnitPrice * Quantity), Discount,  
    Discounted = UnitPrice * (1 - Discount) * Quantity  
FROM OrderDetails  
ORDER BY OrderID  
COMPUTE  
    SUM(UnitPrice * Quantity), SUM(UnitPrice * (1 - Discount) * Quantity)  
    BY OrderID  
```  
  
 このテキストを含んだコマンドを実行し、返される結果のインターフェイスとして行セットを要求した場合、最初の行セットのみが返されます。 コンシューマーでは、返された行セットのすべての行を処理できます。 ただし、DBPROP_MULTIPLECONNECTIONS データ ソースのプロパティ設定されている場合 VARIANT_FALSE と MARS が有効でない接続で、他のコマンドを実行できますなし (SQL Server の OLE DB Driver は別の接続を作成できません)、セッション オブジェクトにまで、コマンドが取り消されました。 接続で MARS が有効でない場合、DBPROP_MULTIPLECONNECTIONS が VARIANT_FALSE に、E_FAIL が返された場合は、アクティブなトランザクションがある場合、OLE DB Driver for SQL Server は DB_E_OBJECTOPEN エラーを返します。  
  
 SQL Server の OLE DB Driver は、DB_E_OBJECTOPEN を使用する場合に、出力パラメーターがストリーム送信され、アプリケーションが呼び出す前にすべての返された出力パラメーター値を使用していないはも返します**imultipleresults::getresults**に次の結果セットを取得します。 コマンドを実行すると、行セットが生成されません MARS が有効でないと、接続がビジー状態である場合、または、サーバー カーソルではないと、DBPROP_MULTIPLECONNECTIONS データ ソース プロパティの場合は VARIANT_TRUE、SQL Server の OLE DB ドライバーに設定される行セットを生成します。同時実行コマンド オブジェクトをサポートする追加の接続、トランザクションがアクティブを返します。 この場合、しない限りはエラーを生成します。 トランザクションとロックは、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] によって接続ごとに管理されます。 他の接続が作成されている場合でも、個別の接続のコマンドはロックを共有しません。 コマンドによって要求された行にロックを設定することで、そのコマンドが別のコマンドによってブロックされないようにする必要があります。 MARS を有効にしている場合、その接続では複数のコマンドをアクティブにできます。明示的なトランザクションを使用している場合、すべてのコマンドが共通のトランザクションを共有します。  
  
 取り消すには、コマンドを使用するか[issabort::abort](../../oledb/ole-db-interfaces/issabort-abort-ole-db.md)コマンド オブジェクトおよび派生行セットに対して保持されているすべての参照を解放します。  
  
 使用して**IMultipleResults**コマンドの実行によって生成されたすべての行セットを取得するコンシューマーは、すべてのインスタンスにでき、コンシューマーは適切にコマンドの実行をキャンセルしで使用するためのセッション オブジェクトを解放する場合の判別その他のコマンド。  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] カーソルを使用するときは、コマンドを実行するとカーソルが作成されます。 カーソルを作成するときに [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] は成功か失敗を返します。したがって、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンスへのラウンド トリップが完了するのはコマンドを実行した結果が返ってきたときです。 各**GetNextRows**呼び出しは、ラウンド トリップになります。 このようなしくみによって、サーバー カーソルからのフェッチの結果である行セットを処理する、複数のアクティブなコマンド オブジェクトが存在できます。 詳細については、次を参照してください。[行セットと SQL Server カーソル](../../oledb/ole-db-rowsets/rowsets-and-sql-server-cursors.md)です。  
  
## <a name="see-also"></a>参照  
 [[コマンド]](../../oledb/ole-db-commands/commands.md)  
  
  
