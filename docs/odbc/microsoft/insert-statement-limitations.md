---
title: "INSERT ステートメントの制限事項 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ODBC SQL grammar, INSERT statement limitations
- INSERT statement limitations [ODBC]
- truncation of data [ODBC]
ms.assetid: dea05698-527a-41ab-8729-bbed85556185
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: f9233e7582083ba08fb1239120e63db819b8724b
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="insert-statement-limitations"></a>INSERT ステートメントの制限事項
長すぎる場合、列に収まるように、右側の警告なしで挿入されたデータが切り捨てられます。  
  
 列のデータ型の範囲外の値を挿入しようと、列に挿入される NULL が発生します。  
  
 DBASE、Excel、Paradox、または Textdriver 使用すると、長さ 0 の文字列を列に挿入実際には NULL が挿入、代わりにします。  
  
 Microsoft Excel ドライバーを使用すると、空の文字列が列に挿入された場合、空の文字列は、NULL に変換しましたその列に WHERE 句で空の文字列で実行される検索結果の SELECT ステートメントは失敗します。  
  
 テーブルでは、次の 2 つの条件下で、Paradox ドライバーによって更新できません。  
  
-   ときに、一意のインデックスでは、テーブルで定義されていません。 これは、空のテーブル、一意のインデックスがテーブルに定義されていない場合でも、1 つの行を更新できる該当しません。 場合は、一意のインデックスがない空のテーブルに 1 つの行が挿入された、アプリケーションは一意インデックスを作成または、1 つの行が挿入された後に、追加のデータを挿入できません。  
  
-   Borland データベース エンジンが実装されていない場合のみ読み取りし、追加 Paradox テーブルでステートメントを使用します。  
  
 Text driver を使用すると、NULL 値は固定長ファイル内の空白が埋め込まれます文字列によって表されますが、区切りファイルのスペースなしで表されます。 たとえば、次の行で 3 つのフィールドを含む、2 番目のフィールドでは、NULL 値には。  
  
```  
"Smith:,, 123  
```  
  
 Text driver を使用すると、すべての列の値は先頭のスペースが埋め込まれていることができます。 任意の行の長さは、65,543 バイト以下にする必要があります。
