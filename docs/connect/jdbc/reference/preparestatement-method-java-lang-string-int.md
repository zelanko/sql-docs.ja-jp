---
title: prepareStatement (java.lang.String) メソッド |Microsoft ドキュメント
ms.custom: ''
ms.date: 02/07/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
apiname:
- SQLServerConnection.prepareStatement (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: e825765c-eb55-4800-951b-f3495da36641
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 26f242db545a79e27ba72808e6c6ce466dbe5f40
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="preparestatement-method-javalangstring"></a>prepareStatement (java.lang.String) メソッド

作成、 [SQLServerPreparedStatement](./sqlserverpreparedstatement-class.md)化されたデータベースに SQL ステートメントを送信するためのオブジェクト。

## <a name="syntax"></a>構文

```
public java.sql.PreparedStatement prepareStatement(java.lang.String sql)
```

#### <a name="parameters"></a>パラメーター
*sql*

A**文字列**SQL ステートメントを含むです。

## <a name="return-value"></a>戻り値
PreparedStatement オブジェクトです。

## <a name="exceptions"></a>例外  
[SQLServerException](./sqlserverexception-class.md)

## <a name="remarks"></a>解説
この prepareStatement メソッドは、java.sql.Connection インターフェイスの prepareStatement メソッドによって指定されます。

## <a name="see-also"></a>参照

[prepareStatement メソッド&#40;SQLServerConnection&#41;](./preparestatement-method-sqlserverconnection.md)

[SQLServerConnection のメンバー](./sqlserverconnection-members.md)

[SQLServerConnection クラス](./sqlserverconnection-class.md)
