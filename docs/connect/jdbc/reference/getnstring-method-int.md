---
title: getNString メソッド (int) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 2048bb9f-7d9b-4aaa-b135-c716910cc800
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ae12095a915fdd1d6c0b47b934a5e0121c77df6f
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2020
ms.locfileid: "80905368"
---
# <a name="getnstring-method-int"></a>getNString (int) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  指定された **NCHAR**、**NVARCHAR**、または **LONGNVARCHAR** パラメーターの値が、Java プログラミング言語の文字列として取得されます。  
  
## <a name="syntax"></a>構文  
  
```  
  
public final java.lang.String getNString(int parameterIndex)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *parameterIndex*  
  
 パラメーターのインデックスを示す **int** です。  
  
## <a name="return-value"></a>戻り値  
 String オブジェクト。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getNString メソッドは、java.sql.CallableStatement インターフェイスの getNString メソッドで規定されています。  
  
## <a name="see-also"></a>参照  
 [getNString メソッド &#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/getnstring-method-sqlservercallablestatement.md)   
 [SQLServerCallableStatement のメンバー](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)  
  
  
