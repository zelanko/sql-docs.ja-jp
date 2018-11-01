---
title: prepareStatement (java.lang.String) メソッド |Microsoft Docs
ms.custom: ''
ms.date: 02/07/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnection.prepareStatement (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: e825765c-eb55-4800-951b-f3495da36641
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: dbe43cf2af208d6547a1dc3dcd83d7d37947308e
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47788170"
---
# <a name="preparestatement-method-javalangstring"></a>prepareStatement (java.lang.String) メソッド

パラメーター化された SQL ステートメントをデータベースに送信するための [SQLServerPreparedStatement](./sqlserverpreparedstatement-class.md) オブジェクトを作成します。

## <a name="syntax"></a>構文

```
public java.sql.PreparedStatement prepareStatement(java.lang.String sql)
```

#### <a name="parameters"></a>パラメーター
*sql*

SQL ステートメントを含む**文字列**です。

## <a name="return-value"></a>戻り値
PreparedStatement オブジェクト。

## <a name="exceptions"></a>例外  
[SQLServerException](./sqlserverexception-class.md)

## <a name="remarks"></a>Remarks
この prepareStatement メソッドは、java.sql.Connection インターフェイスの prepareStatement メソッドによって指定されます。

## <a name="see-also"></a>参照

[prepareStatement メソッド &#40;SQLServerConnection&#41;](./preparestatement-method-sqlserverconnection.md)

[SQLServerConnection のメンバー](./sqlserverconnection-members.md)

[SQLServerConnection クラス](./sqlserverconnection-class.md)
