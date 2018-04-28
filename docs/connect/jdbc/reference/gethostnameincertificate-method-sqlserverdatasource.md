---
title: getHostNameInCertificate メソッド (SQLServerDataSource) |Microsoft ドキュメント
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
- getHostNameInCertificate Method (SQLServerDataSource)
apilocation:
- getHostNameInCertificate Method (SQLServerDataSource)
apitype: Assembly
ms.assetid: 45ea04e2-9ea5-4171-9136-d09f8a95e128
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b0e9312b4c8d8162c069cf9c73ce82c5313fd428
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="gethostnameincertificate-method-sqlserverdatasource"></a>getHostNameInCertificate メソッド (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  SQL Server の SSL (Secure Sockets Layer) 証明書の検証に使用されるホスト名を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.lang.String getHostNameInCertificate()  
```  
  
## <a name="return-value"></a>戻り値  
 A**文字列**ホスト名、または値が設定されていない場合は null を格納しています。  
  
## <a name="remarks"></a>解説  
 ホスト名を使用して、通信レイヤーが SSL で暗号化されているときに、SQL Server の SSL 証明書の値を検証します。  
  
 ホスト名が設定されていない場合、 [getHostNameInCertificate](../../../connect/jdbc/reference/gethostnameincertificate-method-sqlserverdatasource.md) null が返されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerDataSource のメンバー](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource クラス](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
