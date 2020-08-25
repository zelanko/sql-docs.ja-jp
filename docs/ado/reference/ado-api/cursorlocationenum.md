---
description: CursorLocationEnum
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 950d6310bff0bf27affe70899ba63914c9ae0ec4
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/24/2020
ms.locfileid: "88775531"
---
# <a name="cursorlocationenum"></a>CursorLocationEnum
カーソルサービスの場所を指定します。  
  
|定数|値|説明|  
|--------------|-----------|-----------------|  
|**adUseClient**|3|では、ローカルカーソルライブラリによって提供されるクライアント側カーソルが使用されます。 多くの場合、ローカルカーソルサービスでは、ドライバーによって提供されるカーソルが使用できない多くの機能を使用できます。そのため、この設定を使用すると、有効になる機能に対して利点が得られる可能性があります。 旧バージョンとの互換性のために、シノニム **adUseClientBatch** もサポートされています。|  
|**adUseNone**|1|カーソルサービスを使用しません。 (この定数は互換性のために残されており、旧バージョンとの互換性のためだけに残されています)。|  
|**adUseServer**|2|既定値。 データプロバイダーまたはドライバーによって提供されるカーソルを使用します。 これらのカーソルは、非常に柔軟性が高く、他のユーザーがデータソースに対して行う変更に対して、さらに機密性を高めることができます。 ただし、 [OLE DB 用の Microsoft Cursor Service](../../guide/data/the-microsoft-cursor-service-for-ole-db.md)の一部の機能 (関連付けの解除など)<br /><br /> [レコードセット](./recordset-object-ado.md) オブジェクトは、サーバー側カーソルではシミュレートできません。これらの機能は、この設定では使用できません。|  
  
## <a name="adowfc-equivalent"></a>同等の ADO/WFC  
 パッケージ: **com. ms. wfc. データ**  
  
|定数|  
|--------------|  
|AdoEnums を指定します。|  
|AdoEnums. NONE|  
|AdoEnums. サーバー|  
  
## <a name="applies-to"></a>適用対象  
 [CursorLocation プロパティ (ADO)](./cursorlocation-property-ado.md)