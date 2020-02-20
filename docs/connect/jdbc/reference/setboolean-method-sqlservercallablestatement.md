---
title: setBoolean メソッド (SQLServerCallableStatement) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerCallableStatement.setBoolean
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 8cd810b1-9858-4e51-9535-239d864cd288
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 04f09bcd843946763fe3bb2b69cbdcd9560e7c91
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/31/2020
ms.locfileid: "67975038"
---
# <a name="setboolean-method-sqlservercallablestatement"></a>setBoolean メソッド (SQLServerCallableStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  指定されたパラメーターを、渡された **boolean** 値に設定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public void setBoolean(java.lang.String sCol,  
                       boolean b)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *sCol*  
  
 パラメーターの名前を含む**文字列**です。  
  
 *b*  
  
 **boolean** 値。**true** または **false**。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この setBoolean メソッドは、java.sql.CallableStatement インターフェイスの setBoolean メソッドで規定されています。  
  
## <a name="see-also"></a>参照  
 [SQLServerCallableStatement のメンバー](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [SQLServerCallableStatement クラス](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
