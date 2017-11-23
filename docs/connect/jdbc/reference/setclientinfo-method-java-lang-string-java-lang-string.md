---
title: "setClientInfo (java.lang.String, java.lang.String) メソッド |Microsoft ドキュメント"
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
ms.assetid: 8d050831-8305-48a8-bd22-207932111040
caps.latest.revision: "19"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e136cd3eb2330bfd82c531acaa37838ed30e7713
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="setclientinfo-method-javalangstring-javalangstring"></a>setClientInfo (java.lang.String, java.lang.String) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  指定されたクライアント情報のプロパティの値を設定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public void setClientInfo (java.lang.String name,  
                           java.lang.String value)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *name*  
  
 設定するクライアント情報のプロパティの名前を表す文字列。  
  
 *value*  
  
 クライアント情報のプロパティを設定する値を含む文字列です。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この setClientInfo メソッドは、java.sql.Connection インターフェイスの setClientInfo メソッドによって指定されます。  
  
 [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]クライアント情報のプロパティをサポートしていません。 JDBC Driver 2.0 では、このメソッドはプロパティの警告を生成します。 アプリケーションを使用する必要があります[getWarnings](../../../connect/jdbc/reference/getwarnings-method-sqlserverconnection.md)のメソッド、 [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)警告を取得するクラス。  
  
## <a name="see-also"></a>参照  
 [setClientInfo メソッド &#40;です。SQLServerConnection &#41;](../../../connect/jdbc/reference/setclientinfo-method-sqlserverconnection.md)   
 [SQLServerConnection のメンバー](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection クラス](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
