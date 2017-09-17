---
title: "NumericScale プロパティ (ADOX) |Microsoft ドキュメント"
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
- _Column::PutNumericScale
- _Column::GetNumericScale
- _Column::NumericScale
- _Column::put_NumericScale
- _Column::get_NumericScale
helpviewer_keywords:
- NumericScale property [ADOX]
ms.assetid: 573ee5d1-57c7-4a27-be79-a0e12944ad9b
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: a5f943223be304de56e52f54510bd6d27bac6d15
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="numericscale-property-adox"></a>NumericScale プロパティ (ADOX)
列の数値の小数点以下桁数を示します。  
  
## <a name="settings-and-return-values"></a>設定と戻り値  
 設定を返します、**バイト**、列のデータ値の小数点以下桁数の値と、[型](../../../ado/reference/adox-api/type-property-column-adox.md)プロパティは**adNumeric**または**adDecimal**です。 **NumericScale**他のすべてのデータ型は無視されます。  
  
## <a name="remarks"></a>解説  
 既定値は、ゼロ (0) です。  
  
 **NumericScale**は読み取り専用の[列](../../../ado/reference/adox-api/column-object-adox.md)オブジェクトをコレクションに既に追加されています。  
  
## <a name="applies-to"></a>適用対象  
 [Column オブジェクト (ADOX)](../../../ado/reference/adox-api/column-object-adox.md)  
  
## <a name="see-also"></a>参照  
 [ADOX コードの例: NumericScale し (VB) の有効桁数のプロパティの例](../../../ado/reference/adox-api/adox-code-example-numericscale-and-precision-properties-example-vb.md)   
 [Type プロパティ (列) (ADOX)](../../../ado/reference/adox-api/type-property-column-adox.md)
