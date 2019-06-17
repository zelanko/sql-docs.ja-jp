---
title: setObject (int, java.lang.Object) メソッド | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerPreparedStatement.setObject (int, java.lang.Object)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 61f19faa-3006-4a1c-974c-55951e3b3000
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: aaf2b256329c66b6169593f71f4e85439aff21ab
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2019
ms.locfileid: "66788263"
---
# <a name="setobject-method-int-javalangobject"></a>setObject (int, java.lang.Object) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  渡されたオブジェクトを使用して、指定されたパラメーターの値を設定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public final void setObject(int index,  
                            java.lang.Object obj)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *index*  
  
 パラメーターの番号を示す **int** です。  
  
 *obj*  
  
 オブジェクト。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 この setObject メソッドは、java.sql.PreparedStatement インターフェイスの setObject メソッドで指定されています。  
  
 この setObject メソッドを呼び出す前に、指定したパラメーターが次のいずれかのメソッドを使用してアプリケーションで設定されている場合があります。  
  
-   SQLServerPreparedStatement クラスまたは SQLServerCallableStatement クラスの set\<Type> メソッド  
  
-   SQLServerPreparedStatement クラスまたは SQLServerCallableStatement クラスの setNull メソッド  
  
-   [RegisterOutParameter](../../../connect/jdbc/reference/registeroutparameter-method-sqlservercallablestatement.md) SQLServerCallableStatement クラスのメソッド  
  
 このような場合、パラメーターの型が自動的に設定されます。 アプリケーションで obj 値を NULL に設定してこの setObject メソッドを呼び出すと、ドライバーでは、パラメーターの型は以前に呼び出されたメソッドで設定された型であると見なされます。  
  
 obj 値が NULL で、そのパラメーターの型情報を特定できない場合、この setObject メソッドは、指定したパラメーターを CHAR に変換してからデータベースに送信します。  
  
 以降で[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]JDBC Driver 3.0 では、このメソッドの動作は変更、**で sendTimeAsDatetime**接続プロパティ ([接続プロパティの設定](../../../connect/jdbc/setting-the-connection-properties.md)) と[SQLServerDataSource.setSendTimeAsDatetime](../../../connect/jdbc/reference/setsendtimeasdatetime-method-sqlserverdatasource.md)します。  
  
 詳細については、次を参照してください。[を構成する方法の java.sql.Time 値は、サーバーに送信される](../../../connect/jdbc/configuring-how-java-sql-time-values-are-sent-to-the-server.md)します。  
  
## <a name="see-also"></a>参照  
 [setObject メソッド &#40;SQLServerPreparedStatement&#41;](../../../connect/jdbc/reference/setobject-method-sqlserverpreparedstatement.md)   
 [SQLServerPreparedStatement のメンバー](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)   
 [SQLServerPreparedStatement クラス](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
  
