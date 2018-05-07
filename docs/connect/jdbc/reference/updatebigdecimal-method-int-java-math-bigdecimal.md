---
title: updateBigDecimal (int, java.math.BigDecimal) メソッド |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerResultSet.updateBigDecimal (int, java.math.BigDecimal)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 1e15de27-a490-45cd-a3a6-a49721f15a97
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ccb1fa9ab184f7357323c5d8deb417b93ec7985e
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="updatebigdecimal-method-int-javamathbigdecimal"></a>updateBigDecimal (int, java.math.BigDecimal) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  列インデックス BigDecimal オブジェクトで指定された列を更新します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public void updateBigDecimal(int index,  
                             java.math.BigDecimal x)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *インデックス*  
  
 列インデックスを示す **int** です。  
  
 *x*  
  
 BigDecimal オブジェクトです。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この updateBigDecimal メソッドは、java.sql.ResultSet インターフェイスの updateBigDecimal メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [updateBigDecimal メソッド&#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updatebigdecimal-method-sqlserverresultset.md)   
 [SQLServerResultSet のメンバー](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet クラス](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
