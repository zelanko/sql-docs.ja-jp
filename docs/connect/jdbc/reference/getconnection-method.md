---
title: getConnection メソッド () | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.getConnection ()
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 7f520e96-5313-468f-b987-535ddaea027e
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 714ba26610aa27fbc05cb27156b293c13e58130d
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2020
ms.locfileid: "80923326"
---
# <a name="getconnection-method-"></a>getConnection () メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md) オブジェクトが示すデータ ソースとの接続の確立を試みます。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.sql.Connection getConnection()  
```  
  
## <a name="return-value"></a>戻り値  
 [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) オブジェクトです。  
  
## <a name="exceptions"></a>例外  
 java.sql.SQLException  
  
## <a name="remarks"></a>解説  
 この getConnection メソッドは、javax.sql.DataSource インターフェイスの getConnection メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [getConnection メソッド &#40;SQLServerDataSource&#41;](../../../connect/jdbc/reference/getconnection-method-sqlserverdatasource.md)   
 [SQLServerDataSource のメンバー](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource クラス](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
