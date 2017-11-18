---
title: "大きなデータの処理 |Microsoft ドキュメント"
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
ms.assetid: 5b93569f-eceb-4f05-b49c-067564cd3c85
caps.latest.revision: 24
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 2249704a4f5cf87694d1acb01ff46a119a4be7e8
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="working-with-large-data"></a>大きなデータの処理
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  JDBC ドライバーは、サーバー カーソルのオーバーヘッドを発生させることなく、あらゆる種類の大きな値のデータを取得できるアダプティブ バッファリングをサポートします。 アダプティブ バッファリングによる、[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]からステートメントの実行結果を取得、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]一度にはなく、アプリケーションの必要に応じて、します。 また、アプリケーションからアクセスできなくなった結果は、ドライバーによって直ちに破棄されます。  
  
 [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005_md.md)] JDBC Driver version 1.2 のバッファリング モードが"**完全**"既定でします。 アプリケーション"responseBuffering"接続プロパティを設定しなかったかどうか"**アダプティブ**"接続プロパティで、またはを使用して、 [setResponseBuffering](../../connect/jdbc/reference/setresponsebuffering-method-sqlserverstatement.md)のメソッド、 [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md)オブジェクト、サーバーから結果全体を一度に読み取る、サポートされているドライバーです。 アダプティブ バッファリングの動作を取得するために、アプリケーションは"responseBuffering"接続プロパティを設定する必要がある"**アダプティブ**"明示的にします。  
  
 **アダプティブ**値が既定のバッファリング モードであり、JDBC ドライバーが必要な場合に、最小の可能なデータをバッファーします。 アダプティブ バッファリングの使用の詳細については、次を参照してください。[アダプティブ バッファリングを使用して](../../connect/jdbc/using-adaptive-buffering.md)です。  
  
 このセクションのトピックから大きな値データの取得に使用できるさまざまな方法を説明する[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データベース。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
|トピック|Description|  
|-----------|-----------------|  
|[大きなデータを読み取るサンプル](../../connect/jdbc/reading-large-data-sample.md)|SQL ステートメントを使用して大きな値のデータを取得する方法について説明します。|  
|[ストアド プロシージャで大きなデータを読み取るサンプル](../../connect/jdbc/reading-large-data-with-stored-procedures-sample.md)|大きな CallableStatement OUT パラメーター値を取得する方法について説明します。|  
|[大きなデータを更新するサンプル](../../connect/jdbc/updating-large-data-sample.md)|データベース内の大きな値のデータを更新する方法について説明します。|  
  
## <a name="see-also"></a>参照  
 [サンプル JDBC Driver アプリケーション](../../connect/jdbc/sample-jdbc-driver-applications.md)  
  
  

