---
title: getSQLXML メソッド (int) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: a1b32d3a-d7c9-4086-ae2b-fc1da96949b1
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 957def695287bbd63d21e02859a441f07e3583be
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/31/2020
ms.locfileid: "67979688"
---
# <a name="getsqlxml-method-int"></a>getSQLXML (int) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  パラメーターに渡されたインデックスを使用して、指定されたパラメーターの値を SQLXML オブジェクトとして取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public final java.sql.SQLXML getSQLXML(int parameterIndex)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *parameterIndex*  
  
 パラメーターのインデックスを示す **int** です。  
  
## <a name="return-value"></a>戻り値  
 ASQLXML オブジェクト。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getSQLXML メソッドは、java.sql.CallableStatement インターフェイスの getSQLXML メソッドで規定されています。  
  
## <a name="see-also"></a>参照  
 [getSQLXML メソッド &#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/getsqlxml-method-sqlservercallablestatement.md)   
 [SQLServerCallableStatement のメンバー](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)  
  
  
