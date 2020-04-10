---
title: updateObject (int, java.lang.Object, int) メソッド | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.updateObject (int, java.lang.Object, int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 9d33571b-4887-49d3-96df-8abda7b5a904
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3e03d18176eb5c76a2d8332810cc3c7cffe34efc
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2020
ms.locfileid: "80919765"
---
# <a name="updateobject-method-int-javalangobject-int"></a>updateObject (int, java.lang.Object, int) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  渡された列インデックスおよび小数点以下桁数を使用して、指定された列を **Object** 値で更新します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public void updateObject(int index,  
                         java.lang.Object x,  
                         int scale)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *インデックス*  
  
 列インデックスを示す **int** です。  
  
 *obj*  
  
 **Object** 値。  
  
 *scale*  
  
 java.sql.Types.DECIMAL 型または java.sql.Types.NUMERIC 型の場合、この値は小数点以下の桁数になります。 他のすべての型については、この値は無視されます。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="see-also"></a>参照  
 [updateObject メソッド &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updateobject-method-sqlserverresultset.md)   
 [SQLServerResultSet のメンバー](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet クラス](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
