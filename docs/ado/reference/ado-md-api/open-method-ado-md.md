---
title: "Open メソッド (ADO MD) |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Open
- Cellset::Open
helpviewer_keywords: Open method [ADO MD]
ms.assetid: a87d8080-a238-45e5-bc80-9a8625b3810f
caps.latest.revision: "14"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 1b80a0a92956315d7d19db5d17a535b6fe2204b6
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="open-method-ado-md"></a>Open メソッド (ADO MD)
多次元クエリの結果を取得し、結果を返します、[セルセット](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)です。  
  
## <a name="syntax"></a>構文  
  
```  
  
Cellset.Open Source, ActiveConnection  
```  
  
#### <a name="parameters"></a>パラメーター  
 *ソース*  
 省略可。 A**バリアント**多次元式 (MDX) クエリなど、有効な多次元クエリを評価します。 *ソース*引数に対応、[ソース](../../../ado/reference/ado-md-api/source-property-ado-md.md)プロパティです。 MDX の詳細については、次を参照してください。、 [OLE DB のオンライン分析処理 (OLAP)](http://msdn.microsoft.com/en-us/8a7673c6-3ca1-4411-9f1e-adf1e47df4f3) Microsoft Data Access Components SDK のドキュメントです。  
  
 *ActiveConnection*  
 省略可。 A**バリアント**有効 ADO いずれかを指定する文字列に評価される[接続](../../../ado/reference/ado-api/connection-object-ado.md)オブジェクト変数の名前または接続の定義。 *ActiveConnection*引数を開くときの接続を指定する、[セルセット](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)オブジェクト。 この引数に接続の定義を渡すと、ADO は、指定されたパラメーターを使用して新しい接続を開きます。 *ActiveConnection*引数に対応、 [ActiveConnection](../../../ado/reference/ado-md-api/activeconnection-property-ado-md.md)プロパティです。  
  
## <a name="remarks"></a>解説  
 **開く**メソッドでは、そのパラメーターのいずれかを省略するし、開こうとしての前に、対応するプロパティ値が設定されていないエラーが生成されます、**セルセット**です。  
  
## <a name="applies-to"></a>適用対象  
 [CellSet オブジェクト (ADO MD)](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)  
  
## <a name="see-also"></a>参照  
 [セル セットの例 (VB)](../../../ado/reference/ado-md-api/cellset-example-vb.md)   
 [ActiveConnection プロパティ (ADO MD)](../../../ado/reference/ado-md-api/activeconnection-property-ado-md.md)   
 [Close メソッド (ADO MD)](../../../ado/reference/ado-md-api/close-method-ado-md.md)   
 [接続オブジェクト (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)   
 [Source プロパティ (ADO MD)](../../../ado/reference/ado-md-api/source-property-ado-md.md)   
 [State プロパティ (ADO MD)](../../../ado/reference/ado-md-api/state-property-ado-md.md)
