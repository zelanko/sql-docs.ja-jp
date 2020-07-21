---
title: getCharacterStream メソッド (int) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.getCharacterStream (int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 4f9f230d-be4c-469a-b3dc-f24531429aae
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: db007b56cd917eb67aa4e0fdbbb46598865a8d16
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2020
ms.locfileid: "80907924"
---
# <a name="getcharacterstream-method-int"></a>getCharacterStream (int) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) オブジェクトの現在の行にある指定された列インデックスの値が、java.io.Reader オブジェクトとして取得されます。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.io.Reader getCharacterStream(int columnIndex)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *columnIndex*  
  
 列インデックスを示す **int** です。  
  
## <a name="return-value"></a>戻り値  
 Reader オブジェクト。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getCharacterStream メソッドは、java.sql.ResultSet インターフェイスの getCharacterStream メソッドで規定されています。  
  
 このメソッドでは、nchar、nvarchar、nvarchar(max)、ntext などの [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の Unicode 文字データ型のみが読み取られます。 ASCII 文字型などのその他のデータ型では、例外がスローされます。 ASCII データ型を読み取るには、[getAsciiStream](../../../connect/jdbc/reference/getasciistream-method-sqlserverresultset.md) メソッドを使用します。  
  
## <a name="see-also"></a>参照  
 [getCharacterStream メソッド &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/getcharacterstream-method-sqlserverresultset.md)   
 [SQLServerResultSet のメンバー](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet クラス](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
