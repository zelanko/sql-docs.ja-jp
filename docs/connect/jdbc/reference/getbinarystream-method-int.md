---
title: "getBinaryStream (int) メソッド |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname: SQLServerResultSet.getBinaryStream (int)
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: de22a6c4-1ba3-4ed0-91a2-bf235c2ceec3
caps.latest.revision: "10"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 7ff5be6d0a47439f1226ff098c747cd73bb4c991
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="getbinarystream-method-int"></a>getBinaryStream (int) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  この現在の行に指定された列インデックスの値を取得[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)オブジェクトとして解釈されないバイトのバイナリ ストリーム。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.io.InputStream getBinaryStream(int columnIndex)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *columnIndex*  
  
 **Int**列インデックスを示すです。  
  
## <a name="return-value"></a>戻り値  
 InputStream オブジェクト。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getBinaryStream メソッドは、java.sql.ResultSet インターフェイスの getBinaryStream メソッドによって指定されます。  
  
 このメソッドでのみ使用できます[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]binary、varbinary、varbinary (max)、およびイメージのデータ型。 他のデータ型で使用すると、例外がスローされます。  
  
 このメソッドで値をストリームとして取得した後は、ストリームからこの値をチャンク単位で読み取ることができます。 このメソッドは、大きな LONGVARBINARY 値を取得する場合に適しています。  
  
> [!NOTE]  
>  返されたストリーム内のデータはすべて、他の列の値を取得する前に読み取る必要があります。 次に getter メソッドを呼び出すと、ストリームは暗黙的に閉じます。 また、ストリーム 0 を返します InputStream.available メソッドが呼び出されると、データが使用できるかどうかどうか。  
  
## <a name="see-also"></a>参照  
 [getBinaryStream メソッド &#40;です。SQLServerResultSet &#41;](../../../connect/jdbc/reference/getbinarystream-method-sqlserverresultset.md)   
 [SQLServerResultSet のメンバー](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet クラス](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
