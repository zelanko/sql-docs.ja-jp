---
title: Refresh メソッド (ADO) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Collection::Refresh
- Parameters::Refresh
- Properties::Refresh
helpviewer_keywords:
- Refresh method [ADO]
ms.assetid: 089b7ca7-684f-4259-8032-5bd1ecc54426
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a676bf5eb3d8d98f1b2eb9367aa8ad56f0da209d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67931253"
---
# <a name="refresh-method-ado"></a>Refresh メソッド (ADO)
プロバイダーによって使用可能なオブジェクトを反映するように、コレクション内のオブジェクトを更新します。  
  
## <a name="syntax"></a>構文  
  
```  
  
collection.Refresh  
```  
  
## <a name="remarks"></a>解説  
 **Refresh**メソッドは、呼び出し元のコレクションに応じてさまざまなタスクを行います。  
  
### <a name="parameters"></a>パラメーター  
 [Command](../../../ado/reference/ado-api/command-object-ado.md)オブジェクトの[Parameters](../../../ado/reference/ado-api/parameters-collection-ado.md)コレクションに対して**Refresh**メソッドを使用すると、 **command**オブジェクトで指定されたストアドプロシージャまたはパラメーター化クエリのプロバイダー側のパラメーター情報が取得されます。 このコレクションは、ストアドプロシージャ呼び出しまたはパラメーター化クエリをサポートしていないプロバイダーに対しては空になります。  
  
 **Refresh**メソッドを呼び出す前[に、](../../../ado/reference/ado-api/commandtype-property-ado.md) **command**オブジェクトの[ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md)プロパティを有効な[接続](../../../ado/reference/ado-api/connection-object-ado.md)オブジェクト、 [CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md)プロパティを有効なコマンド、および**adCmdStoredProc**に設定する必要があります。  
  
 **Refresh**メソッドを呼び出す前に**Parameters**コレクションにアクセスすると、ADO は自動的にメソッドを呼び出し、コレクションにデータを設定します。  
  
> [!NOTE]
>  **Refresh**メソッドを使用してプロバイダーからパラメーター情報を取得し、1つまたは複数の可変長データ型[パラメーター](../../../ado/reference/ado-api/parameter-object.md)オブジェクトを返す場合、ADO では、可能な最大サイズに基づいてパラメーターにメモリが割り当てられ、実行中にエラーが発生します。 エラーを回避するには、 [Execute](../../../ado/reference/ado-api/execute-method-ado-command.md)メソッドを呼び出す前に、これらのパラメーターの[Size](../../../ado/reference/ado-api/size-property-ado-parameter.md)プロパティを明示的に設定する必要があります。  
  
### <a name="fields"></a>フィールド  
 [フィールド](../../../ado/reference/ado-api/fields-collection-ado.md)コレクションに対して**Refresh**メソッドを使用しても、可視効果はありません。 基になるデータベース構造から変更を取得するには、 [Requery](../../../ado/reference/ado-api/requery-method.md)メソッドを使用するか、[レコードセット](../../../ado/reference/ado-api/recordset-object-ado.md)オブジェクトでブックマークがサポートされていない場合は[MoveFirst](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)メソッドを使用する必要があります。  
  
### <a name="properties"></a>Properties  
 一部のオブジェクトの**プロパティ**コレクションで**Refresh**メソッドを使用すると、プロバイダーが公開する動的プロパティがコレクションに設定されます。 これらのプロパティは、ADO によってサポートされる組み込みプロパティ以外の、プロバイダー固有の機能に関する情報を提供します。  
  
## <a name="applies-to"></a>適用対象  
  
||||  
|-|-|-|  
|[Axes コレクション](../../../ado/reference/ado-md-api/axes-collection-ado-md.md)|[Columns コレクション](../../../ado/reference/adox-api/columns-collection-adox.md)|[CubeDefs コレクション](../../../ado/reference/ado-md-api/cubedefs-collection-ado-md.md)|  
|[Dimensions コレクション](../../../ado/reference/ado-md-api/dimensions-collection-ado-md.md)|[Errors コレクション](../../../ado/reference/ado-api/errors-collection-ado.md)|[Fields コレクション](../../../ado/reference/ado-api/fields-collection-ado.md)|  
|[Groups コレクション](../../../ado/reference/adox-api/groups-collection-adox.md)|[階層のコレクション](../../../ado/reference/ado-md-api/hierarchies-collection-ado-md.md)|[Indexes コレクション](../../../ado/reference/adox-api/indexes-collection-adox.md)|  
|[Keys コレクション](../../../ado/reference/adox-api/keys-collection-adox.md)|[レベルのコレクション](../../../ado/reference/ado-md-api/levels-collection-ado-md.md)|[Members コレクション](../../../ado/reference/ado-md-api/members-collection-ado-md.md)|  
|[Parameters コレクション](../../../ado/reference/ado-api/parameters-collection-ado.md)|[位置のコレクション](../../../ado/reference/ado-md-api/positions-collection-ado-md.md)|[Procedures コレクション](../../../ado/reference/adox-api/procedures-collection-adox.md)|  
|[プロパティのコレクション](../../../ado/reference/ado-api/properties-collection-ado.md)|[Tables コレクション](../../../ado/reference/adox-api/tables-collection-adox.md)|[Users コレクション](../../../ado/reference/adox-api/users-collection-adox.md)|  
|[Views コレクション](../../../ado/reference/adox-api/views-collection-adox.md)|||  
  
## <a name="see-also"></a>参照  
 [Refresh メソッドの例 (VB)](../../../ado/reference/ado-api/refresh-method-example-vb.md)   
 [Refresh メソッドの例 (VC + +)](../../../ado/reference/ado-api/refresh-method-example-vc.md)   
 [Count プロパティ (ADO)](../../../ado/reference/ado-api/count-property-ado.md)   
 [Refresh メソッド (RDS)](../../../ado/reference/rds-api/refresh-method-rds.md)
