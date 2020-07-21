---
title: setNClob メソッド (java.lang.String, java.io.Reader) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: a595679a-89b7-4b18-9ad2-d9cb13af2a28
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 12b09f0a1f4847897397509e4c7cb985c1af7a2b
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2020
ms.locfileid: "80923279"
---
# <a name="setnclob-method-javalangstring-javaioreader"></a>setNClob (java.lang.String, java.io.Reader) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  指定されたパラメーターを、指定された Reader オブジェクトに設定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public final void setNClob(java.lang.String parameterName,  
              java.io.Reader reader)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *parameterName*  
  
 パラメーターの名前を含む**文字列**です。  
  
 *reader*  
  
 Reader オブジェクト。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 このメソッドは、**NCHAR**、**NVARCHAR**、**NTEXT**、**XML** の各パラメーター データ型に対して使用する必要があります。  
  
 この setNClob メソッドは、java.sql.CallableStatement インターフェイスの setNClob メソッドで規定されています。  
  
## <a name="see-also"></a>参照  
 [setNClob メソッド &#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/setnclob-method-sqlservercallablestatement.md)   
 [SQLServerCallableStatement のメンバー](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)  
  
  
