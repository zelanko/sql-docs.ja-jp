---
title: execute メソッド (java.lang.String, int[]) |Microsoft Docs
ms.custom: ''
ms.date: 02/07/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerStatement.execute (javal.lang.String.int[])
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: dc73d1c3-e756-43af-b1fc-ac438cbd0965
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: bf42996fac6ac5f48a41311aa072866ebd79f8b3
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47667480"
---
# <a name="execute-method-javalangstring-int"></a>execute (java.lang.String, int[]) メソッド

  複数の結果を返す可能性のある渡された SQL ステートメントを実行し、渡された配列に示される自動生成キーを検索可能にするように、[!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] に通知します。

## <a name="syntax"></a>構文

```Java
public final boolean execute(
    java.lang.String sql,
    int[] columnIndexes)
```

#### <a name="parameters"></a>パラメーター
*sql*

A**文字列**SQL ステートメントを格納しています。

*columnIndexes*

検索可能にする自動生成キーの列インデックスを示す **int** 配列です。

## <a name="return-value"></a>戻り値
最初の結果が結果セットの場合は **true** です。 それ以外の場合は、 **false**です。
  
## <a name="exceptions"></a>例外
[SQLServerException](./sqlserverexception-class.md)

## <a name="remarks"></a>Remarks
この execute メソッドは、java.sql.Statement インターフェイスの execute メソッドで規定されています。

## <a name="see-also"></a>参照

[execute メソッド&#40;SQLServerStatement&#41;](./execute-method-sqlserverstatement.md)

[SQLServerStatement のメンバー](./sqlserverstatement-members.md)

[SQLServerStatement クラス](./sqlserverstatement-class.md)
