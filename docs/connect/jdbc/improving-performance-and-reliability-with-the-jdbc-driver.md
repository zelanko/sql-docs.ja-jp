---
title: JDBC ドライバーによるパフォーマンスと信頼性の強化 | Microsoft Docs
ms.custom: ''
ms.date: 07/19/2018
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
ms.openlocfilehash: e9108ab6ac330086acab16a73550d5fcab5d3970
ms.sourcegitcommit: 603d2e588ac7b36060fa0cc9c8621ff2a6c0fcc7
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 08/14/2018
ms.locfileid: "42786112"
---
# <a name="improving-performance-and-reliability-with-the-jdbc-driver"></a>JDBC ドライバーによるパフォーマンスと信頼性の強化

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

アプリケーション開発において、パフォーマンスと信頼性の強化は常に求められるものです。 [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] は、このような要求を実現させる技術を豊富に備えています。  
  
このセクションのトピックでは、JDBC ドライバーを使用する際の、アプリケーションのパフォーマンスと信頼性を強化するさまざまな方法について説明します。  

## <a name="in-this-section"></a>このセクションの内容

|トピック|[説明]|  
|-----------|-----------------|  
|[使用されていないオブジェクトを閉じる](../../connect/jdbc/closing-objects-when-not-in-use.md)|必要なくなった JDBC ドライバー オブジェクトを閉じることの重要性について説明します。|  
|[トランザクション サイズの管理](../../connect/jdbc/managing-transaction-size.md)|トランザクションのパフォーマンスを向上させる方法について説明します。|  
|[ステートメントおよび結果セットの操作](../../connect/jdbc/working-with-statements-and-result-sets.md)|ステートメントまたは結果セットのオブジェクトを使用する場合は、パフォーマンスを向上させる方法について説明します。|  
|[アダプティブ バッファリングの使用](../../connect/jdbc/using-adaptive-buffering.md)|サーバー カーソルのオーバーヘッドを発生させることなく、あらゆる種類の大きな値のデータを取得できるように設計されている、アダプティブ バッファリング機能について説明します。|  
|[スパース列](../../connect/jdbc/sparse-columns.md)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のスパース列に対する JDBC ドライバーのサポートについて説明します。|  
|[JDBC Driver の準備されたステートメント メタデータ キャッシュ](../../connect/jdbc/prepared-statement-metadata-caching-for-the-jdbc-driver.md)|準備されたステートメントのクエリでパフォーマンスを改善するためのテクニックについて説明します。|
|[バッチ挿入操作に一括コピー API を使用する](../../connect/jdbc/use-bulk-copy-api-batch-insert-operation.md)|バッチ挿入操作とその利点を一括コピー API を有効にする方法について説明します。|

## <a name="see-also"></a>参照

[JDBC ドライバーの概要](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
  