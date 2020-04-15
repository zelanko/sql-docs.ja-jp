---
title: SELECT ステートメントの制限 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC SQL grammar, SELECT statement limitations
- SELECT statement limitations [ODBC]
ms.assetid: c6b05955-f8fd-4706-a1a7-a8dbd74870c2
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d91e93076a67287cbbd2b64b2ad0d6414a0aea6d
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300922"
---
# <a name="select-statement-limitations"></a>SELECT ステートメントの制限事項
集計関数列を SELECT ステートメントで非集計列と混合することはできません。  
  
 GROUP BY 句を持つ SELECT ステートメントの選択リストには、GROUP BY 句またはセット関数からの式のみを含めることができます。  
  
 GROUP BY 句を含む SELECT ステートメントでアスタリスク (すべての列を選択) を使用することはサポートされていません。 選択する列の名前を指定する必要があります。  
  
 SELECT ステートメントでの垂直バーの使用はサポートされていません。 垂直バーを含むデータ値を参照する必要がある場合は、SELECT ステートメントでパラメーターを使用します。  
  
 SELECT ステートメントで列の別名を使用する場合は、別名の前に 「as」という語を付けなければなりません。 たとえば、"select col1 を b から a として選択します。 "as" を指定しないと、ステートメントはエラーを返します。  
  
 SELECT ステートメントに間違った列名が入力されると、SQLSTATE S0022 エラー「列が見つかりません」の代わりに、SQLSTATE 07001 エラー「パラメーターの数が正しくありません」が返されます。  
  
 Microsoft Excel ドライバを使用する場合、空の文字列が列に挿入されると、空の文字列は NULL に変換されます。WHERE 句で空の文字列を使用して実行される検索 SELECT ステートメントは、その列では成功しません。
