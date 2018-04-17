---
title: SQL_NO_DATA を返す |Microsoft ドキュメント
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
- SQL_NO_DATA [ODBC]
- backward compatibility [ODBC], SQL_NO_DATA
- compatibility [ODBC], SQL_NO_DATA
ms.assetid: deed0163-9d1a-4e9b-9342-3f82e64477d2
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 0163c8e9d8c207d2ce8a7ae80c4ec03d9b7c64e2
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="returning-sqlnodata"></a>SQL_NO_DATA を返す
ODBC 2 時にします。*x*アプリケーション処理 ODBC 3*.x*ドライバー呼び出し**SQLExecDirect**、 **SQLExecute**、または**SQLParamData**、検索された update または delete ステートメントが実行されたが、データ ソース、ODBC 3 行が影響を与えないと*.x*ドライバーは SQL_SUCCESS を返す必要があります。 ときに ODBC 3*.x* ODBC 3 作業アプリケーション*.x*ドライバー呼び出し**SQLExecDirect**、 **SQLExecute**、または**SQLParamData** ODBC 3、同じ結果に*.x*ドライバーが SQL_NO_DATA を返す必要があります。  
  
 ステートメントのバッチがデータ ソースで行に影響を与えない場合は、検索結果を更新または delete ステートメントで**SQLMoreResults** SQL_SUCCESS を返します。 SQL_NO_DATA は、ことを意味するものであり、結果を検索した更新/削除する行に影響はありませんが、以上結果があるため、返すことはできません。
