---
title: getSQLXML (java.lang.String) メソッド |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: f56b192a-3255-4215-b552-8e494fbca083
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: e0fde3887e7f8ac1b2444ba81a93715eed631b02
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2019
ms.locfileid: "66773986"
---
# <a name="getsqlxml-method-javalangstring"></a>getSQLXML (java.lang.String) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  渡されたパラメーター名を使用して、指定されたパラメーターの値を SQLXML オブジェクトとして取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public final java.sql.SQLXML getSQLXML(java.lang.String parameterName)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *parameterName*  
  
 パラメーターの名前を示す **String** です。  
  
## <a name="return-value"></a>戻り値  
 ASQLXMLobject します。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 この getSQLXML メソッドは、java.sql.CallableStatement インターフェイスの getSQLXML メソッドで規定されています。  
  
## <a name="see-also"></a>参照  
 [getSQLXML メソッド &#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/getsqlxml-method-sqlservercallablestatement.md)   
 [SQLServerCallableStatement のメンバー](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)  
  
  
