---
title: "JDBC ドライバーによるパフォーマンスと信頼性を向上させる |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2018
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
ms.assetid: e1592499-b87b-45ee-bab8-beaba8fde841
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d8b2d716ada4cb786eb141c0f49dcad41c5231c4
ms.sourcegitcommit: 9d0467265e052b925547aafaca51e5a5e93b7e38
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/02/2018
---
# <a name="improving-performance-and-reliability-with-the-jdbc-driver"></a>JDBC ドライバーによるパフォーマンスと信頼性の強化
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  アプリケーション開発において、パフォーマンスと信頼性の強化は常に求められるものです。 これを行うための手法のいくつか、[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]です。  
  
 このセクションのトピックでは、JDBC ドライバーを使用する際の、アプリケーションのパフォーマンスと信頼性を強化するさまざまな方法について説明します。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
|トピック|Description|  
|-----------|-----------------|  
|[使用されていないオブジェクトを閉じる](../../connect/jdbc/closing-objects-when-not-in-use.md)|必要なくなった JDBC ドライバー オブジェクトを閉じることの重要性について説明します。|  
|[トランザクション サイズの管理](../../connect/jdbc/managing-transaction-size.md)|トランザクションのパフォーマンスを向上させる方法について説明します。|  
|[ステートメントおよび結果セットの操作](../../connect/jdbc/working-with-statements-and-result-sets.md)|ステートメントまたは結果セットのオブジェクトを使用する場合は、パフォーマンスを向上させる方法について説明します。|  
|[アダプティブ バッファリングの使用](../../connect/jdbc/using-adaptive-buffering.md)|サーバー カーソルのオーバーヘッドを発生させることなく、あらゆる種類の大きな値のデータを取得できるように設計されている、アダプティブ バッファリング機能について説明します。|  
|[スパース列](../../connect/jdbc/sparse-columns.md)|JDBC ドライバーのサポートについて説明[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]スパース列です。|  
|[JDBC Driver のキャッシュの準備されたステートメント メタデータ](../../connect/jdbc/prepared-statement-metadata-caching-for-the-jdbc-driver.md)|準備されたステートメントのクエリのパフォーマンスを向上させるためのテクニックについて説明します。|
  
## <a name="see-also"></a>参照  
 [JDBC ドライバーの概要](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
  
  