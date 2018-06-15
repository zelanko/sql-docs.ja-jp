---
title: EditModeEnum |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- EditModeEnum
helpviewer_keywords:
- EditModeEnum enumeration [ADO]
ms.assetid: 45d54b6e-db2c-4553-9fd0-528147d6da2f
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a98b8dd5b82665aa7416bba67c8a04e46a75babb
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2018
ms.locfileid: "35277981"
---
# <a name="editmodeenum"></a>EditModeEnum
レコードの編集状態を指定します。  
  
|定数|値|説明|  
|--------------|-----------|-----------------|  
|**adEditNone**|0|進行中の編集操作がないことを示します。|  
|**adEditInProgress**|1|現在のレコード内のデータが変更されたが保存されませんを示します。|  
|**adEditAdd**|2|示します、 [AddNew](../../../ado/reference/ado-api/addnew-method-ado.md)メソッドが呼び出されて、れ、コピー バッファーの現在のレコードが新しいレコードがデータベースに保存されていないでします。|  
|**adEditDelete**|4|現在のレコードが削除されたことを示します。|  
  
## <a name="adowfc-equivalent"></a>該当するショートカットは ADO/WFC  
 パッケージ: **com.ms.wfc.data**  
  
|定数|  
|--------------|  
|AdoEnums.EditMode.NONE|  
|AdoEnums.EditMode.INPROGRESS|  
|AdoEnums.EditMode.ADD|  
|AdoEnums.EditMode.DELETE|  
  
## <a name="applies-to"></a>適用対象  
 [EditMode プロパティ](../../../ado/reference/ado-api/editmode-property.md)
