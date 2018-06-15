---
title: getString (int) メソッド |Microsoft ドキュメント
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
- SQLServerCallableStatement.getString (int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: f3fce8bf-8d6e-476f-aa6d-992daa79b899
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6f21b98752effb5fafbc7f87307f639b35697eda
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32839127"
---
# <a name="getstring-method-int"></a>getString (int) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  として指定されたパラメーターの値を取得、**文字列**java プログラミング言語のパラメーターのインデックスを指定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.lang.String getString(int index)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *インデックス*  
  
 **Int**パラメーター インデックスを示すです。  
  
## <a name="return-value"></a>戻り値  
 A**文字列**値。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getString メソッドは、java.sql.CallableStatement インターフェイスの getString メソッドによって指定されます。  
  
 すべての列[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]を文字列として返されることができます。 つまり、数値ベースと文字ベースのすべての型の文字列表現、および binary、varbinary、varbinary(max)、image、timestamp、uniqueidentifier などのバイナリ列の 16 進形式の文字列表現を返すことができます。  
  
 Money、smallmoney、datetime、smalldatetime、float、real、decimal、および numeric などの場所に依存した型では、型の基になる値の標準の toString() 形式を返します。  
  
 ユーザー定義型は、16 進形式の文字列値として返されます。  
  
## <a name="see-also"></a>参照  
 [getString メソッド&#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/getstring-method-sqlservercallablestatement.md)   
 [SQLServerCallableStatement のメンバー](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [SQLServerCallableStatement クラス](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
