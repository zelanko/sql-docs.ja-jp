---
title: getDate (int, java.util.Calendar) メソッド |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerCallableStatement.getDate (int, java.util.Calendar)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 38ce7b75-2623-4eff-bc18-8cf7193adec8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c9d436c323415465f95760a92795e4bace50765c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47849770"
---
# <a name="getdate-method-int-javautilcalendar"></a>getDate (int, java.util.Calendar) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  パラメーターで渡されたインデックスと Calendar オブジェクトを使用して、指定されたパラメーターの値を Java プログラミング言語の java.sql.Date オブジェクトとして取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.sql.Date getDate(int index,  
                             java.util.Calendar cal)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *index*  
  
 パラメーターのインデックスを示す **int** です。  
  
 *cal*  
  
 暦オブジェクト。  
  
## <a name="return-value"></a>戻り値  
 Date オブジェクト。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 この getDate メソッドは、java.sql.CallableStatement インターフェイスの getDate メソッドで規定されています。  
  
 このメソッドは、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の **datetime** または **smalldatetime** データ型の有効な日付部分が返されます。時刻部分は Java のベースラインの時刻である 00:00 (午前 0 時) に設定されます。  
  
## <a name="see-also"></a>参照  
 [getDate メソッド &#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/getdate-method-sqlservercallablestatement.md)   
 [SQLServerCallableStatement のメンバー](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [SQLServerCallableStatement クラス](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
