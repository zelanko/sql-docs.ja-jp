---
title: getResponseBuffering メソッド (SQLServerDataSource) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.getResponseBuffering()
apilocation:
- SQLServerDataSource.getResponseBuffering()
apitype: Assembly
ms.assetid: 19585a93-88a4-415e-a20e-12ba58cddeaa
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 7ea9552ff9a9bf8d0a591f35670ca7147c67e18d
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2019
ms.locfileid: "66801361"
---
# <a name="getresponsebuffering-method-sqlserverdatasource"></a>getResponseBuffering メソッド (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md) オブジェクトの応答バッファリング モードが返されます。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.lang.String getResponseBuffering()  
```  
  
## <a name="return-value"></a>戻り値  
 A**文字列**小文字を含む**完全**または**アダプティブ**します。  
  
## <a name="remarks"></a>Remarks  
 **full** 値は、実行時にサーバーから結果全体を読み取ることを示します。  
  
 **adaptive** 値は、必要に応じて最小限のデータをバッファリングすることを示します。 既定のバッファリング モードは **adaptive** 値です。  
  
 詳細については、応答バッファリング モードを使用して、次を参照してください。[アダプティブ バッファリングを使用して](../../../connect/jdbc/using-adaptive-buffering.md)します。  
  
## <a name="see-also"></a>参照  
 [setResponseBuffering メソッド &#40;SQLServerDataSource&#41;](../../../connect/jdbc/reference/setresponsebuffering-method-sqlserverdatasource.md)   
 [SQLServerDataSource のメンバー](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource クラス](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
