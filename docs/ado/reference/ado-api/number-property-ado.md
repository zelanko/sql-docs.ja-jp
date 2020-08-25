---
description: Number プロパティ (ADO)
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
author: rothja
ms.author: jroth
ms.openlocfilehash: fe4984a9bdbeff69f7c2beba4d91833cdca85f50
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/24/2020
ms.locfileid: "88774101"
---
# <a name="number-property-ado"></a>Number プロパティ (ADO)
[エラー](./error-object.md)オブジェクトを一意に識別する番号を示します。  
  
## <a name="return-value"></a>戻り値  
 [Errorvalueenum](./errorvalueenum.md)定数のいずれかに対応できる**Long 型**の値を返します。  
  
## <a name="remarks"></a>解説  
 **Number**プロパティを使用して、発生したエラーを特定します。 プロパティの値は、エラー状態に対応する一意の番号です。  
  
 [Errors](./errors-collection-ado.md)コレクションは、16進数形式 (0x80004005 など) または long 値 (たとえば、2147467259) のいずれかで HRESULT を返します。 これらの Hresult は、OLE DB や OLE 自体など、基になるコンポーネントによって発生する可能性があります。 これらの数値の詳細については、 [OLE DB プログラマーリファレンス](/previous-versions/windows/desktop/ms713643(v=vs.85))の「[エラー (OLE DB)](/previous-versions/windows/desktop/ms724533(v=vs.85)) 」を参照してください *。*  
  
## <a name="applies-to"></a>適用対象  
 [Error オブジェクト](./error-object.md)  
  
## <a name="see-also"></a>参照  
 [Description、HelpContext、HelpFile、のエラー、Number、Source、および SQLState プロパティの例 (VB)](./description-helpcontext-helpfile-nativeerror-number-source-example-vb.md)   
 [Description、HelpContext、HelpFile、のエラー、Number、Source、および SQLState プロパティの例 (VC + +)](./description-helpcontext-helpfile-nativeerror-number-source-example-vc.md)   
 [Description プロパティ](./description-property.md)   
 [HelpContext、HelpFile プロパティ](./helpcontext-helpfile-properties.md)   
 [Source プロパティ (ADO Error)](./source-property-ado-error.md)