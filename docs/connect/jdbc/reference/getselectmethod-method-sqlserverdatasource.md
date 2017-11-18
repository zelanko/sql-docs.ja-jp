---
title: "getSelectMethod メソッド (SQLServerDataSource) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLServerDataSource.getSelectMethod
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: b6255d2e-0028-474a-afa8-553ef092243e
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: dae0422612846e25cb2d2a60273f753802df3da0
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="getselectmethod-method-sqlserverdatasource"></a>getSelectMethod メソッド (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  これを使用して作成されるすべての結果セットを使用する既定のカーソルの種類を返します[SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)オブジェクト。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.lang.String getSelectMethod()  
```  
  
## <a name="return-value"></a>戻り値  
 A**文字列**既定のカーソルの種類を含む値です。  
  
## <a name="remarks"></a>解説  
 selectMethod プロパティは、結果セットで使用される既定のカーソルの種類を指定します。 このプロパティは、大きな結果セットを処理する場合に、クライアント側でのメモリ セット全体の結果を格納しないようにすると便利です。 このプロパティを "cursor" に設定することで、一度にフェッチするデータのチャンクを小さくできるサーバー側のカーソルを作成できます。 selectMethod プロパティが設定されていない場合、getSelectMethod は既定値の "direct" を返します。  
  
## <a name="see-also"></a>参照  
 [SQLServerDataSource のメンバー](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource クラス](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  

