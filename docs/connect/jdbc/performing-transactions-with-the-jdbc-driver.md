---
title: JDBC ドライバーでのトランザクションの実行 |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: afbb776f-05dc-4e79-bb25-2c340483e401
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ba3c37d70e6457907540abcec19daa275573b414
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="performing-transactions-with-the-jdbc-driver"></a>JDBC ドライバーを使用したトランザクションの実行
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  トランザクション処理技術は、永続的なデータの一貫性を保証する必要のあるすべてのアプリケーションの必須要件です。 [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]、トランザクション処理するローカルで実行されるか、分散します。 トランザクションは、実行の ACID (原子性、一貫性、分離性、および持続性) を有する単位です。  
  
 このセクションのトピックでは、分離レベル、トランザクションのセーブポイント、および結果セットの保持機能など、JDBC ドライバーによってトランザクションがどのようにサポートされるかについて説明します。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
|トピック|Description|  
|-----------|-----------------|  
|[トランザクションについて](../../connect/jdbc/understanding-transactions.md)|JDBC ドライバーでトランザクションがどのように使用されるかについて概要を説明します。|  
|[XA トランザクションについて](../../connect/jdbc/understanding-xa-transactions.md)|JDBC ドライバーで XA トランザクションがどのように使用されるかについて概要を説明します。|  
|[分離レベルについて](../../connect/jdbc/understanding-isolation-levels.md)|JDBC ドライバーでサポートされるさまざまな分離レベルについて説明します。|  
|[セーブポイントの使用](../../connect/jdbc/using-savepoints.md)|トランザクションのセーブポイントと共に JDBC ドライバーを使用する方法について説明します。|  
|[保持機能の使用](../../connect/jdbc/using-holdability.md)|結果セットの保持機能と共に JDBC ドライバーを使用する方法について説明します。|  
  
## <a name="see-also"></a>参照  
 [JDBC ドライバーの概要](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
  
  
