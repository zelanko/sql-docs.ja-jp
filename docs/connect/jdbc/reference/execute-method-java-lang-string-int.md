---
title: execute メソッド (java.lang.String, int[]) |Microsoft Docs
ms.custom: ''
ms.date: 02/07/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerStatement.execute (javal.lang.String.int[])
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: dc73d1c3-e756-43af-b1fc-ac438cbd0965
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 84d3b4d916b91c95efaff5ad9e995e6bad40a9ad
ms.sourcegitcommit: b70b99c2e412b4d697021f3bf1a92046aafcbe37
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 08/13/2018
ms.locfileid: "42785775"
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
