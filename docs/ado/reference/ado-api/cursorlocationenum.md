---
title: カーソル Locationenum |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- CursorLocationEnum
helpviewer_keywords:
- CursorLocationEnum enumeration [ADO]
ms.assetid: acb255ff-1734-4b70-89bb-aef862b4c63b
author: MightyPen
ms.author: genemi
ms.openlocfilehash: b3af18120af91fe06da48c2e3636bf8a7c572161
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "67919292"
---
# <a name="cursorlocationenum"></a>CursorLocationEnum
カーソルサービスの場所を指定します。  
  
|Constant|[値]|説明|  
|--------------|-----------|-----------------|  
|**adUseClient**|3|では、ローカルカーソルライブラリによって提供されるクライアント側カーソルが使用されます。 多くの場合、ローカルカーソルサービスでは、ドライバーによって提供されるカーソルが使用できない多くの機能を使用できます。そのため、この設定を使用すると、有効になる機能に対して利点が得られる可能性があります。 旧バージョンとの互換性のために、シノニム**adUseClientBatch**もサポートされています。|  
|**adUseNone**|1|カーソルサービスを使用しません。 (この定数は互換性のために残されており、旧バージョンとの互換性のためだけに残されています)。|  
|**adUseServer**|2|既定値。 データプロバイダーまたはドライバーによって提供されるカーソルを使用します。 これらのカーソルは、非常に柔軟性が高く、他のユーザーがデータソースに対して行う変更に対して、さらに機密性を高めることができます。 ただし、 [OLE DB 用の Microsoft Cursor Service](../../../ado/guide/data/the-microsoft-cursor-service-for-ole-db.md)の一部の機能 (関連付けの解除など)<br /><br /> [レコードセット](../../../ado/reference/ado-api/recordset-object-ado.md)オブジェクトは、サーバー側カーソルではシミュレートできません。これらの機能は、この設定では使用できません。|  
  
## <a name="adowfc-equivalent"></a>同等の ADO/WFC  
 パッケージ: **com. ms. wfc. データ**  
  
|Constant|  
|--------------|  
|AdoEnums を指定します。|  
|AdoEnums. NONE|  
|AdoEnums. サーバー|  
  
## <a name="applies-to"></a>適用対象  
 [CursorLocation プロパティ (ADO)](../../../ado/reference/ado-api/cursorlocation-property-ado.md)
