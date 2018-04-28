---
title: getStatementPoolingCacheSize メソッド (SQLServerDataSource) |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2018
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
ms.assetid: ''
caps.latest.revision: 1
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f58035df09c3eabb70042dd334c0412206bee607
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="getstatementpoolingcachesize-method-sqlserverdatasource"></a>getStatementPoolingCacheSize メソッド (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  値を返します**statementPoolingCacheSize**接続プロパティです。 この接続の準備されたステートメント キャッシュのサイズを返します。 '0' では、キャッシュ有効になっていないことを意味します。
  
## <a name="syntax"></a>構文  
  
```
public boolean getStatementPoolingCacheSize();  
```  
  
## <a name="return-value"></a>戻り値  
 **Int**の値、 **statementPoolingCacheSize**接続プロパティです。  

## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
 
## <a name="remarks"></a>解説  
 このメソッドは、JDBC ドライバーのバージョン 6.4 から利用できるとは。
 
## <a name="see-also"></a>参照  
 [SQLServerDataSource のメンバー](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource クラス](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
