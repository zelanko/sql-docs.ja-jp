---
title: "getSendTimeAsDatetime メソッド (SQLServerDataSource) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 02287122-5dc1-455d-987f-95fd9a69d503
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 625d1e864cd0f913dbf8826372017ee99a80e41d
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="getsendtimeasdatetime-method-sqlserverdatasource"></a>getSendTimeAsDatetime メソッド (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  このメソッドで追加された[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]JDBC Driver 3.0 です。  
  
 設定値を返します、 **sendTimeAsDatetime**接続プロパティです。  
  
## <a name="syntax"></a>構文  
  
```  
  
public boolean getSendTimeAsDatetime();  
```  
  
## <a name="return-value"></a>戻り値  
 **true** java.sql.Time 値としてサーバーに送信するかどうか、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] **datetime**型です。 **false** java.sql.Time 値としてサーバーに送信するかどうか、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] **時間**型です。  
  
## <a name="remarks"></a>解説  
 参照してください[接続プロパティの設定](../../../connect/jdbc/setting-the-connection-properties.md)の詳細については、 **sendTimeAsDatetime**接続プロパティです。  
  
 [SQLServerDataSource.setSendTimeAsDatetime](../../../connect/jdbc/reference/setsendtimeasdatetime-method-sqlserverdatasource.md)プログラムで設定することができます、 **sendTimeAsDatetime**接続プロパティです。  
  
 詳細については、次を参照してください。[を構成する方法の java.sql.Time 値は、サーバーに送信される](../../../connect/jdbc/configuring-how-java-sql-time-values-are-sent-to-the-server.md)です。  
  
## <a name="see-also"></a>参照  
 [SQLServerDataSource のメンバー](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource クラス](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  

