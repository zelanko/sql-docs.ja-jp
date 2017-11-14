---
title: "Create メソッド (ADOX) |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- _Catalog::raw_Create
- _Catalog::Create
helpviewer_keywords:
- Create method [ADOX]
ms.assetid: 64f5c21c-b581-42d8-bdc7-c4f1bebaf105
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 0bfad8159575c9439846ed2cf407e1b6e407418c
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

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
  
## <a name="remarks"></a>解説  
 **作成**メソッドを作成し、新しい ADO が開きます[接続](../../../ado/reference/ado-api/connection-object-ado.md)で指定されたデータ ソースに*ConnectString*です。 成功した場合、新しい**接続**にオブジェクトが割り当てられた、 [ActiveConnection](../../../ado/reference/adox-api/activeconnection-property-adox.md)プロパティです。  
  
 プロバイダーは、新しいカタログの作成をサポートしていない場合は、エラーが発生します。  
  
## <a name="applies-to"></a>適用対象  
 [カタログ オブジェクト (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md)  
  
## <a name="see-also"></a>参照  
 [メソッドの例 (VB) を作成します。](../../../ado/reference/adox-api/create-method-example-vb.md)   
 [ActiveConnection プロパティ (ADOX)](../../../ado/reference/adox-api/activeconnection-property-adox.md)

