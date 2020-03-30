---
title: updateString (int, java.lang.String) メソッド | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.updateString (int, java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: f8d2f620-0cdf-4a3b-8af4-5e8c4462a42d
author: MightyPen
ms.author: genemi
ms.openlocfilehash: ad0f00eb57bfcf417e45a99ab6b9210ff2277e78
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/29/2020
ms.locfileid: "67998249"
---
# <a name="updatestring-method-int-javalangstring"></a>updateString (int, java.lang.String) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  渡された列インデックスを使用して、指定された列を**文字列**の値で更新します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public void updateString(int index,  
                         java.lang.String x)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *インデックス*  
  
 列インデックスを示す **int** です。  
  
 *x*  
  
 **String** オブジェクト。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この updateString メソッドは、java.sql.ResultSet インターフェイスの updateString メソッドで規定されています。  
  
## <a name="see-also"></a>参照  
 [updateString メソッド &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updatestring-method-sqlserverresultset.md)   
 [SQLServerResultSet のメンバー](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet クラス](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
