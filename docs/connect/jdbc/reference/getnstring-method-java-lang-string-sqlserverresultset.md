---
title: getNString メソッド (java.lang.String) (SQLServerResultSet) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 546d77e2-723a-42ac-ba3f-fabf2395d376
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 962da02de824f164464a9dbc81c0a3ed54283738
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2020
ms.locfileid: "80905328"
---
# <a name="getnstring-method-javalangstring-sqlserverresultset"></a>getNString (java.lang.String) メソッド (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) オブジェクトの現在の行にある指定された列の値が、java.lang.String オブジェクトとして取得されます。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.lang.String getNString(java.lang.String columnLabel)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *columnLabel*  
  
 列ラベルを含む文字列です。  
  
## <a name="return-value"></a>戻り値  
 String オブジェクト。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getNString メソッドは、java.sql.SQLServerResultSet インターフェイスの getNString メソッドで規定されています。  
  
 このメソッドは、**SQLServerResultSet** オブジェクトの現在の行にある**nvarchar**、**nchar**、**nvarchar(max)** 、**ntext**、または [xml](../../../connect/jdbc/reference/sqlserverresultset-class.md) 列の値を取得するために使用できます。 このメソッドを使用して他のデータ型の値を取得しようとすると、例外がスローされます。  
  
## <a name="see-also"></a>参照  
 [getNString メソッド &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/getnstring-method-sqlserverresultset.md)   
 [SQLServerResultSet のメンバー](../../../connect/jdbc/reference/sqlserverresultset-members.md)  
  
  
