---
title: "Number プロパティ (ADO) |Microsoft ドキュメント"
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
- Error::Number
- Error::GetNumber
- Error::get_Number
helpviewer_keywords:
- number property [ADO]
ms.assetid: f92323c5-dd11-4a63-a505-d9014a0f067f
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 8d5567283a62a31842185afce7682d3641d6fcc4
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="number-property-ado"></a>Number プロパティ (ADO)
一意に識別する数値を示します、[エラー](../../../ado/reference/ado-api/error-object.md)オブジェクト。  
  
## <a name="return-value"></a>戻り値  
 返します、**長い**のいずれかに対応している可能性があります値、 [ErrorValueEnum](../../../ado/reference/ado-api/errorvalueenum.md)定数。  
  
## <a name="remarks"></a>解説  
 使用して、**数**プロパティのエラーが発生しました。 プロパティの値は、エラー状態に対応する一意の番号です。  
  
 [エラー](../../../ado/reference/ado-api/errors-collection-ado.md)コレクションは、16 進数形式 (たとえば、0x80004005) または long 型の値 (たとえば、: 2147467259) のいずれかに HRESULT を返します。 Hresult は、OLE DB または自体でも OLE など、基になるコンポーネントで生成されることができます。 これらの番号の詳細については、次を参照してください。[エラー (OLE DB)](http://msdn.microsoft.com/en-us/ed74e62d-4948-4eeb-a7c9-fd7ad46af7fd)で、 [OLE DB プログラマーズ リファレンス](http://msdn.microsoft.com/en-us/3c5e2dd5-35e5-4a93-ac3a-3818bb43bbf8)*です。*  
  
## <a name="applies-to"></a>適用対象  
 [Error オブジェクト](../../../ado/reference/ado-api/error-object.md)  
  
## <a name="see-also"></a>参照  
 [説明、HelpContext、HelpFile、以下、数、ソース、および SQLState のプロパティの例 (VB)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vb.md)   
 [説明、HelpContext、HelpFile、以下、数、ソース、および SQLState のプロパティの例 (vc++)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vc.md)   
 [Description プロパティ](../../../ado/reference/ado-api/description-property.md)   
 [HelpContext、HelpFile プロパティ](../../../ado/reference/ado-api/helpcontext-helpfile-properties.md)   
 [Source プロパティ (ADO エラー)](../../../ado/reference/ado-api/source-property-ado-error.md)

