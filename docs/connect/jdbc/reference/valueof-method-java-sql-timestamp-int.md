---
title: valueOf (java.sql.Timestamp, int) メソッド |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 114f55af-62ab-4c60-8724-0affbbbbbcdc
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: b3d2eb2934474b51aacddebc72230330c86bfeb0
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2019
ms.locfileid: "66797861"
---
# <a name="valueof-method-javasqltimestamp-int"></a>valueOf (java.sql.Timestamp, int) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  引数に java.sql.Timestamp 値とオフセット (分) を示す値を受け取って、GMT からの特定のオフセットで特定の時点を表す **DateTimeOffset** オブジェクトを作成します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public static DateTimeOffset valueOf(java.sql.Timestamp timestamp, int minutesOffset)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *timestamp*  
  
 java.sql.Timestamp値です。  
  
 *minutesOffset*  
  
 分単位のオフセットです。  
  
## <a name="return-value"></a>戻り値  
 指定された時間で指定されたオフセットの java.sql.Timestamp オブジェクト分、GMT からの時点を表す DateTimeOffset オブジェクトを返します。  
  
## <a name="see-also"></a>参照  
 [DateTimeOffset クラス](../../../connect/jdbc/reference/datetimeoffset-class.md)   
 [DateTimeOffset のメンバー](../../../connect/jdbc/reference/datetimeoffset-members.md)  
  
  
