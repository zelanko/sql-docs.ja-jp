---
title: EditModeEnum |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- EditModeEnum
helpviewer_keywords:
- EditModeEnum enumeration [ADO]
ms.assetid: 45d54b6e-db2c-4553-9fd0-528147d6da2f
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 0a8c4ddb27bbc6831095062af5491fb501b6d5b7
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "67933044"
---
# <a name="editmodeenum"></a>EditModeEnum
レコードの編集状態を指定します。  
  
|Constant|値|説明|  
|--------------|-----------|-----------------|  
|**adEditNone**|0|編集操作が実行中でないことを示します。|  
|**adEditInProgress**|1|現在のレコードのデータが変更されていても保存されていないことを示します。|  
|**adEditAdd**|2|[AddNew](../../../ado/reference/ado-api/addnew-method-ado.md)メソッドが呼び出され、コピーバッファー内の現在のレコードが、データベースに保存されていない新しいレコードであることを示します。|  
|**adEditDelete**|4|現在のレコードが削除されたことを示します。|  
  
## <a name="adowfc-equivalent"></a>同等の ADO/WFC  
 パッケージ: **com. ms. wfc. データ**  
  
|Constant|  
|--------------|  
|AdoEnums|  
|AdoEnums|  
|AdoEnums|  
|AdoEnums|  
  
## <a name="applies-to"></a>適用対象  
 [EditMode プロパティ](../../../ado/reference/ado-api/editmode-property.md)
