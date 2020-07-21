---
title: getShort (int) メソッド | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerCallableStatement.getShort (int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: cd9773c1-b598-4adb-aaf6-0c0f589cbef5
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 18161201976c0a00a4d32989667198cd8998223c
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/29/2020
ms.locfileid: "67979880"
---
# <a name="getshort-method-int"></a>getShort (int) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  パラメーターに渡されたインデックスを使用して、指定されたパラメーターの値が Java プログラミング言語の **short** として取得されます。  
  
## <a name="syntax"></a>構文  
  
```  
  
public short getShort(int index)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *インデックス*  
  
 パラメーターのインデックスを示す **int** です。  
  
## <a name="return-value"></a>戻り値  
 **short** 値です。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getShort メソッドは、java.sql.CallableStatement インターフェイスの getShort メソッドで規定されています。  
  
 このメソッドは、**smallint**、**tinyint**、**bit** などの整数値を安全に返すことができる [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データ型でのみサポートされます。 このメソッドを他のデータ型で使用すると、例外がスローされます。  
  
## <a name="see-also"></a>参照  
 [getShort メソッド &#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/getshort-method-sqlservercallablestatement.md)   
 [SQLServerCallableStatement のメンバー](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [SQLServerCallableStatement クラス](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
