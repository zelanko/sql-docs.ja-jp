---
title: "SeekEnum |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords: SeekEnum
helpviewer_keywords: SeekEnum enumeration [ADO]
ms.assetid: f0ec0c92-8253-47c6-9a14-e5dbccbad219
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e6f60ed06b2f23bceec62822f43b77f5c10c3ce1
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="seekenum"></a>SeekEnum
型を指定[シーク](../../../ado/reference/ado-api/seek-method.md)を実行します。  
  
|定数|値|Description|  
|--------------|-----------|-----------------|  
|**adSeekFirstEQ**|@shouldalert|最初のキーと等しいをシーク*keyvalues とも*します。|  
|**adSeekLastEQ**|2|最後のキーと等しいをシーク*keyvalues とも*します。|  
|**adSeekAfterEQ**|4|等しいか、キーをシーク*keyvalues とも*または直後に一致するが発生したとします。|  
|**adSeekAfter**|8|Where の直後に、キーをシークとの一致*keyvalues とも*発生します。|  
|**adSeekBeforeEQ**|16|等しいか、キーをシーク*keyvalues とも*かその直前までと一致するが発生したとします。|  
|**adSeekBefore**|32|場所と一致するキーの直前にシーク*keyvalues とも*発生します。|  
  
## <a name="adowfc-equivalent"></a>該当するショートカットは ADO/WFC  
 パッケージ: **com.ms.wfc.data**  
  
|定数|  
|--------------|  
|AdoEnums.Seek.FIRSTEQ|  
|AdoEnums.Seek.LASTEQ|  
|AdoEnums.Seek.AFTEREQ|  
|AdoEnums.Seek.AFTER|  
|AdoEnums.Seek.BEFOREEQ|  
|AdoEnums.Seek.BEFORE|  
  
## <a name="applies-to"></a>適用対象  
 [Seek メソッド](../../../ado/reference/ado-api/seek-method.md)
