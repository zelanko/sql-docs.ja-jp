---
title: valueOf (java.sql.Timestamp, java.util.Calendar) メソッド | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 7320c383-0b06-446d-963b-7005e50324a2
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c2b742e3ccdf297aaa6ede4feb5bb93b04224823
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "38039240"
---
# <a name="valueof-method-javasqltimestamp-javautilcalendar"></a>valueOf (java.sql.Timestamp, java.util.Calendar) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  作成、 **DateTimeOffset** GMT java.sql.Timestamp 値とオフセットを示す java.util.Calendar 値から特定のオフセットで特定の時点を表すオブジェクト。  
  
## <a name="syntax"></a>構文  
  
```  
  
public static DateTimeOffset valueOf(java.sql.Timestamp timestamp, java.util.Calendar calendar)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *timestamp*  
  
 java.sql.Timestamp値です。  
  
 *カレンダー*  
  
 オフセットの値。  日付と時刻のコンポーネント*カレンダー*に従って設定は、*タイムスタンプ*値。  
  
## <a name="return-value"></a>戻り値  
 特定 java.util.Calendar オブジェクトのタイム ゾーンでの java.sql.Timestamp オブジェクトで指定された特定の時点を表す DateTimeOffset オブジェクトを返します。  
  
## <a name="remarks"></a>Remarks  
 このメソッドは、java.sql.Timestamp オブジェクトによって指定された特定の java.util.Calendar オブジェクトをポイントも設定します。  
  
## <a name="see-also"></a>参照  
 [DateTimeOffset クラス](../../../connect/jdbc/reference/datetimeoffset-class.md)   
 [DateTimeOffset のメンバー](../../../connect/jdbc/reference/datetimeoffset-members.md)  
  
  
