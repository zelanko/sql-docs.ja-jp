---
title: ステータスレコードのシーケンス |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- diagnostic information [ODBC], diagnostic records
- status records [ODBC]
- diagnostic records [ODBC]
ms.assetid: 0e0436cc-230f-44b0-b373-04a57e83ee76
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: bb26731a85d1d6313658fe9c24a32167b351d2d9
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304173"
---
# <a name="sequence-of-status-records"></a>状態レコードのシーケンス
2 つ以上の状態レコードが返された場合、ドライバー マネージャーとドライバーは、次の規則に従ってそれらをランク付けします。 最高ランクのレコードが最初のレコードです。 レコードのソース (ドライバー マネージャー、ドライバー、ゲートウェイなど) は、レコードのランク付け時には考慮されません。  
  
-   **エラー**エラーを記述する状態レコードのランクが最も高い。 エラー レコードの中で、トランザクションの失敗またはトランザクションの失敗の可能性を示すレコードは、他のすべてのレコードを上回ります。 2 つ以上のレコードが同じエラー状態を記述する場合、オープン・グループ CLI 仕様 (クラス 03 から HZ) によって定義された SQLSTATE は、ODBC 定義およびドライバー定義の SQLSTATE を上回ります。  
  
-   **実装定義のデータなし値**ドライバー定義の No Data 値 (クラス 02) を記述する状態レコードは、2 番目に高いランクを持ちます。  
  
-   **警告**警告を記述する状態レコード (クラス 01) のランクは最も低くなります。 2 つ以上のレコードが同じ警告条件を記述している場合、オープン・グループ CLI 仕様で定義された警告 SQLSTATE は、ODBC 定義およびドライバー定義の SQLSTATE を上回ります。  
  
 最高ランクのレコードが複数存在する場合、どのレコードが最初のレコードであるかは未定義です。 他のすべてのレコードの順序は未定義です。 特に、エラーの前に警告が表示される場合があるため、関数がSQL_SUCCESS以外の値を返すときに、アプリケーションはすべての状態レコードをチェックする必要があります。
