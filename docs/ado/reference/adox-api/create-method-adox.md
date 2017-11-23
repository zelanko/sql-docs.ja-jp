---
title: "Create メソッド (ADOX) |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology: drivers
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
helpviewer_keywords: Create method [ADOX]
ms.assetid: 64f5c21c-b581-42d8-bdc7-c4f1bebaf105
caps.latest.revision: "12"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 8b31df006624acdfd66a55c467be5a59dfc6afd1
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
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
 [Catalog オブジェクト (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md)  
  
## <a name="see-also"></a>参照  
 [メソッドの例 (VB) を作成します。](../../../ado/reference/adox-api/create-method-example-vb.md)   
 [ActiveConnection プロパティ (ADOX)](../../../ado/reference/adox-api/activeconnection-property-adox.md)
