---
description: XactAttributeEnum
title: XactAttributeEnum |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- XactAttributeEnum
helpviewer_keywords:
- XactAttributeEnum enumeration [ADO]
ms.assetid: e7dcecd3-7dc7-445c-b922-f700c3067fbc
author: rothja
ms.author: jroth
ms.openlocfilehash: 1c7ea7ccbf1a588458db9e213bfa57837e89898f
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/24/2020
ms.locfileid: "88776821"
---
# <a name="xactattributeenum"></a>XactAttributeEnum
[接続](./connection-object-ado.md)オブジェクトのトランザクション属性を指定します。  
  
|定数|値|説明|  
|--------------|-----------|-----------------|  
|**adXactAbortRetaining**|262144|[RollbackTrans](./begintrans-committrans-and-rollbacktrans-methods-ado.md)を呼び出して新しいトランザクションを自動的に開始することによって、中断を保持します。 すべてのプロバイダーがこの動作をサポートするわけではありません。|  
|**adXactCommitRetaining**|131072|[CommitTrans](./begintrans-committrans-and-rollbacktrans-methods-ado.md)を呼び出して、新しいトランザクションを自動的に開始することによって、コミットの保持を実行します。 すべてのプロバイダーがこの動作をサポートするわけではありません。|  
  
## <a name="adowfc-equivalent"></a>同等の ADO/WFC  
 パッケージ: **com. ms. wfc. データ**  
  
|定数|  
|--------------|  
|AdoEnums.XactAttribute.ABORTRETAINING|  
|AdoEnums.XactAttribute.COMMITRETAINING|  
  
## <a name="applies-to"></a>適用対象  
 [Attributes プロパティ (ADO)](./attributes-property-ado.md)