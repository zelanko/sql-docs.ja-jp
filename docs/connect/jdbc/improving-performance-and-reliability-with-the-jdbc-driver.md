---
title: JDBC ドライバーによるパフォーマンスと信頼性を向上させる |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: e1592499-b87b-45ee-bab8-beaba8fde841
caps.latest.revision: 25
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 58521cbe6c21e7ef58fc97b52e1ef6b27209e4fe
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
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
|[JDBC Driver の準備されたステートメント メタデータ キャッシュ](../../connect/jdbc/prepared-statement-metadata-caching-for-the-jdbc-driver.md)|準備されたステートメントのクエリのパフォーマンスを向上させるためのテクニックについて説明します。|
  
## <a name="see-also"></a>参照  
 [JDBC ドライバーの概要](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
  
  