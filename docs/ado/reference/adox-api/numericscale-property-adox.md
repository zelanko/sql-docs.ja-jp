---
description: NumericScale プロパティ (ADOX)
title: NumericScale プロパティ (ADOX) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 3420a3e3d1e6ee06eaa63926604f3688b3f0590b
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/24/2020
ms.locfileid: "88769911"
---
# <a name="numericscale-property-adox"></a>NumericScale プロパティ (ADOX)
列の数値の小数点以下桁数を示します。  
  
## <a name="settings-and-return-values"></a>設定と戻り値  
 [Type](./type-property-column-adox.md)プロパティが**Adnumeric**または**adDecimal**の場合に、列のデータ値の小数点以下桁数を示す**バイト**値を設定して返します。 他のすべてのデータ型では、 **Numericscale**は無視されます。  
  
## <a name="remarks"></a>解説  
 既定値は 0 です。  
  
 既にコレクションに追加されている[列](./column-object-adox.md)オブジェクトの**numericscale**は読み取り専用です。  
  
## <a name="applies-to"></a>適用対象  
 [Column オブジェクト (ADOX)](./column-object-adox.md)  
  
## <a name="see-also"></a>参照  
 [ADOX のコード例: NumericScale および Precision プロパティの例 (VB)](./adox-code-example-numericscale-and-precision-properties-example-vb.md)   
 [Type プロパティ (列) (ADOX)](./type-property-column-adox.md)