---
title: 列名の制限 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- desktop database drivers [ODBC], column names
- ODBC desktop database drivers [ODBC], column names
ms.assetid: 5a339f61-c52f-40ad-8deb-d785f72753d4
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 41d973afdac360af114da41620997cad23a2c740
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81281382"
---
# <a name="column-name-limitations"></a>列名の制限
列名には、任意の有効な文字 (例えば、スペース) を含めることができます。 列名に文字、数字、およびアンダースコア以外の文字が含まれている場合、名前は引用符 (') で囲んで区切る必要があります。  
  
 Access または Excel のドライバを使用する場合、列名は 64 文字に制限され、長い名前はエラーを生成します。 Paradox ドライバを使用する場合、最大列名は 25 文字です。 Text ドライバを使用する場合、最大列名は 64 文字で、長い名前は切り捨てられます。  
  
 dBASE ドライバーを使用すると、ASCII 値が 127 より大きい文字はアンダースコアに変換されます。  
  
 Microsoft Excel ドライバを使用する場合、列名が存在する場合は、最初の行に含める必要があります。 Excel で "!"文字を使用する名前は、後ろ引用符 (') で囲む必要があります。 "!"文字は、名前が引用符で囲まれていても、ODBC 名では使用できないため、"!"文字は "$" 文字に変換されます。 他のすべての有効な Excel 文字 (パイプ文字 (&#124;) を除く) は、スペースを含む列名に使用できます。 スペースを含めるには、Excel の列名に区切り識別子を使用する必要があります。 指定されていない列名は、ドライバーが生成した名前 (最初の列の "Col1" など) に置き換えられます。  
  
 パイプ文字 (&#124;) は、名前が引用符で囲まれているかどうかにかかわらず、列名に使用することはできません。  
  
 テキスト ドライバーを使用する場合、ドライバーは、列名が指定されていない場合は、既定の名前を提供します。 たとえば、ドライバーは、最初の列 F1、2 番目の列 F2 などを呼び出します。
