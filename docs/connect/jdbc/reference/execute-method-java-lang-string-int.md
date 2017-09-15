---
title: "execute メソッド (java.lang.String, int[]) |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/07/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLServerStatement.execute (javal.lang.String.int[])
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: dc73d1c3-e756-43af-b1fc-ac438cbd0965
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 50cb9686b883ac0a4d682e7ea28f1dba40257c7e
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="execute-method-javalangstring-int"></a>execute (java.lang.String, int[]) メソッド

  指定された SQL ステートメントを実行、複数の結果、および信号を返す可能性のある[!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion-md.md)]渡された配列に示される自動生成キーを検索可能にする必要があることです。

## <a name="syntax"></a>構文

```Java
public final boolean execute(
    java.lang.String sql,
    int[] columnIndexes)
```

#### <a name="parameters"></a>パラメーター
*sql*

A**文字列**SQL ステートメントを含むです。

*columnIndexes*

配列**int**を可能にするか、自動生成キーの列インデックスを示すです。

## <a name="return-value"></a>戻り値
**true**最初の結果が結果セットである場合。 それ以外の場合は、 **false**です。
  
## <a name="exceptions"></a>例外
[SQLServerException](./sqlserverexception-class.md)

## <a name="remarks"></a>解説
この execute メソッドは、java.sql.Statement インターフェイスの execute メソッドによって指定されます。

## <a name="see-also"></a>参照

[方法 &#40; を実行します。SQLServerStatement &#41;](./execute-method-sqlserverstatement.md)

[SQLServerStatement のメンバー](./sqlserverstatement-members.md)

[SQLServerStatement クラス](./sqlserverstatement-class.md)

