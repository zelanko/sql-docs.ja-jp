---
title: INSERT ステートメントの制限 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC SQL grammar, INSERT statement limitations
- INSERT statement limitations [ODBC]
- truncation of data [ODBC]
ms.assetid: dea05698-527a-41ab-8729-bbed85556185
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f903f15ec13baa28a789891c1527dc742daa68ac
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300008"
---
# <a name="insert-statement-limitations"></a>INSERT ステートメントの制限事項
挿入されたデータは、列に収まらない長さでも警告なしに右側で切り捨てられます。  
  
 列のデータ型の範囲外の値を挿入しようとすると、NULL が列に挿入されます。  
  
 dBASE、Excel、パラドックス、またはテキストドライバを使用する場合、列に長さ 0 の文字列を挿入すると、実際には NULL が挿入されます。  
  
 Microsoft Excel ドライバを使用する場合、空の文字列が列に挿入されると、空の文字列は NULL に変換されます。WHERE 句で空の文字列を使用して実行される検索 SELECT ステートメントは、その列では成功しません。  
  
 次の 2 つの条件の下で、Paradox ドライバによってテーブルが更新できません。  
  
-   一意のインデックスがテーブルに定義されていない場合。 これは、表に一意索引が定義されていなくても単一行で更新できる空の表には当てはまりません。 一意のインデックスを持たない空のテーブルに 1 行を挿入した場合、アプリケーションは、1 行の挿入後に一意のインデックスを作成したり、追加のデータを挿入したりすることはできません。  
  
-   Borland データベース エンジンが実装されていない場合、Paradox テーブルでは読み取りおよび追加ステートメントのみが許可されます。  
  
 テキスト ドライバーを使用する場合、NULL 値は固定長ファイルで空白の文字列で表されますが、区切りファイルでは空白で表されません。 たとえば、次の行に 3 つのフィールドが含まれている場合、2 番目のフィールドは NULL 値です。  
  
```  
"Smith:,, 123  
```  
  
 Text ドライバを使用する場合、すべての列の値に先頭のスペースを埋め込むことができます。 行の長さは 65,543 バイト以下でなければなりません。
