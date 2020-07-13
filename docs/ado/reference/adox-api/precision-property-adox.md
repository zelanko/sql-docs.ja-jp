---
title: Precision プロパティ (ADOX) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Column::put_Precision
- _Column::PutPrecision
- _Column::GetPrecision
- _Column::get_Precision
- _Column::Precision
helpviewer_keywords:
- Precision property [ADOX]
ms.assetid: 0e0ecbbf-d7de-49d4-a128-5a519ecd54ba
author: rothja
ms.author: jroth
ms.openlocfilehash: 67512b74e4c2b869cb7b1f9397462ce5566557a8
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2020
ms.locfileid: "82763723"
---
# <a name="precision-property-adox"></a>Precision プロパティ (ADOX)
[列](../../../ado/reference/adox-api/column-object-adox.md)のデータ値の最大有効桁数を示します。  
  
## <a name="settings-and-return-values"></a>設定と戻り値  
 [Type](../../../ado/reference/adox-api/type-property-column-adox.md)プロパティが数値型の場合に、列のデータ値の最大有効桁数である**Long**型の値を設定して返します。 その他のすべてのデータ型では、**有効桁数**は無視されます。  
  
## <a name="remarks"></a>解説  
 既定値はゼロ (**0**) です。  
  
 このプロパティは、既にコレクションに追加されている[列](../../../ado/reference/adox-api/column-object-adox.md)オブジェクトに対しては読み取り専用です。  
  
## <a name="applies-to"></a>適用対象  
 [Column オブジェクト (ADOX)](../../../ado/reference/adox-api/column-object-adox.md)  
  
## <a name="see-also"></a>参照  
 [ADOX のコード例: NumericScale および Precision プロパティの例 (VB)](../../../ado/reference/adox-api/adox-code-example-numericscale-and-precision-properties-example-vb.md)   
 [Type プロパティ (列) (ADOX)](../../../ado/reference/adox-api/type-property-column-adox.md)   
 [Column オブジェクト (ADOX)](../../../ado/reference/adox-api/column-object-adox.md)
