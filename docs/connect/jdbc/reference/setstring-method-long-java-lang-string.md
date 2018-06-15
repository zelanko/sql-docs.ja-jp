---
title: setString (long, java.lang.String) メソッド |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerClob.setString (long, java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 1b2190e9-5ace-497a-8554-0e913ea9b0cb
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7194a8778ecae136d7a70086c5fa2e9353988a93
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32845307"
---
# <a name="setstring-method-long-javalangstring"></a>setString (long, java.lang.String) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  書き込み、指定された**文字列**を CLOB の指定された位置。  
  
## <a name="syntax"></a>構文  
  
```  
  
public int setString(long pos,  
                     java.lang.String s)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *pos*  
  
 CLOB への書き込みを開始する位置です。  
  
 *S*  
  
 **文字列**CLOB に書き込む。  
  
## <a name="return-value"></a>戻り値  
 書き込まれる文字数です。  
  
## <a name="exceptions"></a>例外  
 java.sql.SQLException  
  
## <a name="remarks"></a>解説  
 この setString メソッドは、setString、java.sql.Clob インターフェイスのメソッドでによって指定されます。  
  
 文字データは、指定された開始位置から上書きされ、CLOB の初期データの長さをオーバーランすることができます。 開始位置に CLOB の長さ + 1 の値を指定すると、文字列が追加されます。 位置を指定する + 2 以上 (または 0 以下) の値と、位置エラーがスローされます。  
  
## <a name="see-also"></a>参照  
 [setString メソッド&#40;SQLServerClob&#41;](../../../connect/jdbc/reference/setstring-method-sqlserverclob.md)   
 [SQLServerClob のメソッド](../../../connect/jdbc/reference/sqlserverclob-methods.md)   
 [SQLServerClob のメンバー](../../../connect/jdbc/reference/sqlserverclob-members.md)   
 [SQLServerClob クラス](../../../connect/jdbc/reference/sqlserverclob-class.md)  
  
  
