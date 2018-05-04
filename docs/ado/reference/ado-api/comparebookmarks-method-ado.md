---
title: CompareBookmarks メソッド (ADO) |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- CompareBookmarks
- Recordset20::CompareBookmarks
- Recordset20::raw_CompareBookmarks
helpviewer_keywords:
- CompareBookmarks method [ADO]
ms.assetid: d0b64286-2cc4-4a22-8f1d-9aefeebbcbc6
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f17b1bbb0793e06a5ecbbec393fd87ebcdbc311e
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="comparebookmarks-method-ado"></a>CompareBookmarks メソッド (ADO)
2 つのブックマークを比較し、これらの相対値を示す値を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
result = recordset.CompareBookmarks(Bookmark1, Bookmark2)  
```  
  
## <a name="return-value"></a>戻り値  
 返します、 [CompareEnum](../../../ado/reference/ado-api/compareenum.md)ブックマークによって表される 2 つのレコードの相対行位置を示す値。  
  
#### <a name="parameters"></a>パラメーター  
 *Bookmark1*  
 最初の行のブックマークです。  
  
 *Bookmark2*  
 2 番目の行のブックマークです。  
  
## <a name="remarks"></a>解説  
 ブックマークが同じに適用する必要があります[レコード セット](../../../ado/reference/ado-api/recordset-object-ado.md)オブジェクト、または**レコード セット**オブジェクトとその[クローン](../../../ado/reference/ado-api/clone-method-ado.md)です。 別のブックマークを確実に比較することはできません**Recordset**オブジェクト、同じソースまたはコマンドから作成された場合でもです。 ブックマークを比較することも、 **Recordset**オブジェクトの基になるプロバイダーが比較をサポートしていません。  
  
 ブックマーク内の行を一意に識別する、 **Recordset**オブジェクト。 使用して、[ブックマーク](../../../ado/reference/ado-api/bookmark-property-ado.md)現在の行のブックマークを取得するプロパティです。  
  
 ADO 公開としてブックマークのデータ型は、各プロバイダーに固有であるため、**バリアント**です。 たとえば、SQL Server のブックマークが型 DBTYPE_R8 (**二重**)。 ADO では、次の種類として、**バリアント**のサブタイプに**二重**です。  
  
 ブックマークを比較するときに、ADO は任意の型の強制変換を行いません。 単に値は、比較が行われる場所をプロバイダーに渡されます。 それらのブックマークが渡された場合、 **CompareBookmarks**メソッドが異なる型の変数に格納されている場合、次の型の不一致エラーを生成できます:"個の引数が正しくない型、有効な範囲外または競合互いにします。"  
  
 無効か、形式が正しくありませんをブックマークには、エラーが発生します。  
  
## <a name="applies-to"></a>適用対象  
 [Recordset オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [CompareBookmarks メソッドの例 (VB)](../../../ado/reference/ado-api/comparebookmarks-method-example-vb.md)   
 [CompareBookmarks メソッドの例 (vc++)](../../../ado/reference/ado-api/comparebookmarks-method-example-vc.md)   
 [Bookmark プロパティ (ADO)](../../../ado/reference/ado-api/bookmark-property-ado.md)
