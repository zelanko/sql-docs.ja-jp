---
title: Reader オブジェクトへの setNCharacterStream メソッド - string | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: fd19fbb8-a878-4d98-a584-e4969d649844
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 34eb40d6c36f5c1586ac690de5e9fc354c8fd1f3
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/29/2020
ms.locfileid: "67973871"
---
# <a name="setncharacterstream-method-javalangstring-javaioreader"></a>setNCharacterStream (java.lang.String, java.io.Reader) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  指定されたパラメーターを、指定された Reader オブジェクトに設定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public final void setNCharacterStream(java.lang.String parameterName,  
                       java.io.Reader value)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *parameterName*  
  
 パラメーターの名前を示す **String** です。  
  
 *value*  
  
 Reader オブジェクト。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この setNCharacterStream メソッドは、java.sql.CallableStatement インターフェイスの setNCharacterStream メソッドによって指定されます。  
  
 このメソッドは、**NCHAR**、**NVARCHAR**、**NTEXT**、**XML** の各データ型に対して使用する必要があります。  
  
## <a name="see-also"></a>参照  
 [setNCharacterStream メソッド &#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/setncharacterstream-method-sqlservercallablestatement.md)   
 [SQLServerCallableStatement のメンバー](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)  
  
  
