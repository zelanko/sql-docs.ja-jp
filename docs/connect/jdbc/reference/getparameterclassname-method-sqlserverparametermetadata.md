---
title: getParameterClassName メソッド (SQLServerParameterMetaData) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerParameterMetaData.getParameterClassName
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 545634d8-f06b-429a-9293-0087d758f359
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 7d341d828d3ae0527192c96a3c63fb2951eef7a1
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2020
ms.locfileid: "80904588"
---
# <a name="getparameterclassname-method-sqlserverparametermetadata"></a>getParameterClassName メソッド (SQLServerParameterMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  [SQLServerPreparedStatement](../../../connect/jdbc/reference/setobject-method-sqlserverpreparedstatement.md) クラスの [setObject](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) メソッドにインスタンスを渡す必要のある、Java クラスの完全修飾名を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.lang.String getParameterClassName(int param)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *param*  
  
 パラメーターのインデックスを示す **int** です。  
  
## <a name="return-value"></a>戻り値  
 完全修飾クラス名を含む**文字列**です。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getParameterClassName メソッドは、java.sql.ParameterMetaData インターフェイスの getParameterClassName メソッドで指定されています。  
  
## <a name="see-also"></a>参照  
 [SQLServerParameterMetaData のメソッド](../../../connect/jdbc/reference/sqlserverparametermetadata-methods.md)   
 [SQLServerParameterMetaData のメンバー](../../../connect/jdbc/reference/sqlserverparametermetadata-members.md)   
 [SQLServerParameterMetaData クラス](../../../connect/jdbc/reference/sqlserverparametermetadata-class.md)  
  
  
