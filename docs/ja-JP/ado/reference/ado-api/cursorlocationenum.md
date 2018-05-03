---
title: CursorLocationEnum |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- CursorLocationEnum
helpviewer_keywords:
- CursorLocationEnum enumeration [ADO]
ms.assetid: acb255ff-1734-4b70-89bb-aef862b4c63b
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 60dd24d57cf3897c08daeb4d666c35ed66a6dc88
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="cursorlocationenum"></a>CursorLocationEnum
カーソル サービスの場所を指定します。  
  
|定数|値|Description|  
|--------------|-----------|-----------------|  
|**adUseClient**|3|ローカル カーソル ライブラリによって提供されたクライアント側カーソルを使用します。 ローカル カーソル サービス多くの場合は、ドライバーによって提供されるカーソルよりも多くの機能に関して機能が有効になります利用可能性がありますを提示この設定を使用できます。 旧バージョンと互換性のため、シノニム**adUseClientBatch**もサポートされています。|  
|**adUseNone**|1|カーソルのサービスを使用しません。 (この定数は古い形式と下位互換性のためにのみ表示されます)。|  
|**adUseServer**|2|既定値です。 データ プロバイダーまたはドライバーによって提供されたカーソルを使用します。 これらのカーソルでは、非常に柔軟なは場合もありますし、データ ソースに、他のユーザーの変更を検出できるようにします。 ただし、一部の機能、 [for OLE DB、Microsoft カーソル Service](../../../ado/guide/data/the-microsoft-cursor-service-for-ole-db.md)の関連付けを解除など、<br /><br /> [レコード セット](../../../ado/reference/ado-api/recordset-object-ado.md)サーバー側カーソルをシミュレートできませんオブジェクト、およびこれらの機能はこの設定では使用できません。|  
  
## <a name="adowfc-equivalent"></a>該当するショートカットは ADO/WFC  
 パッケージ: **com.ms.wfc.data**  
  
|定数|  
|--------------|  
|AdoEnums.CursorLocation.CLIENT|  
|AdoEnums.CursorLocation.NONE|  
|AdoEnums.CursorLocation.SERVER|  
  
## <a name="applies-to"></a>適用対象  
 [CursorLocation プロパティ (ADO)](../../../ado/reference/ado-api/cursorlocation-property-ado.md)
