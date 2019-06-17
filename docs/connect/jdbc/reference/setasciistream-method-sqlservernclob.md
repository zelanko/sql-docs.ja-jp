---
title: setAsciiStream メソッド (SQLServerNClob) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 617ece92-0fb1-4f95-b32d-29b5b56eb3fb
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: aebc713ab5256527571eb1a4277caa74e53623d7
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2019
ms.locfileid: "66765048"
---
# <a name="setasciistream-method-sqlservernclob"></a>setAsciiStream メソッド (SQLServerNClob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  この **java.sql.NClob** オブジェクトが表す **NCLOB** 値の指定された位置から ASCII 文字を書き込むために使用するストリームを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.io.OutputStream setAsciiStream(long pos)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *pos*  
  
 **NCLOB** オブジェクトへの書き込みを開始する位置です。最初の位置は 1 です。  
  
## <a name="return-value"></a>戻り値  
 ASCII エンコード文字を書き込むことができるストリームを表す OutputStream オブジェクトです。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 この setAsciiStream メソッドは、java.sql.NClob インターフェイスの setAsciiStream メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerNClob のメソッド](../../../connect/jdbc/reference/sqlservernclob-methods.md)   
 [SQLServerNClob のメンバー](../../../connect/jdbc/reference/sqlservernclob-members.md)   
 [SQLServerNClob クラス](../../../connect/jdbc/reference/sqlservernclob-class.md)  
  
  
