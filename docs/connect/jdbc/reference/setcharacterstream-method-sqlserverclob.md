---
title: "setCharacterStream メソッド (SQLServerClob) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname: SQLServerClob.setCharacterStream
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: c02778f2-6681-4a84-a58b-2bcfac4233e4
caps.latest.revision: "9"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 0028cef27107027e99d3eaf5c5163ea20015209f
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="setcharacterstream-method-sqlserverclob"></a>setCharacterStream メソッド (SQLServerClob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Unicode 文字のストリームを CLOB の指定された位置から書き込むために使用するストリームを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.io.Writer setCharacterStream(long pos)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *pos*  
  
 CLOB オブジェクトへの書き込みを開始する位置です。  
  
## <a name="return-value"></a>戻り値  
 Unicode エンコード文字を書き込むことができるストリームです。  
  
## <a name="exceptions"></a>例外  
 java.sql.SQLException  
  
## <a name="remarks"></a>解説  
 この setCharacterStream メソッドは、setCharacterStream、java.sql.Clob インターフェイスのメソッドでによって指定されます。  
  
 CLOB の文字データは指定された開始位置からライターによって上書きされ、CLOB の初期データの長さをオーバーランすることができます。 開始位置に CLOB の長さ + 1 の値を指定すると、文字が追加されます。 開始位置に CLOB の長さ + 2 以上 (または 0 以下) の値を指定すると、位置エラーがスローされます。  
  
## <a name="see-also"></a>参照  
 [SQLServerClob のメソッド](../../../connect/jdbc/reference/sqlserverclob-methods.md)   
 [SQLServerClob のメンバー](../../../connect/jdbc/reference/sqlserverclob-members.md)   
 [SQLServerClob クラス](../../../connect/jdbc/reference/sqlserverclob-class.md)  
  
  
