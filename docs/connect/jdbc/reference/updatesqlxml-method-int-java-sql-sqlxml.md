---
title: updateSQLXML (int, java.sql.SQLXML) メソッド |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: b5170751-fbe1-433b-96f5-4f237ba55f60
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 53dd6aba263f108a701cc95b8c2269f6edb0c9c8
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32849307"
---
# <a name="updatesqlxml-method-int-javasqlsqlxml"></a>updateSQLXML (int, java.sql.SQLXML) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Java.sql.SQLXML 値で指定された列を更新します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public void updateSQLXML(int columnIndex,  
                         java.sql.SQLXML xmlObject)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *columnIndex*  
  
 列インデックスを示す **int** です。  
  
 *xmlObject*  
  
 SQLXML オブジェクトです。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この updateSQLXML メソッドは、java.sql.ResultSet インターフェイスの updateSQLXML メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [updateSQLXML メソッド&#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updatesqlxml-method-sqlserverresultset.md)   
 [SQLServerResultSet のメンバー](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet クラス](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
