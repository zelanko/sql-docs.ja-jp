---
title: "prepareStatement (java.lang.String) メソッド |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/07/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
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
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: c2452837aba5b8c5a146c12de838a3259f65be38
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

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

[prepareStatement メソッド & #40 です。SQLServerConnection &#41;](./preparestatement-method-sqlserverconnection.md)

[SQLServerConnection のメンバー](./sqlserverconnection-members.md)

[SQLServerConnection クラス](./sqlserverconnection-class.md)

