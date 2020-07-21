---
title: setObject メソッド (java.lang.String, java.lang.Object, int) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerCallableStatement.setObject (java.lang.String, java.lang.Object, int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: a9a0c802-7851-4826-b173-87b0c0acb3a0
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 53249febaa464f19fb9cf392f9e7d250e4249f8a
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2020
ms.locfileid: "80920817"
---
# <a name="setobject-method-javalangstring-javalangobject-int"></a>setObject (java.lang.String, java.lang.Object, int) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  渡されたオブジェクトと変換先の型を使用して、指定されたパラメーターの値が設定されます。  
  
## <a name="syntax"></a>構文  
  
```  
  
public void setObject(java.lang.String sCol,  
                      java.lang.Object o,  
                      int n)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *sCol*  
  
 パラメーターの名前を含む**文字列**です。  
  
 *o*  
  
 **Object** 値。  
  
 *n*  
  
 java.sql.Types での定義に従って変換先の型を示す **int** です。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この setObject メソッドは、java.sql.CallableStatement インターフェイスの setObject メソッドで指定されています。  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] JDBC Driver 3.0 以降、このメソッドの動作は **sendTimeAsDatetime** 接続プロパティ (「[接続プロパティの設定](../../../connect/jdbc/setting-the-connection-properties.md)」を参照) および [SQLServerDataSource.setSendTimeAsDatetime](../../../connect/jdbc/reference/setsendtimeasdatetime-method-sqlserverdatasource.md) によって変更されます。  
  
 詳細については、「[java.sql.Time の値をサーバーに送信する方法の構成](../../../connect/jdbc/configuring-how-java-sql-time-values-are-sent-to-the-server.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [setObject メソッド &#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/setobject-method-sqlservercallablestatement.md)   
 [SQLServerCallableStatement のメンバー](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [SQLServerCallableStatement クラス](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
