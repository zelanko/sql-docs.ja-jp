---
title: executeUpdate (java.lang.String) メソッド |Microsoft Docs
ms.custom: ''
ms.date: 02/07/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerPreparedStatement.executeUpdate (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 91ecb1cd-001d-4ac9-9ae8-5db05c3c2959
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d3a976f9e953729be7b9f993139a7603fe8444cc
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47804856"
---
# <a name="executeupdate-method-javalangstring"></a>executeUpdate (java.lang.String) メソッド

渡された SQL ステートメントを実行します。ステートメントは INSERT、UPDATE、MERGE、DELETE、または SQL DDL ステートメントのような何も返さない SQL ステートメントが可能です。

## <a name="syntax"></a>構文

```
public final int executeUpdate(java.lang.String sql)
```

#### <a name="parameters"></a>パラメーター
*sql*

**文字列**SQL ステートメントを格納しています。

## <a name="return-value"></a>戻り値
影響を受けた行数を示す **int** です。DDL ステートメントを使用している場合は 0 です。

## <a name="exceptions"></a>例外
[SQLServerException](./sqlserverexception-class.md)

## <a name="remarks"></a>Remarks
この executeUpdate メソッドは、java.sql.PreparedStatement インターフェイスの executeUpdate メソッドで規定されています。

SQLServerPreparedStatement オブジェクトが作成される際、オブジェクトの SQL ステートメントが指定されるため、このメソッドを呼び出すと例外が発生します。

## <a name="see-also"></a>参照

[executeUpdate メソッド &#40;SQLServerPreparedStatement&#41;](./executeupdate-method-sqlserverpreparedstatement.md)

[SQLServerPreparedStatement のメンバー](./sqlserverpreparedstatement-members.md)

[SQLServerPreparedStatement クラス](./sqlserverpreparedstatement-class.md)
