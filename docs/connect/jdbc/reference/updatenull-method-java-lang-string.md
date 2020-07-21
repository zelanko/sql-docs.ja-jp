---
title: updateNull メソッド (java.lang.String) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.updateNull (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: fb3e5cde-30e1-4c95-adf0-d5b6c1f0da95
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 20e12781b8b8d19874bb2abeca8fcc2a331d515e
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2020
ms.locfileid: "80919780"
---
# <a name="updatenull-method-javalangstring"></a>updateNull (java.lang.String) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  渡された列名を使用して、指定された列を null 値で更新します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public void updateNull(java.lang.String columnName)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *columnName*  
  
 列名を含む**文字列**です。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この updateNull メソッドは、java.sql.ResultSet インターフェイスの updateNull メソッドで規定されています。  
  
## <a name="see-also"></a>参照  
 [updateNull メソッド &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updatenull-method-sqlserverresultset.md)   
 [SQLServerResultSet のメンバー](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet クラス](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
