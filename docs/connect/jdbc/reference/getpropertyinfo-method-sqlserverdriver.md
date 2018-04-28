---
title: getPropertyInfo メソッド (SQLServerDriver) |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
apiname:
- SQLServerDriver.getPropertyInfo
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: b5eaad8a-31ef-44ac-af11-d5caa13ac3e2
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 011176c3cb96320832bc9a4c0d64894082ff2c3b
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="getpropertyinfo-method-sqlserverdriver"></a>getPropertyInfo メソッド (SQLServerDriver)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  データベースへの接続に必要なプロパティを検出するために使用します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.sql.DriverPropertyInfo[] getPropertyInfo(java.lang.String Url,  
                                                     java.util.Properties Info)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *Url*  
  
 A**文字列**データベースへの接続に使用される URL を含む値です。  
  
 *情報*  
  
 プロパティ値のペアの一覧です。初回使用時には null です。  
  
## <a name="return-value"></a>戻り値  
 DriverPropertyInfo オブジェクトの配列。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getPropertyInfo メソッドは、java.sql.Driver インターフェイスの getPropertyInfo メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerDriver のメソッド](../../../connect/jdbc/reference/sqlserverdriver-methods.md)   
 [SQLServerDriver のメンバー](../../../connect/jdbc/reference/sqlserverdriver-members.md)   
 [SQLServerDriver クラス](../../../connect/jdbc/reference/sqlserverdriver-class.md)  
  
  
