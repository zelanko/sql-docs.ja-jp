---
title: executeUpdate (java.lang.String) メソッド |Microsoft ドキュメント
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
- SQLServerPreparedStatement.executeUpdate (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 91ecb1cd-001d-4ac9-9ae8-5db05c3c2959
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: aa8aef31d1df6798bc209fb1dbb95ef8c58cb3ce
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="executeupdate-method-javalangstring"></a>executeUpdate (java.lang.String) メソッド

渡された SQL ステートメントを実行します。ステートメントは INSERT、UPDATE、MERGE、DELETE、または SQL DDL ステートメントのような何も返さない SQL ステートメントが可能です。

## <a name="syntax"></a>構文

```
public final int executeUpdate(java.lang.String sql)
```

#### <a name="parameters"></a>パラメーター
*sql*

A**文字列**SQL ステートメントを含むです。

## <a name="return-value"></a>戻り値
**Int** DDL ステートメントを使用する場合、影響を受ける行または 0 の数を示すです。

## <a name="exceptions"></a>例外
[SQLServerException](./sqlserverexception-class.md)

## <a name="remarks"></a>解説
この executeUpdate メソッドは、java.sql.PreparedStatement インターフェイスの executeUpdate メソッドによって指定されます。

オブジェクトが作成されるとき、SQLServerPreparedStatement オブジェクトの SQL ステートメントが指定されてためこのメソッドを呼び出すが、例外が発生します。

## <a name="see-also"></a>参照

[executeUpdate メソッド&#40;SQLServerPreparedStatement&#41;](./executeupdate-method-sqlserverpreparedstatement.md)

[SQLServerPreparedStatement のメンバー](./sqlserverpreparedstatement-members.md)

[SQLServerPreparedStatement クラス](./sqlserverpreparedstatement-class.md)
