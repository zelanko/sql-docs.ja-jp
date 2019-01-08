---
title: Delete メソッド (ADO Parameters コレクション) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _DynaCollection::Delete
- _DynaCollection::raw_Delete
helpviewer_keywords:
- Delete method [ADO]
ms.assetid: 160c575e-df63-4ade-a2d3-5fd8f72e70cc
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8864ac47f3fa212cc6c204cc79d587b8952512cd
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/28/2018
ms.locfileid: "52527414"
---
# <a name="delete-method-ado-parameters-collection"></a>Delete メソッド (ADO Parameters コレクション)
オブジェクトを削除、[パラメーター](../../../ado/reference/ado-api/parameters-collection-ado.md)コレクション。  
  
## <a name="syntax"></a>構文  
  
```  
  
Parameters.Delete Index  
```  
  
#### <a name="parameters"></a>パラメーター  
 *Index*  
 A**文字列**をコレクション内で、削除するオブジェクトまたはオブジェクトの位置 (インデックス) の名前を含む値です。  
  
## <a name="remarks"></a>コメント  
 使用して、**削除**一連のメソッドを使用して、一方のオブジェクトをコレクションから削除できます。 このメソッドでのみ使用できます、**パラメーター**のコレクションを[コマンド](../../../ado/reference/ado-api/command-object-ado.md)オブジェクト。 使用する必要があります、[パラメーター](../../../ado/reference/ado-api/parameter-object.md)オブジェクトの[名前](../../../ado/reference/ado-api/name-property-ado.md)プロパティまたはそのコレクションのインデックスを呼び出すときに、**削除**メソッド、オブジェクト変数は有効な引数ではありません。  
  
## <a name="applies-to"></a>適用対象  
 [Parameters コレクション (ADO)](../../../ado/reference/ado-api/parameters-collection-ado.md)  
  
## <a name="see-also"></a>参照  
 [Delete メソッド (ADO Fields コレクション)](../../../ado/reference/ado-api/delete-method-ado-fields-collection.md)   
 [Delete メソッド (ADO Recordset)](../../../ado/reference/ado-api/delete-method-ado-recordset.md)   
 [DeleteRecord メソッド (ADO)](../../../ado/reference/ado-api/deleterecord-method-ado.md)
