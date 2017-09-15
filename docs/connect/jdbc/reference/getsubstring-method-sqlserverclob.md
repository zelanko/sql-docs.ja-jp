---
title: "getSubString メソッド (SQLServerClob) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLServerClob.getSubString
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: bf915590-a883-4403-befa-5b5bb42f34d8
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 0030ce1e83feaa1a619fa9ead2bac3dfec4ccf6d
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="getsubstring-method-sqlserverclob"></a>getSubString メソッド (SQLServerClob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  渡された開始位置とコピーする文字数に基づいて、指定された CLOB の部分文字列のコピーを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.lang.String getSubString(long pos,  
                                     int length)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *pos*  
  
 抽出する部分文字列の先頭の文字です。 先頭の文字の位置は 1 です。  
  
 *length*  
  
 コピーする連続した文字の文字数です。  
  
## <a name="return-value"></a>戻り値  
 A**文字列**CLOB の指定した部分文字列はします。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getSubString メソッドは、java.sql.Clob インターフェイスの getSubString メソッドによって指定されます。  
  
 null または長さが 0 の CLOB から 0 文字を取得しようとすると、空の文字列が返されます。 長さが 0 の CLOB で、位置 1 以外の場所で任意の長さの文字を取得しようとすると、位置の例外がスローされます。  
  
## <a name="see-also"></a>参照  
 [SQLServerClob のメソッド](../../../connect/jdbc/reference/sqlserverclob-methods.md)   
 [SQLServerClob のメンバー](../../../connect/jdbc/reference/sqlserverclob-members.md)   
 [SQLServerClob クラス](../../../connect/jdbc/reference/sqlserverclob-class.md)  
  
  
