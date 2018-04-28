---
title: getSubString メソッド (SQLServerNClob) |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1d91c930-1bac-4da9-b9a5-ac2cfd31541b
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 769f543a2b84474746743bca1e42253cbdc132a0
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="getsubstring-method-sqlservernclob"></a>getSubString メソッド (SQLServerNClob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  指定された部分文字列のコピーを取得、 **NCLOB**に基づいて指定された開始位置とコピーする文字数。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.lang.String getSubString(long pos,  
                                  int length)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *pos*  
  
 抽出する部分文字列の先頭の文字です。 先頭の文字の位置は 1 です。  
  
 *長さ*  
  
 コピーする連続した文字の文字数です。  
  
## <a name="return-value"></a>戻り値  
 A**文字列**内で指定した部分文字列は、 **NCLOB**です。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getSubString メソッドは、getSubString、java.sql.NClob インターフェイスのメソッドでによって指定されます。  
  
 null または長さが 0 の NCLOB から 0 文字を取得しようとすると、空の文字列が返されます。 長さが 0 の NCLOB で、位置 1 以外の場所で任意の長さの文字を取得しようとすると、位置の例外がスローされます。  
  
## <a name="see-also"></a>参照  
 [SQLServerNClob のメソッド](../../../connect/jdbc/reference/sqlservernclob-methods.md)   
 [SQLServerNClob のメンバー](../../../connect/jdbc/reference/sqlservernclob-members.md)   
 [SQLServerNClob クラス](../../../connect/jdbc/reference/sqlservernclob-class.md)  
  
  
