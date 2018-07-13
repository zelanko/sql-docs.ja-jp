---
title: IMultipleResults を使用して複数の結果セットを処理する |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- multiple rowsets
- rowsets [OLE DB], multiple
- IMultipleResults interface
- multiple-rowset results
ms.assetid: 754d3f30-7d94-4b67-8dac-baf2699ce9c6
caps.latest.revision: 39
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a9e60c1b2bbffb236c933f9b01a46d86ef371c2d
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37428311"
---
# <a name="using-imultipleresults-to-process-multiple-result-sets"></a>IMultipleResults を使用した複数の結果セットの処理
  コンシューマーを使用して、 **IMultipleResults**インターフェイスによって返される結果を処理する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダー コマンドを実行します。 ときに、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは、実行するためのコマンドを送信する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ステートメントを実行し、結果が返されます。  
  
 クライアントはコマンドの実行結果をすべて処理する必要があります。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーのコマンドの実行が結果として複数の行セット オブジェクトを作成、使用、 **IMultipleResults**アプリケーション データの取得が完了したことを確認するインターフェイス、クライアントが開始したラウンド トリップします。  
  
 次[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントで生成する複数の行セット、いくつかの行データを含む、 **OrderDetails**テーブルと COMPUTE BY 句の結果を含むいくつか。  
  
```  
SELECT OrderID, FullPrice = (UnitPrice * Quantity), Discount,  
    Discounted = UnitPrice * (1 - Discount) * Quantity  
FROM OrderDetails  
ORDER BY OrderID  
COMPUTE  
    SUM(UnitPrice * Quantity), SUM(UnitPrice * (1 - Discount) * Quantity)  
    BY OrderID  
```  
  
 このテキストを含んだコマンドを実行し、返される結果のインターフェイスとして行セットを要求した場合、最初の行セットのみが返されます。 コンシューマーでは、返された行セットのすべての行を処理できます。 DBPROP_MULTIPLECONNECTIONS データ ソースのプロパティ設定されている場合が VARIANT_FALSE の場合、および MARS が有効でない接続で、セッション オブジェクトでないその他のコマンドを実行することができますが、(、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーが別に作成することはできません接続の場合)、コマンドが取り消されるまでです。 接続で MARS が有効でない場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] DBPROP_MULTIPLECONNECTIONS が VARIANT_FALSE で、E_FAIL が返された場合は、アクティブなトランザクションがある場合、Native Client OLE DB プロバイダーは DB_E_OBJECTOPEN エラーを返します。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーから DB_E_OBJECTOPEN を使用する場合に、出力パラメーターがストリーム送信され、アプリケーションが呼び出す前にすべての返された出力パラメーターの値を使用していないが返さも **:getresults**を次の結果セットを取得します。 MARS が有効でないと、接続がビジー状態の行セットを生成しないか、サーバー カーソルではない行セットを生成するコマンドを実行している場合と、DBPROP_MULTIPLECONNECTIONS データ ソースのプロパティが VARIANT_TRUE に設定されている場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native ClientOLE DB プロバイダー作成コマンドの同時実行のオブジェクトをサポートする追加の接続、トランザクションがアクティブでを返します。 この場合、エラーされます。 トランザクションとロックは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によって接続ごとに管理されます。 他の接続が作成されている場合でも、個別の接続のコマンドはロックを共有しません。 コマンドによって要求された行にロックを設定することで、そのコマンドが別のコマンドによってブロックされないようにする必要があります。 MARS を有効にしている場合、その接続では複数のコマンドをアクティブにできます。明示的なトランザクションを使用している場合、すべてのコマンドが共通のトランザクションを共有します。  
  
 取り消すには、コマンドを使用するか[issabort::abort](../native-client-ole-db-interfaces/issabort-abort-ole-db.md)をコマンド オブジェクトおよび派生行セットで保持されているすべての参照を解放します。  
  
 使用して**IMultipleResults**を適切に判断すると、コマンドの実行をキャンセルし、無料で使用するためのセッション オブジェクトはすべてのインスタンスで、コンシューマーがコマンドの実行によって生成されたすべての行セットを取得できその他のコマンド。  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] カーソルを使用するときは、コマンドを実行するとカーソルが作成されます。 カーソルを作成するときに [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は成功か失敗を返します。したがって、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスへのラウンド トリップが完了するのはコマンドを実行した結果が返ってきたときです。 各**GetNextRows**呼び出しのラウンド トリップになります。 このようなしくみによって、サーバー カーソルからのフェッチの結果である行セットを処理する、複数のアクティブなコマンド オブジェクトが存在できます。 詳細については、次を参照してください。[行セットと SQL Server カーソル](../native-client-ole-db-rowsets/rowsets-and-sql-server-cursors.md)します。  
  
## <a name="see-also"></a>参照  
 [[コマンド]](commands.md)  
  
  
