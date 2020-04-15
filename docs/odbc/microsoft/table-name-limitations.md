---
title: テーブル名の制限 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC SQL grammar, table name limitations
- table name limitations [ODBC]
- Excel driver [ODBC], table name limitations
ms.assetid: d9843e4b-1d05-4d5a-9dc3-ee9ec59edb97
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 738c563961eae56471f0238d9726a1ebb0bdc76e
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81289218"
---
# <a name="table-name-limitations"></a>テーブル名の制限
テーブル名には、有効な文字 (たとえば、スペース) を含めることができます。 テーブル名に文字、数字、およびアンダースコア以外の文字が含まれている場合、名前は引用符 (') で囲んで区切る必要があります。  
  
 Microsoft Excel ドライバを使用し、テーブル名がデータベース参照で修飾されていない場合、既定のデータベースは暗黙的に使用されます。 Excel の名前に "!"文字が含まれている場合は、その名前は自動的に "$" 文字に変換されます。  
  
 ファイル名>を参照\<する Excel のテーブル名は、Excel 3.0 および 4.0 ファイルでサポートされています。 ブック名>を参照\<する Excel のテーブル名は、Excel 5.0、7.0、または 97 ファイルでサポートされています。  
  
 dBASE ドライバーを使用すると、ASCII 値が 127 より大きい文字はアンダースコアに変換されます。  
  
 Access ドライバを使用する場合、テーブル名は 64 文字に制限されます。  
  
 dBASE、Microsoft Excel 3.0 または 4.0、パラドックス、またはテキスト ドライバーを使用する場合、特殊な MS-DOS キーワード CON、AUX、LPT1、および LPT2 はテーブル名として使用しないでください。
