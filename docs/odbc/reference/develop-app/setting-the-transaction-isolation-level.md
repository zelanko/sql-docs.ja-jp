---
title: "トランザクション分離レベルに設定する |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- isolation levels [ODBC]
- transaction isolation [ODBC]
- transactions [ODBC], isolation
ms.assetid: 64a037f0-5065-4f45-9669-6710404a540c
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d30d7746cb49609154a9b5e82ec7a85b1a1480e8
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="setting-the-transaction-isolation-level"></a>トランザクション分離レベルに設定します。
トランザクション分離レベルを設定するには、アプリケーションは、SQL_ATTR_TXN_ISOLATION 接続属性を使用します。 データ ソースが、要求された分離レベルをサポートしていない場合、ドライバーまたはデータ ソースより高いレベルを設定できます。 どのようなトランザクション分離レベルでデータ ソースを決定するをサポートし、既定の分離レベルは、アプリケーションが呼び出す**SQLGetInfo** SQL_TXN_ISOLATION_OPTION と SQL_DEFAULT_TXN_ISOLATION オプションで、それぞれします。  
  
 トランザクション分離レベルは、データベースのデータの整合性を最大限に保護を提供します。 Serializable トランザクションでは、他のトランザクションによって影響を受けるすることは保証および、データベースの整合性を維持するために保証されるためです。  
  
 しかし、高いレベルのトランザクション分離がパフォーマンスが低下アプリケーションが解放されるデータのロックを待機する必要がある可能性が増えるためです。 アプリケーションでは、次の場合にパフォーマンスを向上する分離の下位レベルを指定できます。  
  
-   ときにそれを保証できる他のトランザクションが存在しないことは、アプリケーションのトランザクションと干渉する可能性です。 このような状況では、小規模な会社の 1 人のユーザーが 1 台のコンピューターの個人データを含む dBASE ファイルを保持する場合など、限られた状況でのみ発生し、これらのファイルを共有しません。  
  
-   場合速度精度およびすべてのエラーよりも重要が小さいする可能性があります。 たとえば、会社が多くの小さい売り上げ高を行うことと、大規模な営業はまれであるとします。 開いているすべての売上の合計値を推定するトランザクションでは、Read Uncommitted 分離レベルを安全に使用可能性があります。 注文が開かれたり閉じられたりするは、その後、トランザクションが含まれますが、ロールバックこれらは一般的にも無効にし、ことが、このような順序を検出するたびにブロックされていないために、トランザクションがはるかに高速です。  
  
 詳細については、次を参照してください。[オプティミスティック同時実行制御](../../../odbc/reference/develop-app/optimistic-concurrency.md)です。
