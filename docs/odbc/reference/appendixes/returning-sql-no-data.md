---
title: SQL_NO_DATA を返す |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL_NO_DATA [ODBC]
- backward compatibility [ODBC], SQL_NO_DATA
- compatibility [ODBC], SQL_NO_DATA
ms.assetid: deed0163-9d1a-4e9b-9342-3f82e64477d2
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 74c122819980abaa328db5ad46f240cae24b92d3
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "63280586"
---
# <a name="returning-sqlnodata"></a>SQL_NO_DATA を返す
ODBC 2 時にします。*x*アプリケーションの操作、ODBC 3 *.x*ドライバー呼び出し**SQLExecDirect**、 **SQLExecute**、または**SQLParamData**、検索された update または delete ステートメントが実行されましたが、データ ソース、ODBC 3 行によって影響されなかったと *.x*ドライバーは SQL_SUCCESS を返す必要があります。 ときに、ODBC 3 *.x* 、ODBC 3 の操作アプリケーション *.x*ドライバー呼び出し**SQLExecDirect**、 **SQLExecute**、または**SQLParamData**と同じ結果が、ODBC 3 *.x*ドライバーが SQL_NO_DATA を返す必要があります。  
  
 ステートメントのバッチにし、データ ソースで行が削除されない場合は、検索結果の update または delete のステートメント**SQLMoreResults** SQL_SUCCESS を返します。 SQL_NO_DATA は、するものであり、検索された更新/削除する行が影響を受けませんからの結果は、以上結果があることを意味するために返すことはできません。
