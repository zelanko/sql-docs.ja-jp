---
title: 状態レコードのシーケンス |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- diagnostic information [ODBC], diagnostic records
- status records [ODBC]
- diagnostic records [ODBC]
ms.assetid: 0e0436cc-230f-44b0-b373-04a57e83ee76
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 0a45a5be0c99dd6389fd060cc53f5140c5e7c263
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="sequence-of-status-records"></a>状態レコードのシーケンス
2 つ以上の状態レコードが返される場合は、ドライバー マネージャーとドライバーのランク付けに次の規則に従ってします。 最高のランクを持つレコードは、最初のレコードです。 (ドライバー マネージャー、ドライバー、ゲートウェイ、およびなど) のレコードのソースとは見なされませんときにレコードを順位付けされます。  
  
-   **エラー**状態レコードのエラーを記述する最高ランクであります。 エラー レコードの間では、トランザクションの失敗または可能なトランザクションの失敗を示すレコードは、他のすべてのレコードを outrank です。 2 つまたは複数のレコードには、同じエラー条件について説明する、開くグループ CLI 仕様 (HZ を通じてクラス 03) で定義される SQLSTATEs は ODBC 定義およびドライバー定義 SQLSTATEs を outrank です。  
  
-   **No データ値の実装で定義された**なしのデータ値 (クラス 02) のドライバーの定義を記述する状態レコードがある、2 つ目最高ランクです。  
  
-   **警告**警告 (クラス 01) を示す状態レコード最低ランクであります。 2 つまたは複数のレコードについて警告 SQLSTATEs 開くグループ CLI 仕様によって定義されている、同じ警告の状態を説明する場合は、ODBC で定義され、ドライバーの定義済みの SQLSTATEs を outrank です。  
  
 最高のランクを持つ 2 つ以上のレコードがある場合は、どのレコードが最初のレコードは未定義です。 その他のすべてのレコードの順序は定義されません。 具体的には、エラーの前に警告が表示されるため、関数に関係なく SQL_SUCCESS 以外の値が返されるときに、アプリケーションは状態のすべてのレコードを確認する必要があります。
