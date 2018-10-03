---
title: getTime (java.lang.String, java.util.Calendar) メソッド | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerCallableStatement.getTime (java.lang.String, java.util.Calendar)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 3d4c67c2-a3c8-4a26-a159-89c5d63fda0b
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 200267a37383d858d80419d49e0fbd5172294907
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47793670"
---
# <a name="gettime-method-javalangstring-javautilcalendar"></a>getTime (java.lang.String, java.util.Calendar) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  パラメーターに渡された名前と Calendar オブジェクトを使用して、指定されたパラメーターの値を Java プログラミング言語の java.sql.Time オブジェクトとして取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.sql.Time getTime(java.lang.String sCol,  
                             java.util.Calendar cal)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *sCol*  
  
 パラメーターの名前を含む**文字列**です。  
  
 *cal*  
  
 暦オブジェクト。  
  
## <a name="return-value"></a>戻り値  
 時刻のオブジェクト。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 この getTime メソッドは、java.sql.CallableStatement インターフェイスの getTime メソッドで規定されています。  
  
 「Get アクセス操作子メソッドの変換」というタイトル図を参照してください[データ型変換について](../../../connect/jdbc/understanding-data-type-conversions.md)を確認する[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]データ型は、このメソッドで取得できます。  
  
## <a name="see-also"></a>参照  
 [getTime メソッド &#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/gettime-method-sqlservercallablestatement.md)   
 [SQLServerCallableStatement のメンバー](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [SQLServerCallableStatement クラス](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
