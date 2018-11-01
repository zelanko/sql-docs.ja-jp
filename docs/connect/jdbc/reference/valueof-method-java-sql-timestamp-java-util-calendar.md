---
title: valueOf (java.sql.Timestamp, java.util.Calendar) メソッド | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 7320c383-0b06-446d-963b-7005e50324a2
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: fd94495081d99521758747f174268d2163cf67e7
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47742740"
---
# <a name="valueof-method-javasqltimestamp-javautilcalendar"></a>valueOf (java.sql.Timestamp, java.util.Calendar) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  引数に java.sql.Timestamp 値とオフセットを示す java.util.Calendar 値を受け取って、GMT からの特定のオフセットで特定の時点を表す **DateTimeOffset** オブジェクトを作成します。  
  
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
  
  
