---
title: absolute メソッド (SQLServerResultSet) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.absolute
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 638e8148-8ca0-4e1f-9ec2-04a11bc9809b
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: b0572ed756bd8b347c01e05168873ac543a0ea7e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "66783555"
---
# <a name="absolute-method-sqlserverresultset"></a>absolute メソッド (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) オブジェクトの指定された行にカーソルを移動します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public boolean absolute(int row)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *row*  
  
 移動先の行番号を示す **int** です。 正の値、負の値、または 0 を指定できます。  
  
## <a name="return-value"></a>戻り値  
 **true**の指定された位置にカーソルが移動した場合。 **false**最初の行の前に、または最後の行より後である場合。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 この absolute メソッドは、java.sql.ResultSet インターフェイスの absolute メソッドで規定されています。  
  
## <a name="see-also"></a>参照  
 [SQLServerResultSet のメンバー](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet クラス](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
