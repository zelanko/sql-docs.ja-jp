---
title: "SELECT ステートメントの制限事項 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ODBC SQL grammar, SELECT statement limitations
- SELECT statement limitations [ODBC]
ms.assetid: c6b05955-f8fd-4706-a1a7-a8dbd74870c2
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 53b3e18a07e14e6059a9d193d8659a09b87e6c65
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="select-statement-limitations"></a>SELECT ステートメントの制限事項
SELECT ステートメントで非集計列を含む、集計関数の列を混在させることはできません。  
  
 GROUP BY 句が SELECT ステートメントの選択リストでは、GROUP BY 句から式を持つことができますのみまたは関数を設定します。  
  
 アスタリスク (すべての列を選択)、GROUP BY 句を含む SELECT ステートメントでの使用はサポートされていません。 選択する列の名前を指定する必要があります。  
  
 SELECT ステートメントで垂直バーの使用はサポートされていません。 垂直バーを格納するデータ値を参照する必要がある場合は、SELECT ステートメントで、パラメーターを使用します。  
  
 を SELECT ステートメントで列の別名を使用する場合、"as"という単語は、エイリアスを先頭にあります。 たとえば、"SELECT col1 として、b からです"。 なし、「と」、ステートメントはエラーを返します。  
  
 SELECT ステートメントに無効な列名が入力された、SQLSTATE 07001 エラー、「誤った数のパラメーター」が返されます、SQLSTATE S0022 エラーではなく「列で見つかりませんでした」  
  
 Microsoft Excel ドライバーを使用すると、空の文字列が列に挿入された場合、空の文字列は、NULL に変換しましたその列に WHERE 句で空の文字列で実行される検索結果の SELECT ステートメントは失敗します。

