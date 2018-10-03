---
title: getStatementPoolingCacheSize メソッド (SQLServerConnection) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnection.getStatementPoolingCacheSize
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ''
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 911137407c75d82164bf1ddd96eae91f618bb00b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47841530"
---
# <a name="getstatementpoolingcachesize-method-sqlserverconnection"></a>getStatementPoolingCacheSize メソッド (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

 この接続の準備されたステートメント キャッシュのサイズを返します。 '0' では、キャッシュを有効にしないことを意味します。

## <a name="syntax"></a>構文  
  
```  
  
public int getStatementPoolingCacheSize()  
```  

## <a name="return-value"></a>戻り値
 **Int**の値を格納している**statementPoolingCacheSize**接続プロパティです。

## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
 
## <a name="remarks"></a>Remarks  
 このメソッドは、JDBC driver 6.4 から利用できるとは。
 
## <a name="see-also"></a>参照  
 [SQLServerConnection のメンバー](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection クラス](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
