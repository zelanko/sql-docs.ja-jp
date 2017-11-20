---
title: "テーブル名の制限事項 |Microsoft ドキュメント"
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
- ODBC SQL grammar, table name limitations
- table name limitations [ODBC]
- Excel driver [ODBC], table name limitations
ms.assetid: d9843e4b-1d05-4d5a-9dc3-ee9ec59edb97
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 690b6242b9e8d38b6a1f26ddbd823215030e2b15
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="table-name-limitations"></a>テーブル名の制限
テーブル名には、有効な文字 (スペースなど) を含めることができます。 テーブル名に文字、数字、およびアンダー スコアを除く任意の文字が含まれている場合は、逆引用符 (') で囲んだ名前を区切る必要があります。  
  
 Microsoft Excel ドライバーを使用すると、データベースの参照では、テーブル名は修飾されていない、既定のデータベースは暗黙的です。 Microsoft Excel での名前が含まれている場合、"!"文字の場合、自動的に変換されます「$」文字を代わりにします。  
  
 Microsoft Excel のテーブル名を参照する\<ファイル名 > Microsoft Excel 3.0 と 4.0 のファイルではサポートされています。 Microsoft Excel のテーブル名を参照する\<ブック名 > 5.0、7.0、または 97 Microsoft Excel ファイルがサポートされています。  
  
 DBASE ドライバーを使用すると、127 より大きい ASCII 値を持つ文字はアンダー スコアに変換されます。  
  
 Microsoft Access ドライバーを使用すると、テーブル名は 64 文字以内に制限されます。  
  
 DBASE、Excel 3.0 または 4.0 では、Paradox、またはテキストのドライバーが使用すると、MS-DOS の特別なキーワード CON、AUX、LPT1、LPT2 する必要がありますテーブル名として使用されません。

