---
title: Number プロパティ (ADO) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Error::Number
- Error::GetNumber
- Error::get_Number
helpviewer_keywords:
- number property [ADO]
ms.assetid: f92323c5-dd11-4a63-a505-d9014a0f067f
author: MightyPen
ms.author: genemi
ms.openlocfilehash: ce027747c843e02998f4845db7075e70cf8733b6
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "67917996"
---
# <a name="number-property-ado"></a>Number プロパティ (ADO)
[エラー](../../../ado/reference/ado-api/error-object.md)オブジェクトを一意に識別する番号を示します。  
  
## <a name="return-value"></a>戻り値  
 [Errorvalueenum](../../../ado/reference/ado-api/errorvalueenum.md)定数のいずれかに対応できる**Long 型**の値を返します。  
  
## <a name="remarks"></a>Remarks  
 **Number**プロパティを使用して、発生したエラーを特定します。 プロパティの値は、エラー状態に対応する一意の番号です。  
  
 [Errors](../../../ado/reference/ado-api/errors-collection-ado.md)コレクションは、16進数形式 (0x80004005 など) または long 値 (たとえば、2147467259) のいずれかで HRESULT を返します。 これらの Hresult は、OLE DB や OLE 自体など、基になるコンポーネントによって発生する可能性があります。 これらの数値の詳細については、 [OLE DB プログラマーリファレンス](https://msdn.microsoft.com/3c5e2dd5-35e5-4a93-ac3a-3818bb43bbf8)の「[エラー (OLE DB)](https://msdn.microsoft.com/ed74e62d-4948-4eeb-a7c9-fd7ad46af7fd) 」を参照してください *。*  
  
## <a name="applies-to"></a>適用対象  
 [Error オブジェクト](../../../ado/reference/ado-api/error-object.md)  
  
## <a name="see-also"></a>参照  
 [Description、HelpContext、HelpFile、のエラー、Number、Source、および SQLState プロパティの例 (VB)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vb.md)   
 [Description、HelpContext、HelpFile、のエラー、Number、Source、および SQLState プロパティの例 (VC + +)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vc.md)   
 [Description プロパティ](../../../ado/reference/ado-api/description-property.md)   
 [HelpContext、HelpFile プロパティ](../../../ado/reference/ado-api/helpcontext-helpfile-properties.md)   
 [Source プロパティ (ADO Error)](../../../ado/reference/ado-api/source-property-ado-error.md)
