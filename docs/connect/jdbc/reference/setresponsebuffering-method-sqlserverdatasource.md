---
title: setResponseBuffering メソッド (SQLServerDataSource) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.setResponseBuffering(String responseBufferingValue)
apilocation:
- SQLServerDataSource.setResponseBuffering(String responseBufferingValue)
apitype: Assembly
ms.assetid: c9e43ff2-8117-4dca-982d-83c863d0c8e1
author: MightyPen
ms.author: genemi
ms.openlocfilehash: f5bfc0fb1d1a74131d0e8e71055356f958a9b508
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/31/2020
ms.locfileid: "67973104"
---
# <a name="setresponsebuffering-method-sqlserverdatasource"></a>setResponseBuffering メソッド (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md) オブジェクトを使用して作成された接続の応答バッファリング モードを設定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public void setResponseBuffering(java.lang.String value)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *value*  
  
 バッファリングとストリーミングのモードを含む**文字列**です。 有効なモードは **full** または **adaptive** のいずれかです。モードを表すこれらの文字列では、大文字と小文字のどちらも使用できます。  
  
## <a name="remarks"></a>解説  
 **full** 値は、実行時にサーバーから結果全体を読み取ることを示します。  
  
 **adaptive** 値は、必要に応じて最小限のデータをバッファリングすることを示します。 既定のバッファリング モードは **adaptive** 値です。  
  
 応答バッファリング モードの使用方法の詳細については、「[アダプティブ バッファリングの使用](../../../connect/jdbc/using-adaptive-buffering.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [SQLServerDataSource のメンバー](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource クラス](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
