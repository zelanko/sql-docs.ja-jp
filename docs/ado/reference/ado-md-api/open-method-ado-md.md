---
title: Open メソッド (ADO MD) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Open
- Cellset::Open
helpviewer_keywords:
- Open method [ADO MD]
ms.assetid: a87d8080-a238-45e5-bc80-9a8625b3810f
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: e22ab07f40ad6b4ef916d950909957b04c9d5be1
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "66708719"
---
# <a name="open-method-ado-md"></a>Open メソッド (ADO MD)
多次元クエリの結果を取得しに結果を返します、[セルセット](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Cellset.Open Source, ActiveConnection  
```  
  
#### <a name="parameters"></a>パラメーター  
 *Source*  
 任意。 A**バリアント**多次元式 (MDX) クエリなどの有効な多次元クエリを評価します。 *ソース*引数に対応、[ソース](../../../ado/reference/ado-md-api/source-property-ado-md.md)プロパティ。 MDX の詳細については、次を参照してください。、 [OLE DB のオンライン分析処理 (OLAP)](https://msdn.microsoft.com/8a7673c6-3ca1-4411-9f1e-adf1e47df4f3) Microsoft Data Access Components SDK のドキュメント。  
  
 *ActiveConnection*  
 任意。 A**バリアント**有効な ADO いずれかを指定する文字列に評価される[接続](../../../ado/reference/ado-api/connection-object-ado.md)オブジェクトの変数名または接続の定義。 *ActiveConnection*を開くときの接続を指定する引数、[セルセット](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)オブジェクト。 接続の定義がこの引数を渡すと、ADO は、指定されたパラメーターを使用して新しい接続を開きます。 *ActiveConnection*引数に対応、 [ActiveConnection](../../../ado/reference/ado-md-api/activeconnection-property-ado-md.md)プロパティ。  
  
## <a name="remarks"></a>コメント  
 **開く**メソッドのパラメーターのいずれかを省略するし、開くを試みる前に、対応するプロパティの値が設定されていない、エラーが発生、**セルセット**します。  
  
## <a name="applies-to"></a>適用対象  
 [CellSet オブジェクト (ADO MD)](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)  
  
## <a name="see-also"></a>関連項目  
 [セルセットの例 (VB)](../../../ado/reference/ado-md-api/cellset-example-vb.md)   
 [ActiveConnection プロパティ (ADO MD)](../../../ado/reference/ado-md-api/activeconnection-property-ado-md.md)   
 [Close メソッド (ADO MD)](../../../ado/reference/ado-md-api/close-method-ado-md.md)   
 [接続オブジェクト (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)   
 [Source プロパティ (ADO MD)](../../../ado/reference/ado-md-api/source-property-ado-md.md)   
 [State プロパティ (ADO MD)](../../../ado/reference/ado-md-api/state-property-ado-md.md)
