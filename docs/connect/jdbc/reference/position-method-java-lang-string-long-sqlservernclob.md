---
title: position (java.lang.String, long) メソッド (SQLServerNClob) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 46d4beec-831a-449f-98b6-322a80cc499a
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 4dd9e30039b0d5ef429b8e729ce36f7b085e5cfc
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/29/2020
ms.locfileid: "67976460"
---
# <a name="position-method-javalangstring-long-sqlservernclob"></a>position (java.lang.String, long) メソッド (SQLServerNClob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  指定された部分文字列 *searchstr* が、この **NClob** オブジェクトによって表される **NCLOB** 値の中で出現する文字位置を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public long position(java.lang.String searchstr,  
              long start)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *searchstr*  
  
 検索対象の部分文字列。  
  
 *start*  
  
 検索を開始する位置です。最初の位置は 1 です。  
  
## <a name="return-value"></a>戻り値  
 部分文字列が現れる位置です。部分文字列がない場合は -1 が返されます。 最初の位置は 1 です。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この position メソッドは、java.sql.NClob インターフェイスの position メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [position メソッド &#40;SQLServerNClob&#41;](../../../connect/jdbc/reference/position-method-sqlservernclob.md)   
 [SQLServerNClob のメソッド](../../../connect/jdbc/reference/sqlservernclob-methods.md)   
 [SQLServerNClob のメンバー](../../../connect/jdbc/reference/sqlservernclob-members.md)   
 [SQLServerNClob クラス](../../../connect/jdbc/reference/sqlservernclob-class.md)  
  
  
