---
title: setClientInfo (java.lang.String, java.lang.String) メソッド | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 8d050831-8305-48a8-bd22-207932111040
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 177b92c12ba9daa410de1e65cc3a38b8744f4149
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2020
ms.locfileid: "80927170"
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
  
 設定するクライアント情報のプロパティの名前を含む String です。  
  
 *value*  
  
 クライアント情報のプロパティに設定する値を含む String です。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この setClientInfo メソッドは、javax.sql.Connection インターフェイスの setClientInfo メソッドによって指定されます。  
  
 [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] ではクライアント情報のプロパティをサポートしていません。 JDBC Driver 2.0 では、このメソッドはプロパティの警告を生成します。 アプリケーションは、[SQLServerConnection](../../../connect/jdbc/reference/getwarnings-method-sqlserverconnection.md) クラスの [getWarnings](../../../connect/jdbc/reference/sqlserverconnection-class.md) メソッドを使用して警告を取得する必要があります。  
  
## <a name="see-also"></a>参照  
 [setClientInfo メソッド &#40;SQLServerConnection&#41;](../../../connect/jdbc/reference/setclientinfo-method-sqlserverconnection.md)   
 [SQLServerConnection のメンバー](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection クラス](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
