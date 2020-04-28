---
title: Append メソッド (ADOX Indexes) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Indexes::Append
helpviewer_keywords:
- Append method [ADOX]
ms.assetid: 6695769f-275b-4b70-81bd-1a5f7d74926c
author: MightyPen
ms.author: genemi
ms.openlocfilehash: ef30faf0fef05c4e86ffb4d2c21781592094c198
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "67967304"
---
# <a name="append-method-adox-indexes"></a>Append メソッド (ADOX Indexes)
新しい[Index](../../../ado/reference/adox-api/index-object-adox.md)オブジェクトを[Indexes](../../../ado/reference/adox-api/indexes-collection-adox.md)コレクションに追加します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Indexes.Append Index [,Columns]  
```  
  
#### <a name="parameters"></a>パラメーター  
 *化*  
 追加する**インデックス**オブジェクト、または作成および追加するインデックスの名前。  
  
 *[列]*  
 任意。 インデックスを作成する列の名前を指定する**バリアント**値です (複数可)。 *Columns*パラメーターは、[列](../../../ado/reference/adox-api/column-object-adox.md)オブジェクトまたはオブジェクトの[Name](../../../ado/reference/adox-api/name-property-adox.md)プロパティの値に対応します。  
  
## <a name="remarks"></a>Remarks  
 *Columns*パラメーターには、列名または列名の配列のいずれかを指定できます。  
  
 プロバイダーがインデックスの作成をサポートしていない場合、エラーが発生します。  
  
## <a name="applies-to"></a>適用対象  
 [Indexes コレクション (ADOX)](../../../ado/reference/adox-api/indexes-collection-adox.md)  
  
## <a name="see-also"></a>参照  
 [Indexes Append メソッドの例 (VB)](../../../ado/reference/adox-api/indexes-append-method-example-vb.md)   
 [Append メソッド (ADOX Columns)](../../../ado/reference/adox-api/append-method-adox-columns.md)   
 [Append メソッド (ADOX Groups)](../../../ado/reference/adox-api/append-method-adox-groups.md)   
 [Append メソッド (ADOX Keys)](../../../ado/reference/adox-api/append-method-adox-keys.md)   
 [Append メソッド (ADOX Procedures)](../../../ado/reference/adox-api/append-method-adox-procedures.md)   
 [Append メソッド (ADOX Tables)](../../../ado/reference/adox-api/append-method-adox-tables.md)   
 [Append メソッド (ADOX Users)](../../../ado/reference/adox-api/append-method-adox-users.md)   
 [Append メソッド (ADOX Views)](../../../ado/reference/adox-api/append-method-adox-views.md)
