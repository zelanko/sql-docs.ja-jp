---
title: データ型の制限 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC desktop database drivers [ODBC], data types
- data types [ODBC], desktop database drivers
- desktop database drivers [ODBC], data types
ms.assetid: 81c4eab7-1f6b-47a0-b940-89d6c6a14dae
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 4beaf91a4ead743e3e8a2e32578796baba3c17be
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81280672"
---
# <a name="data-type-limitations"></a>データ型の制限事項
ODBC デスクトップ データベース ドライバでは、データ型に次の制限が課されます。  
  
|データ型|説明|  
|---------------|-----------------|  
|すべてのデータ型|型変換エラーが発生すると、影響を受ける列が NULL に設定される場合があります。|  
|BINARY|長さ 0 の BINARY 列を作成すると、実際には 255 バイトの BINARY 列が返されます。|  
|DATE|DATE データ型を、CONVERT 関数で別のデータ型 (それ自体) に変換することはできません。|  
|10 進数 (正確な数値)|サポートされていません。|  
|浮動小数点データ型|浮動小数点数の小数点以下の桁数は、Windows のコントロール パネルの [国際] セクションで設定されている数値形式によって制限される場合があります。|  
|NUMERIC|最大精度と 28 のスケールをサポートします。|  
|timestamp|TIMESTAMP データ型は、CONVERT 関数によってそれ自体に変換できません。|  
|TINYINT|TINYINT 値は常に符号なしです。|  
|長さ 0 の文字列|dBASE、Excel、パラドックス、またはテキストドライバを使用する場合、列に長さ 0 の文字列を挿入すると、実際には NULL が挿入されます。|
