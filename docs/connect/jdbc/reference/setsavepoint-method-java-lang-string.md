---
title: setSavepoint (java.lang.String) メソッド |Microsoft ドキュメント
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
- SQLServerConnection.setSavepoint (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 1cf15ec4-d9d9-4ab3-bfee-2ea43ff609a6
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a38bd657439dab6c705c176b6bbe90ab5f643546
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32845547"
---
# <a name="setsavepoint-method-javalangstring"></a>setSavepoint (java.lang.String) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  指定した名前、現在のトランザクションにセーブポイントを作成し、返します新しい[SQLServerSavepoint](../../../connect/jdbc/reference/sqlserversavepoint-class.md)を表すオブジェクト。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.sql.Savepoint setSavepoint(java.lang.String sName)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *sName*  
  
 A**文字列**セーブポイントの名前を含む値です。  
  
## <a name="return-value"></a>戻り値  
 セーブポイント オブジェクトです。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この setSavePoint メソッドは、java.sql.Connection インターフェイスの setSavePoint メソッドによって指定されます。  
  
 *SName*引数はによって自動的にエスケープ、[!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]です。  
  
## <a name="see-also"></a>参照  
 [setSavepoint メソッド&#40;SQLServerConnection&#41;](../../../connect/jdbc/reference/setsavepoint-method-sqlserverconnection.md)   
 [SQLServerConnection のメンバー](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection クラス](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
