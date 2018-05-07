---
title: setString メソッド (SQLServerCallableStatement) |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerCallableStatement.setString
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: f38b97b5-d4f0-4f74-a33d-740241a85842
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1a2fa007aa6edfc764534f745029ae6107edd6d6
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="setstring-method-sqlservercallablestatement"></a>setString メソッド (SQLServerCallableStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  指定されたパラメーターを指定し、Java に設定**文字列**値。  
  
## <a name="syntax"></a>構文  
  
```  
  
public void setString(java.lang.String sCol,  
                      java.lang.String s)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *sCol*  
  
 A**文字列**パラメーターの名前を格納しています。  
  
 *S*  
  
 A**文字列**値。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この setString メソッドは、java.sql.CallableStatement インターフェイスの setString メソッドによって指定されます。  
  
 文字列バイナリへの変換からが実行される場合にのみ[!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]変換先の型がバイナリことを認識します。 ここで、JDBC ドライバーには基になる型はわからない場合に合格、**文字列**リテラルし、サーバーは、変換を実行できない場合、サーバー エラーを返します。  
  
## <a name="see-also"></a>参照  
 [SQLServerCallableStatement のメンバー](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [SQLServerCallableStatement クラス](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
