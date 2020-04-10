---
title: getLoginTimeout メソッド (SQLServerDataSource) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.getLoginTimeout
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 316f067c-9e08-456a-af19-b80b0bbd4a5c
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: db1ee4d76dede5b8249852f5ef0fcf91591c3e96
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2020
ms.locfileid: "80921376"
---
# <a name="getlogintimeout-method-sqlserverdatasource"></a>getLoginTimeout メソッド (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  接続の試行中に [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md) オブジェクトが待機する秒数を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public int getLoginTimeout()  
```  
  
## <a name="return-value"></a>戻り値  
 待機する秒数を表す **int** 値です。  
  
## <a name="remarks"></a>解説  
 アプリケーションがタイムアウト値を明示的に指定しない場合、このメソッドは既定値の 15 秒を返します。  
  
 この getLoginTimeout メソッドは、javax.sql.DataSource インターフェイスの getLoginTimeout メソッドで指定されています。  
  
## <a name="see-also"></a>参照  
 [SQLServerDataSource のメンバー](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource クラス](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
