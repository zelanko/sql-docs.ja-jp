---
title: IMultipleResults を使用して、複数の結果セットを処理する |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: native-client-ole-db-commands
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- multiple rowsets
- rowsets [OLE DB], multiple
- IMultipleResults interface
- multiple-rowset results
ms.assetid: 754d3f30-7d94-4b67-8dac-baf2699ce9c6
caps.latest.revision: 40
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: f3ab7376bcbb6b8237aa2600ac19fb5a13b6304f
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32948637"
---
# <a name="using-imultipleresults-to-process-multiple-result-sets"></a>IMultipleResults を使用した複数の結果セットの処理
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  コンシューマーを使用して、 **IMultipleResults**インターフェイスによって返される結果を処理する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダー コマンドを実行します。 ときに、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーの実行でコマンドを送信する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ステートメントを実行し、すべての結果を返します。  
  
 クライアントはコマンドの実行結果をすべて処理する必要があります。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーのコマンドの実行が結果として複数の行セット オブジェクトを作成、使用して、 **IMultipleResults**インターフェイスをアプリケーション データの取得が完了したことを確認してください、クライアントが開始したラウンド トリップされます。  
  
 次[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントでは、複数の行セット、一部を含む行のデータを生成、 **OrderDetails**テーブルと COMPUTE BY 句の一部を含む結果。  
  
```  
SELECT OrderID, FullPrice = (UnitPrice * Quantity), Discount,  
    Discounted = UnitPrice * (1 - Discount) * Quantity  
FROM OrderDetails  
ORDER BY OrderID  
COMPUTE  
    SUM(UnitPrice * Quantity), SUM(UnitPrice * (1 - Discount) * Quantity)  
    BY OrderID  
```  
  
 このテキストを含んだコマンドを実行し、返される結果のインターフェイスとして行セットを要求した場合、最初の行セットのみが返されます。 コンシューマーでは、返された行セットのすべての行を処理できます。 DBPROP_MULTIPLECONNECTIONS データ ソースのプロパティ設定されている場合が VARIANT_FALSE と MARS が有効でない接続で、セッション オブジェクト上の他のコマンドで実行することができますが、(、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーが別に作成することはできません接続の場合)、コマンドが取り消されるまでです。 接続で MARS が有効でない場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] DBPROP_MULTIPLECONNECTIONS が VARIANT_FALSE に、E_FAIL が返された場合は、アクティブなトランザクションがある場合は、Native Client OLE DB プロバイダーは DB_E_OBJECTOPEN エラーを返します。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは、DB_E_OBJECTOPEN を使用する場合に、出力パラメーターがストリーム送信され、アプリケーションが呼び出す前にすべての返された出力パラメーター値を使用していないはも返します**imultipleresults::getresults**を次の結果セットを取得します。 MARS が有効でないと、接続がビジーな行セットを生成しないか、サーバー カーソルではない行セットを生成するコマンドを実行している場合と、DBPROP_MULTIPLECONNECTIONS データ ソースのプロパティが VARIANT_TRUE に設定されている場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native ClientOLE DB プロバイダーを作成、同時実行コマンド オブジェクトをサポートするために追加の接続、トランザクションがアクティブを返します。 この場合、しない限り、エラーします。 トランザクションとロックは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によって接続ごとに管理されます。 他の接続が作成されている場合でも、個別の接続のコマンドはロックを共有しません。 コマンドによって要求された行にロックを設定することで、そのコマンドが別のコマンドによってブロックされないようにする必要があります。 MARS を有効にしている場合、その接続では複数のコマンドをアクティブにできます。明示的なトランザクションを使用している場合、すべてのコマンドが共通のトランザクションを共有します。  
  
 取り消すには、コマンドを使用するか[issabort::abort](../../relational-databases/native-client-ole-db-interfaces/issabort-abort-ole-db.md)コマンド オブジェクトおよび派生行セットに対して保持されているすべての参照を解放します。  
  
 使用して**IMultipleResults**コマンドの実行によって生成されたすべての行セットを取得するコンシューマーは、すべてのインスタンスにでき、コンシューマーは適切にコマンドの実行をキャンセルしで使用するためのセッション オブジェクトを解放する場合の判別その他のコマンド。  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] カーソルを使用するときは、コマンドを実行するとカーソルが作成されます。 カーソルを作成するときに [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は成功か失敗を返します。したがって、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスへのラウンド トリップが完了するのはコマンドを実行した結果が返ってきたときです。 各**GetNextRows**呼び出しは、ラウンド トリップになります。 このようなしくみによって、サーバー カーソルからのフェッチの結果である行セットを処理する、複数のアクティブなコマンド オブジェクトが存在できます。 詳細については、次を参照してください。[行セットと SQL Server カーソル](../../relational-databases/native-client-ole-db-rowsets/rowsets-and-sql-server-cursors.md)です。  
  
## <a name="see-also"></a>参照  
 [[コマンド]](../../relational-databases/native-client-ole-db-commands/commands.md)  
  
  
