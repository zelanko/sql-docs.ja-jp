---
title: "SQLServerParameterMetaData のメンバー |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f9ebb203-2013-4feb-94f5-494b7f098f9a
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 6fbc42820d6a35c054f705eefec36a9c05ee08c3
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="sqlserverparametermetadata-members"></a>SQLServerParameterMetaData のメンバー
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  次の表に、によって公開されるメンバー、 [SQLServerParameterMetaData](../../../connect/jdbc/reference/sqlserverparametermetadata-class.md)クラスです。  
  
## <a name="constructors"></a>コンス トラクター  
 [なし] :  
  
## <a name="fields"></a>フィールド  
 [なし] :  
  
## <a name="inherited-fields"></a>継承されたフィールド  
  
|名前|Description|  
|----------|-----------------|  
|java.sql.ParameterMetaData|parameterModeIn、parameterModeInOut、parameterModeOut、parameterModeUnknown、parameterNoNulls、parameterNullable、parameterNullableUnknown|  
  
## <a name="methods"></a>メソッド  
  
|名前|Description|  
|----------|-----------------|  
|[getParameterClassName](../../../connect/jdbc/reference/getparameterclassname-method-sqlserverparametermetadata.md)|そのインスタンスを渡す必要があります、Java クラスの完全修飾名を取得、 [setObject](../../../connect/jdbc/reference/setobject-method-sqlserverpreparedstatement.md)のメソッド、 [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)クラスです。|  
|[getParameterCount](../../../connect/jdbc/reference/getparametercount-method-sqlserverparametermetadata.md)|内のパラメーターの数を取得、 [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)対象のオブジェクト[SQLServerParameterMetaData](../../../connect/jdbc/reference/sqlserverparametermetadata-class.md)オブジェクト情報を格納します。|  
|[getParameterMode](../../../connect/jdbc/reference/getparametermode-method-sqlserverparametermetadata.md)|指定されたパラメーターのモードを取得します。|  
|[getParameterType](../../../connect/jdbc/reference/getparametertype-method-sqlserverparametermetadata.md)|指定されたパラメーターの SQL 型を取得します。|  
|[getParameterTypeName](../../../connect/jdbc/reference/getparametertypename-method-sqlserverparametermetadata.md)|指定されたパラメーターのデータベース固有の型名を取得します。|  
|[getPrecision](../../../connect/jdbc/reference/getprecision-method-sqlserverparametermetadata.md)|指定されたパラメーターの 10 進の桁数を取得します。|  
|[getScale](../../../connect/jdbc/reference/getscale-method-sqlserverparametermetadata.md)|指定されたパラメーターの小数点以下の桁数を取得します。|  
|[isNullable](../../../connect/jdbc/reference/isnullable-method-sqlserverparametermetadata.md)|指定されたパラメーターで null 値が許可されるかどうかを取得します。|  
|[isSigned](../../../connect/jdbc/reference/issigned-method-sqlserverparametermetadata.md)|指定されたパラメーターの値が符号付き数値かどうかを取得します。|  
  
## <a name="inherited-methods"></a>継承されたメソッド  
  
|継承元のクラス|メソッド|  
|---------------------------|-------------|  
|java.lang.Object|clone、equals、finalize、getClass、hashCode、notify、notifyAll、toString、wait|  
|java.sql.Wrapper|isWrapperFor、unwrap|  
  
## <a name="see-also"></a>参照  
 [SQLServerParameterMetaData クラス](../../../connect/jdbc/reference/sqlserverparametermetadata-class.md)  
  
  

