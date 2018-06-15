---
title: getTime (int, java.util.Calendar) メソッド |Microsoft ドキュメント
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
- SQLServerCallableStatement.getTime (int, java.util.Calendar)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 87b7fbaf-7149-494f-b3b2-16b468a8ebf1
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d0e01aa8c9bb2f0f7e4f7ea38e9bcdda4dd128b9
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32838098"
---
# <a name="gettime-method-int-javautilcalendar"></a>getTime (int, java.util.Calendar) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  指定されたパラメーターの値を Java プログラミング言語、パラメーター インデックスを渡された Calendar オブジェクトを使用して、指定の java.sql.Time オブジェクトとして取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.sql.Time getTime(int index,  
                             java.util.Calendar cal)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *インデックス*  
  
 **Int**パラメーター インデックスを示すです。  
  
 *cal*  
  
 予定表オブジェクトです。  
  
## <a name="return-value"></a>戻り値  
 Time オブジェクト。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getTime メソッドは、java.sql.CallableStatement インターフェイスの getTime メソッドによって指定されます。  
  
 「Get アクセス操作子メソッドの変換」というタイトル図を参照してください[データ型変換について](../../../connect/jdbc/understanding-data-type-conversions.md)を確認するため[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]データ型は、このメソッドを使用して取得することができます。  
  
## <a name="see-also"></a>参照  
 [getTime メソッド&#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/gettime-method-sqlservercallablestatement.md)   
 [SQLServerCallableStatement のメンバー](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [SQLServerCallableStatement クラス](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
