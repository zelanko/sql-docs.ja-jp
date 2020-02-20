---
title: isWrapperFor メソッド (SQLServerStatement) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 53f3291f-d43a-476b-a656-d86168dacf6c
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c35cad678ce4f9b6008b656302d4767bad9b1244
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/31/2020
ms.locfileid: "67977065"
---
# <a name="iswrapperfor-method-sqlserverstatement"></a>isWrapperFor メソッド (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  ステートメント オブジェクトが指定されたインターフェイスのラッパーであるかどうかを示します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public boolean isWrapperFor(Class iface)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *iface*  
  
 インターフェイスを定義する **class** です。  
  
## <a name="return-value"></a>戻り値  
 このオブジェクトがインターフェイスを実装しているか、インターフェイスを実装しているオブジェクトをラップしている場合は **true** です。 それ以外の場合は、 **false**です。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 [isWrapperFor](../../../connect/jdbc/reference/iswrapperfor-method-sqlserverstatement.md) メソッドと [unwrap](../../../connect/jdbc/reference/unwrap-method-sqlserverstatement.md) メソッドは、JDBC 4.0 で導入された java.sql.Wrapper インターフェイスで定義されています。  
  
 このメソッドが true を返す場合、同じ引数を使用した [unwrap](../../../connect/jdbc/reference/unwrap-method-sqlserverstatement.md) の呼び出しは成功します。  
  
 コード例については、「[大きなデータを更新するサンプル](../../../connect/jdbc/updating-large-data-sample.md)」を参照してください。  
  
 詳細については、「[ラッパーとインターフェイス](../../../connect/jdbc/wrappers-and-interfaces.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [unwrap メソッド &#40;SQLServerStatement&#41;](../../../connect/jdbc/reference/unwrap-method-sqlserverstatement.md)   
 [SQLServerStatement のメンバー](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement クラス](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
