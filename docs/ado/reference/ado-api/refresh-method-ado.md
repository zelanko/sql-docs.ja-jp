---
title: "Refresh メソッド (ADO) |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- _Collection::Refresh
- Parameters::Refresh
- Properties::Refresh
helpviewer_keywords:
- Refresh method [ADO]
ms.assetid: 089b7ca7-684f-4259-8032-5bd1ecc54426
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 00a739b4bf90651f1e38402a8309482bf8217680
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="refresh-method-ado"></a>Refresh メソッド (ADO)
プロバイダーをコレクションから、使用可能なオブジェクトを反映するように、固有の仕様内のオブジェクトを更新します。  
  
## <a name="syntax"></a>構文  
  
```  
  
collection.Refresh  
```  
  
## <a name="remarks"></a>解説  
 **更新**メソッドが呼び出し元となるコレクションに応じて異なるタスクを実行します。  
  
### <a name="parameters"></a>パラメーター  
 使用して、**更新**メソッドを[パラメーター](../../../ado/reference/ado-api/parameters-collection-ado.md)のコレクション、[コマンド](../../../ado/reference/ado-api/command-object-ado.md)オブジェクトは、プロバイダー側のパラメーター、ストアド プロシージャの情報を取得または指定されたパラメーター化クエリ、**コマンド**オブジェクト。 コレクションは、ストアド プロシージャの呼び出しまたはパラメーター化クエリをサポートしないプロバイダーを空になります。  
  
 設定する必要があります、 [ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md)のプロパティ、**コマンド**有効なオブジェクト[接続](../../../ado/reference/ado-api/connection-object-ado.md)オブジェクト、 [CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md)プロパティ有効なコマンドを[CommandType](../../../ado/reference/ado-api/commandtype-property-ado.md)プロパティを**adCmdStoredProc**呼び出す前に、**更新**メソッドです。  
  
 アクセスする場合、**パラメーター**コレクションを呼び出す前に、**更新**、ADO 自動的にメソッドを呼び出して、メソッドのコレクションを設定します。  
  
> [!NOTE]
>  使用する場合、**更新**プロバイダーからパラメーター情報を取得するメソッドが 1 つまたは複数の可変長データ型を返します[パラメーター](../../../ado/reference/ado-api/parameter-object.md)オブジェクト、ADO が基づくパラメーターのメモリを割り当てることがあります潜在的なサイズの最大の実行中にエラーが発生します。 明示的に設定する必要があります、[サイズ](../../../ado/reference/ado-api/size-property-ado-parameter.md)呼び出す前にこれらのパラメーター プロパティ、 [Execute](../../../ado/reference/ado-api/execute-method-ado-command.md)エラーを防ぐためのメソッドです。  
  
### <a name="fields"></a>フィールド  
 使用して、**更新**メソッドを[フィールド](../../../ado/reference/ado-api/fields-collection-ado.md)コレクションが表示される影響を与えません。 基になるデータベース構造から変更を取得する、いずれかを使用する必要があります、 [Requery](../../../ado/reference/ado-api/requery-method.md)メソッドまたはの場合、 [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)オブジェクトは、ブックマークをサポートしていません、 [MoveFirst](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)メソッドです。  
  
### <a name="properties"></a>[プロパティ]  
 使用して、**更新**メソッドを**プロパティ**一部のオブジェクトのコレクション、プロバイダーを公開する動的なプロパティをコレクションに設定します。 これらのプロパティは、組み込みプロパティ ADO サポート以外のプロバイダーに固有の機能に関する情報を提供します。  
  
## <a name="applies-to"></a>適用対象  
  
||||  
|-|-|-|  
|[Axes コレクション](../../../ado/reference/ado-md-api/axes-collection-ado-md.md)|[Columns コレクション](../../../ado/reference/adox-api/columns-collection-adox.md)|[CubeDefs コレクション](../../../ado/reference/ado-md-api/cubedefs-collection-ado-md.md)|  
|[Dimensions コレクション](../../../ado/reference/ado-md-api/dimensions-collection-ado-md.md)|[Errors コレクション](../../../ado/reference/ado-api/errors-collection-ado.md)|[Fields コレクション](../../../ado/reference/ado-api/fields-collection-ado.md)|  
|[グループのコレクション](../../../ado/reference/adox-api/groups-collection-adox.md)|[Hierarchies コレクション](../../../ado/reference/ado-md-api/hierarchies-collection-ado-md.md)|[Indexes コレクション](../../../ado/reference/adox-api/indexes-collection-adox.md)|  
|[キーのコレクション](../../../ado/reference/adox-api/keys-collection-adox.md)|[レベルのコレクション](../../../ado/reference/ado-md-api/levels-collection-ado-md.md)|[メンバーのコレクション](../../../ado/reference/ado-md-api/members-collection-ado-md.md)|  
|[Parameters コレクション](../../../ado/reference/ado-api/parameters-collection-ado.md)|[位置コレクション](../../../ado/reference/ado-md-api/positions-collection-ado-md.md)|[プロシージャのコレクション](../../../ado/reference/adox-api/procedures-collection-adox.md)|  
|[プロパティのコレクション](../../../ado/reference/ado-api/properties-collection-ado.md)|[テーブル コレクション](../../../ado/reference/adox-api/tables-collection-adox.md)|[ユーザーのコレクション](../../../ado/reference/adox-api/users-collection-adox.md)|  
|[ビューのコレクション](../../../ado/reference/adox-api/views-collection-adox.md)|||  
  
## <a name="see-also"></a>参照  
 [メソッドの例 (VB) の更新します。](../../../ado/reference/ado-api/refresh-method-example-vb.md)   
 [メソッドの例 (vc++) の更新します。](../../../ado/reference/ado-api/refresh-method-example-vc.md)   
 [Count プロパティ (ADO)](../../../ado/reference/ado-api/count-property-ado.md)   
 [Refresh メソッド (RDS)](../../../ado/reference/rds-api/refresh-method-rds.md)

