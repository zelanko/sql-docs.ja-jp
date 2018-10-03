---
title: getInt (int) メソッド |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerCallableStatement.getInt (int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: c86792bb-096e-4c58-8b9e-74491ccf83a6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e4b3d0f708418dcc6c90b556eb6ff503d4a80b6f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47851670"
---
# <a name="getint-method-int"></a>getInt (int) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  パラメーターに渡されたインデックスを使用して、指定されたパラメーターの値が Java プログラミング言語の **int** として取得されます。  
  
## <a name="syntax"></a>構文  
  
```  
  
public int getInt(int index)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *index*  
  
 パラメーターのインデックスを示す **int** です。  
  
## <a name="return-value"></a>戻り値  
 **Int**値。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 この getInt メソッドは、java.sql.CallableStatement インターフェイスの getInt メソッドで規定されています。  
  
 このメソッドは、int、smallint、tinyint、bit などの整数値を安全に返すことができる [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のデータ型でのみサポートされます。 このメソッドを他のデータ型で使用すると、例外がスローされます。  
  
## <a name="see-also"></a>参照  
 [getInt メソッド &#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/getint-method-sqlservercallablestatement.md)   
 [SQLServerCallableStatement のメンバー](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [SQLServerCallableStatement クラス](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
