---
title: "AllowNullsEnum |Microsoft ドキュメント"
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
- AllowNullsEnum
helpviewer_keywords:
- AllowNullsEnum enumeration [ADOX]
ms.assetid: 6acf3689-1a7f-4379-9d7f-df452ccbac27
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 2b9bb610e1b3f4a31e29ddee31e569c34528e243
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="allownullsenum"></a>AllowNullsEnum
Null 値を持つレコードのインデックスが作成するかどうかを指定します。  
  
|定数|値|Description|  
|--------------|-----------|-----------------|  
|**adIndexNullsAllow**|0|インデックスは、キー列が null 値のエントリを許可します。 キー列に null 値を入力すると、エントリは、インデックスに挿入されます。|  
|**adIndexNullsDisallow**|1|既定値です。 インデックスには、キー列が null 値のエントリはできません。 キー列に null 値を入力すると、エラーが発生します。|  
|**adIndexNullsIgnore**|2|インデックスは、null キーを含むエントリを挿入できません。 キー列に null 値を入力すると場合、エントリは無視され、エラーは発生しません。|  
|**adIndexNullsIgnoreAny**|4|インデックスは、いくつかのキー列が null 値を持つエントリを挿入できません。 複数の列を持つインデックス キーの列で null 値が入力した場合、エントリが無視され、エラーは発生しません。|  
  
## <a name="applies-to"></a>適用対象  
 [IndexNulls プロパティ (ADOX)](../../../ado/reference/adox-api/indexnulls-property-adox.md)
