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
author: rothja
ms.author: jroth
ms.openlocfilehash: 15ea5cf8b565a943f4905a890cb08ba0afed202f
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2020
ms.locfileid: "82759268"
---
# <a name="create-method-adox"></a>Create メソッド (ADOX)
新しいカタログを作成します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Catalog.Create ConnectString  
```  
  
#### <a name="parameters"></a>パラメーター  
 *ConnectString*  
 データソースへの接続に使用する**文字列**値。  
  
## <a name="remarks"></a>解説  
 **Create**メソッドは、 *connectstring*に指定されたデータソースへの新しい ADO[接続](../../../ado/reference/ado-api/connection-object-ado.md)を作成して開きます。 成功した場合は、新しい**接続**オブジェクトが[ActiveConnection](../../../ado/reference/adox-api/activeconnection-property-adox.md)プロパティに割り当てられます。  
  
 プロバイダーが新しいカタログの作成をサポートしていない場合は、エラーが発生します。  
  
## <a name="applies-to"></a>適用対象  
 [Catalog オブジェクト (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md)  
  
## <a name="see-also"></a>参照  
 [Create メソッドの例 (VB)](../../../ado/reference/adox-api/create-method-example-vb.md)   
 [ActiveConnection プロパティ (ADOX)](../../../ado/reference/adox-api/activeconnection-property-adox.md)
