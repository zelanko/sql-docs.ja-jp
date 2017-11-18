---
title: "updateBinaryStream メソッド (java.io.InputStream) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 56883144-26a0-4f45-ad36-4f616369af3e
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 1fa688afc52a05664525a165930dca7ed7ac4b49
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="updatebinarystream-method-javalangstring-javaioinputstream"></a>updateBinaryStream (java.lang.String, java.io.InputStream) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  指定された列をバイナリ ストリーム値で更新します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public void updateBinaryStream(java.lang.String columnLabel,  
                               java.io.InputStream x)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *columnLabel*  
  
 A**文字列**列ラベルを格納しています。  
  
 *x*  
  
 InputStream オブジェクト。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この updateBinaryStream メソッドは、java.sql.ResultSet インターフェイスの updateBinaryStream メソッドによって指定されます。  
  
 このメソッドを使用して、**イメージ**、**テキスト**、および**ntext** SQL Server データ型には、パフォーマンスが低下します。  
  
 このメソッドは、選択された状態に InputStream オブジェクトからバイトを渡します[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]binary、varbinary、varbinary (max)、image、xml、および udt などのバイナリ列です。 このメソッドでは、文字型の列の更新はサポートされていません。 更新するには文字型列、InputStream を使用して、 [updateAsciiStream](../../../connect/jdbc/reference/updateasciistream-method-sqlserverresultset.md)メソッドです。  
  
## <a name="see-also"></a>参照  
 [updateBinaryStream メソッド & #40 です。SQLServerResultSet &#41;](../../../connect/jdbc/reference/updatebinarystream-method-sqlserverresultset.md)   
 [SQLServerResultSet のメンバー](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet クラス](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  

