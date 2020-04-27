---
title: AcceptStop プロパティ (SqlService クラス) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- AcceptStop Property (SqlService Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- AcceptStop property
ms.assetid: bf8ffe79-4f4c-4a2d-82e5-2ae8f5d466c5
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 38da38f867c6266d25f3b5d4c329a3e18a0e7292
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "63223335"
---
# <a name="acceptstop-property-sqlservice-class"></a>AcceptStop プロパティ (SqlService クラス)
  サービスを停止できるかどうかを指定するブール型のプロパティの値を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
object  
.AcceptStop [= value]  
```  
  
## <a name="parts"></a>要素  
 *object*  
 サービスを表す[Sqlservice クラス](sqlservice-class.md)オブジェクト  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 サービスを停止できるかどうかを指定するブール値。サービスを停止できる場合は `true`、サービスを停止できない場合は `false` です。  
  
## <a name="remarks"></a>Remarks  
  
## <a name="see-also"></a>参照  
 [サービスの開始および停止](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
