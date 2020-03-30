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
ms.openlocfilehash: c6b8f6239fbc229af009fc9745b0f19ed27e7ee1
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/29/2020
ms.locfileid: "67979053"
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
  
 Calendar オブジェクト。  
  
## <a name="return-value"></a>戻り値  
 Time オブジェクト。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getTime メソッドは、java.sql.CallableStatement インターフェイスの getTime メソッドで規定されています。  
  
 このメソッドで取得できる [ データ型を確認するには、「](../../../connect/jdbc/understanding-data-type-conversions.md)データ型変換について[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]」の「getter メソッドの変換」というタイトルの図を参照してください。  
  
## <a name="see-also"></a>参照  
 [getTime メソッド &#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/gettime-method-sqlservercallablestatement.md)   
 [SQLServerCallableStatement のメンバー](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [SQLServerCallableStatement クラス](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
