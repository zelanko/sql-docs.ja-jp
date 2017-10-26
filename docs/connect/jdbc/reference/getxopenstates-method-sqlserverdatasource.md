---
title: "getXopenStates メソッド (SQLServerDataSource) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLServerDataSource.getXopenStates
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: de6fdf6b-8345-4490-b35e-7115b61e782e
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 218dd99d0da0f560ae08b2bfc3edf27d3a24a960
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="getxopenstates-method-sqlserverdatasource"></a>getXopenStates メソッド (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  返します、**ブール**XOPEN 互換の状態を SQL 状態の変換が有効かどうかを示す値。  
  
## <a name="syntax"></a>構文  
  
```  
  
public boolean getXopenStates()  
```  
  
## <a name="return-value"></a>戻り値  
 **true** XOPEN 互換の状態を SQL 状態の変換が有効になっている場合。 それ以外の場合は、 **false**です。  
  
## <a name="remarks"></a>解説  
 XopenStates プロパティ設定されている場合**true**、 [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] SQL 状態を XOPEN 互換の状態に変換されます。 既定値は**false**、SQL 99 の状態コードを生成するには、JDBC ドライバーを停止します。 XopenStates が設定されていない場合、getXopenStates メソッドは、の既定値を返します**false**です。  
  
## <a name="see-also"></a>参照  
 [SQLServerDataSource のメンバー](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource クラス](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  

