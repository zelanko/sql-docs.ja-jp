---
title: Create メソッド (ADOX) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Catalog::raw_Create
- _Catalog::Create
helpviewer_keywords:
- Create method [ADOX]
ms.assetid: 64f5c21c-b581-42d8-bdc7-c4f1bebaf105
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: bbdd7f6b663fb1c6c2ee12b7a6e4c843eb16d42d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "66703355"
---
# <a name="create-method-adox"></a>Create メソッド (ADOX)
新しいカタログを作成します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Catalog.Create ConnectString  
```  
  
#### <a name="parameters"></a>パラメーター  
 *ConnectString*  
 A**文字列**値のデータ ソースに接続するために使用します。  
  
## <a name="remarks"></a>コメント  
 **作成**メソッドを作成し、新しい ADO が開きます[接続](../../../ado/reference/ado-api/connection-object-ado.md)で指定されたデータ ソースに*ConnectString*します。 成功した場合、新しい**接続**に割り当てられているオブジェクト、 [ActiveConnection](../../../ado/reference/adox-api/activeconnection-property-adox.md)プロパティ。  
  
 プロバイダーは、新しいカタログの作成をサポートしていない場合、エラーが発生します。  
  
## <a name="applies-to"></a>適用対象  
 [Catalog オブジェクト (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md)  
  
## <a name="see-also"></a>参照  
 [Create メソッドの例 (VB)](../../../ado/reference/adox-api/create-method-example-vb.md)   
 [ActiveConnection プロパティ (ADOX)](../../../ado/reference/adox-api/activeconnection-property-adox.md)
