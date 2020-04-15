---
title: トランザクション分離レベルの設定 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- isolation levels [ODBC]
- transaction isolation [ODBC]
- transactions [ODBC], isolation
ms.assetid: 64a037f0-5065-4f45-9669-6710404a540c
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 80401b276355a47469355cb6921d768d168398ae
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299812"
---
# <a name="setting-the-transaction-isolation-level"></a>トランザクション分離レベルの設定
トランザクション分離レベルを設定するために、アプリケーションはSQL_ATTR_TXN_ISOLATION接続属性を使用します。 データ ソースが要求された分離レベルをサポートしていない場合、ドライバーまたはデータ ソースは、より高いレベルを設定できます。 データ ソースがサポートするトランザクション分離レベルと既定の分離レベルを判断するために、アプリケーションは、それぞれ SQL_TXN_ISOLATION_OPTION オプションとSQL_DEFAULT_TXN_ISOLATION オプションを指定して**SQLGetInfo**を呼び出します。  
  
 トランザクション分離レベルが高いほど、データベース・データの整合性を最大限に保護できます。 シリアル化可能なトランザクションは、他のトランザクションの影響を受けないため、データベースの整合性を維持することが保証されます。  
  
 ただし、トランザクション分離のレベルが高いと、アプリケーションがデータのロックが解放されるのを待つ必要が生じる可能性が高くなるため、パフォーマンスが低下する可能性があります。 アプリケーションでは、以下の場合にパフォーマンスを向上させるために、より低いレベルの分離を指定できます。  
  
-   アプリケーションのトランザクションに干渉する可能性のある他のトランザクションが存在しない場合。 この状況は、小規模な会社の 1 人のユーザーが 1 台のコンピュータ上の個人データを含む dBASE ファイルを管理し、これらのファイルを共有しない場合など、限られた状況でのみ発生します。  
  
-   速度が精度よりも重要で、エラーが小さくなる可能性がある場合。 たとえば、ある企業が小さな売上を多く作り、大きな売上がまれであるとします。 オープン販売の合計値を見積もるトランザクションは、コミットされていない読み取り分離レベルを安全に使用できます。 トランザクションには、開いているか、閉じられ、その後ロールバックされる注文が含まれますが、これらは一般的に互いに取り消され、トランザクションは、そのような注文に遭遇するたびにブロックされないので、はるかに高速になります。  
  
 詳細については、「[オプティミスティック同時実行制御](../../../odbc/reference/develop-app/optimistic-concurrency.md)」を参照してください。
