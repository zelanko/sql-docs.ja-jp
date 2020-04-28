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
ms.openlocfilehash: 089fad427989c26ed1ed22ec3e9267297a29b820
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "67949389"
---
# <a name="open-method-ado-md"></a>Open メソッド (ADO MD)
多次元クエリの結果を取得し、結果を[セルセット](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)に返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Cellset.Open Source, ActiveConnection  
```  
  
#### <a name="parameters"></a>パラメーター  
 *ソース*  
 任意。 多次元式 (MDX) クエリなど、有効な多次元クエリに評価される**バリアント**です。 *Source*引数は、 [source](../../../ado/reference/ado-md-api/source-property-ado-md.md)プロパティに対応しています。 MDX の詳細については、Microsoft Data Access Components SDK の[オンライン分析処理 (OLAP) の OLE DB](https://msdn.microsoft.com/8a7673c6-3ca1-4411-9f1e-adf1e47df4f3)に関するドキュメントを参照してください。  
  
 *ActiveConnection*  
 任意。 有効な ADO[接続](../../../ado/reference/ado-api/connection-object-ado.md)オブジェクト変数名または接続の定義のいずれかを指定する文字列に評価される**バリアント**。 *ActiveConnection*引数は、[セルセット](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)オブジェクトを開くための接続を指定します。 この引数に対して接続定義を渡すと、指定されたパラメーターを使用して新しい接続が開かれます。 *ActiveConnection*引数は、 [ActiveConnection](../../../ado/reference/ado-md-api/activeconnection-property-ado-md.md)プロパティに対応しています。  
  
## <a name="remarks"></a>Remarks  
 **Open**メソッドは、パラメーターのいずれかが省略されていて、それに対応するプロパティ値が**セル**セットを開こうとする前に設定されていない場合に、エラーを生成します。  
  
## <a name="applies-to"></a>適用対象  
 [CellSet オブジェクト (ADO MD)](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)  
  
## <a name="see-also"></a>参照  
 [セルセットの例 (VB)](../../../ado/reference/ado-md-api/cellset-example-vb.md)   
 [ActiveConnection プロパティ (ADO MD)](../../../ado/reference/ado-md-api/activeconnection-property-ado-md.md)   
 [Close メソッド (ADO MD)](../../../ado/reference/ado-md-api/close-method-ado-md.md)   
 [Connection オブジェクト (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)   
 [Source プロパティ (ADO MD)](../../../ado/reference/ado-md-api/source-property-ado-md.md)   
 [State プロパティ (ADO MD)](../../../ado/reference/ado-md-api/state-property-ado-md.md)
